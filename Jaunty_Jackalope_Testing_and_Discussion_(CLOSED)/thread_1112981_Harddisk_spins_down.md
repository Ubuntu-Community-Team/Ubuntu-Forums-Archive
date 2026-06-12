---
title: "Harddisk spins down"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ildfroe on 2009-04-01
Hi,

My harddisk spins down (or powers off) when it's been idle for 1 or 2 minutes. Doesn't matter if the power is plugged or not.
When the system needs the disk (opening an app, or just a menu), I can hear a click sound and the drive starts to spin up again. This takes a second or two, and the system freezes during this.
It happened two times while writing this.
Maybe something with laptop-mode-tools?

---

### Post by Sam Lars on 2009-04-03
You can use the command
```
sudo hdparm -B 255 /dev/sda
```
Where sda is your device and 255 is the power management setting:
```
                Set Advanced Power Management feature, if the drive supports it.
              A low value means aggressive power management and a  high  value
              means better performance.  Possible settings range from values 1
              through 127 (which permit spin-down), and values 128 through 254
              (which  do  not  permit spin-down).  The highest degree of power
              management is attained with a setting of 1, and the highest  I/O
              performance  with a setting of 254.  A value of 255 tells hdparm
              to disable Advanced Power Management  altogether  on  the  drive
              (not all drives support disabling it, but most do).
```

---

### Post by ildfroe on 2009-04-04
Thanks. I'll try that.

---

