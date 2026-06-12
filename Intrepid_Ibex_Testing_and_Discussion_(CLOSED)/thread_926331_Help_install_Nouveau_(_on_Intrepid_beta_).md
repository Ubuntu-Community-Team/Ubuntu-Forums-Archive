---
title: "Help install Nouveau ( on Intrepid beta )"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dkasak on 2008-09-21
Greetings. I found the page:
[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages) and [https://launchpad.net/~raof/+archive](https://launchpad.net/~raof/+archive) ... which have packages for Intrepid for Nouveau. I've added the line:
```
deb http://ppa.launchpad.net/raof/ubuntu intrepid main
```
to my /etc/apt/sources.list

Then, as per instruction in 1st link, I go:
```
sudo module-assistant auto-install drm-modules
```
 ... and get this:
> drm-modules, what is drm-modules?
Also, I can't see the nouveau package either:
```
dkasak@dkasak:~$ sudo apt-get install xserver-xorg-video-nouveau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-video-nouveau
dkasak@dkasak:~$
```
Searching for 'nouveau' in synaptic returns nothing. I take it I'm doing something wrong?

---

### Post by cariboo on 2008-09-21
After you added the new repository did you update the repository lists eg:

```
sudo apt-get update
```

It might better if you asked question concerning intrepid here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

as there are a lot of smart people there and I've even seen some of the devs answer questions from time to time

Jim

---

### Post by dkasak on 2008-09-22
> **cariboo907 said:**
> After you added the new repository did you update the repository lists

Ah. No I didn't do this. Done now and fixed. Thanks :)

---

