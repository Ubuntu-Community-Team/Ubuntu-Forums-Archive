---
title: "Simple internet sharing"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by walkingbeard on 2005-08-28
Hi!

My network looks like this:



Internet----------|etho(DHCP)----eth1(192.168.0.1)|---------------------192.168.0.2

My routing table looks like this, after following the advice of various people on this forum:

82.xxx.xxx.0      *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         cpc3-cowc1-5-0- 0.0.0.0         UG    0      0        0 eth0


I can ping the 192.s from each other and that's fine.  I can browse the web from the gateway machine, which is also fine.

Please can somebody give me a definitive way of browsing from the .0.2 machine?  Please don't tell me you haven't done it since the days of ipchains, because I'll never use ipchains.  If Windows can do it in a matter of seconds, a) why can't Ubuntu and b) why does anybody need to trawl through tens of web pages to find the answer?

Thanks in advance! More to follow.

---

### Post by kagashe on 2005-08-28
[QUOTE=walkingbeard]Hi!

My network looks like this:



Internet----------|etho(DHCP)----eth1(192.168.0.1)|---------------------192.168.0.2

My routing table looks like this, after following the advice of various people on this forum:

82.xxx.xxx.0      *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         cpc3-cowc1-5-0- 0.0.0.0         UG    0      0        0 eth0


I can ping the 192.s from each other and that's fine.  I can browse the web from the gateway machine, which is also fine.

Please can somebody give me a definitive way of browsing from the .0.2 machine?  Please don't tell me you haven't done it since the days of ipchains, because I'll never use ipchains.  If Windows can do it in a matter of seconds, a) why can't Ubuntu and b) why does anybody need to trawl through tens of web pages to find the answer?

Thanks in advance! More to follow.[/QUOTE]
 I think if you install Firestarter firewall on 0.1 machine you can easily set up eth0 for internet and eth1 for local network very easily. Here is the page from Firestarter online manual:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Firestarter is available through apt-get from the "universe" repository.

kagashe

---

### Post by Jason_25 on 2005-08-28
Have you seen [this](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/) page?  Check out section 3.4.  You'll want to paste that stuff into gedit and create a file called rc.firewall-iptables and save it to /etc/init.d/.  You'll need to edit to your needs. Then you should do a chroot 700 on it to make it executable.  Finally, do a update-rc.d on the same file and it should run when you reboot.  I'm sure there's a better way to do it than that though.

---

### Post by walkingbeard on 2005-08-28
Thanks!

---

