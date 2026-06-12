---
title: "CPU Scaling"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-04-13
How do I turn off cpu scaling w/o using the cpu panel monitor

---

### Post by jmmL on 2009-04-13
So you want the CPU always to be at the highest supported frequency?
```

sudo su
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

---

### Post by manuelb on 2009-04-13
If you want to have these settings across reboots you may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=1111090") for one method.

---

### Post by tad1073 on 2009-04-14
It was a service in 8.10, but I have no idea why they changed it in 9.04.

---

### Post by manuelb on 2009-04-14
Previously you could use gconf-edit to modify the default behavior in **apps/gnome-power-manager** but they removed it , so now you have to modify existing scripts in etc/init.d or just add your own.

---

