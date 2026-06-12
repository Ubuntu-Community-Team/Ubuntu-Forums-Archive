---
title: "missing /usr/bin/make"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Nunana on 2006-07-05
Using:
Dell Optiplex GX280 small form factor
Pentium4 2.8GHz HT 520
ubuntu 6.06 kernel 2.6.15-23-386
Oracle DB 10g 10.2.0.1.0

Problem:
During installation of Oracle 10g I get an Error:
Unable to find make utility in location /usr/bin/make

Because I'm behind a proxy I use "sudo apt-get" to update and install.
I made a soft link to /usr/bin/imake but that will not do.

For Ubuntu 5.10
$ sudo apt-get install gcc libaio1 lesstif2 lesstif2-dev libdb1 make rpm libc6 libstdc++5
will do the trick. This statement will not help me for 6.06, afcourse.
How do I get /usr/bin/make? I can't find it anywhere.
Which packages do I have to (un)install?

---

### Post by avdelst on 2006-07-05
I've just spend an hour looking for this.
 
It's completely beyond me WHY this isn't installed by default. Also, when you search for gcc or make in the synaptic package manager is seems that the software is installed (but it isn't).

apparently you have to do:

sudo apt-get install build-essentials

from a commandline.

---

### Post by Nunana on 2006-07-05
All my messages are in dutch :-( (i tried to translate)
Reading lists . . . ready
Tree of dependencies . . . ready
Could not find package build-essentials

---

### Post by avdelst on 2006-07-05
the proxy may be the problem, maybe someone else can help with this.

Does apt-get use the http_proxy environment variable (if it is set ?)

---

### Post by Nunana on 2006-07-05
Yes. I just got an other package through the proxy.
I downloaded build-essential_11.1_i386.deb but than i get:
Error: Dependency is not satisfiable: libc6-dev|libc-dev

---

### Post by avdelst on 2006-07-05
then I hope someone else know how to fix it.

I'm new to ubuntu (NOT new to linux though), and I'm unlikely to use it after installing this one laptop for a coworker.

You may try Suse 10.1 instead, thats what I normally install on desktops & laptops. (Oracle works, C compiler can be installed from cd/dvd)

---

### Post by Nunana on 2006-07-05
Packages are coming trough the proxy. No problem there.
Maybe wrong place?

---

### Post by avdelst on 2006-07-05
I'm not sure why you have to manually download the build-essentials package.

'apt-get install build-essentials' should download & install the package automatically.

---

### Post by Nunana on 2006-07-05
This is what i get (just what i translated before):
# apt-get install build-essentials
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
E: Kon pakket build-essentials niet vinden
= Couldn't find package build-essentials

Maybe i'm missing something in /etc/apt/sources.list

---

### Post by avdelst on 2006-07-05
Maybe......

I've just wiped the laptop I was installing, can't help you any further today.

---

### Post by Nunana on 2006-07-05
Ok. I stopped my oracle-sever installation on Ubuntu.
It's a desktop client anyway. I'll try it on whitebox (redhat clone).
Thnx for your support.
I'll going to have a look at my Ubuntu PC at home where /usr/bin/make is :-)
than i can compare it with a debian distro. When I have a the solution i'll drop it somewhere.

---

### Post by avdelst on 2006-07-05
there's more on your problem here:
[http://www.ubuntuforums.org/showthread.php?t=209482&highlight=gcc](http://www.ubuntuforums.org/showthread.php?t=209482&highlight=gcc)

---

### Post by Nunana on 2006-07-06
I think THAT is the solution for my problem!
Adam S installed 6.06 from CD (no upgrade) just like me.
At home I don't have this problem. Maybe because it was Ubuntu 5.10 before.
/usr/bin/make exist here (at home).
I saved the /etc/apt/sources.list of Richbana so maybe I try it in the future.
Unfortenately i can't test it. Today I removed Ubuntu (on the test machine at my work place) and installed WhiteBox Enterprise Linux.
The main goal for now is a nice Oracle 10g R2 install. Later on when i have a test server for oracle and i need a nice desktop I will install Ubuntu again and see.
Avdelst, thank you again for helping me with this problem.
I cant wait to test it :-)
Work first :-(

---

### Post by Mekik on 2006-07-11
First of all.. i am also facing the same problem with all of you...

I am using Ubuntu 6.06 GUI. PIII 128MB RAM 10GB HDD.

Solution : under GUI interface.. using add / remove program .. you can search for make package. There is ONE package name MAKE. Install it and it should be okey...

I had successfully install make package.. so you will success too..

---

### Post by João Marcelo on 2006-08-16
The command is wrong!

Type (without 's'):
apt-get install build-essential

Sorry for my english :/  
I am brazilian!



Before I installing make but don't work.

Error log in oraInventory:
=========================
INFO: rm -f ntcontab.*

INFO: (if [ "compile" = "compile" ] ; then \
	  /u01/app/oracle/product/10.2.0/db_1/bin/gennttab > ntcontab.c ;\
	  /usr/bin/gcc  -c ntcontab.c ;\
	  rm -f /u01/app/oracle/product/10.2.0/db_1/lib/ntcontab.o ;\
	  mv ntcontab.o /u01/app/oracle/product/10.2.0/db_1/lib/ ;\

INFO:           /usr/bin/ar rv /u01/app/oracle/product/10.2.0/db_1/lib/libn10.a /u01/app/oracle/product/10.2.0/db_1/lib/ntcontab.o ; fi)

INFO: ntcontab.c:7:23: 
INFO: error: sys/types.h: Arquivo ou diretório não encontrado

INFO: mv: impossível fazer stat em `ntcontab.o': Arquivo ou diretório não encontrado

INFO: /usr/bin/ar: /u01/app/oracle/product/10.2.0/db_1/lib/ntcontab.o: Arquivo ou diretório não encontrado

INFO: make: ** [ntcontab.o] Erro 1

INFO: Finalizar saída do processo gerado.
INFO: ----------------------------------
INFO: Exceção lançada de uma ação: make
Nome da Exceção: MakefileException
String de Exceção: Erro ao chamar o destino 'ntcontab.o' do makefile '/u01/app/oracle/product/10.2.0/db_1/network/lib/ins_net_client.mk'. Consulte '/home/oracle/oraInventory/logs/installActions2006-08-13_11-32-30PM.log' para obter detalhes.
Severidade da Exceção: 1
WARNING: Isto interromperá a instalação de todos os produtos e sairá do Installer. Tem certeza de que deseja interromper a instalação e sair?
INFO: Usuário selecionado: Sim/OK
=====================

---

