---
title: "No Boot Options"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by chpage07 on 2010-01-09
I tried to update earlier and it failed, so I tried to do a partial update and it locked up. When I rebooted and my Grub boot came up the only options I had are the two mem tests. I usually have options for Ubuntu Koala and Windows 7.  Any help would be much appriciated, I really don't want to reinstall Windows 7 and lose all my data.

---

### Post by Herman on 2010-01-09
You can download a Super Grub Disk with GRUB2 in it from Super Grub Disk - [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5"). Look for  the 1.21 SG2D Cdrom in one of the mirror sites. 

After you burn it to CD try it and see if it will boot your Ubuntu from the menu.

If  not, try some of the ideas in this link, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System.   

When you get your Ubuntu booted up and running, complete your updates and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg to fix your GRUB in Ubuntu.

---

