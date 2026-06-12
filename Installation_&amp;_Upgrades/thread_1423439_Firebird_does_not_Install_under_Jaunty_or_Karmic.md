---
title: "Firebird does not Install under Jaunty or Karmic"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by rrrobles on 2010-03-06
I have two computers, one running Jaunty, another Karmic. In both the computers when I try to install firebird2.1-classic or firebird2.1-super I get an unresolved dependencies message. 
Someone got the same problem?

The output follows:

rodrigo@rodrigo-laptop:~$ sudo apt-get install firebird2.1-super
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Pacotes sugeridos:
  firebird2.1-doc
Os pacotes a seguir serão REMOVIDOS:
  firebird2.1-classic
Os NOVOS pacotes a seguir serão instalados:
  firebird2.1-super
0 pacotes atualizados, 1 pacotes novos instalados, 1 a serem removidos e 49 não atualizados.
3 pacotes não totalmente instalados ou removidos.
É preciso baixar 3525kB de arquivos.
Depois desta operação, 3695kB adicionais de espaço em disco serão usados.
Você quer continuar [S/n]? s
Obter:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) jaunty/universe firebird2.1-super 2.1.1.17910-release.ds1-1ubuntu1 [3525kB]
Baixados 3525kB em 10s (332kB/s)                                               
Pré-configurando pacotes ...
(Lendo banco de dados ... 220806 arquivos e diretórios atualmente instalados).
Removendo firebird2.1-classic ...
Selecionando pacote previamente não selecionado firebird2.1-super.
(Lendo banco de dados ... 220786 arquivos e diretórios atualmente instalados).
Desempacotando firebird2.1-super (de .../firebird2.1-super_2.1.1.17910-release.ds1-1ubuntu1_i386.deb) ...
Configurando firebird2.1-server-common (2.1.1.17910-release.ds1-1ubuntu1) ...
dpkg: erro processando firebird2.1-server-common (--configure):
 sub-processo post-installation script retornou estado de saída de erro 1
dpkg: problemas de dependência impedem a configuração de libfbembed2.1:
 libfbembed2.1 depende de firebird2.1-server-common (= 2.1.1.17910-release.ds1-1ubuntu1); porém:
  Pacote firebird2.1-server-common não está configurado ainda.
dpkg: erro processando libfbembed2.1 (--configure):
 problemas de dependência - deixando desconfigurado
dpkg: problemas de dependência impedem a configuração de firebird2.1-super:
 firebird2.1-super depende de firebird2.1-server-common (= 2.1.1.17910-release.ds1-1ubuntu1); porém:
  Pacote firebird2.1-server-common não está configurado ainda.
dpkg: erro processando firebird2.1-super (--configure):
 problemas de dependência - deixando desconfigurado
Nenhum relatório do apport gravado porque a mensagem de erro indica é o seguimento de um erro de uma falha anterior.
                                    Nenhum relatório do apport gravado porque a mensagem de erro indica é o seguimento de um erro de uma falha anterior.
                                                                        Erros foram encontrados durante o processamento de:
 firebird2.1-server-common
 libfbembed2.1
 firebird2.1-super
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

