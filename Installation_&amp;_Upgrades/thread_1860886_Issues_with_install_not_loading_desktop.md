---
title: "Issues with install not loading desktop"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by mips on 2011-10-15
I need some help. I downloaded Ubuntu 11.10 alternate cd and installed it, I however can't stand it & rebooted the alternate cd to perform a cli base install and then pulled in xubuntu-desktop & restricted extras. Problem is when it boots it never gets to the desktop it just gets stuck between the cli & some garbled gfx flashing between the two all the time. My hdd light flashes and my gpu fan pulses on and off the whole time. Any ideas on how to fix this?

---

### Post by mips on 2011-10-15
Ok, I traced the problem to **lightdm**. Question is how do I fix it?

---

### Post by mips on 2012-04-12
Just so I don't bang my head on a wall for a 3rd, 4th etc time,

 /etc/lightdm/lightdm.conf
```
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xfce                     #(or xubuntu or whatever else you use)
```

---

### Post by Toz on 2012-04-12
Anything of relevance in the log files in /var/log/lightdm? You might also want to have a look at /var/log/Xorg.0.log.

---

### Post by mips on 2012-04-13
> **Toz said:**
> Anything of relevance in the log files in /var/log/lightdm? You might also want to have a look at /var/log/Xorg.0.log.

The problem is the default is set to
```
greeter-session=unity-greeter 
user-session=xfce

```

---

