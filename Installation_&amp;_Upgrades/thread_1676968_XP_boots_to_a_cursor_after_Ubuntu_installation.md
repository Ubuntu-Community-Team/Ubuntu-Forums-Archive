---
title: "XP boots to a cursor after Ubuntu installation"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by cuzman1977 on 2011-01-28
Built a new system from some old bits and a couple of new bits:

Intel Celeron 430 1.8GHz LGA775 (Intel Core 2 Quad Q8200 2.33GHz upgrade soon)
Gigabyte GA-G31M-S2L LGA775 MicroATX Motherboard
2x OCZ OCZ2RPR800C44GK 2GB DDR2 PC6400
Sapphire Radeon HD 5570 1GB PCI-e (low-profile)
Seagate Barracuda 320GB SATA 7200rpm ST3320620AS
Jeantech 500W JN120F-500AP
Lite-On DVD R-W LH-20A1H
Akasa Baymaster AK-ICR-10 Card and Drive Reader
Microsoft Wireless Keyboard and Mouse

Installed Windows XP Professional from scratch with an NTFS format.  All fine.  Have been tinkering with it for a week before deciding on a dual-boot with Ubuntu.  I defragmented the drive in XP (even though it hasn't had much use)

Created boot CD from the Ubuntu 10.10 32-bit ISO and then used that to partition the XP drive, 121GB Ubuntu and 199GB XP.  Installation of Ubuntu seemed to go smoothly.  Updates applied and a couple of random programs added.

Then I restarted and went to XP in the boot screen.  Now all I get is a cursor in the top left.  Nothing else.  i can still boot into Ubuntu with no problems.

Can anyone advise on the best course of action?  XP Recovery Console from the CD?  I don't want to try that yet if there is a better way.

I know that I could have created the correct partitions when installing XP, but I honestly only had the idea of a dual-boot system long after.  I don't want to start all over again if I don't have to as it has taken several evenings to update XP and get to where I am now.

---

### Post by wilee-nilee on 2011-01-28
Sounds like you moved XP far enough to disrupt the autochkdsk that is run on rebooting. So confirm that XP is there, and boot the XP disc to the repair command and run the chkdsk /r

I assume you tried the update-grub command in Ubuntu as well already.

Generally when you resize any Windows with other then a onboard virtual partitioner like W7 has you would reboot it to make sure it us working before installing Ubuntu, just to be sure.

---

