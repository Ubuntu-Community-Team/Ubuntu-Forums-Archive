---
title: "Install Ubuntu 10.10 over 10.04 in dual boot setup"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by owenll on 2010-10-09
I have dual boot machine with windows and 10.04. After the nightmare of 10.04, especially [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787) the random freeze etc, I have tinkered with the system so much to try to resolve this that I would like to do a fresh install over my current Ubuntu install.
Screenshot shows how things look in gparted.

1 - where should I install Ubuntu?
2 - is it possible to install while keeping my files in Home, or should I just back these up and copy them back?

Thanks for any help.

---

### Post by mikewhatever on 2010-10-09
You linux partition is /dev/sda5, so that's the one you should reuse. There is no separate /home partition, so that you'd have to backup your files. I'd also suggest testing before installing. Just run it from the cd/usb for a few hours/days or as long as needed.

---

### Post by irv on 2010-10-09
I did two Installs of 10.10 the other day, and things went very well. I did one clean installed on a Dell 1505 laptop and an upgrade from 10.04 on a Dell 1521. The upgrade took much longer, but I had many applications  installed on it. There were no problems with either one, so I thought I would just pass this information on to you.

---

### Post by owenll on 2010-10-09
> **mikewhatever said:**
> You linux partition is /dev/sda5, so that's the one you should reuse. There is no separate /home partition, so that you'd have to backup your files. I'd also suggest testing before installing. Just run it from the cd/usb for a few hours/days or as long as needed.

Thanks for the quick response.

---

### Post by scrooge_74 on 2010-10-09
Also you could make a new partition and move /home there, after that is done, reinstall and point the new install so that /home is in that new partition.

Next boot will give you even your old wallpaper. I' being through several Ubuntus and Debians versions on the same laptop and not even my emails needed to be moved out of the way. After some minor adjustments or updates the laptop was again running as usuall 

(Sadly that laptop has now gone to laptop heaven, it will be missed)

---

