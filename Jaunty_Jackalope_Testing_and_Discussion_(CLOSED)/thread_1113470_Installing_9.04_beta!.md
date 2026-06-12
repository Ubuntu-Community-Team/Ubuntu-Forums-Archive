---
title: "Installing 9.04 beta?!"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Teatro on 2009-04-01
Okay, I decided to install 9.04 beta to solve my slow boot problem with 8.10. I have downloaded the file, made a dvd, booted from the live disk and am prepared to install- but...

I have windows xp, which I need, already installed. Apparently the XP install also creates a small Windows 2000 partition. Then I have the Ubuntu 8.10 partition and a linux swap partition. The 9.04 installer seems to want to resize all the partitions instead of just installing to the existing 8.10 partition- or am I choosing the wrong installation scheme? 
I don't want to use the entire disk. but when I choose 'Install them side by side, choosing between each startup, it still shows an 8.10 partition (which, together with the 9.04 partition and the windows partitions add up to 132% of the hard drive. When I press 'forward' from that screen, it pops up a warning that 'before you can select a new partitions size, any previous changes have to be written to disk. You cannot undo this poeration'  How do I just install 9.04 in the 8.10 partition without resizing anything?

---

### Post by anjilslaire on 2009-04-01
Choose Manual Partition, then point it to install in the 8.10 partition.

---

### Post by Teatro on 2009-04-01
> **anjilslaire said:**
> Choose Manual Partition, then point it to install in the 8.10 partition.

Thanks- that makes so much sense now that you point it out...

---

### Post by Teatro on 2009-04-01
Okay, I did that, and it shows me a list of partitions, but when I highlite the 8.10 partition, I can apparently either edit or delete, or undo changes to partitions- which am I doing? I highlited the 8.10 partition and tried 'forward', but it told me no file system was defined...

---

### Post by bodhi.zazen on 2009-04-01
most common reason is that your  swap partition is mounted.

Un mount that first.

---

### Post by Teatro on 2009-04-01
> **bodhi.zazen said:**
> most common reason is that your  swap partition is mounted.

Un mount that first.

I will, as soon as I find out how- how do I do that?

---

### Post by Sef on 2009-04-01
Moved to Jaunty Forum.

---

### Post by Teatro on 2009-04-01
okay

---

### Post by Bölvaður on 2009-04-01
> **Teatro said:**
> Okay, I did that, and it shows me a list of partitions, but when I highlite the 8.10 partition, I can apparently either edit or delete, or undo changes to partitions- which am I doing? 



I think it is that you press edit and then mount point to /
Becomes so instinctive how to do it that we forget :( But my bet is on edit.

---

### Post by Teatro on 2009-04-01
> **Bölvaður said:**
> I think it is that you press edit and then mount point to /
Becomes so instinctive how to do it that we forget :( But my bet is on edit.

I can't find anything quite like that- but it does allow me to choose 'don't use this partition' Is that the same as un mounting?

---

### Post by ptn107 on 2009-04-01
The previous post is correct.  When you manually partition mount points are not defined by default.  You must add each one in turn.  I'm guessing this is for our safety.

---

### Post by Teatro on 2009-04-01
Well, I seem to be in over my head then, because I have no idea how to manually install a mount point. Sounds dangerous.  I must say that the upgrade system seems to require more expertise than it should.

---

### Post by andrewabc on 2009-04-01
When I manual partition, I'm pretty sure you would have to delete your 8.10 partition, then create a new partition from that free space, format it and mount as /

---

### Post by Eestlane on 2009-04-01
There's not need to delete it, just format it as ext4 or ext3

---

### Post by Teatro on 2009-04-02
> **Eestlane said:**
> There's not need to delete it, just format it as ext4 or ext3

Okay, I've had some sleep, ready to tackle this again. Thanks, Eest lane- I'll give it a shot.

---

### Post by robert.rankin.jr on 2009-04-02
The simplest way to upgrade would be pressing alt+f2 and typing 'update-manager -d', then hitting return; then, when it asks, select distribution upgrade.

However, if you want a fresh install, just follow the previous poster's directions. When you're partitioning manually, choose to edit the partition (not sure on the exact words). Where it says "Format this partition", check the box; Where it says "Use as," "Mount as," or something along those lines, type /. Then press okay. Then, do the same with your old swap partition, but use it as swapspace.

Robert

---

### Post by Teatro on 2009-04-02
> **robert.rankin.jr said:**
> The simplest way to upgrade would be pressing alt+f2 and typing 'update-manager -d', then hitting return; then, when it asks, select distribution upgrade.

However, if you want a fresh install, just follow the previous poster's directions. When you're partitioning manually, choose to edit the partition (not sure on the exact words). Where it says "Format this partition", check the box; Where it says "Use as," "Mount as," or something along those lines, type /. Then press okay. Then, do the same with your old swap partition, but use it as swapspace.

Robert

I would do this during boot? (alt+f2) If so, from the 8.10 install or from the 9.04 live disk?

---

