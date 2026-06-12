---
title: "Acpi Module"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by am5687 on 2008-07-19
I have been trying to load UBUNTU 6.06 LTS on an Acare Aspire 5050-3785. When it get's to the ACPI Module it stops loading. From what it looks like this is a common problem. I tried adding 
noapic apci=off
noapic  apci=off noapm
noapic
pci=noacpi
pci=nomsi
None of these have worked and I checked the cd for problems and there were none.
Thanks

---

### Post by Pumalite on 2008-07-19
Try any combination of these:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off

---

### Post by am5687 on 2008-07-19
Thanks For the two new commands. I have tried them with the other ones but still am having no luck. The disc I have has a install OEM option I am now wondering if it is possible to install it that way and how hard it would be to do.

---

### Post by jimv on 2008-07-20
Just do 

acpi=off

by itself.

---

### Post by am5687 on 2008-07-20
I just tried that and it loaded farther than any other attempt but I got 
Failed to start the X server. It is likely not set up correctly. Fault now.

---

### Post by Pumalite on 2008-07-20
Try:
Ctrl+Alt+F1
username
password
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver. Accept most other defaults.

---

### Post by am5687 on 2008-07-20
When I do that what do I need to type to restart the install at the UBUNTU@UBUNTU;~$ screen

---

### Post by Pumalite on 2008-07-20
startx at the prompt.

---

### Post by am5687 on 2008-07-20
Thanks that worked and it is now installed. Now I need to figure out why it will not get online.

---

### Post by Pumalite on 2008-07-20
Post:
sudo lshw -C network
ip addr

---

### Post by am5687 on 2008-07-20
do you want to see the three lists it came up with.

---

### Post by Pumalite on 2008-07-20
Post the whole output.

---

### Post by am5687 on 2008-07-20
1: L0: <loopback, up> mtu 16436 qdisc noqueue
  link/loopback 00:00:00:00:00:00: brd 00:00:00:00:00:00:
  inet 127.0.0.1/8 scope host lo
  inet 6 ;; 1/128 scope host
    valid_lft forever prefferreed_lft forever
2: etho: <broadcast, multicast, up> mtu 1500 qdisc pf:fo_fast qlen 1000
  link/ether 00:1b:24:3e:32:65 brd ff:ff:ff:ff:ff:ff
  inet6 fe80::21b:24ff:fe3e 3265/64 scope link
  valid_lft forever preferred_lft forever
3: sito: <noapr> mtu 1480 qdisc noop
   link/sit 0.0.0.0 brd 0.0.0.0

I am pretty sure it is correct i am going to double check.

---

### Post by am5687 on 2008-07-20
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1b:24:3e:32:65 brd ff:ff:ff:ff:ff:ff
    inet 75.184.97.202/22 brd 255.255.255.255 scope global eth0
    inet6 fe80::21b:24ff:fe3e:3265/64 scope link
       valid_lft forever preferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0


ok here it is copy and pasted

---

### Post by Pumalite on 2008-07-20
It looks like you just have to configure it. In Hardy is in System>Administration>Network. There must something similar in 6.06

---

### Post by am5687 on 2008-07-20
There is but since I am new to linux I am not sure how to configure it.

---

### Post by Pumalite on 2008-07-20
How do you receive your signal?.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by am5687 on 2008-07-20
I am running a ethernet cable in from a cable modem. So I figured it would just start like windows.

---

### Post by Pumalite on 2008-07-20
Your best bet would be to install a router providing you with DHCP and a dynamic ip at boot. Then it would be automatic. Or wait for a 6.06 user that can help you.

---

### Post by am5687 on 2008-07-20
I was pretty much thinking it would be easier having the guy who takes care of the computers at the shop I work at to try to get things squared away. Thanks for all the help getting this installed.

---

### Post by Pumalite on 2008-07-20
You are welcome.

---

