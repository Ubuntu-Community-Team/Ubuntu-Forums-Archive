---
title: "Always update to newest HWE Stack"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by ladiko on 2015-04-13
I have a script which runs on several machines. It runs aptitude update and aptitude dist-upgrade regularly. Now I don't want to adjust the script whenever there is a new HWE stack. I just want it to be updated automatically.

So i need a way to determine the newest HWE-Stack name, wheather if it's none (for the current ubuntu release vivid f.e.) or if it's trusty, utopic or soon it will be vivid. Then i run aptitude install -y xserver-xorg-lts-$NEWEST_HWE_STACK etc.

Is that possible?

---

### Post by dino99 on 2015-04-13
by no means i'm a script fan, but lshw might help to identify it. But that script could be fatty if you want it able to identify everything vs a known limited  list which is easier to manage. By the way you may not have so many cases concerning drivers.

---

### Post by Keith_Helms on 2015-04-14
You'd have to code some smarts into your script.

If I run the command
```
apt list xserver-xorg-lts*
```
on my system, I get back the following results:
```
xserver-xorg-lts-precise/trusty-updates 3:6 amd64
xserver-xorg-lts-quantal/trusty-updates 3:6 amd64
xserver-xorg-lts-raring/trusty-updates 3:6 amd64
xserver-xorg-lts-saucy/trusty-updates 3:6 amd64
xserver-xorg-lts-trusty/trusty-updates 3:6 amd64
xserver-xorg-lts-utopic/trusty-updates,now 1:7.7+7ubuntu2~trusty1 amd64 [installed]
```

Now if I really wanted to, I could parse those results and look for a higher release name that is not marked "installed".  The script would have to be smart enough to know what the codenames are for the newer releases, or at least know where to go and look them up.  It would also have to be smart enough to know that if "vivid" is installed then you shouldn't try and install "trusty" which would be a downgrade.  Currently you can rely on the first letter of the codename being higher for each release.   What happens when we get to the next release after "Zesty Zebra" or whatever the heck they will call it?

---

