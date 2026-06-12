---
title: "Need some help installing soundcard Realtek HD"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by micdac on 2010-09-20
Hello,
I just've install Ubuntu 10.04 now and trying to make my sound  work. I've and Gigabyte E43 DS3L with Realtek HD Audio, anyway maybe  the following link will be useful: 
[http://www.alsa-project.org/db/?f=d548bf06960cea3d1b4a4d2e8019b70f9f2868cb](http://www.alsa-project.org/db/?f=d548bf06960cea3d1b4a4d2e8019b70f9f2868cb)
I  tried to follow the readme intstructions but I think I am missing  something called Kernel Header since I got an error message after the  compiling. 
after sudo make i got following message:

copying file alsa-kernel/core/info.c
/home/michael/Desktop/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/michael/Desktop/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/michael/Desktop/realtek-linux-audiopack-5.15/alsa-driver-1.0.23'
make: *** [include/sndversions.h] Error 2
michael@michael-desktop:~/Desktop/realtek-linux-audiopack-5.15/alsa-driver-1.0.23$ ^C
michael@michael-desktop:~/Desktop/realtek-linux-audiopack-5.15/alsa-driver-1.0.23$ 


I've tried to install 
sudo apt-get install build-essential kernel-headers-$(uname -r)but its also not working.

I would be happy about some help, thanks

update: I just would like to see SPDIF with my Realtek HD working.

---

### Post by soebbi on 2010-09-21
I'm using Ubuntu 10.10 beta on a Sony Vaio S12V9E and I have same problem as you.

According to the SUPPORTED_KERNELS-file, the kernels used by Ubuntu 10.* are unsupported:
```
The alsa-drivers in this package are designed for the following kernels:

 - Vanilla 2.6.29 or earlier
 - Vanilla 2.4.31 or earlier
 - Vanilla 2.2.26 or earlier

It's not guaranteed that they work with any newer version than above or modified kernels by distributors.
```

Maybe some brave soul is brave enough to dig into the code and have a look where it breaks?

---

