---
title: "partitioning"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by yijie on 2006-06-04
I have tried to install xubuntu dapper drake as a second operating system(Win XP, Xubuntu dual boot) but the included gparted was unable
to resize my NTFS partition. When I click the apply button, gparted will pause for a while, but when it finishes, the partition is still not resized. I have not been able to use partitionmagic as I have a faulty keyboard which will automatically input random keys so when it says press a key to abort, the keyboard will automatically enter something and the operation will be cancelled. The keyboard works when it enters an operating system.Otherwise, the LiveCD works perfectly. What should I do to install xubuntu?

---

### Post by aysiu on 2006-06-04
Downloading another distro may seem excessive, but I've never had troubles with [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

QTParted and GParted generally work but sometimes will give you weird errors or grey out options that should be legitimate operations.

---

### Post by yijie on 2006-06-04
I'll try it but it does seem very excessive. :neutral: need to wait another 6 hours...

---

### Post by confused57 on 2006-06-04
You may need to defragment your WinXp(possibly a couple of times), before trying to resize the NTFS partition with the Xubuntu installer.

---

### Post by aysiu on 2006-06-04
[QUOTE=confused57]You may need to defragment your WinXp(possibly a couple of times), before trying to resize the NTFS partition with the Xubuntu installer.[/QUOTE] I don't think it's a terrible idea to have a copy of PCLinuxOS around, but while you're waiting for that, confused57's offering good advice.

I'm not 100% certain about this, but you may want to make sure *ntfsprogs* is "installed," too. In the live CD session, paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install ntfsprogs
```

---

### Post by rcarring on 2006-06-04
If you have room for another ide drive and some technical expertise, adding a second hard disk for Linux might work better than resizingntfs partitions on an existing hard disk.

---

### Post by yijie on 2006-06-04
Thanks for the quick response. ntfsprogs still does not solve the problem, and i have a laptop with only 1 hard drive. I'm defragmenting my computer now while downloading the pclinuxos iso.

---

### Post by yijie on 2006-06-04
I am finally able to partition my harddisk. I used the GParted LiveCD and it works flawlessly. Anyway, I cancelled my pclinuxos download and I'm installing xubuntu now. Thanks for all your help.:)

---

### Post by rcarring on 2006-06-04
Hope it all goes well, in any case post here when you have done installing.

---

### Post by yijie on 2006-06-04
I just finished installing. Thanks for all your help.:)

---

