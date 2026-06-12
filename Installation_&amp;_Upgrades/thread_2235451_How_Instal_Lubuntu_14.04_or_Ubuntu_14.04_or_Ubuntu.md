---
title: "How Instal Lubuntu 14.04 or Ubuntu 14.04 or Ubuntu 12.04 on Abit NF7 Athlon XP Barton"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by bartek6 on 2014-07-21
Hi Everybody!

I've instaled succesfull Lubuntu 14.04 LTS on my old two notebooks - Dell D600, and HP nc6120. Now I want to install on my PC one of the followind systems: Lubuntu 14.04, Ubuntu 14.04 or Ubuntu 12.04, but installation process suspeds. DVD is detected. Installation process begins and I see only five dots changing its colors and Lubuntu install graphics. After about 20 minutes I see information:

--------------------------------------------------------------------------------------------
udevd [95] indify_add_watch(bi/dev/dm-1,10) failed: No such file or directors

Busy box v1.8.5 (Ubuntu 1:1:18.5-1ubuntu) built-in shell(ash)
Enter 'help' for a list of built_in commands
(inittramfs) Unable to find a medium containing a live file system.
--------------------------------------------------------------------------------------------

Full configuration of my PC is:
Motherboard: Abit NF7-S
Processor: Athon XP Barton 2800+
RAM: 2 x 1GB Goodram
GPU: ADM Radeon x1650

---

### Post by Bashing-om on 2014-07-21
bartek6; Hi !

Seems you have a real old ATI graphics card .. bet no driver is loaded .. as there will be no support from AMD for that card, the only choice you have is the Open Source driver.
Try and boot the liveDVD to "try ubuntu" mode with the "nomodeset" boot parameter:
 [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2

If you can do "try ubuntu", then, in the actual install DO NOT check the boxes for "3rd party software" or " install updates" in the initial installation screen.

Once booted into the actual install, and all is complete, we can see about what it will take to eliminate the need for the boot parameter "nomodeset".

[INDENT][INDENT]Maybe Yes
[INDENT][INDENT][INDENT]maybe, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Richard_Fleming on 2014-07-21
I just installed Xubuntu on my Shuttle SK41G which has an Athlon XP 2400+.

It would not boot the Lubuntu CD. It would not boot the Peppermint CD. It would not boot the Crunchbang distro via USB. It would not boot GhostBSD.

It did work with Xubuntu (via USB). If you have problems you may want to try Xubuntu first.

---

