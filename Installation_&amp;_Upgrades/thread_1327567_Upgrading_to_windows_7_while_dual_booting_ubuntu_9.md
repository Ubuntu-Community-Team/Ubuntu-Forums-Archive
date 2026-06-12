---
title: "Upgrading to windows 7 while dual booting ubuntu 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by bsb25 on 2009-11-15
I recently partitioned my hard drive and installed ubuntu 9.10 on the second half. I'm also running windows vista. I want to upgrade vista to windows 7. I have all my important files on a separate hard drive, so I'm not overly concerned about losing any information. What is the easiest way for me to upgrade? Will I need to uninstall ubuntu and if so, how to I do that? I'm new to the linux world for the most part and I only have beginner's knowledge of the command line. Thanks for your help!

---

### Post by darkod on 2009-11-15
Since you have the important data on external drive, the next question is whether you want to do upgrade (keep programs, etc), or clean install of 7 (you would have to install all programs back but you avoid any possibility of upgrade glitches).

Whatever you decide I think windows will write its own bootloader over grub2, so read around about reinstalling grub2 back after you are done with windows.

For example:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Item number 13, Reinstalling Grub2 using LiveCD (in other words, Ubuntu CD, booting up and selecting Try Ubuntu option).

---

### Post by Trebaruna on 2009-11-15
darkod is right. To make things a little more explicit (perhaps redundantly): Windows should not touch your other partition(s) at all. If it does it's a bug. So Ubuntu will be fine, and all it takes is, like darkod says, to restore the bootloader.

---

### Post by bsb25 on 2009-11-16
Thanks guys. Everything is working perfectly now.

---

### Post by darkod on 2009-11-16
Glad it worked. Please mark the thread as solved. Above the first post there is Thread Tools, you can do it there. Helps other people.

---

