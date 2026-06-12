---
title: "Wireless &amp; speakers problem"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by sophist on 2010-05-18
Hello Guys,

I have just received my new laptop T410s Lenovo, and I've installed the latest Ubuntu 10.4 and at the end of the installation There was an error MSG which I don't remember right now.

The problem is once I logged in I found out that the wireless is not working I only can connect through Ethernet and also the speakers are not working. 

waiting for your help.


Regards
Sophist.

---

### Post by lykwydchykyn on 2010-05-18
First stop is to the hardware drivers tool, to see if any nonfree drivers need to be loaded to make your sound/wireless work.

If anything is listed, connect the ethernet and activate the drivers.

If not, post the output from running "lspci" in a terminal here so we can see what hardware is on the system.

---

### Post by John F on 2010-05-18
If basic functions like connecting to a wireless network do not work on start-up, Ubuntu is not going to win over any but a few die-hard enthusiasts.

---

### Post by sophist on 2010-05-18
thanks for your attention,


first of all i want to mention that the wireless is not scanning for any network


I did the following 

System > admin > Hardware Drivers

nothing listed even after i get connected to the Ethernet

went to terminal and typed lspci and herein  the results 



 sophist@sophist-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation Device 3b57 (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 35)
05:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
05:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
sophist@sophist-laptop:~$

---

### Post by cariboo on 2010-05-18
WHat's the output of:

```
sudo lshw -C networking
```

---

### Post by lykwydchykyn on 2010-05-18
Looks like support for that wireless chipset is a known problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532451)

I'd keep an eye on that bug report for possible workarounds.

Not sure about the audio yet; if you launch the mixer, does it seem to indicate that it sees the card? (I don't use GNOME, so I don't know the details of what it would say).

---

### Post by sophist on 2010-05-18
It's PCI (sysfs)

> **cariboo907 said:**
> WHat's the output of:

```
sudo lshw -C networking
```

---

### Post by sophist on 2010-05-19
what about the speakers ?

---

### Post by lykwydchykyn on 2010-05-19
> **sophist said:**
> what about the speakers ?

> **lykwydchykyn said:**
> 
Not sure about the audio yet; if you launch the mixer, does it seem to indicate that it sees the card? (I don't use GNOME, so I don't know the details of what it would say).

Not to be rude, but it's kind of hard to help if you don't answer my questions...

---

### Post by sophist on 2010-05-24
I've fixed my sounds card issue by upgrading Alsa .

but now i'm really confused about the wireless issue

i was searching and most of the help forum saying that Intel didn't realse an update for Intel wimax 6050

and while i was checking my wireless on windows I found it in a different name a -Intel® Centrino® Advanced-N + WiMAX 6250

but in

Ubuntu it shows 

Intel WiMAX/WiFi Link 6050 series

I found at Intel website for Linux they are supporting

Intel® Centrino® Advanced-N + WiMAX 6250  for Linux


[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3199&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3199&lang=eng")


i'm really confused

---

