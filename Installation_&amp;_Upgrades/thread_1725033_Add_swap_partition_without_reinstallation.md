---
title: "Add swap partition without reinstallation"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by h9uest on 2011-04-09
Hi there:

I'm using ubuntu 10.04 and it seems that I forgot to set up a swap partition when I installed my system. So, I can't install hibernate, and I don't think I have any virtual memory any more.

I know that I can always set up a swap file to play the same role, but since swap file is not contiguously stored on hard disk, the performance is expected to be worse than a swap partition.

So, how can I add a swap partition and make my system boot with it every time from now on? I have unused space on my hard disk, and re-installation is NOT an option.

Thanks in advance.

---

### Post by ~Plue on 2011-04-09
1) install > open gparted and make a new partition with 'linux-swap' as the file system
2) right click the newly made swap > click 'information' and copy the UUID
3) open a terminal and enter *gksu gedit /etc/fstab*
4)enter the following to a new line and save the file
```
UUID=975d5ea5-c15d-4cd9-87af-8b1206b6d84b none swap sw 0 0
```(replace the uuid with the one you copied from gparted)
5) then reboot or run *sudo swapon -a*

-hope that helps

---

### Post by vanadium on 2011-04-09
The Ubuntu documentation has a thorough page on this. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

An alternative option that does not require changing your partitions is to create a swapfile instead.

---

### Post by h9uest on 2011-04-09
Thank you guys. Your replies are really helpful.
Particularly, I now know that with the 2.6 kernel, "a swap file is just as fast as a swap partition." from the link provided by_ _[vanadium]("http://ubuntuforums.org/member.php?u=268902").

I appreciate it.

---

