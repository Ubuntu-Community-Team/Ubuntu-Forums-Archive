---
title: "Shutdown Doesn't, but Does Give a Halt Error"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by jglen490 on 2008-02-18
I've looked all over the place for this one, but can't find a solution.  One answer said to add acpi=off, which I did - no change.

I recently installed Kubuntu 7.10 on my IBM T20 laptop. With all the other distros I've thrown at this platform, none have ever failed to properly shutdown and power off. Except for now.

In Kubuntu I've gone to System Settings -> Advanced -> System Administration -> Login Manager -> Shutdown tab (in Administrator mode). I've tried the /sbin/ shutdown, /sbin/stop, /sbin/poweroff, and /sbin/halt entries for the Shutdown dropdown box. In all cases when I select "Turn Off" from the logoff menu selection, the GUI shuts down fine, and all the runs are properly terminated, killed, etc. The message "Will now halt" is displayed, but instead of powering off another error type message is displayed that states "halt: unable to iterate IDE devices: no such file or directory". this is followed by the message "System halted". The system goes quiet, but the power light is still on and the screen still has a display of the last messages. At this point I can press the power button and the power does go off.

This bizarre and maddening, but it seems like there may be a configuration problem somewhere or some shutdown scripts are honked up.

Where to look?

---

### Post by confused57 on 2008-02-19
This thread may help:
[http://ubuntuforums.org/showthread.php?t=699506](http://ubuntuforums.org/showthread.php?t=699506)

---

### Post by jglen490 on 2008-02-19
Thank you!!  Add that to your count :) !

adding apm power_off=1 to /etc/modules did the job for shutdown.  I haven't checked what happens with a warm reboot, but I don't do that very often.

The one thing I noticed was that the halt error still showed up just before the system went quiet and the power light went off.  But I will add this info to bug #193125.

Thanks again.

---

