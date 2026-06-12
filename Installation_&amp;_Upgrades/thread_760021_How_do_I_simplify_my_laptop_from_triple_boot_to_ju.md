---
title: "How do I simplify my laptop from triple boot to just Ubuntu"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Niels Olson on 2008-04-19
My laptop has XP, SuSE 10.1 (a mortally flawed release of that great distro), and Gutsy. Since Gutsy was the last one installed, it got the least hard drive space. I rebooted recently and realized the thing had been on in Gutsy for 184 days straight! So I want to get rid of XP and SuSE 10.1 Getting ready for Hardy, I'd like to get rid of XP and SuSE 10.1 and just generally clean up my partition tables, which are a mess. Here's a screenshot from gparted. 

Again, this is what it looks like:

 [IMG]http://nielsolson.us/images/MyPartitionMess.png[/IMG]

Here's my first, no, second, no, third draft of a plan to fix this using knoppix

1) reformat sda2 (XP)
2) dd, no, cp -ax the gutsy install on sda8 to the clean sda2 ([http://beans.seartipy.com/2006/09/24/moving-a-gnulinux-installation-to-a-different-partition/](http://beans.seartipy.com/2006/09/24/moving-a-gnulinux-installation-to-a-different-partition/))
3) delete sda3 through sda9
4) shrink sda2 to 26 GB, 
5) then add partitions for swap (sda3 8GB), and use the last primary partition (sda4) for a set of extended partitions (sda5, sda6 and sda7) for gutsy, hardy, and some space for another distro in the future.
6) cp -ax the gutsy install a second time, from sda2 to the new sda5, and make 26 GB sda2 the new /home directory.
6) edit /boot/grub/menu.lst to reflect the new setup,
7) and point grub to the new location of that menu.lst ([http://ubuntuforums.org/archive/index.php/t-45362.html](http://ubuntuforums.org/archive/index.php/t-45362.html))

I guess my biggest question is data integrity after cp'ing sda8 to sda2 then expanding sda2.

Here's the current table in text:
======================
sda1 dell utilities
sda2 WinXP
sda4
+- sda5 swap
+- sda6 SuSE 10.1
+- sda7 SuSE 10.1 /home
+- sda8 swap
+- sda9 Gutsy
sda3 some random useless space.
======================

and this is what I my little recipe above should do:

======================
sda1 dell utilities (47MB)
sda2 gutsy (22GB)
sda3 swap (8GB)
sda4
+- sda5 home (26GB)
+- sda6 hardy (22GB)
+- sda7 spare (22GB)
======================

I suppose I could do some more tile-puzzle work and make it

======================
sda1 dell utilities (47MB)
sda2 swap (8GB)
sda3 home (26GB)
sda4
+- sda5 gutsy (22GB)
+- sda6 hardy (22GB)
+- sda7 spare (22GB)
======================

or should I just dd gutsy to someplace safe on the network and redo the whole thing without the tile puzzle. Maybe that makes the most sense, but can I do that with a boot cd?

---

### Post by Happy_Man on 2008-04-19
Your plan sounds good, and I think Gparted will take care of the little things you mention. If you are really worried, though, back up anything you think you may need first. Have fun!

---

### Post by Niels Olson on 2008-04-20
it appears I will also need to edit /boot/grub/menu.lst

and point grub to the new location of that menu.lst ([http://ubuntuforums.org/archive/index.php/t-45362.html](http://ubuntuforums.org/archive/index.php/t-45362.html)) 

Any other things I need to do?

---

