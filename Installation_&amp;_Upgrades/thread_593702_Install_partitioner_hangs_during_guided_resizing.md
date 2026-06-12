---
title: "Install partitioner hangs during guided resizing"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Game_boy on 2007-10-27
I have an 80GB hard drive with 100% used by a Windows XP Home partition on a laptop.

I am installing Ubuntu 7.10 (Gutsy).

On the partitioning step of the installer, I selected the first option, which I assume is resizing the Windows partition and creating new Ubuntu and swap partitions. I set the slider at 40GB for the new size, and pressed Continue.

A message came up saying the resizing operation had to take place before continuing. A "Resizing the partition" progress bar came up and hung at 0%. After five minutes the window closed but the installer main window was deselected and frozen. All other operations were very slow, even for a Live CD.

I turned off the laptop by holding the power button down and Windows was unaffected and still occupied 100% of the drive.

I do not want to use a separate partitioner unless I have to. Is it safe to try to install it again?

---

### Post by Pumalite on 2007-10-27
Defrag XP several times,erase all temp files and get rid of all stuff you wont need, at least 10 GB worth. Then use Gparted Live CD to resize your XP partition. THEN install.

---

