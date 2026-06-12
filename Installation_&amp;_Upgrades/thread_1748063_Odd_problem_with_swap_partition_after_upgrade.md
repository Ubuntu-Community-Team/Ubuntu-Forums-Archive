---
title: "Odd problem with swap partition after upgrade"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by alphacrucis2 on 2011-05-03
I decided to have a go at upgrading a laptop from 10.10 to 11.04 using the CD. I had downloaded it for a new install on another machine and thought it would interesting to try this new option in the ubiquity installer. Before doing the upgrade in place using the CD I made sure that internet access was available after booting off the CD before stating the upgrade. It actually went pretty well and it did download a few extra packages during the upgrade. At the end it came up with an error message which read something like error restoring package (or something like that I should have taken better notice). Anyway it then rebooted and I was surprised to find a nicely functioning system with all my data intact. The only nuisance was that it appeared that it removed all packages that I had installed from PPA's and a few downloaded deb files (googleearth and skype for example). Not a biggy I just had to reinstall a number of apps.

 A more curious thing is that it appears that the installer did something weird such that it seemed to have hosed the swap partition (not that I really need one). I had to reboot from a CD and fix it up using gparted. I was wondering if anyone else has come across anything like this.

---

### Post by alphacrucis2 on 2011-05-03
> **alphacrucis2 said:**
> I decided to have a go at upgrading a laptop from 10.10 to 11.04 using the CD. I had downloaded it for a new install on another machine and thought it would interesting to try this new option in the ubiquity installer. Before doing the upgrade in place using the CD I made sure that internet access was available after booting off the CD before stating the upgrade. It actually went pretty well and it did download a few extra packages during the upgrade. At the end it came up with an error message which read something like error restoring package (or something like that I should have taken better notice). Anyway it then rebooted and I was surprised to find a nicely functioning system with all my data intact. The only nuisance was that it appeared that it removed all packages that I had installed from PPA's and a few downloaded deb files (googleearth and skype for example). Not a biggy I just had to reinstall a number of apps.

 A more curious thing is that it appears that the installer did something weird such that it seemed to have hosed the swap partition (not that I really need one). I had to reboot from a CD and fix it up using gparted. I was wondering if anyone else has come across anything like this.

Googling around I find that someone else has seen the same issue.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/709363]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/709363")

Certainly one I have never come across before in quite a few upgrades.

---

