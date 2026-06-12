---
title: "can't istall the flash plug-in in mozilla"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by screw3d2 on 2008-01-26
Hey there I try to install the flashplayer plugin from afobe but i cant pass the part where it asks me:
"please enter the installation path of mozilla..." i try to put /usr/lic/mozilla which is the default, but it tells me:
WARNING: /HOME/DANIEL/INSTALL_FLASH_PLAYER_9_LINUX/USR/LIB/MOZILLA is not a directory", and of course it is not a directory, i know that, but i dunno how to instruct it to go to root!!!, as usual help on this issue on how to install it correctly, is almost zero, so out of options, i humbly come to you gods of ubuntu, in search of enlightment, and a fricking easy way to install that evil plug-in!

THX

---

### Post by mikewhatever on 2008-01-26
Actually /usr/lib/mozilla is a directory. Just make sure you spell it right, don't insert any spaces and do not capitalize. If I remember correctly, you need to install flash to your home directory, to .mozilla/plugins.

---

### Post by shad0w_walker on 2008-01-26
The path you are looking for is 

/usr/lib/mozilla-firefox

If memory serves that is.

---

### Post by dhysk on 2008-01-26
what i had to do at that part was put it in /usr/lib/firefox.  It did alow me to put it in /usr/lib/mozilla, notice its mozilla not MOZILLA caps maters.  However when i put it in mozilla it installed but the borwser didnt see it.  

So to be safe put it in usr/lib/firefox
Say yes to do you want to install it to another directory,[I]or somthign like that[I]
then put it in usr/lib/mozilla
and again in usr/lib/mozilla-firefox 

let me know witch one workes for you.  Mine was the /usr/lib/firefox however for somereason diffrent people seam to get diffrent outcomes.

---

### Post by screw3d2 on 2008-01-26
thx i really didnt knew that capitals matter in console commands, ..., anyhow, my directory was usr/lib/firefox, ...now the plgun is up and running, thanks to all for the replies :popcorn:

---

