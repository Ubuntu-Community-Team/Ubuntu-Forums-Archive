---
title: "install second lan card"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by cllow2020 on 2010-05-28
(UBUNTU10.04, server )
need help , after installed new PCI lan card but can't init ?? any missing step ?
 
> 
how@wai:~$
how@wai:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
# auto eth1
# iface eth1 inet dhcp
 
auto eth1
iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
 
auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.1
[EMAIL="how@wai:~$"]how@wai:~$[/EMAIL]
 
[SIZE=2]how@wai:~$[/SIZE]
[SIZE=2]how@wai:~$ sudo /etc/init.d/networking restart[/SIZE]
[SIZE=2]* Reconfiguring network interfaces... postconf: fatal: open /etc/postfix/main.cf: No such file or directory[/SIZE]
[SIZE=2]postconf: fatal: open /etc/postfix/main.cf: No such file or directory[/SIZE]
[SIZE=2]ssh stop/waiting[/SIZE]
[SIZE=2]ssh start/running, process 1472[/SIZE]
[SIZE=2]postconf: fatal: open /etc/postfix/main.cf: No such file or directory[/SIZE]
[SIZE=2]ssh stop/waiting[/SIZE]
[SIZE=2]ssh start/running, process 1549[/SIZE]
[SIZE=2]postconf: fatal: open /etc/postfix/main.cf: No such file or directory[/SIZE]
 

but after hard-reset , system can boot back and lan eth1 can work with SSH, i'm not feel comfortable on the message :-
<[SIZE=2]postconf: fatal: open /etc/postfix/main.cf: No such file or directory>[/SIZE]
[SIZE=2]something not right.[/SIZE]
 
[SIZE=2]any help ?[/SIZE]

---

