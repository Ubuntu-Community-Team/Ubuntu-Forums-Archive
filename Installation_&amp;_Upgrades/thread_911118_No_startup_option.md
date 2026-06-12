---
title: "No startup option"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by cathalcummins on 2008-09-05
Don't know how to create search variables for this problem.

So, here goes. I was running XP on my PC. Decided to dual boot with the latest version of Ubuntu.

Went for full installation, everything seemed to be going fine. It finished and asked me to reboot.

Problem: on rebooting, it doesn't ask me what OS do I wish to use. It soes straight to the XP startup screen.

Any ideas on how to get the "choice" screen. (something to do with boot sectors, I think I may have interrupted the partition process)

I am unsure what info you may need to answer this question. I don't wanna rhyme off PC specs in vain, so if you need any info please ask and I will ascertain.

Thank ya.

---

### Post by Pumalite on 2008-09-05
One hardrive or two? Did you disconnect one drive at the time of the installation?
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cathalcummins on 2008-09-05
I have two hard drives. The Ubuntu Installer Partition manager tells me the following:

\dev\sda
\dev\sda1 ntfs ~ 400GB
\dev\sda2 ext3 ~ 44GB
\dev\sda5 swap ~ 1GB

^^^^^^^ This is my Data Slave

\dev\sdb
\dev\sdb1 ntfs ~ 50GB
\dev\sdb6 ext3 ~ 100GB <<< I think this is where Ubuntu has installed itself
\dev\sdb5 swap ~ 5GB

^^^^^^ This is my master.

Following the link you sent me; the grub wants to know whether I want 

 (hd0,1)
 (hd1,5)

I can't really tell whether the 1's and 0's refers to sda or sdb, so I haven't continued.

Any ideas?

---

### Post by cathalcummins on 2008-09-05
Okay, so the GRUB thing helped get the screen up to choose between OS but it introduces the problem that none of them work... not even XP!

I think I may have chosen the wrong partition in grub>

here is my fdisk:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    98526644    49263291    7  HPFS/NTFS
/dev/sda2        98526645   312496379   106984867+   5  Extended
/dev/sda5       303708888   312496379     4393746   82  Linux swap / Solaris
/dev/sda6        98526771   303708824   102591027   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2dd92943

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   691357274   345678606    7  HPFS/NTFS
/dev/sdb2       691357275   777642389    43142557+  83  Linux
/dev/sdb3       777642390   781417664     1887637+   f  W95 Ext'd (LBA)
/dev/sdb5       777642453   781417664     1887606   82  Linux swap / Solaris

---

### Post by Pumalite on 2008-09-05
You have Linux installed in both drives.
Search Dualboot Two Hard Drives in this Forum.

---

### Post by cathalcummins on 2008-09-05
Okay, as you said, I had feisty on the other HDD and this was screwing everything up.

I took it off the 400GB HDD, created a new partition on the master, ann freshly installed it. I needed to, however, install the grub loader to get the choice screen. Thank you for all your help.

---

### Post by rainfield on 2008-09-05
I am also having the same problem of not getting the start up option.  Sorry, I'm pretty new at this so I hope I've got my info correct and I'm not screwing up what I mean.

I tried to do a dual boot with vista on my laptop.  When I reboot after the install, it went straight to vista.  I installed GRUB into my root partition, I believe.  Now I'm not sure how to access the option to boot into ubuntu.

Thanks in advance for any solutions!

---

### Post by Pumalite on 2008-09-05
Since you chose to install Grub in your root partition; you can use Super grub to boot it.

---

