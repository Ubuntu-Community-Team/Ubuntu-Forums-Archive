---
title: "problem after ubuntu 10.10 upgrade"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by bhaskar202 on 2011-10-07
I upgraded my ubuntu 10.10.... after completion of upgrade, i reboot my laptop. after reboot, it stuck with a problem. It showing a terminal in which Ubuntu asking for login then after login it shows me to upgrade to ubuntu natty. I dnt want to upgrade to natty. i m not able to skip tht terminal. What should i do.?

---

### Post by ajgreeny on 2011-10-07
I can not see if you are logged in or not in your screenshot, but if you are, what happens if you use command ```
startx
```

It is possible that a new kernel was added in the updates and that is stopping the GUI appearing;  maybe all you need is the graphic driver installed for the new kernel.

---

### Post by bhaskar202 on 2011-10-08
i m getting some kind of message... :( I taken snapshot of the message... "Startx" couldnt solve the problem......

---

### Post by raja.genupula on 2011-10-08
Hi
I hope this thing with your Display driver problems.may be you should update drivers.choose recovery from grub menu and try to boot with failsafex mode or low graphics mode and then try to update them.

---

### Post by mastablasta on 2011-10-08
before the upgrade did you remove any additional graphics drivers? i think raja is onto something here.... try safe modeand reinstall graphics card drivers

---

### Post by bhaskar202 on 2011-10-11
ya first time when i installed ubuntu, i installed graphic drivers for my nvidia then i updated ubuntu... did that caused problem?
guys, i dnt have much knowledge of ubuntu.. how can i reinstall/update my graphic drivers?

Thanx a lot for helping me :)

---

