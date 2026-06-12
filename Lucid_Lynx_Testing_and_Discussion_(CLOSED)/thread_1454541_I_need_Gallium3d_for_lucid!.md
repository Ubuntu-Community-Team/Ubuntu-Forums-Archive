---
title: "I need Gallium3d for lucid!"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluestar14 on 2010-04-14
I only find guides to install for 9.10 and under, and they all assume that nouveau isn't installed... but i just did a fresh install of lucid beta 1 and updated, and i think nouveau(2D) comes with it, can anyone point me to a guide(or give me instructions themselves) that is just for lucid(with nouveau installed)? Plus, i don't even know if nouveau is activated, don't know how to tell...


B.T.W. i have an nvidia geforce mx 100/200 GPU..the propetiary driver worked fine with it in karmic, bu not in lucid, yet

---

### Post by cariboo on 2010-04-14
You could install the nouveau drivers from the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") to get 3D with the open source drivers.

The restricted drivers work well in Lucid, some times you may have to run nvidia-xconfig in a terminal to create an /etc/X11/xorg.conf file, then the next time you reboot things should work as they should.

---

### Post by bluestar14 on 2010-04-14
do i activate restricted driver before or after running nvidia-xconfig, because it said command not ound

---

### Post by cariboo on 2010-04-14
You have to have the restricted drivers installed before using:

```
nvidia-xconfig
```

as it's a part of the driver package.

---

### Post by bluestar14 on 2010-04-15
while i was waiting for ur reply, i installed open source drivers, it worked, but i couldn't blur with it, how do i uninstall open source and installed restricted nvidia driver?

---

