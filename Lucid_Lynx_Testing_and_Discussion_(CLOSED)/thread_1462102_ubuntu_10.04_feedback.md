---
title: "ubuntu 10.04 feedback"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by megaexception on 2010-04-25
i've already installed ubuntu 10.04 on 6 systems including 4 servers, 1 laptop, and 1 virtual machine. so i think i can give some feedback on positive and negative changes.

1) system is much faster than 9.10 or any other linux system i've used:
* boot time is very impressive (3-6 seconds)
* virtualization is much faster (it is one of the main functions of my servers)
* disk io, filesystem io is very good


2) plymouth is an EPIC FAIL:
* on 6 of 6 my systems, it transformed system to black box: i cannot see what is happening at boot time, and if anything goes wrong, i have very hard times to figure it out.
* it it dependency for vast amount of packets, so i cannot do apt-get purge plymouth
* on my laptop, plymouth leaves my completely without text console, and i've found no way to get console other than chmod -x plymouthd plymouth
* there are no verbose init-script messages, they are completely quiet

examples of "blackbox problems":
* nfs filesystems cannot be mounted - i got black screen and do not know why system is not booting
* X is not starting - i got black screen and do not know why system is not booting
* root fs is corrupt and requires manual fsck - i got black screen and do not know why system is not booting
* ahci driver have a problem with ncq - i got black screen and do not know why system is not booting
* snd-hda-intel hangs while probing codec settins - i got black screen and do not know why system is not booting
... and many others. if i am lucky, i can get text console using ctrl-alt-fX, but it not always helpful, because on vty consoles there are no kernel messages, init-script messages, basically, they are always blank!


3) there are lot problems with packeges of new software, initial configuration, etc.
for example dpkg --reconfigure slapd doesn't correctly install ldap database and do not create ldap root account. i've spent much time figuring out how to initialize ldap manualy


4) there are lot problems with documentation.
again, openldap documentation is very outdated.

---

### Post by megaexception on 2010-04-25
5) networking and wifi.it is awful.
networkmanager is completely useless. especially with kubuntu.
wicd in 10.04 became very buggy (in 9.10 it worked much better).
wifi (iwlagn/intel 5100) stopped to work.
/etc/network/interfaces doesn't configure simple static interface config after upgrade from 9.04.
lot of problems with init scripts, old rc.local now cannot configure iptables, had to write upstart script.
libvirtd erases my iptables config, creates some random bridges, and makes me very angry

---

