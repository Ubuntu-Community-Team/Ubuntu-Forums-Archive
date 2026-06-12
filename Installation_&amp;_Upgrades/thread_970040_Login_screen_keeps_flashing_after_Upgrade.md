---
title: "Login screen keeps flashing after Upgrade"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by roxority on 2008-11-03
Hi,

since the upgrade, I cannot log into GDM, as many others. Yes, I have googled and found a LOT of similar problems, ranging from X Server problems to ATI "poo poo proprietary driver" problems to compiz problems... but none of them quite solving my own problem here.

I have installed the latest ATI (xorg-driver-fglrx) drivers and I followed the steps at [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22)
including running the aticonfig tool.

Before that, my login screen was seriously messed up with a psychedelic "animation" (even after trying xfix and apt-get-autoremoving-purging and dpk?-reconfigure for both X and gdm). That is gone now and GDM seems to start up using the proper resolution (otoh I also at some point restored the xorg.conf that was backed up just before the dist-upgrade and that WORKED under 8.04).

However, I STILL cannot get hold of the login screen. Im not so sure this is still a video driver issue since the resolution and color depth seems to be OK now and the psycho animation is gone (even though fglrxinfo still says "unable to open display (null)" -- but lets not go into that, unless that is a serious problem and you know a fix...)

So, since I disabled the auto-starting of GDM in /etc/init.d, after I boot up Im in the shell where I type sudo gdm. Screen goes black, X cursor appears, screen goes light-brown (Ubuntu default theme) and the white pointer cursor appears, and then EVERY 1-2 SECONDS a wait cursor appears very briefly, the login screen (Ubuntu logo plus username textbox) appears for a FRACTION of a second before the entire screen flashes WHITE for another fraction, then goes back to light-brown with the login screen gone again until this all of this is repeated another 1-2 seconds later. This goes on forever. Well, until I shut down the laptop.

Hardware specs: ATI Radeon HD 2600, Acer TravelMate 5720, 4GB RAM, Intel Centrino dual core, 64bit.

Any ideas? I wonder whether the flashing login screen isnt a known issue that I just didnt find because googling only finds all kinds of issues with (Adobe) Flash...

---

### Post by roxority on 2008-11-04
FWIW... problem persists... any pointers would be so gladly appreciated.

---

### Post by roxority on 2008-11-04
Tried further. I can startx just fine, both as root and as my non-root user. Without a login screen X brings up my desktop and deskbars. Fails to properly open any program or application at all from the menus or icons, though. No error message, just either no window at all (most shortcuts) or a window without a chrome / borders that keeps flickering all the time (some shortcuts such as Evolution or Firefox).

I will try to reconfigure GDM. Problem is, I had some MacOS-like window styles going before the upgrade and am wondering whether disabling them might solve the problem, but System/Preferences/Appearances is one of the shortcuts that just won't open.

I think X is working fine and gdm / gnome are the one to blow it. Here's the warnings and errors from my Xorg.0.log. I'm still pretty certain the gdm-login-screen-flashing-problem is unrelated and X is basically fine. But I'm not sure and one has got to start somewhere...

fglrx: Force AIGLX enabled

This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0

Video driver ABI version of the X server is 4.1

fglrx(0): board is an unknown third party board, chipset is supported

fglrx(0): Unknown vendor-specific block f

fglrx(0): Only one display is connected, so single mode is enabled

[btw why is this a WW warning, seems more like an II info to me...]

fglrx(0): Option "VendorName" is not used

fglrx(0): Option "ModelName" is not used

AIGLX: 3D driver claims to not support visual 0x23
... 0x72

[i.e. this WW warning is repeated for all hex numbers between 0x23 and 0x72]

SynPS/2 Synaptics TouchPad can't grab event device, errno=16

[Then the II info line:]
AIGLX: Suspending AIGLX clients for VT switch

[Then the ever repeating two lines:]
AUDIT: (Date) 15533 X: client 4 rejected from local host (uid=0 gid=0 pid=xxxxx )
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

So, are there any serious problems in there?

---

### Post by roxority on 2008-11-04
This problem kind of evolved and I've "moved" it with an updated problem description to here: [http://ubuntuforums.org/showthread.php?p=6103702]("http://ubuntuforums.org/showthread.php?p=6103702") ... it is however NOT solved yet.

---

### Post by erikvw on 2008-11-15
were you able to get past the flashing login screen? i just upgraded (update-manager) from 8.04->8.10 and on re-boot have the same problem. That is, flashing from username prompt and ubuntu logo TO orange screen...and it never stops.

---

### Post by erikvw on 2008-11-16
i was able to resolve this issue for my installation by simply removing cairo grahics library lib files from /usr/local/lib. In fact, i removed everything (cairo, glitz, ctemplate, pixman) but i think the culprit was cairo. 

After that, everything works fine....incredible!!

---

