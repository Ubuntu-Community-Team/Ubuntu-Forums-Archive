---
title: "Partitioning Tips?"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by jrich1516 on 2008-10-25
I want to dual boot WinXP and Ubuntu on my Toshiba Tecra M2.  It has a 60 GB HD and 2 GB of RAM.  Right now the whole thing is one partition in NTFS.  I want to use a maximum total of 20 GB for Ubuntu.  If I were to partition it using GParted, what sizes should I use for the Ubuntu partition?  What is a swap partition, do I need one, and what size should it be?  Thanks!

P.S What should i do to prepare my HD to have its paritions edited?

---

### Post by bulldog on 2008-10-25
You can use the GParted live cd to make new partitions on your hdd or just use a live ubuntu cd.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Swap will be used when the fysical memory is been used,to avoid problems,make a small partition for it.
I recommend a partition for /  [system] about 10GB
A swap 1-2GB and make the rest an ext3 partition for /home.
In case of a reinstall of ubuntu you can just mount your /home again and won't loose your data.

---

### Post by Idefix82 on 2008-10-25
With only 20 GB to play with I would agree with bulldog. One more tip: before partitioning, defragment your NTFS partition.

If you upgrade your HD at some point or throw microsoft out of the window then you may want to create more partitions like /usr, /var, /tmp and maybe some others. But with the limited space that you have it's probably not worth it.

---

### Post by jrich1516 on 2008-10-25
so it should be:
40 gb for windows
10 gb for /system (this is the os, i presume?)
2 gb for swap
8 gb for /home (this is my files, right?)

what is ext3?  is it like ntfs?

---

### Post by bulldog on 2008-10-25
ext3 is a file system like NTFS for windows or even FAT32.
And yes, you understand perfectly what I said about partitioning.
You can make a swap sized 1GB instead of two, but that's a minor issue.

---

### Post by jrich1516 on 2008-10-25
how would just change my my documents (or whatever they call it) to the 8 gb partition?  and then programs would reside on the /system partition?  how do i set this up in the ubuntu installer?

---

### Post by Idefix82 on 2008-10-25
You should choose the mount points to be 
SWAP, /home and /
There is no /system, the whole file system is mounted under /.
When you go through the install procedure you can choose the option "manual install" and then specify the mount points and the allocated space as we have discussed. You can resize the Windows partition while installing Ubuntu but it might be easier to do it before you start installing.

---

### Post by jrich1516 on 2008-10-25
defragging right now

---

### Post by jrich1516 on 2008-10-26
so the /home is partitioned in ext3?  what are the swap and / partitioned in?  can i make /home in ntfs so winxp can read it?

---

### Post by bulldog on 2008-10-26
/home is formatted ext3
/ is formatted ext3
swap is formatted as swap

No,you can't make your /home NTFS.
There is a plugin however,when installed in winxp,makes windows read your ext3 filesystem.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jrich1516 on 2008-10-26
and are these all primary partitions?

---

### Post by bulldog on 2008-10-26
It's your choice.
Windows needs to be installed on a primary,ubuntu doesn't care if it's on a primary or a logical.

---

### Post by jrich1516 on 2008-10-26
damn it, it got an error.  it says it saved a details report in a /root folder but i can't find it in windows explorer.  not only does gparted have a hard time with my hd, so does the ubuntu partitioner and driveimage xml, a program that backs up your drive image.  how do i access the details log?

---

### Post by sethvath on 2008-10-26
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

might help.

---

### Post by jrich1516 on 2008-10-26
i kno what i want to do, but i get an error with gparted and i don't know where the detail log went.  the gparted live-cd saved it in a /root folder somewhere

---

