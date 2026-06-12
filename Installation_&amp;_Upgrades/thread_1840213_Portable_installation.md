---
title: "Portable installation"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by timbim on 2011-09-07
Hi all,

I've got a project on the go that is based on a portable installation of probably Xubuntu on a USB stick, with some very specific audio player software, playing through a USB sound card that goes with the memory stick.  This is for a radio station so we can use any available laptop when we're away from the studio rather than having to create a dedicated machine.

My key requirements are as follows:
[LIST]
[*]Boots cleanly from USB stick without silly installation interface of standard live CD
[*]Gives full USB stick capacity (16GB)
[*]Music can be added/removed with stick plugged into a source computer and mounted as removable drive
[/LIST]

I've looked at [Rudd-o's Portable Linux]("http://rudd-o.com/new-projects/portablelinux/documentation"), but that's confused me and looks old.  What's the best way of doing what I'm after, if indeed it's at all possible?

Many thanks,
Tim

---

### Post by beew on 2011-09-07
All your requirements can be satisfied by doing a full installation of Ubuntu in your usb stick (it works with any buntus, and I think any Linux as well,--I have tried Mint and Fedora besides the buntus)

[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It is for 10.04 but the modifications for 11.04 is quite obvious. The main point is that you install exactly as you would into an internal hard disk but make sure that you put the bootloader in the usb drive (to have the option you need to choose "manual" or "advanced" install)

The catch of a usb installation is that it can be quite slow especially for updates and it may freeze if you try to multi-task, a better alternative is to install in an external hard drive instead, it may not look as cool, it is still portable but a lot faster, you get the same performance as an install in the internal hard drive.

---

### Post by timbim on 2011-09-07
Thanks, I'll give that a go.

---

### Post by jan0ng on 2013-02-07
> **beew said:**
> 
a better alternative is to install in an external hard drive instead, it may not look as cool, it is still portable but a lot faster, you get the same performance as an install in the internal hard drive.

I did this option but the boot up is so slow... how can i speed it up? thank you

---

