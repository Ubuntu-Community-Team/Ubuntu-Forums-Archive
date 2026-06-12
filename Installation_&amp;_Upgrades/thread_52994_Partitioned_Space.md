---
title: "Partitioned Space"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by deat on 2005-07-29
I installed Ubuntu 5.04 just fine, got a dual boot with WinXP. I had a 20 GB hard drive which I partitioned in half, with 500 MB for swap. I had to going good for about 4 months, but now I just want to completely get rid of Windows. I went into the built in partitioner in the Ubuntu install CD, and I deleted the partition with Windows on it. I looked for a way to take that 9.5 GB of free space I got from Windows, and place it onto the Ubuntu partition. I can't find anywhere how I would be able to do that. Now I have the Ubuntu partition with 10 GB, and 10 GB of free (unused) space. 

Any ideas? Is this even possible?

---

### Post by trivialpackets on 2005-07-29
[QUOTE=deat]I installed Ubuntu 5.04 just fine, got a dual boot with WinXP. I had a 20 GB hard drive which I partitioned in half, with 500 MB for swap. I had to going good for about 4 months, but now I just want to completely get rid of Windows. I went into the built in partitioner in the Ubuntu install CD, and I deleted the partition with Windows on it. I looked for a way to take that 9.5 GB of free space I got from Windows, and place it onto the Ubuntu partition. I can't find anywhere how I would be able to do that. Now I have the Ubuntu partition with 10 GB, and 10 GB of free (unused) space. 

Any ideas? Is this even possible?[/QUOTE]
 Certainly, if you've got the area deleted, just format the space as ext3 or whatever you are using for a file system type, mount it as something, like /extra or something and then you just need tos et your fstab file to recognize it.  I am speaking in very general terms, as I'm nowhere near my notebook right now, but look about the forums, and certainly you'll get more information on these.  At that point, your ubuntu will see them.  Sorry I can't be more specific, I'll follow up later if you need more specific info

---

### Post by matthew on 2005-07-29
This page should help you get started. Take a look and if you have further questions feel free to ask. The big thing to realize is that you cannont resize a partition while it is mounted so you will have to either use the method described in this page and boot using the installer or use a live cd like the Ubuntu one or Knoppix and use a partition program like gparted or qparted.

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

Edit; what I'm getting at is that you should be able to reclaim the space and maybe even make it part of your current ubuntu partition.

---

### Post by deat on 2005-07-29
[QUOTE=matthew]This page should help you get started. Take a look and if you have further questions feel free to ask. The big thing to realize is that you cannont resize a partition while it is mounted so you will have to either use the method described in this page and boot using the installer or use a live cd like the Ubuntu one or Knoppix and use a partition program like gparted or qparted.

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

Edit; what I'm getting at is that you should be able to reclaim the space and maybe even make it part of your current ubuntu partition.[/QUOTE]
 I read over that documentation, and it says to go into the partition and select it's size, but with the partition I want to keep, it doesn't give me the option to change size.


ReiserFS Journalling file system
Mount point: /
Mount options: defaults
Bootable Flag: on


That is the partition's setup. Aside from those and one other option, that's all that shows up when I try editing.

---

### Post by matthew on 2005-07-29
I have heard some horror stories of resizing reiser partitions. Since I have never done it I'm afraid I won't be much help to you. That said, let me share what I would do if it were my system.

1. Backup everything
2. Make sure the backup worked
3. Use the Ubuntu live cd or Knoppix to boot and run the partitioning program (there are several...parted, gparted, qparted...most are just different gui's for the same program) and try to delete the old partition if it wasn't already and then resize the ubuntu one.
4a. if that worked, reboot and test and you're done
4b. if it didn't, reinstall, repartition as desired, restore data

You may want to start a new thread or at least do some searching on resizing a reiser partition before you try this and see what others may have experienced. Sorry I'm not more help on this specific filesystem. i have heard that there may be some specific tools available as well for doing this sort of thing in reiser as well. Maybe you will run across them.

---

### Post by deat on 2005-07-29
You were helpful, thanks.

By the way...

YAY! I deleted the wrong partition! Now I've lost all of my files and many important files that were only located on this machine. Take this as a lesson people: back up your bloody hard drives even if you think you know which partition is which.

Now I can just wipe everything I guess and start again. *sigh*

---

### Post by Xian on 2005-07-29
Unless you formated the partition the data may still be there.
Sorry about the outcome but matthew did instruct you to backup everything.

Anytime you are partitioning this is a must if you are being safe.

---

### Post by deat on 2005-07-29
I know, but I had deleted the partition prior to requesting help, so it was still entirely my undoing.

---

