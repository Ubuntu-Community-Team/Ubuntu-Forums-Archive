---
title: "Ethernet Troubles on Home-Built Desktop"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by 3mp4th on 2012-11-06
All right, guys, I give in. I haven't used Linux in years, but my mother wanted it on the desktop for the family business, since she uses it at home and loves it. 

The desktop computer in question is one that she bought from me, my old gaming tower (built in November of 2009). I built it from bare bones, and have run both Windows and older versions of Linux Ubuntu on it successfully over the years. It's got a Intel DP55WB motherboard and Intel Core i5 (2.66Ghz, Quadcore/Lynnfield) processor. 

I installed Linux Ubuntu 12.10 on it, and everything looks good... except for the fact that it won't connect to the internet. Now, since it has no wireless adapter, it's hooked to the DSL by ethernet. However, it's not coming up with the Auto eth0, and it won't let me connect manually, either through Wired or DSL. :/

Everything I tried suggests that it's not even detecting that it's plugged in. I have checked the physical components about five times now, including unplugging, replugging, etc. I tried to get the driver for the motherboard from Intel, and I have the file, which I put onto the desktop from a USB drive. However, I can't even find clear directions on how to install it, and I don't know if that's the problem, anyway. 

Any ideas? Thanks in advance.

---

### Post by grahammechanical on 2012-11-06
First, you should not be having any problem with a wired (ethernet) connection. Network manager should be handling this connection automatically. Are to trying to set up the connection manually?

Do you see a network manager icon? Was 12.10 installed with Internet access already in place?

If you see a Network Manager icon can you use it to check that Networking is enabled? Can you edit the connection to set to connect automatically?

Regards.

---

### Post by 3mp4th on 2012-11-06
> **grahammechanical said:**
> First, you should not be having any problem with a wired (ethernet) connection. Network manager should be handling this connection automatically. Are to trying to set up the connection manually?

Yes, I thought that it should be handling it automatically. The issue is that it's not detecting a connection at all. It doesn't seem to be acknowledging that the ethernet cord is even plugged into it. As such, yes, I have tried to set it up manually, to no avail, since there is no automatic connection.

> **grahammechanical said:**
> Do you see a network manager icon? Was 12.10 installed with Internet access already in place?

If the Network Manager icon is the pizza slice in the top, yes. It is empty, and when I click on it, it says: No network devices available (greyed out), VPN Connections >, Enable Networking (checked), Connection Information (greyed out), Edit Connections.

The PC that was hooked up before, which was a very, very old desktop that ran Windows XP, connected to the DSL just fine through the same Ethernet cord. And since the DSL is also wifi-enabled, this computer (Linux Ubuntu on an Acer AspireOne netbook, also installed by me) is able to connect to it. Based on this, I infer that the DSL is working perfectly fine. The desktop just isn't detecting it.

I installed 12.10 as a fresh install, after wiping Windows 7 from the computer. I downloaded it with my personal laptop, burnt the ISO to a disk, and installed it to the desktop. The desktop has NOT connected to the internet since the fresh install, nor to any network at all. The fresh install was done yesterday.

> **grahammechanical said:**
> If you see a Network Manager icon can you use it to check that Networking is enabled? Can you edit the connection to set to connect automatically?

Networking is enabled, per the check box. There is no connection available by default. I have attempted to create both a Wired connection as well as a DSL connection. However, I'm not even sure that I'm configuring them correctly. 

In Wired: I put in the modem's MAC address as the Device MAC Address, but I have no idea if I need a Cloned MAC address. I left the IP settings on Automatic; should I customise them? I have no idea if I need to do anything with the 802.1x Security tab. I've tried it with nothing, with the DSL login, with the modem login, etc.

In DSL: Same thing in the Wired tab as above for the MAC address. IP also automatic. DSL tab: I tried putting in the DSL username and password, but I have no idea what the Service should be. I also know that the modem/router from the ISP connects with that information already, so theoretically, I should just be using the Wired connection...? No idea what the PPP Settings tab does.

I know, I must sound like a newbie, but I haven't done this in so long, I've no idea at all what I'm doing. It always came up with Auto eth0 before, with older installations of Linux Ubuntu. Windows also sees it and connects to it.

I'm actually kind of hoping I'm just being an idiot and this is a simple, obvious fix...

---

### Post by Cheesehead on 2012-11-06
In most cases, those MAC fields should have auto-filled.
In a terminal, try 'lspci -v' to see if the ethernet port has a driver assigned.
Then try 'dmesg | grep eth' to see if the kernel detected the hardware and assigned an eth port to it.
Finally, try 'ifconfig -a' to see of the eth* port is configured at all.

Feel free to post the output here, too.

---

### Post by 3mp4th on 2012-11-06
> **Cheesehead said:**
> In most cases, those MAC fields should have auto-filled.

I would imagine that you mean in cases in which a connection was even detected at all.

> **Cheesehead said:**
> In a terminal, try 'lspci -v' to see if the ethernet port has a driver assigned.

> [FONT="Courier New"]00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)
	Subsystem: Intel Corporation Device 0000
	Flags: fast devsel, IRQ 20
	Memory at e0200000 (32-bit, non-prefetchable) [size=128K]
	Memory at e0224000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2020 [size=32]
	Capabilities: <access denied>
	Kernel modules: e1000e[/FONT]

> **Cheesehead said:**
> Then try 'dmesg | grep eth' to see if the kernel detected the hardware and assigned an eth port to it.

Nothing happened...?

> **Cheesehead said:**
> Finally, try 'ifconfig -a' to see of the eth* port is configured at all.

> [FONT="Courier New"]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:482656 (482.6 KB)  TX bytes:482656 (482.6 KB)[/FONT]

> **Cheesehead said:**
> Feel free to post the output here, too.

Done. Mean anything to you? I admit, I have no idea what a lot of that means.
Thanks a ton.

---

### Post by Cheesehead on 2012-11-08
It means that the hardware is recognized and a driver is assigned (good).
It means that no eth* interface is created (not good). Only the loopback interface was created.

Unplug the network cable, wait about 10 seconds, then plug in the network cable. Then run the command 'dmesg | tail -n10' and post the result here.

Also, take a look at /etc/udev/rules.d/70-persistent-net.rules (yours might not be '70-'). If there is anything in that file, please post it.

---

### Post by dannyboy79 on 2012-11-08
check to see if the module is loaded for that chipset

sudo lsmod | grep e1000e

---

### Post by drilltotheheavens on 2012-12-12
Hello, Complete linux noob here. I just built a pc and successfully installed ubuntu 12.10. However, just like the thread starter, my computer is not detecting the ethernet cable I plugged in.

> **Cheesehead said:**
> In a terminal, try 'lspci -v' to see if the ethernet port has a driver assigned.

03:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
Subsystem: Giga-byte Technology Device e000
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
I/O ports at d000 [size=128]
Capabilities: <access denied>

> **Cheesehead said:**
> Then try 'dmesg | grep eth' to see if the kernel detected the hardware and assigned an eth port to it.

Nothing displayed in terminal.

> **Cheesehead said:**
> Finally, try 'ifconfig -a' to see of the eth* port is configured at all.

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:224 errors:0 dropped:0 overruns:0 frame:0
TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:18400 (18.4 KB) TX bytes:18400 (18.4 KB)

> **Cheesehead said:**
> It means that the hardware is recognized and a driver is assigned (good).
It means that no eth* interface is created (not good). Only the loopback interface was created.

What's telling me that the driver was successfully installed?

> **Cheesehead said:**
> Unplug the network cable, wait about 10 seconds, then plug in the  network cable. Then run the command 'dmesg | tail -n10' and post the  result here.

[    3.246843] type=1400 audit(1355396781.949:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=832 comm="apparmor_parser"
[    3.246957] type=1400 audit(1355396781.949:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=833 comm="apparmor_parser"
[    3.247008] type=1400 audit(1355396781.949:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=830 comm="apparmor_parser"
[    3.247018] type=1400 audit(1355396781.949:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrappe r//chromium_browser" pid=832 comm="apparmor_parser"
[    3.479620] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    3.479729] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    3.479807] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    3.479858] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    3.479944] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    3.479988] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14

> **Cheesehead said:**
> Also, take a look at /etc/udev/rules.d/70-persistent-net.rules (yours  might not be '70-'). If there is anything in that file, please post  it.

Don't know how to do that.

> **dannyboy79 said:**
> check to see if the module is loaded for that chipset

sudo lsmod | grep e1000e

Nothing displayed in terminal.

Thanks in advance for your help.

---

### Post by dannyboy79 on 2012-12-13
> **drilltotheheavens said:**
> Hello, Complete linux noob here. I just built a pc and successfully installed ubuntu 12.10. However, just like the thread starter, my computer is not detecting the ethernet cable I plugged in.



03:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
Subsystem: Giga-byte Technology Device e000
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
I/O ports at d000 [size=128]
Capabilities: <access denied>



Nothing displayed in terminal.



lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:224 errors:0 dropped:0 overruns:0 frame:0
TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:18400 (18.4 KB) TX bytes:18400 (18.4 KB)



What's telling me that the driver was successfully installed?



[    3.246843] type=1400 audit(1355396781.949:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=832 comm="apparmor_parser"
[    3.246957] type=1400 audit(1355396781.949:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=833 comm="apparmor_parser"
[    3.247008] type=1400 audit(1355396781.949:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=830 comm="apparmor_parser"
[    3.247018] type=1400 audit(1355396781.949:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrappe r//chromium_browser" pid=832 comm="apparmor_parser"
[    3.479620] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    3.479729] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    3.479807] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    3.479858] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    3.479944] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    3.479988] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14



Don't know how to do that.



Nothing displayed in terminal.

Thanks in advance for your help.You probably should've started your own thread but I'll answer it anyway. You have a very new combined ethernet/bluetooth chipset that doesn't have a module in the kernel yet since it's such new hardware. Follow the directions here: [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

---

### Post by drilltotheheavens on 2012-12-17
Those are instructions for 12.04 though. Further, I do not have a computer with Linux that also has an internet connection.

---

