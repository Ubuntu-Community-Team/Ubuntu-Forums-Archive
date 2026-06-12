---
title: "Upgrade from 7.10 to 8.04 went badly. Please help!"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by joshjani on 2008-08-06
I'm happily running 8.04 on my Compaq laptop, and WAS happily running 7.10 on an older Compaq desktop, dual booting XP. 

Everything was fine, so I probably should have left well enough alone, but every time I let update manager do its thing, I would see that little message saying that there's a new release, would I like to upgrade? 

So one day, (Monday) I decide to go for it. I said to update manager "yes, by gosh, I think I DO want to upgrade! AFter all, it's working so well on my laptop!"

WELL, now on my desktop, I cannot boot to Ubuntu. I get the splash screen, then the login screen, but when I log in, the computer freezes and I must restart.

Also, there's no option on the GRUB boot screen to boot to 8.04- just the 7.10 kernels (I have 2 options) and XP. 

If I try recovery mode and type 
sudo dpkg-reconfigure xserver-xorg
I get a message saying it's broken or not installed.

Any way to use recovery mode to apt-get the upgrade, or at least to simply fix what wasn't broken and get me back to a happy Gutsy Gibbon?

Thanks-
JC

---

### Post by Partyboi2 on 2008-08-06
boot into recovery mode and try
```
dpkg --configure -a
apt-get update
apt-get upgrade
```

---

### Post by joshjani on 2008-08-07
> **Partyboi2 said:**
> boot into recovery mode and try
```
dpkg --configure -a
apt-get update
apt-get upgrade
```

OK, I tried this, and after I type the first line, I get a very long string of errors, something to the effect of "Dependency problems with ... " The final dependency problem ends with "too many errors, stopping"

I can't print the errors, as I'm typing this from work and the desktop in question is not here.

Should I just start over with a CD of 8.04? I hate to do that, as the partitioning tool included seems to want to install Ubuntu in ADDITION to the Ubuntu version I have, shrinking the partitions and installing it side by side with the old version, rather than wiping it out, installing OVER it, so to speak, and using the already established partitions.

I'd much rather repair this install and proceed, so any further suggestions will be most welcome! Thanks-

JC

---

### Post by Partyboi2 on 2008-08-07
Reinstalling probably is the best way to go from here. When you get to the partitioning stage choose to use the manual option. Then tick the box to format your existing / partition this will wipe the / partition and reinstall to it.

---

