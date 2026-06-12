---
title: "nvidia driver trouble"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by kelxso on 2006-11-28
ive gone from fedora core 4 to linspire to ubuntu, and ubuntu has gotten me the closest to successfully installing the nvidia drivers.](*,)  the how to pages never seem to help me, im begining to think theres something im just not getting. i have a (MSI GeForce 5200FX w 128mb) in my agp slot can someone give me an in-depth step-by-step instruction please:)

---

### Post by angkor on 2006-11-28
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Method 1 would be the easiest to try.

Good luck and if you need to enable the universe / multiverse repositories check System -> Administration -> Software Sources (edgy)

If you already have these repos enabled this usually works for me:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx
```

```
sudo nvidia-xconfig enable
```

Log out and log back in again.

---

### Post by cutlerite on 2006-11-28
I tried that code, and this is what it said:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

is there a different place I can look? ](*,)

---

### Post by rpradeep on 2006-11-29
As the above mentioned thread is highly kernel version dependent I recommend you to use the original nvidia drivers.

For your error message you must type sudo before all commands.

[https://help.ubuntu.com/community/NvidiaManual?highlight=%28CategoryCleanup%29](https://help.ubuntu.com/community/NvidiaManual?highlight=%28CategoryCleanup%29)

---

### Post by taurus on 2006-11-29
[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by kelxso on 2006-12-04
i found my solution in this thread 
[http://www.ubuntuforums.org/showthread.php?t=308559](http://www.ubuntuforums.org/showthread.php?t=308559)
:-D

---

