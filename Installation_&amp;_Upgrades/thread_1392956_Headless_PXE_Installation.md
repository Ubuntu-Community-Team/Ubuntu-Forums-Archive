---
title: "Headless PXE Installation?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Xial on 2010-01-28
Ahoy.

I've got a WYSE Winterm WT9455XL that I would love to install something on and tuck away under a desk here.

I just don't have a spare monitor for use in installation.

It's an older Winterm, so there's no optical drive onboard, and I can't get it to boot from a USB flash drive (when I ripped my monitor off the computer I use and tried, it just doesn't see them. Getting that monitor out of there is very difficult...), and it appears to be USB 1.x, so it tries to read from an external HDD, and gets lost in the process.

So I guess I'd have to turn to a PXE boot. The problems that come with it is, most of the instructions I'm finding are for people who already have a linux installation in place, and none of them seem to address installing via PXE to a headless machine, and having it enable ssh as part of its install.

The machine is probably not going to have a GUI -- it's just going to sit under the desk, connected to the router and running an IRC client, as well as (probably) a bittorrent client.

This is where I ask for help and suggestion.

Thanks in advance.


-----

Update:
I pulled a spare monitor off a piece of equipment that was rarely used and found a spare VGA cable.
While finding hardware, I found a USB CD-ROM drive in a closet. 

Trying to run the alternative install CD of ubuntu wasn't turning out too well, though -- spent six hours of retrying installation after installation and kept getting what I didn't want, which were errors (mini.iso wasn't even booting...) or GNOME, despite trying to deselect everything but the bare essentials during the installation procedure.

Per a suggestion given by someone in #Ubuntu, tried a boot disc from boot.kernel.org, which allowed me to make a minimal, CLI-based install that I was looking for, with fresh packages downloaded over the internet or grabbed from the regular Ubuntu CD that I had swapped in after booting.
It even gave me the ability to SSH in to complete the install, which was something I really desired to do.
That let me cut the monitor off after I got the installer started, and save some power (Yes, I know an LCD monitor generally doesn't use that much, but saving is saving).

Result: I now have a box that is fast enough to do what I want it to do, and uses very little electricity compared to my desktop. Now I can actually sleep my regular desktop during the day, and save plenty of juice. :)

---

### Post by AxMstrLP on 2011-08-03
It's a year late but I updated one of the community wiki's that would have helped with this:

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

If you'd like, give it a whirl and I can update the wiki to clarify things as necessary.

---

