---
title: "triple boot"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by imnoob on 2008-11-23
This is what I want to do on an x86-64 bit currently running Vista (64 bit):

(leave Vista untouched)
Install 32-bit Red Hat Enterprise 5
Install 64-bit Ubuntu

Is it possible to share software between the two linux distros? i.e. If I wanted to install openoffice, would I have to install it twice (once for each distro) or could I share one installation between the two?

Also, is there a specific order I should install it in? I was thinking that I should install RHEL last since I want to use the Red Hat bootloader, but I'm not sure if there would be any problems installing a 32 bit OS after 64 bit.

---

### Post by inobe on 2008-11-24
dual boot/ triple boot/ quad boot, windows first regardless, after that it simply doesn't matter what linux distro is installed.

ubuntu will already have office by default, red hat as well !

having them all run at one instance is possible with virtualization or multiseat, without that' you will need to boot to run one os at a single time, you can only drag files between partitions from a single running operating system.

---

### Post by Mark Phelps on 2008-11-24
Just a word of friendly advice ... if you have to "shrink" the Vista partition to make room for the Linux installs, try to do that first from within Vista.  If you use a Linux utility to do that (e.g., GParted), it's likely that the Vista partition will get corrupted and you will need to be able to boot from a Vista DVD or a Vista Recovery CD, and run Startup Repair, to fix Vista.

---

