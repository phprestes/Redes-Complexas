# 🕸️📈 SME0130 - Redes Complexas: Questionários

Resoluções dos questionários da disciplina **SME0130 - Redes Complexas**, em notebooks Jupyter. Cada notebook resolve uma lista de questões sobre medidas topológicas, centralidade, detecção de comunidades, classificação de redes e dinâmica epidêmica.

<p align="center">
  <img alt="Disciplina" src="https://img.shields.io/badge/SME0130-Redes%20Complexas-blue?style=for-the-badge">
  <img alt="Instituição" src="https://img.shields.io/badge/USP-Universidade%20de%20S%C3%A3o%20Paulo-orange?style=for-the-badge">
</p>

> 📚 **Disciplina:** SME0130 - Redes Complexas <br>
> 👨‍🏫 **Professor:** Francisco A. Rodrigues <br>
> 🏛️ **Instituição:** ICMC - USP - Universidade de São Paulo

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter" />
  <img src="https://img.shields.io/badge/NetworkX-2C6E9B?style=for-the-badge&logo=graphql&logoColor=white" alt="NetworkX" />
  <img src="https://img.shields.io/badge/graph--tool-A8322D?style=for-the-badge&logo=gnometerminal&logoColor=white" alt="graph-tool" />
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy" />
  <img src="https://img.shields.io/badge/SciPy-0C55A5?style=for-the-badge&logo=scipy&logoColor=white" alt="SciPy" />
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="pandas" />
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="scikit-learn" />
  <img src="https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=plotly&logoColor=white" alt="Matplotlib" />
  <img src="https://img.shields.io/badge/seaborn-444876?style=for-the-badge&logo=python&logoColor=white" alt="seaborn" />
  <img src="https://img.shields.io/badge/EoN-epidemics-00A98F?style=for-the-badge" alt="EoN" />
</p>

## 📋 Requisitos

- **Python 3** e **Jupyter**
- Pacotes Python: `networkx`, `numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `EoN`
- **graph-tool** (só para o `quest7.ipynb`), que **não** instala via pip: as redes reais vêm de `graph_tool.collection.ns`

## 🚀 Como Executar

```bash
pip install networkx numpy scipy pandas matplotlib seaborn scikit-learn EoN
```

Instalação do `graph-tool`, via conda ou pacote do sistema:

```bash
conda install -c conda-forge graph-tool
# ou, em Debian/Ubuntu: apt install python3-graph-tool
```

O notebook adiciona `/usr/lib/python3/dist-packages` ao `sys.path` para achar a instalação de sistema. Depois:

```bash
jupyter lab   # ou jupyter notebook
```

Os notebooks leem os dados por caminho relativo (`data/data/...`), então execute-os a partir da raiz do repositório.

## 📂 Estrutura do Projeto

```
.
├── quest4.ipynb … quest8.ipynb   # notebooks das questões
├── resultados_redes.csv          # saída do quest7: features das 36 redes (9 reais + 27 modelos)
└── data/data/                    # bases de redes (edgelists, .gml, .pairs)
```

`resultados_redes.csv` é gerado pelo [quest7.ipynb](quest7.ipynb), com uma linha por rede e as colunas `num_nodes`, `num_edges`, `density`, `avg_degree`, `transitivity`, `assortativity`, `expectation` (⟨k⟩), `variance` (⟨k²⟩), `av_cl` (clustering médio), `l` (menor caminho médio), `nome`, `classe` (Biologica / Social / Tecnologia / Modelo) e `tipo` (Real / ER / WS / BA).

## ✨ Funcionalidades Implementadas

| Notebook | Tema | O que faz |
|---|---|---|
| [quest4.ipynb](quest4.ipynb) | Momentos do grau, complexidade e entropia | Terceiro e quarto momentos do grau (*lesmis*), medida de complexidade `<k²>/<k>` (*powergrid*), entropia de Shannon da distribuição de grau (*euroroad*), transitividade e clustering médio (*usairport*) |
| [quest5.ipynb](quest5.ipynb) | Centralidade e correlações | Eigenvector centrality média (*USairport500*), correlação de Pearson entre betweenness e grau (*hamsterster*), correlação de Spearman entre closeness e k-core (*jazz*) |
| [quest6.ipynb](quest6.ipynb) | Detecção de comunidades | Modularidade por fastgreedy e Louvain na rede *jazz*; comparação dos dois algoritmos em grafos LFR benchmark variando o parâmetro de mistura μ |
| [quest7.ipynb](quest7.ipynb) | Classificação de redes | Extrai 10 características topológicas de 9 redes reais (3 biológicas, 3 sociais, 3 tecnológicas), gera modelos nulos ER/WS/BA com mesmo N e grau médio, projeta com PCA e classifica com KNN |
| [quest8.ipynb](quest8.ipynb) | Epidemias e imunização | Modelos SI, SIR e SIS sobre redes ER, BA, WS e BA não-linear (α=0.5, α=1.5) com N=1000 e ⟨k⟩=8; compara imunização aleatória vs. imunização de hubs no modelo SIR |

### Resultados principais

**Questionário 7:** a hipótese de que redes do mesmo domínio (biológica, social, tecnológica) seguem o mesmo modelo topológico **não se sustenta**. O contexto empírico da rede não determina seu modelo gerador: redes de áreas distintas podem ter a mesma assinatura estrutural, e redes da mesma categoria podem seguir regras topológicas diferentes.

**Questionário 8:** a imunização dirigida aos hubs contém a epidemia com uma fração de imunizados muito menor que a imunização aleatória, consequência da heterogeneidade do grau em redes livres de escala.
