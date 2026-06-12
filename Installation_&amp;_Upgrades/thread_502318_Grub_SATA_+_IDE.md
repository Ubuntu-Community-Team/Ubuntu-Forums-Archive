---
title: "Grub: SATA + IDE"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by macdim on 2007-07-16
Hi everyone,
I recently installed a new SATA drive an installed Windows XP on it.  I formatted my original IDE drive and installed Ubuntu 7.04.  I wanted to have the XP bootloader take care of everything with regards to booting the different OSs (to stay away from my MBR).  I installed GRUB onto a floppy disk and was planning on modifying my boot.ini file in XP to give the option of booting Ubuntu as well as XP.  Upon reboot after my install of Ubuntu, attempting to boot from the floppy gave me a blank screen with "GRUB" alone at the top left of the screen.  I figured it had something to do with the SATA drive and so I shut down, unplugged the SATA drive and booted to find that GRUB loaded off the floppy quite well.  I did what I had to do in Ubuntu with the floppy and bootsect.lnx and plugged my SATA drive in and booted into XP to set up the dual boot.  Now, when I boot the computer I get the same screen with "GRUB" at the top left when I choose "Ubuntu" from the XP OS selection screen.  How do I go about configuring GRUB to work with these two drives?
Thanks

System:
P4 2.66Ghz Northwood 533fsb
Intel D865GBF mobo
Western Digital 250Gb SATA
Western Digital 160Gb IDE

---

### Post by dabl on 2007-07-16
This is on the Kubuntu Forum, but configuring Grub is the same for all *buntu:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by macdim on 2007-07-16
Hey thanks for that link.
I just realized that my IDE hard drive is being recognized as "sda".  Is this a problem?  I was under the assumption that IDE drives should be "hdx" and SATA and USB media should be recognized as "sdx".  Would this have anything to do with my problem?

Thanks

---

### Post by macdim on 2007-07-17
Just want to get this back on the first page.  Things disappear so quickly in this forum!  
Just to add... I still have no clue how to solve this problem! :(

---

### Post by Pumalite on 2007-07-17
I thought you had it solved with dabl's link, What's the specific problem at this point?

---

### Post by macdim on 2007-07-17
Well in the case of the link provided, it shows the BIOS and GRUB not configuring the drives in the same order.  The solution was to edit device.map or something to that effect which I did look into, but my drives were listed correctly.  I can't find anything wrong with menu.lst either.
In the link's case, the user's IDE drive and SATA drive were name differently and GRUB was placing more emphasis on the IDE drives rather than the SATA ones.
Here is the outline of my install:

2 drives: One SATA 250Gb (called sda) and one IDE 160Gb(called sdb) 

Sda has an XP partition on it and an extra logical partition.
Sdb has an ext3 partition at ~60Gb, a swap partition at ~2Gb, a Windows partition at ~4gb, and a ~94Gb logical Windows partition, in that order.

Device.map shows:
sda = hd(0,0)
sdb = hd(1,0)

Menu.lst shows multiple entries summarized by the following:

Ubuntu kernel: hd(1,0)
Windows XP: hd(0,0)
-------------------------------------------------------
Thanks for any help!

---

