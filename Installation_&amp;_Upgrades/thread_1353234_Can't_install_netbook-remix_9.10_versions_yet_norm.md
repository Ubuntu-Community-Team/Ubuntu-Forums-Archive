---
title: "Can't install netbook-remix 9.10 versions yet normal ubuntu works"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Stormblazer on 2009-12-12
I have an HP mini 110 netbook.
I originally wanted to install a custom build (maybe gentoo through distcc) but the amount of time involved proved prohibitive. I used the 9.10 Live ISO (converted to LiveUSB via unetbootin) to resize the NTFS partition with no real issues. I also tried installing it, but it drained far more power than XP did (I stripped XP down, disabling all non-essential services and such, hoping to do something similar here with linux).

So instead, I'd like to try to the netbook-remix and maybe manually tune some things. This is where I started to run into trouble.
Initially I used the normal 9.10 netbook-remix ISO through unetbootin, and followed the setup instructions to get the normal boot menu. It completely failed to work - the menu was visible, but all options simply reset the menu and did nothing.

I tried using the built-in utility for creating a usb boot from the CD image on another system - still no luck, trying to boot from any option on the menu resulted in errors about an invalid kernel.

I then tried the kubuntu 9.10 netbook remix, and just did a straight USB creation through unetbootin. This time it actually did manage to load a kernel, but no sooner had it done that before it ran into yet another error, this time it said mount was given invalid arguments for mounting the filesystem on /dev/loop0, and I was dropped into an initramfs shell.

I'm at a complete loss here, why does the normal ubuntu ISO work flawlessly, yet the netbook-targeted one does not, using the same tools and the same 1GB USB flash stick?

---

### Post by raymondh on 2009-12-12
> **Stormblazer said:**
> 

I'm at a complete loss here, why does the normal ubuntu ISO work flawlessly, yet the netbook-targeted one does not, using the same tools and the same 1GB USB flash stick?

If you have 'regular' ubuntu already installed, go to synaptic and search for and install (as well as any dependency/ies)  ubuntu-netbook-remix.  It's in the repos.

Regards,

---

