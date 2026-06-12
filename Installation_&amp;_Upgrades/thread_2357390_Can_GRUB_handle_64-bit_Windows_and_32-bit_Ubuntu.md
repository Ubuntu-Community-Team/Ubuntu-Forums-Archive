---
title: "Can GRUB handle 64-bit Windows and 32-bit Ubuntu?"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by Seamless in Northampton on 2017-04-01
So I installed all new hardware except the hard drives, and my 32-bit Ubuntu install survived intact. I then installed Windows 7 64-bit on a new hard drive, and now I am royally confused. I can dual boot via changing the boot order in my BIOS, but I'm curious to know what I've actually done here. Running Boot Repair doesn't work -- it tells me I need 64-bit, yet my Ubuntu is 32. Not sure what that's about, so I left it. When I'm running Ubuntu, Grub customizer won't read the Windows install at all. Can GRUB handle this? Should I just leave well enough alone? 

Long-term, I'll reinstall Ubuntu and upgrade it to 64-bit, but is there a short-term solution other than switching boot order via BIOS?

---

### Post by oldfred on 2017-04-01
Is issue really UEFI or BIOS?
UEFI with Ubuntu needs the 64 bit.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Seamless in Northampton on 2017-04-01
I think it is indeed a UEFI issue. And I'm new to that whole business, so I have a dumb question -- I take it that individual drives may mount differently when the system boots up? As in right now, I'm running Ubuntu with no issues, and it's 32-bit, so clearly this drive didn't mount as UEFI. But the system is reading my Windows drive, which, I take it, has to mount via UEFI? 

This UEFI stuff seems remarkably confusing. Though I take it from that very helpful link you posted that Windows and Ubuntu can't see each other as it stands. And getting a UEFI Ubuntu install is clearly not as easy as it sounds. I'll try not to find it too irritating! :)

---

### Post by Seamless in Northampton on 2017-04-01
Here's the very long Boot Info text. It reads like the trail of old/abandoned installs, needless partitions and broken OSs that it truly is. Eventually, all will reside on the UEFI drive, and the others will be wiped and used for data storage only.

[http://paste2.org/JFjFxBcA](http://paste2.org/JFjFxBcA)

---

### Post by oldfred on 2017-04-01
Your sdd is an UEFI/gpt partitioned drive.
Windows only boots in UEFI mode from gpt.
Windows only boots in BIOS mode from MBR(msdos).
But Ubuntu can boot in BIOS or UEFI from gpt, but best to also have as UEFI if Windows is UEFI.

UEFI & BIOS are not compatible. Or once you start booting in one mode you cannot switch. Or grub can only boot other installs in same boot mode.

If installing Ubuntu in UEFI mode, it only installs grub's .efi boot files in the ESP - efi system partition on drive seen as sda. Your ESP is currently on sdd.
You either have to reorder drives or convert sda to gpt and add the ESP, FAT32 200 to 500MB with boot flag.

I prefer to only use gpt. I only had BIOS back in 2011, but installed Ubuntu in BIOS mode on gpt drive.
Now all new or reformatted drives are gpt and my first two partitions are always an ESP and bios_grub. Not sure I will ever use bios_grub any more with my new systems, but it is only 1MB and then gives flexibility to configure either UEFI or BIOS boot on every drive.

You can convert MBR to gpt. I have never done it. It has some risk, so be sure to have good backups.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by Seamless in Northampton on 2017-04-01
Thanks! Your explanation makes good sense. I appreciate the clarity. I will eventually back up everything and convert to gpt. But I have some pressing deadline tasks, so it's all about switching via BIOS boot order until then.

---

