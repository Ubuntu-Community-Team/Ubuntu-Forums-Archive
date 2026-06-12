---
title: "Monitor Screen on ubuntu 10.04 goes blank frequently"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2010-06-20
I have a new ubuntu 10.04 install, it is the third that I have done
recently. On this particular install (unlike the others) the screen goes
unexpectedly blank and any motion restores the screen. It is acting like
a screen saver with the blank screen option set. My screensaver preferences
are set to use a screen saver (cosmos, not a blank scrren) and for a 7-minute idle period. The lock screen option is **off**.
For AC power management **never** is chosen for "put computer to sleep" and 30 minutes is chosen for the "put display to sleep" option.

This is a compaq presario desktop. 

Please let me know how to disable this feature.
thanks
tim

---

### Post by gorean on 2010-07-19
I am having the same issue but with entirely different hardware.  On mine it seems to happen just a couple of times after boot.
Looking at the log files there does not seem to be anything that relates to display except some messages from evince: operation="profile_replace" pid=2726 name="/usr/bin/evince".  I currently do not see the connection.  It "feels" like a monitor detection issue but the monitor shows correctly in system/preferences/Monitors.  Anyway your not alone.

---

### Post by tim042849 on 2010-07-19
I swapped out the mag monitor for another one and the problem goes away.
Also, I think I mentioned it in the thread, but I did not have the problem
with the same mag monitor on a different machine, same OS distro.

It is my experience and the experience of my colleges that ubuntu
(and mint) and more sensitive to hardware and graphics issues than
some of the more mature distros like slackware, suse, redhat. 

My hope is that ubuntu will move forward on these issues. 
(see [http://forums.linuxmint.com/viewtopic.php?f=57&t=51819](http://forums.linuxmint.com/viewtopic.php?f=57&t=51819))
Thanks

---

