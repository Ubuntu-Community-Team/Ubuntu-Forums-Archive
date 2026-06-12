---
title: "Ubuntu Preseed xserver resolution"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by decubal on 2008-02-17
Hello Everybody!

I currently making a automatic install with pxe and a preseed file.
Everything is running smootly exept 1 single thing.

When the install is installng the xserver it ask for wicth resolution i want to use even i have used the following in my preseed file.

```
# Monitor autodetection is recommended.
xserver-xorg xserver-xorg/autodetect_monitor boolean true
# Uncomment if you have an LCD display.
xserver-xorg xserver-xorg/config/monitor/lcd boolean true
# X has three configuration paths for the monitor. Here's how to preseed
# the "medium" path, which is always available. The "simple" path may not
# be available, and the "advanced" path asks too many questions.
xserver-xorg xserver-xorg/config/monitor/selection-method \
       select simple
xserver-xorg xserver-xorg/config/monitor/mode-list \
       select 1440x900 @ 60 Hz
```

Any help yould be most welcome :)

---

### Post by decubal on 2008-02-17
solved using 

```
DEBCONF_PRIORITY=critical
```

---

### Post by robertc1985 on 2008-04-25
> **decubal said:**
> solved using 

```
DEBCONF_PRIORITY=critical
```

I'm modifying Wubi myself, where do i put 
the "code" DEBCONF_PRIORITY=critical in the file?

---

