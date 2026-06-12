---
title: "Dual booter reinstalled Windows and needs GRUB2 back"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by pangren on 2013-01-30
Hi, 
   I'm a dual booter and I just re-installed windows but I realized that my GRUB2 doesn't load on startup anymore. My Ubuntu is still working and somewhere inside my C: drive. Its just that I can't access it now. Is there anyway to re-install GRUB2 to the way it was before i re-installed windows? 

Thank you!

---

### Post by Mark Phelps on 2013-01-30
If, in fact, Ubuntu is INSIDE your C: drive, do NOT, repeat NOT, reinstall GRUB2.  That was a Wubi install, does not use GRUB2, and reinstalling GRUB2 will only make matters worse.

You first need to CONFIRM that this was a Wubi install.  Look for a file named root.disk on your C: partition.  IF that is there, this is a Wubi install.

---

### Post by pangren on 2013-01-30
Opps sorry I don't mean that. Hmm... I really mean I've installed ubuntu before and during install, I have partitioned a 250GB partition for ubuntu. 

Now in windows, it just appears as a Healthy partition in Disk manager. It is not really my C: drive . apologies.

---

### Post by pangren on 2013-01-30
and there is no root.disk in my C: drive . Not a Wubi install

---

### Post by pangren on 2013-01-31
Oops fixed it. I downloaded a boot repair disk from 

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

,burned it into a dvd and boot up with it. Everything is just automatic from there. :D

---

### Post by Mark Phelps on 2013-01-31
Good to hear it's fixed.  Please use the Thread Tools at the top of the Thread to mark this as SOLVED.  thanks

---

