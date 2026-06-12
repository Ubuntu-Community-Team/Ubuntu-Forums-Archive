---
title: "Switch over to DeviceKit ?"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BGFG on 2009-03-11
Is anyone currently testing it ? I see that it is complete.
[https://fedoraproject.org/wiki/Features/DeviceKit](https://fedoraproject.org/wiki/Features/DeviceKit)

Can i run DeviceKit exclusively in Jaunty? or is Gnome 2.26 still looking at HAL libs ?

palimpsest looks Hott

---

### Post by ghindo on 2009-03-11
I think I remember reading something about DeviceKit making its final release, and that all of its functionality was being integrated into udev

**EDIT:** Read [here](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html).

---

### Post by yanns on 2009-03-11
See [http://martinpitt.wordpress.com/2009/03/11/wanna-touch-devicekit/](http://martinpitt.wordpress.com/2009/03/11/wanna-touch-devicekit/).

There is a PPA ([https://launchpad.net/~ubuntu-desktop/+archive/ppa](https://launchpad.net/~ubuntu-desktop/+archive/ppa)) if you want to try device kit.

---

### Post by gnomeuser on 2009-03-11
Fedora has had DeviceKit available since the F10 development cycle, I used it via the gnome-disk-utility tool as well as the new gnome-power-manager. It works very well for those tasks.

There is still a lot of applications that need to be ported but that will happen over time. We will have a parallel installable HAL/DeviceKit-ish situation for a while I think.

---

### Post by BGFG on 2009-03-11
> **gnomeuser said:**
> Fedora has had DeviceKit available since the F10 development cycle, I used it via the gnome-disk-utility tool as well as the new gnome-power-manager. It works very well for those tasks.

There is still a lot of applications that need to be ported but that will happen over time. We will have a parallel installable HAL/DeviceKit-ish situation for a while I think.

Forgive me if i interpreted the links wrong, but with devicekit being merged into udev, will all this soon run kernel level ?

As to my install, HAL + DeviceKit ?

Thanks also Ghindo and Yanns

---

### Post by gnomeuser on 2009-03-11
> **BGFG said:**
> Forgive me if i interpreted the links wrong, but with devicekit being merged into udev, will all this soon run kernel level ?

As to my install, HAL + DeviceKit ?

Thanks also Ghindo and Yanns

udev is in userspace.. as for your install, just trust your packagers, they will make sure everything works

---

### Post by BGFG on 2009-03-11
Thanks, on another note, Glad to see you on the Ubuntu Team. Although, It was users like you and Asiyu that inspired my to grab a KDE fedora alpha.

---

### Post by gnomeuser on 2009-03-11
> **BGFG said:**
> Thanks, on another note, Glad to see you on the Ubuntu Team. Although, It was users like you and Asiyu that inspired my to grab a KDE fedora alpha.

Inspiration is inspiration, I'll take what I can get. What person take from my pearls of wisdom is for them to decide.

---

### Post by BGFG on 2009-03-11
> **gnomeuser said:**
> Inspiration is inspiration, I'll take what I can get. What person take from my pearls of wisdom is for them to decide.

Modesty becomes you :P, but seriously, since Fedora has such a rich GUI, i wanted to check out the SELinux gui among other things.

Getting antsy waiting for the jaunty release...

---

