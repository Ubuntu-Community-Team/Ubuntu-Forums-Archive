---
title: "Can't install Nvidia-96"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by pumpkinslayer on 2011-05-09
After upgrading from 10.10 to 11.04 the nvidia drivers are all messed up again. My video card requires the nvidia-96 drivers. These were installed 

If I try to install the drivers through the Ubuntu Software Center it tells me there are dependecies for the nvidia-96 driver that could not be found (or something like that).

Using Synaptic Package Manager it tells me these packages need to be removed to install the nvidia-96 drivers.

```
ubuntu-desktop
xorg
xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-geode
xserver-xorg-video-i128
xserver-xorg-video-740
xserver-xorg-video-intel
xserver-xorg-video-mach64
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nouveau
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-qxl
xserver-xorg-video-r128
xserver-xorg-video-radeon
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo
```

Should I just go ahead and install the drivers through Synaptic Package Manager and remove those packages as it suggests?

The removal of ubuntu-desktop and all of xorg sounds a little ominous (I'm new to all this). Any help would be appreciated. What next step should I take?

Oh, when I try to install using the command line I get:

```
nvidia-96 : Depends: xorg-video-abi-8.0 but it is not available
            Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
```

---

### Post by pumpkinslayer on 2011-05-09
After doing:

```
sudo apt-get remove --purge nvidia*
sudo apt-get update
sudo apt-get install nvidia-96
```

I went back to the Additional Drivers and saw that Nvidia-96 was there in the list again. However, when trying to activate it I got a warning that I have "broken packages".

---

### Post by ivkowalenko on 2011-07-14
> **pumpkinslayer said:**
> After upgrading from 10.10 to 11.04 the nvidia drivers are all messed up again. My video card requires the nvidia-96 drivers. These were installed 

If I try to install the drivers through the Ubuntu Software Center it tells me there are dependecies for the nvidia-96 driver that could not be found (or something like that).

Using Synaptic Package Manager it tells me these packages need to be removed to install the nvidia-96 drivers.

```
ubuntu-desktop
xorg
xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-mouse
xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse
xserver-xorg-input-wacom
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-ark
xserver-xorg-video-ati
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-fbdev
xserver-xorg-video-geode
xserver-xorg-video-i128
xserver-xorg-video-740
xserver-xorg-video-intel
xserver-xorg-video-mach64
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nouveau
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-qxl
xserver-xorg-video-r128
xserver-xorg-video-radeon
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-vesa
xserver-xorg-video-vmware
xserver-xorg-video-voodoo
```Should I just go ahead and install the drivers through Synaptic Package Manager and remove those packages as it suggests?

The removal of ubuntu-desktop and all of xorg sounds a little ominous (I'm new to all this). Any help would be appreciated. What next step should I take?

Removing ubuntu-desktop removes all the default desktop-geared pacakges, and xorg is the graphic interface, so unless you like playing around in the command line interface all the time, it'll basically remove everything you want to use. I'm sitting on the same problem right now.

---

### Post by User3k on 2011-09-20
I know this post is a few months old. But I was wondering if they fixed this problem yet? I am having the same issues as the OP.

---

### Post by MAFoElffen on 2011-09-20
> **User3k said:**
> I know this post is a few months old. But I was wondering if they fixed this problem yet? I am having the same issues as the OP.
As I remeber helping people on this problem back a while ago... post 2 has the fix.  Ignore the error saying that you need to remove the desktop.

People who pursued that, ended up removing and reinstalled their desktops previous to trying to install their drivers... and had the same exact error again.  This error popped up with Ubuntu, Kubuntu and Xubuntu.  Strange- I thought it was over with, meaning I haven't seen it come up in a few months.

---

