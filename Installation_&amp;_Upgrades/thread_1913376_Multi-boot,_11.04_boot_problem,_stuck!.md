---
title: "Multi-boot, 11.04 boot problem, stuck!"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by dichotomy on 2012-01-22
Greetings,

I've been trying to set up a functional multi-boot environment with Ubuntu 11.04 for some time now, without much success. I've set up dual-boot environments with it no problem in the past, but this one baffles me. I apologize for the length of this post...but here goes....

Here's what I'm trying to do, and I may be going about it the wrong way. First, my hardware:

-------------------------
Intel i7-860
8GB RAM

1x 500GB HDD (1 partition, contains Windows 7 x64, Windows bootmgr)

1x 500GB HDD (1 partition, contains another Win 7 x64 installation)

1x 320GB HDD (2 partitions, 1st is storage, 2nd is EXT4-formatted installation of Ubuntu 11.04, contains GRUB2 bootloader, I believe)
-------------------------

I'm using the Windows bootloader. I can reach both of the Windows installations through the Windows bootloader, but no matter what I try, I cannot reach the Ubuntu installation.

What I'm basically trying to do is chain-load GRUB through the Windows bootloader. I know it's possible to do, because all my other dual-boot environments are set up in this fashion and they function perfectly. However, the difference is that in this problematic situation, the Ubuntu installation is not on the same drive as the Windows installation, and additionally not on the same drive as the Windows bootloader. I've actually never had success making a functional dual/multi-boot environment with both Windows and Ubuntu that spans multiple drives.

Here's what I've tried already: 

1) using EasyBCD to add an entry pointing to the Ubuntu installation, with every conceivable combination of options, with no success (Windows bootloader can't find the file specified),

2) successfully chrooting from a live USB to my Ubuntu installation, then using this dd command : ```
dd if=/dev/hda2 of=/mnt/floppy/linux.bin bs=512 count=1
``` to take a copy of the Linux boot sector that I've installed. This copy is placed on the 1st Windows drive that contains the Windows bootloader, and I used the Windows command-line bcdedit to manually add an entry pointing to the linux.bin file produced above. No luck, just a blinking cursor and no activity upon selecting the Ubuntu option in the Windows bootloader,

and 3) using GRUB4DOS's grldr.mbr and a custom menu.lst instead of the linux.bin file. This one confuses me a bit, and I may be screwing it all up... I believe GRUB2 is installed on the Ubuntu partition. From what I understand, GRUB2 does away with menu.lst and uses grub.cfg instead. What happens when I select the Ubuntu option in the Windows bootloader in this situation is this: it seems that grldr.mbr is loaded, and it enumerates my hard drives and produces a list of errors, saying grldr cannot be found on all drives, and prompts me to restart.

I'm not totally averse to using GRUB/GRUB2 as my primary bootloader, and loading Windows from it. I'd rather not change my bootloader if at all possible; but if it won't be too much trouble, I'll consider it. Again, sorry for the long post, but I wanted to explain everything correctly and also show that I'm proactively trying to make this work, and not asking for someone else to just 'do it for me.' I feel I've run out of options, and would really appreciate some help from someone more knowledgeable. Thank you in advance :)

---

### Post by darkod on 2012-01-22
If you are asking me, chainloading grub2 is more problems than benefits. Plus, it doesn't fit totally on the PBR as the older grub1 did, thus making possibilities to break during an update, etc.

Unless you have a really, really good reason, I suggest you start looking into using grub2 as your main bootloader.

With multiple disks, you can leave your windows bootloader on your first disk (hopefully that would be /dev/sda) and simply install grub2 to the MBR of the 320GB disk. You can always boot your windows bootloader if you select to boot from the first 500GB disk.

If you know which is your root partition on the 320GB disk, lets call it /dev/sdc5 for example, you install grub2 to the MBR easily from live mode:
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc

That's it.

If you are not sure on which disk and partition it is (it might not be sdc as in my example), post the output of
sudo fdisk -l (small L)

and we'll figure it out.

Of course, after you install grub2 to the 320GB disk it will show up only if you make the 320GB first option in BIOS.

---

### Post by ajgreeny on 2012-01-22
> **darkod said:**
> If you are asking me, chainloading grub2 is more problems than benefits. Plus, it doesn't fit totally on the PBR as the older grub1 did, thus making possibilities to break during an update, etc.

Unless you have a really, really good reason, I suggest you start looking into using grub2 as your main bootloader.

With multiple disks, you can leave your windows bootloader on your first disk (hopefully that would be /dev/sda) and simply install grub2 to the MBR of the 320GB disk. You can always boot your windows bootloader if you select to boot from the first 500GB disk.

If you know which is your root partition on the 320GB disk, lets call it /dev/sdc5 for example, you install grub2 to the MBR easily from live mode:
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc

That's it.

If you are not sure on which disk and partition it is (it might not be sdc as in my example), post the output of
sudo fdisk -l (small L)

and we'll figure it out.

Of course, after you install grub2 to the 320GB disk it will show up only if you make the 320GB first option in BIOS.
+1

Much the best answer for a multiboot system with more than one HDD.  It leaves your Win 7 bootloader files untouched but grub will find everything if you use that disk as the first boot device.

---

