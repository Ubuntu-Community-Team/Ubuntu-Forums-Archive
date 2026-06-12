---
title: "Monitor shuts down after 15 minutes in spite of ....."
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2014-12-16
Using Xubuntu 14.04, my LG LED monitor shuts down after 15 minutes if idling, in spite of both the light locker and the power manager are disabled. The monitor's power saving mode is also disabled. This is a dual boot Windows 7 & Xubuntu desktop and this never happens in Windows. What have I missed? I am really stumped.

---

### Post by fantab on 2014-12-16
If there is a screensaver installed they you have to disable it too or set it to 'never'. Don't disable light locker and power manager, just set them up to 'never'.

---

### Post by Dennis N on 2014-12-16
This may be the known problem with DPMS (display power management system) - except that DPMS kicks in in 10 minutes, not 15. 

About DPMS
[http://www.computerhope.com/jargon/d/dpms.htm](http://www.computerhope.com/jargon/d/dpms.htm)

If you think this applies to you, a solution is referred to in this thread:
[http://ubuntuforums.org/showthread.php?t=2256459](http://ubuntuforums.org/showthread.php?t=2256459)

---

### Post by ineuw on 2014-12-16
@fantab thanks for the suggestions: I reactivated both in the 'Session and Startup' and rebooted. The power manager is set to 'Never' but Light-locker just flashes by and shuts down even after reinstallation. Tried to activate it from the terminal and it just hangs there. 'sudo light-locker' generated the following error message: 

**process 3608: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file ../../dbus/dbus-message.c line 1263. This is normally a bug in some application using the D-Bus library.**

So, I followed Dennis N's suggestion:
> 
    Re: Monitor shuts down after 15 minutes in spite of .....
    This may be the known problem with DPMS (display power management system) - except that DPMS kicks in in 10 minutes, not 15.

    About DPMS
    [http://www.computerhope.com/jargon/d/dpms.htm](http://www.computerhope.com/jargon/d/dpms.htm)

    If you think this applies to you, a solution is referred to in this thread:
    [http://ubuntuforums.org/showthread.php?t=2256459](http://ubuntuforums.org/showthread.php?t=2256459) 

Dennis N, thanks for the links. I followed them and read all the related posts. I am sure that this is my problem as well. As for the DPMS time, I didn't measure it, it was just an estimate as I was away from the computer. I installed screensaver, added it to the 'Session and Startup' as xscreensaver -no-splash. Let's see what happens.

---

