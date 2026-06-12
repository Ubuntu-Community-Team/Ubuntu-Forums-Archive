---
title: "Change bootloader to new partition"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by BAsecamp.88 on 2006-07-14
I am an XP user slowly moving over to linux and it's great so far -- very challenging in a good way! Prior to Ubuntu I installed Suse from the latest DVD release, 10.1. I let Suse take over and create a boot sector within it's partition. Here are the cliff's notes of what happened next:

1. Unhappy with Suse, attempt uninstall 

2. Since Suse bootloader was mapped to Suse partition, all NTFS partitions are now unrecognized 

3. Use 'David's Ultimate Boot Disk 2.0' to recover data from partitions to network (grr) -- attempt to fix/move MBR and partition table with no luck

4. Reinstall Suse in same partition including boot loader with same settings 

5. Recover all partitions except for one, but luckily had backed up.

6. Install Ubuntu and go through similar hellish scenario as steps 2 and 3. Ubuntu boot loader will not show up and PC still tries to load from Suse bootloader which no longer exists?!

7. Reinstall Suse, point grub to same drive, and learn to edit grub menu to add Ubuntu to the list

Everytime I update Ubuntu to a new kernel, I am forced to edit Suse's grub boot menu by hand. I don't mind having Suse on my drive, but I have some hardware problems with it and would like to either reinstall or remove it. This is not specifically a Ubuntu question, but does anyone know how to move the MBR to another partition? I would like the bootloader to either be handled by Ubuntu or WinXP since they are the permanent installations on my drive. I have access to a lot of tools, I just have not been very successful. Any help is much appreciated.

---

### Post by Herman on 2006-07-14
Hello, BAsecamp.88, has this computer more than one hard disk?
Can you post the output of sudo fdisk -lu please?> sudo fdisk -lu

---

### Post by BAsecamp.88 on 2006-07-19
Here are the results of sudo -lu 

----
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     4096062     2048000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2         4096063   157710104    76807021    7  HPFS/NTFS
/dev/hda3       157710105   312576704    77433300    7  HPFS/NTFS

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63    29398949    14699443+   7  HPFS/NTFS
/dev/hdc2        29398950    31503464     1052257+  82  Linux swap / Solaris
/dev/hdc3        31503465    45078389     6787462+  83  Linux
/dev/hdc4   *    45078390    58621184     6771397+  83  Linux

----

2 hard disks with 7 partitions between them. Hdc3 - Suse, where I am currently booting from. Hdc1 - XP. Hdc4 - Ubuntu, I would prefer to boot from this partition.

---

### Post by Herman on 2006-07-20
Okay, thanks. It seems odd to me that you have a /dev/hda disk (disk 1) and a /dev/hdc (disk 3) but no /dev/hdb (disk 2).  What happened to disk 2 ? I am wondering whether or not these disks are set up in the BIOS the normal way or if there is something special being done here that's different from standard.

 We can try installing Ubuntu's GRUB to MBR again, I don't know why that wouldn't have been done automatically by the Ubunti Install CD. 

I am presuming you have the popular 'Desktop' install CD, and I will tell how to re-install GRUB from that one.
Start the LiveCD, open a terminal, and type the following command,```
sudo grub
``` That command will ask for your password and then give you what is called a 'grub shell', (your prompt will turn into a grub prompt).
After the grub prompt, type,```
find /boot/grub/stage1
```You should get some feedback from that command that will tell you which partitions contian a file called /grub/boot/stage1. 
I'm not sure if SuSe has a grub file by the exact same  name or is different, so I don't know whether you'll get one or two answers. In any case, your Ubuntu partition will probably be called (hd2,3) I think, judging from your fdisk output you posted. You should see that as one of the partitions in the feedback, to confirm this.

If that is correct, type, the following command, or if that is not correct, then type a command similar to the following, but replace (hd2,3) with whatever is the real way to designate your Ubuntu partition. (You can also see that by checking your SuSe grub's menu.lst beforehand).  ```
root (hd2,3)
```You should expect to see a reply something like the following,> Filesystem type is ext2fs, partition type 0x83 Finally, enter the following command, ```
setup (hd0)
```You should see something like the following feedback, > Checking if "/boot/grub/stage1" exists... yes
              Checking if "/boot/grub/stage2" exists... yes
              Checking if "/boot/grub/e2fs_stage1_5" exists... yes
              Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
             succeeded
              Running "install /boot/grub/stage1 d (hd0) (hd2)3+15 p (hd2,3)/boot/grub/stage
             2 /boot/grub/menu.lst"... succeeded
             Done. Then type 'quit' to exit the grub shell. ```
quit
``` That should install Ubuntu's GRUB to the MBR on (hd0), which should be the first hard disk. The BIOS will look at the MBR in your first hard disk, and now, (after performing the steps above), your MBR should point the BIOS to your Ubuntu partition where the GRUB bootloader will take over.
Reboot and remove the 'Desktop CD and see if it has worked.

I hope this will work for you, let me know how you do. If you have any more questions, please ask.
Regards, Herman :D

---

### Post by BAsecamp.88 on 2006-07-20
Thanks for the feedback Herman. I'm going to backup my current MBR configuration and try your advice. Fingers Crossed. 

I believe the reason there is no **hdb** is due to the way my drives are connected. One drive and one cd/dvd on each IDE cable to maximize transfer speeds and reduce collisions. If that's not the reason than I have no clue.

---

