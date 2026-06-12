---
title: "Can't see hard disk"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by jeremija on 2010-10-26
Hello, I have a problem with seeing the partitions from a hard disk in ubuntu after installing updates. I installed the fresh 10.10 x64 desktop edition yesterday and I could've seen everything from the live CD. I think that it started to be missing after installing about 65 updates (those were the recommended updates).

In windows 7 everything is fine. I can see every partition like this:
[[IMG]http://img213.imageshack.us/img213/6572/partitions.th.png[/IMG]](http://img213.imageshack.us/i/partitions.png/)

Disk 0 and Disk 2 are basically the same (SATA) and Disk 1 is a rather old ATA drive, but in Ubuntu I can only see the partitions from the Disk 1 and 2. Ubuntu is installed to the 93.13 GB partition on Disk 2. Grub is installed to Disk 1 and it is the first boot device (not sure if this matters). The partitions from Disk 0 are not displayed on the Places menu bar.

After typing:
```
sudo fdisk -l
```

It only displays some info about Disk 1 and partition Storage and then hangs. The hdd led is lit constantly. It doesn't even display the info about the partitions on Disk 2, even though if I can browse those two partitions. And when I want to reboot, the ubuntu logo displays but it hangs there and I think that this is due to this problem with the hdd recognition.

Help me, I'm desperate - this is a fresh install with only the recommended updates installed!

---

### Post by jeremija on 2010-10-26
well this is weird. after i booted to linux back to windows the all partitions are there and there are no hangs. what could be the cause of these hangs?

i will try to remember what i did if this happens again.

---

### Post by jeremija on 2010-10-26
I have had the same problem again. I THINK that this has something to do with the GRUB timeout. 

When the GRUB loads and I press the enter key instantly - the whole OS loads very fast and the problem with not detecting the partitions happens.

When I let GRUB to automatically load Ubuntu after 10s timeout, everything works fine.

Could this be the reason? If so, how can I fix this so that I don't have to wait the 10s.

**EDIT: after installing the proprietary driver for the nVidia gt9800 graphic card the ubuntu did not boot to the gnome interface. I got a strange message in the CLI:**
[[IMG]http://img641.imageshack.us/img641/5696/20101026141.th.jpg[/IMG]](http://img641.imageshack.us/i/20101026141.jpg/)

Also when i log in and type startx -> the partitions from Disk 0 are not visible in the menu and the hdd led is lit.

**EDIT2: after removing the proprietary nvidia driver, everything works as described above - wait for 10s for GRUB to auto load Ubuntu, and the disks can be seen**


**EDIT3: after disconnecting the problematic disk drive from the pc, everything works fine (with or without the propritary driver)**
But I don't understand it. I tried to connect it to the different SATA port on MBO - same thing.

Sometimes it gets recognized normally, and most of the time it doesn't. When it doesn't get recognized - the hdd light is always on. 

I could understand that this is because the problematic disk is faulty, but how come it works with absolutely no problems on Windows 7??

---

