---
title: "How do I Upgrade through ISO?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by shafin on 2007-11-04
Hi,

I have a slow Internet connection,so I've downloaded the AMD64 alternate CD,But the problem is,I dont have a CD burner.

Is there any way I can upgrade using the ISO file?

Thanks

---

### Post by LinuxGuy1234 on 2007-11-04
> **shafin said:**
> Hi,

I have a slow Internet connection,so I've downloaded the AMD64 alternate CD,But the problem is,I dont have a CD burner.

Is there any way I can upgrade using the ISO file?

Thanks

The only 2 ways is to do this in your case:
Buy a CD-RW drive and a CD-ROM disc (if you need to)
                             or
Use gksudo "update-manager -c", because Gusty is released.

EDIT: You will need a CD-ROM writing program. K/X/Ubuntu have one. If you have a Mac, it comes with one also in /Applications/Utilities/Disk Utility. Under Windows, get one at: [http://infrarecorder.sourceforge.net/]("http://infrarecorder.sourceforge.net/")

EDIT 2: You can mount the ISO too. Do as root:
```

mount /path/to/ubuntu.iso -o loop -t iso9660 /mnt

```
Then add:
deb file://mnt main restricted
to /etc/apt/sources.list and change everything from "feisty" to "gusty" in it and run sudo apt-get update && sudo apt-get upgrade.

---

