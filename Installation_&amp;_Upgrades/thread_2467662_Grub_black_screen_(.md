---
title: "Grub black screen :("
date: 2021-10-03
forum: Installation &amp; Upgrades
---

### Post by whynot on 2021-10-03
Hi
I have lately Clonezilla my ubuntu hard drive backup and a new disk copied. But After that my boot grub startup didn't work all the time black screen with the grub command line if I do ls there are too many unidentified drives how can we fix this issue without a new install.
I appreciate your answers.

---

### Post by yancek on 2021-10-04
Sorry, but I don't understand your question.  Do you mean you have used the Clonezilla softwaare to clone an entire hard drive with Ubuntu installed as the only OS on it and you are now trying to restore or boot the drive you created?

>   if I do ls there are too many unidentified drives

If you do what? So how many drives do you have?

---

### Post by grahammechanical on 2021-10-04
I am completely ignorant of cloning. I am speaking out of ignorance. But would there not be a problem with disk and partition UUIDs? Grub looking for boot files on a partition with a certain UUID which has now been changed?

May be the solution would be to use a live session to update grub on the drive? 

Regards

---

### Post by whynot on 2021-10-05
> **grahammechanical said:**
> I am completely ignorant of cloning. I am speaking out of ignorance. But would there not be a problem with disk and partition UUIDs? Grub looking for boot files on a partition with a certain UUID which has now been changed?

May be the solution would be to use a live session to update grub on the drive? 

Regards
Yes now I can able to log in to ubuntu grub menu but grub menu couldn't read or write kernel! :(
I'm going to boot with the brand new created ubuntu live cd.

---

### Post by whynot on 2021-10-05
> **yancek said:**
> Sorry, but I don't understand your question.  Do you mean you have used the Clonezilla softwaare to clone an entire hard drive with Ubuntu installed as the only OS on it and you are now trying to restore or boot the drive you created?



If you do what? So how many drives do you have?


sda
sda1 sda2
Windows
sdb
sdb1 sdb5
Ubuntu cloned and Debian 11  newly installed
sdc
sdc1 sdc5
Cloned Ubuntu into new hard disk as a USB plugged in.

---

### Post by yancek on 2021-10-06
>  Cloned Ubuntu into new hard disk as a USB plugged in.                                       

Your posts are a bit cryptic and not really informative.  The information you listed in post 5 shows you have 3 drives.  You mention windows, what's that about?  Do you have windows on sda?  Is sdb the drive on which you have Ubuntu (and Debian?) and is sdc the drive you clone to?  If you haven't resolved this issue, you need to start posting more details.

---

### Post by whynot on 2021-10-06
Sorry I solve the copy past issue.
```

whynot@Whynot:~$ sudo blkid
[sudo] password for whynot: 
/dev/sda1: LABEL="System-reserviert" BLOCK_SIZE="512" UUID="D6307D88D07D4F5D" TYPE="ntfs" PARTUUID="fb01fb01-01"
/dev/sda2: BLOCK_SIZE="512" UUID="DAC08AD5D08AC6E3" TYPE="ntfs" PARTUUID="fb01fb01-02"
/dev/sdb1: UUID="422a13f5-495e-44f1-a5b4-55e653786b29" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="616c3295-01"
/dev/sdb5: UUID="b28c3d3c-cd52-4842-a112-f1fb22a56414" TYPE="swap" PARTUUID="616c3295-05"
/dev/sdc1: UUID="1187-63C1" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="f4216753-01"
/dev/sdc5: UUID="d297b26e-bf10-4875-8bda-2b94f74db1e7" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="24f16753-05"
whynot@Whynot:~$ ls
ls           lsblk        lscpu        lsipc        lslogins     lsmod        lsof         lspgpot
lsattr       lsb_release  lsinitramfs  lslocks      lsmem        lsns         lspci        lsusb
whynot@Whynot:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0      2:0    1     4K  0 disk 
sda      8:0    0 149.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   100M  0 part 
&#9492;&#9472;sda2   8:2    0   149G  0 part 
sdb      8:16   0 298.1G  0 disk 
&#9500;&#9472;sdb1   8:17   0 297.1G  0 part /
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0   976M  0 part [SWAP]
sdc      8:32   0 465.7G  0 disk 
&#9500;&#9472;sdc1   8:33   0   512M  0 part /media/whynot/1187-63C1
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9492;&#9472;sdc5   8:37   0 297.6G  0 part /media/whynot/d297b26e-bf10-4875-8bda-2b94f74db1e7
sr0     11:0    1  1024M  0 rom  
whynot@Whynot:~$ 
whynot@Whynot:~$ sudo mount /dev/sdc5 /mnt
whynot@Whynot:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sd
sda   sda1  sda2  sdb   sdb1  sdb2  sdb5  sdc   sdc1  sdc2  sdc5  
whynot@Whynot:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.

```

---

