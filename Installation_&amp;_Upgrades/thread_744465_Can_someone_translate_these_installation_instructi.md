---
title: "Can someone translate these installation instructions (from compspeak to novice)?"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by Redrazor39 on 2008-04-03
[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

when you scroll down to "Installation", there are some instructions I don't understand. I have the driver I need, r5u870_1835.fw as well as a folder called r5u870-0.0+svn50 in my home folder that has a whole bunch of drivers and other stuff. I don't really know how to install the stuff because it doesn't give the exact commands for the terminal. Can someone please help me by posting exact commands to type in the terminal from the instructions below? I have the driver r5u870_1835.fw as the driver I need for my webcam but I don't know what to put in the terminal.

**[edit]  Installation**

This section describes the steps required to install the driver from source, so you can get up and running with your favorite webcam-utilising applications!
[edit] Packages

If you're looking on installation instructions from packages, please see r5u870/Packages.
[edit] Prerequisites

You will need:

    * Either kernel headers, or complete kernel source for your target kernel. Your kernel must be version 2.6.17 or newer.
    * Tools to compile the driver - normally in the build-essentials package or similar. This includes gcc, make, autotools, etc.
    * A webcam supported by the driver (see above).
    * A brain. 

[edit] Compiling

Change the current working directory into the directory in which you have placed the module sources, and execute:
```

$ make
```

You can pass KDIR=<path> to specify a specific kernel location, as such:

```
$ make KDIR=/usr/linux-2.6.23-rc1/
```

[edit] Installing

To install the driver onto the system, simply run:

```
# make install
```

If you ran make with a different kernel path, you should specify it on the command line when installing, too.

Installed modules will be automatically probed for supported devices by the udev coldplug component at boot, and the driver should be automatically loaded on subsequent reboots.

If this is not the case, just add the modulename into a file inside of /etc/modules.d, to load the device on boot.
[edit] Loading the driver

If you installed the driver, you can just run:

```
modprobe r5u870
```

If you wish to load the driver without installing it, you must load the prerequisite modules:

```
modprobe usbcam
modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32		(on 64-bit platforms)
```

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:
```

insmod r5u870.ko

```



For extra important information, I am running Ubuntu 7.10 32 bit

If you need the results of posting lspci or lsusb just ask ;)

---

### Post by dstew on 2008-04-04
> You will need:
* Either kernel headers, or complete kernel source for your target kernel. Your kernel must be version 2.6.17 or newer.You get the kernel headers package from synaptic. You can check your kernel version with```
uname -r
```Then, install the proper kernel headers package. You shouldn't need the whole kernel source.> * Tools to compile the driver - normally in the build-essentials packageSame thing. Install the build-essential package using synaptic. Note, the name is build-essential, not build-essentials.

The rest of the instructions seem pretty straightforward. Post back if you get stuck again.

---

### Post by Redrazor39 on 2008-04-04
Thanks! I did that and my webcam now works in cheese! The only problem is it's not recognized in Camorama OR online camera websites :(

I guess the driver is just incomplete because they didn't want to "bloat the driver" by adding support for other color formats. WTF? How bad would it be? other drivers do the same thing and it works!

---

