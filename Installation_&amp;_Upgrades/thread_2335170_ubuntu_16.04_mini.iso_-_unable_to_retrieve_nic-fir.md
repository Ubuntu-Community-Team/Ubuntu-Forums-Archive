---
title: "ubuntu 16.04 mini.iso - unable to retrieve nic-firmware"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by user49b on 2016-08-26
Hi

Trying to install Ubuntu 16.04 via mini.iso.
At - Download Installer Components - 
Downloading of nic-firmware fails.
Tried 8 different mirrors, but issue persists.

Regards
Kris

---

### Post by sudodus on 2016-08-26
Welcome to the Ubuntu Forums :-)

Maybe you are using an old version, that is no longer working. Did you try the most current version available via this link: [***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")?

---

### Post by jishac on 2017-06-30
Ran into this issue with a virtual machine today.  If anyone is still having issue with this it's likely the amount of memory and the installer running out of room on a ramdisk.  I increased the VM memory from 256M to 1G and it took care of this problem.

---

### Post by johndough2 on 2017-07-03
Hi

The nic-firmware may not be available from a repo maintained by Ubuntu.

My suggestion is to ID your network interface card and search for drivers, firmware etc online.

If found they could be added via another USB stick or something.

Please post the spec of the network kit that you have, and perhaps you may get a pointer from here.

---

### Post by riksoft on 2017-07-24
Same here.
Maybe a fix to the message or having a proper repo would be nice.

I'm on Ubuntu 14.04 upgraded from 12 and instead of upgrading again to 16.04 I've tried to reinstall from scratch using the mini iso, but it stops immediately because of
"unable to retrieve nic-firmware, try another mirror".

No matter what mirror I select.
I'm pretty confident it will install with the standard DVD... if it only had a DVD reader instead of a CD :) and on the repo, the smallest after the mini is the 800MB iso (that does not fit into a cd).

I'm gonna try a portable USB DVD or I'll go with Debian.

---

### Post by riksoft on 2017-07-24
PS: clicking cancel, it ends up in an infinite loop with the screen changing from black to white forever. I had to reset.

---

### Post by Bashing-om on 2017-07-24
Guys : Hey'

We talking a WIFI connection here ? 
Out of the Box .. no . The mini does support a wired connection .

[INDENT][INDENT]what is that interface
[/INDENT][/INDENT]

---

### Post by kaefert66014235 on 2017-12-12
I just ran into the same problem. I'ts not a network problem, the 16.04 minim.iso simply will hang after downloading 29% of the required install packages on downloading the package "nic-firmware" and offer to select a different mirror.

---

