---
title: "Ubuntu installer freezes at initramfs on Toshiba x205 laptop"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by Darkhorse on 2007-08-14
I'm trying to install Ubuntu 7.04, and the installer boots and gets to the initramfs screen and just stops. Nothing happens. I'm trying to install Ubuntu on a new Toshiba x205 laptop with windows vista and 2 hard drives. Help?

---

### Post by talby on 2007-08-14
Apparently the init ramdisk does not have support for certain toshiba hardware controller, I found ["Installing Ubuntu linux in Toshiba Portege S100"@blog.nominet.org.uk]("http://blog.nominet.org.uk/tech/2006/05/08/installing-ubuntu-linux-in-toshiba-portege-s100/") and [" Ubuntu 7.04 on Toshiba Portege S100"@ubuntuforums]("http://ubuntuforums.org/showthread.php?t=519229") they have similar solutions using the ata_piix and ahci modules, maybe it will work for you as well.

Cheers, and good luck

---

