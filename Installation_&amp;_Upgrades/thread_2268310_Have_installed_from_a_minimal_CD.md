---
title: "Have installed from a minimal CD"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by gabmuks on 2015-03-07
Hello and good day.
I have created an Ubuntu 14 "ISO mini" CD to install
on my very old laptop.
 I have installed it ok, but it only comes up in DOS mode.
Is that correct?

---

### Post by papibe on 2015-03-07
Hi gabmuks.

Yes. The minimal installs  a text mode version. Sort of like a server install.

Is that what you were looking to do?

If you share what you what to accomplish, maybe we can come out with more suggestions.

Regards.

---

### Post by Bashing-om on 2015-03-07
gabmuks' Hello;

Yes, booting to a terminal is correct.
With the minimal install it is your choice what is installed on this bare bones. All that is present now is the ability to boot the kernel and enable a wired connection. - that gives you access to the software repository to install whatever your little heart desires of the ubuntu world .

So what do you want on this system ?
What do you want to do with this wonderful opportunity to make a system that is "all your own" ?

[INDENT][INDENT]I can here the wheels turning in your mind 
[/INDENT][/INDENT]

---

### Post by gabmuks on 2015-03-07
Thanks for reply.

I have installed it ok.

I chose the Lubuntu version
 when the selection box came up.

Then remove the CD and let it reboot.

Everything seems to load normally
at first, but when its finished booting
there is no video. Nothing at all. Black screen only.

And I can't shut it off even with the on/off button.

I have to remove the battery.

Any ideas?

---

### Post by grahammechanical on 2015-03-07
> [COLOR=#333333][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]After the base system is installed, log in, and type "sudo tasksel" to select the system to install.[/FONT][/COLOR]

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You should now get a list of desktop environments to install.

Regards.

---

### Post by gabmuks on 2015-03-07
> **grahammechanical said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You should now get a list of desktop environments to install.

Regards.

Yes Sir. the list did come up and I selected Lubuntu.
the installation seems to go well, but then on reboot
there is no video. (No command prompt) nothing at all.
 I can put the CD in again and start over, but I've already done that twice
with the same results.

---

### Post by Bashing-om on 2015-03-08
gabmuks; Good morning ;

It is difficult to tell where you are at in the booting process from the info provided.

Perhaps these tutorials will help:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) <- an example of what you can make .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-03-08
If you want Lubuntu, why not install Lubuntu rather than the minimal install? The idea with the minimal install is to create the computing environment that suits you best with just the apps you need/want and nothing more. If you just want the Lubuntu desktop environment, then you simply reboot after install to the terminal, login and:

```
sudo apt-get install lxde
```

... and whatever other apps/software you want to use. A simple setup would be:

```
sudo apt-get install lxde synaptic lightdm firefox thunderbird xfwm4
```

... for starters. Reboot and that should get you to a login screen. Once at the desktop you can install anything else you want via Synaptics or the terminal.

---

### Post by gabmuks on 2015-03-08
Guess I had to start with a  minimum CD because my old laptop wont boot from
USB. And I don't have means to make a boot DVD.
But I might be wrong. Anyways I managed to install Kubuntu instead of Lubuntu
from some info I found online last night. Also installed Firefox Browser from a tar.bz2.

Only thing missing is my Wifi and Audio. That would be driver problems. Is that correct?

I did a lshw -c network and got this:

*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:9 memory:b0200000-b0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:71:bb:11
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.5 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:b0203000-b02030ff

ifconfig got this:

iz@ubuntu:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:71:bb:11  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe71:bb11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2126748 (2.1 MB)  TX bytes:247473 (247.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I don't know how to get any other info yet.

---

