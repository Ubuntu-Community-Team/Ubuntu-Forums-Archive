---
title: "Installation crash on Acer Aspire 5735: dev/sdb no medium found, screen flickers ecc."
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by Alberto_A. on 2015-09-30
Dear Forum,

this is my first time here and I come with a problem which is driving me crazy: I am trying to install Ubuntu Desktop 15.04 on an Acer Aspire 5735 but installation process crashes and screen flickers all the time.
I thought I was installing the wrong distribution (32 bit instead of 64 bit) but that is not the case; the problem appears either I am trying to install the 32 bit version or the 64 bit version.
To sum up what happens, please look at the screen captures I took during installation attempt (attached to this message): from 01 to 05 as the installation attempt continues.
Can anybody help me with this please?

Thank you very much.

Alberto

---

### Post by dino99 on 2015-09-30
which iso has been installed ? [http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/)
which cpu is inside ?

---

### Post by Alberto_A. on 2015-09-30
Some more pictures (of the BIOS configuration)

---

### Post by Alberto_A. on 2015-09-30
Hi, the iso I have downloaded is the 15.04 (both 32bit and 64bit) that you can find here: [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)
The CPU is a Intel Core Duo Processor T5800 (I suppose it is a 32bit cpu since there was installed Windows Vista 32 bit on it).

Alberto

---

### Post by oldfred on 2015-09-30
I believe that is a core2 duo and is 64 bit. Some older core duo not core2 were 32 bit.

Errors seem to be related to sdb? Are you using DVD or flash drive to install. 
Is flash drive sdb? It may just be your flash drive has issues.

Sometimes certain brands of flash drives, certain ports on system, or different installers give issues. If you have downloaded several times it may be one of those issues.

Have you added a boot parameter? Even some Intel chips need one. And some systems need additional parameters.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
      
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by Alberto_A. on 2015-09-30
Hi oldfred,  thanks for the reply. To answer your questions:  1. This laptop has a 450GB hard drive and it should be a SATA drive 2. It has Windows Vista installed 3. I am trying to install Ubuntu from the DVD drive 4. I was not passing any parameter at boot since I thought that the installation process would proceed smoothly  The problem seems to be dev/sdb which is not found by the installation program; now, while installing Slackware on the same machine, I noticed that FDISK was recognizing dev/sda only. Why Ubuntu is so stubborn to look for dev/sdb? I cannot understand. Besides, the screen starts to flicker and cannot stop.  I have tried passing some parameters pressing e - NOMODESET and/or NOALPCI - but nothing works; I have also tried different combinations: NOTHING WORKS.  Is there a way I can pass more parameters before starting the actual installation process?  Regards,  Alberto

---

### Post by oldfred on 2015-09-30
Some systems promote flash drive to sda.
I had similar issue where I installed second drive to third or fourth SATA port. And with several drives and booting from sdd, a flash drive would be sde. But on reboot flash was sdb and all other drives were one letter up.

Is your hard drive in the first SATA port on motherboard? Probably labeled SATA0.

---

