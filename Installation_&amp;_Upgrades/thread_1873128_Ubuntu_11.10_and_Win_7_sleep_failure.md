---
title: "Ubuntu 11.10 and Win 7 sleep failure"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by jaktar on 2011-10-31
This is something new I found after moving to Ubuntu 11.10.  I have had previous installs of Ubuntu 7,8,9,and 10  but with different drive configurations than I currently have.

I have 3 drives, sda has windows 7, sdb is data, sdc is Ubuntu.  I added sdc when I installed Ubuntu 11.10 and installed GRUB2 as usual.  Also, as usual, Win7 didn't like the fact I just changed the boot manager and at one point I ran the Win7 boot loader repair tool.  Windows re-added a functional bootloader on sda.

At this point I can select either drive 1 in bios and boot to Win7 or select drive 3 and load Grub2 and boot Ubuntu or Win7.

The problem is:  If I boot from drive 3, Win7 is not able to go to sleep.  Ubuntu sleeps normally.  If I boot from drive 1, Win 7 sleeps normally.

I had the same install setup with Mint using GRUB2 recently, but I did not have the same sleep problems with Win7.  I'm unaware of anything in GRUB2 that could cause this behavior, but it's the only real difference between the previous versions of Ubuntu I've had on this same rig.

---

