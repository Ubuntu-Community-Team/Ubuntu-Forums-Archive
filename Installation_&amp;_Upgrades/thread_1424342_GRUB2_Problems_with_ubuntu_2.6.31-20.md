---
title: "GRUB2 Problems with ubuntu 2.6.31-20"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by saejin on 2010-03-07
Things worked pretty good until I upgraded to ubuntu version 2.6.31-20
Now the system hangs during boot about 3 out 4 times. By simply pressing the reset over and over, it eventually boots into either ubuntu version 2.6.31-17 or ubuntu version 2.6.31-20.  both hang. sometimes is hangs waiting for the root file system, and sometimes it hangs after apparmor.
 
rebooting and rebooting it eventually boots without changing anything.  Seems like a time problem.

---

### Post by woodmaster on 2010-03-07
Try reinstalling grub...worked for me to fix grub errors:
[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)

---

### Post by saejin on 2010-03-08
I did reinstall GRUB2.
There also seems to be a problem with the splash screen. Even though /etc/grub.d/05_debian_theme
finds the splash screen, it is never used, and always used the default mono theme. This seems to be a problem when /boot/grub/grub.cnf tries to run the check if loadfont /usr/share/grub/unicode.pf2 ; then set gfxmode
This never succeeds, so gfxmode is never set.  When I try to run loadfont from the command line I get "command not found"

---

### Post by mbogevik on 2010-03-19
This happens with my HP Proliant ML110 server too.  Reboot to 2.6.31-20-server hangs the computer when boot start, always.

What worries me is that it seems that kernel has been updated automatic by security updater.
A unsafe update like this should never had been done automatically.

The good thing is that my server ALWAYS start and work perfect (as normal) when manually selecting kernel 2.6.31-19-server.

---

