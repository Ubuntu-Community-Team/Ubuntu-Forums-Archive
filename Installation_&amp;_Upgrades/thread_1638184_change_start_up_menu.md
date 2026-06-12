---
title: "change start up menu"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by not_the_geekiest on 2010-12-05
Hi,
I recently installed Ubuntu according to the instructions on the site. However, now when I start up my computer I see Ubuntu, Ubuntu recover (something like that), two windows 7's, and windows vista. Before I installed Ubuntu I only had windows 7. How can I clean it up so that I only see Ubuntu and Windows 7?

ps. If you couldn't tell, I am a beginner so try not to use to much linux jargon, or better yet, explain it to me.

---

### Post by efflandt on 2010-12-05
What brand of computer.  Many might have other recovery or utility partitions that are bootable.  Usually the one to select to run Windows would be one that says (loader), which might not be the one that Windows itself runs from as drive C:.

If you want to change that, you either need to edit /boot/grub/grub.cfg (which is **temporary** until kernel or grub update or anything else runs update-grub), or you need to change something in the scripts in /etc/grub.d/ (maybe in 40_custom and disable 30_os-prober by removing its execute permission).  Not sure the proper format, maybe simply copying the correct menu entry for the one you want from grub.cfg to 40_custom, before disabling 30_os-prober and doing **sudo update-grub**.

To disable os-prober: **sudo chmod -x /etc/grub.d/30_os-prober**

To re-enable it: **sudo chmod +x /etc/grub.d/30_os-prober**

Not sure how the binary os-prober determines which "other" partitions are bootable.  For my new desktop, **sudo os-prober** from Maverick (10.10) on sda4 simply shows:

/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sdb1:Ubuntu natty (development branch) (11.04):Ubuntu:linux

From Lucid (10.04) on sda3 of my old PC it shows:

/dev/sda1:Windows NT/2000/XP:Windows:chain
/dev/sda2:Windows NT/2000/XP (loader):Windows1:chain
/dev/sda6:Ubuntu 9.10 (9.10):Ubuntu:linux

Both are correct, it is just that Dell boots from its RECOVERY partition (Win7 is on sda3), and the old HP had another partition (sda1) that you could alternately boot from for recovery.

A shell script wiz could modify 30_os-prober script to toss out any Windows entries that did not contain (loader).  But I am not that wizard.

Note that you have to use **sudo** (or **gksu** for gui programs) prefix for commands to edit or change permissions of system files.  For example **gksu gedit** in a terminal would bring up gedit as root.  You can widen the window, but it is a little difficult to grab the edge.

---

### Post by not_the_geekiest on 2010-12-06
I have an hp computer. Here is exactly what I see.
> Ubuntu, with Linux 2.6.35-23-generic-pae
Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console *I forgot what number was here*)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)

Which one is the standard Windows 7 that I should use?
What is "binary os-prober"?

---

### Post by Quackers on 2010-12-06
Try both of the Windows loaders in turn and note which one actually starts Windows.
Then have a look at this guide by drs305 for ideas

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by not_the_geekiest on 2010-12-06
Thanks Quakers, but before I do anything that could potentially ruin my computer can you make sure what I am doing is right?

In the command line I simply type ```
sudo chmod -x /etc/grub.d/20_memtest86+
``` in order to remove both instances of "MEMTEST86+".
After that I did not understand what I should do (and where I should put the code). Can you help me with that?

---

### Post by Quackers on 2010-12-06
Yes, just copy/paste that line into the terminal and press enter then enter your password when required.
Then whilst still in the terminal type
```
sudo update-grub
```
and press enter. The next time you boot the Memtest entries should have disappeared from the grub menu.

---

### Post by not_the_geekiest on 2010-12-07
Thank you quakers, everything works.

---

### Post by Quackers on 2010-12-07
Excellent! :-)
Can you mark the thread as solved please, using the Thread Tools near the top of the page. Thanks.

---

