---
title: "A question for you all... (porting my current ubuntu to my harddrive)"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by jenarelJAM on 2008-04-09
So, a couple months ago, I became interested in running Linux as a secondary option to Windows. I was a little wary of dual booting my machine, and decided to try something I hadn't heard of anyone else doing. I installed linux on a flash drive. Not just a USB live cd (although I managed to set that up on a separate partition of the same drive), but I actually installed the entire Ubuntu Gutsy to the flash drive as if it were a hard drive.

Okay, so where I'm at right now is that I have a vista machine (lenovo X61 tablet), and I have my bios set to boot from USB HD when detected. So when I want to go to linux, I hibernate windows, plug in the flash drive, and turn on the computer again.

But I've already bumped the flash drive a bit and bent it slightly (it still works fine), and I have plenty of extra space on my hard drive (I keep it very clean) to donate 10GB or so to linux, so I think it's a worthwhile investment to take the plunge and dual-boot my system.

Now: Ubuntu needed a lot of configuration for my system. I'm still a relative newbie to linux, and it was a pain for me to modify all those .conf files to make things like my pen (it's a tablet) work, the trackpoint work as a scroll bar, compiz work, etc., not to mention I've installed a significant number of programs I need that I would then have to reinstall. 

Is there a way I can "port" or "copy" my current version of Ubuntu (with applications, documents, files, etc.)  from my flash drive to a partition on m hard drive?

Now also, I'm wary, because I've already overwritten my Master Boot Record once with  GRUB, and it killed my hard drive. I had to try to salvage my files, get a new hard drive, restore from a backup, and then update all my files. I REALLY don't want that to happen again.

What can I do?

---

### Post by kellemes on 2008-04-09
> **jenarelJAM said:**
> Now also, I'm wary, because I've already overwritten my Master Boot Record once with  GRUB, and it killed my hard drive. I had to try to salvage my files, get a new hard drive, restore from a backup, and then update all my files. I REALLY don't want that to happen again.

Sorry, I can't give any advise on your questions, but surely some others can.

I am a little surprised you had to buy a new HD just because you overwritten the MBR, the MBR needs to be overwritten to be able to run multiple OS's and there is no way you can kill your HD like that. You got scared I guess ;-) No need to.

Next time when you feel you have killed your MBR you can simply reinstall the bootloader of your choice, either the Windows-bootloader using the Windows-installer, or Grub using a Linux livesystem.
Even easier is to download/burn/boot [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), from this tool you can do all kinds of cool stuff, like reinstalling your bootloader, or reconfiguring your bootloader, or boot-up any OS installed at any of your devices etc.. etc..

---

### Post by jenarelJAM on 2008-04-09
When I said it killed my hard drive, I mean it really killed it. Perhaps it coincidentally died for another reason at the exact same time, but I was not able to recover from it.

I tried to restore the OS from a backup.
I tried to restore Everything from a backup.
I tried to restore from a factory state disk
I tried to recover from a Windows Install Disk
I tried to reinstall from a Windows Install Disk
I tried to reformat the drive as an external drive to another computer: it crashed the other computer twice(once, the computer locked up, and once I got a BSOD)

It was a major headache...
Luckily, IBM has amazing service, and they shipped me out a replacement under warranty.

---

