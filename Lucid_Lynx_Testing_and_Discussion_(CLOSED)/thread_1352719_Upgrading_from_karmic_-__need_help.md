---
title: "Upgrading from karmic -  need help"
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by papangul on 2009-12-11
I tried to dist-upgrade from karmic today and got the following list of packages to be removed while upgrading:
```
Calculating upgrade... Done
The following packages will be REMOVED:
  compiz-wrapper deluge-core gnome-games kdepim-runtime-data
  kdepim-runtime-libs4 kubuntu-artwork-usplash libesd-alsa0 libfaad2-0
  libgnomekbdui4 libkabcommon4 libkdcraw7 libmetacity0 lxde-settings-daemon
  pulseaudio-module-udev python-lazr-restfulclient python-lazr-uri same-gnome
  usplash usplash-theme-ubuntu xserver-xorg-input-kbd xserver-xorg-input-wacom

```

I searched the lists regarding 'xserver-xorg-input-kbd' found the following information, but don't get it. Please advise. 
> From archive at ubuntu.com  Mon Dec  7 14:00:33 2009
From: archive at ubuntu.com (Ubuntu Installer)
Date: Mon, 07 Dec 2009 14:00:33 -0000
Subject: [ubuntu/lucid] xserver-xorg-input-keyboard 1:1.4.0-1 (Accepted)
Message-ID: <20091207140033.13962.17772.launchpad@cocoplum.canonical.com>

xserver-xorg-input-keyboard (1:1.4.0-1) experimental; urgency=low

  [ Timo Aaltonen ]
  * New upstream release.
  * Bump the build-dep on xutils-dev (>= 1:7.5~1).
  * Build against Xserver 1.7.

  [ Cyril Brulebois ]
  * Upload to experimental.

Date: Mon,  07 Dec 2009 13:58:17 +0000
Changed-By: Timo Aaltonen <tjaalton at ubuntu.com>
Maintainer: Debian X Strike Force <debian-x at lists.debian.org>
Origin: Debian/unstable
[https://launchpad.net/ubuntu/lucid/+source/xserver-xorg-input-keyboard/1:1.4.0-1](https://launchpad.net/ubuntu/lucid/+source/xserver-xorg-input-keyboard/1:1.4.0-1)
-------------- next part --------------
Origin: Debian/unstable
Format: 1.7
Date: Mon,  07 Dec 2009 13:58:17 +0000
Source: xserver-xorg-input-keyboard
**Binary: xserver-xorg-input-kbd**
Architecture: source
Version: 1:1.4.0-1
Distribution: lucid
Urgency: low
Maintainer: Debian X Strike Force <debian-x at lists.debian.org>
Changed-By: Timo Aaltonen <tjaalton at ubuntu.com>
Changes: 
 xserver-xorg-input-keyboard (1:1.4.0-1) experimental; urgency=low
 .
   [ Timo Aaltonen ]
   * New upstream release.
   * Bump the build-dep on xutils-dev (>= 1:7.5~1).
   * Build against Xserver 1.7.
 .
   [ Cyril Brulebois ]
   * Upload to experimental.
Files: 
 10eb95f6557f3374bad589ab19e7dd1f 1629 x11 optional xserver-xorg-input-keyboard_1.4.0-1.dsc
 69b243fe16b9ae69e64704cbcdee0910 17195 x11 optional xserver-xorg-input-keyboard_1.4.0-1.diff.gz
 fc836be5364d80604cb11f4daacceb23 355862 x11 optional xserver-xorg-input-keyboard_1.4.0.orig.tar.gz

---

### Post by ranch hand on 2009-12-12
Why not use the daily build or the A1 LiveCD or Alt. install Cd?

---

### Post by garvinrick4 on 2009-12-12
I used this from 9.10 to 10.04 and it worked fine. Lot of options this was the one I used.



 sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by wilee-nilee on 2009-12-12
I just loaded a thumb with a full install it seems a more prudent way of trying it, since I have a dual boot of W7 and karmic already.

---

### Post by garvinrick4 on 2009-12-12
Thumb or CD it still doe's not save changes, it is all still a Live CD. Now a 16 gig
Thumb drive with partitions with boot and swap that is a full blown OS that is independent
of HD yet picks up WIFI or Wired on any CPU at boot, now that is what I would like to see.

---

### Post by wilee-nilee on 2009-12-12
> **garvinrick4 said:**
> Thumb or CD it still doe's not save changes, it is all still a Live CD. Now a 16 gig
Thumb drive with partitions with boot and swap that is a full blown OS that is independent
of HD yet picks up WIFI or Wired on any CPU at boot, now that is what I would like to see.

The usb creator will load the ISO and create a persistent that will save updates and additions.

I did a full install on a 16 gig thumb but only used about 6 gigs I just want to test it out.

---

### Post by Gina on 2009-12-12
I'm using 2GB ones with LiveCD made with the USB startup disk creator and that seems quite adequate - everything saved - I can use it just like a full install except that it isn't as fast.  But when you've trashed the MBR on HD it gets you up and running and online without resorting to another computer.

---

### Post by phillw on 2009-12-12
> **Gina said:**
> I'm using 2GB ones with LiveCD made with the USB startup disk creator and that seems quite adequate - everything saved - I can use it just like a full install except that it isn't as fast.  But when you've trashed the MBR on HD it gets you up and running and online without resorting to another computer.

I played with the pre-alpha on a 2GB persistent USB, to make sure it was happy with my hardware. It was - So I've given it 13GB of hard disk on an extended partition - rsync'd my 9.10 ~home over and it's a happy little bunny - even uses my existing /swap area.

Makes Grub2 a bit long, tho !! (Win, 9.10, 10.04 & Memtest) - I haven't bothered to tidy the entries in Grub2 up yet.

Phill.

---

### Post by Gina on 2009-12-12
Glad you've got yours working - I can run in CLI but loads of errors if I try to run the X server.  Nvidia Geforce 9400GT graphics.

---

### Post by clivejo on 2009-12-12
Gina try the nVidia beta driver on their website.

---

### Post by garvinrick4 on 2009-12-12
Can you install it's own boot on the Thumb drive without using the HD's-MBR so it
can be sent to use on another computer? Or travel with you to be used on another
computer?

I have a triple boot,  lucid and Koala and a Windows 7 that came installed on laptop already, desire
to make stable 9.10 to send pre-loaded and operating to family member. Can use gparted
to partition Thump drive. Need to find way to keep a boot on thumb dr.  gparted likes to think it should add boot to existing MBR.

---

### Post by ranch hand on 2009-12-12
Go into your bios and turn off your other drives.  Most bios will let you do this anymore.

Or you could, while the box is off, just unhook the buggers.

The bios route is, by far, the best option.

---

### Post by Gina on 2009-12-12
> **clivejo said:**
> Gina try the nVidia beta driver on their website.I've tried but Firefox won't download it - displays it instead! :(  Tried it on two machines too.  Any suggestions, please?

---

### Post by cariboo on 2009-12-12
Strangely enough, you need flash working to download the driver.

---

### Post by Gina on 2009-12-13
> **cariboo907 said:**
> Strangely enough, you need flash working to download the driver.I do have flash working.  I use it with the BBC iPlayer.

---

### Post by coatzin on 2009-12-13
> **Gina said:**
> I do have flash working.  I use it with the BBC iPlayer.

Use right click and save as...

---

### Post by Gina on 2009-12-13
> **coatzin said:**
> Use right click and save as...Do you mean "Save Link As"?  There is no "Save As".  If so, where should I save the link?  

This is strange - I've never had a problem saving a download before.  I've tried this on three different machines now and two different versions of Ubuntu.  I guess I could try Win XP :(

A bit later...  Tried FF in XP - just the same.  Tried IE - just the same!!

---

### Post by ranch hand on 2009-12-13
> **Gina said:**
> Do you mean "Save Link As"?  There is no "Save As".  If so, where should I save the link?  

This is strange - I've never had a problem saving a download before.  I've tried this on three different machines now and two different versions of Ubuntu.  I guess I could try Win XP :(
That would be one of the things I would just live with out.  I decided, for me, that if MS was the only way to do something, it did not need doing.

Yes, I have an attitude.

---

### Post by coatzin on 2009-12-13
> **Gina said:**
> Do you mean "Save Link As"?  There is no "Save As".  If so, where should I save the link?  

This is strange - I've never had a problem saving a download before.  I've tried this on three different machines now and two different versions of Ubuntu.  I guess I could try Win XP :(

A bit later...  Tried FF in XP - just the same.  Tried IE - just the same!!

yes, save link as (sorry... I don't have english as firefox default language)... save anywhere... then install.

when you save link as... you save a file named NVIDIA-Linux-x86_64-195.22-pkg2.run, don't you?

---

### Post by Gina on 2009-12-13
> **coatzin said:**
> yes, save link as (sorry... I don't have english as firefox default language)... save anywhere... then install.

when you save link as... you save a file named NVIDIA-Linux-x86_64-195.22-pkg2.run, don't you?I didn't think so but I've just "Saved Link As" and it's downloading 39MB so I think you're right :)  

You're never too old to learn something new :lolflag:

Sorry for doubting you, and sorry for not remembering to allow for English not being your first language :)  I didn't get a clue, your English is perfect.

---

