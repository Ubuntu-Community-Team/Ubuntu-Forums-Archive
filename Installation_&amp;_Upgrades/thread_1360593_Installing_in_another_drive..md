---
title: "Installing in another drive."
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2009-12-21
I had Karmic installed with option "install along with windows xp side by side". Now I have emptied a drive for Ubuntu alone. What I want is to install Ubuntu in this empty space and delete the already installed ubuntu "installed along with xp side by side". If I try to install now the installer detects the already installed Karmic and windows.

What can do?

Thank you for help.

---

### Post by hariks0 on 2009-12-21
Nobody ?

---

### Post by darkod on 2009-12-21
First read everything and if you have any questions ask. Make sure you have all CDs that you need.
If you do not have any data now in ubuntu that you want to save, just boot XP and from disk management delete the ubuntu partitions. Then create one single ntfs partition in their place which you can use for XP. Then boot with XP install CD and repair the MBR of that drive. Make sure you have this CD, I'm not sure how to do it without it.
After you have sorted out disk1, go into BIOS and set the ubuntu disk to be first option in boot options, before the windows disk. Then just boot with ubuntu cd, select Install Ubuntu and install it on your other drive as you want.
Instructions how to restore XP bootloader with XP disc:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by hariks0 on 2009-12-21
> **darkod said:**
> First read everything and if you have any questions ask. Make sure you have all CDs that you need.
If you do not have any data now in ubuntu that you want to save, just boot XP and from disk management delete the ubuntu partitions. Then create one single ntfs partition in their place which you can use for XP. Then boot with XP install CD and repair the MBR of that drive. Make sure you have this CD, I'm not sure how to do it without it.
After you have sorted out disk1, go into BIOS and set the ubuntu disk to be first option in boot options, before the windows disk. Then just boot with ubuntu cd, select Install Ubuntu and install it on your other drive as you want.
Instructions how to restore XP bootloader with XP disc:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Only that I do not have a different partition/disk1 of Ubuntu as it was installed in C: along with Windows XP side by side.

---

### Post by darkod on 2009-12-21
> **hariks0 said:**
> Only that I do not have a different partition/disk1 of Ubuntu as it was installed in C: along with Windows XP side by side.

If you installed inside XP, using wubi.exe, then that's not side-by-side. Side-by-side is a term used when you have XP on one partition, and Ubuntu on completely another.
If you installed using wubi it's even easier to remove it. Open Add/Remove programs and it should have ubuntu entry inside. Just uninstall like any windows program.

---

