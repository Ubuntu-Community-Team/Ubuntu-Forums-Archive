---
title: "Question before the upgrade."
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by SonicChao on 2006-12-10
I have a dual-boot, would installing Edgy on Dapper's partition mess anything up? Or should I just do a normal upgrade?

---

### Post by drr422 on 2006-12-10
I would first back up the stuff on the Dapper partition that you would like to keep, like your home directory, and your /etc/X11/xorg.conf file and any other necessary files.  But after that, i would just install on the Dapper partition, and the installation will take care of the new grub and everything.  I perfer installing it all fresh over a normal upgrade since it has fewer problems or so I have heard from the forums.  Have fun, I always like a fresh install :-)

---

### Post by SonicChao on 2006-12-11
Okay. :) I use Windows usually (because I use Wikipedia tools) so all my Linux stuff is on my flash drive. ;) I'll backup what else is necessary though.

---

### Post by drr422 on 2006-12-11
When I'm getting all the little stuff working on a computer, i usually write down how i got everything working (such as special media keys or special shortcuts) and i make sure i have a backup of those necessary files.

I would check out an Edgy live cd first to make sure everything is working as you would like. 

Besides the /etc/X11/xorg.conf file, you could back up your /etc/apt/sources.list file if you have some special repositories that you want to keep.  Other than that and your home directory (only if you want to keep your preferences for all of your programs) your pretty much good to go unless anyone else has a suggestion.

My habit is to do a fresh install, get things working, document how i got it working so next time i can just read how i did it, and then tweak until i usually break something.  Lately i havn't broken anything though.

---

