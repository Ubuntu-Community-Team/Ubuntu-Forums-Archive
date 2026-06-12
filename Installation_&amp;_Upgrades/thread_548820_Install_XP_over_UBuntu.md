---
title: "Install XP over UBuntu"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by mikecomua on 2007-09-11
Hello, I am horribly ashamed of this, but I HAVE to install Xp on my machine over Ubuntu, so how do I do it? How do I partition my ext3 partition?

---

### Post by Pumalite on 2007-09-11
Gparted. Resize partition (right click on partition>Menu>Resize)

---

### Post by mikecomua on 2007-09-11
I can't because the partition is hot!

---

### Post by mikecomua on 2007-09-11
Is there a way to emulate Xp on UBuntu for free?

---

### Post by Pumalite on 2007-09-11
This is new to me. What is a hot partition?

---

### Post by mikecomua on 2007-09-11
I mean it is mounted on UBuntu, because I am running it

---

### Post by Pumalite on 2007-09-11
Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

You boot from this CD, so your partition is not mounted.

---

### Post by bigguy on 2007-09-11
Can you not boot from the xp cd and wipe out all the partitions and install xp. I just did that last night and then removed it again for installing ubuntu sever.

---

### Post by mikecomua on 2007-09-11
How do I restore my data?

---

### Post by Pumalite on 2007-09-11
He asked to partition his hard drive, so I assumed dual booting.
If so, you can re-install Grub afterwards: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mikecomua on 2007-09-11
Will that restore my data? Is there a backup utility like Norton GHost for UBuntu?

---

### Post by Pumalite on 2007-09-11
What do you want to do?. Do you want to dual boot?.
If not, backup all your data to dvd's or an external hard drive.

---

### Post by mikecomua on 2007-09-11
Can you emulate Windows for free?

---

### Post by bigguy on 2007-09-11
Sorry mikecomua; I thought you wanted to erase everything and do it over.

---

### Post by mikecomua on 2007-09-11
I this is how it has to be...

---

### Post by mikecomua on 2007-09-11
OK, I'll just go kill my Ubuntu, And yeah Windows sux!

---

### Post by bigguy on 2007-09-11
If you want to do everything over. Reboot your system with the xp cd in and boot from that. When it asks you if you want to set up Windows say yes; agree to the licsense and proceed to wipe outthe partitions. Then install. 

Yes this will remove all your data unless you back it up first to cd or dvd.

---

### Post by trak87 on 2007-09-11
You can install XP in Linux but you need virtualization software like VirtualBox, Qemu, or VMWare. I've no experience with any of these, but people seem to like this technique as a solution. Here's a relevant thread: [http://ubuntuforums.org/showthread.php?t=276628](http://ubuntuforums.org/showthread.php?t=276628)

---

### Post by Long_Live_Linux on 2008-01-23
Ok, I have been wanting to do the same thing. Can I just pop in my Windows XP install CD into my Ubuntu machine, reboot, and then install XP?

---

### Post by Pumalite on 2008-01-23
I'm not a Windows user, but I doubt it. I think you need to get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it and delete everything in your hard drive. Then make a new large partition of your whole hard drive, formatted ntfs. Then install XP.

---

