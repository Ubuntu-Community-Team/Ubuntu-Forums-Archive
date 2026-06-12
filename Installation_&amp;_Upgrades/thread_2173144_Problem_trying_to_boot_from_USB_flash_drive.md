---
title: "Problem trying to boot from USB flash drive"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2013-09-08
I've had this problem several times with Ubuntu distro and other distros.
In the latest case I've downloaded the Zorin distro and used Startup Disk Creator to attempt to create a bootable USB flash drive that way.
On booting I see Syslinux info, then boot: followed by a flashing cursor and distro does not then proceed to boot.
Help please.

---

### Post by sudodus on 2013-09-08
Sometimes there are problems with the USB Disk Creator. There are several other methods and tools.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

But the first step is to check that the download was OK. Check the md5sum!

The next step, since your computer boots from the USB drive, is to try various boot options, to help the system with some hardware, that is not properly supported. Start with ***nomodeset***, since I suspect problems with the graphics chip/card.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Please specify the computer: Brand name and model, cpu, ram (size), graphics and wifi chip/card. It will make it easier to give good advice.

---

### Post by welshmike on 2013-09-08
> **sudodus said:**
> Sometimes there are problems with the USB Disk Creator. There are several other methods and tools.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

**Thanks. I'll check there**
> But the first step is to check that the download was OK. Check the md5sum!

**It was a good download because I can boot from a DVD burned from the iso using Brasero**
> 
The next step, since your computer boots from the USB drive, is to try various boot options, to help the system with some hardware, that is not properly supported. Start with ***nomodeset***, since I suspect problems with the graphics chip/card.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

**Will do**
> 
Please specify the computer: Brand name and model, cpu, ram (size), graphics and wifi chip/card. It will make it easier to give good advice.

[B]Dual boot Ubuntu & XP
MSi CR620 (Novatech i3 Core i3-350M) 2.27GHz 2GiB RAM, Ubuntu 12.04
and from lspci:
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
[/B]

---

### Post by sudodus on 2013-09-08
Intel graphics will usually work well with the graphics drivers in the Ubuntu flavours. I'm not sure if the network chip will create problems, but other people will be reading this, and someone may know ...

***Ubuntu 12.04 LTS*** is more debugged and polished than the other versions, so I suggest that you try that version, if you have not tried it already. Unless your computer is brand new, then the latest version may have drivers, that are missing in older versions. You may even try ***Lubuntu 13.10 beta 1*** (to be released late in October).

---

### Post by welshmike on 2013-09-08
I am running 12.04 LTS on my laptop right now and like it a lot since the annoying small problems and some performance ones with 11 I found are fixed.
It will not be suitable from my OS averse Windows XP friend though.

I have now managed to get Zorin bootable from my USB flash drive by using Unetbootin to creat the system.
So I must close this report as solved.

---

