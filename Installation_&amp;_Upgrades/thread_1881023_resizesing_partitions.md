---
title: "resizesing partitions"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by gabrielaca on 2011-11-14
i want to resize my partitions using Gparted, as a matter of fact, slim down Win and enlarge Ubuntu; i can allocate space in the win partition but (see screenshot, the sda5 partition grow to 216Gb) but i read that i have to Unmount the Ubuntu partition first in order to resize it unto the unallocated space, is this rigth? is there any risk to lose my data?

---

### Post by drs305 on 2011-11-14
The Ubuntu partition must be unmounted before it can be resized, so you need to boot a System Rescue CD, Gparted CD, etc so you can do so.

Here is a guide on expanding /. Also take a look at the bottom of the first post in that guide for a link to a good discussion by forum member *srs5694*

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by darkod on 2011-11-14
Another option that can save you burning a new cd is using your (k)ubuntu cd and booting into Try Ubuntu (live mode).
That doesn't mount /, it only uses the swap partition if there is any on the disk, but in Gparted you just right click it and do Swapoff and it's unmounted. You can work with the disk fully afterwards.

---

### Post by gabrielaca on 2011-11-14
thanks so much, i'll read the post you mentioned, and try it out later tonite, again thanks to both of you.

---

### Post by drs305 on 2011-11-14
I don't know why I didn't mention the LiveCD, which would be the logical choice to boot. I guess I type that so often I just forgot...  ](*,)

But at least it's covered in the guide.

---

### Post by gabrielaca on 2011-11-14
yes it does, i just started reading, im at work right now, so a little later to try it.

---

### Post by Mark Phelps on 2011-11-15
Any time you mess with partitions, there is a risk of losing data -- but using GParted to resize the Linux partitions should work fine.

Also, be aware that GParted does it all twice -- once for simulation, a second time for real. So, be prepared to wait for quite a while for it to finish -- and do NOT interrupt it or shut down the PC until it is done.  Doing so will leave your partitions in a bad state.

---

### Post by gabrielaca on 2011-11-15
thanks Mark, i postponed this for the weekend, so i have plenty of time to read and prepare my backups and all, thank you guys.

---

