---
title: "Karmic Alpha 6 not working in VirtualBox or LiveCD"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-09-23
EDIT: Please look at the edit down the bottom. It has decided to boot randomly now.

Hi there,

I can't get the latest Karmic Alpha 6 amd64 iso image to work either in VirtualBox, or actually on the system as a LiveCD.

When I first boot into it in either this appears on screen:

```

udevd[825]: unknown key 'SYMLINK{unique}' in /lib/udev/rules.d/50-udev-default.rules:3

udevd[825]: unknown key 'SYMLINK{unique}' in /lib/udev/rules.d/50-udev-default.rules:4

stdin: error 0
Shadow passwords are now on.
Generating locales...
  en_US.UTF-8... done
Generation complete.
xserver-xorg postinst note: Configuring xserver-xorg
Using CD-ROM mount point /cdrom/
Identifying.. [24e41de1ad1b1dcd766405d5eb20d4cc-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 9.10 _Karmic Koala_ - Alpha amd64 (20090917.1)'
Copying package lists...gpgv: Signature made Thu Sep 17 02:08:42 2009 UTC using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha amd64 (20090917.1)1/ karmic main restricted
Repeat this process for the rest of the CDs in your set
W: Skipping non-existing file /cdrom/dists/karmic/main/binary-amd64/Packages
W: Skipping non-existing file /cdrom/dists/restricted/binary-amd64/Packages
Removing any system startup links for /etc/init.d/apparmor ...
   /etc/rcS.d/S37apparmor
(Reading database ... 108560 files and directories currently installed.)
Removing gdm-guest-session ...
Purging configuration files for gdm-guest-session ...
udevd[1780]: Name="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:3

udevd[1780]: Name="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:4

udevd[1780]: Name="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:5

* Setting preliminary keymap

....

```

And it just keeps going on from there but never boots.

It seems to install fine, LiveCD doesn't work, but when I try to run it after installing in VirtualBox it just flickers between a whole heap of console error messages and the Karmic wallpaper.

I think it may be a corrupted iso.

EDIT: No okay it has just decided to boot. Random. Could someone look into these errors anyway?

---

### Post by nhasian on 2009-09-23
those errors go away after the latest round of updates.

btw, during boot if it gets stuck at a blinking cursor, and hitting enter brings you to a terminal login, just press Control-Alt-F7 to get back to the graphical login.

this is part of the fun of testing a developmental version of an operating system :)

---

