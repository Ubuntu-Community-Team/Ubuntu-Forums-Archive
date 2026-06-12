---
title: "Partition Magic"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by hacksign on 2005-11-21
Ok, I have 2 hdd (C: and D: both 80 gigabyte) and I wanted to partition hdd D: to install Ubuntu. I have few questions though:
1. Do I need to create it as Primary or Logical?
2. Does it have to be EXT2 or EXT3?
3. How much does the swap file need to be big?
4. Should I set the swapfile on hdd C: (were windows is installed) or hdd D:?

---

### Post by ofek on 2005-11-21
Swap should be on the hard drive where u gonna install ubuntu.
I use ubuntu on a primary partition i'm not sure if u could use it on logical (never tried).
Swap partition should be 2*[your ram].
Your partition can be ext2, ext3, reiserfs, reiser4, xfs and some others. I would suggest you to go for ext3 for the time being.

---

### Post by az on 2005-11-21
Partition magic may cause you problems.  Just use the Ubuntu installer and let it do the partitioning.  Make it free up some free space on your second drive and then let it do "guided partitioning' where it will figure out the sizes of the partitions for you.

---

### Post by az on 2005-11-21
[QUOTE=ofek]Swap should be on the same partition of ur ubuntu os..[/QUOTE]

No.  It can be anywhere and you can have several different ones at the same time.

---

### Post by ofek on 2005-11-21
I said "should" not "have to be". It just looks more logical to me.

---

### Post by hacksign on 2005-11-21
OK, so I'll use Ubuntu's partition configuration, and the swap file on D:. And, last question, If I want to uninstall Ubuntu, do I need to format Windows when I want to uninstall Ubuntu?

---

### Post by ofek on 2005-11-21
If you got 2 hard drives one for windows and one for ubuntu the eziest way to unistall ubuntu is just to format its hard drive. You don't need to format your windows hard drive.

---

### Post by hacksign on 2005-11-21
Ok, Thanks alot for your fast answers. I will install it and tell you if everything goes ok

---

### Post by az on 2005-11-21
[QUOTE=ofek]I said "should" not "have to be". It just looks more logical to me.[/QUOTE]
You can get a better performance if it is on another drive.

But you are right that it is a lot easier to just put everything on one drive.  And swapping is pretty slow so the performance gain is pretty much only theoretical.

---

