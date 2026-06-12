---
title: "Problem Resizing Ext3 from live CD"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by fice on 2007-04-14
Hi
I have Kubuntu Feisty Herd 5 Installed. I decided to test windows vista for a while so I used a bunch of free space I had on the drive. Now Im done testing it so I deleted the windows partition, and was planning to resize my ext3 to occupy all the space. So I grabbed the ubuntu live cd which convieniently comes with gparted. 

Problem is even with a bunch of unallocated free space(about 46GB) just beside my ext3 partition gparted will not let me make the partition bigger, it will only let me shrink it. As of now I only have two partitions, the swap partition which is in the end of the hard drive, the ext3 partition which is in the middle and all of the unallocated free space which is at the start. So the ext3 partition boundries with the unallocated free space and the swap partition. 

I have the partition unmounted, Im running gparted from a live cd. It will let me do pretty much anything with the unallocated free space except add it to the ext3 partition. I cant move the partition either, tried that as well.  

So I thought I must be doing something wrong. I started looking and now Ive seen several howto's (some even from the gparted sourceforge website) and they dont seem to show up with this problem nor do they mention anything else to do before trying to resize.

I read somewhere else that you should disable journaling whenever shrinking an ext3 partition but dont know if this applies to increasing its size. If so how do I disable journaling on it?

Any other ideas?

---

### Post by zvacet on 2007-04-14
If you can move partition put unallocated space to the right of the ext3 and just extend ext3 to all unallocated space.

---

### Post by fice on 2007-04-14
I cant move it either. I only get the option to shrink it.

---

### Post by UNITI&#1048;U on 2007-04-14
You're not going to be able to if the free space is to the left of the partition you want to resize.

---

### Post by fice on 2007-04-14
It is on the left but it wont let me move it either. 
Is there a workaround this?

Should I just try to copy paste my partition to the left side? and then resize it? It does let me do that but I would definetly backup first and I was trying to find a lazy and faster solution.

---

### Post by fice on 2007-04-14
Why wont it let me resize if the unallocated space is on the left side?

---

### Post by fice on 2007-04-15
So as I supposed so gparted doesnt fix your mbr nor your grub menu(curiously enough it does help you specify a flag for your boot partition which aparently grub overrides anyways). So after i coppied my partition from the right side to the left side then deleted the older partition and then grew it to the right side my system was rendered useless as soon as I rebooted. Truthfully I expected this since I didnt really give too much to gparted so I had a handy Super Grub Disk in hand just in case.

I booted with the Super Grub Disk but for some strange reason it wouldnt let me install grub on the MBR(for some strange reason it rebooted without doing much whenever I tried the setup command) but it did let me boot my linux partition. So I booted my linux partition edited my grub menu in /boot/grub/menu.lst to make sure it can boot to the appropriate partition then I opened the grub comand line by typing
sudo grub
Once in the command line I specified the root partition:
root (hd0,0)
then setup grub:
setup (hd0)
no errors where reported
rebooted and everything works as before except I have a 90GB partition instead of a 43GB.

I still dont understand why gparted didnt let me resize to the left side.

Anyways thanks for all your replies.

---

