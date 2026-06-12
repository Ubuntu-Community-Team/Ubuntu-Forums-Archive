---
title: "Ubuntu &amp; Firewall"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by shmk on 2005-03-20
Ubuntu has for default installed a software firewall or I need to install one ?

If the answer is yes:
"Where I can find it ? How I configure it ?"
If the answer is no:
"I really need one ? Which is the better (free) ?"
If the answer is BOH! :
"Thx for had read this message but I don't need your hand  :wink: "

---

### Post by Buffalo Soldier on 2005-03-20
[QUOTE=shmk]Ubuntu has for default installed a software firewall or I need to install one ?

If the answer is yes:
"Where I can find it ? How I configure it ?"
If the answer is no:
"I really need one ? Which is the better (free) ?"
If the answer is BOH! :
"Thx for had read this message but I don't need your hand  :wink: "[/QUOTE]All the answer is there if you were to take the time to search at Google or use this forums search button.

One of many firewalls for GNU/Linux is FireStarter. The basic instruction is available at [Q: How to install Firewall (Firestarter)?](http://ubuntuguide.org/#firestarter)

Some threads in this forum that discuss about FireStarter:[list]
[*] [http://ubuntuforums.org/showthread.php?t=13659](http://ubuntuforums.org/showthread.php?t=13659)
[*] [http://ubuntuforums.org/showthread.php?t=17983](http://ubuntuforums.org/showthread.php?t=17983)
[*] [http://ubuntuforums.org/showthread.php?t=15890](http://ubuntuforums.org/showthread.php?t=15890)
[*] [http://ubuntuforums.org/showthread.php?t=15081](http://ubuntuforums.org/showthread.php?t=15081)
[/list]

[UbuntuGuide.org](http://ubuntuguide.org/) is a good place to start before posting questions here.

Haven't tried it on Hoary. But anyway, not much of a need of firewall when you don't have ports open by default.

---

### Post by az on 2005-03-20
If you do not know of a reason to use one, you do not need one in Ubuntu.  If you install things that put your privacy or security at risk, you can think about getting one.

Firestarter, guraddog (kde) or shorewall

---

### Post by grim on 2005-03-21
hi everybody.
maybe i understood something wrong, but isn`t firestarter not just a programm to edit your iptables configuration the easy way? iptabels is included in the kernel by default, or am i wrong?

greetings, grim

---

### Post by telmo on 2005-03-21
I think so too, i don't know if i'm wrong though... But what about Fireflier?
Can i set it up? If yes... how?

thx

---

### Post by bored2k on 2005-03-21
Linux and Firewalls

[http://wiki.linuxquestions.org/wiki/Firewall](http://wiki.linuxquestions.org/wiki/Firewall)

---

### Post by az on 2005-03-21
It is the Linux kernel that inspects the packets and modifies the addresses in the packet headers (the NAT function) before forwarding them on to the final destination system (whether that is an Internet server for outgoing packets or a network workstation for incoming packets)

Two other great links:
[http://aboutdebian.com/firewall.htm](http://aboutdebian.com/firewall.htm)
[http://aboutdebian.com/proxy.htm](http://aboutdebian.com/proxy.htm)

---

### Post by emperor on 2005-03-21
[QUOTE=grim]hi everybody.
maybe i understood something wrong, but isn`t firestarter not just a programm to edit your iptables configuration the easy way? iptabels is included in the kernel by default, or am i wrong? greetings, grim[/QUOTE]

You are right!

The debian documentation "azz" posted will lead you down a long twisted road the wrong direction! IPCHAINS is not the answer, use IPTABLES via a user friendly layer like firestarter or shorewall.

---

