---
title: "Multiple Ubuntu 10.04 Installation Problems"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by DJ-HLS on 2010-09-27
Hi, I'm basically a complete noob to Linux, but I know enough about Windows and OSX and hardware and what not.

So first things first.  To be blunt, the HDD in the PC I'm trying to install 10.04 on won't let any file systems be created on it.  I've created the partitions and everything, but every time it gets to the final part of the installation where it tries to create a file system, it always fails at 5%.  I've been through all of the ext's and the reiserFS just failed too.  This thread: [http://ubuntuforums.org/showthread.php?t=1270595](http://ubuntuforums.org/showthread.php?t=1270595) is basically the same problem as me, but it's on a different version of Ubuntu and it was never solved.

And on top of all the file system errors, the entire installation process is EXTREMELY slow.  It takes at very least around 15-20 minutes to get through one step in the install prompts. It's been almost 40 minutes since I pushed the back button from step 6 to try another file system, and still it just sits.  I mean everything else is responsive, I can move the mouse around with great responsiveness and buttons flash up when I move the cursor over them, so the machine is by no means frozen.

If there is another thread that will help me with this, then please redirect me, but I've been searching on here and on Google for quite a while and I can't find anything that seems to help.

Thanks in advance!
-Alex

---

### Post by wojox on 2010-09-27
How much memory do you have in this system? Sounds like an old machine.

---

### Post by DJ-HLS on 2010-09-27
Yea, it is pretty old, although it does have surprisingly fast stats for its age, which is why I'm wondering why it's so slow.

Dell Dimension 4600
3.4GHz Pentium 4 w/ HyperThreading
2GB RAM
80GB HDD
512MB PCI Nvidia Graphics card (dunno exactly which)

---

### Post by wojox on 2010-09-28
> **DJ-HLS said:**
> Yea, it is pretty old, although it does have surprisingly fast stats for its age, which is why I'm wondering why it's so slow.

Dell Dimension 4600
3.4GHz Pentium 4 w/ HyperThreading
2GB RAM
80GB HDD
512MB PCI Nvidia Graphics card (dunno exactly which)

Yeah those specs are pretty sufficient. Have you tried running the memory test on it?

---

### Post by DJ-HLS on 2010-09-28
OK, for some reason the XFS file system was successful and the installation finished.  Should I continue to use this file system? I'm only planning to use this PC in a youth room in a church for stuff like web browsing and what not.

-Alex

---

### Post by wojox on 2010-10-01
> **DJ-HLS said:**
> OK, for some reason the XFS file system was successful and the installation finished.  Should I continue to use this file system? I'm only planning to use this PC in a youth room in a church for stuff like web browsing and what not.

-Alex

Sure, don't see why not.

---

