---
title: "Clicking on touchpad work only sometimes"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-09-12
Hi folks. I have this strange issue with my touchpad after upgrading today. Moving the mouse around works ok, but clicking on the touchpad seems to work erratically. Sometimes it works after clicking 2 or 3 times, sometimes even 6 tries. Other times it works at first try. Pretty annoying.

I'm on a Dell Inspiron 9400, and it did work ok till I upgraded today. I did a dpkg-reconfigure -phigh xserver-xorg, but that didn't help. I'm using all latest packages. Any clues?

---

### Post by wgrant on 2008-09-12
The default for the movement sensitivity (ie. how much you can move your finger before it decides that you didn't really mean to tap) was changed recently. Do things improve if you run this?
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Move" 32 200
```

---

### Post by snifer on 2008-09-13
I'm also experiencing this (Dell Inspiron 9400, too).
Touchpad works fine with your command, indeed.

Default behavior is specially annoying when trying to middle click using two-finger tap.

---

### Post by danf_1979 on 2008-09-13
Fujitsu, thanks!

Anyway to automate this fix other than to put the command in the gnome session?

Snifer: chile tambien :)

---

### Post by meborc on 2008-09-13
> **fujitsu said:**
> The default for the movement sensitivity (ie. how much you can move your finger before it decides that you didn't really mean to tap) was changed recently. Do things improve if you run this?
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Move" 32 200
```

thanks for the info and quick workaround :)

---

### Post by wgrant on 2008-09-13
Are people still having issues with two-finger tapping to middle click? If so, please install [http://launchpadlibrarian.net/17574591/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_i386.deb](http://launchpadlibrarian.net/17574591/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_i386.deb) or [http://launchpadlibrarian.net/17574588/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_amd64.deb](http://launchpadlibrarian.net/17574588/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_amd64.deb), log out and in, run the xinput command, and report your results back here.

---

### Post by meborc on 2008-09-13
> **fujitsu said:**
> Are people still having issues with two-finger tapping to middle click? If so, please install [http://launchpadlibrarian.net/17574591/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_i386.deb](http://launchpadlibrarian.net/17574591/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_i386.deb) or [http://launchpadlibrarian.net/17574588/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_amd64.deb](http://launchpadlibrarian.net/17574588/xserver-xorg-input-synaptics_0.15.2-0ubuntu1%2Bwgrant1_amd64.deb), log out and in, run the xinput command, and report your results back here.

perfect, the two-finger-tap works now :)

---

### Post by phenest on 2008-09-13
> **fujitsu said:**
> The default for the movement sensitivity (ie. how much you can move your finger before it decides that you didn't really mean to tap) was changed recently. Do things improve if you run this?
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Move" 32 200
```

It seems like I have to keep doing this command after a reboot.

---

### Post by wgrant on 2008-09-13
> **phenest said:**
> It seems like I have to keep doing this command after a reboot.

After a restart of X, actually. That's correct. We can consider changing the default if this is indeed a problem.

---

### Post by phenest on 2008-09-13
> **fujitsu said:**
> After a restart of X, actually. That's correct. We can consider changing the default if this is indeed a problem.

So anything xinput changes is not permanent?

---

### Post by wgrant on 2008-09-13
> **phenest said:**
> So anything xinput changes is not permanent?

That is correct.

---

### Post by phenest on 2008-09-13
Did I read somewhere else, the Touchpad tab in Mouse Preferences uses xinput? If so, is that temporary too?

---

### Post by danf_1979 on 2008-09-13
> **phenest said:**
> Did I read somewhere else, the Touchpad tab in Mouse Preferences uses xinput? If so, is that temporary too?

I guess you can always add the command to the gnome session so it will be executed when gnome starts. Go to system->preferences->Sessions and add the command there.

---

### Post by snifer on 2008-09-13
> **fujitsu said:**
> After a restart of X, actually. That's correct. We can consider changing the default if this is indeed a problem.

Please consider changing the default value, since currently double tapping for double click and two-finger tapping for middle click is very difficult.

I don't need a special package to middle click using two-finger tap, just the command you provided. 

If you need a bug report to change this, please let us know, thanks.

---

### Post by wgrant on 2008-09-13
> **phenest said:**
> Did I read somewhere else, the Touchpad tab in Mouse Preferences uses xinput? If so, is that temporary too?

It is similarly temporary, but gnome-settings-daemon sets those when you log in.

---

### Post by iamhimay on 2008-09-13
hi all,

My touchpad clicking has been erratic since the last xserver-xorg-input-synaptics update. None of the suggestions here seem to have any effect. When I try to list options with xinput, I get an error:

koid@luyipa:~$ xinput list-props "SynPS/2 Synaptics TouchPad"Device 'SynPS/2 Synaptics TouchPad':
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  37 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

Right side scrolling works fine. It's just that all clicking by tapping seems to be randomly working. Especially click/hold/drag window and resize window with double click. Extremely frustrating. Is this a kernel problem as well as driver issue?

---

### Post by wgrant on 2008-09-13
> **iamhimay said:**
> hi all,

My touchpad clicking has been erratic since the last xserver-xorg-input-synaptics update. None of the suggestions here seem to have any effect. When I try to list options with xinput, I get an error:

koid@luyipa:~$ xinput list-props "SynPS/2 Synaptics TouchPad"Device 'SynPS/2 Synaptics TouchPad':
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  37 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

Right side scrolling works fine. It's just that all clicking by tapping seems to be randomly working. Especially click/hold/drag window and resize window with double click. Extremely frustrating. Is this a kernel problem as well as driver issue?

Ergh, not this error again... Please post the output of "xinput list" and "dpkg -l | grep xorg".

---

### Post by iamhimay on 2008-09-14
Here are the outputs:

```
koid@luyipa:~$ dpkg -l | grep xorg 
ii  python-xkit                               0.3.6                                 library for the manipulation of the xorg.conf
ii  xorg                                      1:7.4~2ubuntu1                        X.Org X Window System
ii  xserver-xorg                              1:7.4~2ubuntu1                        the X.Org X server
ii  xserver-xorg-core                         2:1.5.0-1ubuntu1                      Xorg X server - core server
ii  xserver-xorg-input-evdev                  1:2.0.99+git20080912-0ubuntu1         X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                    1:1.3.1-1ubuntu2                      X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse                  1:1.3.0-1build1                       X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics              0.15.2-0ubuntu1                       Synaptics TouchPad driver for X.Org/XFree86 server
ii  xserver-xorg-input-vmmouse                1:12.5.1-1ubuntu3                     X.Org X server -- VMMouse input driver to use with VMWa
ii  xserver-xorg-input-wacom                  1:0.8.1.3-0ubuntu2                    X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                    1:7.4~2ubuntu1                        the X.Org X server -- output driver metapackage
ii  xserver-xorg-video-apm                    1:1.2.0-1build2                       X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                    1:0.7.0-1build2                       X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                    1:6.9.0+git20080826.a3cc1d7a-2ubuntu2 X.Org X server -- ATI display driver wrapper
ii  xserver-xorg-video-chips                  1:1.2.0-1build2                       X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                 1:1.2.1-1build2                       X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                  1:0.4.0-1build2                       X.Org X server -- fbdev display driver
ii  xserver-xorg-video-i128                   1:1.3.0-1build2                       X.Org X server -- i128 display driver
ii  xserver-xorg-video-intel                  2:2.4.1-1ubuntu4                      X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                 6.8.0-1build2                         X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                    1:1.4.9.dfsg-1build1                  X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic               1:1.2.1-1build2                       X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nv                     1:2.1.10-1ubuntu2                     X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome             1:0.2.902+svn579-1build1              X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128                   6.8.0-1ubuntu2                        X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                 1:6.9.0+git20080826.a3cc1d7a-2ubuntu2 X.Org X server -- ATI Radeon display driver
ii  xserver-xorg-video-radeonhd               1.2.1-2build2                         X.Org X server -- AMD/ATI r5xx, r6xx display driver
ii  xserver-xorg-video-rendition              1:4.2.0.dfsg.1-2build2                X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                     1:0.6.0-1build2                       X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                1:1.10.1-1build2                      X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                 1:2.2.1-1build2                       X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion          1:1.6.0-1build2                       X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                    1:0.10.0-1build2                      X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                 1:0.9.0-1build2                       X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                   1:1.4.0-1build2                       X.Org X server -- tdfx display driver
ii  xserver-xorg-video-tga                    1:1.1.0-9ubuntu4                      X.Org X server -- TGA display driver
ii  xserver-xorg-video-trident                1:1.3.0-1build2                       X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                  1:1.2.0-1build2                       X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                    1:0.2.0-1ubuntu3                      X.Org X server -- Video 4 Linux display driver
ii  xserver-xorg-video-vesa                   1:2.0.0-1ubuntu3                      X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                 1:10.16.2-1build2                     X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                 1:1.2.0-1build2                       X.Org X server -- Voodoo display driver
```
```

koid@luyipa:~$ xinput list 
"Virtual core keyboard"	id=0	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Virtual core pointer"	id=1	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 0
"TPPS/2 IBM TrackPoint"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=3	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is -1
		Resolution is 1
"Video Bus"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ThinkPad Extra Buttons"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"/usr/sbin/thinkpad-keys"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=9	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

---

### Post by iamhimay on 2008-09-14
By the way, as a workaround, not really a fix, I went and got the previous driver package from its launchpad page:

[https://launchpad.net/ubuntu/intrepid/amd64/xserver-xorg-input-synaptics/0.15.0+git20080820-1ubuntu5](https://launchpad.net/ubuntu/intrepid/amd64/xserver-xorg-input-synaptics/0.15.0+git20080820-1ubuntu5)

Luckily, no dependency issues so far. Still looking around, trying to figure out which bug this is.

---

