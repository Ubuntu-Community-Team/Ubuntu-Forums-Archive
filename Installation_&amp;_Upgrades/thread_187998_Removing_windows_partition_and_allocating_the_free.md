---
title: "Removing windows partition and allocating the free space to my ubuntu partition?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Whimar on 2006-06-03
Hi there,

whats the best way about going of removing my windows partition and increasing the size of my ubuntu one to make use of the free space this creates.

any help in the matter would be greatly appreciated thanks!

---

### Post by John.Michael.Kane on 2006-06-03
You can try using gparted. however before doing so are you sure you ready to go with ubuntu only?

---

### Post by tonyr on 2006-06-03
Does **gparted** resize backwards (if the Wx partition is the first one)?
Here's the way one user approached it.  The steps may be a little different
for you.
[http://www.ubuntuforums.org/showthread.php?t=184426]("http://www.ubuntuforums.org/showthread.php?t=184426")

---

### Post by Whimar on 2006-06-03
[QUOTE=SD-Plissken]You can try using gparted. however before doing so are you sure you ready to go with ubuntu only?[/QUOTE]

Yah, i've played with linux on and off now for about 10 years? since roughly around redhat 4.

I tried gparted, but it didnt appear to support volume resizing, and i didnt want to nuke my windows partition without being to resize my ubuntu one.

I have windows installed in a VMWare VM for all the must have applications.

I used to use ranish partition manager for all my partition needs, but after one nasty write from the software i think im going to steer clear of it.

If anyone can comfirm that GParted does indeed support resizing then i will make the jump.  QTParted wouldnt even recognise my hard drive.

---

### Post by Whimar on 2006-06-03
Mhmm, Could i not boot a liveCD.

Delete the windows partition.

Copy the ubuntu partition to the beginning of the disk.

Delete the original ubuntu partition.

Then expand the copy intot he unused space?

---

### Post by tonyr on 2006-06-03
I think that is the gist of the thread I linked earlier.  The only caveat is be sure to have
a backup image of the ubuntu partition.

---

### Post by John.Michael.Kane on 2006-06-03
Whimar that could work. i know there are live-cd's that allow one to mount and manipulate hard drives and partitions. however i have never used them.

---

### Post by Whimar on 2006-06-03
well im copying and moving partitions as we speak.. wish me luck :) if it works ill let you all know today.  If it didnt ill let you all know tomorrow :P

---

### Post by tonyr on 2006-06-03
May the Force be With You!

---

### Post by Whimar on 2006-06-03
Ok that failed miserably.  So begins my fresh ubuntu installation. Argh! :P

---

### Post by Madvil on 2008-01-05
So, the only solution to that is to reinstall Ubuntu? Because I am facing right now the same problem : I got a hard drive dual-booting Ubuntu 7.10 and xp and I want to delete XP and make the remaining space part of the Ubuntu installation...

Any help accepted :guitar:

---

### Post by ugm6hr on 2008-01-05
> **Madvil said:**
> So, the only solution to that is to reinstall Ubuntu? Because I am facing right now the same problem : I got a hard drive dual-booting Ubuntu 7.10 and xp and I want to delete XP and make the remaining space part of the Ubuntu installation...

Any help accepted :guitar:

I don't see any problem with this, except if Ubuntu is not on the first partition (which is likely), then Grub will get totally messed up and you'll have to be able to manually reconfigure it.  Might be a bit scary though, since you intitially won't be able to boot after moving Ubuntu to ta different partition.

An easier, and perhaps better solution is to use the Windows partition as a separate /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

