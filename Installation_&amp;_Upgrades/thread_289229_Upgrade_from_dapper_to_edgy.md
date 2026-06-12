---
title: "Upgrade from dapper to edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by elgobo on 2006-10-30
After upgrading from dapper to edgy, I'm still in trouble with my linux box:

[LIST=1]
[*]The analog joystick connected to the sblive! gameport doesn't work anymore. I get "analog.c: Unknown joystick device found  (data=0x2, pci0000:00:07.1/gameport0), probably not analog joystick." at modprobe, no matter the map= parm I give. Needless to say, with dapper it worked out of the box
[*]The splash screen is **dark**... I can't even see the progress bar, while the ubuntu logo is near black
[*]The ntp client no longer updates my box clock.
[*]Why the Option "IgnoreAbi" doesn't work in xorg.conf? This is **really** important for my Matrox G550 video card. I (painfully!) worked it around, but I still can't use opengl, as I get a "libGL warning: 3D driver claims to not support visual 0x4b" even with glxinfo
[/LIST]

I'm seriously thinking to downgrade to dapper, which was great for me. [-( 

Did anyone else experience similar problems? :-?

---

### Post by knowmad on 2006-10-31
I am experiencing the same splash screen problems with Edgy using a G550 on amd64 hardware. X won't even start for me due to a bug in the xserver-xorg-video-mga driver (see [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721)).

Given that this problem was reported almost 2 months before Edgy was released and hasn't been addressed by the maintainer, I'm seriously considering either downgrading to Breezy or replacing my video card with an Nvidia card. I'm going to try the Matrox compiled driver next to see how that works although I don't know that it supports xserver 7.1.1 which comes with Edgy.

BTW, there were some workarounds mentioned in the bug reports such as using the framebuffer (matroxfb_base) or using an uploaded deb that contains a more recent release for i386. Unfortunately none of these solutions worked for me. Hopefully we'll hear something from the developers soon.


William

---

