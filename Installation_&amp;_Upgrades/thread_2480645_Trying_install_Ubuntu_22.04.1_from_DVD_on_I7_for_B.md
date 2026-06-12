---
title: "Trying install Ubuntu 22.04.1 from DVD on I7 for BIOS only (no UEFI) - warning EFI?"
date: 2022-11-04
forum: Installation &amp; Upgrades
---

### Post by wb0gaz on 2022-11-04
I'm trying install Ubuntu 22.04.1 from live DVD on an Intel I7 machine that's only be used for BIOS (not UEFI).

During the install process (I've tried both DVD and flash drive created by dd  from ISO to the flash device), I get a warning about absence of EFI partition(s). There are only four primary partitions on the target drive (one of the four is to be Ubuntu.) I've previously installed 18.04 on this machine/partition without this sort of message, and as far as I can tell, have not made any  major configuration changes.

Is there something I'm missing to avoid UEFI altogether  for this install?

Thanks,

Dave

---

### Post by oldfred on 2022-11-04
The installer now seems to always install an ESP partition whether BIOS or UEFI.
Since Microsoft required UEFI with gpt partitioning with release in 2012, systems are now UEFI. 

I would still use gpt partitioning with BIOS, if you really want BIOS boot.
I used gpt starting in 2010 with a Linux only drive. Windows in BIOS mode had to be on a MBR(msdos) drive.
The only time you still need MBR, is if you have to install Windows in old BIOS mode.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

I always partitioned  drives in advance & immediately converted to gpt as gparted defaults to MBR.
If BIOS booting you need a tiny 1 or 2MB unformatted partition with bios_grub flag if using gpt.
For years I added both ESP & bios_grub to every drive & larger flash drives as then it would be easy to convert from BIOS to UEFI or vice-versa.
Now been on UEFI/gpt for about 8 years, so new drives now do not have the bios_grub partition.

---

### Post by &amp;KyT$0P# on 2022-11-04
You're not missing anything, that warning is there for UEFI systems booted in legacy mode, where the installer wants the installed Ubuntu to be able to boot as either EFI or legacy.  If your system is BIOS-only, you can just click Continue on that warning and ignore it.

More details in [this post]("https://ubuntuforums.org/showthread.php?t=2478340&p=14109550#post14109550").

---

### Post by guiverc on 2022-11-05
You can install 22.04 using the `ubiquity` installer **without** a ESP (uEFI System Partition), but the default options do install one. I tested install on BIOS only hardware where it was possible to install with only a single partition (not two, ie. / only) and it installed & booted correctly as expected. The *flavor**s* using `calamares` as the installer do this by default where BIOS (not uEFI) is used; ie. Lubuntu & Ubuntu Studio, and I'd seen reports on a QA site that it wasn't possible (*possibly Ubuntu MATE but I forget*) so I re-tested to ensure it was possible without ESP & yep it was.

The message you no doubt see is WARNING only, not an error, and can be ignored as ESP isn't used by *legacy* or BIOS only hardware.

CD/DVD or *optical *media can be problematic, so I'd avoid that (and use USB *flash* drive), but yeah that's possible too just not recommended.  Optical media is to be avoided on releases past 20.04 for installs.

If you want to not see the warning, you write the ISO to installation media in a specific way; but in my opinion its not worth it, as the media can only be then used to install on non-EFI boxes, and I did not test this, as it was a comment on a bug report on the message I believe you saw & I could be missing something here as I felt the message wasn't an issue as it said it MAY NOT or provided sufficient condition for me.

---

