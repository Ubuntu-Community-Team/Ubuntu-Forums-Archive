---
title: "Black screen after kernel upgrade in Hardy"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by R33D3M33R on 2010-03-03
Yesterday I upgraded the kernel from 2.6.24-26-generic to 2.6.24-27-generic (I'm still using Hardy Heron). After upgrade I uninstalled the previous Nvidia driver installation:

```
sh NVIDIA-Linux-x86-96.43.13-pkg1.run --uninstall
```

and did a install with

```
sh NVIDIA-Linux-x86-96.43.13-pkg1.run
```

After that I started kdm and everything seemed to work fine untill I rebooted. Then I got black screen. The driver didn't freeze the system, because I was able login and when trying some commands (pressing Tab it beeped like it should).

I booted in recovery mode, installed the driver again, and it worked again -- untill reboot, and so on. I tried 96.43.16, and no difference.

After another uninstall i removed everything nvidia related (*.ko) and tried installing. Didn't change anything.
I tried blacklisting modules in /etc/default/linux-restricted-modules-common/

```
DISABLED_MODULES="nv"
```

It didn't work. Only lines suspicious in Xorg.0.log are:

```

[config/hal] couldn't initialise context: (null) ((null))

```

I tried to uninstall NVIDIA proprietary drivers and installing the drivers from repositories with Envy - it doesn't work.
I tried to purge xserver-xorg-core and hal, but it didn't work.
I added nvidia to /etc/modules but it didn't work.

The drivers do work if I boot and start xserver with NV driver, then shutdown kdm, change driver to "NVIDIA" and start kdm.

I have no idea what to do now and I'm completely lost. Before I purge the new kernel and reinstall the old one, I'm asking for help.

---

### Post by R33D3M33R on 2010-03-04
Another detail is that the monitor just doesn't turn on. Because if i turn off the computer by pressing power button, the monitor turns on and shutdown progress appears :o -> it shutdowns normally. So something must be wrong with kdm.

I have tried the same driver with the same kernel on another computer with geforce 2 mx 400, xfce and it works flawlessly :o.

---

### Post by R33D3M33R on 2010-03-04
Ok, I tried clean install, and now installed only the 96.43.05 drivers from the repository. I'm running kernel 2.6.24-19-generic now and it still doesn't work. Even if I put the Geforce 2 MX in, the monitor gets no signal.

After I reset BIOS and set ACPI to off, the monitor turns on, but i see only garbage on the screen.

Still this error:

```
[config/hal] couldn't initialize context: (null) ((null))
```

There are two things that bother me: 
1. The Xubuntu 8.04 machine with this driver, geforce 2 MX and latest kernel ( 2.6.24-27-generic) works flawlessly
2. I was using Hardy with the same configuration and drivers for almost 2 years and now it suddenly stopped working? :o

---

### Post by R33D3M33R on 2010-03-08
Well, the only thing that remains is to try XFCE. In case you are wondering why I don't use latest versions: I can't use anything newer than 8.04 because of this bug: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/429370](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/429370)

edit: installing XFCE doesn't work.

---

### Post by R33D3M33R on 2010-03-23
Today I updated the packages by using the standard procedures (sudo apt-get update, sudo apt-get upgrade). They were kernel upgrades in the updates so I gave the nVidia drivers (96.43.16) another try and it works flawlessly. :twisted:
I guess I'll never do apt-get update again on this system, it might break everything again :(

---

