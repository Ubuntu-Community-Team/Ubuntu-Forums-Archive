---
title: "Resizing partitions problem"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by ninjaPants on 2006-02-21
I just got my laptop back from the service center, and in some stroke of genius they fixed my hardware problems by wiping the hard drive back to factory settings. 
Anyways, this gave me a low-risk opportunity to install Ubuntu in a dual boot situation. I followed the instructions at [http://www.hezardastan.org/breezy_xp_dualboot/en](http://www.hezardastan.org/breezy_xp_dualboot/en) to try to resize the existing partition and make new ones using the Gparted utility on the Ubuntu live CD. 
The problem is that I get errors in Gparted and end up with the same thing I started with. The NTFS partition returns to its original size, even when I do that by itself.
Am I doing something wrong? Should I delete all the partitions and start over for real?
Thanks in advance,
Andrew

---

### Post by renzokuken on 2006-02-21
i had this exact problem with qtparted and gparted. didnt manage to solve it though.

EDIT: i just read that guide and it seem like an overly complicated round-about way of doing it.

it would be easier to install windows over the whole drive. then boot the Ubuntu install cd and let the instalation wizard shrink the NTFS partition to make room for Ubuntu.

theres a guide round here somewhere.....i'll have a look

here it is.....

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by gerbman on 2006-02-21
[QUOTE=ninjaPants]The problem is that I get errors in Gparted and end up with the same thing I started with. The NTFS partition returns to its original size, even when I do that by itself.[/QUOTE]

In general, it is most helpful if you list all the errors you are getting and exactly what you were trying to do when you got them.

---

### Post by plors on 2006-02-21
please use the latest gparted on its own [livecd]("http://gparted.sourceforge.net/livecd.php"). It has far better progressfeedback then its predecessors.

---

### Post by ninjaPants on 2006-02-21
@plors - thank you, that worked out well.

I went ahead and defraged the drive from windows to start with, then used the standalone Gparted. Doing multiple operations failed, but doing them one by one worked like a charm. 

Sorry for the vagueness in the original post - all the error message I got was "operation failed while trying to create -drive-" so I excluded it until I was sure it wasn't just an ID10T error.

Thanks once again for a fast, useful and helpful response. Don't want to gush, but the quality of this community is what convinced me to continue using this distro of Linux.

Thanks all,
Andrew

---

### Post by jchau on 2006-02-22
If your install of Windows is still fresh & you have a restore CD / windows install CD, I would suggest wiping all partitions.  Then use install windows first, leaving some unpartitioned space for Ubuntu. (Be sure to install windows before Ubuntu; the windows install will mess up the Ubuntu boot, but the Ubuntu install should not mess up the Windows install).  

Then use the Ubuntu install cd to install on the unpartitioned space.  

That is the most straight-foward way.  There is no need to resize partitions if you can easily recreate them (less likely to wipe something important out of part of a partition).

---

### Post by dcstar on 2006-02-24
[QUOTE=jchau]
......
That is the most straight-foward way.  There is no need to resize partitions if you can easily recreate them (less likely to wipe something important out of part of a partition).[/QUOTE]
I just used a Knoppix Linux utility boot CD today that had qtparted on it, and it resized a NTFS partition fine for me.

It's a handy little utility that I will probably use again:

[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
[http://www.sysresccd.org/Index.en.php](http://www.sysresccd.org/Index.en.php)

---

### Post by arckeda on 2006-02-24
Same f*$(in problem, and i cant fix it can someone help?

---

### Post by arckeda on 2006-02-24
nvm im downloading stand alone cd now...

---

