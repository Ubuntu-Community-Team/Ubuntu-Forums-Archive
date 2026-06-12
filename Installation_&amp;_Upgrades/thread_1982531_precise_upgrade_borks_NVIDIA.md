---
title: "precise upgrade borks NVIDIA"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2012-05-18
Ive tried to upgrade oneiric -> precise and X only givces me a 640x 480 display 
with the nvidia-current driver installed , additional HW drivers  says 
"this driver is activated but not currently in use "
nvidia-xconfig writes an xorg.conf file,

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

 but the display is still 640x480
lsmod | grep nv  returns nothing 

and now cant get nvidia  configured and working
Google told me that nvidia-current  may be broken with precise, so ive uninstalled it  (and got a graphic display of 640x480 with nv driver)
but when i got to synaptic and try to install nvidia-173 it tells me there are broken packages

synpatic -> fixed broken packages says
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
 ive been to the nvidia website and tried to install 
NVIDIA-Linux-x86-96.43.16-pkg1.run
 but this too fails 
 anyone knwo how to get X/ nvidia [GeForce4 MX 4000/ precise pangolin working together   ?

---

### Post by darkod on 2012-05-18
What if you try to install nvidia-current?

I don't have nvidia but I have seen that package used with 12.04 and reported working. Hopefully it will install it for you.

---

### Post by haresear on 2012-05-18
Nvidia legacy drivers 173 & 96 are unfortunately not compatible with Precise. Take a look at:

[http://www.nvnews.net/vbulletin/showthread.php?t=179489]("http://www.nvnews.net/vbulletin/showthread.php?t=179489")

---

### Post by pdc124 on 2012-05-19
oh dear
:(
No joy with nvidia-current. max screen resolution is still 640x 480

There is a comment in the NVforum thread that someone downgraded xorg.
How do i do that ?

otherwise i'll have to replace the card I think

---

### Post by papibe on 2012-05-19
Hi pdc124.

Have you tried nouveau? It is the nvidia open source driver, and It is already installed on your system.

To do that, uninstall all nvidia packages, and then rename your X configuration file:
```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.old
```
Then restart.

Tell us how it goes.
Regards.

---

### Post by pdc124 on 2012-05-19
I removed  nvidia-common (and it says ubuntu-desktop!) 
and then restarted . After a couple of goes ive got a 1920XX1280 display and it is basically fine. 
Some of the effects are a bit slow and id like to turn them off ( this is a work/WP machine ) but cant see how. But if not , I can live with it. 
I dont have a new /etc/X11/xorg.conf 

I think this is the relveant bit of hwinfo.

27: PCI(AGP) 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: VCu0.YDI4LoFx8+7
  Parent ID: vSkL.ITQqGs0XM26
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce4 MX 4000"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0185 "GeForce4 MX 4000"
  Revision: 0xc1
  Driver: "nouveau"
  Driver Modules: "drm"
  Memory Range: 0xf8000000-0xf8ffffff (rw,non-prefetchable)
  Memory Range: 0xf0000000-0xf7ffffff (ro,non-prefetchable)
  Memory Range: 0xf9000000-0xf901ffff (ro,non-prefetchable,disabled)
  IRQ: 16 (56200 events)
  Module Alias: "pci:v000010DEd00000185sv00000000sd00000000bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Driver Info #1:
    XFree86 v4 Server Module: nvidia
    3D Support: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

---

### Post by coffeecat on 2012-05-19
> **pdc124 said:**
> I removed  nvidia-common (and it says ubuntu-desktop!) 
and then restarted . After a couple of goes ive got a 1920XX1280 display and it is basically fine. 
Some of the effects are a bit slow and id like to turn them off ( this is a work/WP machine ) but cant see how. But if not , I can live with it. 
I dont have a new /etc/X11/xorg.conf 

Ubuntu-desktop is a meta-package which doesn't do anything except make sure that you have everything installed for the ubuntu desktop. It is sometimes removed when you uninstall things. It's probably best to re-install it, but just make sure it doesn't try to re-install anything nvidia-related. I don't think it will, if all the nvidia packages are removed. And by the way, papibe mentioned removing all nvidia packages, and you only mentioned nvidia-common. You need to remove nvidia-current and nvidia-settings

If you are finding effects a bit slow, try logging into the Unity 2d desktop from the login screen. You might find that better to work with.

You won't have a xorg.conf file. It's not necessary with the nouveau driver.

---

### Post by haresear on 2012-05-19
A Geforce4 card with the nouveau driver I doubt can run Unity 3D at all. If you are using Unity it is probably already 2D. You can check with the terminal command 'echo $DESKTOP_SESSION'.

Personally I find the nouveau driver with my older FX5200 card pretty sluggish even using Unity 2D. The gnome-fallback desktop session (or even the gnome-classic) seems faster for me.

---

### Post by OrangeVixen on 2013-04-23
Just wanted to post an update, I personally was able to do a fresh install of Precise 12.04, then went to settings and hardware, and installed the "current/recommended" Nvidia driver (I have a GEForce).

Rebooted and no problems.

I think the problem comes with upgrading, I was not able to upgrade from Lucid to Precise because of the broken/held packages bug. I think 12.04 can only be installed fresh.

The NVidia (proprietery) driver seems to have been updated by the folks at NVidia.

---

