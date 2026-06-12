---
title: "Help I only can boot into Memtest??"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by kirbys on 2010-01-09
I did updates that came up automatically, and now when it rebooted, I can't go in to anything except memtest.  I held shift to see the menu and it still only showed those. I can't loose my data so reinstalling isn't an option for me. Right now I'm using the CD to boot to this. I can see my data on my HDD and its there, but I don't know what to do in order to make it boot to the OS partition (Just switched from Windows 3 days ago).

Ubuntu 9.10
64bit
(GNU GRUB 1.97~beta4)

---

### Post by kirbys on 2010-01-09
Bump

---

### Post by oldfred on 2010-01-09
First do a backup.

Some have been able to boot from the CD using the boot from hard drive choice that seems to bypass whatever issue. And if that works do a reinstall of grub once inside your system.

Otherwise it will be reinstall grub from the CD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
or
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by gingoro on 2010-01-09
I have essentially the same problem.  Here is a slightly updated copy of the post what I posted on the newbie forum.  So far lots of readers but no help.  memtest and a boot of winders still works just fine. Dave ... I have been using Ubuntu 9.10 (32bit) for about 3 weeks on my HP netbook. (Note not netbook remix as I tried that and did not like it.) Ubuntu has almost become my preferred system to boot as it has been working just fine. Yesterday after it performed an update I decided to reboot as is my normal practice. On 31.17 I get prompted for my password and then something that looks like a terminal is brought up. However I can not type in any thing at all. Only solution is to reboot. Have tried going into restore. Have asked it to fix any broken packages but no joy. Also have tried 31.14 and 16 and both hang up prior to the login screen. Thanks Dave

---

### Post by kirbys on 2010-01-09
GRUB works just fine but it doesn't load the kernel so it can't boot to my partition. Also, I can't back up a lot of files as it says I don't have permissions. I try to go in the app manager thing and when i try to reinstall the kernel it says error15 after its done downloading which is aggrevating to say in the least. If i can just figure out how to back up stuff I'll just say screw it and reinstall Ubuntu all together.

---

