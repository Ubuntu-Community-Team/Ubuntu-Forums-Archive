---
title: "showing less harddisk space ..."
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by gauravnarra on 2011-05-05
my hard disk is 320gb and i think i made a mistake while booting ubuntu ,since it is showing only 100gb space .Can any one help me fix this..need help asap...:)

---

### Post by aphatak on 2011-05-05
Open a terminal and run the command 'sudo fdisk -l'.  It will ask for a password; key in your ubuntu password.  Post the results here so together we can figure out where the other 220GB are.

---

### Post by gauravnarra on 2011-05-10
[B][I]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc2fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97654784   83  Linux
/dev/sda2           12158       30402   146541569    5  Extended
/dev/sda5           12158       27362   122128384   83  Linux
/dev/sda6           27363       30402    24412160   82  Linux swap / Solari[/I][/B]

---

### Post by Quackers on 2011-05-10
Your hard drive appears to have 250GB not 320GB.
What sizes are your partitions?

---

### Post by aphatak on 2011-05-11
As Quackers observed, you have a 250GB hard disk, not a 320GB hard disk.  It is being used as -
/dev/sda1     100GB     - your root partition
/dev/sda5     125GB     - don't know what is in this
/dev/sda6      25GB     - swap area
--------------------
    Total     250GB
===========
(The 'extended partition' is a group that contains sda5 and sda6, so its size does not count).

Now, for reclaiming that space.
[LIST=1]
[*]If you bought the hard disk as a 320GB hard disk, start screaming at the seller.  If the 70GB difference is important to you, you might want to get a replacement; if it is not, you might want to ask for some of your money back.  If you replace the hard disk, make sure you have made a copy of your partitions before returning the disk, so you do not lose the effort you have put in creating the set-up.
[*]The 25GB swap space seems a bit excessive.  I have 16GB RAM in my desktop, and I have never seen the swap-space being used, even when I edit 160-megapixel images.  A rough guide is a swap space between 1 and 2 times your RAM, unless you use highly memory-intensive applications.
[*]Find out what sda5 contains.  In a terminal window, enter the command 'cat /etc/mtab'.  That will tell you which directory sda5 is mounted into.  If it is not mounted anywhere, you might want to get rid of it.  If it is mounted as '/home', then your allocation of 100GB to the root partition (sda1) is an overkill, and you might want to reduce it.  The exact size will depend on the software you have installed; but 16GB root partition is a good size to start with.  If sda1 is mounted as '/boot', then 100GB is definitely way too much - I would reduce it to something like 1GB!
[/LIST]
The best way to resize your partitions is to boot your live CD, and then use gparted (System -> Administration -> Gparted).  Please make sure you have backed up your data before you tinker with your hard disk!

If you want to get rid of sda5 altogether, -
[LIST=1]
[*]Boot your live CD, then fire up gparted.
[*]Make sure all the partitions of the hard disk are unmounted.
[*]Delete sda5
[*]Reduce the size of sda6 to the one you want.
[*]Move sda6 to the beginning of sda2 (your extended partition).
[*]Reduce the size of sda2 so it is just sufficient to contain sda6.
[*]Move sda2 to the far end of the disk.
[*]Expand sda1 to occupy all the remaining space.
[*]Click 'apply', then possess your soul in patience - moving partitions around can take a bit of time.
[/LIST]
If you decide to keep sda5, and reduce the size of sda1, the process is similar - from gparted, reduce sda1, move sda2 down into the vacated space, increase its size to occupy the remaining area, move sda6 to the far end, and then increase the size of sda5 as far as it will go.

Please post the results when you try this to let me know how it went.

---

