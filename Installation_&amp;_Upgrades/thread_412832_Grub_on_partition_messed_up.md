---
title: "Grub on partition messed up"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by allrite on 2007-04-18
Hi,

I have a dual boot laptop with no CD drive. Everything was running normal till I decided to play around with my Ubuntu Edgy partition from Windows (actually, increased its size) and now grub won't show up. Thankfully, I didnt install grub on MBR (installed grub on ubuntu's root partition and edited boot.ini in windows) so I can still boot into windows. I was also able to hack my way to boot into ubuntu using Grub for DOS. I can still boot in ubuntu using Grub for DOS whenever I want, but I would rather fix the problem than use this hack forever. So is there a solution? I have tried three things till now (ubuntu root is /dev/sda3):

1) Updated my bootsect.lnx in my windows C: drive by the 'dd if=... of=.. " method

2) Tried updating grub by doing 

> 
grub>root (hd0,2)

grub>find /boot/grub/stage1

grub>setup (hd0,2)

3) Also tried reinstalling Grub by grub-install

> sudo grub-install /dev/sda3


Am I missing something here? None of these helped. If I try to boot into Ubuntu the usual way (without Grub for DOS), I just get a blank black screen with only one word "GRUB" :(

---

### Post by ajgreeny on 2007-04-18
I note you did not show what the output of your  			 				
grub>root (hd0,2)

grub>find /boot/grub/stage1

grub>setup (hd0,2) were.

Incidentally, normally you would do the second of your queries first as the grub>root command depend on the output of the find query.  Also at the end you need to use the command  "quit" at the grub prompt.  Are you sure you put root in the right place and that you have the partitions correct?  Using the ubuntu install that you can boot into, open a terminal and try:-
sudo fdisk -l
to see if your assumptions are right.

Make sure that your /boot/grub/menu.lst file is where you think it is and try from there to reinstall grub as you did before but perhaps using the right partitions this time.

---

### Post by allrite on 2007-04-18
Hi,

Thanks for the reply. I will post the outputs here.
> 
~$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3528    26670743+   7  HPFS/NTFS
/dev/sda2            7135        7751     4664520   12  Compaq diagnostics
/dev/sda3            6237        7134     6782265   83  Linux
/dev/sda4            3529        6237    20474842+   5  Extended
/dev/sda5            3529        6017    18812083+   b  W95 FAT32
/dev/sda6            6017        6237     1662696   82  Linux swap / Solaris

Partition table entries are not in disk order

So I guess root is in /dev/sda3. Output of grub commands:
> 
~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> quit

So something "failed" during the setup command. It says its not fatal. Is that the problem?

I did 'dd' now and booting into windows to replace the old bootsect.lnx file

> ~$ sudo dd if=/dev/sda3 of=bootset.lnx bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 6.6e-05 seconds, 7.8 MB/s

Lets see what happens....

---

### Post by allrite on 2007-04-18
And it works :)

Thanks for the help. I guess the 'trick' was to install grub first and then copy the updated bootsector to C: drive :p 

Pretty noob of me to not think about that! Sorry for bother you :)

---

