---
title: "Partition &amp; Install Problems"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by kainino on 2007-04-26
I posted this a few months ago and I never got the problem fixed. Just to make it clear, I am having TWO problems, #1 which I posted somewhere else (I think):
#1: When I install Ubuntu, GRUB will not work. It always has an error, different depending on whether I use Smart Boot Manager (SBM) to boot the partition. I had to install OS Loader 2000 on top of it, or my computer would not work.
#2: When I make ANY new partition, Windows XP will not boot. I always get the below error. It DOES work when the computer was already in hibernate, and I use SBM to boot the partition.

Also, I hesitate to resize the WinXP partition because I am having all of these other strange problems. This is my main computer and I cannot afford to break it. I do have one other I can fool around with, but it is very old and can barely run text based Debian. (And its CD drive has ceased to function.)

> 
I have an extra unpartitioned 2.7GB on my hard disk and I want to use it, either for Ubuntu or just for storage. When I partition the space with either the installer or GPartEd, in NTFS, ext3, or linux-swap (under an Edgy Desktop CD), Windows XP seems to boot normally for a few seconds, then says (BSoD):

```

A problem has been detected and Windows has been shut down to prevent damage to your computer.
UNMOUNTABLE_BOOT_VOLUME
(blah blah blah...)
Technical information:
*** STOP: 0x000000ED (0x87282E30, 0xC000014F, 0x00000000, 0x00000000)

```

When I get rid of the partition, it works again. Could this have something to do with the BOOT.INI settings? There seems to be a line that says where Windows is installed. (also, if I install Ubuntu, will I have to manually add it to BOOT.INI?) It also boots normally from hibernate, so it must be something later on in the startup.

```

BOOT.INI:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```


---

### Post by Big Ed on 2007-04-26
I don't have any suggestions for your first problem, but the second one sounds like your partitions are being renumbered.  Are you making the new partition ahead of the windows one?  If so, can you edit the bootloader you are using to point the windows boot to the correct partition?

HTH,
Ed

---

### Post by kainino on 2007-04-26
> **Big Ed said:**
> ... the second one sounds like your partitions are being renumbered.

IIRC, the Ubuntu installer automatically created the following partition table. I know it didn't renumber anything.
hda1 - NTFS (my old WinXP partition) ~34.5GB
hda2 - ext3 ~2.3GB
hda5 - extended
^hda3 - linux-swap ~400MB

UPDATE: I just used the Super Grub Disk to uninstall Grub, and the nag screen caused by OS Loader every time I started up is now gone. I'm thinking of installing Ubuntu, then fixing Grub using the SGD, but that still won't fix the problem of Windows not starting.

---

### Post by Big Ed on 2007-04-27
> **kainino said:**
> IIRC, the Ubuntu installer automatically created the following partition table. I know it didn't renumber anything.
hda1 - NTFS (my old WinXP partition) ~34.5GB
hda2 - ext3 ~2.3GB
hda5 - extended
^hda3 - linux-swap ~400MB

UPDATE: I just used the Super Grub Disk to uninstall Grub, and the nag screen caused by OS Loader every time I started up is now gone. I'm thinking of installing Ubuntu, then fixing Grub using the SGD, but that still won't fix the problem of Windows not starting.

If the partitions are not being renumbered, then I'm not sure what is causing windows to fail.

Can you put your partition table here?  Both working and non-working versions?  Include the cylinder info also.  Might give an indication as to what is going wrong.

Ed

---

