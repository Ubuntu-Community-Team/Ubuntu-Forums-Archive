---
title: "Unable to launch new Firmware Updater"
date: 2023-10-16
forum: Installation &amp; Upgrades
---

### Post by FrancoNero on 2023-10-16
Updated from 23.04 to 23.10 and not only was there no firmware updater (even though mentioned in all the articles and release notes) - no biggie, installed the snap by hand - but now it also doesn't launch. The app opens, but just shows a spinning wheel of death. Any ideas?

---

### Post by ActionParsnip on 2023-10-16
Try:
```

sudo service fwupd start
sudo fwupdmgr refresh
sudo fwupdmgr update

```

---

### Post by mbhaber on 2023-10-20
Same issue, tried your suggestion, didn't work. Also, fwupd wasn't even installed, I had to install it manually from the App Center.

Edit: The .deb version of fwupd was not removed when I upgraded from 23.04 to 23.10. Installing the snap version of fwupd with the .deb version still installed seemed to slow down the system a little. I removed the .deb version of fwupd, which then let me uninstall the snap (wouldn't before), and then reinstalled the fwupd snap. But "sudo service fwupd start" results in:

```
Failed to start fwupd.service: Unit fwupd.service not found.
```

So I decided to configure the system to status quo ante, removing the fwudp snap, and reinstalling the fwupd .deb. Has Canonical disabled fwupd, and held back the "Firmware Update" software, on some systems?

```
Preparing to unpack .../fwupd_1.9.5-1_amd64.deb ...
Unpacking fwupd (1.9.5-1) ...
Setting up fwupd (1.9.5-1) ...
fwupd-offline-update.service is a disabled or a static unit not running, not sta
rting it.
fwupd-refresh.service is a disabled or a static unit not running, not starting i
t.
fwupd.service is a disabled or a static unit not running, not starting it.

```

---

### Post by mbhaber on 2023-10-22
Leaving only fwupd.deb installed, then installing Firmware Updater per instructions at [https://snapcraft.io/install/firmware-updater/ubuntu#install](https://snapcraft.io/install/firmware-updater/ubuntu#install) seems to have everything working fine now.

---

### Post by MAFoElffen on 2023-10-22
Thank you for that tip!

---

### Post by FrancoNero on 2023-10-28
so how do I remove the darn snap version of fwupd then?

---

### Post by #&amp;thj^% on 2023-10-28
> **FrancoNero said:**
> so how do I remove the darn snap version of fwupd then?

```
snap remove firmware-updater
```

---

### Post by FrancoNero on 2023-10-29
No, I want to remove the fwupd snap, not the firmware-updater snap. So I removed fwupd that way, which previously didnt work no Idea why. then reinstalled firmware-updater. and now it launches.

---

