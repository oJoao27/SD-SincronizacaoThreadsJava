# Relatório Técnico – Sincronização de Threads em Java

**Aluno:** João Gabriel  
**Data:** 05/11/2025  
**Disciplina:** Sistemas Distribuídos  
**Atividade:** Práticas 01, 02 e 03 – Sincronização de Threads  

---

## Atividade Prática 01 – Sem Sincronização

**Logs analisados:**  
`MeuDadoThreadsJava_20251105_223038.log` e `MeuDadoThreadsJava_20251105_223104.log`

**Trecho do log:**

- Produtor: 4
- Consumidor: 4
- Consumidor: 4
- Produtor: 5
- Consumidor: 5

**Análise:**
- As saídas variam entre as execuções.
- O mesmo valor é lido e escrito múltiplas vezes de forma incorreta.
- As threads acessam o recurso compartilhado simultaneamente, gerando **condições de corrida** e **inconsistência de dados**.

**Conclusão:**  
Sem sincronização, o resultado é imprevisível e inconsistente. Cada execução produz uma sequência diferente.

---

## 🔒 Atividade Prática 02 – Sincronização com Monitores

📄 **Log analisado:**  
`log_monitor_1.txt`

**Trecho do log:**

Consumidor usando Monitor: 0
Produtor usando Monitor: 0
Armazenar Iniciando...
Armazenar Finalizando...
Produtor usando Monitor: 1
Carregar Iniciando...
Carregar Finalizando...
Consumidor usando Monitor: 1


**Análise:**
- O uso de `synchronized`, `wait()` e `notify()` garante que apenas uma thread por vez acesse o recurso.
- Há alternância perfeita entre produtor e consumidor.
- O resultado é determinístico, sem sobreposição de acessos.

✅ **Conclusão:**  
A sincronização via **monitores** garante **exclusão mútua** e elimina as condições de corrida.

---

## ⚡ Atividade Prática 03 – Sincronização com Eventos

📄 **Log analisado:**  
`log_eventos_1.txt`

**Trecho do log:**

Produtor usando Eventos: 0
Consumidor usando Eventos: 0
Produtor usando Eventos: 1
Consumidor usando Eventos: 1

**Análise:**
- O código utiliza comunicação direta entre threads por meio de **eventos (`wait()` / `notify()`)**.
- Há alternância entre produtor e consumidor, mas com pequenas variações na ordem, indicando notificações múltiplas.
- O método oferece **maior flexibilidade e controle**, permitindo que threads reajam a mudanças de estado específicas.

**Conclusão:**  
A sincronização por **eventos** mantém a consistência dos dados e permite comunicação mais refinada entre threads, sendo ideal para cenários mais complexos.

---

## Conclusão Final

As três atividades demonstram claramente a **evolução da sincronização em Java**:

- Sem sincronização → resultados imprevisíveis.  
- Com monitores → segurança e exclusão mútua.  
- Com eventos → coordenação flexível e controle refinado.

O uso correto de técnicas de sincronização é essencial para garantir consistência, previsibilidade e segurança em sistemas concorrentes.  
Cada abordagem tem sua aplicação ideal, dependendo da complexidade e dos requisitos de comunicação entre as threads.

---

