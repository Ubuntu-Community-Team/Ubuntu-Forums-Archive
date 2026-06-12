---
title: "X Server not loading after install"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by GaMz on 2007-05-28
I recently tried installing Ubuntu 7.04 on my HP Laptop. I booted up the LiveCD and it booted up perfectly. I proceeded to install. It installed successfully and prompted me to restart. Booting up it gives me an error with the x server or something. I'm a relatively new person with Linux so I don't really know how to fix this problem.

It allows me to read and diagnose to find the error. It says that it can't find "nvidia" modules or something like that. It only allows me to use the command line; the GUI does not load up.


Here are my system specs in case you need them to help me out:
Intel(R) Core(TM) 2 Duo T5600(1.83GHz/2MB L2Cache)
15.4" WXGA BrightView Widescreen (1280x800)
256MB NVIDIA(R) GeForce(R) Go 7400
2GB DDR2 System Memory (2 Dimm)
80GB 5400 RPM
8X DVD+/-R/RW w/Double Layer Support
Intel(R) PRO/Wireless 3945ABG Network Connection


Any help would be appreciated, I can't do much on here without the GUI :(


Edit: I tried the following commands to download the nvidia drivers: 
```
sudo wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```


When I typed in the second command it said I did not have the required compiled kernel.


Please help, I'm really trying to get this set up.

---

### Post by GaMz on 2007-05-28
Ok, I fixed it. (Sorry for the double post)

This is what I used
```
sudo aptitude update && sudo aptitude install nvidia-glx
```

Then

```
sudo nvidia-xconfig
```

Then I restarted using:

```
sudo /etc/init.d/gdm restart
```

Then the GUI loaded up :D

---

### Post by 4lej4ndr0 on 2007-05-29
You Are My Hero!!!


Thankzzz From Chile!!!!

---

