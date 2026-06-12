---
title: "Nvidia kernel driver for a geforce 8"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by ravalox on 2007-04-27
Has anyone here tried to use the nvidia linux binary directly from their website?  I've got a geforce8 and feisty doesn't support that yet with the nvidia-glx package, I've tried to load it as a kernel module in /etc/modules and it still won't seem to load, X will not start.  But if I build it from the .run file from their website, then startx, everything works fine.  So I can build a working module, I just can't seem to figure how you get feisty fawn to modprobe it properly without having to rebuild it every time I reboot.

---

### Post by 1ino1eum on 2007-04-27
try installing nvidia-glx-new
then you need a workaround.
try a search nvidia-glx-new
in the forum
the nvidia-glx-new dont work "out of the box" for the 8800 .
but after the workaround, it's cleaner than teh .run file

---

### Post by Syke on 2007-04-28
The Linux IA32 9755 drivers at:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

worked perfect for me on my 8800.

---

