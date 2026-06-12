---
title: "How to extend ubuntu partition?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by mgiblets on 2010-08-12
having trouble trying to extend my ubuntu partition. I also have windows 7 on a dual boot, but for some reason the guy who I bought the laptop from decided to throw in an extra partition. I'm trying to merge this with my existing ubuntu one. Is this possible? If so, how?

Tired Gparted, but doesn't seem to work. This is how it looks at the moment;
 
84GB NTFS       -                           <Extended 236GB>
(Ubuntu)          -         118GB NTFS (windows 7)     +       118GB NTFS (unused)

     
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by presence1960 on 2010-08-12
From gparted Live CD/USB delete the unused NTFS partition. Click the Apply button (green check mark). Now right click the ubuntu partition and choose Move/Resize. grab the right corner of the ubuntu partition in the graphic with your mouse and move it to the right until you have added the desired amount of space. Click the resize button. Then click the green check mark.

You can't make changes to a mounted partition with gparted. So if you are using gparted from within ubuntu you can not change the ubuntu partition. You must use a gparted live CD/USB. Download the iso from [here]("http://gparted.sourceforge.net/livecd.php") for gparted live.

---

### Post by drs305 on 2010-08-12
If you are still stumped after following *presence1960's* instructions, you might find some help by reviewing the tips in the second half of the first post in this thread:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by presence1960 on 2010-08-12
> **drs305 said:**
> If you are still stumped after following *presence1960's* instructions, you might find some help by reviewing the tips in the second half of the first post in this thread:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Dave, upon further review it might be helpful if mgiblets posts the output of ```
sudo fdisk -l
``` from terminal. His notation of the partitions and OS is misleading. I read it as ubuntu is the first 118 GB partition in the extended partition, but after looking again it appears that is windows. More precise info is definitely needed here.

---

