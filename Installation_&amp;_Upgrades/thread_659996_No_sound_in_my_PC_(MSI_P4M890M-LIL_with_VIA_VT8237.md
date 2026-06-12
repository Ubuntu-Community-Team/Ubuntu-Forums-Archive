---
title: "No sound in my PC (MSI P4M890M-L/IL with VIA VT8237 paired with VT1708 sound)"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by azwandy on 2008-01-06
Hi guys.I've got a big problem with my ubuntu 7.04 Feisty Fawn installation. After the installation was completed, there's no sound coming from the speakers. Right now I'm using a PC with MSI PM890 motherboard,VIA VT8237 chipset paired with VT1708 8 channel sound. I've tried installing the driver according to the instructions provided by the VIA Arena website. At first, the sound was there.But when I updated my kernel from the default kernel (2.6.20.15) to 2.6.20.16, there was no sound anymore.Hope you guys can help me with this annoying problem.I've installed the latest version (7.10) but the same problems happened.I want to continue using Ubuntu 7.04 because I've already got 1 addon cd and 4 DVDs of Ubuntu repository.I have no Internet connection for my PC.That's why I hope any of you expert guys out there can help me.I will be grateful to death.

According to the VIA website, the driver there is only for the default Ubuntu kernel.So where can I've download the driver mention for different kernel??

In the installation instruction, it told me that I have to issue this command:

#modprobe -r snd-hda-intel

but everytime I ran this command, this message is shown:

FATAL:modue snd-hda-intel is in used

Therefore, I need to know how to unload modules in Linux properly.

Thanks guys.Any help,guides and suggestions is much appreciated.:KS

---

### Post by Paul Dufresne on 2008-01-12
This was reported in bug #137474.
[https://launchpad.net/bugs/137474](https://launchpad.net/bugs/137474)
It won't be fixed in Feisty.
It is expected that it has been fixed in main line alsa-kernel repositories, but not yet included in Hardy.
At least this is how I interpret developers comments.

---

### Post by jcwmoore on 2008-01-12
I had problems with the sound when I moved to version 7.04.  For some reason some of the volume controls were muted by default (I also noticed this when upgrading to 7.10 also)  so the fix was to open volume control and go to Edit>Preferences and click on all the check boxes, then make sure none of the options were set to mute.  I realize this is a simple fix and if you have already tried this then just ignore this post...

---

