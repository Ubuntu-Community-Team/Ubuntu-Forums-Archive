---
title: "dual boot weirdness"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by warden1337 on 2006-11-01
Hello

Here is my problem. I was having some grub issues in the past so i decided to set up a dual boot ubuntu/xp system a little differently this time. What i did was install xp on one of my sata drives with just it plugged in and the other unplugged. Then i installed ubuntu on the other sata drive with the xp drive unplugged. That way when i wanted either distro i would just change the drive order in my bios and boot which OS i wanted.

With windows this works fine. Windows is on the first drive channel 0. When i select drive 1 (ubuntu) to boot first with the xp drive plugged in ubuntu freezes at the splash screen. If i unplug the xp drive and then fire up ubuntu it loads fine. 

I am stumped...

Warden.

btw this is 6.10

---

### Post by Kateikyoushi on 2006-11-01
You have to edit your grub menu, because the drive order changed by adding the windows drive. I wonder if changing the cables of the two drives would be enough.

Anyway, what you need is your  partition layout

```
fdisk -l
```

and to edit your menu

```
sudo nano /boot/grub/menu.lst
```

Help about dualboot setup. [LINK]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by gn2 on 2006-11-01
Do you have a "Boot device selection menu" available from pressing F8 (or other key depending on BIOS version)

If you have this option you may not need to actually change the boot order each time.

---

