---
title: "[SOLVED] help please! no network and X11 after dist-upgrade"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Nycticorax on 2008-03-08
I have caused myself severe problems by attempting to do a dist-upgrade from dapper (5.10) to gutsy. I'm just going to outline the situation I'm in now. If anyone could offer advice , then I would very much appreciate that.

The initial problem was that X would not start as there were dependency problems with key x11 packages (e.g. x11-common) In the course of trying to resolve them, I used dselect and allowed it to remove some packages thinking that it would remove broken packages and eventually allow me to resolve the X11 dependency problems. However it seems that whatever dselect did, it took away my network connection (sudo ifup eth0 reports no such device).

So I now have no network and no X11 on the computer I was trying to upgrade. Could someone please help me get the networking going again? At the moment it looks like some of my apt-get install commands might lead somewhere positive if they were able to download the packages.:(

---

### Post by MeURi on 2008-03-08
What do you have in your */etc/network/interfaces* file?

Mine looks like this:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
auto eth0

```
and if I issue an *ifconfig*, I get:
```

eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:##  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fefd:6b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1269094 (1.2 MB)  TX bytes:237761 (232.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

See if something screwed your interfaces file

I use static IP addresses in my home network, if you need DHCP specify
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

```
in your interfaces file

Hope this helps

---

### Post by MeURi on 2008-03-08
Forgot one thing...

If you change your configuration file, you have to restart the networking

```
$ sudo /etc/init.d/networking restart
```

---

### Post by Nycticorax on 2008-03-08
Thanks a lot,

My /etc/network/interfaces file contains

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet dhcp


/etc/init.d/networking restart fails with messages like
eth0: no such device 

I just managed to install network-manager by downloading the required .debs elsewhere but that hasn't got my networking working (even after reboot)

So I'm still stuck not knowing how to get my networking working. I may try adding a static entry to my /etc/networking/interfaces file tomorrow morning, but that's just going to fail with the same eth0 no such messages isn't it?

---

### Post by MeURi on 2008-03-09
Yep, probably it won't solve your problem, either...

What's the output of *lspci* for your network card? I have:
```

$ lspci | grep Ethernet
02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02))

```
My card requires kernel module *tg3*. Search the web for the right kernel module for your card and try to *modprobe* it, then restart networking
Maybe (I assume you boot with your new Gutsy kernel, rather than with your old Dapper one), do also a *depmod* before modprobing
```

$ sudo depmod -a
$ sudo modprobe *tg3* #assuming you have the same network card
$ sudo /etc/init.d/networking restart

```
If everything goes well, and at next reboot you still have no network, add your network card kernel module to your */etc/modules* file

---

### Post by MeURi on 2008-03-09
Another solution could be using *apt-cdrom* to add the Gutsy cd as source, and then to reinstall the whole *ubuntu-desktop* metapackage (if you use Ubuntu, otherwise change to your needs)
```

$ sudo apt-cdrom -d /media/*<cdrom_mountpoint>* add
$ sudo apt-get update
$ sudo apt-get --reinstall install *<ubuntu_flavour_of_your_choice>*-desktop

```
Actually, I don't know if the Ubuntu Gutsy cd has also *Kubuntu* packages :-P, so be 'careful' ;-)

---

### Post by Nycticorax on 2008-03-09
Thanks for all your help MeURi. In the end I just downloaded the gutsy install .iso, stuck the home directory on my ipod and reinstalled from scratch (with a separate partition for home this time...). 

I have heard that apt-get dist-upgrade can be problematic, so I'm not complaining there. However, if there are any ubuntu/debian developers listening,  I think that it was very poor behaviour of dselect to remove a functioning network connection without warning me. There are presumably some core things that dselect won't remove in the course of fixing broken dependencies, so why doesn't network functionality fall into that category? I'm tempted to consider that a bug.

---

### Post by MeURi on 2008-03-09
Welcome :-)

I always prefer clean installs... had some minor issues after a dist-upgrade, once, and I'm a bit lazy... so I choose a longer but safer way :-D

---

### Post by zvacet on 2008-03-09
@ **Nycticorax**



> I have heard that apt-get dist-upgrade can be problematic, so I'm not complaining there. However, if there are any ubuntu/debian developers listening, I think that it was very poor behaviour of dselect to remove a functioning network connection without warning me. There are presumably some core things that dselect won't remove in the course of fixing broken dependencies, so why doesn't network functionality fall into that category? I'm tempted to consider that a bug.

Your problems started when you decide to do upgrade from Dapper(or Breezy because you said it is 5.10,but that is irelevant now) and skip Edgy and Feisty and go  directly to Gutsy.That is not a way how things should be done.You should go Dapper>Edgy>Feisty>Gutsy if you want to upgrade right way.Or just do fresh install of Gutsy.

---

