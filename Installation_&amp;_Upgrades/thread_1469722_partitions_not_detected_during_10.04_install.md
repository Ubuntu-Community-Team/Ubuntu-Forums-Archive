---
title: "partitions not detected during 10.04 install"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by kingair_six on 2010-05-02
hi,

trying to install 10.04, once i reach the dialog where i'm supposed to select partitions for mount/install, the installer reports my HDD is empty. it wants to create a partition table and proceed from there.

in fact, my 1TB disk is 50% full and contains 10 partitions, including /boot /home, swap (which i wanna reuse) and 2 other OS partitions. 

these partitions do show up when running nautilus in 10.04 live, also "fdisk -l" shows them - the installer does not.

tried the dmraid fix described in several posts - no success.

any help / clue greatly appreciated, thanks :)

kingair_six

---

### Post by rajasthanub on 2010-05-02
i need help on same issue ; at time  of partition it shows " no operating system on computer" ;;;;;
 as far as i can think this might be because of problem with grub2 .
 i am having dual boot ,after installing reinstalling windows there was no ubuntu so i made changes to bootloader as directed by forum.... i think problem is from there

---

### Post by kingair_six on 2010-05-02
i forgott to add, i also have a dual boot via a modified grub2 ;) sounds like that's the key?

---

### Post by dino99 on 2010-05-02
the "alternate" iso let you tweak your installation as you want.
i always format before installing (partedmagic)
unetbootin is a nice solution

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

some more into signature below too

---

### Post by kingair_six on 2010-05-03
having read up on your posts, I will try the alternate installer, however I do not get why prepartitioning should help me?

I already have the partitions I want to use in place, but can not tell Ubuntu to use them from the installer.

---

### Post by dino99 on 2010-05-03
> **kingair_six said:**
> having read up on your posts, I will try the alternate installer, however I do not get why prepartitioning should help me?

I already have the partitions I want to use in place, but can not tell Ubuntu to use them from the installer.

if installer dont see your partitions, well its clear to me that your partitioning , if exist, is wrong. Reread the post, you have to understand it first (the installer on cd is known to be bad)

---

### Post by kingair_six on 2010-05-03
I see what approach you are taking as described in the other thread. but my system is already running and the partitions are neither wrong nor damaged. they've been set up via GParted and have prooven reliable in a production environment. therefore I see no point in repartitioning, considering the amounts of data I'd have to shovel around onto other drives to avoid data loss. I'm currently loading the alternate disk as adviced.

---

### Post by dino99 on 2010-05-03
i've reread your 1st post: 10 partitions, how many primary yet ?

---

### Post by kingair_six on 2010-05-03
four primary partitions. as many as possible.

---

### Post by frantid on 2010-05-03
maybe try mounting them with nautilus outside of the installer?

---

### Post by kingair_six on 2010-05-03
that does not work in live environment either. however, it shows them in the left bar.

---

### Post by frantid on 2010-05-03
click on them in the left bar, that will mount them see if the installer continues.

Make sure you are doing the manual partition selection -- in the installer that is...

---

### Post by kingair_six on 2010-05-03
mounting via nautilus by clicking on them does not work...

---

### Post by frantid on 2010-05-03
open either disk utility or gparted and run a check on your partitions.  

also try mounting via the terminal to see what error you get.

since your system was working, I suspect the cd

---

### Post by kingair_six on 2010-05-03
the system is working, i'm just trying to install 10.04 as an additional os on my 2nd linux root partition (which is clear to use). i veryfied the md5sum, tried 2 different downloads, tried the alternate cd and a usb-booted live version. neither worked. will try mounting via cli in live though.

---

### Post by kingair_six on 2010-05-03
tried mounting drives via cli... worked fine. much to my suprise, mounting from within nautilus also worked (hasnt done so previously). exception is the second linux root. Getting some strange error there: 

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg  reports:```
 EXT4-fs (sda5) - no journal found.
``` 

however, that should not prohibit linux from identifying the rest of the partitions in the installer? 

am now trying mkfs -t ext4 /dev/sda5 ... see what that does. 

EDIT: nothing. working ext4 on /dev/sda5 does not fix the problem.

---

### Post by frantid on 2010-05-03
hmmmm

fsck /dev/sda5

---

### Post by kingair_six on 2010-05-03
device is perfectly fine, both from live as well as 9.10 environment.

fsck is totally happy.

---

### Post by kingair_six on 2010-05-03
bug's already been on launchpad from a beta release:

[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/559110"]
**see launchpad.net** [/URL]

---

### Post by srs5694 on 2010-05-03
Try using a filesystem other than ext4fs. There are lots of choices. For a typical root (/) filesystem with a separate filesystem for user files, try ext3fs or ReiserFS. If the partition will hold lots of big files, try XFS.

---

### Post by Mohammad_Khalid_Hussain on 2010-05-04
I think I have the same problem found over [here](http://ubuntuforums.org/showthread.php?t=1468171).

---

