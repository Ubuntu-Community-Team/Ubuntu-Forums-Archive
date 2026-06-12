---
title: "btnx can't find config files."
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by emshains on 2008-09-13
I tried to install btnx from source to get my VX revolution tilt buttons to work. First I tried installing with apt-get but it can't seem to find the right package even if I have added the repos. So I tried installing from source, and I succeeded. Now when I try to launch it, it displays:```
FATAL: Error inserting uinput (/lib/modules/2.6.24-19-generic/kernel/drivers/input/misc/uinput.ko): Operation not permitted
 btnx: Modprobe uinput failed. Make sure the uinput module is loaded before running btnx. If it's already running, no problem.
 btnx: Could not read the config manager file: No such file or directory
Segmentation fault

```

When I try to run it as root it puts out: ```
 btnx: uinput modprobed successfully.
 btnx: Could not read the config manager file: No such file or directory
Segmentation fault

```

I've got all the dependencies it needs, atleast all the dependencies that were asked by configure.

---

### Post by Partyboi2 on 2008-09-13
deleted

---

### Post by Partyboi2 on 2008-09-13
The packages you need to install if you add[FONT=monospace]
[/FONT]```
deb http://ppa.launchpad.net/daou/ubuntu hardy main
deb-src http://ppa.launchpad.net/daou/ubuntu hardy main
``` to your source.list is
```
sudo apt-get install btnx btnx-config
``` then after it is installed run
```
sudo btnx-config
```

---

### Post by warthogism on 2008-12-11
```
Warning: configuration file for configuration "Default" does not exist. Deleting configuration.
Aborted
```

This is what i get when trying to start btnx-config....any help?

---

### Post by Partyboi2 on 2008-12-11
try removing /etc/btnx/btnx_manager and /etc/btnx_config_Default then running the config again
```
sudo rm /etc/btnx/btnx_manager 
sudo rm btnx_config_Default 
``````
sudo btnx-config
``` If that does not work then try reinstalling the package
```
sudo apt-get --reinstall install   btnx btnx-config
```then
```
sudo btnx-config
```

---

### Post by emshains on 2008-12-13
Heck, after I installed btnx, it fills dmesg up with all kinds of usb BS!

---

