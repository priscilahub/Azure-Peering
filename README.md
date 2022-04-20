# Azure-Peering

No Azure os recursos dentro de uma Vnet podem se comunicar desde que fiquem na mesma vnet mesmo que em subnets diferentes. Mas recursos que estao em Vnets diferentes não se comunicam.

## Como eu faço pra duas Vnets diferentes se comunicarem?

Uma opção seria usar um Gateway de VPN. ( vnet-to-vnet)
	• Trouput limitado (restritos a performance desses gateways)
	• E largura de banda e Alta.

Outra opção sera usar um expressRoute 
	• Latencia alta pois os dados precisam passar primeiro por um peering location e depois acessar a segunda vnet.

## Pra isso a Microsoft criou o Peering ele nos permite conectar:

	- Vnets separadas.
	- Vnets separadas por região.
	- Vnets em assinaturas diferentes.
	- Vnets em Tenants diferentes.

Isso e feito por meio de um backbone interno da Microsoft que garante: Baixa latência, Alta largura de banda, Sem trouput limitado, Mais barato 
	
Existem 2 tipos de peering: O **Virtual Network peering** conecta redes virtuais na mesma região do Azure e o **Global virtual network peering** conecta redes virtuais que estão em diferentes regiões.
	
Tudo isso e feito por meio de endereços IP privados, criando conexões em cada vnet.
Pense em como você conecta dois comutadores de rede. Você conecta um cabo a cada comutador e talvez defina algumas configurações para que os comutadores possam se comunicar. Não tenho custo do gateway de VPN em si, o custo e definido pela quantidade de transferencia de dados que entra ou sai da sua rede.
A diferença para  o peering e que quando fazemos o emparelhamento, estou usando a infra interna na Microsoft, não tenho que sair da internet pra conectar 2 equipamentos. Quando uso a VPN eu crio um tunel de criptografia pela internet conectando esses 2 pontos.



