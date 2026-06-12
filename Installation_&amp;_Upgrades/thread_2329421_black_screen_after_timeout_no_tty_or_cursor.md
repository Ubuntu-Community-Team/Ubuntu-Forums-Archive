---
title: "black screen after timeout no tty or cursor"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by vbdanl-yahoo on 2016-07-01
hi.  i have read many posts on the subject, and have tried many suggestions, all to no joy..
i am trying to install ubuntu 16.04 from a live cd to a HP with 3G ram and Geforce 6150LE nvidia graphics. the install goes perfect.  the unity screen appears with good resolution.  nouveau driver is installed by default. i ran updates and boot into .28 kernel (from .24 that came up from install).

sometimes when i select (top left icon that displays all of your installed programs, etc) it displays fine, but after awhile it will start showing garbled lines and sometimes just freeze the entire system.  sometimes it comes back after few minutes.
i turned off requiring a password and set the screen timeout to 30 min.  after sitting overnight, i now have a black screen, with no way of getting it to appear.  can not get to any other tty using std cntrl-alt-f1, etc.  no cursor, just black screen.

this is the second time i installed from cd.
first time after experiencing same results, i tried installing nvidia 364.. that did not work, purged it and tried nvidia 304, which is what i thought i was using with ub 14.04.. that did not work.. tried blacklist nouveau as suggested in some thread.. that did not work.. tried using gnome classic and gnome default, those would not work either.
ended up with login that would just return to login.. i could get to tty1, 2, etc, but not gui tty7.
even tried removing nvidia and going back to nouveau, but that did not work either.

finally just did another fresh install, and here i am.. hoping someone can lead me in the right direction..
also, i have this pc multi boot with lubuntu 14.04, fedora, and windows vista.. all of them still work fine.  i tried to update my working ubuntu 14.04 to 16.04, but obviously, that was not the piece of cake i thought it would be.  if i remember correctly, i was using gnome classic or gnome metacity or default and not unity with 14.04.  seems i was having similar issues using unity with 14.04.. but gnome was working fine, so i just kept using it.
would like to get this to work with unity if possible.  thanks for your help.

---

### Post by vbdanl-yahoo on 2016-07-04
been up 3 days now by not using the ubuntu search unity icon (certainly will need to sometime) and by turning screen off to never.  i just power off the monitor, and all works when i come back hours later and turn the monitor back on.  Happy 4th everyone !!

---

### Post by vbdanl-yahoo on 2016-07-07
system stays up until i access unity search button, then it freezes.  was able to C-A-F1 or F2 and back to F7 and get past lockup, at least the first 3 lockups, then it took longer to return to F1 and had error "DRM GPU lockup switching to software fbcon".  and "Buffer eviction failed".
added nouveau.modeset=0 to boot line.  boots but display is set to builtin and 1280x1024 on my 24" monitor, which is not too pretty..
will try to install nvidia driver tonight and see what happens..

---

### Post by vbdanl-yahoo on 2016-07-07
actually installed driver before leaving for work.. same basic results as before.  boots fine (i added nouveau.modeset=0 to boot line, but not sure it makes any difference. get a nice looking login screen (appears resolution is correct). i login, then screen just freezes or at least does not change.. login prompt is gone and ubuntu 16.04 logo is gone, but rest of wallpaper is just like it was for login screen, and no mouse or anything.  i was able to get to tty1.  when i go back to tty7, i now have black screen, no cursor.
I appreciate any help on what to try next.. thanks.

---

### Post by vbdanl-yahoo on 2016-07-07
forgot to mention when i installed the nividia driver, there was another selection at the bottom of the screen.. it said "Unknown:unknown" This device is not working.  It gives me the option of selecting "Using processor microcode firmware for AMD CPUs from amd64 microcode, proprietary.  Not sure i can get back to that screen since i can't get past login, but was wondering if anyone knows if it would help my problem.  should be able to install software from tty1 terminal.  any ideas ?

---

