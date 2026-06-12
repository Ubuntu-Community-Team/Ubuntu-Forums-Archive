---
title: "sigh... I hate nVidia drivers..."
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by spowell398 on 2007-05-31
Ok... I thought I would start over with a new post about the nVidia 8800GTS drivers. I have attempted using both the restricted devices manager and envy, neither of which worked. Either way I tried installing it, the picture below pops up. ](*,) Is there any way that I can install the nVidia drivers and them work correctly? I am extremely new to this so please bare with me... I have even tried to reconfigure the xserver an I would get the second picture below pop up with the terminal part at the bottom. (which I have no idea how to use) Can anybody out there help me?

P.S. I'm running the 32bit feisty fawn.

---

### Post by lH)4~mK0e on 2007-05-31
Start here?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Sounds to me like the module isn't there, or it failed to build properly and therefore will not load on boot.

---

### Post by spowell398 on 2007-05-31
um. ok... should I try to use the restricted devices manager again? Sorry, Im really dumb at this...

---

### Post by renzokuken on 2007-05-31
when the error pops up, hit Ctrl+Alt+F1 to get to a tty terminal screen.

now log-in and run

```
sudo nano /etc/X11/xorg.conf
```


use the arrow keys to go to the Section "Device" part and change the "driver" line from

Driver  "nvidia"     (i'm guessing at nvidia here)

to

Driver  "vesa"

press Ctrl+X, Y and enter to save,

then type

```
sudo reboot
```

you should now have X working (if in a low res state) and you will find it easier to try and get the nvidia drivers working. which should actually be very easy

---

### Post by spowell398 on 2007-05-31
ok... let me try that.

---

### Post by spowell398 on 2007-05-31
I went into that and changed driver... which turned out to be nvidia and changed it to versa. when I saved the changes and rebooted the exact same thing happened. ](*,) Any other ideas? I did notice that if I went to change the x-server settings that the default video driver was changed to versa but it still didn't work. I have another post on the installation section that also pertains to this... you need any more information about what is going on... thanks for the help.

---

### Post by Zyphrexi on 2007-05-31
I recognize that problem, try my HOW-TO and see if it helps. Also let me know if it does so I can add your card to the list.

[HOW-TO: fix nvidia-glx]("http://ubuntuforums.org/showthread.php?t=445965")

---

### Post by stchman on 2007-05-31
> **spowell398 said:**
> Ok... I thought I would start over with a new post about the nVidia 8800GTS drivers. I have attempted using both the restricted devices manager and envy, neither of which worked. Either way I tried installing it, the picture below pops up. ](*,) Is there any way that I can install the nVidia drivers and them work correctly? I am extremely new to this so please bare with me... I have even tried to reconfigure the xserver an I would get the second picture below pop up with the terminal part at the bottom. (which I have no idea how to use) Can anybody out there help me?

P.S. I'm running the 32bit feisty fawn.

I was under the impression that Ubuntu does not supports the 8800 Nvidia cards.

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg92481.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg92481.html)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/107831](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/107831)

Maybe Gutsy will fix the 8800 problem or Ubuntu might make a new kernel before then that supports the 8800 cards.

---

### Post by hessiess on 2007-05-31
have you got a older card to use untill this is fixed? do as above but try nv insted of vesa

---

### Post by spowell398 on 2007-05-31
I tried putting the # before all of the text but that didn't work either. I will now try to put nv instead of versa or nvidia. Just wondering but do you think that my windows drivers are messing with this? I'm dual booting it with Windows except for on two different disks. Ubuntu works on install except for the screen resolution isn't high enough and some of the screen savers are choppy. I play BF2 online on xp and it works smooth as silk with maxed settings so I know its not the card. Is it just that this card is too new for Ubuntu?

---

### Post by spowell398 on 2007-05-31
THANK YOU Hessiess. That worked. Now my screen resolution is 1280 by 1024 but now the 3d screen savers aren't working at all. Do I just need to install the nvidia drivers now or is there something else I have to do to fix the 3d stuff?

---

### Post by madscientist on 2007-05-31
That's the difference between the "nv" (free) and "nvidia" (proprietary) video drivers.  The former were written by the free software folks, from scratch, and so they work very well: robust, supported, etc.... BUT they can't take advantage of any of the proprietary, undocumented parts of the video card--basically advanced 3D.

This is a microcosm of the difference between open source and proprietary software, and that's why it's best, whenever possible, to buy hardware from vendors that publish ALL the hardware specifications, or even publish open source drivers themselves.  Of course, for high-performance video cards the choices here are extremely limited, unfortunately.

Anyway.  You will not be able to use the advanced 3D effects until you can get the proprietary drivers to work.  There is an open source effort, called [Nouveau]("http://nouveau.freedesktop.org/wiki/"), which is working to create an open source nVidia driver that supports acceleration, but it's not yet ready for use.

---

### Post by spowell398 on 2007-05-31
Ok. thanks... so probably I wouldn't want to try using the nvidia.com drivers or any other drivers for now unless they fix the problem... ok. I can deal with a few less screen savers for now... Its not like i'm going to be laying bf2 on Ubuntu anyway... THANKS A TON!!! :o

---

### Post by hessiess on 2007-05-31
just put up with no 3d for a wile ,nividia are unlickly to relese linux drivers at the same time as the windows ones becose windows has the majoraty of the market. thay will probaly relese new drivers eventualy.

to get the most out of the newist cards you would haft to run vista, witch althow ive never used it, i have red nothing but bad things about it! so its junk!

hope you get this working propaly, eventualy!

---

### Post by spowell398 on 2007-05-31
Thanks again for all your help everybody. Yeah I can deal with the screensavers and stuff, thats no big deal. I like linux alot because mostly of its safety. I'm going to install avg free linux version on my rig to keep it even more safe. nVidia has drivers... but right now they ARE JUNK!!! I'm even having some problems with the Windowz drivers right now. (bf2 shadows all edgy and unsmooth) Thanx for all the help. :D

---

### Post by heldal on 2007-06-01
The 8800GTS definitely works on Feisty, but there are a couple important issues with the nvidia-driver as supplied in ubuntu-packages. These issues will probably be resolved soon, but are at least still present in driver-packages for version 2.6.20.5-16.28 of the linux kernel :

1. Ubuntu-packages include tools/scripts  to handle 3 different versions of Nvidia's driver. Originally each version of the driver includes its own revision of the kernel-module. Scripts used load the right module depend on certain files which are not removed automatically if you try to switch between "legacy", "current" and "new" versions of the driver.  So /lib/linux-restricted-modules/.nvidia_legacy_installed _OR_ /lib/linux-restricted-modules/.nvidia_new_installed must be present to use nvidia-glx-legacy or nvidia-glx-new. Neither of those 2 files must be present when nvidia-glx is used. If you have tried multiple versions of the driver you need to check the contents of the /lib/linux-restricted-modules directory. The scripts to handle the kernel-module are located in the linux-restricted-modules-common package and will affect module loading also if choose to install the driver you can download from Nvidia. Users who do this, or have the most recent cards (8500/8600) and thus need the most recent beta-driver, must ensure that the nvidia-related hidden files in /lib/linux-restricted-modules are removed.

2. An x-server-module is missing that at least is required for the 8800 cards. Check /var/log/Xorg.0.log to see if the x-server complains about a missing "wfb" module. You can also check if you have the file /usr/lib/xorg/modules/libwfb.so or a symlink pointing to some version of libwfb.so. If not, you can extract the single missing file from Nvidia's original driver-distribution to avoid replacing the entire ubuntu packages.

---

