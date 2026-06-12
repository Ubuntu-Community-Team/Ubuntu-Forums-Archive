---
title: "Dual boot Windows 7 and Ubuntu 9.10 getting &quot;Grub Loading&quot; and immediate reboot"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by dot.man on 2009-11-24
I am having an issue with dual-booting Windows 7 and Ubuntu 9.10 on an MSi A6000 laptop. My system flashes "Grub loading" on the screen for about 1/2 of a second and reboots, repeating this over and over. My system started out with Windows 7, freshly restored and defragmented.  I installed Ubuntu 9.10 Desktop using the LiveCD (32 bit version) and used the Ubuntu installer to repartition sda3 in order to get space for Ubuntu to reside.  I chose EXT3 filesystem type instead of the default of EXT4 for the new partitions.  I have not done any manual editing of the Grub files nor is it customized. I had no issues logging into Ubuntu before now but I did experience the quick "blue screen of death" the two times when selecting Windows 7 and then the "failure to launch windows" screen, but I chose "Start normally" instead of repair both times. The last action performed before seeing this issue was choosing "Restart" from the Windows shutdown menu during the shutdown to get it to reboot so I could log into Ubuntu. After this is when I started getting the "Grub loading" and reboots.  Below is the output from "fdisk -l":

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad7aaef8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       16349   120833024    7  HPFS/NTFS
/dev/sda3           16349       32835   132421875    7  HPFS/NTFS
/dev/sda4           32836       38913    48821535    5  Extended
/dev/sda5           32836       33807     7807558+  82  Linux swap / Solaris
/dev/sda6           33808       34780     7815591   83  Linux
/dev/sda7           34781       38913    33198291   83  Linux

For clarification:

sda1 > restore partition from MSi for Windows 7
sda2 > Windows Vista partition C:
sda3 > Windows 7 partition D:
sda5 > Ubuntu swap partition
sda6 > Ubuntu "/" partition (root partition)
sda7 > Ubuntu "/home" partition

SDA1, 2 & 3 all existed prior to me touching the system.  Again, the only change made to these three partitions was on partition SDA3 for space to install Ubuntu.  I am currently booted using Ubuntu 9.04 on a bootable USB stick, so that is how I am able to get this info.  Does someone recognize this?  If so, do you have any suggestions as to how to fix?

Thank you for any input you may have.

---

### Post by darkod on 2009-11-24
Everything looks fine. Try reinstalling grub2 with item number 12 from here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If it does help, I would recommend booting Win7 few times, and if it asks about any repairs let it do it. Depending how long you have been using windows you know how picky it is about its repair stuff.

---

### Post by dot.man on 2009-11-24
Thank you darkod.  My issue is now resolved.  I looked over your document and ran the commands and then ran one additional command based on an error I was seeing:

grub-setup -d /media/boot/grub -m /media/boot/grub/device.map /dev/sda

It is referenced in post #3, about 3/4 of the way down the page at [http://ubuntuforums.org/showthread.php?t=1332783](http://ubuntuforums.org/showthread.php?t=1332783)

I am not sure if just doing the reinstall of grub2 without this extra command would have worked or not, but I figured I would be on the safe side and run it.

---

