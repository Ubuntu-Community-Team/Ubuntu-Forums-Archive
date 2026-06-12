---
title: "Cannot access SWAT"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by stchman on 2008-03-08
Hello all, I have a problem with SWAT.

I have installed the following packages

samba
swat
netkit-inetd
tcp

I then gave root a password vis the sudo passwd root

I go to Firefox and type localhost:901 and no dice.  I get the message as follows in Firefox:

Firefox can't establish a connection to the server at localhost:901.

I have 2 other PCs running SWAT just fine.  What gives?

Any advice would be very helpful.

Thanks.

---

### Post by quanta on 2008-05-24
+ check /etc/xinetd.d/swat and # service xinetd restart (or inetd)
+ check your firewall to open port 901

---

### Post by wagb278 on 2008-05-31
stchman: Did you get SWAT access?

I am having the same problem on Ubuntu 8.04 (64-bit), but it works on version 7.10 (32-bit).

If you have it working - what did you do?

My file shares are working, but I am having trouble printing to the printer connected to the Ubuntu 8.04 system from the Ubuntu 7.10 system - yet it works printing from a Windows XP system. - I think it does, I need ink for my HP printer.  "Print test page" from local 8.04 works, from Windows XP works, but from Ubuntu 7.10 - it doesn't even move paper through the printer.

So I installed SWAT to help diagnose that problem - and I cannot connect to SWAT (localhost:901, or from other nodes on the network)

Thanks

---

### Post by headlessb on 2008-06-25
Install xinetd and that should take care of your problems for 8.04

---

### Post by NullHead on 2008-06-25
I have the same setup you do; also xinit.d. It works for me. I don't hardly use it, but I ran swat -a I believe it was .. and it works just fine.

---

