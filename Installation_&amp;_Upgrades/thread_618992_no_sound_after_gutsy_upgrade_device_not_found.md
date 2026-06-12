---
title: "no sound after gutsy upgrade device not found"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by flyingmayo on 2007-11-21
I found tens of posts suggesting massive ALSA hackery to solve the post-gutsy-grade sound blues.
The problem in my case was that the general sound as well as chipset specific modules weren't loaded at all.  I had no reason to believe there was anything wrong with ALSA per se.

In my case I am running this device as described by lspci:

00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

I installed this package and rebooted.
sudo apt-get install linux-ubuntu-modules-2.6.22-14-generic
Everything worked thereafter.
I suspect this is not a specific nvidia issue.

It is worth noting that there were no outstanding upgrades pending prior to my manually installing this package.  apt-get dist-upgrade showed that I was all up to date.

---

### Post by Ashrael on 2007-11-21
does it work when running from the livecd? If yes, there should be only a couple of things you should do: find out which module is loaded for sound when running from livecd. To do this type: lsmod in a terminal window. 

reboot from harddrive.

You could try at first to load the module 'by hand' by typing:  sudo modprobe <modulename>  in a terminal window. If it works add this driver to your /etc/modules file.

reboot.

tell me if it worked for you...

---

### Post by Ashrael on 2007-11-28
i removed pulseaudio package, now it works!

HTH

---

