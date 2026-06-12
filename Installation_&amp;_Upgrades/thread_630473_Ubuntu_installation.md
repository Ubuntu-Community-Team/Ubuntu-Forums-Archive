---
title: "Ubuntu installation"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by opaltchenov on 2007-12-03
Hello everybody, i need your help. I have 2 hard disks:
1st: called C: is 18.2GB with windows xp - 13GB are free (ntfs)
2nd is spited to D: and E:
D: is 10GB - 9.18GB are free (ntfs)
E: is 64.5GB - 7.27GB are free (ntfs)

My question is, can i install Ubuntu on D:? How to do this? 
I saw Ubuntu needs 2 places, one for swap and  other for... called "/".
As fas as i know the swap is such a temporary place where Ubuntu keep data for open applications and the other place called "/" is for the file system of the os? 
Am i right? 
If needed i D: could be formated but C: with windows, i must keep it as the other people using this computer need windows.
Pls help guys.

---

### Post by mikewhatever on 2007-12-03
You'll need to manually edit partitions during the installation, delete D and create / and swap in the unallocated space. Don't forget to back up important data from D before editing.
(C:\, D:\ etc are MS Windows notions. While editing partitions in Ubuntu you'll see names like /dev/sda1, /dev/sda2,etc. These would be the first two partitions on the first HDD, /dev/sda1 most probably corresponding to C. /dev/sdb1, etc would be your second HDD. As an example, here is my partition table on the single HDD:
> /dev/sda1   *           1        3665    29439081    7  HPFS/NTFS
/dev/sda2            8583        9598     8161020    c  W95 FAT32 (LBA)
/dev/sda3            9599        9729     1052257+  d7  Unknown
/dev/sda4            3666        8582    39495802+   5  Extended
/dev/sda5            3666        6097    19535008+  83  Linux
/dev/sda6            6098        6159      497983+  82  Linux swap / Solaris
/dev/sda7            6160        8582    19462716    b  W95 FAT32
)

---

### Post by opaltchenov on 2007-12-03
so Mike you mean i can install Ubuntu on D: only, both / and swap? I will start the installation and will make some screen shots as well

---

### Post by mikewhatever on 2007-12-03
> **opaltchenov said:**
> so Mike you mean i can install Ubuntu on D: only, both / and swap? I will start the installation and will make some screen shots as well

Well, yes, but not quite on D. You'll have to delete it getting rid of the partition with NTFS and create both / and swap in its place. / needs to be formatted as ext3, the file system linux uses. Why don't you check out some pictures first [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by opaltchenov on 2007-12-03
these screenshots are very useful. I think i will try with first option :) 
but Mike do you think i have a problem with my partions (see 3.png)
[http://store3.data.bg/opaltchenov/Ubuntu/ubuntu.html](http://store3.data.bg/opaltchenov/Ubuntu/ubuntu.html)

---

### Post by mikewhatever on 2007-12-03
The link you provided does not work. What do you think is the problem? The first option, guided partitioning or something like that, try to resize (shrink) one of the existing partitions and then create / and swap. Choose whatever you prefer.

---

### Post by opaltchenov on 2007-12-03
Mike forget abt previous link, pls check this

[[IMG]http://img81.imageshack.us/img81/3069/screenshotinstallen2.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshotinstallen2.png)

In installation menu (1st option) ive selected the second hard disk, i think all data will be formated... or
Do you want me to post another screenshot from installation?

---

### Post by opaltchenov on 2007-12-03
[[IMG]http://img510.imageshack.us/img510/5354/screenshotinstall1qe7.th.png[/IMG]](http://img510.imageshack.us/my.php?image=screenshotinstall1qe7.png)

Mike im sorry to bother you man, but you are the only one who pay attention to me, and im happy you doing that. If still there pls see this shot below. Do you think that is ok? 10GB are split 1GB for swap and the rest for "/"
[[IMG]http://img137.imageshack.us/img137/8798/screenshotinstall2gm5.th.png[/IMG]](http://img137.imageshack.us/my.php?image=screenshotinstall2gm5.png)

---

### Post by mikewhatever on 2007-12-03
Yep, well done. Everything looks ok.

---

### Post by opaltchenov on 2007-12-03
Yes now everything is ok :) Thanks Mike!

---

### Post by mikewhatever on 2007-12-03
> **opaltchenov said:**
> Yes now everything is ok :) Thanks Mike!

:popcorn:

---

