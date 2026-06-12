---
title: "My homefolder is not recognized after downgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Cotopaxi on 2011-04-29
Hi
I downgraded from 11.10 to 10.10 via installation CD, because the 11.10 installation was lost beyond recovery.

The 10.10 installation works fine except one problem

During the installation, I selected manual setup of Partitions and my home partition was not recognized as /home but only as ext4.

Fortunately I managed to recognize it, due to the size of the partition, so I prevented this partition from being formatted.

Now, this partition is not my home partition, but just an ordinary partition, which I can access and where all my files are present.

Anybody knows any magic trick, how I can make this partition my home partition?

Thanks for your help!

---

### Post by dino99 on 2011-04-29
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by epicoder on 2011-04-29
](*,) I literally **JUST** posted in your other thread.

Boot via livecd/usb, then open up a terminal.
assuming your linux partition is /dev/sda1 and /home is /dev/sda2, run these commands in the terminal:
```
sudo mount /dev/sda1 /mnt
cd /mnt/etc
sudo gedit ./fstab
```In the text editor, that comes up, put this line on the bottom, then save and quit:
/dev/sda2 /home ext4 errors=remount-ro 0 0

Reboot and all should be well.

---

### Post by Cotopaxi on 2011-04-29
I will study through this subject. Thanks again!

---

### Post by Cotopaxi on 2011-04-29
sh228

sorry, I did not manage to read your post on time.

The problem seems to be, that the servers are totally overloaded, so any addressing these servers just did not work!

I will come back to your partitioning suggestion in a few minutes, I will just write doen the exact partitions, and I am back.

Thanks very much indeed again! :popcorn:

---

### Post by Cotopaxi on 2011-04-29
sh, here I am back:

My home partition, that is not recognized as such, is '/dev/sda1' Size: 204.89 GiB

The boot partition, 'ext4 filesystem' is '/dev/sda2'  Size 23.28 GiB

the linuxswap partition is '/dev/sda3' Size 4-71 GiB

For safety reasons, how shall I proceed from here on

Thanks again for your reply!

---

### Post by Cotopaxi on 2011-04-29
sh,

I just made it, following your instructions, only changing sta1 and sta2.

It worked!!

Thanks very much indeed, you are the greatest!!!

Thanks again! :popcorn: :popcorn:

You deserve caviar and champaign, but I don't have these icons available!

---

