---
title: "Lucid - Wifi card not detected"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by G_u_s on 2010-05-01
Hi all,

I'm having a problem with my wifi card: it is not detected by the network manager. I have tried going to the Hardware Drivers utility, but it doesn't find any proprietary hardware.

I really am at a loss as to how to make Lucid "start over" with the wifi detection.

Any help is welcome =)

PS: I have installed Lucid using an existing /home, which was under 8.10. Maybe i just need to wipe out some configuration files to start afresh?

---

### Post by walterav on 2010-05-01
> **G_u_s said:**
> Hi all,

I'm having a problem with my wifi card: it is not detected by the network manager. I have tried going to the Hardware Drivers utility, but it doesn't find any proprietary hardware.

I really am at a loss as to how to make Lucid "start over" with the wifi detection.

Any help is welcome =)

PS: I have installed Lucid using an existing /home, which was under 8.10. Maybe i just need to wipe out some configuration files to start afresh?

Does it show up in the network manager during a livecd session?

Are you running a notebook/laptop or a desktop? 
If you are running a notebook/laptop make sure the FN+(key) combination on your keyboard enables the wifi adapter.

Please provide a little more info about your PC / configuration go to terminal and type:
```
lspci -v>Desktop/lspci.txt
lsusb -v>Desktop/lsusb.txt
```

Attach these files is a start.

PS: These files can contain privacy Unique related system info like hardware MAC address etc.

---

### Post by G_u_s on 2010-05-01
Thank you for helping.

I don't have a livecd to try a livecd session.

I'm running a desktop. Here is what lspci has to say about my wifi card (this is the one and only wifi device in the system):

```
04:02.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
	Subsystem: D-Link System Inc Device 3b04
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e4020000 (32-bit, non-prefetchable) [size=8K]
	Memory at e4000000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: [40] Power Management version 2
```

I can provide any additional info you want. Thank you again.

---

### Post by patman0623 on 2010-05-01
If I could chime in with with *my* network controller as I'm also not having any wireless access.

```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
```
and in sudo:
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 18-2f-14-ff-[truncated by poster]
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

```

---

### Post by walterav on 2010-05-01
G_u_s and patman0623 could you also post the output of the following command from terminal:
```
ifconfig -a>Desktop/ifconfig.txt
```

PS:This file will also contain unique personal related MAC addresses, so mind when posting. Some might not care, but its just the same as a unique serial from a device that leads to a unique device and maybe its user.

---

### Post by G_u_s on 2010-05-01
ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe6a:3680/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34554803 (34.5 MB)  TX bytes:5264003 (5.2 MB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5547237 (5.5 MB)  TX bytes:5547237 (5.5 MB)
```

iwconfig -a:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

This is the output of the commands. I've hidden my MAC address. There is no wifi device.

---

### Post by razy60 on 2010-05-01
I had a similar problem with my wifi card (intel 5300 agn) when ifirst started in the live cd it asked for a log in password i gave it a password (i used the root password) confirmed it, it then detected my wifi card and i had to go through the process of filling in the wifi info SSID ect. Now every time i reboot my Laptop it asks for the password then it will search and detect and connect to all wifi devices that it has permission for.

The other thing to try if you are able is to connect a ethernet  cable do the updates and see if that helps.

Raz

---

### Post by G_u_s on 2010-05-01
Thank you for your answer.

My computer is connected via Ethernet, all the updates are done, it is not the problem. I believe that it might be using a configuration file or something from my previous 8.10 install, which is why i would like to know a way to start afresh.

---

### Post by suryaccnamcse on 2010-05-01
I had the same problem and the network adapter intel pro/wireless 3945ABG  is the same in my laptop. This adapter is supported by Ubuntu.  Make sure that the laptop's wireless switch is switched on.In some laptops it is a physical switch and in some it is a combination of keys (see your laptop manual for it). When you Right click the network manager make sure enable networking and enable wireless are both checked. If this does not work then it is a problem of driver and you have to do a fresh install from a CD or a USB and the wireless is sure to work.

---

### Post by razy60 on 2010-05-01
Does network connections show what devices you have if there is a previous  wifi connection delete it then reboot(it has worked for me in the past).

Raz

---

### Post by G_u_s on 2010-05-01
> **suryaccnamcse said:**
> I had the same problem and the network adapter intel pro/wireless 3945ABG  is the same in my laptop. This adapter is supported by Ubuntu.  Make sure that the laptop's wireless switch is switched on.In some laptops it is a physical switch and in some it is a combination of keys (see your laptop manual for it).
I'm using a desktop.

> When you Right click the network manager make sure enable networking and enable wireless are both checked.
There is no "Enable Wireless" to be checked. That's the problem =)

> If this does not work then it is a problem of driver and you have to do a fresh install from a CD or a USB and the wireless is sure to work.
The point of my thread is precisely to avoid doing that ;) Because I believe that former config files might be the cause, and since I have no means to backup my data, I will always reinstall using an existing /home.



> **razy60 said:**
> Does network connections show what devices you have if there is a previous  wifi connection delete it then reboot(it has worked for me in the past).

Raz
There is no Wifi connection at all.

---

### Post by suryaccnamcse on 2010-05-01
it is a problem of the network drivers they have somehow got corrupted , it is very hard to reinstall the drivers in UBuntu. You can try it with the help of NDISWRAPPER, it can be installed from the synaptic package manager.

---

### Post by G_u_s on 2010-05-01
How exactly would i do, apart from "sudo apt-get install ndiswrapper"? What next, i mean.

Thank you.

---

### Post by razy60 on 2010-05-01
Can you make and or use a livecd or a usb install device if you can or have such does that show up your wifi?. 
Please note i am not asking you to install just to see if it detects your wifi and if it works. 


Raz

---

### Post by G_u_s on 2010-05-01
I have burned a LiveCD and booted with it, the same happens: no networking card.

---

### Post by patman0623 on 2010-05-01
```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:[truncated by poster] 
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe47:f6f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54786185 (54.7 MB)  TX bytes:2715980 (2.7 MB)
          Interrupt:18 

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

wlan0     Link encap:Ethernet  HWaddr 00:18:de:[truncated by poster]  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Interesting, it's showing up there in ifconfig. I am running a Laptop, and it didn't work after I upgraded 9.10 -> 10.4. This is not LTS, my fault.

---

### Post by walterav on 2010-05-01
> **G_u_s said:**
> I have burned a LiveCD and booted with it, the same happens: no networking card.

ifconfig:
Indeed it shows no wireless adapters.

kernel:
I think it is the chipset that is not supported by ubuntu anymore since they pulled the code from the kernel because the sources where unclear...
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=commit;h=492a320431f81088443608d61f739f4f2c207d51](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=commit;h=492a320431f81088443608d61f739f4f2c207d51)
So compiling the kernel with a own patch is one option. Can't find the page or mailing list anymore but I googled it. 

ndiswrapper:
What 'suryaccnamcse' mentioned is indeed true that using the Microsoft Windows XP/vista/7 drivers with ndiswrapper might be the other option. I only did this once with LinuxMint 8 which is also ubuntu based. I only needed to unpack the driver package and select a *.inf, *.vxd or *.sys file and it was up and running, also with network-manager-applet. It was a sis163u usb chipset. LinuxMint supplied a GUI for the ndiswrapper so it was kinda 123bingo.

[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148) #difficult solution..., try mine below first

I would try it directly from the livecd, install ndiswrapper with GUI, and put the Windows driver into it and see if it works. Therefor you don't have to mess with your current setup. If it works on the livecd session you might reconsider it on your current setup. Select 'ndisgtk' in synaptic and choose "System>Administration>Windows Wireless Drivers" than follow the onscreen steps

---

### Post by walterav on 2010-05-01
> **patman0623 said:**
> ```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:[truncated by poster] 
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe47:f6f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54786185 (54.7 MB)  TX bytes:2715980 (2.7 MB)
          Interrupt:18 

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

wlan0     Link encap:Ethernet  HWaddr 00:18:de:[truncated by poster]  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Interesting, it's showing up there in ifconfig. I am running a Laptop, and it didn't work after I upgraded 9.10 -> 10.4. This is not LTS, my fault.

could you post the output terminal:
```
sudo iwlist wlan0 scan
```

To see if it scans? I can't believe this device is not working because it is native supported, so it will be probably some config file from the upgrade process.

---

### Post by G_u_s on 2010-05-01
> **walterav said:**
> ifconfig:
Indeed it shows no wireless adapters.

kernel:
I think it is the chipset that is not supported by ubuntu anymore since they pulled the code from the kernel because the sources where unclear...
So compiling the kernel with a own patch is one option. Can't find the page or mailing list anymore but I googled it. 

ndiswrapper:
What 'suryaccnamcse' mentioned is indeed true that using the Microsoft Windows XP/vista/7 drivers with ndiswrapper might be the other option. I only did this once with LinuxMint 8 which is also ubuntu based. I only needed to unpack the driver package and select a *.inf, *.vxd or *.sys file and it was up and running, also with network-manager-applet. It was a sis163u usb chipset. LinuxMint supplied a GUI for the ndiswrapper so it was kinda 123bingo.

[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148) #difficult solution..., try mine below first

I would try it directly from the livecd, install ndiswrapper with GUI, and put the Windows driver into it and see if it works. Therefor you don't have to mess with your current setup. If it works on the livecd session you might reconsider it on your current setup. Select 'ndisgtk' in synaptic and choose "System>Administration>Windows Wireless Drivers" than follow the onscreen steps

Thank you very much walterav, I installed ndisgtk, grabbed the Windows drivers, launched Windows Wireless drivers, clicked "Install new driver", then pointed to the .inf. An icon appeared, saying "gplus" (the driver, i assume) and "hardware present". The problem is, i still don't have an "Enable Wireless" option. Should i fiddle with /etc/network/interfaces or is there some kind of automated way of refreshing it, now that the card is (supposedly) present and with an appropriate driver? (I've rebooted, didn't help.)

---

### Post by walterav on 2010-05-01
> **G_u_s said:**
> Thank you very much walterav, I installed ndisgtk, grabbed the Windows drivers, launched Windows Wireless drivers, clicked "Install new driver", then pointed to the .inf. An icon appeared, saying "gplus" (the driver, i assume) and "hardware present". The problem is, i still don't have an "Enable Wireless" option. Should i fiddle with /etc/network/interfaces or is there some kind of automated way of refreshing it, now that the card is (supposedly) present and with an appropriate driver? (I've rebooted, didn't help.)

We'll I was hoping that after installing it would work out of the box, what does terminal report at this moment:
```
ifconfig -a
```

Could you also test this from the livesession, not your current upgraded session?

Other wise you have to start reading the long and maybe difficult thread I also supplied.

BTW did you try a XP, or Vista/7 driver?

---

### Post by MightyMouse on 2010-05-01
Hi, 

You could try to install linux-firmware-nonfree-1.6 (as mentioned here [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)). After one (or two) restarts I did have my Wifi card up and running.

MightyMouse

---

### Post by MightyMouse on 2010-05-01
Hi, 

You could try to install linux-firmware-nonfree-1.6 (as mentioned here [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)). After one (or two) restarts I did have my Wifi card up and running.

MightyMouse

---

### Post by G_u_s on 2010-05-01
> **walterav said:**
> We'll I was hoping that after installing it would work out of the box, what does terminal report at this moment:
```
ifconfig -a
```

Could you also test this from the livesession, not your current upgraded session?

Other wise you have to start reading the long and maybe difficult thread I also supplied.

BTW did you try a XP, or Vista/7 driver?
My terminal still shows only lo and eth0. I've tried looking at the thread you mentionned, and typed ndiswrapper -l, which returned that the driver was installed and the hardware present.

I didn't try the live session yet.

The driver i used was an XP one.

Thank you for your help walterav, I appreciate it =)

> **MightyMouse said:**
> Hi, 

You could try to install linux-firmware-nonfree-1.6 (as mentioned here [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)). After one (or two) restarts I did have my Wifi card up and running.

MightyMouse

Thank you MightyMouse, i will try that now!

EDIT: tried, didn't work, still the same =/ I think it would have spared me from installing the ndiswrapper thing, but didn't solve my initial problem, which is to reset/reinitialize the network configuration (i think).

---

### Post by eshandy on 2010-05-01
Hi Gus and all.

I am having a similar problem. I don't believe that it is an old configuration messing things up. I actually had my wireless up and running on Lucid &#8212; for about 60 seconds. Since then, no wireless devices have been recognized.

Also, I just booted into a karmic live-cd. No problems. My wireless card was instantly recognized, and connection worked flawlessly.

From the readouts below, it strikes me as strange that it says "*-network UNCLAIMED", but I don't know enough to know what it means. Do you get the same message, Gus? And does your wifi work with a Karmic live-CD? Any help would be much appreciated.

Thanks in advance
&#8212;eshandy



sudo lshw -C net readout:

[FONT=Courier New]  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:c0200000-c020ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:21:01:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii  10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=full ip=192.168.11.3 latency=64 link=yes  maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:21 ioport:a000(size=256) memory:c0300000-c03000ff
[/FONT]

iwconfig readout:
[FONT=Courier New]lo        no wireless extensions.

eth0      no wireless extensions.[/FONT]

---

### Post by G_u_s on 2010-05-01
It is "unclaimed" on my computer as well.

---

### Post by eshandy on 2010-05-01
> **G_u_s said:**
> It is "unclaimed" on my computer as well.

I think I smell a rat. Problem is, I have no idea how to go about doing something about it. I, too, have tried the non-free firmware package mentioned by mightymouse. With much the same results as Gus&#8212;i.e. no result at all. The problem must lie somewhere else.
&#8212;eshandy

---

### Post by patman0623 on 2010-05-01
I ignored it because it didn't work originally when I switched it on/off, but it appears the hardware wireless was off for me. Very silly mistake.

---

### Post by walterav on 2010-05-01
> **G_u_s said:**
> My terminal still shows only lo and eth0. I've tried looking at the thread you mentionned, and typed ndiswrapper -l, which returned that the driver was installed and the hardware present.

I didn't try the live session yet.

The driver i used was an XP one.

Thank you for your help walterav, I appreciate it =)



Thank you MightyMouse, i will try that now!

EDIT: tried, didn't work, still the same =/ I think it would have spared me from installing the ndiswrapper thing, but didn't solve my initial problem, which is to reset/reinitialize the network configuration (i think).

In my case the light from the wifi adapter got up as soon as the ndiswrapper driver loaded, is this also in your case? 

Any news on the livesession yet? Keep in mind you don't have to re-install but just try the ndiswrapper during the livesession. In a 15 year pc history things always had a different run on a clean system...

---

### Post by G_u_s on 2010-05-01
> **walterav said:**
> In my case the light from the wifi adapter got up as soon as the ndiswrapper driver loaded, is this also in your case?
Well, I'm using a Desktop. I could see no light flashing on the PCI card.

> Any news on the livesession yet? Keep in mind you don't have to re-install but just try the ndiswrapper during the livesession. In a 15 year pc history things always had a different run on a clean system...

I have installed ndisgtk, then the driver, but nothing happened. Obviously, i couldn't restart once i did that, to see if a restart would change anything.

---

### Post by kamalkhadka on 2010-05-01
My computer doesn't have a internet access but .. have  another one that does. Upgraded to Ubuntu 10.04 few days back but couldn't get the wireless working.

I have a broadcom (4328) wireless card. Tried installing bcmwl-kernel-source from Ubuntu CD but it gives me an error saying failed to  fetch (Hash Sum mismatch)

I have no idea what I need to do to make wireless working??:confused::confused:

---

### Post by walterav on 2010-05-02
> **G_u_s said:**
> Well, I'm using a Desktop. I could see no light flashing on the PCI card.



I have installed ndisgtk, then the driver, but nothing happened. Obviously, i couldn't restart once i did that, to see if a restart would change anything.

I did a little more reading, and found that if you compile your own acx drivers you won't have 'wpa' security only 'wep'.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077)
The ndiswrapper guide I wrote earlier might only work with Linksys drivers for pcmcia interfaces, BUT it is reported working with lucid "doubtful wisdom" verified at page 11. So I think this is your only option.
[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

### Post by G_u_s on 2010-05-02
> **walterav said:**
> I did a little more reading, and found that if you compile your own acx drivers you won't have 'wpa' security only 'wep'.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077)
The ndiswrapper guide I wrote earlier might only work with Linksys drivers for pcmcia interfaces, BUT it is reported working with lucid "doubtful wisdom" verified at page 11. So I think this is your only option.
[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

Well, since i could actually do part of what the thread says, and that it seems the problem is not to have working drivers, but to signal the system it should use it, i don't think following the thread would help (especially since it's dedicated to Linksys cards when i have a D-Link DWL-G520+).

Thanks for trying anyway =) No other idea?

---

### Post by MightyMouse on 2010-05-03
Hi,

maybe you can have a look here

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-backports-modules-wireless-lucid-generic](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-backports-modules-wireless-lucid-generic)

I think that you might want to install some of the backports and see if that helps.
I have read somewhere that some drivers were 'wrongly' placed in Karmic and therefore automatically installed, which was apparently not correct due to copyright issues (?). In lucid they have been moved to the non-free section and one has to actively download them somehow.

Maybe this helps?

MightyMouse

---

### Post by G_u_s on 2010-05-03
> **MightyMouse said:**
> Hi,

maybe you can have a look here

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-backports-modules-wireless-lucid-generic](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-backports-modules-wireless-lucid-generic)

I think that you might want to install some of the backports and see if that helps.
I have read somewhere that some drivers were 'wrongly' placed in Karmic and therefore automatically installed, which was apparently not correct due to copyright issues (?). In lucid they have been moved to the non-free section and one has to actively download them somehow.

Maybe this helps?

MightyMouse

Hi MightyMouse,

I've read a similar thing somewhere during my search. I assumed that it wouldn't help since i was able to install the driver via ndiswrapper anyway.

But assuming, with computers, is often wrong. I'll try it out. Thanks for suggesting the idea =) (This is for my home computer, so i won't do it before tonight. I need to set up a remote desktop ;))

---

### Post by eshandy on 2010-05-03
Hi all.

I have tried installing every backports-package available in synaptics. Nothing worked for me. I have therefore reverted to Karmic, where everything works beautifully.

Gus: have you tried Karmic, and did that work for you as well?

&#8212;Eshandy

---

### Post by G_u_s on 2010-05-03
> **eshandy said:**
> Hi all.

I have tried installing every backports-package available in synaptics. Nothing worked for me. I have therefore reverted to Karmic, where everything works beautifully.

Gus: have you tried Karmic, and did that work for you as well?

—Eshandy

No, I "upgraded" my desktop from 8.10 to 10.04. It's more "overwriting" than upgrading, actually. I formatted and installed on /, while keeping my /home (which was on a separate partition).

This is why I'm thinking that maybe it's an old configuration file messing up the detection, but I'm not sure... And what would be the point of a separate /home if it messes up installs?

---

### Post by CaptainPasty on 2010-05-03
Sound's like you're having fun and games there, G_u_s. For anybody else having this problem, I recommend giving MightyMouse's suggestion a go. It's just stopped me from taking my computer outside and driving over it...

---

### Post by G_u_s on 2010-05-03
> **CaptainPasty said:**
> Sound's like you're having fun and games there, G_u_s.
I'm playful like that ^^

> For anybody else having this problem, I recommend giving MightyMouse's suggestion a go. It's just stopped me from taking my computer outside and driving over it...
This gives me hope =) I'll try it when I'm back home and let you know. Hopefully this thread can receive a nice little "SOLVED" prefix =)

---

### Post by james.whanger on 2010-05-03
I'm having a similar problem:

I installed Ubuntu 10.04 from a Live USB onto an HP Mini 1030nr. The bcmwl wireless driver is not installing. 

I've tried a number of solutions that worked with 9.10, such as trying to install using the Deb package installer to grab packages and drivers from the Live USB drive. 

However, I ran into a problem with two dependencies for bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb: both g++-4.4_4.4.3-4ubuntu5_i386.deb AND libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb list each other as dependencies. Thus, it won't install either. 

After setting a CD repository, both the Deb package installer and Synaptic package installer tries to grab the dependencies from a Live CD, but it does not automatically recognize the Live USB as the Live CD image. 

Is there a way to set the Live USB as the Live CD repository for either the Deb installer or the Synaptic installer?

---

### Post by P4man on 2010-05-03
> **james.whanger said:**
> 
Is there a way to set the Live USB as the Live CD repository for either the Deb installer or the Synaptic installer?

Not that I know, but you can with the alternate cd.

But cant you connect a wired ethernet temporarily?

---

### Post by G_u_s on 2010-05-03
> **MightyMouse said:**
> Hi,

maybe you can have a look here

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-backports-modules-wireless-lucid-generic](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux-backports-modules-wireless-lucid-generic)

I think that you might want to install some of the backports and see if that helps.
I have read somewhere that some drivers were 'wrongly' placed in Karmic and therefore automatically installed, which was apparently not correct due to copyright issues (?). In lucid they have been moved to the non-free section and one has to actively download them somehow.

Maybe this helps?

MightyMouse

I've tested, and it doesn't help, my card is still "unclaimed". I really think something is messed up with the config... What do i need to erase to force a fresh config?

---

### Post by HowieGoodell on 2010-05-06
I have a similar problem.  My work laptop was Vista, and I didn't like it.  So when the hard drive crashed last Fall, I took the opportunity to install Ubuntu Jaunty instead, with VirtualBox for XP when I must use a Windows program).  Generally very happy I made the switch; since most of my work is interacting with Unix servers.  However, my Intel 3945ABG wireless card has never worked: neither in J-K or Lucid I just installed.  Wireless showed as DISABLED.  However, now that I installed ndisgtk and the recommended (XP) driver, wireless doesn't appear at all in ifconfig, regardless of the position of the on/off switch.  However, the ndisgtk "Wireless Network Drivers" box shows netw5x32 Hardware present: Yes.  However, as the poster (whose name I can't read while I'm composing this) commented, there's no obvious way to enable or turn on the interface.  I browsed quite a bit, and people mention problems that only the Windows utility can turn it on -- maybe that's my problem here.  It really sucks to have to plug into Ethernet everywhere -- often it's not available; this weekend I may need to bring a long cable through airport security -- all kinds of fun ;-)  Thanks much if anyone has a clue about this!

Howie Goodell

Here's my lspci and ifconfig output:

goodell@r00hg995999:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 360M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
goodell@r00hg995999:~$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:1c:23:36:3c:82  
          inet addr:155.52.120.149  Bcast:155.52.120.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe36:3c82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18422204 (18.4 MB)  TX bytes:4255770 (4.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

virbr0    Link encap:Ethernet  HWaddr aa:2e:5a:e4:c3:97  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::a82e:5aff:fee4:c397/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 Anybody
          RX bytes:0 (0.0 B)  TX bytes:122545 (122.5 KB)

---

### Post by P4man on 2010-05-06
I just googled on "linux wifi killswitch" and came across this:

[http://tamentis.com/doc/travelmate4010/](http://tamentis.com/doc/travelmate4010/)

```
echo 0 > /sys/bus/pci/devices/*/rf_kill
```

Maybe worth a try?

---

### Post by G_u_s on 2010-05-20
> **P4man said:**
> I just googled on "linux wifi killswitch" and came across this:

[http://tamentis.com/doc/travelmate4010/](http://tamentis.com/doc/travelmate4010/)

```
echo 0 > /sys/bus/pci/devices/*/rf_kill
```

Maybe worth a try?

Thank you P4man, I'll try this when I get home.

---

### Post by L_R_N on 2010-12-10
Googled this thread. Since the problem was not solved, i guess i'd  better tell you what worked for me: ```
 sudo modprobe iwl3945 
```  You might need to do ```
sudo rmmod iwl3945
``` (maybe with -f option), and  maybe add some options to modprobe

---

