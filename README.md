# risk-management-ml-databricks

## Visão Geral

Este projeto tem como objetivo desenvolver uma solução completa de Engenharia de Dados e Machine Learning para análise de risco de carteiras de investimentos utilizando a plataforma Databricks.

A proposta é implementar um pipeline ponta a ponta, desde a coleta de dados de mercado até a disponibilização de modelos de Machine Learning em produção, seguindo as principais práticas utilizadas em projetos corporativos.

Embora os fundos de investimento utilizados sejam sintéticos, todos os ativos financeiros são reais e obtidos através do Yahoo Finance, permitindo que as métricas calculadas reflitam comportamentos próximos aos encontrados no mercado financeiro.

Além da construção do pipeline de dados, o projeto contempla todo o ciclo de vida de um modelo de Machine Learning (MLOps), incluindo treinamento, versionamento, registro dos modelos e disponibilização via API utilizando o Model Serving do Databricks.

## Objetivos

O projeto busca demonstrar, de forma prática, como construir uma arquitetura moderna para análise de risco financeiro utilizando Databricks.

Os principais objetivos são:

- construir um pipeline de dados utilizando a arquitetura Medallion (Bronze, Silver e Gold);
- calcular métricas financeiras em nível de ativo e de portfólio;
- gerar um dataset de treinamento para modelos supervisionados;
- treinar modelos especializados utilizando XGBoost;
- rastrear experimentos utilizando MLflow;
- registrar e versionar modelos no MLflow Model Registry;
- disponibilizar modelos através do Databricks Model Serving;
- servir como base para uma futura aplicação web de simulação de carteiras.

## Métricas de Risco

O projeto é focado em três dimensões principais de risco financeiro:

- **Value-at-Risk (VaR)**
- **Risco de Liquidez**
- **Stress Test**

Cada uma dessas métricas será prevista por um modelo de Machine Learning independente.

## Tecnologias Utilizadas

- Databricks
- Apache Spark
- Delta Lake
- PySpark
- Pandas
- NumPy
- Yahoo Finance
- XGBoost
- MLflow
- Databricks Model Registry
- Databricks Model Serving

## Estrutura do Projeto

```
risk-management/
│
├── setup/
│   ├── create_schema.ipynb
│   └── create_fund_data.ipynb
│
├── pipeline/
│   ├── bronze.ipynb
│   ├── silver.ipynb
│   └── gold.ipynb
│
├── src/
│   ├── data/
│   │   └── build_training_dataset.ipynb
│   │
│   ├── model-training/
│   │   ├── train_var_model.ipynb
│   │   ├── train_liquidity_model.ipynb
│   │   ├── train_stress_model.ipynb
│   │   └── evaluate_models.ipynb
│   │
│   ├── model-registry/
│   │   └── register_models.ipynb
│   │
│   └── model-serving/
│       ├── create_serving_endpoint.ipynb
│       └── test_serving_endpoint.ipynb
│
├── LICENSE
└── README.md
```

## Fluxo do Projeto

```
Geração dos Fundos Sintéticos
            │
            ▼
      Pipeline Bronze
            │
            ▼
      Pipeline Silver
            │
            ▼
       Pipeline Gold
            │
            ▼
 Geração do Dataset de Treino
            │
            ▼
 Treinamento dos Modelos
            │
            ▼
 Avaliação dos Modelos
            │
            ▼
 Registro no MLflow
            │
            ▼
 Databricks Model Serving
            │
            ▼
      API de Predição
            │
            ▼
   (Futura Interface Web)
```

## Status do Projeto

- [x] Geração de fundos sintéticos
- [x] Pipeline Bronze
- [x] Pipeline Silver
- [x] Pipeline Gold
- [ ] Geração do dataset de treinamento
- [ ] Treinamento dos modelos de Machine Learning
- [ ] Avaliação dos modelos
- [ ] Registro dos modelos no MLflow
- [ ] Publicação via Model Serving
- [ ] Integração com interface web
- [ ] This is an incomplete task

## Resultado Esperado

Ao final do projeto será possível selecionar uma carteira de investimentos, calcular suas métricas de risco e utilizar modelos de Machine Learning para prever novos cenários de risco a partir de alterações na composição do portfólio.

Os modelos treinados serão disponibilizados através do Databricks Model Serving, permitindo que qualquer aplicação consuma as previsões por meio de APIs REST.

Dessa forma, o projeto demonstra o ciclo completo de uma solução moderna de Data Engineering, Machine Learning e MLOps, desde a ingestão dos dados até a disponibilização dos modelos em produção.
