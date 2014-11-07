<!--#include file="include/conexao.asp"-->
<!--#include file="include/verifica.asp"-->
<%'PARÂMETROS OBRIGATÓRIOS
wprograma			= "pg_ae_040"
wvariavel			= null

SET QRY_MAQ = conexao.execute("pr_it_ler_maquinas")
%>

<!--#include file="include/top.asp"-->
<table width="98%" border="1" cellspacing="0" cellpadding="0" class="cabecalho">
<tr>
	<td width="220">Equip.</td>
    <td widtd="100">Série</td>
    <td widtd="200">Cliente</td>
    <td widtd="100">Dt. Entrega</td>
	<td widtd="100">Dt. Saída</td>
	<td widtd="100">Prev. Instalação</td>
	<td widtd="100">Tec. Responsável</td>
</tr>
<tr>
	<td colspan="50" bgcolor="#7F7F7F" height="1"></td>
</tr>
</table>

<div id="scroll" divisor="40">
<table width="100%" border="1" cellspacing="0" cellpadding="0">
	<td width="220">
	<select name="status_cod" class="form" >
		<option value=""></option>
		<%DO UNTIL QRY_MAQ.EOF%>						
			<option value="<%=QRY_MAQ("item_cod")%>" <%IF item_cod = QRY_MAQ("item_cod") THEN response.write "selected"%>><%=QRY_MAQ("item_descricao")%></option>
		<%QRY_MAQ.MOVENEXT
		LOOP%>
	</select>
	</td>
	<td>
		ABC
	</td>
</table>
</div>
<!--#include file="include/bottom.asp"-->

<%'FECHA CONEXÃO COM O BANCO DE DADOS
QRY_MAQ.CLOSE			:	SET QRY_MAQ 		= nothing
CONEXAO.CLOSE			:	SET CONEXAO 		= nothing%>
