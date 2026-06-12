---
title: "Samba fails to install Karmic server"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by jconstantino on 2009-12-13
Hi everyone,

I've be playing around with ubuntu server 9.10 (amd64), trying to learn to setup a home server...
I had samba working but (after update?) I notice my other machines in the network could't use samba shared resorces anymore (file & print sharing).

Samba was stopped. 
I decide to remove in order to reinstall, but now I get this error:

sudo apt-get install samba smbfs

A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está a usar a
distribuição unstable em que alguns pacotes pedidos ainda não foram 
criados ou foram movidos do Incoming.
A seguinte informação pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências não satisfeitas:
  samba: Depende: libcupsys2 (>= 1.3.4)
         Depende: libgnutls13 (>= 2.0.4-0) mas não é instalável
         Depende: libkrb53 (>= 1.6.dfsg.2) mas não é instalável
  smbfs: Depende: libkrb53 (>= 1.6.dfsg.2) mas não é instalável

I'm sorry for my bad english...used online translator (portugues to english):
sudo apt-get install samba smbfs

Reading package lists ... Ready
The build dependency tree
Reading state information ... Ready
Some packages could not be installed. This may mean that
you requested an impossible situation or if you are using the
unstable distribution that some packages have not been requested
created or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: libcupsys2 (> = 1.3.4)
         Depends: libgnutls13 (> = 2.0.4-0) but it is not installable
         Depends: libkrb53 (> = 1.6.dfsg.2) but it is not installable
  smbfs: Depends: libkrb53 (> = 1.6.dfsg.2) but it is not installable

Any help would be apreciated. Thanks in advance.

---

