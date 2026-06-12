---
title: "Install problems with nVidia"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by David Coton on 2013-01-07
Ubuntu 12.10 64bit with nVidia 660Ti

(System previously had 12.04, upgraded from earlier versions. New video card worked on 12.04)

I had a hard disk failure last night, so I'm trying to reinstall Ubuntu on a different but identical HD. The liveDVD works, no graphics problems. First I forgot about removing previous RAID data from the new HD, which wasted several hours. 

Now I have 12.10 installed, but on booting it complains about only having "low graphics", then won't run even that. It won't escape to console either -- just stops.  I can't intercept grub (single OS, does not respond to Shift key). I can get a liveDVD console, mount and chroot to the new install, but updates won't behave (unable to resolve any server paths). I can edit the grub configuration using ed, but update-grub complains that the \dev is not mounted (it is -- as far as I understand!)

Help please, before I either harm myself or buy Windoze (not even sure I can buy a DIY version, certainly not at a sensible price).

I can try to supply error messages on request, but I'm connected on a different PC so I may have to copy them manually. Yuck.

---

### Post by darkod on 2013-01-07
I would try the Shift option again, because it should be easier working from recovery mode. The computer might be too fast with the POST, try holding Shift as soon as it looks like POST is done. Also go into bios and disable any Quick Boot or similar options. You don't want them when troubleshooting, in fact you want time to hit Shift.

But even if you get to recovery mode, I am running ATI and I don't know which was the best nvidia package to install. Was it nvidia-current?

On another note, if you did the chroot procedure right, there is no reason update-grub not to accept the changes you did in the configuration. Make sure you are not editing the live session grub files.

---

### Post by David Coton on 2013-01-07
Thanks for your suggestions. I tried to install another version alongside to persuade grub to show up -- but even via grub edits I couldn't get a working text box on 64bits. In the end I found that the 32bit version (which I had installed in parallel with 64bit) works, out of the box, no problems. So I re-installed with just that, and it's all going fine. Now just Folding@Home on the GPU to install, via Wine. But that's not tonight.

---

