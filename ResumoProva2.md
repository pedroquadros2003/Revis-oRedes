# 📚 Guia de Revisão para Prova 2: Redes de Computadores e Internet (CSC-35)
> **Baseado no livro-texto:** *Computer Networking: A Top-Down Approach* (Kurose & Ross, 8ª/9ª Ed.)  
> **Conteúdo:** Capítulos 4, 5 e 6 + Laboratórios de Emulação com Mininet (Semanas 9 a 15 do Plano de Ensino do ITA)  
> **Objetivo:** Revisão aprofundada, didática e direta ao ponto, integrando os slides da disciplina, todas as suas anotações e destaques feitos no livro-texto, diagramas *plain-text* e a resolução comentada das questões teóricas do Mininet.

---

## 🧭 Sumário Geral

1. [Capítulo 4: Camada de Rede (Plano de Dados)](#capítulo-4-camada-de-rede-plano-de-dados)
   - [4.1 Visão Geral da Camada de Rede: Plano de Dados vs. Plano de Controle](#41-visão-geral-da-camada-de-rede-plano-de-dados-vs-plano-de-controle)
   - [4.2 Arquitetura Interna de um Roteador: Comutação, Filas e Escalonamento](#42-arquitetura-interna-de-um-roteador-comutação-filas-e-escalonamento)
   - [4.3 O Protocolo IP (IPv4): Datagrama, Fragmentação, Sub-redes e CIDR](#43-o-protocolo-ip-ipv4-datagrama-fragmentação-sub-redes-e-cidr)
   - [4.4 DHCP e NAT (Network Address Translation) + Travessia de NAT](#44-dhcp-e-nat-network-address-translation--travessia-de-nat)
   - [4.5 IPv6: Cabeçalho Simplificado e Transição IPv4 para IPv6](#45-ipv6-cabeçalho-simplificado-e-transição-ipv4-para-ipv6)
   - [4.6 [Menos Importante] Encaminhamento Generalizado e SDN (Match-Plus-Action)](#46-menos-importante-encaminhamento-generalizado-e-sdn-match-plus-action)
2. [Capítulo 5: Camada de Rede (Plano de Controle)](#capítulo-5-camada-de-rede-plano-de-controle)
   - [5.1 Controle por Roteador vs. Controle Logicamente Centralizado (SDN)](#51-controle-por-roteador-vs-controle-logicamente-centralizado-sdn)
   - [5.2 Algoritmos de Roteamento: Estado de Enlace (Dijkstra) vs. Vetor de Distância (Bellman-Ford)](#52-algoritmos-de-roteamento-estado-de-enlace-dijkstra-vs-vetor-de-distância-bellman-ford)
   - [5.3 Roteamento Hierárquico (AS) e Protocolos Intra-AS: RIP e OSPF](#53-roteamento-hierárquico-as-e-protocolos-intra-as-rip-e-ospf)
   - [5.4 Roteamento Inter-AS na Internet: BGP, Seleção de Rotas e Políticas](#54-roteamento-inter-as-na-internet-bgp-seleção-de-rotas-e-políticas)
   - [5.5 [Menos Importante] Plano de Controle SDN e Protocolo OpenFlow](#55-menos-importante-plano-de-controle-sdn-e-protocolo-openflow)
   - [5.6 Protocolo ICMP, Ping e Traceroute](#56-protocolo-icmp-ping-e-traceroute)
   - [5.7 [Menos Importante] Roteamento Broadcast e Multicast (IGMP e Árvores)](#57-menos-importante-roteamento-broadcast-e-multicast-igmp-e-árvores)
3. [Capítulo 6: Camada de Enlace e Redes Locais (LANs)](#capítulo-6-camada-de-enlace-e-redes-locais-lans)
   - [6.1 Serviços da Camada de Enlace e Implementação em Hardware (NIC)](#61-serviços-da-camada-de-enlace-e-implementação-em-hardware-nic)
   - [6.2 Detecção e Correção de Erros: Paridade 1D/2D, Checksum e CRC](#62-detecção-e-correção-de-erros-paridade-1d2d-checksum-e-crc)
   - [6.3 Protocolos de Acesso Múltiplo (MAC): Particionamento, ALOHA, CSMA/CD, Revezamento e DOCSIS](#63-protocolos-de-acesso-múltiplo-mac-particionamento-aloha-csmacd-revezamento-e-docsis)
   - [6.4 Endereçamento MAC e o Protocolo ARP (Mesma LAN vs. Outra LAN)](#64-endereçamento-mac-e-o-protocolo-arp-mesma-lan-vs-outra-lan)
   - [6.5 Ethernet (IEEE 802.3), Switches Autoaprendizes e VLANs (802.1Q)](#65-ethernet-ieee-8023-switches-autoaprendizes-e-vlans-8021q)
   - [6.6 [Menos Importante] Enlaces Ponto-a-Ponto (PPP / Byte Stuffing), MPLS e Redes de Data Center](#66-menos-importante-enlaces-ponto-a-ponto-ppp--byte-stuffing-mpls-e-redes-de-data-center)
   - [6.7 Síntese Completa: Um Dia na Vida de uma Requisição Web (Passos 1 a 24)](#67-síntese-completa-um-dia-na-vida-de-uma-requisição-web-passos-1-a-24)
4. [Semana 12: Laboratórios de Mininet e Questões Teóricas Resolvidas](#semana-12-laboratórios-de-mininet-e-questões-teóricas-resolvidas)
   - [7.1 Arquitetura do Mininet: Namespaces, veth, Open vSwitch e TCLink](#71-arquitetura-do-mininet-namespaces-veth-open-vswitch-e-tclink)
   - [7.2 Resolução Comentada das Questões Teóricas do Lab 04 (Q1 a Q4)](#72-resolução-comentada-das-questões-teóricas-do-lab-04-q1-a-q4)
   - [7.3 Resolução Comentada das Questões Teóricas do Lab 05 (Q1 a Q3)](#73-resolução-comentada-das-questões-teóricas-do-lab-05-q1-a-q3)
5. [Resumo das Fórmulas Críticas para a Prova 2](#resumo-das-fórmulas-críticas-para-a-prova-2)
6. [Quadros Comparativos Rápidos](#quadros-comparativos-rápidos)

---

# Capítulo 4: Camada de Rede (Plano de Dados)

## 4.1 Visão Geral da Camada de Rede: Plano de Dados vs. Plano de Controle

Enquanto a camada de transporte fornece comunicação lógica entre **processos** nos sistemas finais, a camada de rede fornece comunicação lógica **hospedeiro a hospedeiro (*host-to-host*)**, estando presente em **todos** os hosts e roteadores da rede. Sua operação divide-se em duas funções fundamentais:

| Função | Plano | Escala de Tempo / Escopo | Descrição Técnica |
| :--- | :--- | :--- | :--- |
| **Encaminhamento (*Forwarding* / Repasse)** | **Plano de Dados (*Data Plane*)** | **Local** ao roteador (nanosegundos, implementado em **hardware**) | Ação de mover um pacote que chega em uma interface de entrada para a interface de saída apropriada, consultando a tabela de repasse (*Forwarding Table*) ou tabela de fluxo (*Flow Table*). |
| **Roteamento (*Routing*)** | **Plano de Controle (*Control Plane*)** | **Global** na rede (milissegundos a segundos, implementado em **software**) | Processo que determina a rota fim-a-fim da origem ao destino e preenche as tabelas de repasse dos roteadores (seja por algoritmos distribuídos por roteador ou por um controlador SDN centralizado). |

### Modelos de Serviço de Rede (*Network Service Model*):
* **Modelo da Internet (*Best-Effort* / Melhor Esforço):** Não oferece **nenhuma garantia** quanto à entrega de datagramas, atraso máximo, entrega em ordem, variação de atraso (*jitter*) ou largura de banda mínima. Sua simplicidade no núcleo da rede (aliada a largura de banda abundante e mecanismos fim-a-fim no TCP) permitiu a escalabilidade global da Internet.
* **Outras arquiteturas históricas (ex: ATM):** Ofereciam garantias como *Constant Bit Rate* (CBR — banda e atraso constantes como circuito dedicado) e *Available Bit Rate* (ABR — banda mínima garantida e sem perdas).

### [Menos Importante — Apenas nos Slides `parte4-1.pdf`] Redes de Circuitos Virtuais (VC) vs. Redes de Datagramas:
* **Redes de Circuitos Virtuais (ex: ATM, Frame Relay):** Camada de rede **orientada a conexão**.
  - Possui 3 fases: estabelecimento do VC (via protocolos de sinalização), transferência de dados e encerramento.
  - Um VC consiste em: **(1)** um caminho da origem ao destino; **(2)** **números de VC** (um número diferente para cada enlace ao longo do caminho, reescrito pelo roteador a cada salto para evitar coordenação global e manter o campo pequeno no cabeçalho); e **(3)** entradas de estado nas tabelas de repasse de cada roteador no caminho: `(Interface Entrada, Nº VC Entrada) -> (Interface Saída, Nº VC Saída)`.
* **Redes de Datagramas (Internet IP):** Camada de rede **sem conexão**.
  - Não há estabelecimento de chamada; os roteadores **não mantêm estado de conexão fim-a-fim**.
  - Os pacotes são encaminhados usando o endereço IP de destino e podem seguir rotas diferentes.

---

## 4.2 Arquitetura Interna de um Roteador: Comutação, Filas e Escalonamento

Um roteador é composto por **4 elementos arquiteturais principais**:

```
                     +-------------------------------------+
                     |     Processador de Roteamento       | <-- Plano de Controle (Software, ms)
                     |  (Protocolos OSPF/BGP ou Agente SDN)|
                     +-------------------------------------+
                                        | (Atualiza tabelas de repasse)
                                        v
   Enlaces de    +-------------------+     +-------------------+     +-------------------+   Enlaces de
   Entrada ----> | Portas de Entrada | --> |     Elemento      | --> |  Portas de Saída  | ----> Saída
                 | (Física, Enlace,  |     |   de Comutação    |     | (Buffer/Fila,     |
                 |  Lookup TCAM,Fila)|     | (Switching Fabric)|     |  Enlace, Física)  |
                 +-------------------+     +-------------------+     +-------------------+
                 |<------------------ Plano de Dados (Hardware, ns) -------------------->|
```

### 1. Processamento na Porta de Entrada e *Longest Prefix Matching*
* A porta de entrada realiza a terminação física (camada 1), desencapsulamento do quadro (camada 2) e a **busca descentralizada (*lookup*)** na cópia local da tabela de repasse (*shadow copy*) para descobrir a porta de saída em velocidade de linha (*line rate*).
* **Regra da Concordância do Prefixo Mais Longo (*Longest Prefix Matching*):**
  Quando o endereço IP de destino de um datagrama casa com **mais de uma entrada** na tabela de repasse, o roteador utiliza a regra que possui o **prefixo mais longo (mais bits coincidentes da esquerda para a direita, i.e., a rota mais específica)**.

> **Exemplo Clássico de *Longest Prefix Matching*:**
> ```
> Prefixo na Tabela                       Interface de Saída
> ----------------------------------------------------------
> 11001000 00010111 00010*** ********          0
> 11001000 00010111 00011000 ********          1
> 11001000 00010111 00011*** ********          2
> Caso contrário (Default)                     3
> ```
> * Destino `11001000 00010111 00010110 10100001` $\implies$ Casa apenas com a 1ª regra (21 bits) $\to$ **Interface 0**.
> * Destino `11001000 00010111 00011000 10101010` $\implies$ Casa com a 2ª regra (24 bits) e com a 3ª regra (21 bits). Como $24 > 21$ (prefixo mais longo!), vai para a **Interface 1**.

* **Hardware TCAM (*Ternary Content Addressable Memory*):** Permite buscar endereços de 32 bits (com bits `0`, `1` e `don't care *`) em **um único ciclo de clock** (ordem de nanosegundos), independentemente do tamanho da tabela.

---

### 2. Os 3 Tipos de Elementos de Comutação (*Switching Fabrics*)

```
(1) Por Memória (CPU)           (2) Por Barramento (Bus)        (3) Por Rede Crossbar (Malha)
   +---------------+             [In]      [In]      [In]            [In]   [In]   [In]
   |  CPU / Memória|               |         |         |               |      |      |
   +---------------+             =========================           --+------+------+-- [Out]
     ^           |                      |         |                  --+------+------+-- [Out]
     |           v                    [Out]     [Out]                --+------+------+-- [Out]
   [In]        [Out]             (1 pacote por vez no bus)          (Múltiplos pacotes em paralelo!)
```

1. **Comutação via Memória:** Roteadores de 1ª geração. O pacote é copiado da porta de entrada para a memória do processador (via interrupção) e depois da memória para a porta de saída. Como atravessa o barramento de memória **duas vezes**, a vazão máxima é limitada a $\frac{B}{2}$ (onde $B$ é a largura de banda da memória).
2. **Comutação via Barramento (*Bus*):** A porta de entrada coloca um rótulo interno no pacote e o transmite diretamente em um barramento compartilhado; todas as portas de saída recebem, mas apenas a porta designada o retém. Não sofre intervenção da CPU, mas **apenas 1 pacote pode cruzar o barramento por vez** (a velocidade do switch é limitada pela banda do barramento).
3. **Comutação via Rede de Interconexão (*Crossbar / Banyan*):** Composta por $2N$ barramentos que conectam $N$ portas de entrada a $N$ portas de saída. É **não-bloqueante (*non-blocking*)**: múltiplos pacotes podem ser encaminhados **simultaneamente em paralelo**, desde que sejam destinados a portas de saída diferentes! Pacotes de tamanho variável podem ser quebrados em células de tamanho fixo para cruzar a malha.

---

### 3. Onde Ocorrem as Filas? (*Input Queuing* vs. *Output Queuing*)

* **Enfileiramento na Entrada e *HOL Blocking* (*Head-of-the-Line Blocking*):**
  - Se o elemento de comutação não for rápido o suficiente para transferir todos os pacotes que chegam ($R_{\text{switch}} < N \cdot R_{\text{line}}$), formam-se filas nas portas de entrada.
  - **Bloqueio de Cabeça de Linha (*HOL Blocking*):** Mesmo em uma malha *Crossbar*, se dois pacotes na frente de duas filas de entrada quiserem ir para a **mesma porta de saída**, um passa e o outro espera. Um pacote **atrás** do pacote bloqueado na fila de entrada fica impedido de avançar, **mesmo que sua porta de saída de destino esteja completamente livre!**
  - Sob tráfego uniforme em portas de alta carga, o *HOL Blocking* limita a vazão das filas de entrada a no máximo **$2 - \sqrt{2} \approx 58{,}6\%$** da capacidade da linha.

```
HOL Blocking na Entrada:
Entrada 1:  [Pacote p/ Saída A]  ---> (Passa!) ---------------------> Saída A
Entrada 2:  [Pacote p/ Saída B (LIVRE!)] [Pacote p/ Saída A (BLOQUEADO)] ---> Saída B (Ociosa!)
             ^-- Preso atrás do pacote vermelho que disputa a Saída A!
```

* **Enfileiramento na Saída, *Drop-Tail*, AQM e *Bufferbloat*:**
  - Se $R_{\text{switch}} \ge N \cdot R_{\text{line}}$, não há fila na entrada, mas se múltiplos pacotes de entradas diferentes forem comutados para a mesma porta de saída ao mesmo tempo, formam-se filas no **buffer da porta de saída**.
  - Quando o buffer enche, ocorre perda de pacotes: **Drop-Tail** (descarta o pacote recém-chegado) ou **AQM (*Active Queue Management*)**, como **RED (*Random Early Detection*)** e **ECN (*Explicit Congestion Notification*)**, que descartam ou marcam pacotes no cabeçalho IP **antes** de o buffer lotar para avisar o TCP precocemente.
  - **Dimensionamento de Buffer (RFC 3439):**
    - Regra clássica: $B = \text{RTT} \cdot C$ (produto atraso $\times$ capacidade do enlace).
    - Regra moderna para $N$ fluxos TCP independentes concorrentes:
      $$B = \frac{\text{RTT} \cdot C}{\sqrt{N}}$$
  - ***Bufferbloat*:** Quando roteadores domésticos possuem buffers exageradamente grandes e o TCP só reduz a janela após perda (*Drop-Tail*), as filas permanecem **persistentemente cheias**, causando atrasos de enfileiramento ($d_{\text{queue}}$) altíssimos e prejudicando aplicações de tempo real (VoIP/jogos).

---

### 4. Disciplinas de Escalonamento de Pacotes (*Packet Scheduling*)

| Algoritmo | Funcionamento | Características / Detalhe de Prova |
| :--- | :--- | :--- |
| **FIFO (*First-In-First-Out* / FCFS)** | Transmite os pacotes estritamente na ordem de chegada à fila de saída. | Simples, mas não diferencia tráfego sensível a atraso (ex: VoIP) de downloads pesados. |
| **Fila de Prioridade (*Priority Queuing*)** | Pacotes são classificados em filas de alta e baixa prioridade. Sempre transmite da fila de maior prioridade que não esteja vazia. | **Atenção:** No modelo padrão é **não-preemptivo (*non-preemptive*)**: se um pacote de baixa prioridade já começou a ser transmitido no enlace, ele **não é interrompido** se chegar um pacote de alta prioridade! |
| ***Round Robin* (RR)** | Pacotes são separados em classes e o escalonador alterna ciclicamente entre as filas não vazias ($1 \to 2 \to 3 \to 1 \dots$). | Disciplina **conservadora de trabalho (*work-conserving*)**: nunca deixa o enlace ocioso se houver pacote em qualquer fila (avança imediatamente para a próxima classe). |
| ***Weighted Fair Queuing* (WFQ)** | Generalização do Round Robin onde cada classe $i$ recebe um peso $w_i$. | Garante que a classe $i$ receba no mínimo uma fração $\frac{w_i}{\sum_j w_j} \cdot R$ da largura de banda do enlace, mesmo sob saturação total. |

* **Neutralidade de Rede (*Net Neutrality* — Destaque no Livro, p. 339):** Relaciona-se diretamente ao escalonamento de pacotes e baseia-se em regras como **Não Bloqueio (*No Blocking*)** (ISPs não podem bloquear conteúdos, aplicações ou serviços lícitos) e **Não Priorização Paga (*No Paid Prioritization*)** (ISPs não podem cobrar para favorecer determinados fluxos de tráfego em detrimento de outros).

---

## 4.3 O Protocolo IP (IPv4): Datagrama, Fragmentação, Sub-redes e CIDR

### 1. Formato do Datagrama IPv4

```
Cabeçalho IPv4 (20 bytes mínimos sem opções):
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|Versão |Tam.Cab|Tipo de Serviço|   Comprimento Total (16 bits) |
| (4b)  | (4b)  | (DiffServ+ECN)|     (Cabeçalho + Dados)       |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|     Identificador (16 bits)   |Flags|   Offset de Fragmento   |
|         (Fragmentação)        | (3b)|    (13b, unid. de 8B)   |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| Tempo de Vida |   Protocolo   |     Checksum do Cabeçalho     |
|   TTL (8b)    | Superior (8b) |           (16 bits)           |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Endereço IP de Origem (32 bits)               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Endereço IP de Destino (32 bits)              |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Opções (se houver, variável)               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Dados (Payload: Segmento TCP/UDP/ICMP)        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

* **Sobrecarga (*Overhead*) Padrão:** $20\text{ bytes (IP)} + 20\text{ bytes (TCP)} = \mathbf{40\text{ bytes}}$ de cabeçalhos para cada pacote TCP/IP.
* **TTL (*Time-To-Live*):** Decrementado em $1$ a cada roteador atravessado. Quando atinge $0$, o datagrama é descartado (evita loops infinitos) e um erro ICMP é enviado à origem.
* **Protocolo de Camada Superior (*Upper-Layer Protocol*):** É a "cola" que permite ao host de destino demultiplexar o datagrama para o protocolo correto: **`6` = TCP**, **`17` = UDP**, **`1` = ICMP**, **`89` = OSPF**.
* **Checksum do Cabeçalho IPv4:** Cobre **apenas o cabeçalho IP** (ao contrário do checksum TCP/UDP que cobre cabeçalho + payload). **Deve ser recalculado em todo roteador** porque o campo `TTL` (e possivelmente opções/fragmentação) muda a cada salto!

---

### 2. Fragmentação e Remontagem IPv4
* Cada enlace de camada 2 possui um **MTU (*Maximum Transmission Unit*)** que limita o tamanho máximo do datagrama IP que pode carregar (ex: Ethernet padrão tem $\text{MTU} = 1500\text{ bytes}$).
* Quando um roteador recebe um datagrama maior que o MTU do enlace de saída, ele **fragmenta** o datagrama em datagramas menores, copiando o mesmo `Identifier`.
* **Onde ocorre a remontagem (*reassembly*)?** **Exclusivamente no host final de destino!** (Mantém o núcleo da rede simples e permite que fragmentos viajem por rotas distintas). Se **um único fragmento** se perder, o datagrama inteiro é descartado pelo destino.
* **Cálculo dos Fragmentos (Atenção às Regras):**
  1. Cada fragmento precisa do seu próprio **cabeçalho IP de 20 bytes**. Logo, o espaço máximo de payload por fragmento é $\text{MTU} - 20$, arredondado para baixo para o **múltiplo de 8 bytes** mais próximo (pois o campo `Offset` tem 13 bits e o comprimento total tem 16 bits, logo o `Offset` é expresso em **unidades de 8 bytes**!).
  2. Todos os fragmentos iniciais têm a flag **`M = 1` (*More Fragments*)**; apenas o **último fragmento tem `M = 0`**.
  3. O deslocamento (`Offset`) do fragmento é:
     $$\text{Offset} = \frac{\text{Total de bytes de payload enviados nos fragmentos anteriores}}{8}$$

> **Exemplo Numérico Clássico (Livro & Slides `parte4-2.pdf`):**  
> Um datagrama IP de **4000 bytes** ($20\text{ B de cabeçalho} + 3980\text{ B de dados}$) chega a um roteador cujo enlace de saída tem **$\text{MTU} = 1500\text{ bytes}$**. Como ele é fragmentado?  
> * Payload máximo por fragmento $= 1500 - 20 = 1480\text{ bytes}$ (como $1480 / 8 = 185$ é divisível por $8$, usamos $1480\text{ B}$).
> 
> | Fragmento | Tamanho Total (`Length`) | Bytes de Payload | `ID` | Flag `M` | `Offset` (Bytes Ant. / 8) |
> | :--- | :--- | :--- | :--- | :--- | :--- |
> | **1º Fragmento** | $1500\text{ B}$ ($20 + 1480$) | Bytes $0$ a $1479$ ($1480\text{ B}$) | `x` | `1` | $0 / 8 = \mathbf{0}$ |
> | **2º Fragmento** | $1500\text{ B}$ ($20 + 1480$) | Bytes $1480$ a $2959$ ($1480\text{ B}$) | `x` | `1` | $1480 / 8 = \mathbf{185}$ |
> | **3º Fragmento** | $1040\text{ B}$ ($20 + 1020$) | Bytes $2960$ a $3979$ ($1020\text{ B}$) | `x` | `0` | $2960 / 8 = \mathbf{370}$ |

---

### 3. Endereçamento IPv4, Interfaces, Sub-redes e CIDR
* **Interface:** Fronteira física entre um host/roteador e o enlace físico. Um endereço IP está tecnicamente associado a uma **interface** (um roteador possui múltiplas interfaces, logo possui múltiplos endereços IP).
* **Sub-rede (*Subnet*):** Conjunto de interfaces de dispositivos que podem alcançar umas às outras fisicamente **sem passar por um roteador intermediário**.
  - **Receita prática para contar sub-redes em uma topologia (Slides `parte4-2.pdf`):** Destaque (desconecte) todas as interfaces dos hosts e roteadores; cada **"ilha" isolada** formada é exatamente **1 sub-rede** (incluindo enlaces ponto-a-ponto entre dois roteadores!).
* **CIDR (*Classless Interdomain Routing*):** Notação `a.b.c.d/x`, onde os primeiros $x$ bits constituem o **prefixo da rede (*subnet part*)** e os $32 - x$ bits restantes identificam o **host (*host part*)**.
  - Número de endereços no bloco $/x = 2^{32-x}$ (tipicamente $2^{32-x} - 2$ hosts utilizáveis, descontando o endereço de rede — todos os bits de host em `0` — e o endereço de broadcast — todos os bits de host em `1`).
  - Endereço de Broadcast Global da sub-rede local: **`255.255.255.255`**.
* **Agregação de Rotas (*Route Aggregation / Route Summarization*):**
  - Um ISP que possui os blocos `200.23.16.0/23`, `200.23.18.0/23`, ..., `200.23.30.0/23` pode anunciá-los para o restante da Internet como um **único prefixo agregado `200.23.16.0/20`**, reduzindo drasticamente o tamanho das tabelas de roteamento globais.
  - Se uma organização (`200.23.18.0/23`) mudar para outro ISP, o novo ISP passa a anunciar o prefixo mais específico `/23`. Pela **regra do prefixo mais longo**, o tráfego será corretamente desviado para o novo ISP (`/23` vence `/20`)!

---

## 4.4 DHCP e NAT (Network Address Translation) + Travessia de NAT

### 1. DHCP (*Dynamic Host Configuration Protocol*)
Protocolo cliente-servidor *plug-and-play* que aloca endereços IP dinamicamente a hosts que entram na rede. Opera sobre **UDP** (**porta 67 no servidor**, **porta 68 no cliente**).

> 📝 **Sua Anotação no Livro (p. 355):**  
> * **DHCP:** Distribui **IP do host**, **máscara de sub-rede**, **gateway padrão (*first-hop router*)** e **endereço do servidor DNS local**.  
> * **ARP:** Descobre qual endereço MAC corresponde a um IP na rede local IPv4.  
> * **Switch e controles de segurança:** Encaminham quadros e, quando configurados, podem restringir quais dispositivos e tráfegos são aceitos.

```
Os 4 Passos do DHCP (Mecanismo DORA):
  Host Cliente Recém-Chegado                             Servidor DHCP (ex: 223.1.2.5)
  (Sem IP: 0.0.0.0, Porta 68)                                     (Porta 67)
              |                                                       |
              | --- (1) DHCP DISCOVER ------------------------------->|
              |     IP Orig: 0.0.0.0:68 | IP Dest: 255.255.255.255:67 | (Broadcast!)
              |                                                       |
              | <-- (2) DHCP OFFER -----------------------------------|
              |     IP Orig: 223.1.2.5:67 | IP Dest: 255.255.255.255:68
              |     yiaddr (Seu IP oferecido): 223.1.2.4, Lease Time  |
              |                                                       |
              | --- (3) DHCP REQUEST -------------------------------->|
              |     IP Orig: 0.0.0.0:68 | IP Dest: 255.255.255.255:67 | (Ainda Broadcast p/ avisar outros servidores DHCP!)
              |                                                       |
              | <-- (4) DHCP ACK -------------------------------------|
              |     Confirma IP, Máscara, Default Gateway e DNS Local |
```

* **Por que os passos 1 e 3 (e frequentemente 2 e 4) usam Broadcast (`255.255.255.255`)?** Porque no início o host ainda não possui um endereço IP configurado nem sabe o IP do servidor DHCP; e no passo 3 (`DHCP Request`), como pode haver múltiplos servidores DHCP na sub-rede que enviaram ofertas, o broadcast avisa a todos qual oferta foi aceita para que os demais liberem os IPs não escolhidos.

---

### 2. NAT (*Network Address Translation* — RFC 3022)
Permite que toda uma rede local doméstica/corporativa (usando **endereços IP privados**: `10.0.0.0/8`, `172.16.0.0/12` ou `192.168.0.0/16`) se apresente ao mundo externo como **um único dispositivo com um único endereço IPv4 público** na interface WAN do roteador NAT.

> 📝 **Sua Anotação no Livro (p. 357):**  
> *"Sub-rede organiza a comunicação IP entre os hosts; o NAT permite que vários desses hosts compartilhem um endereço público. São mecanismos complementares, não substitutos."*

```
Funcionamento da Tradução NAT (IP + Porta):
Rede Privada (10.0.0.0/24)            Roteador NAT               Internet Pública (WAN)
                                +-----------------------+
[Host 10.0.0.1] --------------> | Tabela de Tradução NAT| --------------> [Servidor Web]
Envia datagrama:                | WAN         <-> LAN   | Envia datagrama: 128.119.40.186:80
Orig: 10.0.0.1, Porta 3345      | 138.76.29.7 <-> 10.0.0.1| Orig: 138.76.29.7, Porta 5001
Dest: 128.119.40.186, Porta 80  | Porta 5001      Porta 3345| Dest: 128.119.40.186, Porta 80
                                +-----------------------+
[Host 10.0.0.1] <-------------- | Reescreve Destino p/  | <-------------- Resposta do Servidor:
Recebe datagrama:               | 10.0.0.1, Porta 3345  | Orig: 128.119.40.186, Porta 80
Dest: 10.0.0.1, Porta 3345      +-----------------------+ Dest: 138.76.29.7, Porta 5001
```

* Como o campo de porta TCP/UDP tem **16 bits**, um único endereço IP público no roteador NAT pode suportar **mais de $60.000$ conexões simultâneas**!
* **Objeções Arquiteturais ao NAT:**
  1. Os números de porta pertencem à **Camada 4 (Transporte)** e destinam-se a endereçar *processos*, não *hosts* (violação do isolamento em camadas).
  2. Roteadores deveriam processar pacotes apenas até a **Camada 3 (Rede)**, sem modificar campos TCP/UDP.
  3. Viola o **Princípio Fim-a-Fim**: hosts deveriam falar diretamente entre si sem que nós intermediários alterem endereços IP e números de porta.

### 3. O Problema da Travessia de NAT (*NAT Traversal*) e as 3 Soluções (Slides `parte4-2.pdf` pp. 37-39):
Se um cliente externo quiser **iniciar** uma conexão com um servidor ou par P2P localizado atrás de um NAT (ex: `10.0.0.1`), o pacote será descartado pelo roteador NAT caso não exista entrada prévia na tabela de tradução. As **3 soluções clássicas** são:
1. **Solução 1 — Configuração Estática (*Static Port Forwarding*):** O administrador configura manualmente a tabela NAT para que qualquer pacote que chegue em `(IP_WAN, Porta 2500)` seja sempre redirecionado para `(10.0.0.1, Porta 25000)`.
2. **Solução 2 — UPnP (*Universal Plug and Play*) / Protocolo IGD (*Internet Gateway Device*):**  
   > 📝 **Sua Anotação no Slide 38 de `parte4-2.pdf`:**  
   > *"Protocolo auxiliar que preenche de forma inteligente a tabela NAT, permitindo que dispositivos da rede local solicitem ao roteador a criação de mapeamentos de portas"* e descubram o endereço IP público automaticamente.
3. **Solução 3 — *Relaying* (Repasse via Servidor Intermediário, ex: TURN / Skype):**
   - **(1)** O host atrás do NAT inicia uma conexão de saída com um servidor *Relay* público (criando entrada no NAT).
   - **(2)** O cliente externo também se conecta ao servidor *Relay*.
   - **(3)** O *Relay* faz a ponte (*bridge*) retransmitindo os pacotes entre as duas conexões estabelecidas.

### 4. Firewalls e IDS na Borda da Rede (Destaque no Livro, p. 358):
* **Firewalls:** Inspecionam campos dos cabeçalhos de datagramas IP e segmentos TCP/UDP, bloqueando tráfego suspeito (ex: bloquear pacotes `ICMP Echo Request` ou permitir apenas segmentos pertencentes a conexões TCP aprovadas e rastreadas).
* **IDS (*Intrusion Detection System*):** Situado na borda da rede, realiza **Inspeção Profunda de Pacotes (*Deep Packet Inspection*)**, examinando não apenas os cabeçalhos, mas também o **conteúdo útil (*payload*)** dos pacotes em busca de assinaturas de ataques.

---

## 4.5 IPv6: Cabeçalho Simplificado e Transição IPv4 para IPv6

Motivado pelo esgotamento dos endereços IPv4 de 32 bits e pela necessidade de agilizar o processamento em roteadores, o **IPv6** introduziu mudanças profundas:

### Principais Mudanças do IPv4 para o IPv6:
1. **Endereços de 128 bits ($2^{128}$ endereços):** Capacidade praticamente inesgotável; inclui modos *unicast*, *multicast* e ***anycast*** (entregar para o servidor mais próximo de um grupo).
2. **Cabeçalho de Tamanho Fixo e Simplificado de 40 bytes:** Permite processamento muito mais rápido nos roteadores.
3. **Sem Fragmentação/Remontagem em Roteadores Intermediários:** Apenas os sistemas finais de origem e destino podem fragmentar! Se um datagrama IPv6 for grande demais para o enlace de saída, o roteador simplesmente **descarta o datagrama** e envia uma mensagem de erro **ICMPv6 *"Packet Too Big"*** para o emissor reduzir o tamanho.
4. **Remoção do *Header Checksum*:** Como a camada de enlace (Ethernet CRC) e a camada de transporte (TCP/UDP Checksum) já fazem verificação de erros, o IPv6 eliminou o checksum na camada 3 para evitar o recálculo custoso a cada roteador.
5. **Remoção do Campo de Opções do Cabeçalho Base:** As opções passam a ser apontadas pelo campo **`Next Header` (*Próximo Cabeçalho*)**, formando uma cadeia modular que só é processada quando necessário.
6. **Rotulagem de Fluxo (*Flow Label* — 20 bits) e Classe de Tráfego (*Traffic Class* — 8 bits):** Permitem tratamento diferenciado (QoS) para fluxos específicos (ex: áudio/vídeo).

### Transição de IPv4 para IPv6: **Tunelamento (*Tunneling*)**
Como não existe um *"Flag Day"* para desligar todos os roteadores IPv4 do planeta simultaneamente, a rede entre dois roteadores IPv6 (ex: B e E) composta por roteadores legados IPv4 (C e D) é chamada de **Túnel**.

```
Funcionamento do Tunelamento (IPv6 dentro de IPv4):
[Roteador IPv6 A] ---> [Roteador B (Dual Stack)] =====(Túnel IPv4: C -> D)=====> [Roteador E (Dual Stack)] ---> [Roteador IPv6 F]
                        Encapsula o datagrama                                     Desencapsula o IPv4 e
                        IPv6 inteiro dentro do                                    recupera o datagrama
                        payload de um datagrama IPv4!                             IPv6 original!
```

* **Por que a adoção do IPv6 foi tão lenta? (Analogia Destacada na p. 363 do Livro):**
  - Introduzir novos protocolos na **Camada de Aplicação** é como *"adicionar uma nova mão de tinta em uma casa"* (fácil, pois exige atualizar apenas os sistemas finais).
  - Introduzir mudanças na **Camada de Rede (IP)** é como *"trocar o alicerce (fundação) de uma casa"* — extremamente difícil de fazer sem mexer em toda a infraestrutura global de roteadores!

---

## 4.6 [Menos Importante] Encaminhamento Generalizado e SDN (Match-Plus-Action)

> ⚪ **Menos Importante (Não grifado no livro-texto):** Você parou as marcações do Capítulo 4 na página 363 (Tunelamento IPv6) e não grifou a Seção 4.4 no livro. Mantido aqui de forma enxuta apenas como suporte ao Lab 04 de Mininet/OpenFlow.

No encaminhamento tradicional baseado apenas no IP de destino, o roteador olha um único campo da camada 3. Nas **Redes Definidas por Software (SDN)** com switches **OpenFlow**, o plano de dados realiza **Encaminhamento Generalizado (*Match-Plus-Action*)** através de uma **Tabela de Fluxo (*Flow Table*)** contendo:
1. **Conjunto de Campos de Cabeçalho (*Match*):** Pode inspecionar campos das camadas 2, 3 e 4 (`Ingress Port`, `MAC src/dst`, `Eth type`, `VLAN ID`, `IP src/dst`, `IP Proto`, `TCP/UDP src/dst port`). *(Observação: o protocolo OpenFlow não permite casar o campo TTL nem o comprimento do datagrama)*.
2. **Conjunto de Contadores (*Counters*):** Número de pacotes e bytes que casaram com aquela regra e tempo desde a última atualização.
3. **Conjunto de Ações (*Actions*):**
   - **Encaminhar (*Forwarding*):** Enviar para uma porta física específica, fazer broadcast para todas as portas ou multicast para um grupo de portas.
   - **Descartar (*Dropping*):** Uma regra sem nenhuma ação descarta silenciosamente os pacotes que casam com ela (atuando como **Firewall**!).
   - **Modificar Campos (*Modify-Field*):** Reescrever campos de cabeçalho das camadas 2, 3 ou 4 antes de encaminhar (atuando como **NAT**!).

> **Polivalência de um Switch OpenFlow (*Chameleon Network Device*):**  
> Dependendo das regras `Match-Plus-Action` instaladas pelo controlador SDN, o mesmo switch OpenFlow pode operar simultaneamente como **Roteador** (match no prefixo `IP dst`), **Switch L2** (match no `MAC dst`), **Firewall** (match em `IP src` ou `TCP dst port` com `Action = Drop`) e **NAT** (reescrita de IP e porta)!

---

# Capítulo 5: Camada de Rede (Plano de Controle)

## 5.1 Controle por Roteador vs. Controle Logicamente Centralizado (SDN)

O Plano de Controle é responsável por coordenar como as tabelas de repasse (ou tabelas de fluxo) são calculadas, mantidas e instaladas em todos os roteadores da rede. Existem duas abordagens arquiteturais:

```
(A) Controle por Roteador (Tradicional: OSPF, BGP)        (B) Controle Logicamente Centralizado (SDN)
   [Algoritmo] <---> [Algoritmo] <---> [Algoritmo]                    +-------------------------+
   |Tabela Rep|      |Tabela Rep|      |Tabela Rep|                   | Controlador SDN Remoto  |
   +----------+      +----------+      +----------+                   +-------------------------+
   |Plano Dado| ---> |Plano Dado| ---> |Plano Dado|                     /          |          \  (OpenFlow)
   +----------+      +----------+      +----------+                    v           v           v
   (Planos de Controle e Dados monolíticos no mesmo                [ Agente ]  [ Agente ]  [ Agente ]
    hardware proprietário; roteadores conversam entre si)          |Tab.Fluxo| |Tab.Fluxo| |Tab.Fluxo|
                                                                   +---------+ +---------+ +---------+
```

1. **Controle por Roteador (*Per-Router Control*):** Cada roteador executa uma instância individual do algoritmo de roteamento (OSPF, RIP, BGP) no seu próprio processador de roteamento, trocando mensagens diretamente com os outros roteadores para calcular sua tabela de repasse.
2. **Controle Logicamente Centralizado (SDN):** Um **Controlador SDN remoto** mantém a visão global da rede, calcula todas as tabelas de fluxo e as instala nos comutadores via protocolo **OpenFlow** através de um Agente de Controle (*Control Agent - CA*) mínimo em cada switch. É dito *logicamente* centralizado porque, na prática, o controlador é implementado como um cluster distribuído de servidores para tolerância a falhas e escalabilidade.

---

## 5.2 Algoritmos de Roteamento: Estado de Enlace (Dijkstra) vs. Vetor de Distância (Bellman-Ford)

Modela-se a rede como um grafo $G = (N, E)$, onde $N$ é o conjunto de nós (roteadores) e $E$ é o conjunto de arestas (enlaces), cada qual com custo $c(x, y)$ (que pode refletir distância física, inverso da largura de banda $\frac{1}{R}$, atraso ou políticas). O objetivo é encontrar o **caminho de menor custo (*least-cost path*)** entre origem e destino.

### Classificação dos Algoritmos de Roteamento:
1. **Centralizado / Global (*Link-State - LS*) vs. Descentralizado (*Distance-Vector - DV*):** No LS, cada nó possui conhecimento completo da topologia e de todos os custos da rede; no DV, cada nó conhece apenas os custos até seus vizinhos diretos e troca estimativas iterativamente com eles.
2. **Estático vs. Dinâmico:** Estáticos mudam rotas muito lentamente (intervenção humana); dinâmicos reagem automaticamente a mudanças de carga ou topologia.
3. **Sensível à Carga (*Load-Sensitive*) vs. Insensível à Carga (*Load-Insensitive*):** Algoritmos sensíveis à carga ajustam $c(x,y)$ conforme o congestionamento atual. Como destacado nas **pp. 397–398 do livro**, isso provoca **oscilações severas de rota** (todos os roteadores mudam simultaneamente para a mesma rota alternativa e depois voltam). Para evitar a **auto-sincronização (*self-synchronization*)** entre roteadores que enviam anúncios com a mesma periodicidade, cada roteador deve **aleatorizar (*randomize*) o instante de envio** dos seus anúncios de estado de enlace! Os protocolos atuais da Internet (**RIP, OSPF, BGP**) são **insensíveis à carga**.

---

### 1. Algoritmo de Estado de Enlace (*Link-State - LS*) — Algoritmo de Dijkstra
Para que todos os nós conheçam a topologia completa $G=(N,E)$, cada nó executa previamente um **Broadcast de Estado de Enlace (*Link-State Broadcast*)**, inundando a rede com pacotes contendo a identidade e o custo dos seus enlaces adjacentes.

#### Notação de Dijkstra (calculando a partir da origem $u$):
* $D(v)$: Custo do caminho de menor custo conhecido até o momento da origem $u$ até o nó $v$.
* $p(v)$: Nó predecessor imediato de $v$ ao longo desse caminho a partir de $u$.
* $N'$: Subconjunto de nós cujo caminho de menor custo a partir de $u$ já é **definitivamente conhecido**.

```
Pseudocódigo do Algoritmo de Dijkstra (para o nó origem u):
1. Inicialização:
   N' = {u}
   Para todos os nós v:
       Se v é vizinho direto de u:
           D(v) = c(u, v), p(v) = u
       Caso contrário:
           D(v) = infinito
2. Loop (repetir até que todos os nós estejam em N'):
   Encontre w não pertencente a N' tal que D(w) seja mínimo
   Adicione w a N'
   Atualize D(v) para todo vizinho v de w que NÃO esteja em N':
       D(v) = min( D(v), D(w) + c(w, v) )   # Relaxamento da aresta
```

#### Exemplo Clássico de Execução de Dijkstra (Figura 5.3 do Livro — Origem `u`):
Considere os enlaces: $c(u,v)=2, c(u,x)=1, c(u,w)=5, c(x,v)=2, c(x,w)=3, c(v,w)=3, c(w,y)=1, c(x,y)=1, c(y,z)=2, c(w,z)=5$.

| Passo | Conjunto $N'$ | $D(v), p(v)$ | $D(w), p(w)$ | $D(x), p(x)$ | $D(y), p(y)$ | $D(z), p(z)$ |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **0** | $\{u\}$ | $2, u$ | $5, u$ | $\mathbf{1, u}$ | $\infty$ | $\infty$ |
| **1** | $\{u, x\}$ | $\mathbf{2, u}$ | $4, x$ | — | $\mathbf{2, x}$ | $\infty$ |
| **2** | $\{u, x, y\}$ | $\mathbf{2, u}$ | $3, y$ | — | — | $4, y$ |
| **3** | $\{u, x, y, v\}$ | — | $\mathbf{3, y}$ | — | — | $4, y$ |
| **4** | $\{u, x, y, v, w\}$ | — | — | — | — | $\mathbf{4, y}$ |
| **5** | $\{u, x, y, v, w, z\}$ | — | — | — | — | — |

> 📝 **Suas Anotações sobre Complexidade do LS (pp. 394 e 406 do Livro):**  
> * **Complexidade Computacional (CPU):** Na implementação simples com busca linear, buscar o mínimo leva $|N| + (|N|-1) + \dots + 1 = \mathbf{O(|N|^2)}$. *"Com heap, o algoritmo fica bem melhor"*: utilizando uma fila de prioridade baseada em *Min-Heap* (ou Fibonacci Heap), a complexidade cai para **$O(|N| \log |N| + |E|)$**!  
> * **Complexidade de Mensagens:** *"Pela necessidade de broadcast de estado, a complexidade de mensagens é $\mathbf{O(|N| \cdot |E|)}$"*, pois cada um dos $|N|$ nós precisa inundar seu estado de enlace atravessando todas as $|E|$ arestas da rede.

---

### 2. Algoritmo de Vetor de Distância (*Distance-Vector - DV*) — Equação de Bellman-Ford
O algoritmo DV é **distribuído**, **iterativo**, **assíncrono** e **autoterminante** (para sozinho quando nenhum vetor muda). Baseia-se na célebre **Equação de Bellman-Ford**:

$$d_x(y) = \min_{v \in \text{vizinhos}(x)} \big\{ c(x, v) + d_v(y) \big\}$$

* Cada nó $x$ mantém seu vetor de distâncias $D_x = [D_x(y) : y \in N]$ e a última cópia dos vetores $D_v$ recebidos de cada um de seus vizinhos diretos $v$.
* Sempre que $x$ detecta uma mudança no custo de um enlace local $c(x,v)$ **ou** recebe um vetor atualizado de um vizinho $v$, ele recalcula $D_x(y)$ usando Bellman-Ford. **Se (e somente se) o vetor $D_x$ mudar**, $x$ envia seu novo vetor $D_x$ para todos os seus vizinhos diretos.

> 📝 **Sua Anotação no Livro (p. 399):**  
> *"Mensagens são de complexidade $\mathbf{O(|E|)}$ em quantidade"* (por iteração, pois os vetores são trocados apenas entre vizinhos diretamente conectados por uma aresta $e \in E$).

---

### 3. O Problema da Contagem ao Infinito (*Count-to-Infinity*) e Reversão Envenenada

```
Cenário Clássico do Livro (Figura 5.7, p. 404):
         c(x,y): 4 ---> Muda p/ 60!
      (x) ----------------------- (y)
        \                         /
 c(x,z)=50\                     / c(y,z)=1
            \                 /
              ----- (z) -----
```

* **"Boas notícias correm rápido" (*Good news travels fast*):** Se $c(x,y)$ cai de $4$ para $1$, $y$ atualiza $D_y(x)=1$ e avisa $z$, que atualiza $D_z(x)=2$ imediatamente em $2$ iterações.
* **"Más notícias correm devagar" (*Bad news travels slowly* — Loop de Roteamento):**
  Suponha que antes da mudança teníamos $D_y(x) = 4$ e $D_z(x) = 4 + 1 = 5$ (pois $z$ passava por $y$). Agora o custo $c(x,y)$ sobe abruptamente de **$4$ para $60$**:
  1. Em $t_0$, o nó $y$ detecta que $c(x,y)=60$ e recalcula:
     $$D_y(x) = \min\{ c(y,x) + D_x(x),\ c(y,z) + D_z(x) \} = \min\{ 60 + 0,\ 1 + 5 \} = \mathbf{6}$$
     **Erro de visão local!** $y$ não sabe que o custo $D_z(x)=5$ de $z$ passava pelo próprio $y$! Forma-se um **Loop de Roteamento (Buraco Negro)**: $y$ envia pacotes para $z$ achando que $z$ chega em $x$ com custo $5$, e $z$ devolve para $y$!
  2. $y$ anuncia $D_y(x)=6$ para $z \implies z$ recalcula $D_z(x) = \min\{50, 1+6\} = \mathbf{7}$ e anuncia para $y$.
  3. $y$ recalcula $D_y(x) = \min\{60, 1+7\} = \mathbf{8}$ e anuncia para $z \implies z$ recalcula $D_z(x) = \mathbf{9}$, e assim sucessivamente!

> 📝 **Sua Anotação no Livro (p. 404 — Cálculo Exato do Número de Atualizações):**  
> *"Precisa de **46 atualizações** do vetor, somando as mudanças em $x$ e em $z$, até chegar no valor correto"*:  
> * O loop de pingue-pongue entre $y$ e $z$ persiste por **44 iterações** (enquanto $D_y(x)$ e $D_z(x)$ sobem de $6, 7, 8, \dots$ até $D_y(x) = 50$).  
> * Na 45ª atualização, $z$ finalmente percebe que $1 + D_y(x) = 51 > 50$ e escolhe o enlace direto $c(z,x) = \mathbf{50}$, anunciando $D_z(x) = 50$ para $y$.  
> * Na 46ª atualização final, $y$ recebe $D_z(x)=50$ e estabiliza em $D_y(x) = \min\{60, 1+50\} = \mathbf{51}$ via $z$!

* **Solução Parcial — Reversão Envenenada (*Poisoned Reverse*):**
  - **Regra:** Se o nó $z$ roteia para o destino $x$ passando pelo vizinho $y$, então $z$ **mente para $y$** anunciando que sua distância até $x$ é infinita: **$D_z(x) = \infty$**!
  - Assim, quando $c(x,y)$ sobe de $4$ para $60$, $y$ vê $D_z(x) = \infty$, atualiza $D_y(x) = 60$ imediatamente e avisa $z$; $z$ muda sua rota para o enlace direto de $50$ (e passa a anunciar $D_z(x)=50$ para $y$, pois não usa mais $y$), e $y$ converge para $51$ sem entrar em loop!
  - **Limitação Crítica:** A Reversão Envenenada **NÃO resolve** loops de contagem ao infinito que envolvam **3 ou mais nós** (ciclos indiretos como $y \to z \to w \to y$).

---

## 5.3 Roteamento Hierárquico (AS) e Protocolos Intra-AS: RIP e OSPF

### 1. Por que Roteamento Hierárquico em Sistemas Autônomos (*Autonomous Systems - AS*)?
Tratar a Internet inteira como um único grafo plano de roteadores é inviável por duas razões fundamentais:
1. **Escala:** Com centenas de milhões de roteadores e bilhões de destinos, nenhum roteador teria memória para armazenar tabelas globais nem banda para inundar pacotes LS ou convergir vetores DV.
2. **Autonomia Administrativa:** Cada ISP ou organização deseja operar sua rede interna com o protocolo que preferir e ocultar sua topologia interna dos concorrentes.
* **Solução:** Dividir a Internet em **Sistemas Autônomos (ASs)**, cada um identificado por um número **ASN** único atribuído pela ICANN/RIRs.
  - **Protocolo de Roteamento Intra-AS (*Interior Gateway Protocol - IGP*):** Roda dentro de um mesmo AS (ex: **RIP**, **OSPF**, IS-IS). Foco em **desempenho**.
  - **Protocolo de Roteamento Inter-AS (*Exterior Gateway Protocol - EGP*):** Roda entre ASs diferentes (o padrão único da Internet é o **BGP**). Foco em **políticas comerciais**.

---

### 2. Protocolos Intra-AS: OSPF (Foco do Livro) vs. RIP ([Menos Importante — Apenas nos Slides `parte4-3.pdf`])

> ⚪ **Nota sobre as suas marcações:** No livro (Seção 5.3, pp. 406–409), você grifou **apenas o OSPF** (o RIP não faz parte da 8ª edição do livro, aparecendo somente nos slides `parte4-3.pdf`).

| Característica | **RIP (*Routing Information Protocol*)** | **OSPF (*Open Shortest Path First*)** |
| :--- | :--- | :--- |
| **Algoritmo Base** | **Vetor de Distância (DV)** (Bellman-Ford) | **Estado de Enlace (LS)** (Dijkstra + Inundação) |
| **Métrica de Custo** | **Contagem de Saltos (*Hop Count*)**: cada enlace tem custo $1$. Máximo de **15 saltos** (**$16 = \infty$**, com *Poisoned Reverse*). | Pesos configuráveis pelo administrador (ex: inversamente proporcional à banda ou atraso). |
| **Periodicidade de Anúncios** | Troca vetores (até 25 sub-redes por mensagem) entre vizinhos a cada **30 segundos**. Se um vizinho não for ouvido por **180 segundos**, é declarado morto! | Inunda *Link-State Advertisements (LSAs)* para **todo o AS** sempre que o estado de um enlace muda **e** periodicamente a cada **30 minutos** (robustez). |
| **Encapsulamento** | Processo de aplicação (`routed`) operando sobre **UDP na porta 520**. | Transportado **diretamente sobre IP** (`Upper-Layer Protocol = 89`), sem UDP nem TCP! |

####Os 4 Recursos Avançados do OSPF (que não existem no RIP):
1. **Segurança:** Mensagens OSPF podem ser autenticadas (ex: via **MD5** com chave secreta compartilhada entre os roteadores), impedindo que invasores injetem rotas falsas.
2. **Múltiplos Caminhos de Mesmo Custo (*ECMP — Equal-Cost Multi-Path*):** Se existirem múltiplas rotas com o mesmo custo mínimo até um destino, o OSPF divide o tráfego entre todas elas, sem precisar escolher apenas uma.
3. **Suporte Integrado a Roteamento Unicast e Multicast (MOSPF)** e múltiplos custos por enlace conforme o Tipo de Serviço (*TOS*).
4. **Hierarquia em Duas Camadas dentro de um Único AS:** Um AS OSPF grande pode ser dividido em **Áreas Locais** interligadas por uma **Área de Backbone (Área 0)**. O broadcast de estado de enlace fica confinado dentro de cada área, e os **Roteadores de Borda de Área (*Area Border Routers*)** roteiam pacotes entre as áreas passando obrigatoriamente pelo Backbone.
* **Inversão de Causa e Efeito na Engenharia de Tráfego OSPF (Destaque na p. 408 do Livro):** Na teoria, os pesos dos enlaces são dados e o OSPF calcula as rotas. Na prática, operadores de rede invertem essa lógica: sabendo quais rotas desejam obter (ex: minimizar a utilização máxima dos enlaces), eles **ajustam artificialmente os pesos OSPF** para forçar o algoritmo de Dijkstra a escolher aqueles caminhos!

---

## 5.4 Roteamento Inter-AS na Internet: BGP, Seleção de Rotas e Políticas

O **BGP (*Border Gateway Protocol* — versão 4, RFC 4271)** é o protocolo descentralizado e assíncrono do tipo **Vetor de Caminhos (*Path-Vector*)** que interconecta todos os Sistemas Autônomos da Internet. No BGP, os pacotes não são roteados para um endereço IP isolado, mas sim para **prefixos CIDR** (ex: `138.16.68/22`).

### 1. As 3 Funções do BGP e Sessões eBGP vs. iBGP
1. **Obter informações de alcançabilidade de prefixos** de ASs vizinhos (via sessões **eBGP** — *External BGP* entre roteadores de borda de ASs distintos).
2. **Propagar essas informações para todos os roteadores internos** do próprio AS (via sessões **iBGP** — *Internal BGP*).
3. **Determinar as "melhores" rotas** para cada prefixo com base nas informações de alcançabilidade e nas **políticas do AS**, preenchendo as tabelas de repasse.

```
Propagação de Anúncios BGP (eBGP + iBGP):
       AS1                                   AS2                                  AS3
+-----------------+                   +-----------------+                  +-----------------+
| [1a]       [1b] |      eBGP         | [2a]       [2b] |      eBGP        | [3a]            |
|                 |     Sessão TCP    |                 |    Sessão TCP    |                 | Prefix X
| [1d]       [1c] | <===============> | [2d]       [2c] | <==============> | [3d]            | (138.16.68/22)
+-----------------+                   +-----------------+                  +-----------------+
 (iBGP distribui                       (2c recebe de 3a via eBGP
  internamente no AS1)                  e espalha no AS2 via iBGP)
```

* **Transporte:** Sessões BGP rodam sobre conexões **TCP semipermanentes na porta 179** (4 tipos de mensagens: `OPEN`, `UPDATE`, `KEEPALIVE`, `NOTIFICATION`).

### 2. Atributos de Rota BGP: `AS-PATH` e `NEXT-HOP`
Quando um roteador anuncia um prefixo em uma sessão BGP, ele anexa atributos BGP (uma **rota BGP** = `PREFIX + Atributos`):
* **`AS-PATH`:** Lista ordenada dos ASNs pelos quais o anúncio já passou (ex: `AS2 AS3`).
  - **Prevenção de Loops:** Se um roteador vê o número do **seu próprio AS** já presente na lista `AS-PATH` de um anúncio recebido, ele **rejeita o anúncio imediatamente**, evitando loops de roteamento entre ASs!
* **`NEXT-HOP`:** É o endereço IP da **interface do roteador de borda do próximo AS** onde começa o `AS-PATH` (ou seja, a interface externa do link eBGP). Ele faz a ponte essencial entre o protocolo inter-AS (BGP) e o protocolo intra-AS (OSPF)!

---

### 3. Algoritmo de Seleção de Rotas no BGP (Ordem Estrita de Decisão!)
Se um roteador aprende **duas ou mais rotas** para o mesmo prefixo, ele aplica sequencialmente as **4 regras de desempate** abaixo até restar uma única rota:

```
Ordem de Seleção de Rota no BGP (Decorar para a Prova!):
  [Múltiplas Rotas p/ Prefixo X]
               |
               v
  (1) Maior Preferência Local (LOCAL-PREF) -----> Definida por decisão política/administrativa do AS!
               | (Empate)
               v
  (2) Menor Comprimento de AS-PATH -------------> Rota que atravessa o menor número de ASs (saltos de AS).
               | (Empate)
               v
  (3) Roteamento Batata Quente (Hot Potato) ----> Escolhe a rota cujo roteador NEXT-HOP tem o MENOR CUSTO
               | (Empate)                         INTRA-AS (IGP/OSPF) a partir do roteador atual!
               v
  (4) Identificadores BGP (Tie-Breaker) --------> Menor Router ID / critérios operacionais BGP.
```

> 🔥 **O que é o Roteamento Batata Quente (*Hot Potato Routing*)?**  
> Um pacote em trânsito é como uma "batata quente" queimando as mãos do AS: o roteador quer **se livrar do pacote (expulsá-lo do seu próprio AS) com o menor custo interno possível**, sem se importar com o custo que o pacote terá depois de entrar no próximo AS!  
> *Consequência importante:* Dois roteadores dentro do **mesmo AS** (ex: `1b` e `1d`) podem escolher roteadores de saída (`NEXT-HOP`) **diferentes** para o mesmo prefixo externo `x`, dependendo de qual roteador de borda está mais próximo de cada um segundo a métrica interna do OSPF!

---

### 4. Políticas de Roteamento BGP e Por que Intra-AS $\ne$ Inter-AS
* **Regra de Ouro das Políticas Comerciais (*Stub Networks* vs. ISPs):**
  Considere um cliente *multi-homed* $X$ conectado a dois provedores $B$ e $C$. $X$ quer ser alcançado por todos, mas **não quer carregar tráfego de trânsito entre $B$ e $C$**! Como $X$ garante isso usando BGP?
  - **Solução:** $X$ simplesmente **não anuncia para $B$ que possui rota para $C$**, e **não anuncia para $C$ que possui rota para $B$**! (Se $B$ não sabe que $X$ alcança $C$, $B$ nunca enviará tráfego destinado a $C$ através de $X$).
  - Da mesma forma, se um ISP regional $B$ aprende que $C$ alcança $Y$ (rota `BCY`), mas $W$ é cliente apenas de $C$ e não de $B$, $B$ não anuncia `BCY` para $A$ se não quiser carregar tráfego gratuito entre $A$ e $C$!

| Critério | **Roteamento Intra-AS (RIP / OSPF)** | **Roteamento Inter-AS (BGP)** |
| :--- | :--- | :--- |
| **Política (*Policy*)** | Tudo pertence a um único administrador; políticas quase não importam. | **Dominante!** Decisões baseadas em contratos comerciais (quem é cliente vs. *peer*). |
| **Escala (*Scale*)** | Número moderado de roteadores (hierarquia de áreas resolve). | Escala planetária (dezenas de milhares de ASs e centenas de milhares de prefixos). |
| **Desempenho (*Performance*)** | **Foco principal!** Busca caminhos de menor custo técnico (banda/atraso). | Secundário frente às políticas (uma rota mais longa porém mais barata vence). |

---

## 5.5 [Menos Importante] Plano de Controle SDN e Protocolo OpenFlow

> ⚪ **Menos Importante (Não grifado no livro-texto):** As páginas 421 a 433 (Seção 5.5 do livro) não possuem nenhum grifo seu (você pulou direto da Seção 5.4 de BGP na p. 420 para a Seção 5.6 de ICMP na p. 434). Mantido apenas para referência rápida dos slides e do Lab 04.

Um **Controlador SDN** (como ONOS, OpenDaylight ou Ryu/POX) é organizado em **3 camadas internas**:
1. **Camada de Comunicação (*Southbound Interface*):** Protocolo entre o controlador e os dispositivos controlados (ex: **OpenFlow**, SNMP, NETCONF).
2. **Camada de Gerenciamento de Estado em Rede (*Network-Wide State Management*):** Mantém o banco de dados distribuído do estado atualizado de todos os enlaces, switches, hosts e tabelas de fluxo.
3. **Interface para Aplicações de Controle (*Northbound API*):** API REST/Java pela qual **Aplicações de Controle de Rede** (roteamento Dijkstra, engenharia de tráfego, balanceamento de carga, firewall) leem o estado da rede e registram callbacks para eventos.

### Principais Mensagens do Protocolo OpenFlow (TCP porta 6653):
* **Controlador $\to$ Switch:**
  - `Modify-state`: Inclui, exclui ou modifica entradas na Tabela de Fluxo do switch.
  - `Read-state`: Coleta estatísticas e contadores das portas e fluxos do switch.
  - `Send-packet`: Envia um pacote específico por uma porta determinada do switch.
* **Switch $\to$ Controlador:**
  - `Packet-in`: Quando chega um pacote que não casa com nenhuma entrada da Tabela de Fluxo (*table-miss*) ou cuja ação explícita é enviar ao controlador, o switch encapsula o pacote e o envia ao controlador.
  - `Flow-removed`: Informa ao controlador que uma regra de fluxo expirou por *idle timeout* ou *hard timeout*.
  - `Port-status`: Informa ao controlador que uma porta física do switch subiu (*up*) ou caiu (*down*).

---

## 5.6 Protocolo ICMP, Ping e Traceroute

O **ICMP (*Internet Control Message Protocol* — RFC 792)** é usado por hosts e roteadores para comunicar informações da camada de rede (relato de erros e diagnóstico).
* **Arquitetura:** Situa-se logo acima do IP — as mensagens ICMP são transportadas **dentro do payload de datagramas IP** (`Upper-Layer Protocol = 1`).
* **Estrutura:** Possui campos **`Type`** e **`Code`**, além de carregar o **cabeçalho IP e os primeiros 8 bytes do datagrama original** que provocou o erro (os 8 bytes contêm as portas de origem/destino TCP/UDP para que o host emissor saiba qual socket/processo sofreu a falha!).

| Tipo ICMP (`Type`) | Código (`Code`) | Descrição / Aplicação |
| :---: | :---: | :--- |
| **`0`** | **`0`** | **Echo Reply** (Resposta ao Ping) |
| **`3`** | **`0` / `1` / `3`** | **Destination Network / Host / Port Unreachable** (`Code 3` = usado pelo **Traceroute** no destino!) |
| **`8`** | **`0`** | **Echo Request** (Solicitação de Ping) |
| **`11`** | **`0`** | **TTL Expired** (Tempo de vida expirado em trânsito — usado pelo **Traceroute** nos roteadores!) |
| **`12`** | **`0`** |Cabeçalho IP ruim (*Bad IP Header*) |

### Como Funcionam o `Ping` e o `Traceroute`?
* **`Ping`** *(Sua Anotação na p. 434)*: Mede o RTT enviando um datagrama IP contendo **`ICMP Type 8 Code 0` (*Echo Request*)** para o destino, cujo sistema operacional responde diretamente no kernel com um **`ICMP Type 0 Code 0` (*Echo Reply*)**.
* **`Traceroute`:** Descobre todos os roteadores no caminho até o destino:
  1. A origem envia uma série de segmentos **UDP** (ou pacotes ICMP no Windows) para um número de porta **improvável** no destino, configurando o campo `TTL` do cabeçalho IP sequencialmente como $\text{TTL} = 1$, depois $\text{TTL} = 2$, $\text{TTL} = 3$, etc. (enviando 3 sondas para cada valor de TTL).
  2. O $n$-ésimo roteador recebe o datagrama com $\text{TTL} = n$, decrementa o TTL para $0$, descarta o datagrama e devolve à origem uma mensagem **`ICMP Type 11 Code 0` (*TTL Expired*)**, revelando o nome/IP do $n$-ésimo roteador e o RTT até ele!
  3. Quando uma sonda finalmente alcança o **host de destino**, o TTL não expira, mas como a porta UDP escolhida não possui nenhum processo ouvindo, o host de destino devolve um **`ICMP Type 3 Code 3` (*Port Unreachable*)**, sinalizando à origem que o rastreamento terminou!

---

## 5.7 [Menos Importante] Roteamento Broadcast e Multicast (IGMP e Árvores)

> ⚪ **Menos Importante (Não grifado no livro-texto — Apenas nos Slides `parte4-3.pdf`, pp. 59–77):** Tópico ausente na 8ª edição do livro-texto e sem marcações suas.

### 1. Roteamento Broadcast (1 para Todos)
* **Duplicação na Origem ($N$-way Unicast):** Ineficiente; desperdiça banda nos enlaces iniciais e exige que a origem conheça o endereço de todos os destinatários.
* **Inundação Não Controlada (*Uncontrolled Flooding*):** Cada nó duplica e envia o pacote para todos os vizinhos exceto aquele de quem recebeu. **Falha fatal:** Se o grafo tiver ciclos, gera uma **Tempestade de Broadcast (*Broadcast Storm*)** infinita!
* **Inundação Controlada (*Controlled Flooding*):**
  1. **Controlada por Número de Sequência:** Cada nó mantém uma lista de `(Endereço Origem, Nº Sequência Broadcast)` já vistos; se receber duplicata, descarta.
  2. **Encaminhamento pelo Caminho Inverso (*RPF — Reverse Path Forwarding*):** Quando um roteador recebe um pacote de broadcast, ele **só o retransmite** para suas demais interfaces **se o pacote chegou exatamente pela interface que está no seu próprio caminho mais curto de volta para a origem (*unicast shortest path back to source*)**! Caso contrário, descarta.
* **Abordagem por Árvore Geradora (*Spanning Tree*):** Constrói-se primeiro uma árvore sem ciclos que conecta todos os nós (ex: elegendo um *Center Node / Rendezvous Point* pelo qual os nós enviam mensagens `unicast tree-join` até bater na árvore). Os pacotes broadcast trafegam apenas pelas arestas da *Spanning Tree* (custo mínimo e zero pacotes duplicados!).

### 2. Roteamento Multicast (1 para um Grupo de Interesse)
* **Protocolo IGMP (*Internet Group Management Protocol*):** Opera **localmente** entre um host e seu roteador de primeiro salto para que o host informe que deseja participar de um grupo multicast (identificado por um endereço IP Classe D de 32 bits: `224.0.0.0` a `239.255.255.255`). Mensagens: `membership_query`, `membership_report`, `leave_group`.
* **Árvores de Roteamento Multicast (entre roteadores):**
  - **Árvore Baseada na Fonte (*Source-Based Tree*):** Constrói uma árvore de caminhos mais curtos específica para cada origem usando **RPF (*Reverse Path Forwarding*) + Poda (*Pruning*)** (roteadores de folha que não têm hosts interessados no grupo enviam mensagens `prune` a montante para cortar o galho; usado no protocolo **DVMRP**).
  - **Árvore Compartilhada (*Group-Shared Tree*):** Uma única árvore compartilhada por todas as fontes do grupo, construída em torno de um roteador central (*Center-Based Tree* / *Rendezvous Point*).

---

# Capítulo 6: Camada de Enlace e Redes Locais (LANs)

## 6.1 Serviços da Camada de Enlace e Implementação em Hardware (NIC)

* **Terminologia:** Qualquer dispositivo que executa protocolos de camada 2 (hosts, roteadores, switches, Access Points WiFi) é um **nó (*node*)**; os canais de comunicação que conectam nós adjacentes são **enlaces (*links*)**; e a unidade de dados da camada 2 (que encapsula o datagrama IP) é o **quadro (*frame*)**.
* **Dois Tipos de Enlaces:**
  1. **Enlaces Ponto-a-Ponto (*Point-to-Point*):** Um único emissor em uma ponta e um único receptor na outra (ex: PPP, HDLC, Ethernet comutada full-duplex).
  2. **Enlaces de Difusão (*Broadcast Links*):** Múltiplos nós compartilham o mesmo meio de transmissão (ex: Ethernet clássica em barramento/hub, WiFi 802.11, HFC DOCSIS). Exigem um **Protocolo de Acesso Múltiplo (MAC)** para coordenar as transmissões.

### Principais Serviços da Camada de Enlace:
1. **Enquadramento (*Framing*):** Encapsular o datagrama da camada de rede dentro de um quadro de enlace, adicionando cabeçalho e trailer.
2. **Acesso ao Enlace (*Link Access / MAC*):** Definir as regras pelas quais os nós transmitem quadros no meio compartilhado.
3. **Entrega Confiável (*Reliable Delivery*):** Garantir que cada datagrama atravesse o enlace sem perdas via ACKs e retransmissões. **Onde é usada?** Frequente em enlaces com alta taxa de erro como **redes sem fio (WiFi 802.11)**, pois corrigir localmente no enlace sem fio é muito mais rápido do que esperar um *timeout* fim-a-fim do TCP; mas **desnecessária (não usada)** em enlaces de baixa taxa de erro como fibra óptica, coaxial e par trançado (Ethernet)!
4. **Detecção e Correção de Erros (*Error Detection and Correction*):** Identificar (e opcionalmente corrigir) bits invertidos por ruído ou atenuação eletromagnética.

### Onde a Camada de Enlace é Implementada?
Na **Placa de Rede (*Network Interface Controller — NIC* / Adaptador de Rede)**, conectada ao barramento de I/O (PCIe) do host.
* A maior parte da camada de enlace (enquadramento, protocolo MAC, geração/verificação de CRC) e toda a camada física são implementadas diretamente em **hardware dedicado no chip da NIC**, enquanto a parte superior da camada de enlace (montagem de endereços, interação com a camada de rede e tratamento de interrupções) roda em **software no driver da CPU**.

---

## 6.2 Detecção e Correção de Erros: Paridade 1D/2D, Checksum e CRC

No nó emissor, aos $D$ bits de dados são adicionados $EDC$ bits de redundância (*Error-Detection and -Correction bits*). Nenhuma técnica é $100\%$ infalível (sempre existe uma pequena probabilidade de **erros não detectados** se o padrão de ruído transformar um quadro válido exatamente em outro quadro válido).

### 1. Verificação de Paridade (*Parity Checks*)
* **Paridade de 1 Único Bit (1D):** Inclui 1 bit extra de modo que o número total de bits `1` em $D + \text{bit de paridade}$ seja **par** (*paridade par*) ou **ímpar** (*paridade ímpar*).
  - Detecta qualquer número **ímpar** de erros de bit, mas falha completamente se ocorrer um número **par** de inversões de bits (ex: 2 bits invertidos em uma rajada de ruído).
* **Paridade Bidimensional (2D):** Os $d$ bits de dados são organizados em uma matriz de $i$ linhas por $j$ colunas. Calcula-se 1 bit de paridade para cada linha e 1 bit de paridade para cada coluna.

```
Paridade Bidimensional (Par): Detecta E Corrige 1 erro de bit!
   1  0  1  0  1  | 1
   1  1  1  1  0  | 0
   0  1  (0->1)1  0 | 0  <-- Erro na Linha 3! (Soma ficou ímpar)
   ---------------+--
   0  0  0  0  1  | 1
         ^
         +-- Erro na Coluna 3! (Cruzando Linha 3 x Coluna 3, sabemos exatamente qual bit inverter de volta!)
```

* **Propriedades da Paridade 2D:**
  - **Detecta E corrige** qualquer erro de **1 único bit** (cruzando o índice da linha e da coluna com erro).
  - **Detecta** (mas não corrige) qualquer combinação de **2 ou 3 erros** de bit em qualquer posição da matriz!
  - Capacidade do receptor de detectar e corrigir erros sem pedir retransmissão chama-se **FEC (*Forward Error Correction*)**.

---

### 2. Verificação de Redundância Cíclica (*CRC — Cyclic Redundancy Check*)
Técnica de códigos polinomiais usada em redes Ethernet e WiFi (tipicamente com polinômios de 32 bits — **CRC-32**).
* **Ideia Matemática:**
  - Dados $D$ vistos como um número binário de $d$ bits.
  - Emissor e receptor concordam previamente sobre um **Polinômio Gerador $G$** de **$r + 1$ bits** (cujo bit mais significativo MSB é obrigatoriamente `1`).
  - O emissor calcula **$r$ bits adicionais $R$** (chamados bits de CRC) e os anexa ao final de $D$, transmitindo os $d + r$ bits ($D \cdot 2^r \oplus R$), de modo que o padrão transmitido seja **exatamente divisível por $G$ em aritmética módulo-2 (XOR)**.
  - O receptor divide os $d + r$ bits recebidos por $G$: se o **resto for diferente de zero**, houve erro! Se for zero, o quadro é aceito.

> 📝 **Sua Anotação no Livro (p. 471 — Fórmula de Construção do CRC):**  
> *"Afirmação: Para construir $R$, podemos usar o resto da divisão de $D \cdot 2^r$ por $G$. Assim, $D \cdot 2^r \oplus R$ vai ser divisível por $G$, como deve ser verificado pelo receptor."*  
> Como na aritmética módulo-2 adição e subtração são idênticas à operação **XOR ($\oplus$)** (sem *carry* e sem *borrow*):
> $$D \cdot 2^r \oplus R = n \cdot G \iff D \cdot 2^r = n \cdot G \oplus R \implies \mathbf{R = \text{resto}\left(\frac{D \cdot 2^r}{G}\right)}$$

#### Exemplo Numérico Completo da Página 471 do Livro:
Dados $D = \mathbf{101110}$ ($d = 6\text{ bits}$), Gerador $G = \mathbf{1001}$ ($r+1 = 4\text{ bits} \implies r = 3\text{ bits de CRC}$).
1. Deslocamos $D$ em $r = 3$ bits para a esquerda (anexando três zeros): $D \cdot 2^3 = \mathbf{101110\,000}$.
2. Dividimos $101110000$ por $1001$ usando subtração **XOR** bit a bit:

```
Divisão em Aritmética Módulo-2 (XOR):
        101011   <-- Quociente (descartado)
      ---------
1001 | 101110000
       1001|||||  <-- XOR com G (pois começa com 1)
       ----vvvvv
        01010|||
        00000|||  <-- XOR com 0000 (pois começa com 0)
        -----vvv
         10100||
         10010||  <-- XOR com G
         -----vv
          01100|
          00000|  <-- XOR com 0000
          -----v
           11000
           10010  <-- XOR com G
           -----
            1010
            1001  <-- XOR com G
            ----
             011  <-- RESTO R = 011 (3 bits!)
```
3. Quadro transmitido pelo emissor ($D$ seguido de $R$): **`101110 011`** ($9\text{ bits}$).

---

## 6.3 Protocolos de Acesso Múltiplo (MAC): Particionamento, ALOHA, CSMA/CD, Revezamento e DOCSIS

Quando múltiplos nós compartilham um canal de difusão (*broadcast*) de taxa $R\text{ bps}$, se dois ou mais nós transmitirem quadros simultaneamente, os sinais se sobrepõem ocorrendo uma **colisão** (todos os quadros colididos são perdidos).

### Propriedades de um Protocolo MAC Ideal (para canal de taxa $R$ bps):
1. Quando apenas $1$ nó tem dados para enviar, ele transmite à taxa total $R\text{ bps}$.
2. Quando $M$ nós têm dados para enviar, cada um obtém vazão média de $\frac{R}{M}\text{ bps}$.
3. O protocolo é totalmente **descentralizado** (sem nó mestre nem relógio global que possa falhar).
4. O protocolo é simples e barato de implementar.

---

### Classe 1: Protocolos de Particionamento de Canal (*Channel Partitioning*)
* **TDMA (*Time-Division Multiple Access*):** O tempo é dividido em **quadros de tempo (*time frames*)**, e cada quadro é subdividido em $N$ **slots de tempo**, com 1 slot fixo atribuído a cada um dos $N$ nós.
  - *Prós:* Elimina totalmente colisões e é perfeitamente justo.
  - *Contras:* Um nó fica sempre limitado à taxa média $\frac{R}{N}\text{ bps}$ e precisa esperar sua vez no ciclo **mesmo quando é o único nó com pacotes para enviar!**
* **FDMA (*Frequency-Division Multiple Access*):** Divide o canal de $R\text{ bps}$ em $N$ faixas de frequência diferentes, cada uma com largura de banda $\frac{R}{N}$. Possui as mesmas vantagens e desvantagens do TDMA.
* **CDMA (*Code-Division Multiple Access*):** Atribui um **código único ortogonal** a cada nó. Permite que múltiplos nós transmitam **simultaneamente em toda a faixa de frequência e em todo o tempo**, desde que os receptores separem os sinais multiplicando pelo código do emissor desejado (muito usado em redes celulares e sem fio).

---

### Classe 2: Protocolos de Acesso Aleatório (*Random Access*)
Um nó com dados transmite sempre na **taxa total do canal $R\text{ bps}$**; se houver colisão, cada nó envolvido aguarda um **atraso aleatório independente** antes de retransmitir.

#### 1. Slotted ALOHA vs. Pure ALOHA
* **Slotted ALOHA:**
  - *Premissas:* Quadros têm tamanho fixo $L$ bits (tempo de transmissão $= \frac{L}{R} = 1\text{ slot}$); nós são sincronizados para iniciar transmissões **apenas no início de um slot**; se houver colisão, todos detectam antes do fim do slot.
  - Se houver colisão, o nó retransmite em cada slot subsequente com probabilidade independente $p$ até ter sucesso.
  - **Probabilidade de um nó específico ter sucesso em um slot** (ele transmite com prob. $p$ e os outros $N-1$ nós não transmitem com prob. $(1-p)^{N-1}$):
    $$P(\text{sucesso de 1 nó específico}) = p \cdot (1 - p)^{N-1}$$
  - **Probabilidade de QUALQUER um dos $N$ nós ter sucesso no slot (Eficiência):**
    $$P(\text{sucesso de algum nó}) = N \cdot p \cdot (1 - p)^{N-1}$$
  - Derivando em relação a $p$ para maximizar, obtém-se $p^* = \frac{1}{N}$. Tomando o limite quando $N \to \infty$:
    $$\text{Eficiência Máxima (Slotted ALOHA)} = \lim_{N \to \infty} N \cdot \frac{1}{N}\left(1 - \frac{1}{N}\right)^{N-1} = \mathbf{\frac{1}{e} \approx 0{,}37 \quad (37\%)}$$

* **Pure ALOHA (ALOHA Puro — Não-Slotted):**
  - Sem sincronização de relógio: assim que um quadro chega da camada de rede, o nó transmite imediatamente.
  - Para um quadro transmitido em $t_0$ (de duração unitária $1$) não sofrer colisão, **nenhum outro nó pode iniciar uma transmissão no intervalo $[t_0 - 1, t_0 + 1]$** (janela de vulnerabilidade de tamanho **$2$ slots**!):
    $$P(\text{sucesso de algum nó no Pure ALOHA}) = N \cdot p \cdot (1 - p)^{2(N-1)} \implies \text{Eficiência Máxima} = \mathbf{\frac{1}{2e} \approx 0{,}18 \quad (18\%)}$$

> 🎯 **Resolução do Exercício do Slide 105 (`Semana 13/parte5.pdf`):**  
> **Enunciado:** *Quatro nós ativos ($A, B, C, D$, logo $N=4$) competem por um canal usando **Slotted ALOHA**, tentando transmitir em cada slot com probabilidade $p$.*  
> * **Seja $p_{\text{A}} = p(1-p)^3$** a probabilidade de o nó $A$ ter sucesso em um determinado slot, e **$p_{\text{any}} = 4p(1-p)^3$** a probabilidade de *algum* dos 4 nós ter sucesso em um slot.  
> * **a) Probabilidade de o nó $A$ ter sucesso pela primeira vez no slot 5:**  
>   O nó $A$ deve falhar nos slots 1, 2, 3 e 4 e ter sucesso no slot 5:  
>   $$P = \big(1 - p(1-p)^3\big)^4 \cdot p(1-p)^3$$  
> * **b) Probabilidade de que algum nó ($A, B, C$ ou $D$) tenha sucesso no slot 4:**  
>   Como os slots são independentes, é simplesmente a probabilidade de sucesso de qualquer um dos 4 nós em um único slot:  
>   $$P = \mathbf{4p(1-p)^3}$$  
> * **c) Probabilidade de que o primeiro sucesso de qualquer nó ocorra no slot 3:**  
>   Nenhum nó tem sucesso nos slots 1 e 2, e algum nó tem sucesso no slot 3:  
>   $$P = \big(1 - 4p(1-p)^3\big)^2 \cdot 4p(1-p)^3$$

---

#### 2. CSMA e CSMA/CD (*Carrier Sense Multiple Access with Collision Detection*)
* **duas Regras de Ouro da Conversa Humana no CSMA/CD:**
  1. **Detecção de Portadora (*Carrier Sensing — CSMA*):** *"Ouça antes de falar"*. Se o canal estiver ocupado, aguarde até ficar ocioso. *(Variações nos slides: **1-persistente** transmite imediatamente ao ficar livre; **não-persistente** aguarda tempo aleatório antes de ouvir de novo; **$p$-persistente** em canais slotted transmite com prob. $p$ quando livre)*.
  2. **Detecção de Colisão (*Collision Detection — CSMA/CD*):** *"Ouça enquanto fala; se outra pessoa começar a falar junto, pare de falar imediatamente!"* Abortar um quadro corrompido logo no início (enviando um sinal de reforço de colisão de 48 bits chamado **Jam Signal**) economiza o tempo que seria desperdiçado transmitindo o restante do quadro inútil.
* **Por que ainda ocorrem colisões se todos "ouvem antes de falar" no CSMA?**
  Por causa do **Atraso de Propagação Finito ($d_{\text{prop}}$)**! Se o nó $B$ começa a transmitir no instante $t_0$, a energia eletromagnética do seu sinal leva um tempo $d_{\text{prop}} = \frac{d}{s}$ para chegar ao nó $D$. Se no instante $t_1 < t_0 + d_{\text{prop}}$ o nó $D$ escutar o canal, ele o sentirá **falsamente ocioso** e começará a transmitir, gerando colisão!

* **Algoritmo de Recuo Exponencial Binário (*Binary Exponential Backoff*) do Ethernet:**
  Após um adaptador sofrer a **$m$-ésima colisão consecutiva** ao tentar transmitir um mesmo quadro:
  1. Define $n = \min(m, 10)$ (congela o expoente em $10$ para $m \ge 10$; após 16 tentativas sem sucesso, descarta o quadro).
  2. Sorteia um número inteiro $K$ com igual probabilidade no conjunto discreto de **$2^n$ valores**:
     $$K \in \{0, 1, 2, \dots, 2^n - 1\}$$
  3. Aguarda um tempo igual a **$K \times 512\text{ tempos de bit}$** (isto é, $\frac{K \times 512}{R}$ segundos) antes de voltar a escutar o canal!

> 🎯 **Resolução do Exercício do Slide 104 (`Semana 13/parte5.pdf`):**  
> **Enunciado:** *Em CSMA/CD, após a **5ª colisão** ($m = 5$), qual a probabilidade de que um nó escolha $K = 4$? O resultado $K = 4$ corresponde a um atraso de quantos segundos em uma rede Ethernet de $10\text{ Mbps}$?*  
> * **1. Probabilidade de escolher $K = 4$:**  
>   Para $m = 5$, o conjunto de sorteio é $\{0, 1, 2, \dots, 2^5 - 1\} = \{0, 1, \dots, 31\}$, que possui $2^5 = \mathbf{32}$ valores equiprováveis. Logo:
>   $$P(K = 4) = \mathbf{\frac{1}{32} = 0{,}03125 \quad (3{,}125\%)}$$
> * **2. Tempo de atraso em Ethernet de $R = 10\text{ Mbps} = 10^7\text{ bps}$:**  
>   Cada unidade de $K$ equivale a $512\text{ tempos de bit}$. Para $K = 4$, o nó aguarda $4 \times 512 = 2048\text{ bits}$:
>   $$t_{\text{backoff}} = \frac{4 \times 512\text{ bits}}{10^7\text{ bps}} = \frac{2048}{10^7}\text{ s} = \mathbf{204{,}8\ \mu\text{s}} \quad (0{,}0002048\text{ segundos})$$

* **Eficiência do CSMA/CD:**
  $$\text{Eficiência}_{\text{CSMA/CD}} = \frac{1}{1 + 5 \cdot \frac{d_{\text{prop}}}{d_{\text{trans}}}}$$
  - Quando $d_{\text{prop}} \to 0$ (nós muito próximos) ou $d_{\text{trans}} \to \infty$ (quadros longos), a **eficiência tende a $1$ ($100\%$)**!

---

### Classe 3: Protocolos de Revezamento (*Taking-Turns*)
Buscam atingir $\text{vazão} = R$ quando apenas 1 nó está ativo e $\frac{R}{M}$ quando $M$ estão ativos, sem colisões:
1. **Protocolo de Sondagem (*Polling*):** Um **nó mestre** convida cada nó escravo em sequência circular a transmitir até um número máximo de quadros (ex: Bluetooth).
   - *Desvantagens:* Introduz **atraso de sondagem (*polling delay*)** ao consultar nós inativos; e **Ponto Único de Falha** (se o mestre cair, o canal inteiro para de funcionar!).
2. **Passagem de Permissão (*Token Passing*):** Não há mestre; um quadro especial pequeno chamado **Token (Ficha)** circula entre os nós em uma ordem lógica fixa ($1 \to 2 \to \dots \to N \to 1$, ex: Token Ring IEEE 802.5, FDDI). Quem não tem quadros passa o token imediatamente; quem tem transmite e depois passa o token adiante.
   - *Desvantagens:* A falha de **um único nó** (ou placa de rede) no anel pode interromper todo o canal; se um nó esquecer de liberar o token ou o token se perder por ruído, é necessário invocar procedimentos complexos de eleição/recuperação.

---

### Estudo de Caso Síntese: DOCSIS (Redes de Acesso a Cabo HFC)
O protocolo **DOCSIS (*Data-Over-Cable Service Interface Specification*)** conecta milhares de *cable modems* residenciais ao **CMTS (*Cable Modem Termination System*)** na central a cabo, combinando **TODAS as 3 classes de protocolos MAC** ao mesmo tempo:

> 📝 **Suas Anotações no Livro (pp. 486 e 488):**  
> * **Modem:** *"Modulador/demodulador que fica nas extremidades do cabo com a finalidade de codificar e decodificar os sinais que transitam no cabo."*  
> * **Como o DOCSIS combina FDM + TDM + Acesso Aleatório + Alocação Centralizada:**  
>   1. **FDM:** Divide o cabo em canal **Downstream** (CMTS $\to$ modems: apenas 1 transmissor, logo **não há problema de acesso múltiplo nem colisão no downstream!**) e múltiplos canais **Upstream** (modems $\to$ CMTS: compartilhado, sujeito a colisões).  
>   2. **TDM no Upstream:** O canal upstream é dividido em intervalos de tempo chamados ***mini-slots***.  
>   3. **Revezamento / Alocação Centralizada (para dados):** O CMTS envia quadros de controle **MAP** no downstream especificando qual *cable modem* tem permissão exclusiva para transmitir dados em cada *mini-slot* futuro (os slots de dados alocados **nunca sofrem colisão**!).  
>   4. **Acesso Aleatório com Backoff Binário (para pedir *mini-slots*):** Para pedir espaço ao CMTS, os modems enviam quadros de requisição dentro de um subconjunto especial de *mini-slots* dedicados a requisições. Se duas requisições colidirem, o modem não vê a alocação no próximo MAP, deduz que houve colisão e usa **recuo exponencial binário**.  
>   5. **Detalhe Crucial (Sua Anotação na p. 488):** *"Esse tempo [de backoff] é contado em unidades de **minislots ou oportunidades de transmissão**. Portanto, se o backoff terminar em um instante em que não existe um minislot reservado para requisições, o modem simplesmente aguarda a próxima oportunidade válida."*

---

## 6.4 Endereçamento MAC e o Protocolo ARP (Mesma LAN vs. Outra LAN)

### 1. Endereçamento MAC (Camada 2) vs. Endereçamento IP (Camada 3)
* Todo adaptador de rede (*interface*) possui um **Endereço MAC (*Media Access Control* / Endereço de LAN / Endereço Físico)** de **48 bits (6 bytes)**, expresso em notação hexadecimal de 12 dígitos (ex: `1A-2F-BB-76-09-AD`), gravado em ROM na fabricação sob gestão do IEEE ($2^{48}$ endereços).
* **Por que precisamos de endereços MAC na camada 2 se já temos endereços IP na camada 3?**
  1. LANs foram projetadas para suportar **qualquer protocolo de camada 3** (não apenas IPv4, mas IPv6, IPX, etc.).
  2. Se os adaptadores usassem endereços IP, o endereço precisaria ser regravado na NIC sempre que o notebook se movesse para outra sub-rede; ou, alternativamente, a NIC teria de interromper a CPU do sistema operacional a **cada quadro que passasse na LAN** para verificar o IP! Com o MAC em hardware na NIC, ela filtra silenciosamente todos os quadros não destinados a ela sem acordar a CPU.
* **Analogia de Kurose & Ross:**
  - **Endereço MAC = CPF / Identidade Nacional (Espaço Plano):** É permanente e viaja junto com a placa de rede para qualquer lugar do mundo.
  - **Endereço IP = Endereço Postal / CEP (Espaço Hierárquico):** Muda sempre que o dispositivo muda de localização (sub-rede).
* **Detalhe Crucial (Destaque na p. 489 do Livro):** **Switches de camada de enlace NÃO possuem endereços MAC** associados às suas interfaces que conectam hosts e roteadores! Isso ocorre porque o switch é **transparente**: os hosts e roteadores nunca endereçam um quadro para o switch, mas sim diretamente para o MAC do host ou roteador de destino.
* **Endereço de Broadcast MAC:** **`FF-FF-FF-FF-FF-FF`** ($48$ bits consecutivos iguais a `1` — todos os adaptadores da LAN recebem e repassam o quadro para a camada superior).

---

### 2. Protocolo ARP (*Address Resolution Protocol* — RFC 826)
Traduz um **endereço IP** para o **endereço MAC correspondente**, mas **APENAS para nós que residem na MESMA sub-rede (mesma LAN)**!
* Cada host e roteador mantém em memória uma **Tabela ARP** com entradas no formato:
  $$\langle \text{Endereço IP}\ ;\ \text{Endereço MAC}\ ;\ \text{TTL (tipicamente 20 minutos)} \rangle$$
* **Funcionamento do ARP (Quando o IP de destino não está na Tabela ARP):**
  1. O nó emissor constrói um **Pacote de Consulta ARP (*ARP Query*)** perguntando *"Quem possui o IP X.X.X.X?"* e o encapsula em um quadro Ethernet com destino **Broadcast (`FF-FF-FF-FF-FF-FF`)** e `Type = 0x0806`.
  2. Todos os adaptadores da sub-rede recebem o quadro broadcast e o repassam ao seu módulo ARP, mas **apenas o nó que possui o IP consultado** responde.
  3. O dono do IP envia de volta um **Quadro de Resposta ARP (*ARP Reply*)** em **Unicast** diretamente para o MAC do solicitante. O solicitante atualiza sua Tabela ARP e envia o datagrama IP!
* *Observação:* O ARP é *plug-and-play* (tabelas construídas automaticamente) e situa-se na fronteira entre as camadas 2 e 3 (mensagens ARP são encapsuladas diretamente dentro de quadros Ethernet, com `Type = 0x0806`).

---

### 3. Caminhamento de um Datagrama para FORA da Sub-rede (Ponto Clássico de Prova!)
Suponha que o Host `A` (`111.111.111.111`, MAC `74-29-9C-E8-FF-55`) na Sub-rede 1 queira enviar um datagrama IP para o Host `B` (`222.222.222.222`, MAC `49-BD-D2-C7-56-2A`) na Sub-rede 2, passando pelo Roteador `R` (Interface 1: IP `111.111.111.110`, MAC `E6-E9-00-17-BB-4B` | Interface 2: IP `222.222.222.220`, MAC `1A-23-F9-CD-06-9B`).

```
Reescrita de Endereços MAC Salto a Salto (Enquanto o IP Fim-a-Fim NÃO MUDA!):
   [Host A] ----------------(Sub-rede 1)---------------> [Roteador R] ----------------(Sub-rede 2)---------------> [Host B]
IP: 111.111.111.111                             Int.1: 111.111.111.110 | Int.2: 222.222.222.220              IP: 222.222.222.222
MAC: 74-29-9C-E8-FF-55                          MAC1: E6-E9-00-17-BB-4B| MAC2: 1A-23-F9-CD-06-9B             MAC: 49-BD-D2-C7-56-2A

   Quadro na Sub-rede 1:                                                 Quadro na Sub-rede 2:
   +-----------------------------------+                                 +-----------------------------------+
   | IP Orig: 111.111.111.111 (Host A) |                                 | IP Orig: 111.111.111.111 (Host A) | <-- NÃO MUDA!
   | IP Dest: 222.222.222.222 (Host B) |                                 | IP Dest: 222.222.222.222 (Host B) | <-- NÃO MUDA!
   +-----------------------------------+                                 +-----------------------------------+
   | MAC Orig: 74-29-9C-E8-FF-55 (A)   |                                 | MAC Orig: 1A-23-F9-CD-06-9B (R2)  | <-- MUDOU!
   | MAC Dest: E6-E9-00-17-BB-4B (R1!) |                                 | MAC Dest: 49-BD-D2-C7-56-2A (B!)  | <-- MUDOU!
   +-----------------------------------+                                 +-----------------------------------+
```

> ⚠️ **Pegadinha Clássica de Prova:**  
> `A` **NUNCA** faz ARP perguntando pelo MAC de `B` (pois `B` está em outra sub-rede e o broadcast ARP não atravessa roteadores)!  
> Em vez disso, `A` consulta sua tabela de repasse, vê que o gateway padrão é a interface `R1` (`111.111.111.110`), usa **ARP na Sub-rede 1 para descobrir o MAC de `R1`** (`E6-E9-00-17-BB-4B`), e coloca no quadro Ethernet:  
> * **IP Destino = IP de `B`** (`222.222.222.222`), mas **MAC Destino = MAC do Roteador `R1`** (`E6-E9-00-17-BB-4B`)!

---

## 6.5 Ethernet (IEEE 802.3), Switches Autoaprendizes e VLANs (802.1Q)

### 1. Estrutura do Quadro Ethernet (IEEE 802.3)

```
Quadro Ethernet (Tamanho do Payload de 46 a 1500 bytes -> Quadro de 64 a 1518 bytes s/ Preâmbulo):
+------------------+------------------+------------------+----------+-----------------------+----------+
|    Preâmbulo     |   MAC Destino    |    MAC Origem    |   Tipo   |     Dados (Payload)   |   CRC    |
|     (8 bytes)    |    (6 bytes)     |    (6 bytes)     | (2 bytes)|   (46 a 1500 bytes)   | (4 bytes)|
+------------------+------------------+------------------+----------+-----------------------+----------+
 7x (10101010) + SFD                                       0x0800=IP   Se < 46B, preenche     Detecção
    (10101011)                                             0x0806=ARP  com stuffing (pad)!    CRC-32
```

* **Preâmbulo (8 bytes):** Os primeiros 7 bytes têm valor `10101010` para "acordar" os adaptadores receptores e **sincronizar seus relógios** com o relógio do transmissor (compensando desvios de frequência); o 8º byte (`10101011`) termina com dois bits `11` consecutivos (*Start of Frame Delimiter*) avisando que o cabeçalho real vai começar!
* **Tamanho Mínimo dos Dados (46 bytes $\implies$ Quadro mínimo de 64 bytes sem preâmbulo = 512 bits):** Se o datagrama IP tiver menos de 46 bytes, o emissor preenche (*stuffing/padding*) até completar 46 bytes (a camada de rede no destino usa o campo `Comprimento Total` do cabeçalho IP para remover o preenchimento!). Esse tamanho mínimo de 512 bits garante que, no CSMA/CD, o transmissor ainda esteja transmitindo quando o sinal de uma colisão na outra ponta da LAN retornar!
* **Serviço Ethernet:** **Sem Conexão** *(Sua anotação na p. 498: "Não precisa de handshake como TCP para começar")* e **Não Confiável** (o adaptador receptor **não envia ACK nem NAK**; se o quadro falhar no CRC, ele é descartado em silêncio e cabe ao TCP recuperar).

---

### 2. Comutadores de Camada de Enlace (*Switches*) vs. *Hubs* e Roteadores
* **Hubs (Repetidores de Camada 1 — Física):** Dispositivos "burros" que apenas amplificam e replicam cada bit recebido em uma porta para todas as demais portas. Todos os hosts conectados a um hub pertencem ao **mesmo domínio de colisão** e dividem a banda total.
* **Switches (Comutadores de Camada 2 — Enlace):**
  - Operam sobre quadros Ethernet (até a camada 2), realizando **Filtragem** (decidir se um quadro deve ser descartado ou encaminhado) e **Repasse (*Forwarding*)** para a porta de saída específica.
  - **Eliminam colisões:** Em uma LAN comutada moderna (topologia em estrela com cabos de par trançado *full-duplex*), cada porta do switch é um enlace ponto-a-ponto dedicado e **não existe colisão (não se usa CSMA/CD em links full-duplex com switch!)**.
  - São **transparentes (invisíveis)** para os hosts e roteadores: os nós enviam quadros endereçados ao MAC final sem saber que existem switches no caminho.
  - **Vantagens Adicionais Destacadas no Livro (pp. 505–506):**
    - **Enlaces Heterogêneos:** Como o switch isola os enlaces, diferentes portas podem operar em velocidades e meios distintos ($10\text{ Mbps}$, $100\text{ Mbps}$, $1\text{ Gbps}$, cobre ou fibra) simultaneamente.
    - **Gerenciamento (*Jabbering Adapter*):** Se uma placa de rede defeituosa enviar um fluxo interminável de quadros (*jabbering adapter*), o switch detecta e desconecta internamente apenas aquela porta, sem derrubar a LAN inteira.
    - **Ataque de Envenenamento de Switch (*Switch Poisoning / MAC Flooding* — p. 506):** Um invasor envia milhares de quadros com endereços MAC de origem falsos (*bogus source MACs*) para lotar a Tabela de Comutação do switch. Sem espaço para aprender MACs legítimos, o switch passa a fazer *broadcast (flooding)* de todos os quadros, permitindo que o atacante capture tráfego alheio (*sniffing*).

#### Algoritmo de Filtragem, Repasse e Autoaprendizagem (*Self-Learning*) do Switch:
Quando um quadro com **MAC de origem $S$** e **MAC de destino $D$** chega ao switch pela **interface $x$**:
1. **Autoaprendizagem (*Self-Learning* — Olha sempre o MAC de ORIGEM $S$!):** O switch registra na sua **Tabela de Comutação (*Switch Table*)** a tupla `(MAC S, Interface x, Timestamp atual)`. Assim, o switch aprende que o nó $S$ reside na direção da porta $x$!
2. **Filtragem / Repasse (Olha o MAC de DESTINO $D$):**
   - **Caso 1 (`D` não está na tabela — desconhecido, ou é Broadcast):** O switch faz **Inundação (*Flooding*)**, enviando cópias do quadro para **todas as interfaces de saída exceto a interface de chegada $x$**.
   - **Caso 2 (`D` está associado à própria interface de chegada $x$):** O switch **filtra (descarta)** o quadro, pois o destinatário já recebeu o quadro no mesmo segmento de LAN sem precisar cruzar o switch.
   - **Caso 3 (`D` está associado a outra interface $y \ne x$):** O switch encaminha o quadro **unicamente para a interface $y$**.
3. **Expiração (*Aging Time*):** Se nenhum quadro tiver determinado endereço como MAC de origem durante o *aging time* (ex: 60 min), o switch apaga a entrada da tabela.

> 📝 **Sua Anotação Crucial no Livro (p. 504 — Armadilha do *Aging Time*):**  
> *"Não matamos as linhas em que `destination` parou de chegar. É possível que um computador seja desconectado da LAN e continue recebendo mensagens, ocupando desnecessariamente os switches."*  
> **Por quê?** Porque a tabela do switch atualiza e expira entradas olhando apenas para o **MAC de ORIGEM**! Se o host `B` for desligado ou desconectado da porta 2, mas antes disso a entrada `(MAC_B, Porta 2)` estava ativa, qualquer quadro enviado por `A` para `MAC_B` continuará sendo encaminhado pelo switch para a porta 2 vazia até que o *aging time* da entrada de `MAC_B` finalmente expire!

---

### 3. [Menos Importante] VLANs (*Virtual Local Area Networks* — Padrão IEEE 802.1Q)

> ⚪ **Menos Importante (Não grifado no livro-texto):** No Capítulo 6, suas marcações de Switches vão até a página 508 (comparativo Switches vs. Roteadores), parando no título da Seção 6.4.4 (VLANs).
Uma única LAN comutada grande apresenta **3 limitações**:
1. **Falta de isolamento de tráfego de broadcast:** Qualquer quadro broadcast (ARP, DHCP ou destino desconhecido) inunda a instituição inteira.
2. **Ineficiência de switches:** Se um grupo tem apenas 10 pessoas espalhadas em 10 prédios, o tráfego delas precisa cruzar toda a árvore.
3. **Gerenciamento de usuários:** Se um funcionário muda de sala física, seria preciso refazer o cabeamento físico para mantê-lo no switch do seu departamento.

* **Solução — VLANs Baseadas em Porta:** As portas de um switch físico são divididas em grupos por software (ex: Portas 2–8 = VLAN Engenharia Elétrica; Portas 9–15 = VLAN Ciência da Computação). Cada VLAN constitui seu próprio **domínio de broadcast isolado**; quadros entre VLANs diferentes precisam passar obrigatoriamente por um **roteador Layer 3**!
* **Entroncamento de VLAN (*VLAN Trunking* — IEEE 802.1Q):**
  Para interconectar múltiplos switches que possuem portas da mesma VLAN usando **um único cabo físico compartilhado (*Trunk Port*)**, o switch emissor insere uma **Tag 802.1Q de 4 bytes** dentro do cabeçalho Ethernet (e o switch receptor remove a tag antes de entregar ao host):

```
Quadro Ethernet com Tag VLAN IEEE 802.1Q (+4 bytes no cabeçalho + Recálculo do CRC):
+--------------+-------------+-------------+----------------------------+------+---------+-----+
|  Preâmbulo   | MAC Destino | MAC Origem  |    Tag 802.1Q (4 bytes)    | Tipo |  Dados  | CRC |
|   (8 bytes)  |  (6 bytes)  |  (6 bytes)  | TPID (2B) | Controle (2B)  | (2B) |         | (4B)|
+--------------+-------------+-------------+-----------+----------------+------+---------+-----+
                                             0x8100     VLAN ID (12b) +           Recalculado!
                                                        Prioridade (3b)
```

---

## 6.6 [Menos Importante] Enlaces Ponto-a-Ponto (PPP / Byte Stuffing), MPLS e Redes de Data Center

> ⚪ **Menos Importante (Não grifado no livro-texto):** Você não grifou as Seções 6.5 (MPLS) e 6.6 (Data Centers) no livro (páginas 513 a 522), e o protocolo PPP consta apenas nos slides `parte5.pdf` (pp. 79–86). Você pulou direto da página 508 para a Seção 6.7 na página 523.

### 1. Protocolo Ponto-a-Ponto (PPP) e *Byte Stuffing* (Slides `parte5.pdf` pp. 79–86)
Em enlaces ponto-a-ponto (1 emissor e 1 receptor, sem necessidade de protocolo MAC nem endereços MAC), o **PPP (RFC 1661)** delimita o início e o fim de cada quadro usando um **byte de Flag fixo: `01111110` (`0x7E`)**.
* **Problema da Transparência de Dados:** E se o próprio padrão de bits `01111110` (`0x7E`) aparecer por coincidência dentro dos dados da aplicação/IP? O receptor acharia erroneamente que o quadro terminou!
* **Solução — Preenchimento de Bytes (*Byte Stuffing*):**
  - Define-se um byte especial de **Escape (*Control Escape*): `01111101` (`0x7D`)**.
  - **No Emissor:** Sempre que o byte de Flag (`01111110`) **ou** o próprio byte de Escape (`01111101`) aparecer dentro do campo de dados, o emissor insere um **byte de Escape `01111101` imediatamente antes dele**!
  - **No Receptor:**
    - Se encontrar um **único `01111110` (Flag)** não precedido de escape $\implies$ **Fim do quadro**!
    - Se encontrar `01111101` seguido de `01111110` $\implies$ descarta o byte de escape e mantém `01111110` como dado normal.
    - Se encontrar dois bytes de escape seguidos (`01111101 01111101`) $\implies$ descarta o primeiro e mantém o segundo como dado normal!

---

### 2. MPLS (*Multiprotocol Label Switching* — Camada "2,5")
Rede de circuitos virtuais que opera com cabeçalhos de rótulo fixo inseridos **entre o cabeçalho de Camada 2 (Ethernet) e o cabeçalho de Camada 3 (IP)**:

```
Posição do Cabeçalho MPLS ("Camada 2,5"):
+----------------------+-----------------------------------------+----------------------+---------+
| Cabeçalho Ethernet   |          Cabeçalho MPLS (4 bytes)       |   Cabeçalho IPv4     | Payload |
|     (Camada 2)       | Label (20b) | Exp (3b) | S (1b) |TTL(8b)|      (Camada 3)      |         |
+----------------------+-----------------------------------------+----------------------+---------+
```

* **Como funciona um Roteador Comutador de Rótulos (*Label-Switched Router — LSR*):**
  - Encaminha o pacote consultando sua tabela MPLS usando **apenas o Rótulo (*Label*) de tamanho fixo (20 bits)** (busca exata imediata, sem precisar extrair o datagrama IP nem fazer *Longest Prefix Matching*), trocando o rótulo de entrada pelo rótulo de saída.
* **Principal Utilidade Moderna — Engenharia de Tráfego (*Traffic Engineering*) e VPNs:**
  - Enquanto o roteamento IP tradicional força todos os pacotes destinados a um mesmo IP a seguirem o mesmo caminho de menor custo, o MPLS permite estabelecer **caminhos comutados por rótulo (*LSPs*) distintos** para desviar fluxos específicos por rotas alternativas (balanceamento de carga, recuperação rápida de falhas *Fast Reroute* e isolamento de **VPNs corporativas**).

---

### 3. Redes de Data Center (*Data Center Networking* — Seção 6.6 do Livro)
* **Arquitetura Hierárquica em Árvore / Topologia de Clos (*Leaf-Spine*):**
  - Milhares de servidores organizados em **Racks** (20 a 40 servidores *blade* por rack), tendo no topo de cada rack um switch **TOR (*Top of Rack*)**.
  - Os switches TOR conectam-se a múltiplas camadas de switches **Tier-2** e **Tier-1** (formando uma **Rede de Clos** altamente interconectada com múltiplos caminhos disjuntos entre quaisquer dois racks), que por sua vez se ligam aos roteadores de borda e balanceadores de carga (*Load Balancers*).
* **ECMP (*Equal-Cost Multi-Path*):** Essencial em data centers para distribuir fluxos entre os múltiplos caminhos equivalentes entre switches TOR e Tier-2/Tier-1.
* **ARP Modificado em Data Centers Virtualizados:** Para permitir que Máquinas Virtuais (VMs) migrem entre switches físicos sem quebrar conexões e sem inundar dezenas de milhares de servidores com broadcasts ARP, o ARP em nuvens modernas é substituído por um **sistema de diretório estilo consulta DNS** que mapeia `(IP da VM -> Switch TOR físico atual)`.

---

## 6.7 Síntese Completa: Um Dia na Vida de uma Requisição Web (Passos 1 a 24)

> 📌 **Sua Anotação no Livro (p. 523):**  
> *"Copiar para o resumo este exemplo detalhado"* — Abaixo está a síntese completa e estruturada da **Seção 6.7 de Kurose & Ross**, integrando todos os protocolos da disciplina (`DHCP`, `UDP`, `IP`, `Ethernet`, `Switch Self-Learning`, `ARP`, `DNS`, `OSPF`, `BGP`, `TCP` e `HTTP`) desde o instante em que o estudante Bob conecta seu notebook no cabo Ethernet da escola até a página `www.google.com` aparecer na tela!

```
Cenário Completo (Figura 6.32 do Livro):
Rede Escolar (68.85.2.0/24)                  Rede ISP Comcast (68.80.0.0/13)        Rede Google (64.233.160.0/19)
+----------------------------------------+   +----------------------------+         +---------------------------+
| [Notebook do Bob]                      |   | [Servidor DNS Comcast]     |         | [Servidor Web Google]     |
| MAC: 00:16:D3:23:68:8A                 |   | IP: 68.87.71.226           |         | www.google.com            |
| IP (via DHCP): 68.85.2.101             |   |            ^               |         | IP: 64.233.169.105        |
|        |                               |   |            | (OSPF)        |         |            ^              |
|        v                               |   |            v               |         |            |              |
| [Switch Ethernet] ---> [Roteador Esc.] |==>| [Roteadores Comcast] <=====|=(eBGP)=>| [Roteadores Google]       |
| (Autoaprendiz)         IP: 68.85.2.1   |   +----------------------------+         +---------------------------+
|                        MAC: 00:22:6B.. |
+----------------------------------------+
```

### Fase 1: Obtendo IP, Máscara, Gateway e DNS via DHCP (Passos 1 a 7)
Quando Bob conecta o cabo Ethernet, seu notebook não possui endereço IP (`0.0.0.0`), não sabe a máscara da rede, não sabe quem é o roteador padrão (*default gateway*) nem sabe o IP do servidor DNS:
1. **Criação da Requisição DHCP (Passos 1 e 2):** O SO de Bob cria uma mensagem `DHCP Request/Discover`, coloca dentro de um **segmento UDP** (`Porta Origem = 68`, `Porta Destino = 67`), encapsula em um **datagrama IP** (`IP Origem = 0.0.0.0`, `IP Destino = 255.255.255.255` — broadcast IP) e encapsula em um **quadro Ethernet** (`MAC Origem = 00:16:D3:23:68:8A`, `MAC Destino = FF:FF:FF:FF:FF:FF` — broadcast MAC).
2. **Autoaprendizagem no Switch e Inundação (Passo 3):** O quadro chega ao Switch Ethernet. O switch **aprende na sua tabela** que o MAC de Bob (`00:16:D3:23:68:8A`) está naquela porta de entrada, e faz *broadcast* do quadro para todas as outras portas, alcançando o Roteador Escolar.
3. **Processamento pelo Servidor DHCP no Roteador (Passos 4 e 5):** O roteador recebe o quadro na interface `00:22:6B:45:1F:1B`, extrai o datagrama IP e demultiplexa via UDP (porta 67) até o servidor DHCP local. O servidor DHCP aloca o endereço `68.85.2.101` e monta uma mensagem **`DHCP ACK`** contendo **4 informações vitais**:
   - **IP de Bob:** `68.85.2.101`
   - **Bloco/Máscara da Sub-rede:** `68.85.2.0/24`
   - **IP do Roteador Gateway Padrão:** `68.85.2.1`
   - **IP do Servidor DNS Local:** `68.87.71.226`
4. **Entrega Unicast do `DHCP ACK` (Passos 6 e 7):** O roteador encapsula o `DHCP ACK` em UDP $\to$ IP $\to$ Quadro Ethernet com `MAC Origem = 00:22:6B:45:1F:1B` e `MAC Destino = 00:16:D3:23:68:8A` (unicast!). Como o switch **já aprendeu** a porta de Bob no Passo 3, ele encaminha o quadro **apenas para a porta do notebook de Bob** (sem inundar!). Bob configura seu IP, registra o servidor DNS e instala o gateway padrão `68.85.2.1` na sua tabela de repasse IP.

---

### Fase 2: Descobrindo o MAC do Gateway via ARP e Preparando o DNS (Passos 8 a 13)
Bob digita `www.google.com` no navegador e precisa traduzir esse nome para IP usando DNS:
5. **Montagem da Consulta DNS (Passo 8):** O SO cria uma mensagem **`DNS Query`** para `"www.google.com"`, coloca em um **segmento UDP** (`Porta Destino = 53`), e coloca em um **datagrama IP** com `IP Origem = 68.85.2.101` e `IP Destino = 68.87.71.226` (servidor DNS).
6. **Por que o pacote DNS trava antes de sair? (Passo 9):** Como o IP do servidor DNS (`68.87.71.226`) está **fora da sub-rede escolar** (`68.85.2.0/24`), Bob deve enviar o quadro Ethernet para o **roteador gateway padrão (`68.85.2.1`)**. Porém, Bob só conhece o **IP** do gateway (`68.85.2.1`), e **ainda não conhece o endereço MAC dele**!
7. **Resolução ARP para o Gateway (Passos 10, 11 e 12):**
   - **Passo 10 (`ARP Query`):** Bob cria uma mensagem `ARP Query` perguntando *"Qual o MAC do IP `68.85.2.1`?"*, encapsula em um quadro Ethernet **Broadcast (`FF:FF:FF:FF:FF:FF`)** e envia ao switch, que inunda para todas as portas.
   - **Passo 11 (`ARP Reply`):** O roteador gateway vê que o IP alvo `68.85.2.1` é o seu, monta um `ARP Reply` informando que seu MAC é `00:22:6B:45:1F:1B`, e o envia em um quadro Ethernet **Unicast** destinado ao MAC de Bob (`00:16:D3:23:68:8A`).
   - **Passo 12:** Bob recebe o `ARP Reply` e grava `(68.85.2.1 -> 00:22:6B:45:1F:1B)` em sua Tabela ARP.
8. **Envio do Quadro contendo a Consulta DNS (Passo 13):** Agora Bob finalmente encapsula o datagrama IP da consulta DNS (`IP Destino = 68.87.71.226`) dentro de um quadro Ethernet com **`MAC Destino = 00:22:6B:45:1F:1B` (o MAC do roteador gateway!)** e envia pelo switch ao roteador.

---

### Fase 3: Roteamento Intra-Domínio até o Servidor DNS da Comcast (Passos 14 a 17)
9. **Encaminhamento até o DNS (Passos 14 e 15):** O roteador escolar desencapsula o quadro, examina o `IP Destino = 68.87.71.226`, consulta sua tabela de repasse e envia o datagrama pelo enlace até o roteador de borda da Comcast. Os roteadores internos da Comcast encaminham o datagrama salto a salto até o servidor DNS usando tabelas de repasse preenchidas pelo protocolo intra-AS da Comcast (**OSPF / IS-IS**) e pelo **BGP**.
10. **Resposta DNS (Passos 16 e 17):** O servidor DNS da Comcast consulta seu banco de dados/cache, encontra o registro Tipo `A` para `www.google.com` $\to$ **`64.233.169.105`**, monta uma mensagem **`DNS Reply`** dentro de UDP $\to$ IP (`IP Destino = 68.85.2.101`) e a envia de volta pela rede Comcast $\to$ Roteador Escolar $\to$ Switch $\to$ Notebook de Bob. Bob extrai o IP `64.233.169.105`!

---

### Fase 4: Interação Cliente-Servidor Web via TCP e HTTP + Roteamento BGP (Passos 18 a 24)
11. **Início do *3-Way Handshake* TCP (Passo 18):** O navegador de Bob cria um socket TCP e envia um segmento **`TCP SYN`** (`Porta Destino = 80`, bit `SYN = 1`) dentro de um datagrama IP (`IP Origem = 68.85.2.101`, `IP Destino = 64.233.169.105`) encapsulado em um quadro Ethernet destinado ao MAC do gateway (`00:22:6B:45:1F:1B`). *(Não precisa de novo ARP, pois o MAC do gateway já está na Tabela ARP de Bob do Passo 12!)*
12. **Roteamento Inter-Domínio via BGP (Passo 19):** Os roteadores da escola, da Comcast e da Google encaminham o datagrama contendo o `TCP SYN` até `64.233.169.105`. As entradas de repasse que governam o enlace inter-AS entre a rede da Comcast e a rede da Google foram determinadas pelo protocolo **BGP**!
13. **Resposta `TCP SYN-ACK` do Servidor Google (Passos 20 e 21):** O datagrama chega ao servidor `www.google.com`, é demultiplexado para o *welcome socket* da porta 80, cria-se um *connection socket* dedicado e o servidor devolve um segmento **`TCP SYN-ACK`** (`SYN = 1, ACK = 1`), que viaja de volta pela Google $\to$ Comcast $\to$ Escola até o socket TCP de Bob (que entra no estado *ESTABLISHED*).
14. **Envio do `HTTP GET` e Recebimento do `HTTP 200 OK` (Passos 22, 23 e 24):**
    - **Passo 22:** O navegador de Bob escreve a requisição **`HTTP GET`** no socket TCP, que é empacotada em um segmento TCP (com o `ACK` do 3º passo do handshake!), encapsulada em datagrama IP e quadro Ethernet, e entregue ao servidor da Google.
    - **Passo 23:** O servidor HTTP da Google lê o `HTTP GET` do socket, gera a mensagem **`HTTP Response (200 OK)`** contendo o código HTML da página e a envia pelo socket TCP.
    - **Passo 24:** Os datagramas retornam através das redes da Google, Comcast e Escola até o notebook de Bob; o navegador lê o HTML do socket e **renderiza a página na tela!**

#### Tabela-Resumo da Jornada de Endereços nos Passos Principais:

| Etapa / Mensagem | Camada 5 (Aplicação) | Camada 4 (Transporte) | Camada 3 (`IP Orig` $\to$ `IP Dest`) | Camada 2 (`MAC Orig` $\to$ `MAC Dest` na LAN Escolar) |
| :--- | :--- | :--- | :--- | :--- |
| **Passo 1–2** | `DHCP Discover/Req` | UDP (`68` $\to$ `67`) | `0.0.0.0` $\to$ `255.255.255.255` | `MAC_Bob` $\to$ `FF:FF:FF:FF:FF:FF` |
| **Passo 5–6** | `DHCP ACK` | UDP (`67` $\to$ `68`) | `68.85.2.1` $\to$ `68.85.2.101` | `MAC_Roteador` $\to$ `MAC_Bob` |
| **Passo 10** | — (ARP) | — | Alvo ARP: `68.85.2.1` | `MAC_Bob` $\to$ `FF:FF:FF:FF:FF:FF` |
| **Passo 11** | — (ARP) | — | Remetente ARP: `68.85.2.1` | `MAC_Roteador` $\to$ `MAC_Bob` |
| **Passo 13** | `DNS Query` | UDP (`ephem` $\to$ `53`) | `68.85.2.101` $\to$ `68.87.71.226` | `MAC_Bob` $\to$ **`MAC_Roteador`** |
| **Passo 18** | — (Handshake) | `TCP SYN` ($\to$ `80`) | `68.85.2.101` $\to$ `64.233.169.105` | `MAC_Bob` $\to$ **`MAC_Roteador`** |
| **Passo 22** | `HTTP GET` | `TCP ACK+Data` ($\to$ `80`) | `68.85.2.101` $\to$ `64.233.169.105` | `MAC_Bob` $\to$ **`MAC_Roteador`** |

---

# Semana 12: Laboratórios de Mininet e Questões Teóricas Resolvidas

> **Referências da Disciplina:**  
> * [laboratorio-04-mininet-introducao.pdf](../Semana%2012/laboratorio-04-mininet-introducao.pdf) — *Laboratório 04: Emulação de Redes com Mininet*  
> * [laboratorio-05-mininet-avancado.pdf](../Semana%2012/laboratorio-05-mininet-avancado.pdf) — *Laboratório 05: Emulação de Redes e Arquitetura Cliente-Servidor no Mininet*  
> * [relatorio_lab5.pdf](../Semana%2012/relatorio_lab5.pdf) — *Relatório do Laboratório 05*

## 7.1 Arquitetura do Mininet: Namespaces, veth, Open vSwitch e TCLink

### 1. Emulação em Tempo Real (Mininet) vs. Simulação de Eventos Discretos (ns-3)
* **Simuladores (ex: ns-3, OMNeT++):** Modelam o comportamento da rede por abstrações matemáticas e filas de eventos discretos em tempo virtual. Exigem reescrever protocolos/aplicações para a API do simulador.
* **Emuladores Baseados em Contêineres Leves (Mininet):** Executam o **código real da pilha TCP/IP do kernel Linux** e aplicações reais sem modificação (`python3 -m http.server`, `curl`, `iperf3`, `tcpdump`, `wireshark`) em tempo real dentro de uma única máquina Linux.

### 2. Os 4 Pilares do Kernel Linux usados pelo Mininet

```
Arquitetura Interna de Emulação no Kernel Linux (Mininet):
+-------------------------------+      +-----------------------------------+      +-------------------------------+
| Network Namespace: Host h1    |      | Root Namespace (Kernel Hospedeiro)|      | Network Namespace: Host h2    |
| IP: 10.0.0.1/24               |      |                                   |      | IP: 10.0.0.2/24               |
| Tabela ARP / Rotas / Sockets  |      |     +-----------------------+     |      | Tabela ARP / Rotas / Sockets  |
|                               |      |     |   Open vSwitch (s1)   |     |      |                               |
|  [h1-eth0] <==================|======|===> | [s1-eth1]   [s1-eth2] | <===|======|=================> [h2-eth0]   |
+-------------------------------+  ^   +-----+-----------------------+-----+   ^  +-------------------------------+
                                   |                     ^                     |
                        Par veth + TCLink (tc)           |          Par veth + TCLink (tc)
                        (HTB p/ bw + netem p/ delay)     v          (HTB p/ bw + netem p/ delay)
                                                [Controlador OVS (c0)]
                                                 (Protocolo OpenFlow)
```

1. **Network Namespaces (`CONFIG_NET_NS` — `unshare(CLONE_NEWNET)`):** Isola completamente a pilha de rede de cada host (`h1`, `h2`, ...). Cada host possui interfaces de rede (`lo`, `hX-eth0`), endereço IP, endereço MAC, tabela ARP, tabela de roteamento, regras `iptables` e **espaço de portas de sockets TCP/UDP próprios e independentes**, embora compartilhem o mesmo kernel e sistema de arquivos.
2. **Pares de Ethernet Virtual (`veth pairs`):** Atuam como um "cabo de rede virtual" em memória: todo quadro Ethernet injetado em uma ponta (ex: `h1-eth0`, dentro do namespace de `h1`) sai instantaneamente na outra ponta (`s1-eth1`, conectada à porta do switch virtual `s1`).
3. **Open vSwitch (`OVS` / `OVSKernelSwitch`):** Switch multicamada em software de alto desempenho compatível com o protocolo **OpenFlow**, operando diretamente no kernel Linux para encaminhar quadros segundo sua Tabela de Fluxo (*Flow Table*).
4. **Linux Traffic Control (`tc` / `TCLink`):** Subsistema de QoS do kernel Linux acoplado às interfaces `veth` que aplica:
   - **Limitação de Largura de Banda (`bw`):** Via *Hierarchical Token Bucket* (`HTB`) ou *Token Bucket Filter* (`TBF`), controlando a taxa de drenagem de bits para o enlace.
   - **Emulação de Atraso de Propagação (`delay`), Jitter e Perda (`loss`):** Via disciplina de fila **`netem` (*Network Emulator*)**, que retém cada pacote pelo tempo `delay` configurado antes de entregá-lo.

### 3. Comandos Essenciais de Diagnóstico da CLI do Mininet (`mininet>`)
* `nodes`: Lista todos os nós criados na topologia (`c0`, `h1..h4`, `s1`).
* `net`: Mostra o mapeamento exato de conexões porta-a-porta (ex: `h1 h1-eth0:s1-eth1`).
* `dump`: Exibe a classe, o IP, a interface e o **PID do processo `bash`** associado a cada nó no Linux.
* `pingall`: Dispara testes de conectividade ICMP entre todos os pares de hosts da topologia.
* `h2 iperf -c h1`: Executa o cliente `iperf` dentro do namespace de `h2` medindo a vazão TCP até o servidor em `h1`.
* `dpctl dump-flows` (ou `sh ovs-ofctl dump-flows s1`): Inspeciona todas as regras de fluxo OpenFlow instaladas na tabela do switch `s1`.
* `sudo mn -c`: Limpa processos órfãos, pares `veth` e configurações do OVS após encerramento.

---

## 7.2 Resolução Comentada das Questões Teóricas do Lab 04 (Q1 a Q4)

Abaixo estão as respostas completas, rigorosas e prontas para prova das **4 Questões de Engenharia do Laboratório 04** ([laboratorio-04-mininet-introducao.pdf](../Semana%2012/laboratorio-04-mininet-introducao.pdf)).

### 🔹 Q1 (Isolamento de Processos):
> **Pergunta:** *Explique como o kernel Linux utiliza o recurso de Network Namespaces para permitir que os hosts `h1` e `h2` executem serviços na mesma porta (ex: porta 80 ou 5001) sem conflitos no sistema operacional hospedeiro.*

**Resposta Completa:**
* Em um sistema operacional tradicional sem virtualização de rede, a tabela de sockets TCP/UDP é global para todo o kernel. Se dois processos tentarem executar a chamada de sistema `bind()` no mesmo endereço curinga (`0.0.0.0`) e na mesma porta (ex: porta `80` do HTTP ou `5001` do iPerf), o segundo processo falhará imediatamente com o erro **`EADDRINUSE` (*Address already in use*)**.
* O Mininet contorna isso criando cada host emulado (`h1`, `h2`) como um processo `bash` colocado dentro de um **Network Namespace (`net_ns`) exclusivo** do kernel Linux, instanciado via chamada de sistema `unshare(CLONE_NEWNET)` (ou `clone(..., CLONE_NEWNET)`).
* Cada *Network Namespace* possui sua **própria instância isolada da pilha de protocolos de rede** dentro do kernel, incluindo:
  1. Suas próprias interfaces de rede (`lo` e `hX-eth0`) e endereços IP (`10.0.0.1` em `h1` e `10.0.0.2` em `h2`);
  2. Suas próprias tabelas de roteamento IP e cache ARP;
  3. **Sua própria tabela hash de sockets TCP e UDP (espaço de portas de 16 bits totalmente independente).**
* Assim, quando um servidor é iniciado na porta `80` ou `5001` dentro de `h1`, a chamada `bind()` registra o socket **apenas na estrutura de dados do namespace de `h1`**. Quando outro servidor faz `bind()` na mesma porta `80` ou `5001` em `h2`, o kernel verifica a tabela de sockets do namespace de `h2` (que está livre!), permitindo que ambos os serviços coexistam na mesma máquina física sem nenhum conflito de porta com `h1` nem com o sistema operacional hospedeiro (*root namespace*).

---

### 🔹 Q2 (Análise de Desempenho e Latência):
> **Pergunta:** *Ao disparar um `ping` de `h1` para `h2` na Atividade 2, qual foi o valor do RTT (Round Trip Time) médio observado? Explique teoricamente por que o RTT aproximou-se de 20 ms (considerando os atrasos de enfileiramento e propagação nos dois enlaces de 5 ms).*

**Resposta Completa:**
* **Valor observado:** O RTT médio observado no `ping` de `h1` para `h2` é de **aproximadamente $20{,}1\text{ ms}$** (com o primeiro pacote ligeiramente maior, ex: $21\text{ a }25\text{ ms}$, devido à resolução inicial de ARP e ao aprendizado de fluxo no controlador OpenFlow).
* **Explicação Teórica e Decomposição dos Atrasos:**
  Na topologia em estrela da Atividade 2, o caminho entre `h1` e `h2` passa pelo switch central `s1`, sendo composto por **dois enlaces em série**, cada qual configurado via `TCLink` com largura de banda $R = 10\text{ Mbps}$ e atraso unidirecional $d_{\text{prop}} = 5\text{ ms}$:
  $$\text{Enlace 1: } \mathtt{h1 \leftrightarrow s1}\ (5\text{ ms}) \qquad \text{e} \qquad \text{Enlace 2: } \mathtt{s1 \leftrightarrow h2}\ (5\text{ ms})$$

```
Trajeto de Ida e Volta de um Pacote ICMP Ping (Total = 4 Travessias de Enlace de 5 ms):
  [Host h1] ====================> [Switch s1] ====================> [Host h2]
            (1) Ida: +5 ms                    (2) Ida: +5 ms        (Total Ida = 10 ms)
            ICMP Echo Request                 ICMP Echo Request

  [Host h1] <==================== [Switch s1] <==================== [Host h2]
            (4) Volta: +5 ms                  (3) Volta: +5 ms      (Total Volta = 10 ms)
            ICMP Echo Reply                   ICMP Echo Reply
```

  Pela equação do atraso nodal de Kurose & Ross ($d_{\text{nodal}} = d_{\text{proc}} + d_{\text{queue}} + d_{\text{trans}} + d_{\text{prop}}$):
  1. **Atraso de Propagação Total ($d_{\text{prop}}$):**
     - **Ida (`ICMP Echo Request`):** Atravessa $\mathtt{h1 \to s1}$ ($5\text{ ms}$) + $\mathtt{s1 \to h2}$ ($5\text{ ms}$) $= \mathbf{10\text{ ms}}$.
     - **Volta (`ICMP Echo Reply`):** Atravessa $\mathtt{h2 \to s1}$ ($5\text{ ms}$) + $\mathtt{s1 \to h1}$ ($5\text{ ms}$) $= \mathbf{10\text{ ms}}$.
     - Soma dos atrasos de propagação emulados pelo `netem`: $4 \times 5\text{ ms} = \mathbf{20\text{ ms}}$.
  2. **Atrasos de Transmissão ($d_{\text{trans}} = \frac{L}{R}$), Enfileiramento ($d_{\text{queue}}$) e Processamento ($d_{\text{proc}}$):**
     - Um pacote `ping` padrão possui apenas $64\text{ bytes}$ de payload IP + $14\text{ bytes}$ Ethernet $= 78\text{ bytes} = 624\text{ bits}$. A $10\text{ Mbps}$, o atraso de transmissão por enlace é $d_{\text{trans}} = \frac{624}{10^7} \approx 0{,}0624\text{ ms}$ (menos de $0{,}25\text{ ms}$ somando os 4 saltos).
     - Como o `ping` envia apenas 1 pacote por segundo sem tráfego concorrente, a intensidade de tráfego $I = \frac{L \cdot a}{R} \approx 0$, resultando em **atraso de fila nulo ($d_{\text{queue}} \approx 0$)** e atraso de processamento em memória no OVS da ordem de microssegundos ($d_{\text{proc}} \approx 0$).
  - Portanto:
    $$\text{RTT} = 4 \cdot d_{\text{prop}} + 4 \cdot d_{\text{trans}} + d_{\text{queue}} + d_{\text{proc}} \approx 20\text{ ms} + 0{,}25\text{ ms} \approx \mathbf{20{,}25\text{ ms}}$$

---

### 🔹 Q3 (Gargalo de Vazão com iPerf):
> **Pergunta:** *Qual foi a vazão máxima atingida na transferência TCP de `h3` (100 Mbps) para `h1` (10 Mbps)? Identifique qual enlace atuou como gargalo (bottleneck link) e explique por que a taxa não ultrapassou 10 Mbps.*

**Resposta Completa:**
* **Vazão Máxima Atingida:** A vazão útil de camada de aplicação (*goodput* TCP) medida pelo `iperf` de `h3` para `h1` estabilizou em aproximadamente **$9{,}4\text{ a }9{,}56\text{ Mbps}$**, sem jamais ultrapassar o limite nominal de **$10\text{ Mbps}$**.
* **Identificação do Enlace Gargalo (*Bottleneck Link*):**
  O caminho de `h3` até `h1` é composto por dois enlaces em série com capacidades assimétricas:
  - Enlace 1 ($\mathtt{h3 \to s1}$): $R_1 = 100\text{ Mbps}$ (atraso $2\text{ ms}$).
  - Enlace 2 ($\mathtt{s1 \to h1}$): $R_2 = 10\text{ Mbps}$ (atraso $5\text{ ms}$) $\implies$ **Este é o Enlace Gargalo (*Bottleneck Link*)!**
* **Explicação Teórica (Por que a taxa fim-a-fim não ultrapassa 10 Mbps e fica em ~9,5 Mbps):**
  1. **Princípio do Elo Gargalo em Série (Seção 1.4.3 de Kurose & Ross):** Em uma rota com enlaces em série de capacidades $R_1, R_2, \dots, R_N$, a vazão fim-a-fim é estritamente limitada pelo enlace de menor taxa de transmissão:
     $$\text{Throughput}_{\text{máx}} = \min(R_1, R_2) = \min(100\text{ Mbps}, 10\text{ Mbps}) = \mathbf{10\text{ Mbps}}$$
  2. **Dinâmica de Fila no Switch `s1` e Controle de Congestionamento TCP:** Quando `h3` injeta segmentos TCP a até $100\text{ Mbps}$ no enlace $\mathtt{h3 \to s1}$, os pacotes chegam ao switch `s1` $10\times$ mais rápido do que a porta de saída `s1-eth1` (limitada a $10\text{ Mbps}$ pelo *Token Bucket* do `tc`) consegue drená-los. Os pacotes excedentes acumulam-se no **buffer da porta de saída do switch `s1`**. Se `h3` continuar enviando acima de $10\text{ Mbps}$, o buffer lota ($I = \frac{L \cdot a}{R_2} > 1$), ocorrem descartes (*packet drops*) e o **Controle de Congestionamento do TCP** em `h3` reduz a janela `cwnd`, além do mecanismo de **Auto-Temporização dos ACKs (*ACK Clocking*)**, que faz os ACKs retornarem de `h1` exatamente no ritmo ditado pelo gargalo de $10\text{ Mbps}$.
  3. **Sobrecarga de Cabeçalhos (*Protocol Overhead*):** O limitador de camada 2 (`tc`) contabiliza o quadro Ethernet inteiro ($1500\text{ B IP} + 14\text{ B Ethernet} = 1514\text{ bytes}$), enquanto o `iperf` mede apenas os dados úteis da aplicação TCP ($\text{MSS} = 1460\text{ B}$, ou $1448\text{ B}$ com opções de *Timestamps* TCP de $12\text{ B}$):
     $$\text{Goodput}_{\text{teórico}} = 10\text{ Mbps} \times \frac{1448\text{ B}}{1514\text{ B}} \approx \mathbf{9{,}56\text{ Mbps}}$$

---

### 🔹 Q4 (Inspeção OpenFlow no Switch):
> **Pergunta:** *Executando o comando `dpctl dump-flows` no terminal do Mininet, descreva as regras de fluxo instaladas no switch `s1`. Como o switch decide para qual porta física repassar um quadro Ethernet?*

**Resposta Completa:**
* **Descrição das Regras Observadas no `dpctl dump-flows`:**
  Ao executar `dpctl dump-flows` logo após um `ping` ou `iperf`, observam-se entradas na Tabela de Fluxo (*Flow Table*) do switch `s1` com o formato:
  ```
  cookie=0x0, duration=3.4s, table=0, n_packets=5, n_bytes=490, idle_timeout=60,
  priority=65535, icmp, in_port=1, vlan_tci=0x0000,
  dl_src=00:00:00:00:00:01, dl_dst=00:00:00:00:00:02, nw_src=10.0.0.1, nw_dst=10.0.0.2
  actions=output:2
  ```
  *(Importante: Se você rodar `dpctl dump-flows` após mais de 60 segundos de ociosidade, a tabela aparecerá vazia porque as regras instaladas pelo `OVSController` possuem um `idle_timeout=60s` e expiram automaticamente sem tráfego!)*
* **Como o Switch Decide para qual Porta Física Repassar um Quadro (Paradigma SDN Reativo + Autoaprendizagem L2):**
  O switch `s1` (`OVSKernelSwitch`) em conjunto com o controlador padrão `c0` (`OVSController`) implementa um **Switch de Autoaprendizagem de Camada 2 (*Learning Switch*) via protocolo OpenFlow** seguindo o modelo **`Match-Plus-Action`**:
  1. **Estado Inicial e *Table-Miss*:** Inicialmente a Tabela de Fluxo de `s1` está vazia. Quando `h1` envia o primeiro quadro para `h2` entrando pela porta `in_port=1` (`s1-eth1`), o switch procura uma regra na sua *Flow Table* e ocorre um ***Table-Miss*** (nenhuma regra casa).
  2. **Consulta ao Controlador (`Packet-In`):** O switch encapsula o quadro em uma mensagem OpenFlow **`Packet-In`** e o envia ao controlador `c0`.
  3. **Autoaprendizagem no Controlador:** O controlador `c0` inspeciona o **endereço MAC de origem (`dl_src = 00:00:00:00:00:01`)** e a **porta de entrada (`in_port = 1`)**, gravando em sua tabela interna que o MAC de `h1` reside na porta `1`. Como no primeiro pacote o controlador ainda não conhece a porta do MAC de destino (`dl_dst`), ele instrui o switch (via `Packet-Out` com `actions=FLOOD`) a inundar o quadro para todas as outras portas.
  4. **Instalação da Regra de Fluxo (`Flow-Mod` / `Modify-State`) e Repasse em Hardware/Kernel:** Assim que `h2` responde pela porta `2` (`s1-eth2`), o controlador aprende que `00:00:00:00:00:02` está na porta `2`. Agora que conhece as portas de ambos os MACs, o controlador envia uma mensagem OpenFlow **`Flow-Mod`** instalando na *Flow Table* de `s1` as regras diretas:
     - **Campos de *Match*:** Porta de entrada (`in_port`), endereço MAC de origem (`dl_src`), endereço MAC de destino (`dl_dst`), tipo Ethernet (`dl_type`) e cabeçalhos L3/L4.
     - **Campo de *Action*:** `actions=output:2` (para o sentido $\mathtt{h1 \to h2}$) e `actions=output:1` (para o sentido $\mathtt{h2 \to h1}$).
  5. A partir desse momento, todos os quadros subsequentes daquele fluxo **casam diretamente na Tabela de Fluxo do kernel no OVS** e são encaminhados em microssegundos para a porta física exata (`output:N`) sem precisar consultar o controlador novamente!

---

## 7.3 Resolução Comentada das Questões Teóricas do Lab 05 (Q1 a Q3)

Síntese das **3 Questões de Engenharia do Laboratório 05** ([laboratorio-05-mininet-avancado.pdf](../Semana%2012/laboratorio-05-mininet-avancado.pdf) e [relatorio_lab5.pdf](../Semana%2012/relatorio_lab5.pdf)):

### 🔹 Q1 (Isolamento de Processos e Sockets no Servidor HTTP):
> **Pergunta:** *Como o Mininet garante que o comando `python3 -m http.server` rodando no host `h2` utilize uma tabela de rotas e interface IP isoladas do host `h1` e do próprio sistema operacional hospedeiro?*

**Resposta:**
* Ao executar `h2.cmd('python3 -m http.server 8080 ...')`, o Mininet dispara o processo Python como processo filho do `bash` associado ao **Network Namespace (`CONFIG_NET_NS`) exclusivo do host `h2`** (criado via `unshare(CLONE_NEWNET)`).
* No Linux, processos filhos herdam automaticamente o *Network Namespace* do processo pai. Enquanto o sistema de arquivos, memória e árvore de processos são compartilhados com o hospedeiro, toda chamada de sistema de rede feita pelo `http.server` (`socket()`, `bind()`, `listen()`, `accept()`, `send()`) é interceptada pelo kernel e resolvida **estritamente contra as estruturas de rede privadas do namespace de `h2`** (visão exclusiva da interface `h2-eth0` com IP `10.0.0.2/24`, tabela de rotas própria e tabela ARP isolada de `h1` e do host).

---

### 🔹 Q2 (Análise do Gargalo de Banda: `iperf3` vs. `curl` em enlace de 10 Mbps):
> **Pergunta:** *O enlace entre `h2` e o switch possui largura de banda configurada em 10 Mbps. Comparando os resultados obtidos pelo `curl` e pelo `iperf3`, qual foi a taxa de transferência efetiva atingida pela aplicação e qual a razão dessa diferença em relação à capacidade nominal do canal?*

**Resposta:**
* **Resultados Medidos:** No `iperf3` (fluxo contínuo de 5 s), o *goodput* recebido em `h2` foi de **$9{,}38\text{ Mbps}$** (enquanto o transmissor `h1`, em enlace de $100\text{ Mbps}$, injetou média de $12{,}15\text{ Mbps}$ acumulando pacotes no buffer do switch `s1`). Já no `curl`, a velocidade média reportada foi de apenas **$16.896\text{ B/s} \approx 0{,}135\text{ Mbps}$** (tempo total de $57{,}1\text{ ms}$).
* **As 2 Razões Técnicas para a Diferença:**
  1. **Sobrecarga de Cabeçalhos (*Protocol Overhead*) no `iperf3`:** O controle de tráfego `tc` limita a taxa na camada 2 contando todos os $1514\text{ bytes}$ do quadro Ethernet ($14\text{ B Eth} + 20\text{ B IP} + 32\text{ B TCP c/ Timestamps} + 1448\text{ B Payload}$), enquanto a aplicação mede apenas o payload útil de $1448\text{ bytes}$. Isso impõe um teto físico de *goodput* de:
     $$\text{Goodput}_{\text{máx}} = 10\text{ Mbps} \times \frac{1448}{1514} \approx \mathbf{9{,}56\text{ Mbps}}$$
  2. **Domínio do RTT do Handshake TCP + *Slow Start* em Transferências Curtas no `curl`:** O RTT entre `h1` ($2\text{ ms}$) e `h2` ($10\text{ ms}$) é de $2 \times (2 + 10) = \mathbf{24\text{ ms}}$. Como o `curl` baixa uma listagem HTML minúscula ($\approx 965\text{ bytes}$, que cabe em 1 único segmento TCP), a conexão exige **1 RTT ($24\text{ ms}$) para o *3-Way Handshake* TCP** + **1 RTT ($24\text{ ms}$) para enviar o `HTTP GET` e receber o objeto**, operando ainda no início da **Partida Lenta (*Slow Start*, `cwnd` inicial pequena)** e encerrando com `FIN`. Assim, dos $57{,}1\text{ ms}$ totais, **$48\text{ ms}$ ($84\%$ do tempo) foram gastos esperando propagação de RTTs de controle com o canal ocioso**, derrubando a vazão média aparente ($\frac{F}{2\cdot\text{RTT} + d_{\text{trans}}}$) para $0{,}135\text{ Mbps}$!

---

### 🔹 Q3 (Estruturação de Métricas para Análise: JSON/CSV e `.pcap` vs. Terminal):
> **Pergunta:** *Quais são as vantagens técnicas de automatizar a coleta de dados de rede exportando relatórios estruturados (JSON/CSV) e capturas brutas (`.pcap`) em comparação com a inspeção manual no terminal?*

**Resposta (Os 3 Pilares de Engenharia de Redes):**
1. **Reprodutibilidade Científica e Sincronismo Temporal:** A automação via script Python garante que o `tcpdump`, o servidor HTTP e os geradores de tráfego (`curl` / `iperf3`) sejam disparados sempre na mesma sequência exata e sem interferência de digitação humana, evitando perda do início da captura ou erros de transcrição manual.
2. **Interoperabilidade e Processamento Programático em Larga Escala (`JSON` / `CSV`):** A saída textual do terminal é voltada para leitura humana pontual. O formato estruturado `iperf3 --json` preserva séries temporais discretas completas (vazão por segundo, bytes enviados/recebidos, retransmissões TCP, janela de congestionamento `snd_cwnd` e RTT), permitindo que scripts com `pandas` e `matplotlib` calculem médias, intervalos de confiança e plotem gráficos automaticamente.
3. **Auditoria Forense e Análise Microscópica em Nível de Pacote (`.pcap`):** Enquanto relatórios JSON fornecem médias agregadas (ex: janelas de $1\text{ s}$), o arquivo `.pcap` captura **cada quadro individual** com *timestamps* de microssegundos do kernel. Isso permite inspecionar no Wireshark/Python fenômenos transitórios invisíveis no resumo agregado, como *ARP broadcast*, *3-Way Handshake*, enchimento de fila no switch, *3 Duplicate ACKs* (*Fast Retransmit*) e *Overhead* exato de cabeçalhos.

---

# Resumo das Fórmulas Críticas para a Prova 2

### 1. Camada de Rede: Plano de Dados (Capítulo 4)
* **Dimensionamento de Buffer de Roteador (RFC 3439):**
  $$B_{\text{clássico}} = \text{RTT} \cdot C \qquad \text{e} \qquad B_{\text{moderno ($N$ fluxos)}} = \frac{\text{RTT} \cdot C}{\sqrt{N}}$$
* **Limite de Vazão por *HOL Blocking* na Fila de Entrada:** $\text{Vazão}_{\text{máx}} = (2 - \sqrt{2}) \cdot R \approx \mathbf{58{,}6\% \cdot R}$
* **Garantia de Banda no *Weighted Fair Queuing* (WFQ):**
  $$R_i \ge \frac{w_i}{\sum_{j} w_j} \cdot R$$
* **Fragmentação IPv4 (Payload Máximo e Offset):**
  $$\text{Payload}_{\text{frag}} = \left\lfloor \frac{\text{MTU} - 20}{8} \right\rfloor \times 8 \qquad ; \qquad \text{Offset} = \frac{\text{Bytes de dados anteriores}}{8}$$
* **Bloco CIDR `a.b.c.d/x`:**
  $$\text{Total de IPs} = 2^{32 - x} \qquad ; \qquad \text{Hosts Utilizáveis} = 2^{32 - x} - 2$$

### 2. Camada de Rede: Plano de Controle (Capítulo 5)
* **Equação de Bellman-Ford (Vetor de Distância):**
  $$d_x(y) = \min_{v \in \text{vizinhos}(x)} \big\{ c(x, v) + d_v(y) \big\}$$
* **Relaxamento de Aresta em Dijkstra (Estado de Enlace):**
  $$D(v) = \min\big\{ D(v),\ D(w) + c(w, v) \big\}$$
* **Complexidades do Algoritmo LS (Dijkstra) com $|N|$ nós e $|E|$ arestas:**
  $$\text{Tempo (Busca Linear)} = O(|N|^2) \quad ; \quad \text{Tempo (Min-Heap)} = O(|N|\log|N| + |E|) \quad ; \quad \text{Mensagens} = O(|N|\cdot|E|)$$
* **Complexidade de Mensagens do Algoritmo DV por Iteração:** $\text{Mensagens} = O(|E|)$

### 3. Camada de Enlace e Protocolos MAC (Capítulo 6)
* **Cálculo dos $r$ bits de CRC ($R$) em Aritmética Módulo-2 (XOR) com Gerador $G$ de $r+1$ bits:**
  $$R = \text{resto}\left(\frac{D \cdot 2^r}{G}\right)$$
* **Probabilidade de Sucesso e Eficiência no Slotted ALOHA ($N$ nós):**
  $$P(\text{1 nó específico}) = p(1-p)^{N-1} \quad ; \quad P(\text{algum nó}) = N \cdot p(1-p)^{N-1} \quad ; \quad \text{Eficiência}_{\text{máx}} = \frac{1}{e} \approx \mathbf{37\%}$$
* **Probabilidade de Sucesso e Eficiência no Pure ALOHA ($N$ nós):**
  $$P(\text{algum nó}) = N \cdot p(1-p)^{2(N-1)} \quad ; \quad \text{Eficiência}_{\text{máx}} = \frac{1}{2e} \approx \mathbf{18\%}$$
* **Recuo Exponencial Binário do Ethernet (após a $m$-ésima colisão, com $n = \min(m, 10)$):**
  $$K \in \{0, 1, 2, \dots, 2^n - 1\} \quad ; \quad P(\text{escolher } K) = \frac{1}{2^n} \quad ; \quad t_{\text{espera}} = \frac{K \times 512\text{ bits}}{R}$$
* **Eficiência do CSMA/CD:**
  $$\text{Eficiência}_{\text{CSMA/CD}} = \frac{1}{1 + 5 \cdot \frac{d_{\text{prop}}}{d_{\text{trans}}}}$$

### 4. Emulação Mininet (Semana 12)
* **RTT Teórico em Topologia em Estrela ($h_1 \leftrightarrow s_1 \leftrightarrow h_2$):**
  $$\text{RTT}_{\text{teórico}} = 2 \times \big(d_{\text{prop}}(h_1, s_1) + d_{\text{prop}}(s_1, h_2)\big)$$
* **Goodput Máximo Teórico TCP sobre Enlace Gargalo Ethernet ($R_{\text{bottleneck}}$):**
  $$\text{Goodput}_{\text{máx}} = R_{\text{bottleneck}} \times \frac{\text{MSS}}{\text{MSS} + \text{Cab}_{\text{TCP}} + \text{Cab}_{\text{IP}} + \text{Cab}_{\text{Eth}}} = R_{\text{bottleneck}} \times \frac{1448}{1514} \approx 0{,}9564 \cdot R_{\text{bottleneck}}$$

---

# Quadros Comparativos Rápidos

### 1. Comparativo de Algoritmos de Roteamento: Estado de Enlace (LS) vs. Vetor de Distância (DV)

| Critério | **Estado de Enlace (*Link-State — LS / Dijkstra*)** | **Vetor de Distância (*Distance-Vector — DV / Bellman-Ford*)** |
| :--- | :--- | :--- |
| **Visão da Topologia** | **Global:** Todo nó conhece o grafo completo $G=(N,E)$ via *Link-State Broadcast*. | **Local / Descentralizada:** Cada nó só conhece seus vizinhos diretos e os vetores deles. |
| **Complexidade de CPU** | $O(|N|^2)$ (simples) ou **$O(|N|\log|N| + |E|)$ com *Heap***. | Proporcional ao número de vizinhos e destinos na tabela local. |
| **Complexidade de Mensagens** | **$O(|N| \cdot |E|)$** (inundação de pacotes LS para todos os nós). | **$O(|E|)$** por iteração (troca apenas entre vizinhos adjacentes). |
| **Velocidade de Convergência** | **Rápida** ($O(|N|^2)$), sem sofrer de contagem ao infinito. | Pode convergir **lentamente**, apresentando **Loops de Roteamento** e **Contagem ao Infinito** (*"más notícias correm devagar"*). |
| **Robustez a Falhas/Sabotagem** | **Alta:** Um roteador defeituoso pode anunciar custo errado apenas para seus próprios enlaces; cada nó calcula sua própria árvore isoladamente. | **Baixa:** Um cálculo incorreto em um nó se propaga e contamina toda a rede (como o apagão de 1997 causado por um roteador de ISP pequeno). |
| **Exemplos de Protocolos** | **OSPF**, IS-IS (e aplicações em Controladores SDN). | **RIP** (e BGP como *Path-Vector*, uma extensão do DV que carrega o `AS-PATH` completo). |

---

### 2. Comparativo de Dispositivos de Interconexão: Hubs vs. Switches vs. Roteadores (Tabela 6.1 do Livro)

| Propriedade | **Hubs (Camada 1)** | **Switches L2 (Camada 2)** | **Roteadores (Camada 3)** |
| :--- | :---: | :---: | :---: |
| **Camadas Processadas** | Apenas Camada 1 (Física — bits) | Até a Camada 2 (Enlace — quadros MAC) | Até a Camada 3 (Rede — datagramas IP) |
| **Isolamento de Tráfego / Colisão** | **Não** (1 único domínio de colisão) | **Sim** (isola domínios de colisão por porta) | **Sim** (isola domínios de colisão e de broadcast) |
| ***Plug-and-Play* (Sem Config.)** | **Sim** | **Sim** (Autoaprendizagem pelo MAC de origem) | **Não** (requer configuração de prefixos IP) |
| **Roteamento Ótimo / Ciclos** | **Não** | **Não** (restrito a uma *Spanning Tree* sem ciclos) | **Sim** (usa topologias arbitrárias com múltiplos caminhos e firewalls) |
| **Proteção contra *Broadcast Storm*** | **Não** | **Não** (inunda quadros broadcast na VLAN) | **Sim** (broadcasts L2/ARP não atravessam roteadores!) |

---

### 3. Comparativo IPv4 vs. IPv6

| Característica | **IPv4** | **IPv6** |
| :--- | :--- | :--- |
| **Tamanho do Endereço** | **32 bits** ($4\text{ bytes}$, ex: `192.168.1.1`) | **128 bits** ($16\text{ bytes}$ em hexadecimal) |
| **Tamanho do Cabeçalho** | **Variável (20 bytes mínimos** + opções) | **Fixo de 40 bytes** (opções vão em `Next Header`) |
| **Fragmentação de Pacotes** | Realizada **nos roteadores intermediários** e nos hosts (remontagem no destino). | Realizada **exclusivamente nos hosts finais** (roteador descarta e envia ICMPv6 *"Packet Too Big"*). |
| **Checksum de Cabeçalho (L3)** | **Possui** (deve ser recalculado a cada roteador por causa do TTL). | **Removido** (confia no CRC da camada 2 e no Checksum do TCP/UDP na camada 4). |
| **Resolução de Endereço Físico** | **ARP** (via broadcast Ethernet) | **NDP (*Neighbor Discovery Protocol*)** (via ICMPv6 multicast) |

---
*Bons estudos e excelente Prova 2 de CSC-35!*
