---
title: "Karmic on Acer Travelmate 4000 (4001 wlmi)"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by teranex on 2009-11-25
Two days ago i upgraded Ubuntu from Jaunty to Karmic on my Acer Travelmate 4001 laptop. Although the laptop is around 5 years old, Jaunty worked perfect, including reporting of Battery status and hibernating.
Now with Karmic I can't Hibernate anymore and my system load is always 2.00+, even when doing nothing (although my CPU only has a usage of <10%).
Also when i poweroff the laptop sometimes i still have to press (and hold) the power button the power it down.
I guess this is a problem with ACPI. If i disable ACPI (kernel param acpi=off), i can Hibernate the laptop, but obviously i miss other features (no battery information, always have to press the powerbutton to turn it off).
In Jaunty i had none of these problems, i could use hibernate, the power was switched of automatically after shutting down and the system load was always below 0.5 when doing nothing.

When i tried to Hibernate i noticed sometimes a message telling me that the sensors process had blocked for more than 120 seconds. When i ran 'sensors' from the commandline it didn't work either, it just kept waiting (under Jaunty it gave me the sensors information as expected). So I uninstalled the package lm-sensors, but this did not change anything.

Other then this when trying to hibernate i don't get any warning/error. Either the screen blinks and changes back to the screensaver, or i get a black screen with a blinking cursor and nothing happens (and it seems i can only reboot with SysRq BUSIER).

I also tried the info i found in [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31) and [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) but this didn't help either.

Any help/tips are appreciated. So far Karmic has been a rather disappointing experience...

---

### Post by teranex on 2009-11-26
Nobody who can help me in the right direction? Or maybe help me with the correct commands to at least file a bug report? Thx

---

### Post by SiL3NC3 on 2010-04-12
yes, man. you are right. same to me after updated to karmic.
somethings wrong with the acer-wmi interface.

the boot screen tells me, that there was no supported device found ...
also deactivating acpi in grub will not fix this annoying behavior. :(

anybody any hints??

---

