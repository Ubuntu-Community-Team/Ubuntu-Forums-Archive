---
title: "can't install Ubuntu on SSD"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by rouvenster on 2018-01-19
Hi,
So I have this Acer aspire 5610 from 2006 with 2,5gb RAM on it and I was able to run windows 10 on it but as you can guess everything was really laggy and slow. So I brought this SanDisk SSD and wanted to install Ubuntu on it and wipe out windows.

HERE IS THE PROBLEM : I didn't have anywhere to plug sata device on that old thing, so I found on eBay one of those caddy bay adapter in the shape of a  DVD device where you are supposed to plug your SSD and shove the whole thing in place of the DVD player.
But mine is kind of special because it was 2006 and sata was not popular yet so my DVD player is an "ATAPI" device, and my adapter is basically SATA to "ATAPI/IDE".
I installed everything and checked on windows, bingo! It shows the ssd, even ran some speed test and acknowledged the speed gain (around 2-3 times faster than my normal old HDD).

HERE IS WHERE I AM STUCK : can't install Ubuntu. The installer does show the SSD but when trying to part it or access it with gparted it drop an error code input/output error. Tried updating the bios, tried install with another USB key, on another USB plug on the laptop, with Lubuntu instead of Ubuntu and even tried all the F6 special installation modes but nothing.

I have a clue though, since I have the EXACT SAME ERROR CODES than this guy :

[https://forums.techguy.org/threads/solved-input-output-error-during-read-on-dev-sda-on-installing-ubuntu-10-04.977983/](https://forums.techguy.org/threads/solved-input-output-error-during-read-on-dev-sda-on-installing-ubuntu-10-04.977983/)

But I lack similar stuff on my bios. Old Phoenix bios have no options like those :-(.

Any ideas? 

Thanks guys

---

### Post by ubfan1 on 2018-01-20
I had one of those IDE/PATA caddies and it had problems with grub/booting, but worked fine as a disk.  Can you access the SSD/caddy from the live media?  Just "try Ubuntu" and then try  partitioning / mounting on the device.  I found if I could get beyond grub, which would freeze upon ANY access while booting the device), I could actually access it normally.  My caddy was enumerated before the internal hard disk (regardless of BIOS settings), so I couldn't even boot off the original hard disk with the caddy present. What I COULD do was boot off a USB (before the hard disk in boot order, so grub never hit them), then with grub happily running a menu, I could edit the menu and select the SDD/caddy for boot, and that worked.

---

### Post by gordintoronto on 2018-01-21
Ubuntu is a poor choice for such an old computer. I have heard that Lubuntu is much better, but I would probably just install Puppy Linux and use the old thing for browsing. I'm pretty sure that the SSD would have little impact with Puppy, other than the boot time.

---

