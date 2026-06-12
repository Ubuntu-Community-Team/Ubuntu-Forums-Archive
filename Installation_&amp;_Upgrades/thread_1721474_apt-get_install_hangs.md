---
title: "apt-get install hangs"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by kagrahar on 2011-04-04
I have installed Ubuntu 64bit 10.04 LTS version. I am trying to install open-iscsi and my apt-get install commands hangs
[COLOR=black][FONT=Arial]=====================================================[/FONT][/COLOR]
[COLOR=black][FONT=Arial][EMAIL="root@gnat"]root@gnat[/EMAIL]:~# uname -a
Linux gnat 2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux
[EMAIL="root@gnat"]root@gnat[/EMAIL]:~# apt-get install open-iscsi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  open-iscsi-utils
The following NEW packages will be installed:
  open-iscsi open-iscsi-utils
0 upgraded, 2 newly installed, 0 to remove and 20 not upgraded.
Need to get 684kB of archives.
After this operation, 1,696kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to us.archive.ubuntu.com (91.189.88.31)]
0% [Connecting to us.archive.ubuntu.com (91.189.88.31)[/FONT][/COLOR]
[COLOR=black][FONT=Arial]=================================================[/FONT][/COLOR]
[COLOR=black][FONT=Arial]my sources.list seems to be fine. What might be the issue?? never had this issue on a 32 bit version of Ubuntu 9[/FONT][/COLOR]
[COLOR=black][FONT=Arial]Any help to resolve this is very much appreciated.[/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by mörgæs on 2011-04-04
It seems like you can't connect to this mirror.

Does it help if you change mirror in Software Sources and reload the package list?

---

