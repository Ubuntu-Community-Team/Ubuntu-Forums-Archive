---
title: "How to upgrade 8.04 using ssh connection"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by josir on 2010-04-08
Hi folks, I'm trying to upgrade a remote Ubuntu 8.04 server to a newer release. Following some tutorials, I tried:

root@linux18:/etc/apt#** lsb_release -a**
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.4 LTS
Release:	8.04
Codename:	hardy
root@linux18:/etc/apt#  **sudo apt-get install update-manager-core**
Lendo lista de pacotes... Pronto
Construindo árvore de dependências       
Reading state information... Pronto 
update-manager-core já é a versão mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
root@linux18:/etc/apt#** do-release-upgrade**
Checking for a new ubuntu release
No new release found

Now I am stucked. Does somebody has a tip for doing this upgrade?

Thanks in advance,
Josir.

---

### Post by josir on 2010-04-09
Just to notice the solution found: I have to go the server location to do a graphical update with update-manager -c.

It seems that do-release-upgrade does not work on 8.04 because when I tried to issue the same command on 8.10, it recognizes a new version (9.04) to be updated.

---

