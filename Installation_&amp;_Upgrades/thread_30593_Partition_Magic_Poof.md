---
title: "Partition Magic Poof"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by momo66 on 2005-04-29
I know this is not really a Ubuntu ? but its where Im starting.  I installed Ubuntu without trouble on my PC at work using Partition Magic to partition the drive.

Now at home Im using PM as well to partition the drive and it will not let me.  I go through the process of resizing the partition to create one for Ubuntu but when I go to apply the change it beeps and goes back to what the previous settings were.  I have tried numerous things including defragging the drive. 

Any ideas would be appreciated.

---

### Post by defkewl on 2005-04-29
Have you made logical drive?

---

### Post by momo66 on 2005-04-29
[QUOTE=defkewl]Have you made logical drive?[/QUOTE]
 Thats what I keep trying to do but it will not let me apply the change.

---

### Post by momo66 on 2005-04-29
[QUOTE=momo66]Thats what I keep trying to do but it will not let me apply the change.[/QUOTE]
After running chkdsk, I was able to partition my drive using the Linux based [SystemRescueCD](http://www.sysresccd.org/)  and [QTparted](http://qtparted.sourceforge.net/) .   I now have Ubuntu running at home and work. :)

---

### Post by 23meg on 2005-04-29
qtparted is so cool. i keep advising people to just run it off any linux live cd instead of buying and using partition magic.

by the way, resizing partitions with partition magic isn't a good idea. version 8 once rendered all my filenames to illegible characters and killed a whole other partition while trying to resize; fortunately i had backups. anyone who absolutely has to use it: make sure you have backups!

---

### Post by Jenda on 2005-04-30
Does the Ubuntu LiveCD have QT? And is it safe to resize a win2k partition with it?

---

### Post by jodef on 2005-04-30
> **23meg]qtparted is so cool. i keep advising people to just run it off any linux live cd instead of buying and using partition magic.

by the way, resizing partitions with partition magic isn't a good idea. version 8 once rendered all my filenames to illegible characters and killed a whole other partition while trying to resize said:**
> 

AMEN!! that's the gospel truth DO NOT USE PARTITION MAGIC with Linux partitions. 

[QUOTE]Does the Ubuntu LiveCD have QT? And is it safe to resize a win2k partition with it? I have resized every partition imaginable with qtparted w/out a single problem but as a general caution resizing can cause data loss so always backup your data.

---

