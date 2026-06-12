---
title: "Partition Oddity"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by kayners on 2005-06-15
Hi folks,

I installed Kubuntu on my lunch hour and encountered a little problem with partitioning. I was installing over a Mandrake 10.1 install, where I had the following partitions:

/ = 6GB
swap = 1GB
/home = 112GB

I tried to reuse the existing partitions, but when I went in to configure them, they were marked "Can not use" or "Do Not Use." No keys would change that status, so I had to blow that away and go with the default of / = 118GB and swap = 1GB (IIRC).

Is it possible to reuse partitions, or to specify a custom scheme?

TIA, Steve.

---

### Post by alastair on 2005-06-15
Yes - you can re-use - but you would need to make new filesystems on the "system" partitions i.e. / etc.

You can also re-partition any way you want.

Not sure why it didn't work for you.

---

### Post by kayners on 2005-06-15
Thanks for the response.

I'll go back and try it again, from the beginning.

Steve.

---

### Post by kayners on 2005-06-16
OK, for anyone who's reading this with a similar problem:

When I was in the installer, working with partitioning, I was seeing the selected partition marked "Do not use." With this line highlighted (selected), all I had to do was hit Return to see the other choices. I previously tried PageUp, PageDown, UpArrow, down, left, right, wleirjvw;lkdjv, and none of that works.

Just hit Return to see the choices.

Revealing my cluelessness to save the masses.

Steve.

---

### Post by bloodpuppy on 2005-06-16
6 GB for root. isn't that a lot? I thought you only need about 200mb.

---

### Post by blind0wl on 2005-06-17
Depends on what you want and where you install things. In my experience, root needs to be quite large so i can install and uninstall all the things I want in their default areas.  If you have a specific function for your install and only require a couple of services, then I assume 200mb will be fine (as long as Ubuntu actually fits into 200mb,which I doubt).  I like to keep things simple, with either a small /boot partition, swap partition and the rest is /.

---

### Post by afonic on 2005-06-17
[QUOTE=bloodpuppy]6 GB for root. isn't that a lot? I thought you only need about 200mb.[/QUOTE]
 If you just create / and /home then all other folders go to / no?

I mean /usr, /etc, /var and more. If that is the case then you'll need more space in / than /home.

---

