---
title: "hardware change"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by sir_skiner on 2007-04-07
hi, is it possible to make valid Ubuntu instalation working on difrent hardware configs? what i think of is to put Ubuntu on one machine, install apropriate packages then screw the hard drive out of it and hook it up to another computer with diffrent mobo, cpu, gpu etc. can it be done to make it somehow working (like rescue mode or something), or i can forget about the idea?
forgive me any languege mistakes.

---

### Post by eapache on 2007-04-07
I think it should work, but I'm not entirely positive. You might want to make sure that the hard drive is plugged into the same spot though (master, slave, etc.).

---

### Post by teaker1s on 2007-04-07
provided you have a suitable kernel to boot, depending on the graphics you may want to set driver to vesa. you may need to reconfigure xserver if you move to different hardware
```
sudo dpkg-reconfigure xserver-xorg
```
also if you have ubuntu setup as ide1 then it must be plugged into ide1 or your mount point in grub will be wrong.

We have some people running on external usb drives- this may be a better solution for regular changing

---

### Post by sir_skiner on 2007-04-08
thanks for your answers!

teaker1s, it's a one shot operation so no regular changing have been planned.
thanks for suggestion about vesa driver - i'll keep it in mind.

do you know about any special packages neded for amd nf3 chipset setup wich might be passed by durring installation process on i965 system?

---

### Post by teaker1s on 2007-04-08
last question, I don't know answer, also to some degree you may get some compatibility issues if for instance you have a peculiar device on one machine

---

