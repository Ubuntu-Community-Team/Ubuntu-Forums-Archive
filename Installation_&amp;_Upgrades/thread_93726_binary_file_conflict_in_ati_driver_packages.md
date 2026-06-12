---
title: "binary file conflict in ati driver packages"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by rocifier on 2005-11-22
Hi. I manually installed a .deb file from ati.com for my radeon 9600. It seemed to install alright using alien. But it did not make my opengl hardware accelerated. Anyway I see now in package manager it's recognised the package. The problem is the default one is there as well, and there is a file they're sharing. I'm not sure what I've done, but I've broken one of them now. The error is below. I am unable to remove either of the packages using synaptic package manager because it gives me this error. How can I go about resolving this cross-dependency? It seems a lot of programs I have rely on fglrx, so I don't want to try *completely* removing that. I tried deleting the .deb file manually but it just re-downloaded it. I am trying to get my system all error free before I upgrade to breezy. Now I remember - the site told me to make sure I have ubuntu-desktop package installed, so I added that. Unfortunately it had to remove libmesa-gl etc to install a different one, and something went wrong..


The following problems were found on your system:

E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb:  trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0

---

