---
title: "Nvidia install is a mess"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2013-07-02
HI
First I've checked in synaptic nvidia 130 or alike. Worked but I wanted to update, hence downloaded from Nvidia, run the installer and X has gone. Even failsafe mode failed! I had to restart the whole install!
Second time I only installed kernel sources and the Nvidia download works like a charm. I'm pretty sure also to update that later will be working perfectly.

What I want to say is that having ~10 Nvidia downloads in synaptic that don't even work and break the whole os is really sick.-

---

### Post by dino99 on 2013-07-02
works ok here; :P  you only need to know which chipset/card is used and which driver to install. But ubuntu is clever enough to know for you, simply check that the metapackage is installed :popcorn:

---

### Post by TheFu on 2013-07-02
Going directly to nVidia might not be the best idea.  I've been burned more than a few times using their drivers direct.  I learned to wait for Canonical to update their repo with newer versions.   notice, I don&#8217;t call them "upgrades" - since that is often NO TRUE.

For any lurkers, there is an "ubuntu nvidia driver" how-to guide that google will find.

**Newer isn't always better.**

---

### Post by MikeCyber on 2013-07-02
I disagree...:popcorn: I probably never, ever will try such a messy Ubuntu only etc. solution again.

---

### Post by grahammechanical on 2013-07-02
Why did you not use the Additional Drivers utility? Did you not notice that Nvidia drivers are proprietary software? I have had Nvidia drivers give me exactly the same result us you have  seen but I did not blame Ubuntu. I stopped using Nvidia for a while. In the last two days I have installed Ubuntu and each of the flavours of Ubuntu but I never tick to install third party software because that brings in the Nvidia driver and I am not confident of getting a working desktop with Nvidia any more. Saying that, I am at the moment running Saucy Salamander on Nvidia 319.32 that I installed through Additional Drivers and it is working fine.

You will find that every Linux distribution relies on either open source drivers or proprietary drivers. It is the hardware, you see. It is the same hardware for all distributions. Microsoft has the weight to pressurize video card makers to provide drivers that work on the hardware that Windows is going to be installed on. Linux developers have to rely on the good nature of the makers.

For example, Nvidia Optimus technology has been around for months but it was only recently the Nvidia started to work on a Linux driver. Even now it is only at Beta stage and is not fully functional with its own Optimus technology. So, what chance do open source developers stand?

Regards.

---

### Post by buzzingrobot on 2013-07-02
The safest, recommended way of installing Nvidia drivers is via Additional Drivers.  Only the relevant drivers are offered. Synaptic will show all the Nvidia drivers in the repositories.

---

### Post by MikeCyber on 2013-07-03
Again, as I've said using stuff from synaptic crashed my system to an unbootable state! :(

So all u need is kernel sources and download from Nvidia.

Or ok if you don't want the latest drivers stick to synaptic and never touch it again....

---

### Post by kurt18947 on 2013-07-03
> **buzzingrobot said:**
> The safest, recommended way of installing Nvidia drivers is via Additional Drivers.  Only the relevant drivers are offered. Synaptic will show all the Nvidia drivers in the repositories.

This is how I handle Nvidia as well.  I don't know that Synaptic offers any assurance about available drivers functioning in all or even most situations.

---

### Post by buzzingrobot on 2013-07-03
All the drivers are in the repositories.  Synaptics does not draw from some special pool of software.  It's a GUI-ified way of doing what apt-get does.

Additional Drivers has the advantage that it is structured to install, and install correctly, the right drivers on the right hardware.  It knows what video card you have and it knows which of the drivers in the repos are appropriate for that card.  Synaptic and apt, do not know, and they will happily do their best to install anything you select, even if it won't work. Blaming Synaptic for pilot error is pointless.

---

