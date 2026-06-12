---
title: "Upgrade from 6.06 to 6.10 Error"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by golf22r on 2006-11-23
I would like to completely remove Ubuntu 6.06 from my computer and install  Ubuntu l6.10.  I made two live Cd's of 6.10 from two different mirrors using the direction from the Ubuntu website.  During installation it says to select the partition on which to mount each part,  I select my 33 gig primary partition for the root, it is the same partition I have 6.06 (I selected / from the drop down list), and my 1 gig primary partition for the swap.  I selected format for each.  When I click forward it says in the bottom left of the page "No Root".  Can Somebody please help me?  Thank you!

---

### Post by taurus on 2006-11-23
Perhaps you should try to install Edgy by using the alternate CD instead of the LiveCD...  It can handle the partition part a little better than the LiveCD.

---

### Post by celem on 2006-11-23
FYI: I just finished an on-line update from dapper to Edgy Eft. All went well until near the end. I had two errors. One with SAMBA and the second with firestarter. The SAMBA error resolved itself but the firestarter problem was tough to cure. I finally did a apt-get -purge remove, then a "locate firestarter", and saved the output to a file, added a "rm " to the front of each line and executed it. Then when I re-did a apt-get install firestarter it worked. All previous attempts of apt-get install  or remove firestarter failed. All is well at last. I tested SAMBA and it works well.

---

### Post by golf22r on 2006-11-28
Successful Installation! Thank you!

---

