---
title: "New install freezing on LiveCD / 6.10"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by nstrom on 2007-02-28
I'm having some issues installing Ubuntu 6.10 on one of my PCs. Computer is a based on a Shuttle
[SN41G2]("http://global.shuttle.com/Product/Barebone/brb_OverView.asp?B_id=11") barebones system (FN41 motherboard). Chipset is nForce2, using onboard video, ethernet, sound. 2GB RAM. Netgear WG311v2 PCI 802.11g wireless adapter. USB mouse, PS2 keyboard. That's it hardware-wise.

On booting the 6.10 install/liveCD the system will randomly hard-lock (freeze). Ctrl-alt-delete won't do anything, caps lock won't respond -- hard reset w/ reset button on case is needed. As far as I can tell, it is not freezing at any consistent spot. It's frozen as the desktop is loading both before and after icons have been visible, and one time I was able to start the actual install process (double-clicking on install icon) before it froze.

On reading the forums, it seems freezing has been reported by others, but most of the reports I've read have correlated it w/ ATI video cards, which this PC does not have. I have tried booting without the mouse connected, and using the kernel flags "irqpoll pci=noacpi noapic nolapic acpi=off" as suggested in [this post]("http://www.ubuntuforums.org/showpost.php?p=2191079&postcount=4") but to no avail.

I have MD5 verified the downloaded ISO image and the burned CD and both check out.

[Edit: I forgot to mention that I also tried loading in safe video mode, no dice also.]

This system is stable in Windows, and Windows has recently been freshly installed after a HDD repartition leaving some room for Linux.

Any suggestions? I'm new to Ubuntu but experienced w/ Linux in various Mandrake and Red Hat flavors.

Thanks in advance.

---

### Post by solar george on 2007-02-28
Try using the alternate install cd.

---

### Post by nstrom on 2007-02-28
Will do... But if the livecd isn't working I am not expecting stellar results once installed, even if the alt installer works.

I'll give it a shot though, thanks.

---

