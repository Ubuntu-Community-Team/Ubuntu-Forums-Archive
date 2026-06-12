---
title: "Kernel panic - Unable to mount root fs"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by tlwest on 2006-08-09
I'm upgrading from Breezy to Dapper - I believe I've followed all the info in the upgrade guide. 

On boot-up, things come to a screeching halt with:

(N.B. - I'm typing this in from notes - I can't post from the system in question . . .)

```
RAMDISK: Compressed image found at block 0
input: AT Translated Set 2 keyboard as /class/input/input0
invalid compressed format (err=2)
Please append a correct "root= " boot option
Kernel panic - not synching: VFS: Unable to mount root fs on unknown-block (3,5)
```

This seems almost, but not quite, like the problem people are having with the boot order naming of hard drives moving around.

I tried the UUID workaround that was mentioned, but the only difference is that the failure refers to unknown-block (0,0) rather than (3,5)

I guess the first issue is to determine if the invalid compressed format error is the real problem, implying a corrupted image, or is it really looking in the wrong place.

Any suggestions as to what to try next?

System info:
Althlon 64
hda 40GB ide 0 Ubuntu, root on hda5
hdb 40GB ide 1 WindowsXP Home
hdc CDRW
hdd CDROM
usb mouse, printer, and joystick (When I get enough of Xorg working to get the accelerated video drivers for VIA working, FlightGear is the next project)

---

### Post by tlwest on 2006-08-11
A follow-up:

entering root=/dev/hda5 at the boot prompt cleared this problem ...
after I cleaned out an old partition on /dev/hda1 that had an old image file in it. Breezy didn't get confused by this, but it looks like it might be more of a lilo issue than disk drive assignemt issues.

gdm comes up, but the mouse seems to be non-functional in Xorg 7.0.0. I'll work that issue in a separate thread if I can't find the resolution.

---

