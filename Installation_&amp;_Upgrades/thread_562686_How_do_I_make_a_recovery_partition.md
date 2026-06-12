---
title: "How do I make a recovery partition?"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by deepseth on 2007-09-29
Hi,

I bought a shiny new Thinkpad, preinstalled with Windows. One of the nice features about it is the recovery partition. If anything goes hideously wrong with my Windows install, I can simply reboot, press the Acces IBM button on my keyboard, hit OK a few times, and it'll replace the Windows install with the factory default.

Is there an easy way I can go about doing something similar if I replace Windows with Ubuntu? Not all my devices are supported out of the box, and if something does go wrong, a simple reboot to my recovery partition to re-image the machine with a known working image with a few OK clicks would be ideal. I know it's not usually necessary to go to this extreme if you know what you're doing, and simply having an image stored somewhere and using a livecd + partimage would do the job, but that requires the end user to know what they're doing, which wont always be the case.

Any suggestions on how to go about doing this?

Cheers,
Deeps.

---

### Post by logos34 on 2007-09-30
I'm not sure there's a one-click restore solution for linux, but you could make a separate /home partition (a popular option), which is where all your personal data and applications settings are stored.  Save your downloaded/installed deb pkgs with APTonCD (or else make a separate partition for /var directory).  Backup other sys files using (automated) sbackup, and your gnome desktop settings with gnome-reset ..  If you brick your system, simply reinstall over the root partition and reinstall the deb pkgs.  Your saved files on /home partition remain unaffected.

Or, as you mentioned, you could periodically copy root with partimage, but yes that requires a bit more knowledge.

---

### Post by mhedges48 on 2007-09-30
How does one make an extra partition once Ubuntu has been installed?

thanks

---

### Post by logos34 on 2007-09-30
> **mhedges48 said:**
> How does one make an extra partition once Ubuntu has been installed?

you mean /home?

---

### Post by JBAlaska on 2007-09-30
Here's the guide I used, painless;
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mhedges48 on 2007-09-30
perfect, thanks!

---

