---
title: "GeForce4 MX 440 AGP 8x - not working"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Elfy on 2008-07-26
When I try and boot intrepid I get a warning during boot

can't create /lib/modules/2.6.24.4-generic/volatile

I believe it says something to do with not having root rights to do so, I have had the same problem from alpha1 - but haven't had much time to look further.

Up until alpha2 I had upgraded from hardy - this week though I got the alpha3 iso and did a clean install but the same error appears.

In addition I have not been able to get my nvidia card to work at all - I know there have been problems and have read what appear to be relevant threads to no avail.

I do now however get the card showing in hardware drivers - which allows me to download and apparently install after enabling it.

I can see from the Hardy filesystem that /lib/modules/kernel/volatile appears to have nvidia in there - could the 2 be linked?

---

### Post by eeclark on 2008-07-26
I have the same msg.
I am using ATI (open source drivers).

---

### Post by Elfy on 2008-07-27
Half dealt with then - bit embarassing - make the directory and error goes.

Doesn't seem to have had anything to do with the nvidia though.

Yup - can't get the nvidia go  to work at all - uninstalled everything and now it doesn't show in jockey again.

---

### Post by ronacc on 2008-07-27
what Nvidia card do you have ? here is how I got my 7600gs to work with A3 , made sure nvidia-177-glx was installed , uninstalled the other 2 (173 & 96) that were showing as "in use" (but not "enabled") in jockey along with their modailiases and nvidia-kernel-common , copied my hardy xorg.config to intrepids /etc/X11/xorg.conf replacing the one that was there . installed fusion-icon .  Note ny display was the correct resolution from the start so I suspect that the nvidia driver was there from the start, I was not getting the "low graphics" warning but desktop effects could not be enabled from system>preferences>appearence , I had to use fusion-icon to enable desktop effects , compiz was showing as selected in fusion-icon>select window manager  clicking on it again activated compiz , it has to be "activated" again each boot .

---

### Post by Elfy on 2008-07-27
I have an old one  :D - Geforce4 - uses the -96 driver I believe, at least that's what hardy tells me.

To clarify what I've done and tried, 

At this point jockey was reporitng 2 drivers -96 and -71, both in use buit neither enabled. Removed and purged all previous drivers - it reboots with 1152x768 resolution which is at least usable after an xfix in recovery - even if it is bent.

I tried envy once until I relaised it wasn't going to work - so uninstalled that just in case.

Installed the correct driver and modaliases with synaptic - it reboots with the low graphics warning and won't accept the previously installed nvidia driver.

As it stands if I try to enable the nvidia after reboot I get the low graphics warning and round and round I go.

I think later today I will reinstall alpha3 and thne make sure that the /lib/modules/2.6.24.4-generic/volatile folder is ther before I do a first boot in recovery mode and try form scratch with the -96 driver again.

I know it's an old card but it's worked ok since feisty and I can't be buying new one just yet - want a flat screen first :lol:

---

### Post by ronacc on 2008-07-27
which ever driver number was working for you before should work in intrepid ( just use the intrepid package ) I just used nvidia-glx-177 as an example because that works for my card . I notice you don't say that you replaced your xorg.config with one known to work from a previous install . The one the installer inserts don't seem to get everything right . envy dosen't provide drivers for developement installs things change too fast .

---

### Post by Elfy on 2008-07-27
Yea sorry meant to say about the xorg - I've tried using the one from hardy after I'd installed the drivers in intrepid.

After I'd tried envy I read it wasn't working yet, and yes I understood you were using an example.

Thanks for looking - once I've done the install I'll post back with a solved or not.

Have a good day

---

### Post by ronacc on 2008-07-27
good luck , during the developement cycle video drivers are always a problem and not just for Nvidia , what works for one person/system may not work for the next , by all means post back, your experiences may help someone else .

---

### Post by Elfy on 2008-07-27
Ok - well first the lib/modules error still needed the folder to be made. Without it it errored on boot. I'll make it a bug I guess - it's happenend to me constantly since alpha1.

Nvidia - jockey recognised the card with a clean install - enabling the -96 driver caused it to download and install, called for a restart - on restart I got the low graphics.

Shall carry on - thanks for the help ronacc.

---

### Post by ronacc on 2008-07-27
check your xorg.conf again low graphics has a nasty habit of trashing it .  jockey may have also, the new xorg is "supposed" to use a much reduced xorg.conf , unfortunately it dosen't always work that way .

---

### Post by Elfy on 2008-07-27
Yea it's definitely much reduced

> the new xorg is "supposed"I heard it was supposed to be bulletproof - I'd try that :D

Still I'll get there I'm sure - I'll try and pare down my hardy one for it, I'll get there eventually - although ubuntu might get there before me, only mucked about with it once before.

I put a bug report for the /volatile thing - but didn't know which package I should have put it against so it's just a public bug.

---

### Post by ronacc on 2008-07-27
do not pare down your hardy one , if it was working the way you wanted it in hardy use it as is .the reduced xorg.conf is the one that often don't work right , in the future it may be great  but  so far it is not nearly "bulletproof".

---

### Post by Elfy on 2008-07-27
Ok tried with the good hardy xorg - 

hardware drivers reports that driver is enabled and in use

nvidia-settings tells me I'm not using the nvidia driver use nvidia-xconfig, that appers to add the same info to xorg as is present in the intrepid xorg

result is the graphics warning and 800x600 resolution.

---

### Post by ronacc on 2008-07-27
hmm I'm fresh out of sugestions , you are doing the right things they just aren't working for some reason ,  does your /var/log/xorg.log give any clue ? or /home/.xsessionerrors ?

---

### Post by Elfy on 2008-07-27
Theres a failed to load for nvidia in xorg log - but I can't see anything in the xsession.errors, but then I've never actually looked at that so it's a bit new. I've copied my xorg - just in case you can see something, but I do know that nvidia is a bit hit and miss at the moment as you said. Shortly after the xorg.log nvidia error - vesa loads - which I knew :D

The only thing that strikes me at the moment from xsession.errors is
> Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

Following from xorg.log

```
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(II) LoadModule: "freetype"
```


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Jan 22 19:53:46 PST 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 768
    Screen      1  "Screen1" Above "Screen0"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 85.0
    VertRefresh     47.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0; CRT: 1280x1024_75 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

Anyway if you can see anything odd perhaps you could let me know, I shant bother with anothere install though - obviously something is awry here - I can't think of anything else I could be doing in order to get it to work - that said this is the first time I've pitched up at alpha stage - with gutsy and hardy I started when it was beta - but I didn't get any problems with either of those.

Thanks for your help ronacc, if I do manage to stumble on something I shall make sure to document it here.

I think I'll also get the title changed as it's more an nvidia thread now :)

---

### Post by Gina on 2008-07-27
I've just installed Alpha 3 on my AMD 64 from the Alternate CD and was pleased to see the 177, 173 and 96 nvidia drivers listed in the Hardware Drivers dialog.  I ticked the 177 version and let it install and after what seemed rather a long time all three drivers appeared loaded with 177 enabled.  After rebooting my screen gave the correct resolution and all was fine :)  This is a great improvement on Alpha 2 :)

---

### Post by Elfy on 2008-07-27
Well I did get an improvement on alpha2 - it gets recognised by jockey now - hopefully alpha4 will finish the job and install it completely unless I get there before :lol:

---

### Post by joffe on 2008-07-27
I've just skimmed through the thread and from the xorg.log it seems like you are running either 96.43.05 or 96.43.07 driver together with the new X server 1.4.99.905.

Nvidia fixed the 2.6.26 kernel incompatibility in their latest 96 driver but unfortunately it does not support this latest X server. If you really want to try intrepid you should go for the nv driver in the mean time as I have been forced to do.

---

### Post by Elfy on 2008-07-27
> **joffe said:**
> I've just skimmed through the thread and from the xorg.log it seems like you are running either 96.43.05 or 96.43.07 driver together with the new X server 1.4.99.905.

Nvidia fixed the 2.6.26 kernel incompatibility in their latest 96 driver but unfortunately it does not support this latest X server. If you really want to try intrepid you should go for the nv driver in the mean time as I have been forced to do.

Aaah - ok I'll give that a go later - it was more about seeing if it was just me or others had similar. There is a lot in the forum about newer cards but I never seemed to get anywhere.

Shall look at that in the morning - thanks for the heads up.

---

### Post by ronacc on 2008-07-27
joffe is correct the 96 driver is not working with xorg 1.5  , I found this [http://albertomilone.com/wordpress/?p=212](http://albertomilone.com/wordpress/?p=212)  referenced in another thread , Alberto is the maintainer of envy .

---

### Post by Elfy on 2008-07-28
/thanks all - I'll play the waiting game then - I did read that but obviously missed the xorg server bit :)

---

