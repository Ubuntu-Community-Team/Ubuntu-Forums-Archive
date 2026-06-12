---
title: "Dual Boot"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by CasPol on 2008-01-23
Hi there;

I have played around with Ubuntu and do like it. I want to install on a system with two Hard Drives. Hard Drive 1 ( master) at the moment has WinXP on it. Hard Drive 2 (slave) is empty. I do not want to loose WinXP as I still need it for a while yet. I have tried this on another system and found that GRUB did overwrite the WinXP MBR.

I want the MBR on the WinXP drive untouched. How can I install Ubuntu on the second hard drive without GRUB overwriting the MBR, and subsequently let WinXp boot and give me choice to go into WinXP or Ubuntu.... ?

Many thanks !!

---

### Post by kellemes on 2008-01-23
> **CasPol said:**
> Hi there;

I have played around with Ubuntu and do like it. I want to install on a system with two Hard Drives. Hard Drive 1 ( master) at the moment has WinXP on it. Hard Drive 2 (slave) is empty. I do not want to loose WinXP as I still need it for a while yet. I have tried this on another system and found that GRUB did overwrite the WinXP MBR.

I want the MBR on the WinXP drive untouched. How can I install Ubuntu on the second hard drive without GRUB overwriting the MBR, and subsequently let WinXp boot and give me choice to go into WinXP or Ubuntu.... ?

Many thanks !!


Why don't you want the MBR overwritten?
Nothing wrong with Grub, for me it's the best bootloader for multiboot.
Also.. you can simply reinstall the Windows bootloader using the Windows-cd or [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by bwtranch on 2008-01-23
Re#2

No, I don't really agree. Best to leave GRUB out of the picture and part with fdisk or something like it. 

Look at the Gentoo website for details on how to do this. You don't have to install Gentoo. I'm just saying there is some good info there.

I don't think that GRUB is always bad. I'm just saying that it doesn't always work. I think in this instance, you will have to manually configure the drives.

---

### Post by CasPol on 2008-01-23
Thanks for replying so quick to my question. I am sorry to have to say  that restoring the MBR is not as simple as it seems, judging from all the postings of many people in many forums. I do not assume "grub" is a bad thing, I do think though that for a beginner like me it would be better to install a linux distro without grub..... to play it safe and get some more grub-experience first. I cannot afford any problems with the windows installation on this particular computer because other people need to use it as well. I will certainly get hold of a copy of super grub disk ( might come in hany anyway) but would still like to boot from windows rather then Ubuntu.

---

