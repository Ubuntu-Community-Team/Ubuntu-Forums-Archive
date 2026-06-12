---
title: "Trouble installing 9.10 on AsRock Nettop Ion 330"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by mekanix on 2010-02-28
Hi

I'm puzzled at some severe installing-issues with a ASRock Nettop Ion 330.

I bought this specificaly because I thought it was Linux-ready - but this one does seem far from it. I've got at nagging feeling it might be HW-related.

This is what I've have done so far with a Ubuntu 9.10 Live CD:

1) Try to install directly from the CD (no booting into the Live CD) - but GParted couldn't detect the harddrive.

2) Checked BIOS - showed a nice Hitachi 160GB harddrive.

3) Booted the LiveCD - Running Gpartede. Still G-parted still wasn't able to detect the harddrive.

4) Googled around and tried booting the LiveCD with the nodmraid option. Gparted detected the harddrive so I ran the Installation. Towards the end (Grub install) Ubiquity crashed.

5) Tried running the installation without booting into the LiveCD - with the nodmraid and fingers crossed. Ubuntu got installed.

6) Rebooted PC... splash-screen... and then nothing.

7) Rebooted PC with the nodmraid option, and Ubuntu started.

8) Updated the install - hoping a new kernel might fix it. It didn't. Ubuntu jumps into shell at boot - it can't find the harddrive! And the "nodmraid"-option doesn't help. Sometimes the Grub-menu doesn't even show!

Weird part is - while am writing this, the person for whom I'm installing this told me it just booted fine - no issues!?!?

This really tells me that there is something wrong with the HW.

Any ideas how to proceed?

- Bjarne
- Bjarne

---

### Post by jcitguy78 on 2010-02-28
Dual-booting? if so what is the other OS? I may be wrong but if Gparted isn't finding the HDD you could have a HW issue. I am still learning all this too.

---

### Post by mekanix on 2010-02-28
No dual-booting. Crisp new PC with no OS on it.

I'm also leaning towards HW-issue though I'm not 100% sure since I could make Gparted detect the harddrive when booting with the nodmraid option.

Or perhaps it's just a loose wire and it's coincidence and it's a coincidence that it works (sometimes!) with the nodmraid option?

If I just new of a sure way to prove faulty hardware... this PC is a replacement from the shop - the first one she got had faulty RAM (and looked liked it was a used/returned one).

---

### Post by possumbasil on 2010-05-17
I have been struggling with an Asrock ION 330 in the weekend.  It has a Sata DVD and Sata WD500Gb, I could not get it to work with AHCI and ended up changing the bios value to IDE. I ended up with a working system, but I am still puzzled as to why the system didn't work as both IDs are SATA and the MB only has SATA connectors. Maybe one day it will come to me.

I also disabled the onboard Lan as this was something I had found on-line, but I do not know if that was needed.  Don't forget to cahnge it as otherwise the system will not pickup on the restricted driver for the Nvidea VDPAU.

good luck

I now have to setup XBMC on the little one.

---

