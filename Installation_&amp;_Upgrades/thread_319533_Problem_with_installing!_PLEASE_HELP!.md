---
title: "Problem with installing! PLEASE HELP!"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by condawg on 2006-12-15
Hi there. I really REALLY need help installing my Linux Ubuntu version 6.10 onto my computer.
Right now, i'm running off of the Live version, but I'm trying to install it so that I can daulboot it and XP.
I get up to step 5, the partitioning part.
When I tell it to do it by itself, I set the size to about 20gigs, and when I click "next," it never goes to the next step. It just stays at step 5.
When I try to manually partition my hard drive, I just click "next," twice, and it says "No root file system."
How can I fix either of these problems to get my Linux Ubuntu running?
Thank you!

---

### Post by wpshooter on 2006-12-15
I would suggest that you NOT let the install do the paritioning itself but rather you should do the paritioning manually yourself.

You probably need to reboot to the Ubuntu CD again to get out of this loop you are in.

I would highly recommend that if you don't really know what you are doing that you install Ubuntu on an old computer by itself first before you attempt putting it on your computer that has Windows on it, because you may wind up wrecking your Windows installation.

Good luck.

---

### Post by condawg on 2006-12-15
1) I already tried to do it manually (I listed results above...)
2) I already rebooted like... 20 times.
3) I don't have any old computers that belong to me, rather my siblings.

Thanks for trying to help, it's much appreciated.

---

### Post by drphilngood on 2006-12-15
See here:

[psychocats-partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by bulldog on 2006-12-15
If you're serious about the install,download the gparted live cd from here,

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a disk and boot from it.
You should get a graphical interface with your hard disk and partitions listed.
Resize your windows after you have run defag several times.
Be sure you can make 20Gb free without hurting your windows.

In the free space you made,right click it and choose new partition.
Make a swap space about 1GB and format it as swap.
Make the rest of the space a partition with ext3 file system.
Don't forget to hit apply,otherwise nothing will happen.
If done.exit the gparted cd an reboot the ubuntu live cd.

When you come to the partitioner,choose manual partitioning.
Mount the created swap as swap and the other ext3 partition as /   (root) and complete the installation.

---

