---
title: "e-maxchine - ubuntu install hangs"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by monochasr on 2007-06-26
due to necessity, I installed ubuntu7.04 on a hard drive using a compaq box, then installed the working linux hd into a recalcitrant e-machine. upon boot, it gets to GRUB Loading... ; 8254 timer not connected to... ; then the Ubuntu logo appears in center of black screen with a progress bar. After 5-10 minutes, this message appears: 270.489670 <0> Kernel Panic - not syncing: Fatal exception in interrupt.

Ok, so I try to install it on top of itself by booting up from an ubuntu7.04 cd.in the e-machine with the bios set to boot from CD. This failure happens much faster. There are a bunch of characters like a memory dump, last entry being 36.790182 Segmentation Fault.

The e-machine doesn't seem to like this O.S. change, is there some proprietary bios code that prevents this? This hard drive works in the compaq... nice clean install & update. I'm standing by with a soldering iron, ready to rip out that bios chip--- just give me the circuit board coordinates......!

Really, any ideas? Its heavy enough to be a canoe anchor.

---

### Post by dabl on 2007-06-26
I recently did a Ubuntu 7.04 installation on a new e-machine PC -- can't recall the model number off the top of my head, but it had Vista pre-installed, so I just shrunk that partition down to 20GB and then put Feisty on the rest of it.  The only hiccup I ran into was that it needed the xserver-xorg-video-intel driver to run a 1400x900 display on that Intel video chip.  I didn't need to touch the BIOS.

I think maybe your mistake is installing on Compaq and then booting on e-machine -- the software is now "built" for the Compaq.  Can you wire up a CD ROM drive to the e-machine for long enough to install Ubuntu on it? Probably that's what you're going to have to do. :(

---

### Post by monochasr on 2007-06-26
Well, I left some stuff out that was probably necessary info - the e-machine's windows portion is broke- it keeps asking for a recovery disk- and that's all it does. I can't boot from the cd, nothing- that's why I used the compaq to install ubuntu on that drive, but you gave me an idea to remove and somehow format and partition that e-machine drive, put it back in and hope I can boot from live cd for install. Soldering iron is on stand by.

---

### Post by dabl on 2007-06-26
Is it set in BIOS to boot first from the CD ROM?  I think they had mine set to boot first from hard drive, so that could screw you up.

---

