---
title: "Ubuntu 10.04 LTS upgrade to 12.04 LTS"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by dayab on 2013-06-21
Hello all,
I tried to upgrade 10.04 LTS to 12.04 LTS using Alternate CD. I mount the ubuntu-12.04.2-alternate-amd64.iso and run the cdromupgrade file. It runs for some hours, upgrading packages successfully, but when the system is restarted, it doesnt boot. I have tried it Virtualbox, and while booting after upgrade, it only shows some dots.

Howerver, I have am able to upgrade using Online repo, using do-release-upgrade. Do anybody upgraded 10.04 system using Alternate CD.

Thanks !

---

### Post by grahammechanical on 2013-06-21
Do you get a Grub boot menu? If so try Recovery mode>Resume and if you get to a desktop activate a video driver. When we upgrade using the alternate CD some packages cannot be upgraded because the newer version are not on the CD. I am wondering if 12.04 needs a video driver that has to be downloaded and installed through Additional Drivers.

Regards.

---

### Post by dayab on 2013-06-21
Hi, I have tested in Virtualbox, and I couldn't see the grub boot menu. It only shows some white spot dots. I have repeated the upgrade process for 3 times, same error appear. I am in need of offline LTS upgrade. Is there is any way, I make my own private repo, make the bundle and use it for upgrade. 

Thanks,

---

### Post by dayab on 2013-06-26
I have found it to be the Virtuabox issue. It couldn't properly display the fonts. In Vmware the error didn't came. My curiosity is ,it upgrade most of the packages but fails to upgrade the kernel. When rebooted after successfully upgraded, it again show the same 2.6 .28 instead of 3.x Kerenel. Any idea to upgrade the kernel  by Alternate cdrom upgrade.
thank You !

---

