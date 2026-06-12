---
title: "Gigabyte Ga-73um-s2h"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by snowdrift on 2007-12-03
I recently put together a new system at home that is based upon the GIGABYTE GA-73UM-S2H motherboard. This mobo has NVIDIA IGP and I am unable to get Ubuntu 7.10 even to load and install on this machine.

Basically, the install just freezes while going through some sort of start-up routine and I have to reboot the machine -- only to stick at the same exact place the next time I try to install.

Any ideas? OpenSUSE does install but the video drivers appear to be very low res.

Thank you.

---

### Post by xdot on 2008-01-05
I have the GA-73PVM-S2H and had the same problem, you should try a failsafe graphics install from the boot menu of the CD.  Worked for me.  But then the trouble will reallly start.  Still haven't got my audio working and the onboard graphics won't show a resolution higher than 800 x 600.  Good luck  :!:

---

### Post by eneBeanee on 2008-01-13
I have a GA-73VM-S2H with an Intel core duo and all 64bit installs have failed with a kernel panic during booting of the live CD.

I did manage to do a 32-bit server install from the special server CD, and everything "seems to" work ok during install, but now I'm getting Oops messages and sometime kernel panics about every 12 hours or so.

I also installed the nvidia video drivers and they seem to work fine, I could run a minimal GNOME installation without a problem with a 20'' monitor in native resolution. I uninstalled them again just to see if that had any effect on the Oops messages but so far no change.

I've also disabled on board stuff like usb, sound, parallel port, and serial port, basically all things I don't need as some of the kernel panics were apparently due to irq conflicts but that does not seem to help.

Anyone have any ideas?

---

### Post by eneBeanee on 2008-01-15
Ok, my server seems stable now, not sure what exactly did it, but here is what worked for me:

1) Disabled almost all on board functionality (serial, paralell, USB, firewire, audio) even disabled on board IDE (I have SATA disk though and that is enabled). Ethernet card is enabled and SATA, that's it.
2) boot kernel with acpi=off option.

The last two things I changed (and yes I did change them simultaneously) were disabling IDE and booting with acpi=off option, I suspect that the acpi=off option has more to do with it, but as the computer is in use I can't play with it much.

---

### Post by srajkumar on 2008-01-17
With acpi=off option able to boot ubuntu and installed .But not able to install graphics and audio driver.I have only built in graphics and audio card of Gigabyte Ga-73um-s2h.

---

### Post by eneBeanee on 2008-01-17
Have you tried the Envy script?  I haven't tried it myself but hear good things about it.  It should help you install video drivers.  If you search the forums for 'Envy' I'm sure you'll find some help on the video at least.  Also I have a couple of links laying around somewhere that helped me with the video, I'll post them if I can find them again.  One of them also talked about the sound, but I never got that to work (but I wasn't trying that hard either).

---

### Post by Partyboi2 on 2008-01-17
[Here]("http://albertomilone.com/nvidia_scripts1.html") is the link to envy. Just download the .deb package. Hope it works for you. :)

---

### Post by eneBeanee on 2008-01-17
and here is a link for a blog that I found useful if you are installing it by hand: [http://www.beulbek.nl/2007/12/26/re-building-the-linux-based-mediacenter-ubuntu-x86_64-mythtv/]("http://www.beulbek.nl/2007/12/26/re-building-the-linux-based-mediacenter-ubuntu-x86_64-mythtv/")

I'm still getting the occasional kernel Oops, but I haven't really got a clue how to figure out how to fix them or even figure out why they are happening. What I've read so far indicates that this could be a rather convoluted process. Anyone know of a "kernel debugging for dummies" site? [-o<

---

