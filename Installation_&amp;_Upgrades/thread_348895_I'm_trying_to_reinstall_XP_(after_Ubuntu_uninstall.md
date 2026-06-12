---
title: "I'm trying to reinstall XP (after Ubuntu uninstall) I get a GRUB 17 error"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by arkitech on 2007-01-29
I recently uninstalled Ubuntu and I'm trying to boot up with a XP installation CD. However I seem to get a GRUB 17 error every time I try to boot with my CD. Is there a way to access my XP installation CD?

---

### Post by gamerteck on 2007-01-29
Have you tried looking in the BIOS to make sure it's set to **boot from the CD** first? 

If you are getting that grub error then you would be well past the **boot from CD **stage.

---

### Post by arkitech on 2007-01-29
> **gamerteck said:**
> Have you tried looking in the BIOS to make sure it's set to **boot from the CD** first? 

If you are getting that grub error then you would be well past the **boot from CD **stage.

yep, I verified that I can boot from the CD. In fact I have a boot menu that allows me to select which device I want to boot from on startup. When I select the CD option I get the GRUB 17 error. Oddly enough if I replace the XP CD with the Ubuntu one, I experience no errors.

---

### Post by mysticrider92 on 2007-01-29
The cd could be bad (unlikely, but possible). Do you have any other os's on the hard drive? [Here]("http://ubuntuforums.org/showthread.php?t=1669") is another thread with the same problem, if that helps any.

[edit] I just looked at the thread title, how did you uninstall Ubuntu? It looks like the MBR didn't get wiped, so Grub can't start all the way.

---

### Post by arkitech on 2007-01-29
> **mysticrider92 said:**
> The cd could be bad (unlikely, but possible). Do you have any other os's on the hard drive? [Here]("http://ubuntuforums.org/showthread.php?t=1669") is another thread with the same problem, if that helps any.

[edit] I just looked at the thread title, how did you uninstall Ubuntu? It looks like the MBR didn't get wiped, so Grub can't start all the way.

I have no other OS's on the drive. I un-installed Ubuntu by booting up with the Live CD and removing all of the partitions. I added a new NTFS partition and rebooted the machine, but whenever I try to go with my CD I get the same Grub error. I'm going to try a different CD and see if that makes a difference.

---

### Post by arkitech on 2007-01-29
Looks like it was the CD that was bad, I swapped it out with another and it's working fine now. Thanks for the help guys.

---

