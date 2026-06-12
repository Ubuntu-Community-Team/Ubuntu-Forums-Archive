---
title: "Ubuntu 6.06 K8N4-E"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Aphoxema on 2007-02-06
Hello, I'm having an issue with my Asus K8N4-E (Called 'Deluxe', but that's an interesting thing to call it when there aren't any other K8N4-Es).

Booting from Ubuntu 6.06 hangs with an endless attempt at...

hda: dma_timer_expiry: dma status == 0xff

The problem is *not* DMA, it's 'MMConfig' PCI access. A kernel configured with 'any' PCI access can be booted on a K8N4-E (and I think a few other Asus boards that are difficult about it) by appending 'pci=nommconfig', but I can't get this to work on any of the Ubuntu/Kubuntu 6.06 discs I got from Shipit.

Recompiling a 2.6 kernel with 'Direct' PCI access solves the problem. I haven't tested BIOS access.

Passing ide=nodma isn't a solution at all, because all it's doing is sidestepping another problem caused by the first one... the hard drive controller can't be properly accessed because of MMConfig's incompatability. While the kernel doesn't hang on trying to access the controller anymore, it still can't access the USB controller, the SATA controller, the ethernet controller, and I expect nothing plugged into any PCI slots will work (right), either.

I believe the problem is that the Ubuntu kernel is compiled with MMConfig access only, so pci=nommconfig doesn't really do anything.

My problem is that I want to try Ubuntu (I've already gotten several other people trying it, but I feel like a punt getting them on it when I haven't even used it), but I can't boot it on this motherboard without breaking support.

So, I want to know how to boot Ubuntu using a different kernel (and make things like the initrd still work), from another GNU/Linux installation (Slackware), or if there's any other way around it, like loading direct PCI access drivers somehow.

Honestly, this is mostly to satisfy my curiousity, and so I can feel more confident handing out Ubuntu discs to the kids at the college. I only desire a rapid solution, so anything more lengthy would be for the sake of other K8N4-E users... so, in other words, no rush.

---

### Post by urson on 2007-02-08
Oh, I "got through hell to get it working" ;) But the solution is the simpliest thing i've thought about... You just have to add "pci=nommconf" boot command, instead of the "pci=nommconfig", which is "not supported" by ubuntu.
Cheers ;)

---

### Post by eeried on 2007-02-13
Hello,

There are other kinds of  K8N4-E than deluxe:  K8N4-E SE, for instance. it looks similar but for the LAN chip. As I may buy this motherboard, I'm interested in this thread.
cheers

---

### Post by karnbo on 2007-03-01
Me too had simular problems with the K8N4-E Delux motherboard.
First upgraded from BIOS 1007 to BIOS 1010, didn't help, tried 4 different linux distributions. 
Then upgraded to BIOS 1011. That did the trick.

/karnbo

---

### Post by eeried on 2007-03-01
Good news, karnbo! Could you explain how to flash the BIOS safely?
Thanks!:)

---

