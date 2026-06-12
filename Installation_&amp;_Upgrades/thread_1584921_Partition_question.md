---
title: "Partition question"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by OperatorA on 2010-09-29
I got a grandson got loose and installed something called "Limewire" on my PC. I had it Dual Booted with WindowsXP & Ubuntu. 
Limewire made such a mess I decided to "Restore" the area that Ubuntu sat on disappeared and my C: drive was smaller by the part that Ubuntu occupied. I ran GParted and restored the Linux partitions to NTSF with no problems. Question is now how do i make my NTSF main (Windows) partition take the whole drive and wipe out the smaller NTSF partitions. I can't find Info at GParted site on how to do that and it is NOT in the GParted help files (there aren't any)

[Part 2]

If I decide for reasons of easy installs to keep the smaller NTSF partition and do a wubi install, will wubi install in that smaller partition and will wubi give me a choice of partitions.

Some day after I feel real comfortable running Linux i WILL format the drive as one big "C:\" drive then split it up into at least to 50% size partitions and do a full install of Ubuntu.
Os on one C:\, "documents" (papers, pictures, music etc.) on the other one.

---

### Post by mikewhatever on 2010-10-01
> **OperatorA said:**
> I got a grandson got loose and installed something called "Limewire" on my PC. I had it Dual Booted with WindowsXP & Ubuntu. 
Limewire made such a mess I decided to "Restore" the area that Ubuntu sat on disappeared and my C: drive was smaller by the part that Ubuntu occupied. I ran GParted and restored the Linux partitions to NTSF with no problems. Question is now how do i make my NTSF main (Windows) partition take the whole drive and wipe out the smaller NTSF partitions. I can't find Info at GParted site on how to do that and it is NOT in the GParted help files (there aren't any)

Gparted has an option of resizing partitions. First delete the partition you created, then right click the Windows partition and select 'Resize'. Drag the partition edge to fill the unallocated space.
[Part 2]

> If I decide for reasons of easy installs to keep the smaller NTSF partition and do a wubi install, will wubi install in that smaller partition and will wubi give me a choice of partitions.

It should, but read [wubi FAQ]("http://wubi-installer.org/faq.php") to be sure.

---

### Post by OperatorA on 2010-10-01
Thanks for the info Mike...this is what I LIKE about UBUNTU...all the friendly help givers in the forums...you're a great bunch of gals & guys...If we all pull together we can conquer the world...for Linux...LOL

I have done two "wubi" installs on older computers of 10.4.1 LTS and all went smoothly. I put it on my son in laws cobbed together PC (Pentium 4 & 512MB of RAM, 30GB hard drive)no problems...(his son screwed up a wubi install) I just cleared out the wubi & *.iso from my documents, ran REVO Uninstaller, downloaded a new wubi and ran it. Same for my daughter Lora's PC a $20.00 yard sale special with a 2.2GhZ CPU, & a 100MB hard drive & 768MB of RAM. (1 - 512MB stick & 1 256MB stick) Ubuntu runs like a Jet on her PC.

So That is 5 PCs I know of in the area running Ubuntu. My son in law has a co-worker running it, and I have a co-worker running it. Including me, 3 in my family. We ate the "unofficial" Linux group in Scott County we are SLUGs (Scottsburg Linux Users Group or LOGS - Linus Users Group of Scottsburg) ... I know...go get another cup of coffee...LOL

Once again thank you one and all...
Larry in Scottsburg Indiana, USA
(Mark this thread as resolved...)

---

### Post by mikewhatever on 2010-10-01
You are welcome, Operator. To mark the thread as 'Solved', click the 'Thread Tools' above your first post.

---

### Post by OperatorA on 2010-10-01
I really don't know why I took to long to really use Linux except I bought a book back in the early 2000s "Red Hat Linux for Dummies" that had an early version of Red Hat in it and it left a NASTY taste in my mouth...LOL...I/E an aversion to Linux...
Ubuntu cured that...thank you Ubuntu development team....

Larry

---

