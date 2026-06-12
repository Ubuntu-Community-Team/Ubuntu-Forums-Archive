---
title: "I need to reinstall Grub 2, but how?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by LGN on 2010-05-16
Today I reinstalled my Windows partition of my PC. If you need to know, my config is like this
-Windows (formally XP MCE, now Vista Ultimate) on Partition 1
-Windows Recovery on Partition 2
Logical Partition
   -Ubuntu 10.04 Lucid on Partition 3
   -Ubuntu Swap

I have to reinstall GRUB because Windows wrote over the MBR.

I have a 10.04 install disc, but I do not know how to reinstall Grub2

how do I reinstall Grub2?

---

### Post by drs305 on 2010-05-16
This post should help you restore your Grub installation:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

Should work for Lucid as well for those reading this with a 10.04 install.

---

### Post by LGN on 2010-05-16
Where exactly does it say anything about GRUB2 in there

---

### Post by drs305 on 2010-05-16
D'oh, sorry. Right title but apparently the answer to another post was still in memory. I've corrected the original.

---

### Post by pritam_par on 2011-07-18
This is quite long but worked for me

1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
2. Open a terminal - Applications, Accessories, Terminal.
3. Determine your normal system partition - (the switch is a lowercase "L")

      sudo fdisk -l
          * If you aren't sure, run

            df -Th. Look for the correct disk size and ext3 or ext4 format. 
4. Mount your normal system partition:
          * Substitute the correct partition: sda1, sdb5, etc. 

   sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
5. Only if you have a separate boot partition:
          * sdYY is the /boot partition designation (for example sdb3)
          *sudo mount /dev/sdYY /mnt/boot 
6. Mount the critical virtual filesystems:

      sudo mount --bind /dev  /mnt/dev
      sudo mount --bind /proc /mnt/proc
      sudo mount --bind /sys  /mnt/sys
7. To ensure that only the grub utilities from the LiveCD get executed, mount /usr

      sudo mount --bind /usr/ /mnt/usr
8. Chroot into your normal system device:

      sudo chroot /mnt
9. If there is no /boot/grub/grub.cfg or it's not correct, create one using

      update-grub
10. Reinstall GRUB 2:
          *Substitute the correct device - sda, sdb, etc. Do not specify a partition number. 

      grub-install /dev/sdX
11.Verify the install (use the correct device, for example sda. Do not specify a partition): sudo grub-install --recheck /dev/sdX

---

### Post by Shobuz99 on 2013-01-23
Deleted post. Started new thread


Shobuz99

---

