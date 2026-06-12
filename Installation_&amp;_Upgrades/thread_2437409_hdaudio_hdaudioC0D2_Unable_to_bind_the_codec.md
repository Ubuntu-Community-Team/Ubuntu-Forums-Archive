---
title: "hdaudio hdaudioC0D2: Unable to bind the codec"
date: 2020-02-23
forum: Installation &amp; Upgrades
---

### Post by dbee on 2020-02-23
Booting up takes ages on my laptop with ubuntu 19.10. It goes to black screen and outputs
> 
hdaudio hdaudioC0D2: Unable to bind the codec

before eventually booting up into gnome.

I want to boot up faster ....

I've edited the grub file to include 'nomodeset' or else it won't boot up at all ...

can anyone help  ?

---

### Post by dbee on 2020-02-26
bump :-)

---

### Post by CelticWarrior on 2020-02-27
If you need 'nomodeset'... You have a problem with the graphics.

> It goes to black screen and outputs

Definitely a problem with graphics.

This error message
```
hdaudio hdaudioC0D2: Unable to bind the codec
```
may or may not be related with the graphics as well (HDMI audio), but one step at the time... 

Please post your Ubuntu version and hardware specifications, namely the graphics. I suspect you have a Nvidia graphics that needs proprietary drivers (you may keep using 'nomodeset'  to have a graphical environment; after installing the Nvidia drivers it won't be needed and the system should boot and run smoothly).

---

### Post by dbee on 2020-02-29
OK I installed nvidia-driver-435. hopefully that'll help...

should i remove nomodeset from grub ?

---

### Post by CelticWarrior on 2020-02-29
Yes, you should remove it. Otherwise it won't load the drivers even if installed. 'nomodeset' is a workaround only. Its purpose is to give a generic graphics mode and override the default open-source driver that isn't fully compatible with your card. Oncve the Nvidia drivers are installed and loading properly, you no longer need 'nomodedset'.

---

