---
title: "Preserve GRUB BEFORE Windows install"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by hexwind on 2010-05-04
I have to install Windows XP on another partition which already has Windows Seven installed.. but I want to preserve my GRUB2 installation without going through that GRUB reinstall process. Can I copy my /boot/grub that works fine and then paste it again through the live CD?
Thanks in advance

---

### Post by mikewhatever on 2010-05-04
There is no need to backup anything in /boot/grub, because that location (and in fact, any other on the Ubuntu partition) is not affected by installing Windows. You could backup the MBR and restore it after Windows installation, in which case, you shouldn't need to reinstall grub.
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)

---

