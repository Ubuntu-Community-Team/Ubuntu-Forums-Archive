---
title: "'ubuntu-drivers' not identiging my video card?"
date: 2018-06-24
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-06-24
I just installed my first 18.04 and am in the process of configuring it. My motherboard has an Nvidia Graphics chip and I want to install the nvidia driver for it. Running ```
#ubuntu-drivers devices
#
``` returns no output. I thought "ubuntu-drivers" was supposed to identify the chip-set and recommend the correct drivers.

---

### Post by Bashing-om on 2018-06-24
rsteinmetz70112; Hummmm .........

My result:
```

sysop@x1810:~$ sudo ubuntu-drivers devices
[sudo] password for sysop: 
== /sys/devices/pci0000:00/0000:00:0f.0/0000:06:00.0 ==
modalias : pci:v000010DEd0000128Bsv00003842sd00002712bc03sc00i00
vendor   : NVIDIA Corporation
model    : GK208B [GeForce GT 710]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

sysop@x1810:~$

```

what shows :
```

lspci -k | grep -EA2 'VGA|3D'

```

as there
[INDENT][INDENT]has to be a reason
[/INDENT][/INDENT]

---

### Post by rsteinmetz70112 on 2018-06-24
I just installed from the server iso then installed the ubuntu-desktop and some other stuff. I'm still getting used to everything.
Some stuff installed on the desktop iso may not be installed, but if the command "ubuntu-drivers' is installed, then I'd think all of the dependencies would be installed. the command runs for a few seconds before returning no a prompt.

```
# lspci -k | grep -EA2 'VGA|3D'
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
	Subsystem: ASRock Incorporation C61 [GeForce 7025 / nForce 630a]
	Kernel driver in use: nouveau
```

I just ran the command on another machine still running 16.04 with the same motherboard and it returned the correct information
I've had problems with the nouveau driver in the past so I use the Nvidia drivers.

---

### Post by Bashing-om on 2018-06-24
rsteinmetz70112; Ouch !

That old card:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
 is no longer supported:
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

But, you can still get that 304 version driver from our trusted PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by rsteinmetz70112 on 2018-06-24
Adding the ppa solved the problem of the device not being identified. It now recommends the nvidia-304, but that won't install due to unmet dependencies. For now I guess I'll continue using the nouveau driver and see how that works out 
```
The following packages have unmet dependencies:
 gvfs : Depends: gvfs-daemons (>= 1.36.1-0ubuntu1)
        Depends: gvfs-daemons (< 1.36.1-0ubuntu1.1~)
 libgtk-3-0 : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                       libwayland-egl1
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```



Still it seem like Ubuntu-drivers should give some kind of output, even if no drivers are found.

---

### Post by Bashing-om on 2018-06-24
rsteinmetz70112; Maybe -

You are booted into the wayland session  ??
As yes, no nvidia support in wayland for old devices.

what shows:
```

systemctl status gdm
echo $XDG_SESSION_TYPE

```

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

