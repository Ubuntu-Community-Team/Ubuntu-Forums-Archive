---
title: "Upgrade to Gutsy stuck using Adept on &quot;Stopping Bluetooth Services&quot;"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by secretservgy on 2007-11-18
I'm upgrading to Gutsy , using kubuntu, so I'm upgrading through adept. The upgrader is on Installing Updates but stuck for the last maybe, 30 minutes, at 

```
Preparing to replace bluez-utils 3.9-0ubuntu4 (using .../bluez-utils_3.19-0ubuntu3_i386.deb) ...
 * Stopping Bluetooth services

```

How can I fix this? Thanks.

EDIT: In another terminal I did ```
 /etc/init.d/bluemon stop
``` Which killed that succesfully. But then I also did ```
/etc/init.d/bluetooth stop
``` which just hangs.


EDIT2: I just kill'd bluetooth process, now the dist-upgrade is continuing, a box came up to report it as a bug (becuase it couldn't install bluez something or other) but it made Adept freeze, so I needed to close that box.

---

