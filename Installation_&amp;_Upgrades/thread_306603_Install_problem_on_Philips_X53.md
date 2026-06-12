---
title: "Install problem on Philips X53"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by jasontheknight on 2006-11-25
Hello

I recently purchased a new laptop (Philips X53) - I'm installing Edgy (or trying to), but every time it tries to detect the network adapters it fails. A bit of Google-fu has shown me that this is a known problem (well, by about 5 people it seems), and is because the 8139too module has an option missing by default which causes the NIC to lock the system up (CONFIG_8139TOO_OLD_RX_RESET needs to be set and isn't).

Anyway, I don't even need this network adapter to be working (we're all wireless here and we don't even have a wired router) - and in any case I can sort that out once I'm installed... my basic question is how to stop Ubuntu auto-detecting eth0 - I don't need it, I don't want it, and it's beginning to annoy me! 

One thing I did try was simply dumping the ISO onto disk, uncompressing the SquashFS'd filesystem, removing the offending module, resquashing and remaking the ISO and installing from that, but that seemed to hang at the same point.

Any help would be much appreciated!

Jason

---

