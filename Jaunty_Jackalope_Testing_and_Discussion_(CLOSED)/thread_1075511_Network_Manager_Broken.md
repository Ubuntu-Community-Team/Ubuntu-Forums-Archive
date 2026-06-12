---
title: "Network Manager Broken"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nepmit on 2009-02-20
After yesterday's update(Feb.19) I can't get on the net. I can see both wired and wireless networks but cannot connect. Anyone else have this happen? Any ideas? If not I'll reinstall.

---

### Post by rustybronco on 2009-02-20
I downloaded J/J daily build 19-Feb and ran it off the live cd, but I didn't install it. NM worked fine for me.

---

### Post by philobyte on 2009-02-20
me too.  Totally broken as of last night (19th), looks like even if I manage to connect, the routes are borked (not accepting the dhcp routes.)

It is seriously toast.  I killed all the network manager related processes, then logged in by putting the following in my /etc/network/interfaces file

iface eth0 inet dhcp

and connecting via copper... but I recall it being painful to do for wireless.

---

### Post by syko21 on 2009-02-21
This looks like it might be related to a problem I've been having as well. I documented it here [https://bugs.launchpad.net/ubuntu/+bug/330755](https://bugs.launchpad.net/ubuntu/+bug/330755)
The basic gist of it is that the external internet does not work on certain access points or connection types (haven't been able to narrow down what the exact culprit is) but local network works fine. Some routers may allow you to access the internet, I tried going on my neighbor's wifi which worked for me.

---

### Post by Peter09 on 2009-02-21
I have had a problem with connecting to my router for a while in Jaunty, not quite sure what was going on. Today I could not connect at all. I sooved it in the end by blacklisting the ath5k module and then going to hardware->drivers a enabling the third party driver again, its installed the ath module and its working.

peter@toshsat:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:92:26:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.7 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

