---
title: "help with updating"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by LT72884 on 2007-12-18
Ok i know that this is a very interesting question. I know how to update, its just that last time i updated with 117 packages it killed my system. I reinstalled ubuntu 7.04 yesterday because for some reason 7.10 jacked up during DL. the first thing i did was install the nvidia drivers using 

sudo apt-get install nvidia-glx

then i used apt-get to grab beryl, beryl-manager and emerald theme manager. the thing is beryl doesnt work. so its either because i have not updated or its just not working right for me. I need to update but there are 117 packages and last time i did that it killed my xserver. so what are the most important updates to get first.

thanx guys

---

### Post by PmDematagoda on 2007-12-18
There should not be any problem with the way the packages are updated automatically, if you have a problem with the GUI you can use the vesa driver to bring up a GUI with which you can repair the normal GUI.

The command used to revert the X-Server configuration back to the vesa driver is:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by LT72884 on 2007-12-18
ok, yeah im in the process of doing that right now. xserver reconfig lists 7 diff driver types and im guessing i need to p[ick the vesa one

---

