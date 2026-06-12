---
title: "Installing Ubuntu on 3rd hdd"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by KrakHT on 2007-04-08
I've got two hard drives, both 300gb and running windows xp with nvidia raid1 (mirror).

I just got a 160gb hard drive. I put in the 160gb hard drive, and formatted it. I don't want to use the full 160bg for Ubuntu if i can get away with it. I parted it out 12 for root, 12 for home and 4 for the swap. Installed Ubuntu, and then rebooted. Grub returns error 22. Tried changing the boot order of my drives to see if I could get into one of the OSes, no. So I used the Windows recovery console, did a fixmbr.

Now if I boot with the 3rd drive first, then the raid, windows gets to loading screen flashes a quick bsod and reboots. If i load raid then the 3rd hdd I get a cant load an os error message. If i remove the 3rd hard drive and reboot, windows boots just fine.

How can I get my computer to boot with raid first, then the other hdd (like it did the first time around).

and

How can I install ubuntu on those three partitions on the 3rd hdd?

I want to have ubuntu installed on those partitions on the 3rd hdd (non raid), and dual boot with windows (windows is on the raid hdds).

Would it just be easier to use the entire 3rd hdd for ubuntu?

Or, at a bare minimum get the drives to boot raid, then the sata, and ill just use the whole thing as extra ntfs partitions.

---

### Post by confused57 on 2007-04-08
You might be able to install grub to the drive's mbr that you have Ubuntu installed on, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Before doing the above method, set your hard drive boot order as you had it when you installed Ubuntu, then following the link above you would do something similar to this:
```
sudo grub
find /boot/grub/stage1
```
this should something like
root (hdx,y)
you would then enter:
```
root (hdx,y)
setup (hdx)
quit
```

Then try booting first to the drive with Ubuntu, IF you get a grub menu, highlight the Ubuntu entry, press "e", then change root  from (hdx,y) to (hd0,y), then press "b" to boot...this is temporary if it works, but can be made permanent.

---

