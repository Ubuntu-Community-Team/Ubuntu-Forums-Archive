---
title: "Nvidia closed driver + xorg 7.4"
date: 2008-07-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xan.scale on 2008-07-11
with last upgrade ubuntu intrepid use xorg 7.4, with this version of xorg and kernel 2.6.26 the nvidia closed driver can works?

i have also tried with xen patch but noting...

if i use open driver "nv" i can use xorg but, obviously, without direct rendering...

---

### Post by autocrosser on 2008-07-11
There are packaged drivers now available in Synaptic--look at the other threads about Nvidia drivers...Make sure you are using the main repo source. The drivers are almost ready to work with the new Xorg--was expected for yesterday--might be as late as Monday/Tuesday.

---

### Post by plun on 2008-07-11
> **autocrosser said:**
> There are packaged drivers now available in Synaptic--look at the other threads about Nvidia drivers...Make sure you are using the main repo source. The drivers are almost ready to work with the new Xorg--was expected for yesterday--might be as late as Monday/Tuesday.

Yup the driver works just fine with Xorg 7.4

Within Intrepids repo
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nvidia](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nvidia)

The ppa was just updated
[https://launchpad.net/~lrm-intrepid/+archive](https://launchpad.net/~lrm-intrepid/+archive)

I am still on ppa


I also have this within my xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
        
EndSection
```

Fedora 9 users must have it... have not tested without.  :)


Without knowing exactly it seems to be trouble with Jockey.
[http://martinpitt.wordpress.com/2008/07/11/argh-dbus-python/](http://martinpitt.wordpress.com/2008/07/11/argh-dbus-python/)


For a little more experienced user its no problem with this.

---

### Post by plun on 2008-07-11
Followup... new packages accepted.

Example ver 177.13  (cards from 6XXX GPUs and up)
[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003312.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003312.html)

Metapackage name also.

---

### Post by autocrosser on 2008-07-12
Went to a concert last night, so I didn't work with my system ;)

Did the same thing as you--tried xorg.conf without the "device0" mod--went straightaway to vesa driver....as soon as I changed my Device area to to "device0"--all was well. I will experiment with adding my "wanted" options in the device area to see if that was the only change needed........ 

> **plun said:**
> Yup the driver works just fine with Xorg 7.4

Within Intrepids repo
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nvidia](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=nvidia)

The ppa was just updated
[https://launchpad.net/~lrm-intrepid/+archive]("https://launchpad.net/%7Elrm-intrepid/+archive")

I am still on ppa


I also have this within my xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
        
EndSection
```Fedora 9 users must have it... have not tested without.  :)


Without knowing exactly it seems to be trouble with Jockey.
[http://martinpitt.wordpress.com/2008/07/11/argh-dbus-python/](http://martinpitt.wordpress.com/2008/07/11/argh-dbus-python/)


For a little more experienced user its no problem with this.

---

### Post by plun on 2008-07-12
> **autocrosser said:**
> Went to a concert last night, so I didn't work with my system ;)

Did the same thing as you--tried xorg.conf without the "device0" mod--went straightaway to vesa driver....as soon as I changed my Device area to to "device0"--all was well. I will experiment with adding my "wanted" options in the device area to see if that was the only change needed........

Well...   

Also take a look at tseliots [ppa]("https://launchpad.net/~lrm-intrepid/+archive") 

The nvidia-common package makes Jockey working. (ongoing work)

I made a mess and switched over to my patched driver...:)

---

### Post by autocrosser on 2008-07-12
Hmmm--I had not installed nvidia-common.....just installed it & will reboot to look at it. Also, I am going to try putting some of the nvidia options I use back in the Device section--If my hunch is correct, one only needs to have the "device0" for device---we will see.

Have been using tseliots PPA as soon as it opened........

---

### Post by autocrosser on 2008-07-12
OK--update---

1. Jockey still not working with nvidia-common. Using all the current stuff from tseliots PPA....

2. Looks like the only "real" change is the need to define as "device0". I added things back in & xorg came up normally. My Device section looks like:

Section "Device"
    Identifier    "Device0"
    Driver        "nvidia"
    Vendorname    "NVIDIA Corporation"
    Option        "Coolbits"    "1"
    Option        "TripleBuffer"    "true"
    Option        "NoLogo"    "false"
        #Enable 32-bit ARGB GLX Visuals
    Option        "AddARGBGLXVisuals"    "true"
EndSection

---

### Post by tseliot on 2008-07-13
> **plun said:**
> The nvidia-common package makes Jockey working. (ongoing work)
This package has another purpose. You'll see it in the next future.

We'll work on Jockey soon. In the meantime you should install the driver manually.

NOTE: nvidia-glx-96 and nvidia-glx-71 don't work with the new xserver.

---

### Post by foobar1 on 2008-07-13
Anyone get the evdev driver with xorg 7.4?

Everytime I add the entry (the same one I used with 7.3), it just crashes before it shows anything.

---

### Post by tim1 on 2008-07-14
The nvidia drivers don't work for me right now.

During boot, this error occurs:
> 
* Preparing restricted drivers...
mkdir: cannot create directory '/lib/modules/2.6.26-3-generic/volatile': Read-only file system


Any ideas how to fix this?

---

### Post by tseliot on 2008-07-14
> **tim1 said:**
> The nvidia drivers don't work for me right now.

During boot, this error occurs:



Any ideas how to fix this?

I guess it's not related to the NVIDIA driver.

Can you attach your /etc/fstab ?

---

### Post by vhaarr on 2008-07-14
I get that error on boot as well and the nvidia driver works fine for me (running nvidia-glx-177 and friends).

---

### Post by tim1 on 2008-07-14
> **tseliot said:**
> I guess it's not related to the NVIDIA driver.

Can you attach your /etc/fstab ?


Attached to this post.

---

### Post by tseliot on 2008-07-15
> **tim1 said:**
> Attached to this post.

It looks good. There might be errors in the filesystem though. You can type this command so as to reboot and force a filesystem check:
```
sudo shutdown -rF 0
```

---

### Post by tim1 on 2008-07-15
> **tseliot said:**
> It looks good. There might be errors in the filesystem though. You can type this command so as to reboot and force a filesystem check:
```
sudo shutdown -rF 0
```

I checked and the filesystems are fine.

I also filed a bug here, but got no response so far:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/247743](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/247743)

---

### Post by tseliot on 2008-07-15
> **tim1 said:**
> I checked and the filesystems are fine.

I also filed a bug here, but got no response so far:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/247743](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/247743)
Can you set the driver to "nvidia" in your xorg.conf then restart the Xserver so as to reproduce the crash, set the driver back to "nv" restart the Xserver again and post your /var/log/Xorg.0.log?

---

### Post by tim1 on 2008-07-15
> **tseliot said:**
> Can you set the driver to "nvidia" in your xorg.conf then restart the Xserver so as to reproduce the crash, set the driver back to "nv" restart the Xserver again and post your /var/log/Xorg.0.log?

Thank you for the fast response!

I won't attach the log because this time it didn't crash.

I reinstalled nvidia-177 and dkms told me about missing source files, so I installed linux-headers,

The nvidia drivers should probably depend on linux-headers because they are needed for dkms.

---

### Post by tseliot on 2008-07-16
> **tim1 said:**
> Thank you for the fast response!

I won't attach the log because this time it didn't crash.

I reinstalled nvidia-177 and dkms told me about missing source files, so I installed linux-headers,

The nvidia drivers should probably depend on linux-headers because they are needed for dkms.

Weird, it already depends on the headers:

```
Version: 177.13-0ubuntu6
Priority: optional
Section: misc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 8045k
Depends: make, sed (> 3.0), dkms, linux-libc-dev, libc6-dev,
         linux-headers-generic | linux-headers
```

---

### Post by crisnoh on 2008-10-08
> **tseliot said:**
> This package has another purpose. You'll see it in the next future.

We'll work on Jockey soon. In the meantime you should install the driver manually.

NOTE: nvidia-glx-96 and nvidia-glx-71 don't work with the new xserver.

So, are those of us who need the nvidia-glx-96 or -71 driver just screwed, or is there another option available to us?

---

