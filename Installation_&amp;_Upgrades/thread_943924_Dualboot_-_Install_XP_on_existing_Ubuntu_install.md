---
title: "Dualboot - Install XP on existing Ubuntu install"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by sufslnd on 2008-10-10
The XP install hangs after intial loading of drivers. Gives me a black screen and a bliking cursor.

I have tried each of the memory modules and without HDD, still hangs at the same place.

This is very funny because I have installed XP over ubuntu before on this computer. And ubuntu over XP at least five times on the same computer.

Anyone? This is bugging the crap out of me, because although I use Ubuntu on a 24/7 basis, I need XP to play my games.

---

### Post by Pumalite on 2008-10-10
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by sufslnd on 2008-10-10
Well, I've done that. But the windows install hangs and gives me a black screen just before the xp partitioner loads.

---

### Post by Pumalite on 2008-10-10
Well, you probably made a mistake somewhere. Get Super Grub and see if you can boot Windows:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Also post:
sudo fdisk -lu

---

### Post by sufslnd on 2008-10-10
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42d542d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        81915435   476230859   197157712+  83  Linux
/dev/sda2       476230860   488392064     6080602+   5  Extended
/dev/sda3   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda5       476230923   488392064     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by sufslnd on 2008-10-10
I have tried without the HDD pluged into the SATA connector, and it still hangs without giving me an error message. This leads me to think it is not HDD related, but I could be wrong.

---

### Post by caljohnsmith on 2008-10-10
It sounds most likely that you have a Windows problem and not a Grub problem, but we should at least check your Grub menu entry for Windows just to make sure; please post the Windows entry from:
```
cat /boot/grub/menu.lst
```
Do you have your Windows XP Install CD? I would boot that up, go to the recovery console, and begin with the following commands:
```

fixboot
chkdsk /r
```
Probably it will take more to fix your Windows, but we need to make sure you don't first have some really basic problem, which is the reason for the above commands. So give that a shot, let me know if it changes anything, and we can go from there.

---

### Post by sufslnd on 2008-10-10
Well, problem is: I CANT install windows. When I insert the XP install CD crashes during the intial loading, before I get to the XP partitioner that is. I have tried my original XP CD and my nLite stripped one.. :/

---

### Post by Pumalite on 2008-10-10
Try shrinking Ubuntu with Gparted Live CD and formatting the new space ntfs
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by sufslnd on 2008-10-10
> **Pumalite said:**
> Try shrinking Ubuntu with Gparted Live CD and formatting the new space ntfs
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

Already done.

---

### Post by sufslnd on 2008-10-11
UPDATE: My bios reports that it does not know the version of my prosessor, which perhaps could be because I took out and reinserted my BIOS battery a week ago (remove old forgotten password from BIOS). That should not have anything to do with it?

Anyone? I really need help on this one.

---

