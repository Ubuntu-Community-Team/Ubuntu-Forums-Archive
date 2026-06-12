---
title: "Nvidia installation problem"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by tkrisz on 2007-07-08
Seems like i managed to screw up something with the nvidia installation.
(Actually the 1st problem was, that it recognized only 800x600 resolution)
So i set the driver to vesa in xorg.conf, and restarted, now i try to install the nvidia-glx package.

It downloads the nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb
Then it attempts to install it but i get the following errors:

```

(Adatbázis olvasása ... Most 133321 fájl és könyvtár telepített.)
Kicsomagolás: nvidia-glx innen: .../nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: hibás feldolgozás: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb (--unpack):
 pre-installation script alfolyamat 2 hibakóddal kilépett
Hibák történtek a feldolgozáskor:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Egy csomag telepítése meghiúsult. Kísérlet a helyreállításra:

```

It is in Hungarian, but it says it was a faulty processing. pre-installation script exited with error code 2.
Finally it says, that installing a package failed. And it makes an attempt to restore.

My current xorg.conf:
```

(...)
Section "Device"
        Identifier      "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
       SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection
(...)

```

Anyone knows what is wrong?

---

### Post by Pumalite on 2007-07-08
Why don't you install from the NVIDIA site? It's easy to do and there is a primer in the site.

---

### Post by tkrisz on 2007-07-08
I tried that way. I was asked to install a libc development package, then it made some NVIDIA kernel module.
Then X failed to start, so i changed the driver in my xorg.conf back to vesa again.

---

### Post by confused57 on 2007-07-08
You could try Method 1 here:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

Probably wouldn't hurt to uninstall any Nvidia drivers you've already installed, before trying the above.

---

### Post by tkrisz on 2007-07-08
Didn't work. seems like once "nvidia" appears for the driver, my X is destroyed.

---

### Post by Pumalite on 2007-07-08
You have to install a 'legacy' driver.

---

### Post by tkrisz on 2007-07-08
Are you sure? GeForce 6200 TurboCache(TM) is listed as included in  nvidia-glx and nvidia-glx-new.

---

### Post by rocknrolf77 on 2007-07-08
Maybe check out envy at :  [www.albertomilone.com](www.albertomilone.com)

---

### Post by Pumalite on 2007-07-08
Make sure you have 'build-essential' installed. This should include: kernel-headers matching your kernel, make, automake, autoconf, latest gcc. Your driver should be in /home/<username>. Make sure you do the installation as root: sudo sh xxxxx

---

### Post by tkrisz on 2007-07-10
Thank you for the answers. envy solved my problem. So i think i should thank tseliot as well.

---

