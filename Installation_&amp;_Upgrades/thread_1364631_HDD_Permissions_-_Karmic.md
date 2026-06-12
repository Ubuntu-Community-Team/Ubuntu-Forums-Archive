---
title: "HDD Permissions - Karmic"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by nuffy on 2009-12-26
Recently did a fresh install of Karmic Koala after experiencing some problems with upgrades and I now cannot access my second HDD (old windows dve) that has all my data on it without entering my root password.

This is a problem as I use this drive as I said for all my data including t/bird profile.

I enter 'gksudo nautilus' in a terminal snd attempted to change permissions, but each time I change the 'File Access' permissions of the drive (as myself ) I see the dropdown box change back to '---'.

I have done hours of searching in vain for a solution and would appreciate anyone providing assistance.

Regards...nuffy

---

### Post by nerdtron on 2009-12-26
Is it a windows drive that you are trying to access? Can you mount the partition and is it formatted as NTFS? Try using the NTFS Configuration tool. I installed it using synaptic.

---

### Post by nuffy on 2009-12-26
Ahhh.... that did the trick thanks nerdtron.  Much appreciated!:)

---

### Post by nerdtron on 2009-12-26
You're welcome! I am happy that a newbie like me can share something. :-D

Note: If your problem is solved, please mark this thread as SOLVED using Thread Tools. Thanks!

---

