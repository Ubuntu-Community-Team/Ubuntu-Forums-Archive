---
title: "apt-get doesn't work when trying to upgrade dapper server to edgy"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by mielie007 on 2007-02-21
i have now downloaded ubuntu 6.10 server (edgy)

i am currently running dapper i386 on my one pc.

i have desided to upgrade to edgy cause i can't get my PPPoE modem set up on it. 

i have read the release notes for edgy on how to upgrade for dapper to edgy, but when i enter the "apt-get dist-upgrade" command it just gives me the following notification.:confused: 

root@Dapper-Drakie:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Dapper-Drakie:~#

please can somebody help.

---

### Post by jtapper on 2007-02-21
I suggest you read [http://www.ubuntuforums.org/showthread.php?t=286599&highlight=upgrade+dapper+to+edgy](http://www.ubuntuforums.org/showthread.php?t=286599&highlight=upgrade+dapper+to+edgy)

---

### Post by Kateikyoushi on 2007-02-21
Dist upgrade just tries to upgrade your installation to the newest packages.
Read this about upgrading. [LINK]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by mielie007 on 2007-02-21
Thanks i got it

had to run apt-cdrom fist and add the new edgy cd that i downloaded.

after that i ran apt-get update and then apt-get upgrade with success.:KS

---

