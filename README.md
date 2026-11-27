
📝 Como elaborei esta análise (Árvores de Regressão — Boston Housing)

1. Adaptação da Base e Validação de Integridade:
• Como a base clássica de Boston foi removida das versões mais recentes do Scikit-Learn por questões éticas, adaptei o carregamento lendo os dados diretamente do arquivo BostonHousing.csv via pd.read_csv() e separei as variáveis explicativas (X) da variável resposta (y = medv).
• Antes de iniciar a modelagem, realizei uma checagem de qualidade exigida pelo Scikit-Learn, confirmando a ausência de dados faltantes (.isna().sum()) e garantindo que todas as colunas estavam em formato numérico (.dtypes).
2. Análise de Correlação (Heatmap):
• Calculei a matriz de correlação (.corr()) e construí um mapa de calor divergente (sns.heatmap com cmap='PiYG' e center=0) para facilitar a distinção visual entre correlações positivas e negativas.
• Com isso, identifiquei rapidamente as variáveis com maior potencial preditivo sobre o valor dos imóveis (medv), destacando lstat (-0,74) e rm (0,70), seguidas por ptratio, indus, tax e nox.
3. Divisão dos Dados e Treinamento das Árvores (DecisionTreeRegressor):
• Utilizei train_test_split para dividir o conjunto de dados em 75% para treinamento e 25% para teste.
• Treinei dois modelos de árvores de regressão com níveis diferentes de complexidade: uma árvore mais simples e restrita (max_depth=2) e outra mais profunda (max_depth=8), permitindo comparar o comportamento de subajuste (underfitting) versus sobreajuste (overfitting).
4. Avaliação de Métricas e Visualização da Estrutura:
• Avaliei o desempenho das duas árvores calculando o Erro Quadrático Médio (MSE) na base de teste e o coeficiente de determinação (R²) na base de treino.
• Identifiquei que a árvore de profundidade 8 alcançou um erro bem menor no teste (13,81 contra 28,79), mas apresentou forte indício de overfitting ao atingir R² = 0,97 no treino.
• Por fim, utilizei tree.plot_tree com preenchimento de cores (filled=True) para visualizar a estrutura da árvore mais profunda e inspecionar quais variáveis guiaram as divisões dos nós.
Se você quiser, posso:
• Formatar este texto em um README.md completo para o GitHub
• Gerar o código ajustado da Questão 5 calculando o MSE tanto no treino quanto no teste para comprovar o overfitting



exercicios 02 - 
💡 Explicação de Como Elaborei o Projeto

Para resolver esse desafio de previsão de valores imobiliários com Árvores de Regressão, estruturei o meu raciocínio em quatro etapas lógicas:
Primeiro, precisei contornar o fato de a base de Boston não estar mais disponível nativamente no Scikit-Learn. Busquei o dataset BostonHousing.csv em um repositório externo, carreguei com o Pandas e separei as variáveis explicativas (X) da variável alvo (medv). Antes de qualquer modelagem, garanti que os dados atendiam aos pré-requisitos do algoritmo: verifiquei que não havia valores nulos e confirmei que todas as colunas eram numéricas.
Na segunda etapa, antes de treinar os modelos, fiz uma análise exploratória usando uma matriz de correlação plotada em um mapa de calor divergente (PiYG centralizado em zero). Isso me permitiu enxergar de forma visual quais variáveis tinham mais relação com o preço das casas — destacando imediatamente lstat (correlação negativa de -0,74) e rm (correlação positiva de 0,70).
Com os dados validados e compreendidos, parti para a modelagem. Dividi a base em 75% para treino e 25% para teste usando train_test_split, garantindo uma avaliação justa em dados inéditos. Treinei duas árvores de regressão (DecisionTreeRegressor) com profundidades bem distintas (max_depth=2 e max_depth=8) justamente para observar na prática como o aumento da complexidade afeta o aprendizado.
Por fim, avaliei os resultados comparando o Erro Quadrático Médio (MSE) no teste e o R² no treino. Percebi que a árvore mais profunda (max_depth=8) reduziu o erro pela metade no teste em comparação à árvore rasa (13,81 contra 28,79), mas o seu R² de 0,97 no treino acendeu um alerta claro de overfitting (quando o modelo decora os dados de treino). Para fechar, plotei a estrutura visual da árvore (plot_tree) para inspecionar como o algoritmo tomava as decisões e quais variáveis apareciam nos nós principais.
Se você quiser, posso:
• Formatar este projeto em um README.md pronto para o GitHub
• Escrever uma versão curta deste texto para postar no LinkedIn
