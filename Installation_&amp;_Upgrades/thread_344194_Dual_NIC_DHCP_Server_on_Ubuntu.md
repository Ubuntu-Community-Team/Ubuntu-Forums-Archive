---
title: "Dual NIC DHCP Server on Ubuntu"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by raftav00 on 2007-01-22
Hello,

I'm very new to Linux but I want to get cooking on some stuff.  I have a book that has helped me tremendeously.  I'm looking for some help on setting DHCP on a server which has 2 nics.  Ubuntu has no problem recognizing the 2 nics.  I want to know if this can be done and any docs someone can point me to.

My setup will be:

5 IP phones-->Switch--->Server NIC 1 goes to Switch--->Server NIC 0 goes to a public IP.

I want to be able to have NIC 1 offer DHCP (eth 1) and NIC 2 server as a GW (eth 0) for all phones to get out on and access the internet.  This was I can have my own private segment and protect my phones from the outside.

Can this be done?
Any docs that points to a start on how to do this?


Thanks in Advance.

):P

---

### Post by scrooge_74 on 2007-01-22
You can do it

 I never quite manage to get the the DHCP server running a few months back (but it was my fault anyway) I did manage to have one NIC get IP from provider and then assign static Ip inside my network

---

