---
title: "CDROM problem"
date: 2012-08-02
forum: Installation &amp; Upgrades
---

### Post by dgundling on 2012-08-02
Trying to build up a computer for Ubuntu. Ran into a problem. With no OS loaded the bios sees the CDROM drive. The computer can't read from the CDROM drive. The only way I can get a live disk to work is to load a version of Windows (have tried both 98SE and XPhome). I can then load a version of Ubuntu. (I have 10.10 and up through 12.04) . Once a version is installed, it works but won't recognize the CDROM drive nor read from it. I have two other WIN XP computers either of which will read any UBUNTU live disk that I have. Does anyone know what Windows does different from Ubuntu that allows live CDROM disks to be recognized and read from that Ubuntu does not?

---

### Post by El Potro on 2012-08-06
Hello,

It seems your problem is a very strange one. 

If you can boot Ubuntu it means GRUB2 gets loaded before. In this case you can create an entry in GRUB2 to boot from an .iso file.

Also you could still boot from a pen drive.

Good luck

---

### Post by darkod on 2012-08-06
Are you sure you are not having some hardware issues with the cd-rom? Loose cable maybe, etc?

The computer should be able to boot from a bootable cd always, regardless what you have on the hdd. In fact, you should be able to boot from cd even with no hdd inside the computer.

Double check that the cd is good, burnt at low speed (not more than 8x or 10x), and that the cd-rom is good and working. Also, make sure in the bios boot devices cd-rom is before hdd.

Sometimes if you burn a cd too fast it can work in some drives but not in others, if they are more sensitive or nearly broken. Always burn OS install cd at 8x or 10x, it minimizes errors on it.

---

### Post by dgundling on 2012-08-06
Thanks for the replies. I could probably boot from  USB drive but that isn't the problem. What I would like to do is have a "live" CD run and give me the choice of running from the CD or installing. At the moment such a CD, when inserted, causes the CDROM drive power light to come on briefly but then instead of loading the contents of the CD the CDROM drive turns off. (BTW, I have both a CDROM drive and a CD?DVDROM drive installed and the problem is the same with either.) If I load a version of Windows and with the windows version booted up, the live CD works fine. That was the route I had to use to get Ubuntu loaded.  If I shut down and reboot in Ubuntu the live CD doesn't work. My hypothesis is that Windows is handling the live cd in a manner somwhat different that Ubuntu does. I have been unable to find out what the difference, if any, might be. Have you tried to use a live cd when running a version of ubuntu?

---

