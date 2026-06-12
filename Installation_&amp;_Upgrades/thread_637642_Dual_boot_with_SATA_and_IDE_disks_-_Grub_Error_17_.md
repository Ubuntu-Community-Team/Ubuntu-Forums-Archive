---
title: "Dual boot with SATA and IDE disks - Grub Error 17 and Error 22"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by IanHobson on 2007-12-11
I've just spent the weekend fighting to get grub to install properly, and finally discovered the problem. 

I strongly suspect a bug somewhere in the install script that installs Grub from the Ubuntu 7.10 live CD. 

(Where should that be reported?). 

What I wanted was windows and Ubuntu to dual boot from my large SATA drive. I have two IDE drives in the system also - one is moved from another system and the other is a slow (but large) backup drive. Neither contains an active  bootable partitions. 

I was getting error 17 and error 22 on grub after an apparently good install.  

My BIOS is placing the IDE drives before the SATA drives and Grub is putting itself onto the first drive it finds - NOT the first drive with an active partition. 

Result is GRUB boots from a disk it does not think it is on, gets confused and all bets are off. 

The solution was simple when I finally got there. 

I removed ALL drives except the SATA that I wanted to install to, and did the install. 

I ensured that C: and \ are BOTH physical partitions. D:\ and \home and the swap went into an extended partition as logical drives. This may not be 100% necessary but I can confirm it worked and is sometimes necessary. 

Everything worked. Then I reinstalled the IDE drives and everything continued to work. :)

Hope this helps someone having the same troubles I was.

Regards

Ian

---

### Post by logos34 on 2007-12-11
> **IanHobson said:**
> My BIOS is placing the IDE drives before the SATA drives and Grub is putting itself onto the first drive it finds - NOT the first drive with an active partition.

That's the one bad thing about grub--it looks for ide first and installs there, even when the sata are ahead in the Bios hard disk boot order.  It confuses a lot of people.

> I ensured that C: and \ are BOTH physical partitions. D:\ and \home and the swap went into an extended partition as logical drives. This may not be 100% necessary but I can confirm it worked and is sometimes necessary.

/ (root) will boot just fine from primary or logical partitions.  Even XP C: will boot from a logical--as long as there is another XP
on a primary that is the active partition (containing the bootloader files).

---

