---
title: "Edgy install boot crash"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by ZQJ on 2007-01-16
I've been trying to install Edgy (Kubuntu) today but I've been completely stumped by this problem. 90% or so of the time the installation CD hangs during the boot sequence (I've put a photo of the kernel output up [here](http://users.ox.ac.uk/~univ1845/pict4324-1.jpg)). Occasionally it will start, successfully but for no apparent reason. I've tried the noapic and nolapic options with no success.

I also tried installing Edgy (Ubuntu) about two months ago with similar results, except then I did proceed with the install when the installer booted successfully. However the installed system suffered the same problem so I pretty quickly went back to my old distro, Debian (that's got its own problems though).

---

### Post by sn0m on 2007-01-16
Hi, ia had kinda the same problem, but it was due to a RAM failure. Have u tried to memory test them?
Koli

---

### Post by ZQJ on 2007-01-16
Well, I've just done about an hour of testing a few options, and it seems I may have two separate problems on my hands. If I take off the 'splash' option and add 'mem=512M' then it boots fine every time. Without either it crashes during USB setup as before, but with the splash screen (and messages) it crashes during 'scripts/casper-premount'. I'd really like to get to the bottom of this a bit better though because one thing I don't want is an OS that doesn't boot...

---

