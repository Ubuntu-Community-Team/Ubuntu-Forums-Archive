---
title: "PROBLEM! Dual Booting Windows Xp and Ubuntu 7.04"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by micksterminator3 on 2007-07-21
I run Windows Xp on my laptop. I've been thinking about Dual Booting Ubuntu on it for a while. I found a guide on how to do it on "digg.com." I read it and it seemed amazingly simple so I decided to do it. I created the partitions for Ubuntu to run on and what not. Everything worked fine until I rebooted and went to the grub boot menu. THERE WAS NO WINDOWS XP! I soon found a guide on how to add "windows xp" to the list using the command "sudo gedit /boot/grub/menu.lst." 

The main problem here is that you need to have a partition # to run another operating system from the grub boot menu. I tried to not include one and it resulted in failure. It always says the drive does not exist. THE GUIDE NEVER MENTIONED PARTITIONING MY WINDOWS DRIVE!!! I downloaded GNOME Partition Editor and it says that 49.83 out of 55.89 GB is "unallocated."

Is there anyone who could help me boot Windows again?

---

### Post by Pumalite on 2007-07-21
Post sudo fdisk -l (small L) When dual booting: defrag several times, erase temp files, use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
If all you want is to recover XP: plug you installation XP CD>Hit Recovery>FIXMBR

---

### Post by luctor on 2007-07-21
-

---

### Post by marcelinoM on 2007-07-21
Can you post the URL to that digg story?    BTW, typing the following from the Ubuntu terminal (applications -> terminal) will tell us what your partitions table looks like:

sudo fdisk -l

If you have USB stick or something you can direct the output to file and then copy to USB stick with this:

(to create text file called table.txt)

sudo fdisk -l  > /tmp/table.txt

Use GUI to copy to USB stick and attach it to your post.

---

### Post by micksterminator3 on 2007-07-21
Here is the digg story

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

Thanks for the help. I ended up just deleting ubuntu. I think its better to stick with one OS at a time. I'll end up getting it on a separate computer.

---

### Post by upchucky on 2007-07-21
Heavy Sigh.....

such a simple problem to fix and no patience to fix it, there must be a thousand posts about how to set up win xp and linux, if any other beginners are reading this please read first and pay attention to the install when u do it.

In this case he simply did not tell the installer to dual boot, editing the linux loader would have gotten both linux and xp running in about 3 minutes

---

