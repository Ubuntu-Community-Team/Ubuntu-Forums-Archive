---
title: "re-install without currupting home partition"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by fsman on 2005-04-25
I've installed hoary with 3 partitions
1 /
2 Swap
3 Home

I'm installing a new motherboard, which will remove sblive and pci Lan. So I want to do a clean install on the new hardware.

What do I need to do in the installer to ensure that only partitiions 1 & 2 are reformatted. Also how do I ensure that the permissions on the Home partition are still valid for the new install?

---

### Post by derrick1985 on 2005-04-25
[QUOTE=fsman]I've installed hoary with 3 partitions
1 /
2 Swap
3 Home

I'm installing a new motherboard, which will remove sblive and pci Lan. So I want to do a clean install on the new hardware.

What do I need to do in the installer to ensure that only partitiions 1 & 2 are reformatted. Also how do I ensure that the permissions on the Home partition are still valid for the new install?[/QUOTE]

I can't say from personal experience, i'm just going to say what I see in the Ubuntu Installer.

One, if you do a manual format, you can just format the first two partitoins (/ and swap) and leave the home. Select the home partition though, and select to use it, but dont' format it. (not formatting should be the default)

Just try the installer and see what you get, it won't write changes until you say YES

---

