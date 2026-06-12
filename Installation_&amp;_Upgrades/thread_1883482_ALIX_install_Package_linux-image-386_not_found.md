---
title: "ALIX install: Package linux-image-386 not found"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2011-11-19
Hi,

I am currently preparing my CF card for use in an ALIX 3d3 box following those instructions: [http://wiki.ubuntuusers.de/Alix/CF-Bootmedium_erstellen](http://wiki.ubuntuusers.de/Alix/CF-Bootmedium_erstellen)

When it comes to installing the kernel, with "apt-get -y install linux-image-386", the response is: "unable to locate package linux-image-386". I've also tried with "i386" instead "386" but the kernel cannot be found.

What should I do next?

Oh, I'm using Ubuntu 11.10 for everything.

---

### Post by ygoe on 2011-11-20
Nevermind, the kernel linux-image-generic is just as fine, although not recommended by that tutorial.

By the way, don't try extlinux and just go with GRUB. extlinux doesn't do anything. It had cost me a few hours to figure that out. GRUB works just fine on the ALIX board and on my notebook (via USB CF card reader).

---

### Post by MAFoElffen on 2011-11-20
> **LonelyPixel said:**
> Nevermind, the kernel linux-image-generic is just as fine, although not recommended by that tutorial.

By the way, don't try extlinux and just go with GRUB. extlinux doesn't do anything. It had cost me a few hours to figure that out. GRUB works just fine on the ALIX board and on my notebook (via USB CF card reader).
Most of your problems seem to stem from that Tutorial being over 3 years old. :pts of changes since then.

---

### Post by ygoe on 2011-11-21
Well, it claims to be tested with Ubuntu 11.04 which is not so old now... But it seems it has not been updated after 10.04 and that's where the changes come from.

Now I've got my own script for 11.10 which I may eventually publish.

---

### Post by rufik on 2011-11-22
> **LonelyPixel said:**
> 
Now I've got my own script for 11.10 which I may eventually publish.

Could you share?

---

### Post by ygoe on 2011-11-24
Here's the current draft. It's incomplete for the LED and WLAN part, but the base system works fine so far. German only. PDF and automated bash script included.

[http://unclassified.de/tmp/ubuntu-11.10-alix-3d3.7z](http://unclassified.de/tmp/ubuntu-11.10-alix-3d3.7z)

(A more stable URL will follow.)

---

### Post by ygoe on 2012-05-06
I have upgraded my ALIX and the installation tutorial for Ubuntu 12.04 LTS just in case somebody would be interested in it. It wasn't a big deal, mostly replacing "oneiric" with "precise". I'm still looking for a decent place to publish it, preferably near my website or maybe some Ubuntu wiki.

---

### Post by binary_dreamer on 2012-10-01
Hi. i am afraid i am getting into a problem with this file. it says that it is corrupted. is is possible to get the instructions?

also will it work for all alix variants?

---

