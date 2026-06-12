---
title: "Kubuntu not playing nicely with Win7"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by tonymoloney on 2011-02-09
My daughter, who has been using Kubuntu for the past 3 years, has just bought a new laptop with Win7 Home Premium already installed.
She asked me to install Kubuntu 9.04 on it in dual-boot mode, something which I have had plenty of experience doing.

However, when I went to install it, at the Partition Manager screen, Kubuntu did not recognise that there was already another operating system installed on the machine.
Instead, it just gave me a choice of using the entire disk or manually partitioning it.

When I went to manually partition it, it showed 4 partitions: sda1 as 100Mb, Sda2 as 480Gb, sda3 as 100Mb and sda4 as 100Mb.
I assumed from the size and the ntfs format that sda2 was the Windows partion and resized it to 250Gb. However, the remainder of the partition was then shown as unusable and I could not format it. In fact, I couldn't even undo the new partitioning.

Can anyone offer me any help?

---

### Post by wilee-nilee on 2011-02-09
4 primary partitions is the maximum on one HD. You may have converted the partitions to dynamic, not sure of the fix. Is W7 still booting, if so open the disk manager and take a screen shot or confirm the partitions.

Post 6 in this thread has a possible fix for a converted disc to dynamic, back to basic.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10286110](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10286110)

---

### Post by tonymoloney on 2011-02-09
Yes, Win7 is still booting and running properly, although it had to do a disk check on the first boot.
My daughter has taken the computer home, so right now I can't get the screen shot.
She might leave it as it is, 'cos she has a desktop running Kubuntu.

---

