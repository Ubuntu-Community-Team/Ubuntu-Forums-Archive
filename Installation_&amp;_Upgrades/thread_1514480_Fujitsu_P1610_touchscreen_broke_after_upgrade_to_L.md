---
title: "Fujitsu P1610 touchscreen broke after upgrade to Lucid"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by nsfx on 2010-06-21
Ever since I upgraded, the touchscreen on my Fujitsu Lifebook P1610 no longer works. On Karmic, it worked out of the box without installing any extra packages.

I see xserver-xorg-input-fpit in Synaptic Package Manager but it conflicts with netbook remix packages for some reason so I haven't tried installing it.

I didn't see anything in dmesg about the touchscreen but there are Xorg errors:

```

...
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.10.5
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet eraser"
(II) UnloadModule: "wacom"
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet"
(II) UnloadModule: "wacom"
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet"
(II) Serial Wacom Tablet: removing automatically added devices.
(II) UnloadModule: "wacom"
...

```

I'm not sure if it's supposed to be recognized as a wacom tablet or what, and I'm also not sure how it used to be configured when it worked in Karmic. Any tips to get this working? Thanks.

---

### Post by Favux on 2010-06-21
Hi nsfx,

That is bizarre.  I'm reasonably sure it has a passive touchscreen, not an active Wacom digitizer.  So it probably works with the evtouch driver.  Check in Synaptics Package Manager if it is installed and if not install it.

I don't think I've seen the wacom driver pick up another device before.  It might be due to some changes they made in xf86-input-wacom to let it support Waltop and N-trig tablets.

---

### Post by nsfx on 2010-06-21
@Favux: I will try that out tonight and post the results here. Thanks!

---

### Post by nsfx on 2010-06-22
After installing evtouch I now don't see anything in dmesg or Xorg.0.log regarding the touchscreen, nor does the touchscreen work, lol. 

It seems to me like the xserver-xorg-input-fpit package is really what I need, as it "...provides the driver for Fujitsu Stylistic tablet PCs..." but for some reason it conflicts with netbook remix. Any other ideas?

Thank you!

---

### Post by Favux on 2010-06-22
I still think that's the right driver.  Fpit is for the digitizer, not the touch screen I think.  Check for a xx-evtouch.conf that the package should have added in /usr/lib/X11/xorg.conf.d/.  Maybe you need to amend the MatchProduct line?

I think evtouch took over for an older Fuji touch driver:  [http://spareinfo.blogspot.com/2009/05/linux-on-fujitsu-u810-p1620-touchscreen_19.html](http://spareinfo.blogspot.com/2009/05/linux-on-fujitsu-u810-p1620-touchscreen_19.html) & [http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html](http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html)

---

### Post by KsLIVER on 2010-09-12
Hi All...
 
I too have a Fujitsu P1610, and the touchscreen doesn't work.  This is a new / clean install of Ubuntu 10.04.
 
I've tried many drivers / scripts to get this to work (via google and here), but still no luck.  Almost seems like there has been a few subtle changes with the newer version of Ubuntu.
 
Is there anyone who has a step by step 'how to' available with this newer version of Ubuntu with this particular tablet notebook?
 
Any advice on resolving this issue (xorg.0.log is the same for me as above).
 
I'm still a bit of a newbie too... :)  
 
Thanks... :)

---

### Post by kathleenhenri on 2010-09-23
Check out this thread - posts 37 and 44 should get your touchscreen up and running. Although the thread is for the p1510 series the p1610 has similar hardware. I've used the instructions with Lucid and it works fine.

[http://ubuntuforums.org/showthread.php?t=811200&page=4](http://ubuntuforums.org/showthread.php?t=811200&page=4)

---

