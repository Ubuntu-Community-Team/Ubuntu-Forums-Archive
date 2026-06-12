---
title: "OpenGL fails on 11.10 upgrade"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by eric_marsh on 2012-03-10
I've got a Dell D630 that I've been running with Ubuntu 11.04 and I recently decided to do a web upgrade to 11.10. After the upgrade Blender wouldn't start. I did some investigating and discovered that OpenGL wouldn't start.

First I tried sudo nvidia-xconfig to no avail.

I did an installation of the current Nvidia driver from the command line thus:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates sudo apt-get update sudo apt-get install nvidia-current

Having done this I rebooted and discovered that the GUI wouldn't start - it just hung at the first screen. I logged in and tried starting it but only got some errors logged such as this one:

[ 36.090] (II) NVIDIA(GPU-0): Display (LPL (DFP-0)) does not support NVIDIA 3D Vision

Doing some more research I discovered that in 11.10 the NVidia driver was replaced by Nouveau which is evidently incomplete (no 3d).

I discovered that I if I booted 2.6.38-13 the system would start up properly with OpenGL. With that I did some more digging and decided that perhaps I should disable Noveau. I found these instructions on-line:

You have to disable nouveau driver (which I think is the default driver of Ubuntu). First, you have to edit the modprobe blacklist file (terminal: gksu gedit /etc/modprobe.d/blacklist.conf) and add these entries at the bottom:

blacklist vga16fb 
blacklist nouveau 
blacklist rivafb 
blacklist nvidiafb 
blacklist rivatv

Then reboot and they shouldn’t be loaded. Next, open the Terminal and type ”sudo update-initramfs -u” to create a new image and reboot before nouveau is actually removed.

So far no luck. I'm running 11.10 with the 2.6.38-13 kernel.

What should I try next? If I'd realized it would be this much trouble I would have never done the upgrade.

---

### Post by LinuxFan999 on 2012-03-10
> **eric_marsh said:**
> I've got a Dell D630 that I've been running with Ubuntu 11.04 and I recently decided to do a web upgrade to 11.10. After the upgrade Blender wouldn't start. I did some investigating and discovered that OpenGL wouldn't start.

First I tried sudo nvidia-xconfig to no avail.

I did an installation of the current Nvidia driver from the command line thus:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates sudo apt-get update sudo apt-get install nvidia-current

Having done this I rebooted and discovered that the GUI wouldn't start - it just hung at the first screen. I logged in and tried starting it but only got some errors logged such as this one:

[ 36.090] (II) NVIDIA(GPU-0): Display (LPL (DFP-0)) does not support NVIDIA 3D Vision

Doing some more research I discovered that in 11.10 the NVidia driver was replaced by Nouveau which is evidently incomplete (no 3d).

I discovered that I if I booted 2.6.38-13 the system would start up properly with OpenGL. With that I did some more digging and decided that perhaps I should disable Noveau. I found these instructions on-line:

You have to disable nouveau driver (which I think is the default driver of Ubuntu). First, you have to edit the modprobe blacklist file (terminal: gksu gedit /etc/modprobe.d/blacklist.conf) and add these entries at the bottom:

blacklist vga16fb 
blacklist nouveau 
blacklist rivafb 
blacklist nvidiafb 
blacklist rivatv

Then reboot and they shouldn’t be loaded. Next, open the Terminal and type ”sudo update-initramfs -u” to create a new image and reboot before nouveau is actually removed.

So far no luck. I'm running 11.10 with the 2.6.38-13 kernel.

What should I try next? If I'd realized it would be this much trouble I would have never done the upgrade.
Upgrading through the update manager can (and usually will) break you Ubuntu installation, so it is not recommended. I recommend doing a clean installation of Ubuntu 11.10.

---

### Post by grahammechanical on 2012-03-10
Did the upgrade really do this or is it what you have done since finding that Blender would not run?

After the upgrade did you run Additional Drivers to get the latest Nvidia driver for the upgraded kernels that were installed? Could this be the reason that Blender would not start?

The Nvidia driver that you installed through a PPA broke the desktop. You should have removed that driver. Instead you blacklisted Nouveau which was the only video driver that was giving you a desktop when you booted the 2.6.38-18 kernel.

And now you have a kernel with a video driver that breaks the desktop and another kernel with no video driver. I cannot tell you how to put this right step by step but you need to, in my opinion,

1) boot Ubuntu into rescue mode. That will boot Linux without a desktop. You will be at a command prompt where you can log in.

2) Remove the blacklisting of Nouveau. Undo what you have done. Somehow. May be re-install Nouveau.

3) When you get back to booting a kernel with a desktop deactivate that PPA Nvidia driver and run Additional Drivers to activate a Nvidia driver through the standard Ubuntu video driver install method.

Alternatively, you could load a live CD, rescue your data and re-install. It might be easier.

Regards and good luck.

---

### Post by eric_marsh on 2012-03-11
I was trying to do my own research on this problem. I'm sure that I can back the blacklist stuff out but that gets me back to the original problem. So when there are several different ways to do an upgrade how is someone supposed to know which ones work and which ones will break things?

For now I'm probably just going to stick with the earlier kernel. Somewhere down the road I may decide to take another shot at it or I may just wait for version 12 to come out.

---

