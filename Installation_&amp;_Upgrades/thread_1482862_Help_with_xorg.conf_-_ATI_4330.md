---
title: "Help with xorg.conf - ATI 4330"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by kingdruid on 2010-05-14
Hopefully somebody can help me out on this. I've been working on this the last 2 days and am about to give up.

I get no display when trying to use radeonhd as my driver.
I have the following MSI nettop:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167039](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167039)
some guy on the reviews page said he got audio to work through HDMI using the PPA driver.

So here is what I did:
1. Installed Ubuntu 10.04LTS
2. Updated Ubuntu
3. entered the following from: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) --> [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) --> [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) -->
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

4. Then I went into the package manager and checked apply all updates and also selected radeonhd.

5. I then copied his config to my machine, but it never boots...
NOTE:(I can still ssh into the box and if I VNC in I get colored lines going down the screen)

6. So I started tweaking my own config and my display works if I switch :
Driver      "radeonhd" to Driver      "ati" under Device
But then I get no audio over HDMI.

Here are my configs and hopefully somebody can help me out with this and tell me what I'm doing wrong.

My config:
[www.thelowridergame.com/new.conf](www.thelowridergame.com/new.conf)
My recent log with radeonhd:
[www.thelowridergame.com/new.log](www.thelowridergame.com/new.log)
Here is the original xorg.conf:
[http://www.paulfour.com/xorg.conf](http://www.paulfour.com/xorg.conf)

---

### Post by kingdruid on 2010-05-14
Tried a few things and its still down:

```

sudo echo "deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA" /etc/apt/sources.list
sudo echo "deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA" /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8844C542
sudo apt-get update
sudo apt-get dist-upgrade

```
Rebooted and had the same results.
BTW: Here is what the screen looks like in VNC:
[IMG]http://img148.imageshack.us/img148/1323/radeonhd.png[/IMG]

So next I tried updating the kernel to the latest RC build:
```

wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb linux-headers-2.6.34-020634rc7_2.6.34-020634rc7_all.deb linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb

```

Now it still doesn't complete, but this time when I VNC I get a white screen instead of the image above. Another thing to note is if I switch it back to Driver ati in xorg.conf and reboot it comes up fine again, but ofcourse not HDMI audio.

---

### Post by kingdruid on 2010-05-14
BTW here are the new logs if anyone wants to take a look and help me out:

with radeonhd driver:
[http://www.thelowridergame.com/XorgNEWKERNELBLEED.0.log](http://www.thelowridergame.com/XorgNEWKERNELBLEED.0.log)

with ati driver:
[http://www.thelowridergame.com/Xorg.0NEWKERNATI.log](http://www.thelowridergame.com/Xorg.0NEWKERNATI.log)

---

### Post by kingdruid on 2010-05-14
Not sure if this helps at all, but here is a parse of the log:

```

root@server:/var/log# cat Xorg.0.log  | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEONHD(0): Unusupported PowerPlayInfo Revision
(EE) RADEONHD(0): Power Management: Cannot get known good chip configurations
(EE) RADEONHD(0): rhdAtomGetDDCIndex: GPIO_DDC Index 5 exceeds maximum 5
(EE) RADEONHD(0): RHDHdmiInit: unknown HDMI output type
(EE) Logitech USB Receiver: failed to initialize for relative axes.
root@server:/var/log# cat Xorg.0.log  | grep "(WW)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0x44fec VRAM End: 0x1000000
0
(WW) RADEONHD(0): [drm] failed to enable new memory map
(WW) RADEONHD(0): RHDCSInit: CS for R600 requires DRI.
(WW) RADEONHD(0): Failed to initalize EXA; disabling acceleration.
(WW) RADEONHD(0): Option "VendorName" is not used
(WW) RADEONHD(0): Option "ModelName" is not used

```

---

### Post by kingdruid on 2010-05-14
Very simple fix!

I didn't even think of trying this until I found a post stating radeon is newer than radeonhd.

So what I did was changed "Driver" "radeonhd" to "radeon"

and just like that it was fixed.....

---

### Post by otis34 on 2010-08-14
I have the same nettop with ati 4330 and realtek alc888 running ubuntu 10.04 and haven't been able to get the sound to work.  I have tried everything i can find and no luck.  What did you finally do to get it to work?  Also the fglrx driver didn't work so i'm running the 2d ubuntu driver.


Any help would be reatly appreciated.

---

### Post by kingdruid on 2010-08-14
All I really had to do was use the "radeon" driver instead of the "radeonhd" driver.

I'm using Xorg so just update your unbuntu completely and modify your xorg.conf to use "radeon"
You also need:
	BusID       "PCI:2:0:0"
        Option   "DRI" "on"   #this is the default in recent radeonhd versions
        Option   "AccelMethod" "EXA" #this is the default in recent radeonhd versions
	Option "Audio" "on"
	Option "HDMI" "all"

Here is my xorg.conf:
[http://www.megaupload.com/?d=NULFWO4Q](http://www.megaupload.com/?d=NULFWO4Q)

The only think that I couldn't get to work good, but it may just be my tv is I can't run it at 1280x720. I'm currently running it at 1024x768 and that looks fine.

If just running updates and modifying your xorg.conf doesn't work you may need to follow these steps first:

So here is what I did:
1. Installed Ubuntu 10.04LTS
2. Updated Ubuntu
3. entered the following from: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) --> [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) --> [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) -->
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update

4. Then I went into the package manager and checked apply all updates and also selected radeonhd.


Another thing I did that may make a difference is I updated my kernel to 2.6.34 and that was because I needed it for the xorg-edgers drivers needed it, but at this point running updates may get you up to that kernel version.

---

### Post by otis34 on 2010-08-14
I updated my linux kernel.  that was all it took.

Thanks a lot.

---

