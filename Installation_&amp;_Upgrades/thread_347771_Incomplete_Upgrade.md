---
title: "Incomplete Upgrade?"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by RCC2k7 on 2007-01-27
As I mentioned in a [separate thread]("http://ubuntuforums.org/showthread.php?t=347624"), I had to upgrade from version 6.06 to 6.10, even though I would've preferred to install build 6.10 right from the start.

Here's a problem I'm having that makes me think the upgrade was incomplete, even though it reported success: I noticed that my Windows drives were not accessible in Ubuntu, so I look for answers in the manual. According to [this section]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html") in the Ubuntu Desktop Manual, all that is needed is to enable the drives in using the menu System - Administration - Disks. There is no "Disks" item there! I look for it in all menus, and even in Add/Remove Programs and Synaptic. The so called Disk Manager is nowhere to be found. How do I get it back? How do I know if there aren't more items missing from my Ubuntu installation?

---

### Post by kingmonkey on 2007-01-27
Interesting. I did a semi-fresh install of edgy and i dont have disks there either unless it is gnome patition manager. I have a sepreate /home partition.

---

### Post by rainwalker on 2007-01-27
I don't use Edgy (still thinking about upgrading, though) but it might be that it's in the menu, it just isn't shown. In Dapper, you can go to the Alcarte Menu Editor under Applications -> Accessories and choose what you want to show up in menus, I don't know if you can do that in Edgy. Check it out though, it might not be that it's not there, you might just need to set it so that the option appears in the menu.

Hope it works, Peace

---

### Post by RCC2k7 on 2007-01-27
It took me a reinstallation, but now I think I know what happened.

Unlike the live CD session, the installer decided not to assign mount points to my Windows drives when I installed Ubuntu. In fact, the installer suggested to erase the entire hard drive to install Ubuntu as the default choice. (!!!) I selected to install in the available free space. It created an ext3 and swap partitions on that free space but decided not to mount my Windows partitions.

When I reinstalled, I chose to partition manually and created the ext3 and swap partitions myself. Ironically, this time the installer did mount my Windows system drive as /media/sde1, and my data partition as /media/sde5. The Disks menu item is now visible and the drives are accessible - at least the data partition is, since I used the Disks item to disable the mounting of my Windows OS partition. This is how I wanted things set up.

EDIT: I take that back. The "Disks" item vanished again from the menu. :(

---

