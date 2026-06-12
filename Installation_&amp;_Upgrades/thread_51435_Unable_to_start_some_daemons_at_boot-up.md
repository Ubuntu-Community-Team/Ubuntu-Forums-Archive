---
title: "Unable to start some daemons at boot-up"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by garion on 2005-07-23
Hi I am new to Ubuntu/Debian... and I was having trouble to let a few program start at the boot-up.  Specifically, firestarter, ddclient, and emifreq-applet.  All three are in /etc/init.d and in proper /etc/rcX.d folders.  I tried using Boot-Up Manager and update-rc.d to rebuild the links... everything looks fine, but those three things just won't start automatically.

Does it have anything to do with the fact that these three daemons require root to start?  My sshd starts just fine.  Is there anything I did wrong?  This sudo thing is really confusing me...

Thanks.

---

### Post by garion on 2005-07-23
Actually, firestarter works (so does ssh)... but the other two (ddclient and emifreqd) do not... still confused...  :| 


[QUOTE=garion]Hi I am new to Ubuntu/Debian... and I was having trouble to let a few program start at the boot-up.  Specifically, firestarter, ddclient, and emifreq-applet.  All three are in /etc/init.d and in proper /etc/rcX.d folders.  I tried using Boot-Up Manager and update-rc.d to rebuild the links... everything looks fine, but those three things just won't start automatically.

Does it have anything to do with the fact that these three daemons require root to start?  My sshd starts just fine.  Is there anything I did wrong?  This sudo thing is really confusing me...

Thanks.[/QUOTE]

---

### Post by garion on 2005-07-25
Solved, see [http://www.ubuntuforums.org/showthread.php?p=270504#post270504](http://www.ubuntuforums.org/showthread.php?p=270504#post270504).

---

