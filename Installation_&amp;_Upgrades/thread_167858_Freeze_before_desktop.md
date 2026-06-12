---
title: "Freeze before desktop"
date: 2006-04-29
forum: Installation &amp; Upgrades
---

### Post by ACoolie on 2006-04-29
First of all, I am on a high-end iMac G5 w/o iSight. 400GB, 2GHz, and 1GB RAM.

I have tried Badger 5.1 Live and Install and also Dapper Live and Install. My problem is not solved with any.

Install doesn't even pick up my Airport wireless card (although it did once, a while ago) (and I ended up with the same freeze, except at a login screen). So, I have been trying live. I can get through the entire install, but it goes to a screen the color of the banner of this forum (color-blind =P), then I can move the mouse around for a couple seconds, but then the mouse freezes and the fans come on real loud. I am using a Mighty Mouse but also tried a normal Apple Mouse, no change. The only thing that I noticed relating was during install I remember getting an error about dev.mac_hid_mouse_1 (or similiar), mouse_2, and mouse_emulation.

Also, I don't think this is a PPC issue, because my friend on a PC had the same issue.

Any help would be great, 
ACoolie.

---

### Post by Sef on 2006-05-16
Found this:

> A Linux driver for the Broadcom bcm43xx wireless chips.
Broadcom never released details about these chips. So this driver is based upon reverse engineered specifications.

This driver was included into the Linux kernel since 2.6.17-rc2.

Another branch of this driver, based on the Devicescape 802.11 Stack, which should be the future in Linux wireless support and which supports advanced capabilities (namely, full WPA support), can be found in the wireless-dev tree:
git://git.kernel.org/pub/scm/linux/kernel/git/linville/wireless-dev.git

The bcm43xx-fwcutter tool (required - see documentation for further info) can be found here.

The bcm43xx-sprom tool can be found in the SVN repository:
svn checkout svn://svn.berlios.de/bcm43xx/trunk/sprom


[http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/")

Another link about the chip.

[http://www.linuxelectrons.com/article.php/20051205195525114]("http://www.linuxelectrons.com/article.php/20051205195525114")

Found links above through this site:

[http://digg.com/linux_unix/Finally,_a_linux_driver_for_the_Airport_Extreme_]("http://digg.com/linux_unix/Finally,_a_linux_driver_for_the_Airport_Extreme_")

---

