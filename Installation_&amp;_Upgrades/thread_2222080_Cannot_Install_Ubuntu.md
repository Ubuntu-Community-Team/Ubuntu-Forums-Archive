---
title: "Cannot Install Ubuntu"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by david205 on 2014-05-05
I'm a beginner with Linux in general, and only know the common sense portion of computers in general, maybe a bit more. I'm smart and learn fast though and im trying to install Ubuntu on my Lenovo B575 Laptop. It has no operating system install on it currently. I've already burned the ISO, but couldn't figure out how to check the MD5, i tried but eventually gave up and moved on. (probably not the smartest idea, i know.) But after i install Ubuntu, using any of the options, and even partioning the HDD myself, It says it was successful, But never will boot Ubuntu. All i get are Media test failure errors...?  I've tried everything a beginner like i am can google, but I've reached a dead end and need to ask for help. I'm willing to work as closely as you need, and give any information you want of the laptop. It previously ran Windows 7.

Cpu: AMD E-350 Processor
RAM: 4GB
1MB L2 Cache
System BIOS shadowed
Video BIOS shadowed
BIOS Version: 52CN11WW

Thanks! :)

EDIT: When i run the install disk it says "Could not open "\EFI\BOOT\fallback.efi": 14"

EDIT2: when i check disk for defects i get the result:
error: file `/boot/grub/x86_64-efi/zfs.mod' not found.
error: file `/boot/grub/x86_64-efi/tar.mod' not found.
error: file `/boot/grub/x86_64-efi/sfs.mod' not found.
error: file `/boot/grub/x86_64-efi/nilfs2.mod' not found.
error: file `/boot/grub/x86_64-efi/minix.mod' not found.
error: file `/boot/grub/x86_64-efi/afs.mod' not found.
error: file `/boot/grub/x86_64-efi/affs.mod' not found.
error: unknown filesystem.
unaligned pointer 0xb00e6c88
aborted.

---

### Post by Bucky Ball on 2014-05-05
*Thread moved to **Installation & Upgrades**.*

You may have more luck here and you've made it clear you're a beginner so helpers will be gentle with you. ;)

As there is no other operating system on the drive, try installing with EFI off (in legacy). You can change that in the bios. Change it to legacy and see if it makes a difference.

Alternatively, you can try installing in EFI as it sounds like you are currently doing, choose 'Something Else' at the partitioning section of the install (manual partitioning) and create a small FAT32 partition, say between 100-300Mb. Yes, megabytes, not gigabytes. DON'T give it a mountpoint, a label, or do anything else. Just create the partition and Ubuntu should 'automagically' see that and use it as your EFI boot partition and install accordingly. 

The problem you're getting seems to be that you are lacking this small EFI boot partition. EFI works differently to the regular old school legacy install (where everything boots from the MBR - master boot record - at the beginning of the drive). EFI needs this small partition and the bootloaders of whatever OSs you install go there. That small EFI partition can go anywhere. 

Welcome to the swim, hope that helps, and good luck. ;)

---

### Post by david205 on 2014-05-05
When i opened the something else with my current installation i already had a fat 32 installed with 1GB of memory in size, and 33 MB used.

---

### Post by Bucky Ball on 2014-05-05
Could you please boot from the install cd, 'Try Ubuntu', and when at the desktop, open a terminal and post the output of these two commands:
```

sudo blkid
sudo df
```

Thanks. You may also like to attach a screenshot of Gparted (Adv. Reply and use the paperclip icon to attach the screenshot).

Interesting. I am presuming the FAT32 partition you mention is the EFI partition that was used by Win7. You didn't create that? Did Ubuntu create that automagically during install? Did you install Win7 yourself or it was already on the machine when you bought it?

If you want to forget about EFI, go the legacy option, as suggested. If you want to dual boot with Win later, Win7 will install fine in legacy mode.

---

### Post by david205 on 2014-05-05
this is what came up
[ATTACH=CONFIG]252873[/ATTACH]

Honestly, couldn't figure out how to boot in legacy mode... But i have no intentions of running any other OS on this machine. I'm assuming that Ubuntu Automagically installed the efi partition.

---

### Post by david205 on 2014-05-05
strange, i did the same thing again feeling strange that the blkid did not yield and results the first time, and got something entirely different...?
[ATTACH=CONFIG]252874[/ATTACH]

---

### Post by david205 on 2014-05-05
Tried wiping the hard drive and re installing with the basic installer (again) didn't work (again).

---

### Post by Bucky Ball on 2014-05-06
Have no ideas at the moment and a bit busy with other things, but when you are running from the liveCD, please take screenshots using the screenshooter and attach to a post using the paperclip icon in 'Adv. Reply' rather than inserting pics in the body of your post, as I have already requested you to do. Thanks. ;)

---

