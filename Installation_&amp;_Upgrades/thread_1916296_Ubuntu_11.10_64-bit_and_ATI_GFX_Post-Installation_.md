---
title: "Ubuntu 11.10 64-bit and ATI GFX Post-Installation Problem"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by LinuxReaper on 2012-01-27
Sorry, I am sure a topic on a similar issue like mine has been posted and/or sticked to the above forum section.

Today, I installed Ubuntu 11.10 64-bit distribution for AMD chipsets. The installation went without a hitch even managed to pick up the built-in webcam during installation. After I was given the standard "You must restart the computer" message. I restarted and proceed to login on the standard Ubuntu desktop environment (Unity?) Nothing, loads but the default desktop wallpaper. No icons, top menu bar, nothing. So I restarted and logged in under the Ubuntu 2D desktop environment. It loaded up properly and all. I want to configure/fix Ubuntu to work in its default desktop environment. 

Here are some of my laptop's details

Dell Inspiron

Graphics: ATI Mobility Radeon HD4250

Processor: AMD Athlon II P340

Display Monitor: 15.6" High Definition (720p) 1366 x 768 WLED Display with TrueLife

I know that has been posted before but, yes I did search the forums and google. Nothing I found seemed to be quite specific towards my graphic card's configuration which I am sure is what needs to be sorted out. And, yes I did apply all updates and bug fixes.

---

### Post by jboniello on 2012-01-27
I am of no help, simply because I have been having the EXACT same problem.  I posted a few days ago and have received no help, hopefully we will get an answer from someone.  I have a desktop and this has been frustrating me to the point of giving up on ubuntu, and with that said, linux all together.  You said the 2D worked though?  I'm new to unity, so I'm not sure what the difference really is, why not just use 2D?

---

### Post by LinuxReaper on 2012-01-27
I haven't explored the 2D desktop environment in detail to say I noticed a difference, but doesn't seems like there really isn't one besides a few nice desktop features such as the rotating cube. Which I could care less about, but I am nitpicker and like my installations to run like how they should. Especially since this I finally have a graphics card that should support it. I am guessing it's mainly a issue with the drivers.

---

### Post by jboniello on 2012-01-27
After reading your post I decided to try a fresh install and try the 2D desktop environment, for some reason I hadn't thought of that previously.  I was pleasantly surprised that it worked, so we are facing the same issue.  I believe it is a driver issue, but do not know how to install it considering the fglrx driver is installed for my ATI card.  Opengl driver does no better.  Sorry I am only comiserating, not solving your problem.  Hopefully someone else can help us.

---

### Post by LinuxReaper on 2012-01-31
Oh, no it's cool. At least I helped you a little bit sort of, lol.

---

### Post by LinuxReaper on 2012-01-31
I am starting to notice the differences right away. Now I have had time to play around with it a bit since the installation. So far the immediate difference is how much slower my wireless, usb receiver mouse is. Very slow compared to how smooth it runs on my other laptop with a 32-bit version of ubuntu which I am able to log into the default Ubuntu desktop enviroment. I hope someone could take a peak at this thread and help us find a working solution. Until then Ill post any progress I might make.

---

### Post by LinuxReaper on 2012-01-31
Okay, made a little headway, sort of. Finally, got a notification  by the system that I needed to install some proprietary drivers, of course it was the ATI/AMD FGLRX graphics drivers. I present with two on them On the bottom of the list was I am assuming was the first one I needed to activate it said. The second was the same driver except, the post-release updates. So I activated the first driver, restarted. Proceeded on to apply the post-release updates at some point during the installation it quits with a error. In the error log the last few lines I skimmed over seemed to be complaining about a Xorg driver not being set. If this is the problem of a Xorg driver not being set. What is the resolution to this? 

Here is the part of the log file - /var/log/jockey.log

```

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-15-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-02-01 02:13:36,131 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:05.0
2012-02-01 02:14:06,662 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:06,663 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:06,829 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:06,829 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:07,043 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,043 DEBUG: fglrx_updates is not the alternative in use
2012-02-01 02:14:07,112 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,113 DEBUG: fglrx_updates is not the alternative in use
2012-02-01 02:14:07,211 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,211 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:07,356 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,356 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:07,578 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,578 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:07,742 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,743 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:07,995 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:07,995 DEBUG: fglrx_updates is not the alternative in use
2012-02-01 02:14:08,064 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:08,065 DEBUG: fglrx_updates is not the alternative in use
2012-02-01 02:14:08,173 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:08,174 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-02-01 02:14:08,337 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-02-01 02:14:08,338 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking


```

---

