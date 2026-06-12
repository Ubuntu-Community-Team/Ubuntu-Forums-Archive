---
title: "Ubuntu 18.04/Win10 dual boot - reduce Win partition and increase /home"
date: 2021-01-21
forum: Installation &amp; Upgrades
---

### Post by carlo8 on 2021-01-21
Hi there,
I have a dual boot with Ubuntu18.04 and Windows10, and when I installed everything I underestimated the space I would need in my /home partition.

This is my current situation:

[IMG]https://i.postimg.cc/GhykkXCf/Schermata-da-2021-01-21-12-08-33.png[/IMG]


I was planning to reduce the dimensions of the Windows partition (sda3) and to use that space to increase the /home (sda7).
Before starting, however, I was reading some guides and I seem to understand it wouldn't work. As I understand, the created empty space would be adjacent to the original partition (sda3), so I couldn't use it to extend sda7.
Is that so? In case, how can I fix that?
Thanks![IMG]https://ibb.co/w79rpMz[/IMG]

---

### Post by ActionParsnip on 2021-01-21
The partitions that you want to manipulate are not next to each other so you can't do this easily. If this was an LVM then you coluld shrink the NTFS in Windows, make a new file system of the freed space and add it to the LVM of /home.
You still have 15.5Gb free in /home (25% ish free) so not too shabby. I'm guessing your data needs have changed and you need more space.
You can always make a folder in the NTFS for casual user data (images, video etc) then store that there instead. Ubuntu can read and write NTFS.

---

### Post by oldfred on 2021-01-21
Only use Windows to shrink NTFS partitions. Windows wants 30% free to work well, so do not make too small.

And you will have to use live installer to modify Linux partitions with gparted. Little key icons say partitions are mounted and you cannot change mounted partitions. 
Easiest from a partition standpoint, would be just to add another partition and use it as a data partition for some of your data in /home.

Make sure you have good backups of both Windows & Ubuntu, as partition changes can corrupt system if any power failure or other issue. Never interrupt a gparted change.

---

### Post by yancek on 2021-01-21
This is feasible but anytime you are changing partitions, it is risky.  I would agree with the posts above that the first step is to make backups of any and all data that has importance to you.

Then you would need to boot into windows and use Disk Management to resize/shrink the largest windows partition which is shown as sda3 in GParted and should be what is referred to as C in windows.  Once that is done, you need to reboot into windows to verify that it boots without problems and runs without problems.

As pointed out above, you need to use a 'live' system with Ubuntu or GParted to modify the other partitions as you cannot modify a mounted partition.  Make sure the partitions are not mounted.  You should have unallocated space between sda3 (windows) and sda5 which is the Ubuntu install.  Use GParted to move that partition to the left.  This will require not only moving the boundaries of the partition but also the nearly 20GB of data on it and will take some time.  Decide how large you want this partition, you can leave it the same size (34GB).  When that finishes use GParted tp turn swap off and delete the swap partition (create a new one later if you want).    You can then use the available unallocated space to move the /home partition to the left whcih will also take some time as again, it has to move 43GB of data.  If you want a swap partition, be sure not to use all the space for /home but leave some which you can use for swap.

The other far simpler method and one suggested above and which is what I would do is to simply shrink the largest windows partition and create another 'data' partition.

---

