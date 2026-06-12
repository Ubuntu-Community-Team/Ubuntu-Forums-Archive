---
title: "Dual boot install Windows + Ubuntu, later to be made Ubuntu only?"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Abdi110 on 2007-03-08
Hi there. I think it's high time I give Linux a try again, especially since I've upgraded from a ThinkPad 570 to a T41. My goal is to get 6.10 running with Windows under VM for some select apps I need for work. At the moment I've got a 100 gig drive running XP Pro. Is there a way I can change the NTFS partition around so there's space for Ubuntu, install Ubuntu, get dual boot going, then when I feel like I don't need the Windows boot anymore, kill off the NTFS partition and give that space to Ubuntu?

Thanks,

---

### Post by bulldog on 2007-03-08
The best thing you can do is download the GParted live cd from here,[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it on a cd-r and boot from it,after you defrag windows several times to get all your files to the front as much as possible.

Now you have a graphical interface,and you should be able to resize your windows partition and create three new partitions.
Reccomendation is:
10GB /   (root) partition formatted as ext3
1GB swap partition formatted as swap
The rest of the free space is mend for your /home partition, and should be formatted as ext3 as well.

You only can have four primary partitions,so if this give you any trouble,create an extended partition and make your ubuntu partitions in the extended.

Make your windows the first primary to avoid problems later on.
Ubuntu doesn't care if it's on a primary or logical partition,so don't worry about that.

If you made the partitions as you like,you can exit the live cd and boot from the ubuntu cd for thr install.
When you come to the partitioner,select manually partition,because you already did this.

Now mount your 10GB partition as /  which means root and set it to format as ext3.
Mount the 1GB as swap and set it to format it as swap.
Mount the last partition as /home and format it as ext3 again and proceed with the install.

All should go fine,good luck.

---

### Post by Abdi110 on 2007-03-08
Thank you, happy to see I've got a bit of direction now. I'm guessing that later on when I opt to drop Windows all together as a bootable OS, I can just kill the partition through GParted?

---

### Post by bulldog on 2007-03-08
> **Abdi110 said:**
> Thank you, happy to see I've got a bit of direction now. I'm guessing that later on when I opt to drop Windows all together as a bootable OS, I can just kill the partition through GParted?

Yep,no problem with that one.
But don't do this too soon,just make yourself comfortable with ubuntu,and time will tell if it works out for you.

Welcome to Ubuntu.:)

---

### Post by Abdi110 on 2007-03-09
Thanks! Running from within Ubuntu now.

---

