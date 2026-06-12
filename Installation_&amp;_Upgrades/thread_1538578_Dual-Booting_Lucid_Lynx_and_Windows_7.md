---
title: "Dual-Booting: Lucid Lynx and Windows 7"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by iSeizmik on 2010-07-25
I've decided that after a long time of not being able to get some programs and games that I like to use(GuitarPro, Deus Ex) on Lucid, that I'll just Dual-Boot and have a Windows section dedicated to programs and games that Linux can't run so well, or where the alternative isn't as good.

I've dual-booted before, when I stared with windows XP and then added a karmic installation, but I haven't had luck doing that backwards (going from Linux > Linux+Windows)

Last time I tried this I had lucid lucid installed fine, but I didn't have a grub menu for selecting Windows, and didn't know how to create one.

I thought it might be a good idea to find out exactly what I'm doing *before* I do it this time. So basically my question is: can I add a Windows 7 partition to my currently Linux box without removing Linux first?

---

### Post by oldfred on 2010-07-25
Grub2 is better at finding windows partitions than grub legacy was.

You will need a primary partition NTFS for windows with the boot flag set. Depending on how you installed Ubuntu determines what primary partitions you have left.

After you install windows you have to reinstall grub2 to the MBR to boot Ubuntu & run sudo update-grub to get grub2 to find the new windows install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Older but goes over some of the issues, but use grub2 not any of the other alternatives shown:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

---

### Post by iSeizmik on 2010-07-26
Thanks oldfred, but I don't think I have any primary partitions available, as I formatted my hdd entirely before using the 10.04 LiveCd to install just ubuntu on 197gb and 3gb swap.

---

### Post by oldfred on 2010-07-26
Show us what partitions you have.

```
sudo fdisk -lu
```

---

