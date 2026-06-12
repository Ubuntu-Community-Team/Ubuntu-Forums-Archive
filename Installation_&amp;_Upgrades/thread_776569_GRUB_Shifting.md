---
title: "GRUB Shifting"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Sid1980 on 2008-04-30
I have Hardy Heron 8.04 installed on External USB hard drive and Windows on Internal HDD. After installation i find out that to load GRUB i must have USB HDD ON or otherwise i cant boot to Win or Either Ubuntu, 

Is there any possible way to shift GRUB to my internal HDD so i dont have to turn ON my External HDD just for booting Windows. :confused:

---

### Post by RATM_Owns on 2008-04-30
I don't know about shifting, but you can install GRUB on your internal through Live CD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Rallg on 2008-04-30
More likely than not, here is what happened:

When your computer boots, it read the master boot record (MBR) on your primary hard drive. The MBR points to where the bootloader can continue.

Originally, the MBR pointed to the Windows bootloader on your hard drive. When you installed Ubuntu (or nearly any Linux), you probably allowed it to install GRUB bootloader files on the new Ubuntu partition, and the MBR was changed to point to GRUB. From GRUB, you can continue to load Ubuntu, or be transferred back to the Windows bootloader on the Windows partition.

But if you installed Ubuntu (and GRUB) on removable media, you have a problem: The MBR points to GRUB on the removable media. It's not smart enough to realize that when the removable media is missing, it should go back to the original Windows bootloader.

You don't have to install GRUB on the same partition as Ubuntu. The link in the first reply gives you more details. If you keep GRUB on your primary hard drive, then you can still boot if the Ubuntu removable media is not attached.

You can even have several GRUB files here and there. But the MBR (or another boot option) will only point to one of them, and that's the one that will be used.

---

### Post by Sid1980 on 2008-04-30
> **Rallg said:**
> More likely than not, here is what happened:

When your computer boots, it read the master boot record (MBR) on your primary hard drive. The MBR points to where the bootloader can continue.

Originally, the MBR pointed to the Windows bootloader on your hard drive. When you installed Ubuntu (or nearly any Linux), you probably allowed it to install GRUB bootloader files on the new Ubuntu partition, and the MBR was changed to point to GRUB. From GRUB, you can continue to load Ubuntu, or be transferred back to the Windows bootloader on the Windows partition.

But if you installed Ubuntu (and GRUB) on removable media, you have a problem: The MBR points to GRUB on the removable media. It's not smart enough to realize that when the removable media is missing, it should go back to the original Windows bootloader.

You don't have to install GRUB on the same partition as Ubuntu. The link in the first reply gives you more details. If you keep GRUB on your primary hard drive, then you can still boot if the Ubuntu removable media is not attached.

You can even have several GRUB files here and there. But the MBR (or another boot option) will only point to one of them, and that's the one that will be used.

During installtion i chose HDD 0, dont know howcome GRUB installed in Removable Disk :( Is there any solution for this ??

---

### Post by confused57 on 2008-04-30
Grub's IPL(Initial Program Loader) wrote over your Window's IPL on the internal hard drive's mbr.  Grub's IPL looks for grub files needed to boot, which are located on the Ubuntu root partition on your external drive...therefore Windows won't boot when you don't have the external drive connected.

You'll first need to restore Window's IPL to your internal drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
if you don't have a Window's install disk, then Super Grub Disk can do this for you.

If your bios is capable of booting first to your usb external drive, use the live cd to install grub to the external drive's mbr:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
read the instructions, but it will be something like:
```
sudo grub
find /boot/grub/stage1
```
from the output of the above:
```
root (hd1,x)
setup (hd1)
quit
```
x means replace this with the output of "find /boot/grub/stage1"

You should then get a grub boot menu when you boot first to the external drive...but you'll need to highlight the first Ubuntu entry, press "e", highlight the root line, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot.  This is temporary if it works, but you can make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```

---

