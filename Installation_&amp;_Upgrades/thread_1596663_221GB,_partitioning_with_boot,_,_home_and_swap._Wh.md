---
title: "221GB, partitioning with /boot, /, /home and /swap. What sizes?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Meandlinux on 2010-10-14
Hello!

I'm wondering how big the /boot partition should be, and how big the rest of the partitions should be, and should I create the /swap as the first partition, or the last?

Thanks in advance!

---

### Post by Elfy on 2010-10-14
I'd not use a /boot unless you really need to.

I have a largish / but then I do not have a seperate /home - when I did I always used a 10Gb / and it never filled.

/home deoends on whether you keep all your data in there or not - if you wanted to you could just use whatever is left.

You'll get a whole load of different options in this thread - at the end of the day it really depends on you and how you want to work it.

---

### Post by dabl on 2010-10-14
As already said, you don't need a partition for /boot unless you're planning a whole lot more than installing Ubuntu.

The root filesystem will install on about 3.5GB, but it will quickly outgrow that.  If you'd like to just not worry about it for a long time, make it 10GB.

The swap partition needs to be the same as your memory if you think you ever might want to use "hibernate" aka Suspend to Disk.  Technically, if you never use S2Disk, and you've got lots of RAM that you'll never fully utilize, you can get by without a swap partition.  I always put the swap partition toward the middle of a disk, if possible (like between the root and the /home partitions), but that's more a matter of taste than function.

Then /home can be all the rest of the disk.

---

### Post by Meandlinux on 2010-10-14
Thank you!

Aren't programs installed on /? Is 20GB enough?

Found this nice guide: [http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

---

### Post by Meandlinux on 2010-10-14
> **dabl said:**
> As already said, you don't need a partition for /boot unless you're planning a whole lot more than installing Ubuntu.

I read that it will make the boot faster here: [http://ubuntuforums.org/showthread.php?t=414054](http://ubuntuforums.org/showthread.php?t=414054)

But then I read this: [http://superuser.com/questions/66015/installing-ubuntu-do-i-really-need-a-boot-parition](http://superuser.com/questions/66015/installing-ubuntu-do-i-really-need-a-boot-parition)

---

### Post by Elfy on 2010-10-14
> **Meandlinux said:**
> I read that it will make the boot faster here: [http://ubuntuforums.org/showthread.php?t=414054](http://ubuntuforums.org/showthread.php?t=414054)


That is an old post and refers to ext2 - a default in ubuntu now is ext4

---

### Post by Meandlinux on 2010-10-14
Swap first or last: [http://ubuntuforums.org/archive/index.php/t-598625.html](http://ubuntuforums.org/archive/index.php/t-598625.html)

---

### Post by Meandlinux on 2010-10-14
> **forestpiskie said:**
> That is an old post and refers to ext2 - a default in ubuntu now is ext4

I see, thank you!

---

### Post by dabl on 2010-10-14
> **Meandlinux said:**
> 

Aren't programs installed on /? Is 20GB enough?



Yes, packages are installed in /usr but you won't fill up 20GB if you install every Linux package in the world.  Seriously, 10GB is way more than you'll ever use, if you've got your /home folder on another partition.

---

### Post by Meandlinux on 2010-10-14
> **dabl said:**
> Yes, packages are installed in /usr but you won't fill up 20GB if you install every Linux package in the world.  Seriously, 10GB is way more than you'll ever use, if you've got your /home folder on another partition.

Thank you! :)

---

### Post by dabl on 2010-10-14
> **Meandlinux said:**
> Swap first or last: [http://ubuntuforums.org/archive/index.php/t-598625.html](http://ubuntuforums.org/archive/index.php/t-598625.html)

A. If you have plenty of RAM (2GB or more) you probably won't use swap, and it won't matter where it is located on the hard drive.

B. His argument that the inner cylinders are a shorter trip for the heads depends entirely on where the drive heads start their journey to save the information that is to be swapped out.  On the average, the middle cylinders are ... the closest average location.  :guitar:

---

