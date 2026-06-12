---
title: "Installing Windows after ubuntu and boot sequence"
date: 2018-09-26
forum: Installation &amp; Upgrades
---

### Post by jfca283 on 2018-09-26
Hi, 
I've installed Ubuntu 18.04 in my ssd disk. Now I'm planning to buy another ssd disk and use it as slave. Then I'd install windows on the slave drive.
The doubt I have is how do I add the windows in the grub sequence. Because I assume that grub won't detect the new OS on the slave drive.
Many thanks for your time and interest.

---

### Post by oldfred on 2018-09-26
If both systems are in same boot mode, both UEFI or both BIOS, then grub will find Windows on reboot and running:
sudo update-grub

Is system UEFI or BIOS? Windows may install boot files to default drive. So if Ubuntu drive is default in UEFI/BIOS Windows may install its boot files into that drive. It does not see nor seem to care if something is there. Or better to disconnect Ubuntu drive when installing Windows.
But disconnecting a drive may cause UEFI to lose UEFI entries. You can easily add back with efibootmgr or reinstall grub.

Note that grub2's os-prober only sees working Windows. And Windows has fast boot which is just hibernation. And if hibernation flag is set then Ubuntu cannot see the Windows install or boot it. And Windows will turn fast start up back on with updates.

If Windows 10 and its fast start up issue, you need to have its boot loader on its drive, so you can directly boot it from UEFI or BIOS, when it does turn on fast start or need other repairs.

---

