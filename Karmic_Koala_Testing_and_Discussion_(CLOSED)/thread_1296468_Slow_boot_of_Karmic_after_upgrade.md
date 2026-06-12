---
title: "Slow boot of Karmic after upgrade"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kkkkdddd on 2009-10-20
About a year ago I installed Ubuntu 8.10. 
It booted in 1 minute and 15 seconds.
Then I upgraded to 9.04 and my system booted in 1 minute.

Yesterday I upgraded it to 9.10 but now it needs 1 minute and 35 seconds to boot.

By "boot" it mean a time from pressing "enter" in grub till all icons on the desktop are shown. I have been using autologon from the beginning. At first I see kernel messages for 5 seconds, then white Ubuntu logo for about 20 seconds, then screen is blank for 25 seconds, then I see brown screen with progress animation for next 20 seconds and then finally Gnome is starting to appear.  

My system is 32-bit and I use ext3. This is a laptop with C2D 2.4 GHz, 2 GB RAM and 160 GB HDD 5600 RPM.

> $ uname -a
Linux krzysztof 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

> $ df -h
/dev/sda5              57G   34G   21G  62% /
udev                 1006M  316K 1006M   1% /dev
none                 1006M  572K 1006M   1% /dev/shm
none                 1006M  224K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sda2              91G   65G   26G  72% /media/OS

I am also attaching boot chart.

Any help would be appreciated, but please do not tell me to reinstall Ubuntu.

---

### Post by KrazyPenguin on 2009-10-23
Here is something interesting about bootchart.

When I use it i get some kind of mounting error on the initial splash screen.

But that's not all!!! Using a stopwatch from grub to desktop with icons and the network manager password box showing takes 45 seconds.

Removing bootchart and the mounting error disappears and it appears that booting only takes 43-44 seconds. 

But the really weird thing is my "bootchart" says it takes 1:13 to boot.

There is no way I am off by almost 28 seconds using a stopwatch.

I suggest you do the same tests and see what you get.

I am also finding that after making changes, sreadahead needs to be executed during boot, and then you need to reboot again (thus resulting in two reboots).  The second boot, after making system changes is a lot faster.

Anybody else???

---

