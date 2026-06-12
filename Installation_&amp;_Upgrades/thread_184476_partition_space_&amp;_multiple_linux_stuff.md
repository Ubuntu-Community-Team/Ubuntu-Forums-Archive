---
title: "partition space &amp; multiple linux stuff"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by ubuntubrian on 2006-05-30
I have been updating/upgrading since Hoary and notice that my 15 Gb partition is getting filled. I've archived all my photos and music onto a usb drive after having a major meltdown due to a completely filled partition borking my system. Still, with all the updates I'm down to 3.2 Gb remaining  and I wonder if all the updates have left unneeded packages. I notice that I have, installed,  linux images, kernels and headers from 2.6.10 and the newest installed versions are 2.6.15. I have run "apt-get -clean" to keep as much space as I can get. Do I need all of these old versions of linux pacakages? They amount to almost 1 gig!
Thanks

---

### Post by aysiu on 2006-05-30
You don't need old Linux images (kernels)--go ahead and uninstall those.

---

### Post by ubuntubrian on 2006-05-30
I'm sending a list of installed and not installed linux stuff. As there are headers, images and modules I want to make sure I don't uninstall something that breaks my system. Also, I wonder why the headers version doesn't match the latest image version? Thanks for the info.

installed
linux-headers-2.6.10-5
linux-headers-2.6.10-5-powerpc
linux-headers-2.6.12.8
linux-headers-2.6.12.8-powerpc
linux-headers-2.6.12.9
linux-headers-2.6.12.9-powerpc
not installed
linux-headers-2.6.15-23
linux-headers-2.6.15.23-powerpc
installed
linux-image-2.6.12-8-powerpc
linux-image-2.6.12-9-powerpc
linux-image-2.6.15-20-powerpc
linux-image-2.6.15-21-powerpc
linux-image-2.6.15-22-powerpc
linux-image-2.6.15-23-powerpc
linux-image-powerpc
linux-kernel-headers  version 2.6.11-2-0ubuntu18
linux-powerpc         version 2.6.15.22
linux-restricted-modules-2.6.12-8-powerpc
linux-restricted-modules-2.6.12-9-powerpc
linux-restricted-modules-2.6.15-20-powerpc
linux-restricted-modules-2.6.15-21-powerpc
linux-restricted-modules-2.6.15-22-powerpc
linux-restricted-modules-2.6.15-23-powerpc
linux-restricted-modules-2.6.15-23-powerpc-smp
linux-restricted-modules-common   version 2.6.15.11-1
linux-restricted-modules-powerpc   version 2.6.15.22

---

### Post by Dutch on 2006-06-01
[QUOTE=aysiu]You don't need old Linux images (kernels)--go ahead and uninstall those.[/QUOTE]

How ?
How to locate them and how to remove them ?

---

### Post by ubuntubrian on 2006-06-01
That's the easy part. Synaptic shows them all but which are needed and which are safe to uninstall?

---

