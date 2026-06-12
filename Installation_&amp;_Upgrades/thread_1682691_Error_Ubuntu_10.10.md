---
title: "Error Ubuntu 10.10"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by PawelBp on 2011-02-06
Hi, I'm new on this forum.
 My problem with the installation of ubuntu 10.10 on my PC . I recorded a CD with Ubuntu 10.10 and then try to install the system. Unfortunately I did not manage it. The disc is Verbatim, recorded a hundred percent well and without errors. Very often stops on an error: error_code 0 x73/0x78. After the turn, I tested the individual parts of a computer and I noticed that the games do not use my AGP graphics card just the onboard system is all about installs and runs. I also noticed that this problem occurs only with the "new" distrostribution ubuntu 9.x. Ubunto 8.04, we managed to properly install the graphics card. Maybe the reason is the Kernel? Here I try to install the graphics card and without it. Sorry for poor quality but I recorded the phone.

Without the AGP card:
[http://www.youtube.com/watch?v=yblJW8IKPTs](http://www.youtube.com/watch?v=yblJW8IKPTs)
Agp card:
[http://www.youtube.com/watch?v=qhw901SJPtg](http://www.youtube.com/watch?v=qhw901SJPtg)

 I will give even the most important, namely computer components:

 Motherboard: Asrock P4i45GV
 RAM: 1024 MB (2x 512)
 Graphics card: Leadtek WinFast A340, the FX 5200 GPU
 Processor: Intel Celeron 2.53 GHz
 HDD: WDC WD800BB-00FJA0

Paul

---

### Post by dino99 on 2011-02-06
always burn cd with the slowest speed

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by PawelBp on 2011-02-06
Yes, the cd was recorded at low speed. Here the problem is not Cd. Using the same CD I installed ubuntu 10.10 successfully on another PC. Ten sam problem mam z ubuntu 9.x, 10.04.

---

### Post by PawelBp on 2011-02-06
Bump

---

### Post by kansasnoob on 2011-02-06
Are you able to run any Linux Live CD/USB? If so it'd be good to see the output of:

```
cat /proc/cpuinfo|head -8
```

```
lspci | grep VGA
```

```
free -m
```

This: "Leadtek WinFast A340, the FX 5200 GPU" appears to be an Nvidia card and there are notes about some of those here:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display)

I tend to go all Intel or VIA here :p

---

### Post by PawelBp on 2011-02-07
Hi,

> 
ubuntu@ubuntu:~$ cat /proc/cpuinfo|head -8
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Celeron(R) CPU 2.53GHz
stepping    : 3
cpu MHz        : 2529.471
cache size    : 256 KB
> ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
> ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           993        880        112          0         94        507
-/+ buffers/cache:        277        715
Swap:         2533          0       2533


I entered these commands using the Ubuntu liveCD 10.10 using the integrated graphics card.

Paul

---

### Post by PawelBp on 2011-02-07
bump

---

### Post by PawelBp on 2011-02-08
bump

---

### Post by PawelBp on 2011-02-09
Bump

---

### Post by kansasnoob on 2011-02-09
If this is due to the AGP card I see there were updates released that should address this (look at posts #169 and #170):

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974)

I'm otherwise a bit unsure :confused:

---

