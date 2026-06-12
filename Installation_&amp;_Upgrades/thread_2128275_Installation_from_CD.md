---
title: "Installation from CD"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by bschmitt13 on 2013-03-22
I have an older AMD Athlon based computer. It does not recognize flash drives for booting, so when I tried that route, it failed. It only has a CD drive on it, not a DVD drive, so all of the iso images I've been able to find are too large to fit. Is there a version of an installer that will fit on a CD and then allow me to upgrade?

---

### Post by ManamiVixen on 2013-03-22
There is a way to install, but does the computer have a ethernet port? It will need to be plugged straight into a router or dsl/cable modem. Wireless will not work. Also, what CPU is it exactly? We will need to know if it supports PAE. If your CPU does not have PAE, you cannot use 12.04 or later and you will be limited to 11.10 and earlier.

---

### Post by ibjsb4 on 2013-03-22
12o4 fits on a CD, but like [**[COLOR=#000000]ManamiVixen[/COLOR]**]("http://ubuntuforums.org/member.php?u=1777813") said, is you computer up to running it.  Whats your specs?

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by plucky on 2013-03-22
> **bschmitt13 said:**
> I have an older AMD Athlon based computer. It does not recognize flash drives for booting, so when I tried that route, it failed. It only has a CD drive on it, not a DVD drive, so all of the iso images I've been able to find are too large to fit. Is there a version of an installer that will fit on a CD and then allow me to upgrade?

Try using the [Plop Boot Loader](http://www.plop.at/en/bootmanager/index.html) to boot the USB drive on any system that cannot boot fom USB.

You can either load from CD or Floppy.

Good Luck

---

### Post by bschmitt13 on 2013-03-22
It's actually an AMD Sempron Processor. The specs say Model: 3000+;  Operating Mode 32 Bit/64 Bit; Revision: E6; Core Speed (MHz): 1800. It's  installed on an MSI Motherboard (K8MM-V). I don't believe PAE is there,  there is nothing about it in the documentation or the BIOS screens. 1  GB og memory on it. There is an ethernet port but no boot from network  that I can find. I do have another Win/XP machine I could put a DVD into  if there is an installer that could use it from there. A frustrating  thing here is that the MB is IDE and SATA 1.5. There are two SATA  connections on the MB, but one doesn't work (no idea why). I have a SATA  DVD and a SATA HD, but can only use 1. The CD Drive is IDE and was  grabbed from an old case that was discarded. I have no idea where I  would find an IDE DVD drive anymore. This machine ran XP until the hard  drive crashed.

---

### Post by ManamiVixen on 2013-03-22
Oh.... I know EXACTLY what computer you have and trust me, Ubuntu isn't worth the pain and agony required to get it working. It comes with a VIA chipset which has virtually NO LINUX SUPPORT. VIA never released proper drivers for their hardware so Linux won't run well if at all. Trust me, I had that EXACT SAME CPU AND MOTHERBOARD. It came as a all-in-one package from CompUSA and I thought it was a steal at the time for $40. I regret ever buying it cause in the 1 year of owning it, Linux wouldn't run... Ever.

---

### Post by sanderj on 2013-03-22
> **bschmitt13 said:**
> It's actually an AMD Sempron Processor. The specs say Model: 3000+;  Operating Mode 32 Bit/64 Bit; Revision: E6; Core Speed (MHz): 1800. It's  installed on an MSI Motherboard (K8MM-V). I don't believe PAE is there,  there is nothing about it in the documentation or the BIOS screens. 1  GB og memory on it. There is an ethernet port but no boot from network  that I can find. I do have another Win/XP machine I could put a DVD into  if there is an installer that could use it from there. A frustrating  thing here is that the MB is IDE and SATA 1.5. There are two SATA  connections on the MB, but one doesn't work (no idea why). I have a SATA  DVD and a SATA HD, but can only use 1. The CD Drive is IDE and was  grabbed from an old case that was discarded. I have no idea where I  would find an IDE DVD drive anymore. This machine ran XP until the hard  drive crashed.

According to [http://www.cpu-world.com/CPUs/K8/AMD-Sempron%2064%203000+%20-%20SDA3000AIO2BX%20(SDA3000BXBOX).html](http://www.cpu-world.com/CPUs/K8/AMD-Sempron%2064%203000+%20-%20SDA3000AIO2BX%20(SDA3000BXBOX).html) the Sempron 3000+ with 1800 Mhz is 64-bit. So I certainly expect it to have 32-bit PAE.

Anyway: I would advice Lubuntu as your system is a bit old and hasn't got too much RAM. So, go to [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) , download the 64-bit CD image, burn it to CD and boot it in the Sempron machine

EDIT: according to [http://en.wikipedia.org/wiki/Sempron](http://en.wikipedia.org/wiki/Sempron) the 3000+ 1800Mhz is ... 32bit. So get the 32-bit Lubuntu from said URL.

HTH

---

### Post by ibjsb4 on 2013-03-22
> **ManamiVixen said:**
> Oh.... I know EXACTLY what computer you have and trust me, Ubuntu isn't worth the pain and agony required to get it working. It comes with a VIA chipset which has virtually NO LINUX SUPPORT. VIA never released proper drivers for their hardware so Linux won't run well if at all. Trust me, I had that EXACT SAME CPU AND MOTHERBOARD. It came as a all-in-one package from CompUSA and I thought it was a steal at the time for $40. I regret ever buying it cause in the 1 year of owning it, Linux wouldn't run... Ever.

[http://us.msi.com/product/mb/K8MM-V.html#/?div=Detail](http://us.msi.com/product/mb/K8MM-V.html#/?div=Detail)

[http://www.via.com.tw/en/support/tech_faq.jsp#linux](http://www.via.com.tw/en/support/tech_faq.jsp#linux)

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by ManamiVixen on 2013-03-22
[**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120") Yeah, but that means you must download and manually install them. Hence the pain and agony part.They are not even part of the Linux Kernel and have to be added on as modules. So they are not open sourced drivers. They also tend to be buggy and lots of things go wrong installing them. Anyways, those are relatively recent and at the time I had that system, it was 2008 and the drivers and such didn't exist and in a way still don't unless you use VIA's site.

---

### Post by ibjsb4 on 2013-03-22
> **ManamiVixen said:**
> [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120") Yeah, but that means you must download and manually install them. Hence the pain and agony part.They are not even part of the Linux Kernel and have to be added on as modules. So they are not open sourced drivers. They also tend to be buggy and lots of things go wrong installing them. Anyways, those are relatively recent and at the time I had that system, it was 2008 and the drivers and such didn't exist and in a way still don't unless you use VIA's site.

Yes, the way Im reading those links, you can forget any support.

---

### Post by ManamiVixen on 2013-03-22
Fine[**[COLOR=#000000] ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120"). Then can you kindly explain to [**[COLOR=#000000]bschmitt13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1802581") how to compile and install the drivers? Cause I find it hard to believe a newcomer to Linux dosen't know how to do that. Cause you know everyone does It easy. Especially getting all the dependencies correct and the correct flags for your hardware! Oh and the hours spent trying to get them work right is an absolute pleasure! [**[COLOR=#000000]bschmitt13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1802581") will be fine.

---

### Post by ibjsb4 on 2013-03-22
> **ManamiVixen said:**
> Fine[**[COLOR=#000000] ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120"). Then can you kindly explain to [**[COLOR=#000000]bschmitt13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1802581") how to compile and install the drivers? Cause I find it hard to believe a newcomer to Linux dosen't know how to do that. Cause you know everyone does It easy. Especially getting all the dependencies correct and the correct flags for your hardware! Oh and the hours spent trying to get them work right is an absolute pleasure! [**[COLOR=#000000]bschmitt13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1802581") will be fine.

Im in agreement with you :confused:

We appear to be suffering a communications gap :)

---

### Post by ManamiVixen on 2013-03-22
Oh, I thought it was sarcasm, sorry. XD

---

### Post by ibjsb4 on 2013-03-22
No harm done :)

---

### Post by bschmitt13 on 2013-03-22
Thanks, everyone. I will give it a shot with all the pointers you've given and see what happens. My Linux is admittedly weak, but I've done just about everything else so I may even try the compile. I've written JCL requiring Compile AND Link (two separate steps) on Mainframes so how difficult can it be? :) This is a Micron box that started out running Win95 a long time ago and has had Motherboards (after a lightning strike somehow got through), Disks, and adapters swapped in and out since then. I think the only thing original is the case itself, so I've gotten my money's worth out of it. But it's a good challenge. Thanks for all the advice.

Bill

---

