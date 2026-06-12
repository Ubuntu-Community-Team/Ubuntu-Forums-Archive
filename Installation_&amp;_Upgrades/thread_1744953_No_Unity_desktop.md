---
title: "No Unity desktop"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by mpjbrennan on 2011-04-30
I chose the try Ubuntu option on the Live CD and it boots straight into Gnome 2. Does this mean my hardware cannot support Unity?

Patrick

---

### Post by sikander3786 on 2011-04-30
Might be the required graphics drivers are not available.

Please run this command in Terminal under Applications > Accessories and post the complete output.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by davidself1001 on 2011-04-30
I don't have a /nux dir in /usr/lib.  Could that be an installation issue?  I can't get unity to work either.

---

### Post by sikander3786 on 2011-05-01
> **davidself1001 said:**
> I don't have a /nux dir in /usr/lib.  Could that be an installation issue?  I can't get unity to work either.
Can't be sure but it can be. If it is a fresh install, why not re-install and see if that solves the issue.

---

### Post by ssherwood on 2011-05-01
Hi guys,

I have the same issue, but I can login to the default 'Ubuntu' session but the only display I get is the default Ubuntu background nothing else. I have performed several clean installs of 11.04 and the same issue occurs over and over again. This issue only occurs on my desktop system which uses a nVidia graphics whilst my netbook uses Intel graphics and the Unity session works perfectly.

I will try this >>sikander3786<<

```
/usr/lib/nux/unity_support_test -p
```

Thanks Stephen (SSHERWOOD)

---

### Post by ssherwood on 2011-05-01
Hi guys,

I have issue the command 

```
/usr/lib/nux/unity_support_test -p
```
and the results (attachment) say that may system is able to support unity but no unity shows.

what should i do from here.

Thank Stephen (SSHERWOOD)

---

### Post by pontu on 2011-05-01
same problem here, made a thread about my discoveries ([http://ubuntuforums.org/showthread.php?t=1745529](http://ubuntuforums.org/showthread.php?t=1745529)) looks like some driver/software issue where everything is reported ok, incl. Unity support, but it doesn't work somehow

i also have no 3D output (black window) from glxgears, can you check yours?
```
glxgears
```
if same the please try this too
```
vblank_mode=0 glxgears
```

---

### Post by ssherwood on 2011-05-01
thanks for the input I have tried the ```
glxgears
``` and did not receive a blank window.

sorry :(

Stephen, (SSHERWOOD)

---

### Post by ssherwood on 2011-05-01
Im going to forget about the unity as now the ubuntu classic is flashing and i cant use the gnome desktop... time for a clean install. might go back down to 10.10.

Thanks anyway guys

---

### Post by davidself1001 on 2011-05-01
I solved this issue.  In my case unity wasn't even installed.  I went to synaptic and installed it and all was fine.  Don't know why it didn't get installed.  I did an upgrade instead of clean install so that may have been the issue but you would think you'd get some indication if the main new feature in the release doesn't get installed.

---

