---
title: "Please help with Dual Booting"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by LinuxNewb092 on 2007-10-18
Hey guys, I want to dual boot my machine that has Windows XP and openSUSE on it.  I went to the installer and Im a newb to linux so I always go with the guided.  But the only option for using guided was taking up all the space.  Can someone help me with this.  I want to delete all the openSUSE partitions and create them for Ubuntu.  Please help.

Thanks in advance,
LN

---

### Post by Sef on 2007-10-18
Are you using the Live CD?  There should be an option for a manual install.  If not, then download the [alternate cd]("http://users.bigpond.net.au/hermanzone/") and use that to install.

---

### Post by LinuxNewb092 on 2007-10-18
Im using Live.  Yes there is an option for manual install but I dont know how to set up the partitions.  For example, I dont know how big the Root and Swap have to be.  I dont want to make them too small.

---

### Post by retrow on 2007-10-18
> **LinuxNewb092 said:**
>  I want to delete all the openSUSE partitions and create them for Ubuntu

When you reach the partition stage, go for manual instead of guided. In the listing you would see your disk partitioned with either FAT32/NTFS or reiserFS or ext3 or swap. Right click on the swap space and say delete. Do the same thing for the other linux partition (i.e. one that [COLOR="Red"]DOES NOT[/COLOR] say FAT32 or NTFS). No you would see free space in the partition list. At this point you can create ~1GB of swap space and use the remainder of the free space for root. (Specify / as the mount point).

I am not much experienced in this stuff myself, but this is what I did. If anyone else can suggest a better method, go with it.

---

### Post by LinuxNewb092 on 2007-10-18
Ok, and it worked fine for you?

---

### Post by Whiffle on 2007-10-18
How much space are we talking here?  I would suggest dividing up the remainder of the space into 1GB or so for swap, 10-15 for /  and the rest for /home.  Makes it much easier in the future if you reinstall and such.

---

### Post by LinuxNewb092 on 2007-10-18
40G HD with WinXP and openSUSE(want to get rid of this).

---

### Post by Whiffle on 2007-10-18
I think I'd do 12 GB for /, 1 GB for swap, and the rest for /home, and then whatever windows is already taking up.  My full install of ubuntu takes up 7.78 GB right now on my desktop, including pretty much all the software I need and everything.  12 should be plenty of room.

---

