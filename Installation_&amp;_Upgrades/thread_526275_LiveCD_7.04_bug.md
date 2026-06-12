---
title: "LiveCD 7.04 bug?"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by derbouka on 2007-08-15
Hey!

I was trying to install ubuntu from the live CD, and when I choosed to resize the partition it asked me if I was sure that I wanted to partitioned that partition; I choosed Cancel and then it just block the installation process.

I have a screenshot of this ;)

---

### Post by derbouka on 2007-08-15
I can actually recreate this.. ;)

I'm attaching two screenshots:
- If I choose to "Go Back", it goes to the "Screenshot-2.png"

best regards

---

### Post by fredj on 2007-08-16
You are not giving it an option that it can work with. If you choose to resize the partition and then
cancel it at the confirmation screen then the installer doesn't know what to do next.
Give it a sensible choice if you want to proceed.

---

### Post by louieb on 2007-08-16
Yea probably, I've never liked the partitioner on the live CD.   Until it gets fixed  this is what i do. I use the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") to  partition and format the drive the way I want it. Then during the install I choose the manual partitioning  a use it to select the mount points for / (root) and /home.

---

### Post by stchman on 2007-08-16
> **derbouka said:**
> Hey!

I was trying to install ubuntu from the live CD, and when I choosed to resize the partition it asked me if I was sure that I wanted to partitioned that partition; I choosed Cancel and then it just block the installation process.

I have a screenshot of this ;)

Looks like your have a 60GB hdd?  If you want to partition it then try this method:

Using gparted on the LiveCD first erase the entire disc.

Create 30GB partition of free space at the front of the disc and create a 30GB partition formatted in EXT3 at the back of the disc.

When you install Ubuntu tell it to use the largest continuous free space.

---

