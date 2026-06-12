---
title: "Installation stuck on SYSLINUX"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by Jowzer on 2013-07-11
I have searched all over the internet, without a working solution:
I try to install Ubuntu via USB on my netbook.
I put the ISO on my usb with unetbootin, and try to start it on my laptop.
It is stuck on the screen SYSLINUX 4.03 2010-10-22 EDD Copyright etc. etc.
I tried a few things:
- remove 'ui' from the isolinux.cfg
- removed syslinux.cfg, renamed isolinux.cfg to syslinux.cfg and the folder isolinux to syslinux
- formatted USB to Fat32
- formatted USB to NTFS
- three different iso's/versions

I got no working OS on the netbook, and no CD-ROM drive.
It boots from USB, but I can't get past the SYSLINUX screen.
Please help!

---

### Post by ubfan1 on 2013-07-11
Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.

---

### Post by oldfred on 2013-07-11
Welcome to forums.

If md5sum is ok, it just may be the installer your used or the flash drive.

If you do not have an Ubuntu with its installer.
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

 Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by Cheesehead on 2013-07-11
All syslinux does is tell the system to load the kernel and the init process (in that order).
Does your syslinx.cfg show the accurate location of these?

Loading the kernel from USB can take a minute or two, especially over an older USB1.1 connection.
did you give the system long enough to load?

Try creating the USB with unetbootin again.
Look for any error messages.
Give the system enough time to load.
If it still fails, paste your syslinux.cfg here.

---

### Post by Jowzer on 2013-07-12
Thanks for the replies! :)
I MD5summed my iso, and it was ok.
I tried both manually downloading ISO's and downloading via Unetbootin.
Now I also tried pendrivelinux, but it also doesn't work.

It's USB2.0, and I alway wait for like 5 minutes or so.
I get no errors at all.
Here's my syslinux.cfg:
```
# D-I config version 2.0include menu.cfg
default vesamenu.c32
prompt 0
timeout 50


# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo



```

Note: I also tried it without the 'ui' and the '#' on the last line of syslinux.cfg

---

### Post by oldfred on 2013-07-12
It looks like your include menu.cfg line is in the first line and should be a separate 2nd line.

My isolinux.cfg in 12.04.2
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

---

