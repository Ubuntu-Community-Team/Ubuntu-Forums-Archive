---
title: "fpit dependancy error"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by redxine on 2010-04-29
I've just finished installing lucid and started setting up my tablet and all went well until I tried to install the fpit driver. I tried installing it from synaptic but it says it has to remove ubuntu-desktop, xorg, xserver-core -- some very important things and then says "xserver-xorg-input-fpit: Depends: xserver-xorg-core but it is not going to be installed."

I tried downloading the deb and extracting the driver manually but Xorg complains with:

```
(II) LoadModule: "fpit"
(II) Loading /usr/lib/xorg/modules/input/fpit_drv.so
(II) Module fpit: vendor="X.Org Foundation"
(II) UnloadModule: "fpit"
(II) Unloading /usr/lib/xorg/modules/input/fpit_drv.so
(EE) Failed to load module "fpit" (module requirement mismatch, 0)
(EE) No input driver matching `fpit'
```

Sounds like a repository problem. Can I fix this somehow or will I need to wait for an update?

---

### Post by pmsoft1 on 2010-05-01
I'm experiencing the same on my LG C1 tablet.

---

### Post by Favux on 2010-05-01
Hi,

You might want to check to see if the fujitsu X driver fpit_drv.so has been patched/updated to work with the 1.7 Xserver in Lucid.

---

### Post by redxine on 2010-05-01
Here's the ticket for the bug. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540)

I'm going to try both compiling source and using an older package, although I remember having problems with the old one. (1.2)

EDIT: Old package fails under same situation.

---

### Post by sm8ps on 2010-05-02
Just added the following to Launchpad. Favux seems to have a clue, right? (Re-posting here in hope to reach a wider audience.)
I met the same problem on a HP/Compaq TC1000. So I tried to install the fpit driver regardless of its dependencies. (Before installation through synaptics, it tries to remove ubuntu-desktop, xorg, xserver-core and many more which would not make much sense to me.) I manually copied the appropriate files (/usr/lib/xorg/modules/input/fpit_drv.so and /usr/share/bug/xserver-xorg-input-fpit/script which is a symlink). After that, the X server starts normally but the driver still does not work. Here is the relevant part of Xorg.0.log:
(II) LoadModule: "fpit"
(II) Loading /usr/lib/xorg/modules/input/fpit_drv.so
(II) Module fpit: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.3.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(EE) module ABI major version (4) doesn't match the server's version (7)
(II) UnloadModule: "fpit"
So the driver module seems to be incompatible with the X server's version. Any work-arounds?
Cheers!
Stefan Mueller, Switzerland

---

### Post by pmsoft1 on 2010-05-06
By adding this [repo]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates"), my tablet now works like a charm.

---

### Post by redxine on 2010-05-06
Thank you for sharing the repo; it's a step in the right direction and my tablet is working with the exception of calibration. All of a sudden the X-axis calibration numbers seem to make no difference at all. Y works fine, and changing the numbers shows a difference in calibration, but not at all for the x axis. For example this is my original code block:

```
Section "InputDevice"
	Identifier "Tablet"
	Driver "fpit"
	Option "Device" "/dev/ttyS0"
	Option "InvertY"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
	Option "SendCoreEvents" "true"
	Option "Passive" "false"
	Option "TrackRandR" "on"
EndSection

```

However changing Option "MaximumXPosition" "12550" to Option "MaximumXPosition" "0" shows absolutely no difference in calibration. The pointer goes all the way right when my pen is a little more than half way across the screen. Up and down is fine. Is this a typo in my xorg.conf, or a bug in fpit?

Filed a bug here: [https://bugs.edge.launchpad.net/launchpad/+bug/576677](https://bugs.edge.launchpad.net/launchpad/+bug/576677)

---

### Post by MadCarrot on 2010-05-21
here is a tiny manual for installing fpit on Ubuntu 10.4 for the Compaq  TC1000:

1. register new repository
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

```

2. install fpit
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-input-fpit

```

3. edit /etc/X11/xorg.conf (you might want to backup first) ... add or  change the following sections:
```

Section "InputDevice"
Identifier "pen"
Driver "fpit"
Option "AlwaysCore" "on"
Option "Device" "/dev/ttyS0"
Option "BaudRate" "19200"
Option "MaximumXPosition" "8600" # "6250"
Option "MaximumYPosition" "6485" # "4950"
Option "MinimumXPosition" "154"
Option "MinimumYPosition" "110"
Option "InvertY"
Option "TrackRandR"
Option "SendCoreEvents"
Option "Button2" "3"
Option "Reporting
EndSection
...
Section "ServerLayout"
Identifier "Default Layout" 
Screen "Default Screen"
InputDevice "pen"
EndSection
...

```

4. restart
```

sudo init 6

```


Worked for me. Finally got my pen support back after upgrading my TC1000  from Ubuntu 9.10 to 10.4.
Have a nice weekend!

---

