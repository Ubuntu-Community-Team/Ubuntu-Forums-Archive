---
title: "Alternate CD Install Problems"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by dorion on 2007-02-02
Hi, I'm having problems in the actual install process of Ubuntu under the Alternate CD. My problem is that the CD drive detection process freezes saying:
> Loading Module 'trm290' for 'IDE Chipset Support'

Yes, I have verified the disk. 

I have no idea how to fix this.

---

### Post by K.Mandla on 2007-02-02
Try an expert installation, and you should be able to screen out the offending module, and hopefully get past that point in the process.

Unfortunately, expert installations take a little longer and require a little extra thinking. 

What kind of computer are you using? What kind of CDROM are you using?

If your network card is configurable under the Ubuntu installation process, you might be able to get away with a netboot install.

There are also options to install from an ISO copied to a hard drive, or install from another distro ... or from Windows. 

You're not sunk yet! :mrgreen:

---

### Post by mikewhatever on 2007-02-02
Having looked at the [ other post you made, ](http://ubuntuforums.org/showthread.php?t=348573) I'd say you should try redownloading, or reburning, perhaps on another PC, or, if nothing works, order one by mail.

---

### Post by dorion on 2007-02-03
Mikewhatever, thanks for looking at my other post, but I finally found a computer to verify the CD with, the names of some of the files on the CDs were being read incorrectly by windows and MD5summer, and the md5 progrm included on Cygwin were throwing errors, and the one bad hash was fixed.

So K.Mandla, is Expert Install the OEM option? How do I screen out the faulty module, I looked at [The Linux Bootpromt-How To]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html") but its way to much info and mostly over my head.

I've got a crossover cable to connect my laptop for a netboot... but that again seems like a bit over my head, but my Computer has a Via chipset so should be no problem on the hardware.

I've tried two Install from Windows approaches, one I found on [Digg]("https://wiki.ubuntu.com/install.exe/"), and Instlux. Both failures.

The computer I'm trying to install on is:
AMD64
Soltek K890 Motherboard
2GB of Ram
ATI 850 Video Card
2 40GB SATA Harddrives in Raid 0(Windows Drives)
30GB Drive(Future Linux Drive)
Sony DVD Drive
LiteOn DVD-RW SATA Drive(I avoid this thing except when I need to burn)
SoundBlaster Sound Card and a cheap TV Tuner

I also have a Macbook which irratatingly has only one problem but thats no problem, its been a lifesaver in the whole affair. Possible netboot install?

Oh and a 10GB USB HardDrive which I haven't tried an install off of yet. 

Thanks very much.

---

### Post by dorion on 2007-02-03
Ok well the minimal install installed without a hitch, thanks for the encouragement, but I'm off to learn me some linux.

---

