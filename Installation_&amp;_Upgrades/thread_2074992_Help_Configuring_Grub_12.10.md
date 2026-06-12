---
title: "Help Configuring Grub 12.10"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by TurtleKing on 2012-10-22
I usually Dual boot with 2 separate Hard Drive tot have a backup just in case. Well apparently a clean install of Ubuntu 12.10 just happened to hit the exact thing. It seems the Ubuntu installer picked the Window 7 Hard Drive to install Grub, but sent everything else to the assigned hard-drive. 

So now I lost Grub on the Ubuntu Hard drive, and the Window 7 bootloader was replaced with Grub (the exact thing I wanted to avoid).

Is it possible to fix Grub within the Ubuntu Hard Drive? I am not very experienced with Grub, so I am hoping I can fix this without having to Boot into the Live USB. Not to mention, the Live USB is buggy (missing left docklet and panel).

---

### Post by darkod on 2012-10-23
Lets assume your windows disk is /dev/sda and the ubuntu disk /dev/sdb.

If you want to add grub2 to /dev/sdb, boot your ubuntu and simply do:
sudo grub-install /dev/sdb

That will add it on the MBR of the disk where you want it.

And in future, use the manual installation not the automatic ones. That gives you more control including where the bootloader goes. I think recently they developed the installer to put grub2 on the disk that is first in your bios to boot from, or something like that.
I guess they did that because with multiple disks many people install ubuntu and then it doesn't boot if grub2 is on the same disk as ubuntu and they have their windows disk as first to boot from.
The windows installer does the same, installs the bootloader on the first disk in the boot order.

You can add a generic MBR from ubuntu, but I prefer doing it from live mode so it doesn't leave any traces inside your ubuntu. But it can work from your installation too.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

When installing lilo ignore the message about the configuration, you won't be using it fully. That should add a generic MBR to /dev/sda which is the same as windows bootloader.

---

### Post by funicorn on 2012-10-23
```

[ -s /usr/lib/syslinux/mbr ] && sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda bs=440 count=1 conv=notrunc

```And I think it's OK.

---

### Post by Mark Phelps on 2012-10-24
> **TurtleKing said:**
> ... So now I lost Grub on the Ubuntu Hard drive, and the Window 7 bootloader was replaced with Grub (the exact thing I wanted to avoid).

Sorry to hear this, as this can be a difficult problem to fix.

In future, you should be sure to DISCONNECT the Win7 drive before you update Ubuntu.  I also have a multi-drive system, setup similar to yours, and learned this lesson myself the same way.

---

### Post by TurtleKing on 2012-10-25
Thanks darkod, I got the problem fixed following your instructions.

And I agree Mark, I had this happen before but it was so long ago I forgot to disconnect it (last time it happened was for 10.10).

---

