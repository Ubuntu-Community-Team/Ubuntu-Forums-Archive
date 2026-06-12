---
title: "asus UL30 dual boot. boot/grub problem"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by aurantium_risso on 2010-11-23
Hello everyone!

I have a pretty new ASUS UL-30 laptop that works just fine with dual boot. I have windows 7 and the newest Ubuntu on it.

A few days ago I decided that I wanted to reinstall windows from the hidden backup partition and later reinstall ubuntu as well to make the computer fresh and new again with same setup as before. When I ran the hidden partition it asked me if it should use the entire harddrive (except hidden partition of course) which I said yes to. It then created a big windows partition and here comes my problem:

When I wanted to reboot the computer into windows all I got was this message:
```

error: no such partition.
grub rescue>

```Clearly windows recreated it's partition but didn't bother to fix the rest.

Then I thought that maybe if I boot from a USB stick with ubuntu I could reinstall ubuntu and thereby create the same functioning boot sequence with ubuntu/windows as before or atleast just ubuntu.

however, when I run the USB stick created with the "usb-creator" I get:

```

Syslinux 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al
_ 

```and then nothing happens.

I also tried to boot using an usb with system rescue CD which works just fine and I can access internet and so on. In this program I can access gparted, emelFM2, Hardware Lister, Htop Midnight Commander, Mrxvt, Partimage, Show Filesystems, Terminal, Testdisk etc. 

what should I do do to fix this? 

If I cannot get them both to function again, then I'd rather have just ubuntu because I use the windows system very rarely. 

I appreciate all the help I can get with this problem... the solution is unfortunately beyond my limited skills. :-(

Thanks for all your help in the past too. Alot of problems were solved for me here in ubuntu forums.

---

### Post by lmarmisa on 2010-11-23
The new installation of Windows 7 did not update the code area (first 440 bytes) of [the MBR]("http://en.wikipedia.org/wiki/Master_boot_record") with the Windows 7 loader, maintaining the previous GRUB loader. 

But GRUB is not able to start the system because the Ubuntu partition and its folder /boot have been deleled. 

I believe that this is your problem.

So, when you re-install Ubuntu, you will solve your problems.

You should be able to boot Ubuntu from a Live CD (using an USB CD/DVD drive) or from a USB stick.  Maybe the data of your USB stick are corrupted. Try to create a new one.

---

### Post by aurantium_risso on 2010-11-23
> **lmarmisa said:**
> The new installation of Windows 7 did not update the code area (first 440 bytes) of [the MBR]("http://en.wikipedia.org/wiki/Master_boot_record") with the Windows 7 loader, maintaining the previous GRUB loader. 

But GRUB is not able to start the system because the Ubuntu partition and its folder /boot have been deleled. 

I believe that this is your problem.

So, when you re-install Ubuntu, you will solve your problems.

You should be able to boot Ubuntu from a Live CD (using an USB CD/DVD drive) or from a USB stick.  Maybe the data of your USB stick are corrupted. Try to create a new one.

Is it a bad sign that I have to push [ESC] in order to get the computer to boot from the USB?

I tried booting it with an USB containing a newly downloaded and unpacked ubuntu iso file. I tried using the usb creator program last time and now I tried just unpacking the iso on the USB and then I got this message, which is almost like the last one:

```

Syslinux 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 H. Peter Anvin et al
No DEFAULT or UI configuration directive found!
boot: 

```this is all so very strange but I agree with you - it should not be that difficult to just boot from an USB but for some reason it does not seem to work.

---

### Post by lmarmisa on 2010-11-23
I do not know your computer, but I recommend to enter the BIOS menu and select your USB stick as the first priority device to boot.

You made a comment in your first post about a system rescue CD wich works just fine. If you have a CD/DVD drive, you could use an Ubuntu Live CD for the installation.

---

### Post by aurantium_risso on 2010-11-23
> **lmarmisa said:**
> I do not know your computer, but I recommend to enter the BIOS menu and select your USB stick as the first priority device to boot.

You made a comment in your first post about a system rescue CD wich works just fine. If you have a CD/DVD drive, you could use an Ubuntu Live CD for the installation.

I went into the BIOS and changed the boot order so it is removable device as number one, but for some reason it does not seem to help either... :(

Well my computer does not have CD-drive. If it had a cd it would be simpler I think. The System rescue CD-program works fine and I am able to boot into it but I dont know what to do when I have that program started. 

Another problem I have is that the only working computer I have now is an older windows XP machine. Between every new USB installation I try I do a normal format of the USB memory to sure that its clean. 

Should I try some other linux live version on my USB, or what is the best course of action?

---

### Post by aurantium_risso on 2010-11-23
I booted into Ubuntu Rescue Remix from the USB just now.
For the default live system it says I should enter "live" in the "boot:" prompt.

when I do enter "live" I get this message:
```

Can not mount /dev/loop1 on /cow
_

```

---

### Post by lmarmisa on 2010-11-23
Were you able to boot successfully Ubuntu from your USB stick before the occurrence of this problem?.

You have an old computer running XP. Can you boot Ubuntu in this computer using your USB stick?.

Do you have a CD drive in your older computer?.

Is the System Rescue CD program stored in your BIOS?

[http://www.sysresccd.org/Screenshots](http://www.sysresccd.org/Screenshots)

---

### Post by aurantium_risso on 2010-11-23
> **lmarmisa said:**
> Were you able to boot successfully Ubuntu from your USB stick before the occurrence of this problem?.

You have an old computer running XP. Can you boot Ubuntu in this computer using your USB stick?.

Do you have a CD drive in your older computer?.

Is the System Rescue CD program stored in your BIOS?

[http://www.sysresccd.org/Screenshots](http://www.sysresccd.org/Screenshots)

I installed ubuntu on the USB after this trouble and I never tried booting from any USB before all this.

The problem with the older computer is that it's my girlfriends work computer so if something happens to it - she'll kill me! :) therefore I'm too afraid to change boot order or so to try the usb. The old computer has a CD drive though.

The system rescue CD is not stored on my bios, I installed it on an USB and succeeded in booting into that USB system.

---

### Post by lmarmisa on 2010-11-23
> **aurantium_risso said:**
> I installed ubuntu on the USB after this trouble and I never tried booting from any USB before all this.

The problem with the older computer is that it's my girlfriends work computer so if something happens to it - she'll kill me! :) therefore I'm too afraid to change boot order or so to try the usb. The old computer has a CD drive though.

The system rescue CD is not stored on my bios, I installed it on an USB and succeeded in booting into that USB system.

Thanks for your answers.

First of all, we have to try your girlfriend does not kill you. ;)

If you succeed in booting into system rescue USB stick and you fail with Ubuntu USB stick, it seems clear that usb-creator is not the appropriate tool for creating your Ubuntu USB stick.

I always use the Startup Disk Creator included in the Ubuntu Live CD. This is 100% reliable.

In my humble opinion, you should burn a CD with the Ubuntu 10.10 iso file. Then boot your older PC from this Live CD and create a Ubuntu USB stick using the Startup Disk Creator tool.

I think this new USB stick will be correct.

A minor question: do you plan to install a 64 or 32 bits version of Ubuntu?.

---

### Post by aurantium_risso on 2010-11-23
> **lmarmisa said:**
> Thanks for your answers.

First of all, we have to try your girlfriend does not kill you. ;)

If you succeed in booting into system rescue USB stick and you fail with Ubuntu USB stick, it seems clear that usb-creator is not the appropriate tool for creating your Ubuntu USB stick.

I always use the Startup Disk Creator included in the Ubuntu Live CD. This is 100% reliable.

In my humble opinion, you should burn a CD with the Ubuntu 10.10 iso file. Then boot your older PC from this Live CD and create a Ubuntu USB stick using the Startup Disk Creator tool.

I think this new USB stick will be correct.

A minor question: do you plan to install a 64 or 32 bits version of Ubuntu?.

I only tried installing the 32-bit version so far.

I downloaded "Universal-USB-Installer-1.8.1.4" from the ubuntu page and did an installation on the USB with ubuntu 10.10. 

The message I got when I tried it was: 

```

SYSLINUX 4.02 2010-07-21 EDD Copzright (C) 1994-2010 H. Peter Anvin et al
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: _

```I will go down town now, buy a CD and then try booting the old computer into ubuntu and do the USB from there. Let's hope for the best! I'll report back as soon as I've tried it!

---

### Post by lmarmisa on 2010-11-23
Something is different in the new Ubuntu 10.10 version.

I tried to create a USB pendrive for Ubuntu 10.10 from the Startup Disk Creator of Ubuntu 10.04 and it failed. I had to use Ubuntu 10.10 tools for creating a Ubuntu 10.10 USB stick.

---

### Post by mike daly on 2010-12-30
Please understand that I am so new I can't be trusted.  This happened to me a couple years ago and I remember a DOS command  FDISK /MBR which recreated the boot record and overwrote GRUB..  I think I got to the dos prompt by going to the rescue disk and then ctrl-break or crtl-c my way back to a dos prompt.

good luck - disregard if I'm in the wrong field

---

