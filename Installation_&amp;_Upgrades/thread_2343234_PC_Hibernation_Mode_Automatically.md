---
title: "PC Hibernation Mode Automatically"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by sram180990 on 2016-11-14
Hi Friends I have a issue my System goes to hibernation mode automatically.
Is there any solution for resolving this issue. If any pls suggest me some ways.
It has become a huge problem.

---

### Post by nikefalcon on 2016-11-15
Most desktops provide an option to suspend when inactive for some time. You can change this in you DE's settings. I assume you are on unity?
Also are you sure its hibernate, and not suspend?

Please post back output of:
```
gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
```

---

### Post by sram180990 on 2016-11-15
Hi it Shows
sreeram@sreeram-GA-78LMT-S2:~$ gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
'suspend'
sreeram@sreeram-GA-78LMT-S2:~$ 


How to Change that setting

---

### Post by deadflowr on 2016-11-15
Run the same command but replace get with range, to see what options you have
```
gsettings range org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
```
then choose the one you want and use set in place of range/get
```
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type option-name-here
```
No need to wrap in quotes. 
Replace option-name-here with whatever the option you want to use, example if you want hibernate, then just type hibernate there.

To revert simply run with reset, in place of get/range/set
```
gsettings reset org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
```

Hope it moves you in the direction you want.
Good Luck

---

### Post by nikefalcon on 2016-11-17
You can change the idle power option and duration under power management options of the GNOME/Unity control center GUI(It might be called settings on Unity..I'm not sure.).
```
unity-control-center 
```
or
```
 gnome-control-center 
```

---

