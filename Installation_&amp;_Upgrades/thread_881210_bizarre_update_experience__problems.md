---
title: "bizarre update experience / problems"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by virgil_disgr4ce on 2008-08-05
Hi everyone.  Recently I went ahead and started some updates as I have often done before--I'm not even sure what all was in there, I only remember seeing Evolution and various other mundane things.  When I came home the next day the computer was crashed.  When I hard rebooted it it reported hundreds of filesystem errors.  I tried fsck and then saw a thread about e2fsck (I think?) and amazingly enough that sort of worked and brought me back into Gnome, except that now my video card drivers weren't detected, the resolution was back to 800x600, and no sound card drivers are detected, and some apps like Firefox won't start.

Needless to say I never touched the hardware, and the harddrives are basically all new, and all my data is intact just as before.  The package manager system icon showed the "do not enter" sign so I found a thread about running dpkg --configure -a via an ssh session.  But now it's hanging on "running depmod" after "Setting up linux-image-2.6.24-19-generic (2.6.24-19.36) ...".  I can't seem to start any new ssh sessions, though my VNC session runs normally; and attempting to start the package manager in gnome does nothing.  Samba server seems fine as I'm still streaming music and such from it.

I'd love to hear any help about what to do... I am loathe to hard reboot this thing again as it seems so shaky.  But I have no idea how to proceed!  Thanks so much in advance!

---

