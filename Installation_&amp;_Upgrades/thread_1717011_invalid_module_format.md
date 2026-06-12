---
title: "invalid module format"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by jcrowley3 on 2011-03-29
New install of Ubuntu 10.10, uname -r shows as 2.6.35-22-generic

We need to make a patch to a loadable module -- snd-usb-audio.  Downloaded the source, and re-built the kernel with no problem, but cannot install the new version of snd-usb-audio.ko (note:  the original source -- have not applied any changes yet).

Modprobe issues 'Invalid module format',  dmesg has the message "disagrees about the version of symbol module_layout"

Modprobe with -f (force) does not change anything.  With --force-modversion same result.

Did a 'modinfo' on both the original version (from the install) and the re-compiled version -- the only difference is the 'srcversion' value.

Also, doing an apt-get on the linux-source brings down 2.6.35.11 (from the Makefile).  Changed this to be 2.6.35-22-generic in order to get the correct 'vermagic' in the module.

How should we approach this issue?  Is there a version of the source that exactly matches the 2.6.35-22-generic kernel from the installation?   Do we have to re-compile and replace the entire kernel (really trying to avoid that as a general approach)?  Is the 'srcversion' mismatch the cause of the Invalid module format error?  If so, can we fudge that to get the module to load?

BTW:  In general, would prefer to have the apt-get linux-source exactly match the installed kernel to avoid any possible mis-matches.

Thanks for any advice.

---

