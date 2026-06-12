---
title: "Ubuntu 7.10- creating a new partition"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by totakad on 2008-04-20
hello to the Ubuntu forums!

i'm  having a little problem with creating a new partition where i can install Ubuntu on. my laptop's hd is 40gb big and basically all of the space is used for one partition where i have windows xp home sp2. i have the hd defragmented, i have booted Ubuntu up from the live cd, trying to make some unallocated space for the installer to make the new partitions itself, because at the moment it says that i don't have enough free space on my hd to make new partitions. now the main problem is that i cannot resize or edit the main partition in the gnome partition editor. all the windows stuff etc. are on the first 1/6 of the disk so it cant be that the partition is fragmented. the resize option only lets me choose whether the 7mb of unallocated space is in front of the windows partition or behind it. would like some advice and solutions :)

thanks.

---

### Post by Pumalite on 2008-04-20
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP, choose 'resize from the menu. In the 'free space', make 3 'New' partitions:
10 GB for '/'
1 GB for /swap ( in laptops, /swap=RAM)
The rest for /home.
Install Ubuntu, go 'Manual' and choose the partitions already prepared.

---

### Post by gsiliceo on 2008-04-20
What happens if you run the defrag utility? you'r files might be fragmented.
I strongly recommend you this utility to defrag.
[http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)
And it has a screensaver defrag too, plus is open source.
And try using partition magic from windows to reduce your ntfs partition's size.

---

### Post by totakad on 2008-04-20
i have defragmented the hd several times already, this can't be the problem. i'm going to try reducing the ntfs partition's size from the partition magic in windows.

pumalite- tried it. booting from the cd just took me to some kind of a grub command line. if that was the thing that was supposed to happen then i'm too weak for doing things you said in that thingy.

---

### Post by man_bash on 2008-04-20
Defragmenting simply puts files on NTFS partition in relative order. It will be simpler to resize with partition magic or any other partitioner, but it will not make you a partition. Do try using Partition Magic - I have had good results with that in the past.

---

### Post by Pumalite on 2008-04-20
Use the Partition Manager in the Live CD then. Partition Magic and Ubuntu don't get along very well.

---

### Post by totakad on 2008-04-20
pumalite i told already that the partition manager in the live cd doesn't work. it doesnt let me change the size of the main partition. THAT is the main problem as said before :(

and i'm just going to shrink the main partition and ubuntu live cd will make new ones for itself on the unallocated space

edit: and looks like the partition magic demo doesnt let me to resize it also. just says that it is a demo version, but that shouldn't be the problem. probably just blocks me again from resizing it or something.
im getting confused :S :(

---

### Post by Pumalite on 2008-04-20
Post a screen shot of Gparted.

---

### Post by totakad on 2008-04-20
there is of course another way i think. the windows on that laptop is quite fresh (doesnt have almost anything important on it) so i could reinstall windows and when making a partition for windows, then only use 25gb from the 40gb for windows and then maybe ubuntu can settle down in that free area?

---

