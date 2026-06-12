---
title: "Blank screen on install - nomodeset doesn't fix"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by justintime2002 on 2012-06-04
Hi all,

I'm trying to install Ubuntu 12.04 64-bit to dual-boot on a new desktop machine (using a Crucial SSD & Nvidia graphics card).  I've tried booting from both a DVD and USB drive, but I get a black screen immediately after selecting install.  I've tried using the 'nomodeset' option but this just gives me a blank terminal (a blinking white cursor on black background) instead of a completely blank screen.  I'm not sure what else to try, any advice?

Thanks!

---

### Post by btwThieves on 2012-06-04
In addition to the nomodeset kernel option, try 
```
xforcevesa
```
as well. To do this, hit ESC after selecting "nomodeset" from the kernel options. This will allow you to edit the kernel options directly. Type "xforcevesa" before the "--" and post back with the result.

---

### Post by justintime2002 on 2012-06-04
I tried adding "xforcevesa" to the kernel options and nothing changed.  The computer still freezes on a blank terminal screen.

---

### Post by oldfred on 2012-06-05
If nVidia it needs the nomodeset, but some new or very old systems need other boot parameters. Are you removing quiet & splash as sometimes it will give clues as to what is wrong.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

What motherboard or system is it.

---

### Post by justintime2002 on 2012-06-05
I've tried acpi=off and nomodeset together, but this didn't change anything.  I'll turn off quiet mode and report back.

I'm using an Asrock Z77 motherboard - it's a custom build.

---

### Post by oldfred on 2012-06-05
Ok with the new Z77 are you booting in UEFI or BIOS mode?

AsRock calls BIOS mode AHCI.
"Launch EFI Shell from Filesystem Device" in the Exit tab of Asrock motherboard

---

### Post by justintime2002 on 2012-06-05
I'm booting in AHCI mode.  I tried removing the quiet splash option and everything appears to be normal until I get something along the lines of:

```
[   36.xxxxxx] ata8.00: failed command: IDENTIFY PACKET DEVICE
[   36.xxxxxx] ata8.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   36.xxxxxx]            res 40/00:00:00:00:00/00:00:00:00:00 Emask 0x56 (ATA bus error)
[   36.xxxxxx] ata8.00: status: { DRDY }
[   36.xxxxxx] ata8: hard resetting link
```

The system freezes up after these lines.

Edit: I tried using UEFI mode and got the same result after I edited the boot options.  I also get the same error whether I boot from a DVD or USB stick.

---

### Post by oldfred on 2012-06-05
What is ata8? Do you have some unique device plugged into that SATA port? Blueray or something it cannot identify?

Some others with Ivy Bridge:
[http://ubuntuforums.org/showthread.php?p=11995888#post11995888](http://ubuntuforums.org/showthread.php?p=11995888#post11995888)
[http://openbenchmarking.org/s/Z77%20Extreme4](http://openbenchmarking.org/s/Z77%20Extreme4)

---

### Post by justintime2002 on 2012-06-05
I'm not sure what ata8 is.  The only things I have plugged into SATA ports are a Crucial M4 SSD, a 500GB Western Digital hard drive, and an ASUS DVD burner.

---

### Post by justintime2002 on 2012-06-06
I figured out the problem.  I'm using an Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).  I had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away.  Now I have Ubuntu 12.04 successfully installed.

Thanks for your assistance!

---

### Post by jameslong06 on 2012-11-21
Had a similar problem with the ASUS Maximus V Gene. At first I thought it was a graphics issue with the on board Inte HD 4000, however after using "no splash" as a boot option I saw that I was getting a ```
hard resetting link
``` notice in the output.

I too had made the mistake of plugging into a shared port, after popping out a few things from the SATA bus things fired right up without any issue whatsoever.

---

### Post by stefanoradice on 2013-06-28
Hello I am experiencing the same problem. Should I move the DVD only or the HD as well?

Tks

---

### Post by oldfred on 2013-06-28
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

---

