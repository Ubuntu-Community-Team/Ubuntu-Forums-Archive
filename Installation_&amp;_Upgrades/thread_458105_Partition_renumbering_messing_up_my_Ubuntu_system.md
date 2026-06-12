---
title: "Partition renumbering messing up my Ubuntu system"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by RCC2k7 on 2007-05-29
First, this is my current hard drive configuration:

sda1 - 60GB - NTFS - Windows XP Professional
sda2  - 35GB - NTFS - Windows Vista Ultimate
sda3 - Extended Partition
sda5 - 3GB - Linux Swap
sda6 - 60GB - ReiserFS - PCLinuxOS 2007
sda7 - 60GB - Ext3 - Ubuntu 7.04
sda8 - 247GB - NTFS - data partition

Other than the fact sda4 is missing (I have no idea why) this partition numbering scheme actually matches the physical order the partitions appear on the disk. Now, here's the problem:

Back when I first installed Ubuntu 7.04 my data partition was 30GB smaller and I had Xandros 4.1 installed too. At that time, Xandros had sda9 at the end of the disk but for some reason, mysterious to me, _what is now sda7 (Ubuntu) was sda8 and what is sda8 (NTFS data) was then sda7_. When I deleted the Xandros sda9 partition and resized my NTFS data partition to fill the gap, all of a sudden the partition numbering change to what it is now. (sda7 and sda8 swapped places.)

This means I had a momentary crisis with Ubuntu -  it wouldn't boot because it was trying to load from sda8, which had actually been turned into sda7. I also had problems accessing my NTFS data partition because it was originally sda7 but then shifted to sda8.

Don't ask me why this happened. The case is, I modified Ubuntu's menu.lst file to load from what is now sda7 (hd0,6) and modified the fstab for both of my Linux OS's to reflect the sda7-sda8 swapping. Everything was fine and dandy until last night, when I downloaded a kernel update posted for Ubuntu. Ubuntu modified the menu.lst to add the new kernel entries, but it modified the file based on the original assumption that it was installed to sda8 and not sda7. You probably know what happened next...

What do I need to modify in Ubuntu so that future kernel updates don't leave me with an unbootable Ubuntu? How do I make Ubuntu know that from now on sda7 is its partition and not the original sda8, without having to reinstall?

---

### Post by Jussi Kukkonen on 2007-05-29
You have probably misunderstood how to edit menu.lst. Please see this thread: [http://ubuntuforums.org/showthread.php?t=457135](http://ubuntuforums.org/showthread.php?t=457135)

---

### Post by RCC2k7 on 2007-05-29
So basically, by changing that groot line from hd0,7 to hd0,6 I should avoid problems the next time I install a kernel update?

---

### Post by merlinus on 2007-05-29
Definitely don't bet on it!!!

But you can press e at the grub screen, and change the root from there.

This happened to me when I upgraded to the 16- kernel.  And if you do upgrade, if you have IDE drives it will change them from sd's to hd's, so you will have to edit a couple of files as well.

-merlin

---

### Post by LarsBjerregaard on 2007-05-29
Sounds like you've been bitten by this: [http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662) like a lot of other people. Please consider my suggestion on: [http://ubuntuforums.org/showpost.php?p=2744328&postcount=194](http://ubuntuforums.org/showpost.php?p=2744328&postcount=194)

Good luck

---

### Post by Jussi Kukkonen on 2007-05-29
> **RCC2k7 said:**
> So basically, by changing that groot line from hd0,7 to hd0,6 I should avoid problems the next time I install a kernel update?
That should do it, but remember to run "sudo update-grub" after you've set the groot variable and then check if the file got updated correctly.

---

### Post by Mike_ on 2007-06-11
> **merlinus said:**
> Definitely don't bet on it!!!

But you can press e at the grub screen, and change the root from there.

This happened to me when I upgraded to the 16- kernel.  And if you do upgrade, if you have IDE drives it will change them from sd's to hd's, so you will have to edit a couple of files as well.

-merlin

Good lord, I am 3 for 3 on menu.lst being changed after an upgrade. Is it possible to change the file permissions to not allow the system to jack with the file until the issue is fixed?

---

