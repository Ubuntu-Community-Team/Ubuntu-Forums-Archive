---
title: "Upgrading from Feisty to Gutsy = problems!"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by monkeymoo on 2007-10-22
Hi, 

Just upgraded from Feisty to Gutsy using the update manager. A few rather annoying problems have occurred. I'm x86 64bit if that has any relevance. 

1) The default kernel doesn't work. When I load Ubuntu 7.10, kernel 2.6.22-14-generic I just get a black screen and no signs of life. I have selected and defaulted (by changing /boot/grub/menu.lst) to Ubuntu 7.10, kernel 2.6.20-16-generic instead, which is ok, but I am wondering why the default is not working. Perhaps this has some influence on the other problems? 

2) The big one! No internet. 
Network Manager is up and working and not complaining about anything but I simply can't access the internet in any way (have tried firefox, thunderbird, synaptic, update manager, apt, Pidgin). I have tried roaming mode, dhcp and static IP address and nothing makes any difference. I also tried installing and reinstalling network manager but there's no difference. I've unplugged the ethernet cable and plugged it back in again and restarted the computer a few times so it's nothing silly like that. 

I only have a wired ethernet connection so this is not a problem with some exotic wireless card or anything like that. 

/etc/network/interfaces gives: 
> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

lshw -C network gives:
>   *-network               
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 21
       serial: 00:30:1b:44:27:be
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 duplex=full firmware=5789-v3.29a ip=192.168.1.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

ifconfig gives:
> eth0      Link encap:Ethernet  HWaddr 00:30:1B:44:27:BE  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe44:27be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5670424 (5.4 MB)  TX bytes:1227497 (1.1 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7073 (6.9 KB)  TX bytes:7073 (6.9 KB)

If I do "sudo /etc/init.d/networking restart" I get
>  * Reconfiguring network interfaces...                                          eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.

Oh there is one thing that works. If I ping ubuntu.com I get 100% successful packets. 

It is not a router problem as the router is working with other machines. Actually it is working with the machine with the problem also. This is what I find most confusing. In my old feisty 64bit I had a 32bit chroot which I used for things that didn't work in 64bit. Now this has not been upgraded when I upgraded the 64bit Feisty to Gutsy. When I start Firefox from the chroot then everything works fine. So there's nothing wrong at all with the machine or the router it's just the new Gutsy install. 

Please help as this is driving me nuts. 

3) My final Gutsy problem. Strangely when I choose Shutdown everything goes black but my computer doesn't actually turn off. Any ideas?

Any help greatly appreciated, especially to the network problem as that is the biggest annoyance by far. 

Thanks!

---

### Post by monkeymoo on 2007-10-22
Ok. So I have a workaround for the connection problem. I am using OpenDNS [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)
So I'm connected at least. Does this help anyone else work out what the original problem is because I'm still confused. 

Problems 1 and 3 are still problems though so any help on those appreciated.

---

### Post by build6 on 2007-10-22
Hi, just wanted to say, I'm having the same problem 3 as well.  

I'm on 32 bit, and also went to 7.10 by upgrading from feisty, so you may be on to something about your being on 64 bit being a problem w.r.t. problem 1 at least.

---

### Post by build6 on 2007-10-23
After a lot of fiddling, I "solved" (or rather, worked around) my problem 3 by disabling the splash screen.  When I do that, the machine powers off correctly on shutdown, and can reboot, whereas when the splash screen was active, it would hang at shutdown/reboot in a blank screen (with a blinking text-mode cursor)

---

### Post by monkeymoo on 2007-10-24
> **build6 said:**
> After a lot of fiddling, I "solved" (or rather, worked around) my problem 3 by disabling the splash screen.  When I do that, the machine powers off correctly on shutdown, and can reboot, whereas when the splash screen was active, it would hang at shutdown/reboot in a blank screen (with a blinking text-mode cursor)
Thanks. That works great. 

Still can't get the latest kernel to boot properly (although I can get the command line now). 

Does anyone have a proper fix for the network problem?

---

### Post by Slade Winstone on 2007-11-02
Hi,

I have had a really similar problem.  I'm running an ASUS A8M Laptop with Gutsy and 2.6.22-14-generic would freeze on boot and lockup without any errors that I could find, but 2.6.20-16-generic would boot fine.

I edited the kernel options in /boot/grub/menu.lst and added:

acpi=off

and now everything starts fine.  

I did have to reinstall my nvidia after messing about with it and then further reinstall the linux-restricted-generic over the 386 pacakges that Synaptic installed for me.  :mad:  However, in the end and, after a bit of trial and error, everything is OK again. :)

Seems like there are a few people having problems.  Maybe new buggy code, or a regression, or perhaps a buggy ASUS ACPI implementation peeking around the edges ?

Best of luck with it all.

Slade.

---

### Post by monkeymoo on 2007-11-02
> **Slade Winstone said:**
> 
I edited the kernel options in /boot/grub/menu.lst and added:

acpi=off

and now everything starts fine.  


Thanks for the suggestion, but I tried that and nothing changed, that kernel still won't boot. This problem is really frustrating!

---

### Post by Slade Winstone on 2007-11-02
I'd previously tried "irqpoll" and "noapic" which had got me further along the boot process but still hung in the end.

There are quite a few launchpad entries regarding the 2.6.22-x series kernels, but I'm sure that you're already looking there.

Sorry I couldn't help :(  Good luck with it.

Slade.

---

### Post by Slade Winstone on 2008-01-05
Hi, I have a quick update:

2.6.22.14 Kernel set nosmp noapic

UPDATE I have now found kernel boot parameters that will allow ACPI to run. Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I now use nosmp and noapic which allows some ACPI functionality and a good boot

Add to the end of defoptions and the end of the current kernel in /boot/grub/menu.lst

nosmp noapic

Slade.

---

