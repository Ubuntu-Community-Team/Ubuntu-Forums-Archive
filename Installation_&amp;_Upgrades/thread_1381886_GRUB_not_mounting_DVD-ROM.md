---
title: "GRUB not mounting DVD-ROM"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by jamster12 on 2010-01-15
Hey guys,

I'm relatively a newbie when it comes to linux etc however have messed around with a few distros in the past. 

I decided to have a bash at ubuntu again, everything was going smoothly until I realised the dvd drive wasn't functioning. I did many re-installations of other ubuntu flavours but the same thing kept on happening. Also, the drive wasn't working in windows too (I'd dual-booted) so I guess the only thing in common with both OS's was GRUB. I used GAG (graphical bootloader) off a cd and everything worked fine! 

I've had a look at how to delete grub and get either LiLO or GAG but most people say that you should really be an experienced user to do this or you may end up bricking your computer? Considering that I deleted ubuntu, is there anyway to install either LiLO or GAG instead of GRUB from a fresh installation? OR, is there a way to get GRUB mounting my drive? 

Cheers!
Jam.

P.S. In the past ubuntu has had no problems mounting my dvd drive. Since paragon partition manager (yeah i should have used Gparted) froze on me during formating a partition last year, grub doesn't seem to mount my dvd drive. Dunno if this is linked and maybe paragon messed up something. :mad:

---

### Post by drs305 on 2010-01-15
Do you mean grub or fstab?  Are you trying to have an option on boot to run an ISO on a cd? Normally the cdrom settings are made in /etc/fstab, with an entry such as:
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by jamster12 on 2010-01-15
> **drs305 said:**
> Do you mean grub or fstab?  Are you trying to have an option on boot to run an ISO on a cd? Normally the cdrom settings are made in /etc/fstab, with an entry such as:

Nope, I want to use a grub alternative such as lilo or gag. I was hoping someone could give me an easy guide on how to remove grub and install lilo OR solve the problem with grub not mounting my cdrom for use in ubuntu or windows.

I used the alternate CD to get Lilo! BUT, lilo is causing me problems with the option menu etc but the cd drive is mounting correctly. Guess I'll post another thread about my latter problem.

---

