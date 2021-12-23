<div align="center">
  <h1>Consumo de API paginada com Pentaho Data Integration</h1>
</div>

### Sobre
O job cria uma rotina de consumo de dados de APIs paginadas através do Pentaho Data Integration, contemplando as etapas de extração e carga de dados para uma stage area, possibilitando o tratamento dos dados de acordo com a necessidade, o que possibilita um fluxo ETL completo.

### Tecnologias
* Pentaho Data Integration;
* SQL Server.


### Para utilizar
*	Instalar o Pentaho Data Integration. Recomenda-se a utilização da plataforma em ambiente Linux, porém o mesmo pode ser instalado em ambiente Windows;
*	Criar repositório dentro do Pentaho e adicionar os arquivos ao repositório;
*	Editar o arquivo “Executa_Job.bat”, informando o local do Kitchen, o nome do repositório e o nome do arquivo de job;
*	Editar o step "GerarUrlParametros" da transformação “UltimaPagina”, informando os dados da API. Para o exemplo criado, a autenticação é feita com os parâmetros no header e o retorno é em JSON, podendo ser ajustado conforme necessidade;

<div align="center" >
  <img src="/img/001.PNG">
</div>

*	A transformação “IncrementarLoop” não precisa ser editada;
*	Editar o step “GerarUrlParametros” na transformação “ExtrairAPIBanco” informando os dados da api, se atentando para o parâmetro que recebe o número da paginação atual. Também é necessário incluir os dados do banco de dados no último step da transformação;

<div align="center" >
  <img src="/img/002.PNG">
</div>

*	O job “Execucao” pode ser automatizado utilizando o arquivo “Executa_Job.bat”, podendo ser adicionado em qualquer agendador de tarefas, fazendo com que a execução seja periódica na janela escolhida. Uma das maneiras de automatizar o ETL é utilizando o Cronjob no Linux ou o Agendador de Tarefas no Windows.

<div align="center" >
  <img src="/img/003.PNG">
</div>
