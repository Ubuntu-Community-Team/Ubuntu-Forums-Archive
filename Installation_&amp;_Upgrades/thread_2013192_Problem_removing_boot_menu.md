---
title: "Problem removing boot menu"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by SudeepShakya on 2012-06-30
I wanted to remove Ubuntu, so when i previously uninstalled it; the GRUB remained. So last time i reinstalled windows. This time first I removed Ubuntu(ie  from boot menu) from EasyBCD and then tried to uninstall Ubuntu, but it failed because of some error. Then I just deleted the Ubuntu folder. But the boot menu appears with Windows only(I removed it using EasyBCD) but I don't want those menus. Is the GRUB removed or is it still there ?? And i tried to install Ubuntu(inside windows), the installation doesn't asks about uninstalling previous Version of Ubuntu(previously 11.10). So again I want to ask is GRUB removed ?? And how to skip the Boot choosing screen ?

---

### Post by darkod on 2012-06-30
With wubi you have no grub in reality, everything is virtual.

By deleting the ubuntu folder everything is deleted. If you uninstalled it in Control Panel - Programs, then it should be done.

You also deleted the wubi entry from the windows bootloader.

Maybe you will have better luck asking on the windows forums or EasyBCD forums since this is windows bootloader you are asking about, not grub.

With wubi windows bootloader remains on the MBR of the disk, and when you select ubuntu from it only then a virtual grub menu shows up. But you never had grub on the MBR.

---

### Post by SudeepShakya on 2012-06-30
But, The boot menu with only Windows option is displayed. And I always have to press enter to continue or wait for few seconds. Later on I again tried to reinstall Ubuntu(inside windows) but when rebooted, there was only Windows as the option to select. Did EasyBCd did some nasty stuff ??
Sorry for trouble. I will try to get solution from other forums. 
ThanK U very much for reply

---

