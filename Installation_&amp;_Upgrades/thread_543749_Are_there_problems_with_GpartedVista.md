---
title: "Are there problems with Gparted/Vista?"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by keithk50 on 2007-09-05
Hi,   I have bought a new laptop which came with Vista Premium pre-installed.   Ran the 7.04 live CD which seemed to tick all the boxes in regard to sound, network card etc.   After running Ubuntu on my old laptop, dual with XP, I really did enjoy it.   Now, before I install on the new laptap, I have read a few posts stating that Gparted is not working properly with Vista!
Is there a problem or can I use Gparted to partition my HD prior to clicking the big install button from the live CD.   To be honest it has put me off from installing since reading the posts.   Perhaps I should wait until 7.10 appears in the next couple of months?   Any advice/guidance would be appreciated.:)

---

### Post by merlinus on 2007-09-05
Before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

Also, use vista's disk manager to resize its partition.

-merlin

---

### Post by keithk50 on 2007-09-05
Thanks merlinus.   Sorry to ask but where is 'disk manager' in vista?   Only had the laptop a couple of days and cant wait to get Ubuntu up and running again.   Thanks again

---

### Post by merlinus on 2007-09-05
Maybe in System Tools/Advanced, or something like that?  You can probably look in Help to locate it.

-merlin

---

### Post by keithk50 on 2007-09-05
Thanks again.   Found it.   'Shrinking' the HD looks pretty staightforward.   I am going to give it a go.   Do you think I should leave the new partition 'unallocated' in order to install Ubuntu from the live cd?   Thanks.

---

### Post by merlinus on 2007-09-05
Ubuntu cannot use unallocated space.  You can format it as fat32.

Then during install you can format it as ext3.

Also, best to follow my suggestions posted earlier before shrinking the vista partition.  It will give you more space for ubuntu.

-merlin

---

### Post by keithk50 on 2007-09-05
Thanks again.   Your help is appreciated.

Keithk50

---

### Post by merlinus on 2007-09-05
You are most welcome, and good luck with installing.

Be sure to back up data!

Let us know how it goes.

-merlin

---

### Post by robotii on 2007-09-05
It looks like the vista partition resizer will not shrink the partition below 50%. Anyone know of a way to get more free space for ubuntu, without reinstalling vista?

---

### Post by merlinus on 2007-09-05
Delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

-merlin

---

