---
title: "Ubuntu 14.04 to 16.04.1 Upgrade - Trackpad/Touchpad not existing anymore"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by craft4 on 2016-09-02
Hello,
i run into the issue that after the upgrade from 14.04 LTS to 16.04.1 LTS my Touchpad is no longer working.
Been searching for a while now, there has been a thread in this forum marked as solved - [https://ubuntuforums.org/showthread.php?t=2322413](https://ubuntuforums.org/showthread.php?t=2322413) - yet this does not solve the issue for me.

When running on a Live system via USB Stick the Touchpad works perfectly fine, when booting my System - it does not.
Since it is working in a 16.04 Live System, i assume it is a configuration issue that came with the upgrade. 

Computer: Dell XPS13 9333

It is not show in the xinput devices:
```

xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 1241:1177                               id=9    [slave  pointer  (2)]
&#9116;   &#8627; SYNAPTICS Synaptics Large Touch Screen      id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                       id=14    [slave  keyboard (3)]

```

I tried the solution that was mentioned in the other forum thread - installing the xserver-xorg-input-synaptics, it was already installed - i did remove it and add it again:
```
apt-cache policy xserver-xorg-input-synapticsxserver-xorg-input-synaptics:
  Installed: 1.8.2-1ubuntu3
  Candidate: 1.8.2-1ubuntu3
  Version table:
 *** 1.8.2-1ubuntu3 500
        500 http://at.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

Driver missing? Can this be the issue? (from: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad))
```
synclient Couldn't find synaptics properties. No synaptics driver loaded?

```

Thanks, any help is appreciated.

---

### Post by craft4 on 2016-09-06
Solved the "Windows" way ... i made a backup of my home folder, then wiped Ubuntu and installed a fresh 16.04.1 release from my USB Stick.
--> works again.

Pad is detected and configured automatically, shown in all outputs.

---

