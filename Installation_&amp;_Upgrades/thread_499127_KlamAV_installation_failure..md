---
title: "KlamAV installation failure."
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2007-07-12
(Reposted from [http://ubuntuforums.org/showthread.php?t=498827](http://ubuntuforums.org/showthread.php?t=498827) - Accidentally posted to wrong forum.)

I get KlamAV installed via synaptic no problem, however, when I try to run it, I get this:


```

~$ sudo klamav
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
QLayout "unnamed" added to Klamav "KlamAV ", which already has a layout
klamav: Checking for new ClamAV
klamav: ERROR: Couldn't start kio_uiserver from kio_uiserver.desktop: KDEInit could not launch 'kio_uiserver'.
klamav: Checking for new KlamAV
khtml (dom): WARNING: Can't communicate with cookiejar!
khtml (dom): WARNING: Can't communicate with cookiejar!
khtml (dom): WARNING: Can't communicate with cookiejar!
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)

```

Can I get a translation and help please?

And yes, I know I don't need an anti-virus :lolflag:

Previous response was to use klamav without sudo.

---

### Post by VoiceOvGod on 2007-07-12
I should mention I am using KDE. Been playing with it trying to make up my mind between GNOME and KDE.

---

### Post by kitterma on 2007-07-12
I'm not sure exactly what to tell you.  When I install klamav and run in on my Dapper KDE system, it just works.  Please file a bug against klamav with the above information on Launchpad.  Specify you are using Dapper Kubuntu.

---

### Post by VoiceOvGod on 2007-07-15
Ok, I've filed Bug #126199.


Thanks!

---

