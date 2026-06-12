---
title: "Adding a kernel module to DKMS?"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by syko21 on 2009-01-15
Is there any way to add say the nvidia driver to DKMS so that it can be recompiled after any kernel updates? (A nudge in the direction of useful information would also be appreciated.)

---

### Post by bash on 2009-01-15
Maybe the official DKMS ressources from Dell are of help to you:

[http://linux.dell.com/dkms/](http://linux.dell.com/dkms/)

---

### Post by syko21 on 2009-01-15
Ok so I went through the man page and I'm trying to configure the dkms.conf, here's what I have so far (copying the format from the vboxdrv configuration I also found on my system.)
```
BUILT_MODEULE_NAME=nvidia
DEST_MODULE_LOCATION=
PACKAGE_NAME=nvidia
PACKAGE_VERSION=180.22
AUTOINSTALL=yes
POST_BUILD=


```
I don't know what to put (if anything for POST_BUILD) or for DEST_MODULE_LOCATION.

---

### Post by glasen on 2009-01-15
Here is a sample configuration file i've written for the "linux-phc"-patch :

```
PACKAGE_NAME="linux-phc"
PACKAGE_VERSION="0.3.2-2.6.27"
CLEAN="rm -f *.*o"
BUILT_MODULE_NAME[0]="acpi-cpufreq"
DEST_MODULE_LOCATION[0]="/updates/linux-phc-0.3.2-2.6.27"
AUTOINSTALL="yes"

```

For your driver you must change the file to something like this :

```
PACKAGE_NAME="nvidia-kernel-module" (Or similar name)
PACKAGE_VERSION="180.22" (driver-version)
CLEAN="rm -f *.*o"
BUILT_MODULE_NAME[0]="nvidia" (Name of the kernel module without ".ko")
DEST_MODULE_LOCATION[0]="/updates" (Destination of the compiled module in directory /lib/modules/kernel_version)
AUTOINSTALL="yes"
```

There must be a directory named "nvidia-kernel-module-180.22" under "/usr/src", which contains the source code for the kernel module and the file "dkms.conf".

After this, just type in the following instructions :

```
dkms add -m nvidia-kernel-module -v 180.22
dkms build -m nvidia-kernel-module -v 180.22
dkms install -m nvidia-kernel-module -v 180.22
```

---

### Post by RAOF on 2009-01-15
> **syko21 said:**
> Is there any way to add say the nvidia driver to DKMS so that it can be recompiled after any kernel updates? (A nudge in the direction of useful information would also be appreciated.)

Is there some reason the official nvidia-180-kernel-source package isn't working for you? ;)

**EDIT**: If you'd like to see a simple dkms-using package, then the nouveau-kernel-source package currently sitting in Jaunty's NEW queue is pretty simple.

---

### Post by syko21 on 2009-01-15
I just upgraded to jaunty last night and since I started using intrepid I used to compile the nvidia driver manually (I like using the latest from nvidia). Since I switched to testing jaunty I knew there would inevitably be kernel updates so I wanted to add a way to automatically update my driver. I have not yet tried the nvidia-180-kernel-source package, I didn't know it existed. This information will still be useful after release though since I will continue to use the beta nvidia drivers.

PS> Thank you glasen, your information was very helpful!

---

### Post by gtdaqua on 2009-01-15
> **syko21 said:**
> I just upgraded to jaunty last night and since I started using intrepid I used to compile the nvidia driver manually (I like using the latest from nvidia). Since I switched to testing jaunty I knew there would inevitably be kernel updates so I wanted to add a way to automatically update my driver. I have not yet tried the nvidia-180-kernel-source package, I didn't know it existed. This information will still be useful after release though since I will continue to use the beta nvidia drivers.

PS> Thank you glasen, your information was very helpful!

Ubuntu repositories are indeed updating to latest NVIDIA stable as they come out. Current Latest stable by Nvidia is 180.22 and is available in ubuntu via package nvidia-glx-180. Simply doing a 'sudo apt-get install nvidia-glx-180' will take care of everything you need including automatic DKMS automatic updates during kernel updates.

When the next kernel is released, you can update by apt-get upgrade and during the kernel installation, dkms will jump in and recompile the nvidia driver for you.

However, if you want to try the NVIDIA's beta version, then you have to do things manually.

To see what nvidia version will be installed by ubuntu, type 'sudo apt-get install nvidia-glx-180 -s'. This will simulate an installation but not install in which you could find the exact package version that will be installed by aptitude.

---

