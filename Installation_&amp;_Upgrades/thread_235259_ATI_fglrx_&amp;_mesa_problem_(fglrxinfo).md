---
title: "ATI fglrx &amp; mesa problem (fglrxinfo)"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by dabros on 2006-08-12
Hi,

I try to install the ATI driver following the instructions in

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually)

but fglrxinfo always gives

stavros@stavros-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

instead of the ATI driver information. I can't get rid of that mesa stuff and tried really anything I could find so far ](*,) :

[http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+driver+install](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=ati+driver+install)
[http://www.ubuntuforums.org/showthread.php?t=143283&page=3&highlight=mesa+xgl](http://www.ubuntuforums.org/showthread.php?t=143283&page=3&highlight=mesa+xgl)
[http://www.ubuntuforums.org/showthread.php?t=231039&highlight=compiz+mesa](http://www.ubuntuforums.org/showthread.php?t=231039&highlight=compiz+mesa)
[http://www.darkwizzard.rulz.hu/](http://www.darkwizzard.rulz.hu/) (then click on Articles)

Is there anyone who can help me? My Intention is to set up xgl&compiz. I got it to work just once (fglrxinfo giving the correct output and xgl/compiz working perfectly) but after a reboot everything turned back to that mesa thing and xgl/compiz isn't working.

I have Dapper Drake 32 Bit installed and I'm running a RADEON 9600 XT.

Many thanks in advance
Stavros

---

### Post by dabros on 2006-08-13
Hi,

I really don't know what to do next. The problem I encounter is:

(...)
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(...)
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb6f6f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(...)

listed in the "/var/log/Xorg.0.log" file. I cannot find any solution to that. "lspci | grep AGP" tells me that I have

0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)

So I inserted nvidia_agp in "/etc/modules" and "lsmod" yields

fglrx                 394284  0
nvidia_agp              8348  0
amd64_agp              12356  0
agpgart                34888  3 fglrx,nvidia_agp,amd64_agp

Is there ANYONE who can help?

Stavros

---

### Post by mlakilud on 2006-08-13
Just type in console 
[I]sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv[/I]
reboot
then try *fglrxinfo*
and you should be ok.

---

### Post by dabros on 2006-08-14
Hi,

that didn't work since it's just updating the xorg.conf as I think. But I guess it's rather a driver or Compiz problem concerning the kernel module agpgart since when mesa is shown by fglrxinfo I get

stavros@elektrowinzling:~$ dmesg | grep agpgart
[17179586.380000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.380000] agpgart: Detected AGP bridge 0
[17179586.380000] agpgart: Setting up Nforce3 AGP.

but when fglrxinfo showed the ATI drivers I got

stavros@elektrowinzling:~$ cat /home/stavros/Save/dmesg.log | grep agpgart
[17179590.688000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.688000] agpgart: Detected AGP bridge 0
[17179590.688000] agpgart: Setting up Nforce3 AGP.
[17179590.692000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179611.888000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179611.888000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179611.888000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

So my guess is that we will have to take a closer (and very detailed) look at the initialisation sequence of this module. Is there anyone who can tell me how to do this?

I will be back again on the weekend.
Stavros

---

### Post by dabros on 2006-08-21
Hi,

I found a solution to that problem. BUT: I definitely do not recommend to follow these instructions!

Anyway, I will describe what I did and the problems I obtained. I found the following discussion

[http://www.ubuntuforums.org/showthread.php?t=143855&highlight=1006+fglrx](http://www.ubuntuforums.org/showthread.php?t=143855&highlight=1006+fglrx)

and downgraded my BIOS from 1009 to 1006. My system is ASUS K8N + ATI Radeon 9600 XT. Now XGL and Compiz are working fine but after downgrading my computer obtained some new problems appeared. No ethernet any more and an error message on boot up "Flash Chip not supported - Press F1 to resume". After pressing F1 my system boots but I can't flash the bios any more. Even the FAQ on the Asus web site doesn't have any solution to that problem. I guess a new BIOS-Chip is needed here.

Ok, that's it. Have fun ](*,) 
dabros

---

