---
title: "Weird installation errors"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by CorranSW on 2007-03-28
I have installed linux several times on my desktop....... I had to erase my partitions at one point because grub loader got messed up...... So i reinstalled windows and tryed to install linux again.... for some reason when i get to the instlal menu after booting from CD.... I get a couple messages like, decompressing kernal.... Success OK... loading...
And then i get this flashing underscore as if it has frozen... no i did wait at least 1 hour at one point to see if it was just takinig its time...
But no it just freez.... Ok next thought... maybe its the cd... so i download 6.10 again burn ISO image etc.... still... same error...
i try a different version like 6.6LT dapper.... Now this CD came out of a linux book a bought one week ago so i know the copy is good.... Still same error....
I really need help any inquiry would be greatly appreciated....

---

### Post by geojim55 on 2007-03-28
Corran,
After a week of trying to install the iso 6.10 image with stalls in the partitioning, I downloaded the 6.06 version and it worked.  I installed this on an old Compaq desktop with p3 processor and very little ram.  The 6.06 is also a live cd version and I used the Gnome partioner under System-  Administrative tasks and deleted previous partitions and made the disk a large linux swap file for the additional memory.  Anyway the 6.06 version worked for this older system while the newer 6.10 would hang at the partitioning.  This is new to me also, but so far is working, although a few bugs to work out.  Good Luck.
geojim55

P.S. forgot:  loaded the 6.06 as the live cd, partitioned, then did install.  waiting patiently for next screens till done.  Had a bad install and 2nd reload working.
P.S. 2: As a last follow up, I looked at the beginning of these threads and found the easy way to upgrade to 6.10 from the update script.  See the first post that gives the script you can copy and paste into the terminal program and go thru the update manager.

---

