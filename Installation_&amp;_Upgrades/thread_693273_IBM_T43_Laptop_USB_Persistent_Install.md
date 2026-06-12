---
title: "IBM T43 Laptop USB Persistent Install"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by DallasAlien on 2008-02-10
I got a new 8gb flash drive this week and decided to it up to boot Ubuntu 7.10, Just a note about trying to run Ubuntu from a flash drive on an IBM T43, I needed to disable the boot from USB FDD setting in the BIOS but leave the boot from USB CD setting enabled for it to work, it could be the same for similar models. Hope that helps someone.

I still wanted to access the USB drive when booting into windows. XP doesn't support multiple partitions (which you need to make to have a persistent installation) on a USB flash drive but here is a good guide to editing an IDE driver to be able to get at both partitions - [http://www.msfn.org/board/lofiversion/index.php/t69211.html](http://www.msfn.org/board/lofiversion/index.php/t69211.html)

Also the second partition on my drive is EXT2 formatted, a good open source windows driver for EXT2 is Ext2fsd - [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

I have one problem tho, when running on battery if the power gets to ~30% the system freezes does anybody have any idea why this is? It does the same thing when running from the live CD.

On a side note the Transcend V10 8gb flash drive was a good deal at $29 but is very slow, even for a flash drive. The build quality of the plastic casing feels pretty cheap too. But I guess you get what you pay for.   :)

---

