---
title: "Desktop double entries on 14.04 LTS"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2015-04-07
Just did a dual boot install of Win7 and Ubuntu 14.04 LTS.
All went well with both, as was expected.

The only bug is with this double look in desktop upper bar.
How do I remove the upper right middle portion so that only the portion in the upper far right shows, as it should?

[IMG]http://s28.postimg.org/96622kn25/Screenshot_from_2015_04_07_23_30_27.png[/IMG]

---

### Post by dino99 on 2015-04-08
looks like you are logged with unity; do you get that issue also with a gnome-shell session ?
maybe you have added some plugin; check either ubuntu-tweak-tool or unity-tweak-tool

at last a 'sudo dpkg --configure -a' may help, and glance at the logs too

---

### Post by cybrsaylr on 2015-04-08
Am using unity, know nothing about using any gnome-shell session.
Added no plugin to Ubuntu yet, that I know of.

Did try to reload unity by running...
Code:
> setsid unity
but it didn't help.

This happened to a friend's 4-5 year old Acer Veriton z290g 'all in one' model PC, who wanted Ubuntu installed as a dual boot with W7.

So far both W7 & Ubuntu run fine.

---

### Post by cybrsaylr on 2015-04-08
Where is this ubuntu-tweak-tool or unity-tweak-tool?
I  can't find it.

code:   'sudo dpkg --configure -a'  

gave me nothing.

---

### Post by grahammechanical on 2015-04-08
Here are two commands to try

```
unity --reset icons
```

This command will automatically restart. I have just tested it and it does restart.

```
killall unity-panel-service
```

That command will clear the top panel of its icons and immediately replace the icons. 

Regards.

---

### Post by efflandt on 2015-04-08
Notice that an entire vertical portion of the screen is replicated, as though something in X thinks you have a 4:3 screen and replicates that to fill in the wide screen. So I don't know if that has something to do with screen configuration or video driver or virtual desktop. What does Settings > Displays show for your screen resolution vs. its actual resolution?

---

### Post by cybrsaylr on 2015-04-08
grahammechanical, both your codes did nothing.
First code gave error message: the reset option is now deprecated.
Second code made top bar turn off , then back on with same duplicate icons as in OP screenshot.


efflandt, here's what Settings > Displays show:

---

### Post by cybrsaylr on 2015-04-09
efflandt, just discovered when dropping Resolution from 1366 x 768 (16:9) down to 1280 x 720 (16:9) the duplicate top bar reverts to single icons as it should!

All top icons and vertical icons are slightly larger but ok.

Is this a fix then?

---

