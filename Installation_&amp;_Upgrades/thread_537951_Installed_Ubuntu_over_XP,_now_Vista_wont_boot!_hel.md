---
title: "Installed Ubuntu over XP, now Vista wont boot! help!"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by Singee15 on 2007-08-29
Previously I had windows XP and Vista installed. I decided to delete XP and install Ubuntu (Feisty). So after grub installed it didn't have an option for booting to Vista. So i added one:
title Windows Vista
rootnoverify (hd0,1)
makeactive
chainloader +1

but when I try to boot to it I get the dreaded "bootmgr missing" message. I have a lot of important info on the vista partition so I can't reformat or anything like that.

Any ideas?!

---

### Post by merlinus on 2007-08-29
Easy way out -- boot from vista cd, choose recovery (or something similar) and fix mbr.

Then you will have to reinstall grub, but that is not difficult.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

-merlin

---

### Post by al108 on 2007-08-29
I had to go thru a lot of trouble recently with XP/Vista/Ubuntu trippleboot. Here's what I ended up with: Vista loader on the top, Grub installed on Ubuntu partition.

I'm sure there are ways to make Grub configured to work for you but what I did worked just fine.

1. Now to get Vista back I used [mbrfix]("http://www.download.com/MbrFix/3000-2094_4-10485991.html") after booting with Vista DVD

```
 MbrFix /drive 0 fixmbr /vista
``` Or
```
bootsect SYS c:
``` from vista DVD might work too.

Reinstall a [Vista bootmanager]("http://technet2.microsoft.com/WindowsVista/en/library/49ded4da-b66f-4b42-9563-04c218a1a6ac1033.mspx?mfr=true") from DVD

using ```
bootsect /nt60 ALL

```2.Install Ubuntu from alternate CD and in the end choose  to  install grub to a partition where you installed Ubuntu.

3.Use [easybcd 1.6]("http://neosmart.net/dl.php?id=1") to edit Vista boot manager to add your Ubuntu to the boot menu.

4.Enjoy

---

### Post by maybeway36 on 2007-08-29
I hate how Windows Vista puts its bootloader on the XP partition. (XP with 98 did the same thing.)

---

