---
title: "Loading problem...?"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by ubunchu64 on 2013-06-11
Hi, I have a Windows 8 HP Pavilion g6 laptop computer and I am having a tough time running ubuntu along-side win-8. I'll explain. When I start my computer (Note this is after install, before it everything worked fine.) I get an OS boot manager that says Windows 8, but no ubuntu 12.04 LTS. I press escape to get to the boot manager and there is two ubuntu's. I click on the one with a capital U and it takes me back to the OS boot manager with the screen res different. I click the lowercase one and it takes me to a glitchy screen with a bunch of options. It looks purple with white words stretched out so badly I cant read it. I press enter for the first one 'cause i don't know any better, and it takes me to ubuntu. No problem right? WRONG. I try to do as much as I can, but then the mouse starts getting "icy", it slides alot and the programs freeze, as I cant do anything. I try to struggle, and my computer slam-shuts down on me. Help???

---

### Post by claracc on 2013-06-12
How did you install ubuntu, through wubi or is is a dual boot installation?.

This thread: [http://ubuntuforums.org/showthread.php?t=2088425](http://ubuntuforums.org/showthread.php?t=2088425) contains a lot of valuable information. Perhaps it can help you.

---

### Post by fantab on 2013-06-12
What version of Ubuntu do you have? Does you Windows8 boot in EFI mode? if yes, then have you installed Ubuntu in EFI mode?
Have you [disabled 'fast startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")'? Have you disabled 'fast boot'? Have you disabled 'Intel SRT', if you have it?

If you have an SSD pre-insatalled then what mode is you SATA set to? You can check this in BIOS UEFI. 

Boot with Ubuntu LiveDVD/USB and post the output of:

```
sudo parted -l
```

Installing Ubuntu alongside Windows 8 needs some special care, read: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by ubunchu64 on 2013-06-12
> **claracc said:**
> How did you install ubuntu, through wubi or is is a dual boot installation?.This thread: [http://ubuntuforums.org/showthread.php?t=2088425](http://ubuntuforums.org/showthread.php?t=2088425) contains a lot of valuable information. Perhaps it can help you.Thanks for your reply, I am running a dual boot installation through my USB disc. Im not that much of a genius with computers so EFI and UEFI are new to me. Sorry for the trouble, but thanks for your reply.

---

### Post by ubunchu64 on 2013-06-12
> **fantab said:**
> What version of Ubuntu do you have? Does you Windows8 boot in EFI mode? if yes, then have you installed Ubuntu in EFI mode?
Have you [disabled 'fast startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")'? Have you disabled 'fast boot'? Have you disabled 'Intel SRT', if you have it?

If you have an SSD pre-insatalled then what mode is you SATA set to? You can check this in BIOS UEFI. 

Boot with Ubuntu LiveDVD/USB and post the output of:

```
sudo parted -l
```

Installing Ubuntu alongside Windows 8 needs some special care, read: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Thanks for the reply, I am currently using the LTS version. I have no idea what EFI is and could you explain it. Fast startup I just turned off. Fast boot im confused. Intel SRT i have never seen on my computer.

---

### Post by fantab on 2013-06-12
Post the output of the above command. Its important.

To put it simply, UEFI (earlier EFI) is the replacement for BIOS. BIOS is 30years old interface and has limitations with newer hardware. To boot in UEFI we need GPT (GUID Partition Table). Most of the new OEM machines have UEFI. Most of the Windows8 preinstalled machines do. If Windows 8 is booting in UEFI then Ubuntu too needs to be installed in UEFI. To install Ubuntu in UEFI/EFI, the LiveDVD/USB needs to be booted in EFI mode.

The link I posted in my earlier post has most of the things you need to know about UEFI and Dual booting with Windows8. You must read 'em.

Once the requested output of 'sudo parted -l' is provided we can help you precisely.

Good Luck...

---

