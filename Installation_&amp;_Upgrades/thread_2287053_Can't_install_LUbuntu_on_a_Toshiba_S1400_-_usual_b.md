---
title: "Can't install LUbuntu on a Toshiba S1400 - usual blank display - getting nowhere"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by leigh3 on 2015-07-16
Hi
I'm trying to get an old Toshiba Satellite S1400 to run "any" linux but keep getting frozen and or blank screens when installing.
I have around 20 DVD/CDROM's of various flavours of linux and the only 2 I can get to work are mint (mate) and mint (XFCE) both of which are too slow to be usable.

I put LUbuntu 14 on a another HP machine which has a  slower CPU and it works great, so trying to install 15.04 on the S1400-103

I've tried "live" runs with various kernel options (vga=771, nosplash, noapi) but always end up with a blank display.
I think linux kernel is running as pressing the power off button causes the laptop to shutdown after a few seconds and eject the boot DVD.
Pressing any ctrl+alt+F(any) or esc, or shift or any other keys does nothing.

Started to look at the blank display sticky posting but at 101 pages I'm not sure if I'll find the problem so just wondered if anyone else with an old Tosh Sat 1400 got there's working ?

Spec
Celeron CPU 1.3GHz
Ram 750Mb
Display = Trident Cyber 8820 (Supports VESA mode upto 795 according to Megeia hardware inspection software)

Hope someone can give me a few pointers

Thanks

Leigh

---

### Post by sudodus on 2015-07-16
You may have better luck with an ultra light linux distro, for example Wary Puppy, TahrPup or Tiny Core.

You might have problems with the graphics drivers, that support for your graphics is dropped in newer versions of Linux. If this is the case things might work better with a community re-spin based on Ubuntu 12.04 LTS, for example LXLE, Bento or Bodhi Linux.

---

### Post by oldfred on 2015-07-16
My Toshiba laptop is a "lot" newer. From 2006 with dual core and a whopping 1.5GB of RAM. But it uses the Intel internal video.

But in my desktop with Ubuntu 14.04 I ran a list of available drivers.
fred@trusy-ar:~$ dpkg -l|grep xserver-xorg-video
And one was:
```
ii  xserver-xorg-video-trident                            1:1.3.6-0ubuntu5                                    amd64        X.Org X server -- Trident display dri
```

You may need a generic boot parameter, but you add it like nomodeset in this link.
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 Generic parameters: 
xforcevesa
nouveau.modeset=0

You may also need others.
Also VGA modes are obsolete.

 vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub, examples shown not sure what 795 is any more:
GRUB_GFXMODE=1024x768
replace "set gfxmode=auto" by "set gfxmode=1366x768"

---

### Post by leigh3 on 2015-07-16
Thanks for the info, will do some more reading and try a few options.
Have tried Puppy/simplicity and another one which i can remember - Puppy is OK but prefer a better GUI, Simplicity (Netbook or desktop) will not boot for some reason.

Leigh

---

### Post by sudodus on 2015-07-16
Have a look at the following thread about old hardware (and linux)

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

