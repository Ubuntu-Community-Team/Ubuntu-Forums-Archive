---
title: "Reformat a Raid 1 setup"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by whiteraven on 2007-10-07
I'm a Linux/Ubuntu newbie, computer is a 2.8GHz Dual Core Intel with 2 320 GB sata drives.

I made the decision to lose Windows XP and go with Ubuntu after using the 32-bit desktop 7.04 Feisty Fawn LiveCD. I had a couple of issues with the install and sought professional help from the shop where I purchased the computer. The tech convinced me to install the 64-bit version alternate cd version using a Raid1 disk setup.

I've run into problems finding 64-bit versions of a lot of the software I liked, and think I want to revert back to the 7.04 32-bit desktop and lose the raid setup. I was told that it is difficult to reformat the drives removing the LVM and raid setup. I'd like to re-install the 7.04 desktop on one drive and use the other as a backup without the raid.

Bad idea?
With what software and how should I format the drives?
Other suggestions on how to revert to the 32-bit desktop version?

---

### Post by Pumalite on 2007-10-07
Excellent idea. Disable Raid at setup. Use Gaprted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
to format your hard drives and re-install using 32 bit.

---

### Post by whiteraven on 2007-10-07
Thank you Puma... I've played with Gparted but wasn't aware that it would kill the LVM and Raid setup. Hope this goes well as I'm looking forward to digging into Ubuntu!

---

### Post by Pumalite on 2007-10-08
Good luck.

---

