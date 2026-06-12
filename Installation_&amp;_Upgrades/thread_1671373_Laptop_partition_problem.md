---
title: "Laptop partition problem"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by whaase on 2011-01-19
I shrunk a win 7 partition, made a 100 gig empty partition
For ubuntu. When I boot the ubuntu install DVD all it sees as
The total size of the drive, it doesnt see the partitions on it.

What am I doing wrong?

---

### Post by Bucky Ball on 2011-01-19
When you get to the partitioning section of the install are you choosing 'Manual partitioning'? That should show you all partitions. Install onto the free space.

/ = OS, 20Gb plenty
/home = your personal data and settings, big as you like
/swap = 2Gb or as big as your RAM if you intend hibernation.

---

### Post by Quackers on 2011-01-19
How many primary partitions exist on the hard drive?

---

### Post by whaase on 2011-01-20
The drive is a 500 gig. I have the 20MB partition that Win 7
Requires. Then I have a 368 gig partition for Win 7, and a 97 gig unallocated
Space for ubuntu I want to use. When I boot the install DVD, I've tried every option
To use the 97 gig space, but the installer only see's the 500 gig drive, no partitions.

Very weird. I've installed Linux of every flavor 100's of times over the years, including Gentoo and never run into this?

---

### Post by dino99 on 2011-01-20
that might help:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by srs5694 on 2011-01-20
I think the other posters are all on the wrong track. If I'm understanding correctly, the installer is telling you there are *no current partitions* on the disk, when in fact there are. If so, you should ***not*** go ahead with the install; that will *trash* your existing Windows installation!

If I'm correct, then there are several possible causes of this problem. I've got a [Web page devoted to one of them,](http://www.rodsbooks.com/missing-parts/index.html) including a procedure to fix it. I recommend you read that Web page. If you can follow it and it solves your problem, then great. If you need more help, then please post back with the output of the following command, typed at a text-mode terminal prompt from the Ubuntu installer's live CD mode:

```

sudo fdisk -lu

```

Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

