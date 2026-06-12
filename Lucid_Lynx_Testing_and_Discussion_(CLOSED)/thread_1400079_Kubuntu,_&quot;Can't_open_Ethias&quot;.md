---
title: "Kubuntu, &quot;Can't open Ethias&quot;"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bobmatino17 on 2010-02-06
Well, i reacently installed Kubuntu Lucid, and was pleased with it. I installed the upgrades, and restarted, and when it came time for me to log in, a oxygen themed window popped up on a black screen saying something along the lines of "can not open the ethias theme folder", now if i misspelled ethias, i am sorry. if i hit the ok button, a small white blinking cursor appeared in the top right hand corner of my screen. i opened a virtual machine, and tried to find the problem, but to no avail, could somebody help me with this?

---

### Post by Merk42 on 2010-02-06
Been running it in a VM and I came across the same issue.
Reinstalled via the daily CD, which is only up as far as the 3rd. Currently applying updates to see if that error happens again.

---

### Post by koso on 2010-02-06
There are missing files in that theme. You have 2 options:

1. download manualy theme files, it is described here: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/517803](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/517803)

2. second option is to edit "kdmrc" and choose another theme, if you have some installed

---

### Post by bobmatino17 on 2010-02-06
i would like to thank you for your help.

for anyone else who has this problem...

hit Ctrl+Alt+F2 to bring up a virtual machine (any "F" key works, i just like F2.)

```
wget htt://shtylman.com/stuff/new_kdm_theme.tar.gz
tar -xzvf new_kdm_theme.tar.gz
cd new_kdm_theme
sudo ./install.sh
```

works fine.

---

### Post by xebian on 2010-02-06
Or before you reboot, install some themes in system-settings-> advanced -> login manager

If you are having this issue now, you can boot to root with networking and execute startx (install if not) and then install new themes as above.

The Kubuntu glass theme looks pretty.

---

