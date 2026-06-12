---
title: "mysql odbc connector installation crash"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by lamprvm on 2010-09-14
Hi everyone:
I use ubuntu lucid lynx, LAMP (mysql 5.1 and last php) and tried to install the package from mysql web page (mysql-connector-odbc-5.1.7-linux-glibc2.3-x86-32bit.tar.gz) through alien. Terminal output is as follows:   	 	 	 	p { margin-bottom: 0.21cm; }  

 “$ sudo alien -d -c -k -i mysql-connector-odbc-5.1.7-linux-glibc2.3-x86-32bit.tar 
 	dpkg --no-force-overwrite -i mysql-connector-odbc_5.1.7-1_all.deb 
 (Lendo banco de dados ... 147517 arquivos e diretórios atualmente instalados). 
 Preparando para substituir mysql-connector-odbc 5.1.7-0 (usando mysql-connector-odbc_5.1.7-1_all.deb) ... 
 myodbc-installer: symbol lookup error: myodbc-installer: undefined symbol: SQLRemoveDriverW 
 dpkg: aviso: antigo script pre-removal retornou um erro 127 como status de saída 
 dpkg - tentando script do novo pacote em vez disso ... 
 dpkg: erro processando mysql-connector-odbc_5.1.7-1_all.deb (--install): 
  não há script na nova versão do pacote - desistindo 
 myodbc-installer: symbol lookup error: myodbc-installer: undefined symbol: SQLInstallDriverExW 
 dpkg: erro enquanto efetuava a limpeza: 
  sub-processo script post-installation instalado retornou estado de saída de erro 127 
 Erros foram encontrados durante o processamento de: 
  mysql-connector-odbc_5.1.7-1_all.deb 
 Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <FILELIST> line 15. 
 	find mysql-connector-odbc-5.1.7 -type d -exec chmod 755 {} ; 
 	rm -rf mysql-connector-odbc-5.1.7 ”
 

 After this crash, when opening Synaptic I got the following msg:
 

 E: O pacote mysql-connector-odbc precisa ser reinstalado, mas não foi possível encontrar um arquivo para o mesmo. 
 E: Erro interno ao abrir o cache (1). Por favor reporte."
After I click close, Synaptic crash.


It is in portuguese (I'm from Brazil), but I believe the code is understandable.


 Briefly, alien found an error in processing the file, get an error 127, and now Synaptic can't found the package to correct the error and get an error opening cache.
I already tried to correct through a sequence of commands in <https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure>, but with no success.
Can anyone help me? I do not want to do a unnecessary reinstall.
Thanks is advance,
Rafael

---

### Post by lamprvm on 2010-09-15
Well, I founded an solution for my problem.:p
Somebody with the same problem in:

[http://www.debianhelp.org/node/16264](http://www.debianhelp.org/node/16264)

In bottom of this page there is a link for:

[http://forum.freespire.org/archive/index.php/t-3429.html](http://forum.freespire.org/archive/index.php/t-3429.html)

Which led me to edit the status file in /var/lib/dpkg/status

And deleting the entry relative to mysql-connector-odbc.
Now I can open synaptic and solve my problems.
Hope this can help someone.

Cheers to everybody,

---

