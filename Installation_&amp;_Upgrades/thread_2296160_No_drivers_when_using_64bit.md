---
title: "No drivers when using 64bit"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by Nathan_Spiegel on 2015-09-23
Hi guys, first forum post here so maliciously berate me if I don't follow protocol properly ;)

What I'm trying to do: Install 64bit ubuntu desktop to a separate ssd hard drive (hard drive is empty, windows 10 on a seperate drive)

What's happening: If I try to install a 64bit ubuntu system (either by DVD or bootable usb) The installation technically goes fine, but none of my USB's work, and the wired ethernet connection isn't detected (during install nor after). Luckily my mother board has one of those old fashioned keyboard inputs (not sure what they're called) and I can plug one in and muddle around, but no mouse works and I cant do much further as no networking.

I found a DVD I had burned a few months ago and thinking it might be an older version, I installed it and noticed that networking was detected during installation and all my usb's (keyboard mouse, audio) were all working great. Afterwards, I noticed that it was a 32bit operating system that I had been able to install successfully and use.

To sum all that up, it seems that 32bit OS will detect all my hardware, 64bit will not.

Hopefully you all can provide some insight as I'd really love to get it working with a 64bit OS. This is my first venture into linux desktop stuff. I've got a lot of experience with ubuntu server and centos (unfortunately) so hit me with any questions you may have.

---

### Post by oldos2er on 2015-09-23
What is your motherboard make & model? And other hardware specs too.

---

### Post by Nathan_Spiegel on 2015-09-23
Board: Gigabyte Technology Co., Ltd. 990FXA-UD3 
Bus Clock: 200 megahertz
UEFI: American Megatrends Inc. F2 07/15/2013

8172 Megabytes Usable Installed Memory

AMD Radeon R9 200 Series [Display adapter]

KINGSTON SV300S37A60G [Hard drive] (60.02 GB) -- drive 0, s/n 50026B7749005BBB, rev 580ABBF0, [SMART]("http://www.belarc.com/smart.html") Status: Healthy
WDC WD10EZEX-22BN5A0 [Hard drive] (1000.20 GB) -- drive 1, s/n WD-WCC3FJFP11F7, rev 01.01A01, [SMART]("http://www.belarc.com/smart.html") Status: Healthy

3.93 gigahertz AMD FX-8350 Eight-Core

AMD PCI IDE Controller
AMD SATA Controller
ATA Channel 0 [Controller]

Marvell 91xx SATA 6G Controller
Marvell Storage Virtual Device
Microsoft Storage Spaces Controller
Standard Enhanced PCI to USB Host Controller (3x)
Standard OpenHCD USB Host Controller (4x)
VIA USB 3.0 eXtensible Host Controller - 1.0 (Microsoft)

---

### Post by Nathan_Spiegel on 2015-09-23
also have this belarc profile for you [URL="http://e-dev.us/files/profile.htm"]http://e-dev.us/files/profile.htm
[/URL]

---

### Post by QIII on 2015-09-23
Hi.  That's a common issue with those boards.

Please have a look at [http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)

That should help.  But if you have any questions, be sure to come back and ask.

---

### Post by Nathan_Spiegel on 2015-09-23
> **QIII said:**
> Hi.  That's a common issue with those boards.

Please have a look at [http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)

That should help.  But if you have any questions, be sure to come back and ask.

This is the kind of help that made me want to get into linux in the first place! Worked like a charm and I am up and running now . Much appreciated. I'm sure ill be back in the future with more issues, but until then, thank you!

Cheers,
Nate

---

### Post by oldos2er on 2015-09-24
Could you please mark the thread as 'Solved' (under Thread Tools at the top of the page)? Thanks.

---

