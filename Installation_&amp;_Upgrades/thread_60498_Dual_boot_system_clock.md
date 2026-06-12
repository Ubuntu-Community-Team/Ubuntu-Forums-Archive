---
title: "Dual boot system clock"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by KurtB on 2005-08-28
Hi there,

During install I've had to choose the time settings -> ubuntu recommended to set "the system clock as hardware reference" when you're using a dual boot.

Now I see that I always have a 2h difference between win XP & ubuntu:
* boot XP = 9h
* reboot in ubuntu = 11h, so I change the clock to 9h again.
* reboot in XP again = 7h...

Any tips how I can reconfigure & synchronize  my time settings?

thx,
KurtB

---

### Post by stepper on 2005-08-28
[http://ubuntuguide.org/#disablesystemtimedateutc](http://ubuntuguide.org/#disablesystemtimedateutc)

---

### Post by darrensnospam on 2006-10-18
How to disable system time/date from being reset to UTC (GMT)

    * Read #General Notes 
```

sudo cp /etc/default/rcS /etc/default/rcS_backup
gksudo gedit /etc/default/rcS
```

    * Find this line 

```
...
UTC=yes
...
```

    * Replace with the following line 
```

UTC=no
```

    * Save the edited file
    * System -> Administration -> Time and Date 

Set the correct time/date

```
sudo /etc/init.d/hwclock.sh restart
```

---

### Post by louieb on 2006-10-18
Thanks, this fixed an irritant of mine. :-\"

---

### Post by darrensnospam on 2006-10-19
I subscribed to this thread and just copied the information from the wiki just in case the wiki changed.
This is one of the first things I do when I reinstall.
Glad to hear it helped out.

---

