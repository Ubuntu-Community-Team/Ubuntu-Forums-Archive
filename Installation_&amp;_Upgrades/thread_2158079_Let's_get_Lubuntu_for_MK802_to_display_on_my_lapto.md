---
title: "Let's get Lubuntu for MK802 to display on my laptop screen"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by MediaBanger on 2013-06-27
Alright, so I've installed [the 1080p 1GB RAM Lubuntu distro found here]("https://www.miniand.com/forums/forums/2/topics/1") to an 8GB SD card, and it runs pretty okay on my [Avatar Titan 13-inch Allwinner A10 Cortex A8 notebook]("http://avatarpctv.com/android/78-avatar-13-3-titan-avra-138a1").

Thing is, I have to plug into my TV to see what I'm doing because the MK802 Lubuntu distro doesn't have support for a laptop screen. That makes sense because the MK802 displays solely via HDMI output. 

Other than the screen output, my notebook's internal hardware is pretty much a dead ringer for the chipset inside a 1GB MK802 stick, and Lubuntu seems to be running very well.Of course, I'd like to be able to run Lubuntu on this machine anywhere, without the need to plug into a TV. That means I need to get it to display on the laptop's built-in screen. I'm guessing it wouldn't take a ton of work, but I don't really know where to start. 

When I first installed this distro, I thought I'd be able to CTRL-ALT-F1 into a non-GUI terminal, run "sudo service lightdm stop", reload the X server by running "X -configure", then switch the X session back on by running "sudo service lightdm start", but as it turns out, all the Lubuntu A10 distros don't support switching to a non-GUI terminal like that. I hit CTRL-ALT- and any F key, and it just freezes the screen, mouse, and keyboard. I can bring it back to life with CTRL-ALT-F7.

So bearing in mind that I'm still sort of new at this Lubuntu and setting up a new display stuff, a little help anyone?

---

### Post by dino99 on 2013-06-28
which graphic driver is used ?
running x-configure might disturb the kernel graphic process, so purge xorg.conf (sudo rm /etc/X11/xorg.conf*)

---

### Post by MediaBanger on 2013-06-28
> **dino99 said:**
> which graphic driver is used ?
running x-configure might disturb the kernel graphic process, so purge xorg.conf (sudo rm /etc/X11/xorg.conf*)

If I run the rm command, won't that remove my xorg setup? As in, I won't be able to use even the HDMI for an external monitor?

The SOC has a Mali 400 graphics chip, and as far as I can tell, the MK802 Lubuntu distro has a graphics driver for that chip. [See some build notes here]("https://www.miniand.com/forums/forums/development--3/topics/ubuntu-12-10-linux-sunxi-3-4-24-kernel-image-and-build-from-scratch").

---

