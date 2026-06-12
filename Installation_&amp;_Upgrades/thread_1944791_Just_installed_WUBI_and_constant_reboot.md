---
title: "Just installed WUBI and constant reboot"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by weilrich on 2012-03-21
This is my first installation of Ubuntu using WUBI - I don't know what version it is because I just downloaded it from the Ubuntu website, but I remember seeing 11.10 during the installation process. When the WUBI installation finished it told me I needed to restart. I did and Ubuntu will not boot. On startup I have the choice of booting Windows 7 and Ubuntu. Choosing Ubuntu reboots the computer, but choosing Windows 7 boots normally. 

I googled 'Ubuntu constant reboot' and found old articles that dealt with a similar problem with Ubuntu 10.04 (vintage 2010).

Some system info (if it helps): 
OS: Windows 7 Pro x64 SP1 
Processor: AMD Phenom 9850, 2.51GHz
RAM: 8GB 
Video: ATI Radeon HD 5700 and ATI Radeon HD 4600 adapters with three monitors - two on the 5700
Network: Belkin Play Wireless USB adapter bridged to Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller - the Internet comes in on the wireless and is bridged to a small wired network
Mouse: USB
Keyboard: USB
Drives: Maxtor STM3320620A (C:), Samsung HD204UI (K:), Seagate FreeAgent USB (1T J:), Sony Storage Media USB (8GB E:). 

Windows 7 is installed on the Maxtor (C:) and I told WUBI to install Ubuntu on a 30GB partition on the Samsung (K:).

What can I do to get Ubuntu to boot? :-\"

Note: edited 12.x version to 11.10. I relaunched WUBI and found the version number at the top of the window.

---

### Post by weilrich on 2012-03-22
I've uninstalled and reinstalled WUBI twice with the same results. Poking around in the forums here, I found several tidbits that may relate to the problems I'm having: (1) multiple graphic cards are not well-supported and (2) WUBI seems extremely flaky. I'll try downloading a CD copy to see if I can boot from that. Failing that, and with the deafening silence from the likely extraordinarily busy mods, I'll try Debian. If neither of those work, I'll cobble together an ancient PIII machine. Seems like a lot of work to get Airtime running.

---

