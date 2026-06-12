---
title: "Time wrong"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by curuxz on 2009-09-17
Hey guys,

I am in the uk and since upgrading to karmic my time is one hour behind my UK time zone. Tried forcing an NTP update but wont let me, says the port is in use.

Any ideas?

---

### Post by curuxz on 2009-09-17
ok very odd, been like it for 2 days, just did a package update and its back to the correct time, please ignore i guess it got fixed!

---

### Post by megamania on 2009-09-17
> **curuxz said:**
> ok very odd, been like it for 2 days, just did a package update and its back to the correct time, please ignore i guess it got fixed!
I'm having the same problem. My time is now 2 hours behind.

NTP wasn't installed. I installed it and rebooted, but the time is still 2 hours behind and if I right click on the time in gnome-panel there's no option to change it.

The system is updated.

Any help?

---

### Post by slakkie on 2009-09-17
Check /etc/timezone

---

### Post by megamania on 2009-09-19
> **slakkie said:**
> Check /etc/timezone
Apparently it is correct (Europe/Rome).

I managed to manually fix the clock, but still if I run system-administration-date and time, it's a big mess. The map of the world is completely messed up, and the application (time-admin) crashes as soon as I try to change something...

---

### Post by zika on 2009-09-19
> **megamania said:**
> Apparently it is correct (Europe/Rome).

I managed to manually fix the clock, but still if I run system-administration-date and time, it's a big mess. The map of the world is completely messed up, and the application (time-admin) crashes as soon as I try to change something...Same here, I thought it was my fault ... huh ...

---

### Post by megamania on 2009-09-19
It may be (at least in part) this:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg326095.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg326095.html)

---

### Post by lisati on 2009-09-19
> **megamania said:**
> It may be (at least in part) this:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg326095.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg326095.html)

+1 for a likely suspect.

Another thing I have found in other releases is sometimes UTC settings can mess with clock settings, particularly in multiboot situations (e.g. with Windows)

---

### Post by EugeneK on 2009-09-29
The time in my panel clock is wrong, too (it's displaying GMT, but I'm in EDT). I don't have an /etc/timezone/ directory, but 'date' gives me the proper time, so I assume there's something wrong with the configuration of the clock applet itself. NTP is installed, but there's no option for setting the time with a network time server in the preference dialog, and no time zone selector.

---

### Post by slakkie on 2009-09-29
> **EugeneK said:**
> The time in my panel clock is wrong, too (it's displaying GMT, but I'm in EDT). I don't have an /etc/timezone/ directory, but 'date' gives me the proper time, so I assume there's something wrong with the configuration of the clock applet itself. NTP is installed, but there's no option for setting the time with a network time server in the preference dialog, and no time zone selector.



/etc/timezone is a file. 
Also have a look at: [http://ubuntuforums.org/showthread.php?p=8021046#post8021046](http://ubuntuforums.org/showthread.php?p=8021046#post8021046)

---

