---
title: "Dual Booting vista and ubuntu"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by bwoogie on 2007-05-06
Ok, I just installed ubuntu on my computer than is already running vista.
Vista is on my primary hard drive ide cable and ubuntu is on my secondary ide cable.
It installed fine, and when it booted up grub, I was surprised to see that it found vista! First I booted up ubuntu and it works fine! So then I restarted the computer to see if vista is still working. When I select it from the list vista starts to load, I get the progress bar screen... then the screen turns black and nothing happens. I let it sit there for a while but it just locks up , i cant even flash the num/cap lock lights on my keyboard or press ctrl alt del, i have to do a hard reset.
Has anyone had this problem, or know how to fix it?

---

### Post by confused57 on 2007-05-06
> **bwoogie said:**
> Ok, I just installed ubuntu on my computer than is already running vista.
Vista is on my primary hard drive ide cable and ubuntu is on my secondary ide cable.
It installed fine, and when it booted up grub, I was surprised to see that it found vista! First I booted up ubuntu and it works fine! So then I restarted the computer to see if vista is still working. When I select it from the list vista starts to load, I get the progress bar screen... then the screen turns black and nothing happens. I let it sit there for a while but it just locks up , i cant even flash the num/cap lock lights on my keyboard or press ctrl alt del, i have to do a hard reset.
Has anyone had this problem, or know how to fix it?
You might want to open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"
and
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list
and
```
gedit /boot/grub/device.map
```

---

### Post by bwoogie on 2007-05-06
fdisk -l
> Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4864    39070048+   7  HPFS/NTFS
/dev/hdb2   *        4865        9527    37455547+  83  Linux
/dev/hdb3            9528        9729     1622565    5  Extended
/dev/hdb5            9528        9729     1622533+  82  Linux swap / Solaris


menu.lst
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

device.map:
> (hd0)	/dev/hda
(hd1)	/dev/hdb

i'm pretty sure all this is set correctly, because windows starts to boot.. i'm thinking im just gonna have to do a "repair" install of vista.

---

### Post by bwoogie on 2007-05-06
bump

---

### Post by hal8000 on 2007-05-06
Just reading your post, I have an idea what might be happening. When booting into Ubuntu, try shutting down not rebooting.

If you power on again now, does Vista load ok?

I had this problem once on a Dell laptop dual booting win xp / suse linux. If I rebooted, windows would never load, the only way round was to switch off, this may be your problem also, and I think that it has to do with the different refresh rates the graphics card sends to the display. This does not affect every chipset/monitor however, so may not necessarily be your problem.

---

### Post by confused57 on 2007-05-06
I'm assuming your Ubuntu root is (hd1,1) in your menu.lst.  You could try "rootnoverify (hd0,0)" instead of just "root (hd0,0)" in your Window's entry, if what hal8000 suggested doesn't work.

---

