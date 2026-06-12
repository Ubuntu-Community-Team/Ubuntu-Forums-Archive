---
title: "Move Installation or Reinstall and restore backup - Help!"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by CheapStartups on 2011-12-21
Ok so here's the deal... 

I have an IBM T61 that is dual boot Vista + Ubuntu 11.10. 

The Hard drive needs to be changed and I no longer want the dual boot. I just want Ubuntu... So...

Can I just clone the Ubuntu area onto new hard drive or do I install a fresh Ubuntu installation then do a restore backup to move everything over to new drive?...  

Help!

Thanks!

---

### Post by jerrrys on 2011-12-23
You can clone the existing install with something like [clonezilla]("http://clonezilla.org/"), but you will need to fix or reinstall grub afterward.

I think better to start fresh.

---

### Post by CheapStartups on 2011-12-23
Thanks for the response...  The thing is that I have all of my programs installed, all ubuntu updates, etc... 

My settings, config and everything on this install took a lot of hours to get the way I want and need it so I don't want to have to go so far as to start over if I don't have to...

---

### Post by oldfred on 2011-12-23
It depends on how easy it is to download the installed apps again or not. If you have slow Internet the Clonezilla or other full image backup may be best.

If you have high speed Internet you can easily export a list of installed apps and reinstall, I do this for all new installs as it installs the most current version. But if installing the same version it does not matter as the apps will be the same. 

All your user settings are in /home so if you back it up and reinstall it you will have all your user settings.

I do clean installs and my recovery plan is just a new install and restore /home, programs and some other minor stuff.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

