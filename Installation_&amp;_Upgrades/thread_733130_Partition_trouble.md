---
title: "Partition trouble"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by hp_notebook on 2008-03-23
Hi all,

I'm a not-so-experienced Linux user, and I hear that Ubuntu is the most user-friendly. I downloaded the Ubuntu 7.10 iso and burned it to a disc, and booted up into the "LiveCD" thing.

Everything went ok, except when I went to partition my drive. I have Windows Vista installed on a big partition that takes up my entire drive, but GParted does not recognize the partition. Instead, it says I have one big unallocated partition with nothing on it, which is incorrect.

I went back to Vista and shrunk the volume and created a new NTFS-based partition next to the first big partition w/ the Vista on it, and booted back up into the LiveCD. GParted still doesn't recognize my partition as having anything on it, and says my drive is taken up by unallocated space.

What should I do? :confused:

---

### Post by Pumalite on 2008-03-23
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Hope you can see the whole picture now.

---

### Post by hp_notebook on 2008-03-23
> **Pumalite said:**
> Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Hope you can see the whole picture now.

What will this do for me?

---

### Post by Pumalite on 2008-03-23
Maybe show you your partitions as they are. From there, I can help you.

---

### Post by hp_notebook on 2008-03-23
> **Pumalite said:**
> Maybe show you your partitions as they are. From there, I can help you.

Thanks, will do.

---

### Post by buntu_Geek on 2008-03-23
In that partition step(during installation..).... you chose manual partitioning option...
from there it opens a partitioner... where it will surely show you the partitions..

---

### Post by hp_notebook on 2008-03-23
> **buntu_Geek said:**
> In that partition step(during installation..).... you chose manual partitioning option...
from there it opens a partitioner... where it will surely show you the partitions..

That's what I did, but it shows that my disk is entirely unallocated.

Also, I ran the GParted LiveCD, and it told me the exact same thing. /dev/hda (about 78.0GB) is all unallocated, according to the program.

---

### Post by Pumalite on 2008-03-23
Let's hope you did not deleted it

---

### Post by Pumalite on 2008-03-23
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If there is anything there, it'll boot it. Unless you are running Vista now. Then I don't know what to think.

---

### Post by hp_notebook on 2008-03-23
> **Pumalite said:**
> Let's hope you did not deleted it

It's not. I'm posting from my Vista installation on the "unallocated" partition.

Is there any way for Ubuntu to recognize my partition as an allocated one? (Besides reformatting my disk and reinstalling Vista, then installing Ubuntu?) I've installed 6.10 on my computer before.

Although, the 6.10 LiveCD is now showing up that my disk is unallocated too.

---

### Post by buntu_Geek on 2008-03-23
Probably you have to recovery the partition table using gpart

Use your live cd and boot from it.. ( connect to internet...)
Type the following code in the terminal
[code]
ubuntu@ubuntu:~$ sudo apt-get install gpart
ubuntu@ubuntu:~$ sudo gpart /dev/sda -W /dev/sda
[\code]

Then after the execution of the second command just see whether gpart is able to recognize the partitions that you expect....
If not... then dont try to overwrite the existing partition table...

Note: Sometimes this step might cause some loss of data....do it on your own risk...
But this is the way to recover the partition table...

---

### Post by Pumalite on 2008-03-23
You can also use TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

