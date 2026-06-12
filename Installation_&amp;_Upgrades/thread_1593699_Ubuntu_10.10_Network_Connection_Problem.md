---
title: "Ubuntu 10.10 Network Connection Problem"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by smfoote on 2010-10-11
I've just updated my Dell Inspiron Mini to Maverick Meerkat (10.10), and I've very quickly run into quite a few problems. First, it took an awful long time to install all of the updates. Is that normal? Perhaps it's just because I'm using a puny netbook?

When the updates were finished and I rebooted, I logged in without any problems, but then got a gray screen. I've seen that screen before, when Ubuntu loads (especially with Lucid), but it doesn't go away. I rebooted using Desktop Edition instead of Netbook Edition, and there was an improvement, but the top toolbar is blank.

Additionally, and most importantly, I can't get an Internet connection of any kind, wired or wireless. When I run ```
ifconfig
```, it shows I have an IP address, and says I am receiving packets, but I can't ping, I can't load any pages in an Internet browser, and I can't run ```
update-manager
```. 

Any ideas on what I might be able to do to fix these problems (especially the connection issues)?

---

### Post by poohlo on 2010-10-12
got nearly the same  - upgraded from 10.04 now when i starting skype my network disables, or sometims it just disables. still looking for a clue

---

### Post by poohlo on 2010-10-12
reinstalled the system. What's interesting - after SKYPE starting my network fails and it needs 2 or 3 times rebooted till it starts

---

### Post by physio_amer on 2010-10-13
[SIZE=3]Same type of problem here. i upgraded to ubuntu 10.10, and now not able to use mobile broadband. although wifi is working and wired connection is working. any way to activate mobile broadband settings?[/SIZE]:confused:

---

### Post by drtvasudevan on 2010-10-13
upgraded from 10.04
Eth0 connection is erratic and of late not working. works from windows and so hardware issues. Belkin N150 router modem.
should i reinstall something?

---

### Post by garvinrick4 on 2010-10-13
smfoote,
 Check your drivers in "additional drivers" all Dells I have seen
have proprietary drivers. 
Connection information in network manager applet (right click) should tell you your active connections. In 10.10 tells you everything. 
 What does it say there or in:
```
gedit /etc/resolv.conf
```
should be domain and name server if connected. (How did you upgrade system?) Said it took a long time?
Top panel can you right click and add notification area? (desktop edition)

---

### Post by poohlo on 2010-10-15
I find that when starting Skype on 10.10 it generates a lot of traffic. Try to disably the firewall on your gateway - helped for me!

---

### Post by jimstar79 on 2010-10-15
Following upgrade this morning, apparently i have lost all internet connections!

well, nothing shows up on the network applet. Wifi has totally disappeared  - stating network disabled. 

Do i have to somehow reapply IP settings somewhere for my WIFI?

Right now I can not even see any network information regarding my ethernet connection. 

crappy!

---

### Post by jimstar79 on 2010-10-16
last night i tried out Lucid LiveCD - connected straight to the internet using wifi - what could have gone so drastically wrong when upgrading to 10.10 that is affecting so many of us?

peace and love brothers and sisters!

---

### Post by Kiisseli on 2010-10-17
I got mine working by doing this:
  1. apt-get remove --purge usb-modeswitch
  2. Reboot
  3. apt-get install usb-modeswitch
  4. reboot

I'm not sure if you need to reboot in the step 2.

---

### Post by koschei on 2010-10-21
I have ubuntu netbook 8.04 on a dell inspiron mini 9, and when I booted from USB to try out 10.10 it couldn't find any networks. I can't get on the internet at all, and it won't let me run any sudo apt-get command - just says failed. Is this because I am booting from USB or something else? I'm not very linux-savvy, and any help would really be appreciated.

---

### Post by OneWayPT on 2010-11-03
> **jimstar79 said:**
> Following upgrade this morning, apparently i have lost all internet connections!

well, nothing shows up on the network applet. Wifi has totally disappeared  - stating network disabled. 

Do i have to somehow reapply IP settings somewhere for my WIFI?

Right now I can not even see any network information regarding my ethernet connection. 

crappy!

Got the same problem, After updating to 10.10 my NetWorkMannager stop showing wifi, eth0 and gsm connections, i can access web with the eth0 but i cannot use the other connections... Tried the usb-modeswitch reinstall but no solution.

Any suggestion? 

Tks

---

### Post by drtvasudevan on 2010-11-03
> **drtvasudevan said:**
> upgraded from 10.04
Eth0 connection is erratic and of late not working. works from windows and so hardware issues. Belkin N150 router modem.
should i reinstall something?

during one of those erratic connections i reinstalled everything connected with networking through synaptic. i got back the network manager icon etc but still the connection is erratic. sometimes i boot into windows and after sometime that connects. then i reboot into ubuntu and then it is connected.

---

### Post by Def_101 on 2010-11-11
I had to do this on a new install.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by drtvasudevan on 2010-11-13
> **drtvasudevan said:**
> during one of those erratic connections i reinstalled everything connected with networking through synaptic. i got back the network manager icon etc but still the connection is erratic. sometimes i boot into windows and after sometime that connects. then i reboot into ubuntu and then it is connected.

windows connection became consistent with updating drivers.
still ubuntu connections failed; not even erratic but no connection.
finally solved by adding to boot params the "magic word" no acpi

btw that editing was done by opening gedit as root and editing etc/default/grub modifying a line thus: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash no acpi"

---

### Post by drtvasudevan on 2010-11-14
> **drtvasudevan said:**
> 
finally solved by adding to boot params the "magic word" no acpi


spoke too soon!
it failed again this afternoon.
i fooled around and seeing the ipv6 was getting configured but not ipv4 i edited avahi-daemon.conf and set ipv6 to no
seems to work now
need to see the consistency! :-)

---

### Post by drtvasudevan on 2010-11-14
> **Def_101 said:**
> I had to do this on a new install.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

this one too talks about ipv6 disabling !

---

### Post by alexthunder on 2010-12-24
I have problems with my Internet connection after upgrading to Maverick. I have DG965SS motherboard and I use an ethernet connection. It worked just fine in 9.04, 9.10 and 10.04, but not in 10.10.

I tried the following suggestions:
1. run
```
sudo ifconfig eth0 up
sudo dhclient eth0
```

2.
in /etc/network/interfaces use
```
auto eth0
iface eth0 inet dhcp
```

but this didn't help.

Another user posted that the problem was resolved after 20 reboots. I tried to reboot and on the 3rd reboot I got an Internet connection. But on the next reboot it disappeared again.

my /etc/network/interfaces 
```
auto lo
iface lo inet loopback
```

---

### Post by alexthunder on 2010-12-24
This problem seems to happen more in 2.6.35-24 and less in 2.6.35-22. And I have only managed to solve it by rebooting (sometimes I need to reboot multiple times).

And the biggest problem is that my bootable flash drive used to save me a lot, because I was able to access Internet using it. Now I can't access Internet when using a bootable usb drive with Ubuntu Maverick.

My Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection

---

### Post by alexthunder on 2011-01-20
Still have the same problem. If I disable my internet connection, I can't enable it anymore. Only rebooting helps, but sometimes I need to reboot 5-10 times.

---

### Post by alexthunder on 2011-01-25
I have to reboot even more times now to get my Internet connection to work. Can't find a solution.

lshw -c network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:16:76:cf:be:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.1-0 latency=0 multicast=yes
       resources: irq:46 memory:92200000-9221ffff memory:92224000-92224fff ioport:40c0(size=32)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:cf:be:25  
          inet6 addr: fe80::216:76ff:fecf:be25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256 (256.0 B)  TX bytes:12405 (12.4 KB)
          Interrupt:20 Memory:92200000-92220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

sudo ifdown eth0; sudo ifup eth0
```
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
```

---

### Post by tinadad on 2011-03-13
Well I woke up this morning to an eth0 disconnected. No matter how many time I reboot the issue is the same. Was able to plug in a wireless usb adapter and it worked. Replaced the cat5. The interface was found in lspci and dmesg. Stopped the network manager, brought eth0 up, but dhclient failed. This system has worked without a hitch under 10.4 LTS, but a week into the upgrade I loose the interface. :confused:

---

### Post by 91voyager on 2011-04-10
same here. 10.10 lost my wired and can't get it back. depressing me. i am a newbie, so if any one solves this and can add some detailed steps to fix, that would be greatly appreciated.   i haven't tried rebooting 5-10-15 times yet, so will do that next.

---

### Post by cwoodruf on 2011-09-01
I believe this is a problem with NetworkManager. I have a static IP address and had settings in resolv.conf for my name servers. These vanished on the upgrade from 10.04 to 10.10. NetworkManager was overwriting resolv.conf. 

So if you have something like this in /etc/resolv.conf
```

nameserver 1.2.3.4

```
It may be lost on reboot. There are two solutions. Both outlined here:
[http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/)

For me removing NetworkManager (solution 2) was the only one that worked.

I really don't recommend using the purge method to remove NetworkManager as it will remove a bunch of other stuff you may want to keep. Try "remove" instead:
```

aptitude remove network-manager network-manager-gnome

```

Note that disabling IPv6, turning on network cable monitoring in the bios etc had no effect for me. However, by adding the nameserver lines to my nameservers in resolv.conf the issue instantly vanished without having to reboot the system.

---

