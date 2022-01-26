<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Classificação de Falhas em poços do tipo "Stripper Well".

#### Aluno: [Richard Peters](https://github.com/richpe87/TCC_MasterBI)
#### Orientador: [Felipe Borges](https://github.com/link_do_github)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->
- [Link para o código](https://github.com/link_do_repositorio). <!-- caso não aplicável, remover esta linha -->

- [Link para a monografia](https://link_da_monografia.com). <!-- caso não aplicável, remover esta linha -->

---

### Resumo

Os poços do tipo "Stripper Well", apesar de se tratarem daqueles próximos do fim da vida útil economica, ainda são responsáveis por boa parte da produção de Óleo e Gás dos EUA. Dada sua baixa produção individual, os gastos com sua manutenção precisam ser planejados de forma a otimizar o retorno. 

O foco deste trabalho é de identificar a ferramenta de Inteligencia Artificial que melhor se adequa a classificação de um novo evento de falha entre "surface" e "downhole", a partir do treinamento em uma base de dados de falhas posteriores. Classificar novos eventos permitirá que a empresa operadora possa planejar corretamente o tipo de intervenção necessária, assim como correta alocação de recursos. 


### Abstract 

The Stripper Wells, despite of being the ones near to the end of its economics life, still are responsible for a considerable portion of EUA' Oil and Gas production. Due to its low individual production capacity, the maintenance expenses must be planned to optimize the profits. 

The main objectiv of this work is to identify an Artificial Integilence tool that classifies a new failure event between "surface" and "downhole", based on a training with previous failures data base. To classify new events allows the company to proper plan the workover/intervation and the resources needed.  

### 1. Introdução

Os poços denominados "Stripper Well" são aqueles de superfície, que possuem produção entre 1-15bbl/d de Óleo, ou equivalente de Gás. 

De acordo com a NSWA (National Stripper Well Association), este tipo de poço foi responsável por aproximadamente 11,3% da produção de Óleo, e 8,3% da produção de Gás dos EUA em 2017, quando existiam em torno de 770 000 poços operacionais ao redor do país.  

Este trabalho foi baseado em um desafio liberado no site Kaggle, onde tem-se por objetivo identificar um método de classificação de tipo de falha de poços do tipo "stripper well", entre "surface" (superfície) e "downhole" (fundo). 

Do site foi utilizada apenas a base de dados de falha, e o objetivo do desafio, porém este trabalho não fez parte da competição.

A base é constituída de dados de medições de sensores espalhados no poço, coletados em cada evento de falha. Ao analisar a base com ferramentas inteligentes, devemos ser capazes de classificar o tipo de falha que aquelas medições indicam, de forma a direcionar os esforços de planejamento estratégico e financeiro da empresa, durante a mobilização de equipe para solução das ocorrências. 


### 2. Modelagem

Durante o estudo, iremos aplicar diferentes métodos de classificação, de forma avaliar o desempenho de cada um, com diversas configurações, e indicar aquele que se apresenta a eficiência para o problema proposto.

Os métodos utilizados foram:

-	*Random Forest*
-	*Decision Tree*
-	*Redes Neurais MLP (Multi-Layer Perceptron)*

A base de dados foi separada entre treino e teste, com tamanhos de 85% e 15% da base, respectivamente. A base de treino foi dividida novamente, de forma que pudesse ser utilizado 20% de seus dados para validação, quando utilizado o método de Rede Neural MLP.

Após os treinamentos, os modelos foram aplicados sobre as bases de teste, e os dados gerados foram comparados com os "verdadeiros", utilizando a métrica "*precision_recall_fscore_support*", do scikit Learn (sklearn). 

### 3. Resultados

Para cada método, e configuração de um mesmo método, foram salvos os resultados da métrica de validação (*precision*, *recall*, *fscore*). Adicionalmente, foram salvas as Árvores de Decisão para os métidos *Random Forest* (somente a primeira árvore) e *Decision Tree*, e para as redes MLP foram salvos os gráficos de Acurária e Perda de treino/validação de treino, e o gráfico de perda somente da validação, para observação mais detalhada dos comportamentos. Outro parâmetro que foi anotado foi o tempo de treinamento das bases, pois trata-se de uma informação relevante no processo de decisão do modelo/método ideal.

### 4. Conclusões

|**Teste**|**_Presicion_**|**_Recall_**|**_fscore_**|**Tempo de Treino**|
|---|---|---|---|---|
|*Random Forest* Normalizado|0.9998870439399073|0.9932885906040269|0.9965651372113189|18,74s|
|*Random Forest* Não Normalizado|1|1|1|35,39s|
|*Decision Tree* Normalizado|1|1|1|1,06s|
|*Decision Tree* Não Normalizado|1|1|1|0,99s|
|MLP 1|0.9917222222222222|0.5|0.4958265643381323|57s (18 épocas)|
|MLP 2|0.9917222222222222|0.5|0.4958265643381323|104s (33 épocas)|
|MLP 3|0.9917222222222222|0.5|0.4958265643381323|41s (12 épocas)|
|MLP 4|0.9917222222222222|0.5|0.4958265643381323|55s (20 épocas)|
|MLP 5|0.9917222222222222|0.5|0.4958265643381323|75s (24 épocas)|
|MLP 6|0.9917222222222222|0.5|0.4958265643381323|69s (27 épocas)|
|MLP 7|0.9917222222222222|0.5|0.4958265643381323|50s (16 épocas)|
|MLP 8|0.9917222222222222|0.5|0.4958265643381323|69s (19 épocas)|
|MLP 9|0.9917222222222222|0.5|0.4958265643381323|75s (20 épocas)|
|MLP 10|0.9917222222222222|0.5|0.4958265643381323|83s (23 épocas)|
|MLP 11|0.9917222222222222|0.5|0.4958265643381323|75s (22 épocas)|
|MLP 12|0.9917222222222222|0.5|0.4958265643381323|99s (29 épocas)|
|MLP 13|0.9917222222222222|0.5|0.4958265643381323|52s (19 épocas)|

Pode-se concluir que, apesar das redes *Multi-Layer Perceptron* ser uma ferramenta de inteligência artificial bastante robusta para tratamento de dados em grande volume e complexidade, para o problema apresentado, os métodos de aprendizado *Random Forest* e *Decision Tree* apresentaram performance superior tanto em velocidade de treino, quanto em capacidade de predizer a classe dos eventos de falha.

Dentre os dois métodos mais eficazes, o *Decision Tree* foi o que sobressaiu, devido ao tempo necessário para treino do modelo. Observou-se também que, para este método, a normalização não influenciou no resultado final de forma expressiva, tendo alcançado o mesmo resultado com 0,07s a mais de tempo de treino, o que é imperceptível.

Haja visto o supracitado, optou-se por definir o *Decision Tree* não normalizado como o modelo ideal de classificação do tipo de falha dos poços do tipo *Stripper Well*, em atendimento a proposta do trabalho. 

---

Matrícula: 201.110.002

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
