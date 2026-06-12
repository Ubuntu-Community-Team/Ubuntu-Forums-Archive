---
title: "screen goes black while installation"
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by joesatch on 2013-08-24
Hi,

Bought a new laptop today and the first thing I decided to do was to install Ubuntu (Ofcourse!). Did following:

1. Disabled secure boot
2. Disabled intel smart connect
3. Disabled windows 8 fast boot

Created a 12.4.* bootable USB and plugged it in. First screen came up with 3 options and I chose Install Ubuntu + enter. My laptop screen went blank (and black as if it was powered off). Tried installing version 13.x but still the same behavior. Couldn't figure out what the issue was so decided to give Fedora a try (Trying to segregate the problem) but again fell into same problem. The screen went blank.

My laptop config:

HP touchsmart 15-j051sa
i7 4700 mq
Default OS win 8
UEFI enabled boot
NVIDIA GeForce graphics

Could it be a problem with the graphics driver? Any help is deeply appreciated.

Thanks

J

---

### Post by Quackers on 2013-08-24
Try using the nomodeset boot option.
When the live usb starts press F6 key and you should see a purple screen wtith options at the bottom right of the screen. Choose the nomodeset option and see if it then boots.

If this works and you get Ubuntu installed you will need to use the same boot option to boot the new installation but you get to it differently. On startup keep tapping the shift (or esc) key and you should see a grub menu appear with the top item highlighted. At this point press the e key and a new screen will appear. At the end of the kernel line of text (about 4 or 5 lines down) you will see the words quiet splash.  Enter the word nomodeset after quiet splash and then I think it's ctrl x to boot (but it tells you on the bottom of the screen what to press to boot).

---

### Post by joesatch on 2013-08-25
Hey Man,

Thanks for that! Installation worked :) After installation, when I tried to boot ubuntu - it couldnt start X and fell back to command prompt. I changed the grub from command line to include nomodeset permanently and then sudo update-grub. Rebooted hoping to see Gnome but again command prompt. My Xorg.0.log says this:

VESA(0) Initializing int10
[COLOR=#ff0000]VESA(): V_BIOS address 0x0 out of range[/COLOR]
UnloadModule: VESA
Unloadsubmodule: int10
Unloadingmodule: int10
Unloadingsubmodule vbe
SCreens(s) found, but none have a usable configuration
Fatal server errir
Please consult http|://wiki.x.org..
Server Terminated with error (1)

Cheers

J

---

### Post by Quackers on 2013-08-25
When trying to boot the new installation tap the shift key immediately and you should get a grub menu show up with the top item highlighted.
press the e key and you should see another screen appear.
About 4 or 5 lines down you should see the kernel line and it should currently end with "quiet splash" - do you see nomodeset in that line?
If not, type it in after quiet splash leaving a space in between (inside the "" "" if they're there) then do ctrl + x to boot (I think it is, but the screen tells you).
Any improvement?

---

### Post by joesatch on 2013-08-25
hey,

The grub has nomodeset in it permanently now (as you mentioned in your post). Status quo :(.

Regards
J

---

### Post by Quackers on 2013-08-25
Ah, so something else is causing the error with X.
It seems to be complaining about the V_BIOS address being out of range. Sadly I have no idea what that means in this context.
Let's see if anyone else comes up with anything.

---

### Post by joesatch on 2013-08-26
ok no worries. Thanks for you help man.

Any help with the V Bios error??

---

### Post by Quackers on 2013-08-26
Just an idea here, but instead of nomodeset try modeset=0 (that's a zero)
So go to the end of the kernel line and delete nomodeset then type in modeset=0 then ctrl+x to boot.
Any help?

---

### Post by joesatch on 2013-08-26
nope, still the same.

---

### Post by bweinel on 2013-08-26
Just out of curosity, do you have the X vesa and X nouveau drivers installed? You can check this with the following:

dpkg-query -L xserver-xorg-video-vesa && dpkg-query -L xserver-xorg-video-nouveau

Here's how my system looks with a dpkg-query:

```

bill@excalibur:~$ dpkg-query -L xserver-xorg-video-vesa && dpkg-query -L xserver-xorg-video-nouveau
/.
/usr
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/vesa_drv.so
/usr/share
/usr/share/bug
/usr/share/bug/xserver-xorg-video-vesa
/usr/share/doc
/usr/share/doc/xserver-xorg-video-vesa
/usr/share/doc/xserver-xorg-video-vesa/changelog.Debian.gz
/usr/share/doc/xserver-xorg-video-vesa/copyright
/usr/share/man
/usr/share/man/man4
/usr/share/man/man4/vesa.4.gz
/usr/share/bug/xserver-xorg-video-vesa/script
/.
/usr
/usr/share
/usr/share/bug
/usr/share/bug/xserver-xorg-video-nouveau
/usr/share/man
/usr/share/man/man4
/usr/share/man/man4/nouveau.4.gz
/usr/share/doc
/usr/share/doc/xserver-xorg-video-nouveau
/usr/share/doc/xserver-xorg-video-nouveau/README.Debian
/usr/share/doc/xserver-xorg-video-nouveau/copyright
/usr/share/doc/xserver-xorg-video-nouveau/NEWS.Debian.gz
/usr/share/doc/xserver-xorg-video-nouveau/changelog.Debian.gz
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/nouveau_drv.so
/usr/share/bug/xserver-xorg-video-nouveau/script

```

I ran into an similar issue a while back with a 'black screen on boot' when trying to start X and found that the vesa driver wasn't being initialized until later in the boot process. Likely not related to your case though...

cheers,
bill

---

