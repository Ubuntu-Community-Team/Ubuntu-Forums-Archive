---
title: "Upgrade 8.04 LTS to 10.04 LTS - NVIDIA"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-03-04
I upgraded from 8.04 to 10.04 (finally)

I have a NVIDIA GeForce 7600 GS

There is no graphic display anymore.

I tried many things, did all not work. What is the correct solution?

startx  starts the opening sound and displays [Input not supported]

CTRL-ALT-F2 shows in the last line:
(FE) Failed to initialize GLX extension (Compatibilbe NVIDIA X driver not found)

sudo apt-get install nvidia-glx-new linux-restricted-modules

This brings me 
...
Package nvidia-glx-new is not available, but is referred bo by another package, .....


How can Ii solve my graphic problem?


bye

Ronald

---

### Post by mikewhatever on 2011-03-04
The naming of nvidia packages has changed, try 'nvidia-current' instead. Running 'nvidia-xconfig' might also help.

---

### Post by sikander3786 on 2011-03-04
Removing your existing xorg.conf and reconfiguring the graphics might also help.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot now
```

---

### Post by Keith_Beef on 2011-03-07
> **sikander3786 said:**
> Removing your existing xorg.conf and reconfiguring the graphics might also help.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot now
```

I have a similar problem, reported in [this post]("http://ubuntuforums.org/showpost.php?p=10527737&postcount=121").

I removed the xorg.conf file, rebooted, and I get a 1920 × 1050 display. When I try doing the dpkg-reconfigure as you suggested, the display goes back to something like 640 × 480, just like it does when I use sudo nvidia-xconfig.

K

---

### Post by ELMIT on 2011-03-07
I dowloaded the NVIDIA driver from their web site and installed it, 

I run sudo sh NVIDIA-Linux-x86_64-260.19.36.run and start x again with start gdm and it works, .. till the next reboot!!! Then I have to do the entire procedure again.

Whwat do I miss to keep it permanent?

---

