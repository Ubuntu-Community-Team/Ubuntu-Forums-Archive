---
title: "Problem installing Gutsy on SATA HDD with IDE."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Tipharet on 2007-10-28
Im fairly new to the scene, so far its been a nice change and adjustment. For some reason, I keep getting error 15 when booting after installing. Basically, I have 1 SATA drive which is my primary and then I have 2 IDE HDD, which I disable in bios before installing. I have XP installed on first partition as C:. With 7.04, like I said all I had to do is disable IDE in bios and then choose where to install, left grub as (hd0) and it worked fine, however 7.10 will not.
 
I have tried leaving it default as well as trying to set grub to install in /dev/sda. This actually worked, then I decided I did not want the amd64 version. I can no longer get /dev/sda to work. I have also once installed booted to live disc and tried to reinstall grub ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGru](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGru)), but it always says it can not find the find /boot/grub/stage1"

I have also tried using the super grub disc and did not have any luck. What is going on here, why is this different?

---

