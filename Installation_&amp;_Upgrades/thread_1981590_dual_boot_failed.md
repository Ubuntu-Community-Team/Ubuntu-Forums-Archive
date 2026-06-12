---
title: "dual boot failed"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by yumyam on 2012-05-17
hi i have recetly got dell vostro 3550 with has ubuntu 10.10 install in  it . as i want to get windows 7 to be installed on the system , i have shrinked the partition and manged to install windows 7 on that . As expected now i am not able to boot to ubuntu after windows installation . i have read about boot-repair , prepared a boot repair flash drive and tried to repair , unfortunaly i have failed to recover and later i have followed some steps provided in the 
[http://askubuntu.com/questions/6317/how-can-i-install-windows-7-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-7-after-ive-installed-ubuntu)
sudo mount /dev/DEVICENAME_FROM_STEP_ONE /mnt
sudo rm -rf /boot    # Careful here, make sure YOU ARE USING THE LIVE CD. I tried it, it works.
sudo ln -s /mnt/boot /boot
sudo apt-get update && sudo apt-get install grub-pc
sudo grub-setup /dev/sda     # NOTE THAT THERE IS NO DIGIT
sudo umount /boot



but i got error while executing the above steps .

the error that i can see is 
Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE

boot repair logs
--------------------
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1        80,262        80,262  de Dell Utility
/dev/sda2              80,263     3,084,168     3,003,906   c W95 FAT32 (LBA)
/dev/sda3           3,084,288   119,926,783   116,842,496  83 Linux
/dev/sda4    *    119,926,784   324,726,783   204,800,000   7 NTFS / exFAT / HPFS



Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2               5         192     1501953    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3             192        7466    58421248   83  Linux
/dev/sda4   *        7466       20214   102400000    7  HPFS/NTFS

Disk /dev/sdb: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d841b9f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3882     3913024+   b  W95 FAT32



chroot: failed to run command `type': No such file or directory
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
INSTALLOUTPUT: INSTALLEXIT:1
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda1: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /live/image: No such file or directory
ls: cannot access /live/image: No such file or directory
ls: cannot access /live/image: No such file or directory
ls: cannot access /live/image: No such file or directory
ls: cannot access /live/image: No such file or directory
ls: cannot access /live/image: No such file or directory
ls: cannot access /live/image: No such file or directory
Found Windows 7 (loader) on /dev/sda4
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg
Unhide GRUB boot menu in sda3/boot/grub/grub.cfg
Boot successfully repaired.

You can now reboot your computer.

---

### Post by wilee-nilee on 2012-05-17
Did you run the bootscript from the boot repair, if so post it, if not here it is. Download it, extract it to the desktop, and run the command and post the whole results.txt that is generated. When you open the reply to paste the text click on the # this generates code tags paste between them.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by yumyam on 2012-05-17
[http://paste.ubuntu.com/991796/](http://paste.ubuntu.com/991796/)

i have used recomended repair option in boot repair

---

### Post by wilee-nilee on 2012-05-17
The sda2 partition shows as a ext4 and a fat32 in different parts of the script, the sda2 is rather small, so we will get some comment on why this maybe possibly. That same partition shows the whole grub file set needed for booting same as the sda3 the actual Ubuntu install.

I could just give you the commands to chroot to the HD and reload grub to the mbr, and it may work, but I rather get some comment from other users who work on these same sort of issues.

It may be that the sda2 can just be made into a swap as you don't have one and then just reload the mbr.

The sda1 looks like dell firmware probably not needed anymore as well.

---

### Post by wilee-nilee on 2012-05-17
So just to be safe here since you did run commands after the script was run from the boot-repair lets run it again and post it, these scripts may basically show the same, it is just best to know where it is now. You can run it with my earlier posts instructions if you like.

---

### Post by yumyam on 2012-05-17
yes it shows the same error

---

### Post by wilee-nilee on 2012-05-17
> **yumyam said:**
> yes it shows the same error

I think you misunderstand we would want to see the bootscript after any commands are run look at my first post to run it again.

---

### Post by yumyam on 2012-05-17
[http://paste.ubuntu.com/992944/](http://paste.ubuntu.com/992944/)  -- new status

---

### Post by oldfred on 2012-05-18
Was this a Dell with LInux preinstalled? It looks like you have a FAT partition sda2 that is some sort of install or repair partition.

But your Linux install is in sda3 and it looks like you installed Windows in sda4 and it put its boot loader into the MBR of the drive.

You have grub2 installed to the Partitions of sda2 & sda3. But grub2 is less reliable in the partition and works better from the MBR. 

Only if running Windows software with DRM which might interfere with grub in the MBR, you should install grub2's boot loader to the MBR. 

Since it is finding two installs, you may have to tell boot repair to install grub from sda3 into the MBR.

From a Ubuntu LiveCD you can manually do it this way:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda3 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda3 if not correct:
sudo fdisk -l
#confirm that linux is sda3
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by yumyam on 2012-05-18
I have tried the the above approach earlier  . but no luck i have got the same error as i mentoined in the boot summary profile . I thank you for ur time any guess what would be cause

---

### Post by oldfred on 2012-05-18
But you only have grub2's boot loader installed to PBR - partition boot sectors not the MBR or master boot record. Computers can only boot from MBR.

Was your system configured to use a Windows boot loader in the MBR, and have grub2's boot loader in the PBR to get it to boot? If so you can move boot flag to sda3 and it should boot grub2 menu. 

But if Windows is not booting that will not resolve that issue as Windows has to work before grub can chain load to it.

Grub in the PBR is less reliable and it is better to have it in the MBR.

Your grub install command has to use sda - the drive , not sda2 or sda3 as those are partitions on drive sda.

---

### Post by yumyam on 2012-05-22
can you please provide me the command to execute . i am complete new to this linux environment

---

