---
title: "GRUB Error 2?"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by mastaphoo on 2007-06-14
I installed 7.04 originally on my 160GB HD and it worked fine (the boot HD was my 80GB with WinXP) but I tried to install nvidia drivers for my 8800GTS (640) and I got the X server failed to start error and was stuck with the terminal (>.<). After trying to reinstall, I got to the GRUB loader and it said this:

GRUB loading stage 1.5.....

GRUB loading, please wait....
Error 2

.... and now I can't get to XP or 7.04. I'm typing this on the live CD, which still works. I tried reinstalling (again) and the same thing happened. My old Ubuntu 5.10 Live CD doesn't work at all, and I'm a complete newb in the terminal. Right now all I want is the GRUB loader off of the 80GB HD so I can start over, but I don't think I can just wipe the 160GB (with apparently corrupt 7.04). Can I just wipe the 160 and start over? Or should I get another 7.04 disc (maybe this one is corrupt?) and try reinstalling again? Or is there some way I can get around the GRUB loader to get on XP to re-burn the 7.04 disc? Sorry, way to many questions. What should I do?

Thanks!

---

### Post by avik on 2007-06-14
Can access the hard drive with Ubuntu on it from the Live CD?  If so, can you post the bottom portion of the file /boot/grub/menu.lst from that hard drive?

Error 2 means that the referenced disk doesn't exist, which makes me think that it may be a malformed grub menu file.

---

### Post by mastaphoo on 2007-06-14
I'm not sure if this is what you want, (tell me if it isn't) but here's the bottom of the menu.lst file. I copied from the last commented out line down to the bottom:


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d046f95f-1e24-4b0d-80de-894dc0738689 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d046f95f-1e24-4b0d-80de-894dc0738689 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



Hope this helps.

---

### Post by confused57 on 2007-06-14
> **mastaphoo said:**
> I installed 7.04 originally on my 160GB HD and it worked fine (the boot HD was my 80GB with WinXP) but I tried to install nvidia drivers for my 8800GTS (640) and I got the X server failed to start error and was stuck with the terminal (>.<). After trying to reinstall, I got to the GRUB loader and it said this:

GRUB loading stage 1.5.....

GRUB loading, please wait....
Error 2

.... and now I can't get to XP or 7.04. I'm typing this on the live CD, which still works. I tried reinstalling (again) and the same thing happened. My old Ubuntu 5.10 Live CD doesn't work at all, and I'm a complete newb in the terminal. Right now all I want is the GRUB loader off of the 80GB HD so I can start over, but I don't think I can just wipe the 160GB (with apparently corrupt 7.04). Can I just wipe the 160 and start over? Or should I get another 7.04 disc (maybe this one is corrupt?) and try reinstalling again? Or is there some way I can get around the GRUB loader to get on XP to re-burn the 7.04 disc? Sorry, way to many questions. What should I do?

Thanks!
Here are several methods to restore Window's IPL to your Windows drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If your bios is capable of booting first to your Ubuntu drive, try installing grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the method described in the link...to install grub's IPL to the Ubuntu drive's mbr:
```
root (hd1,y)
setup (hd1)
```

if you want to try reinstalling grub to the Windows drive's mbr(even before you try restoring Window's IPL):
```
root (hd1,y)
setup (hd0)
```

If you do install grub to your Ubuntu drive's mbr and can boot to it first...if you get a grub boot menu, highlight your Ubuntu entry, press "e" to edit, then change root from (hd1,y) to (hd0,y), then press "b" to boot...this change is temporary, but can be made permanent if it works.

Added:  Just saw your last post, looks like you're already booting first to your Ubuntu drive...have you tried changing bios to boot first to your Window's drive?

---

### Post by mastaphoo on 2007-06-14
Thanks guys, I'm trying the WinXP MBR restoration now. Hope this works, if it doesn't I'll be back.

EDIT: To what you added (confused57) I have to set the BIOS to boot from the 80GB which has WinXP installed to get the GRUB loader to work correctly. From there, I have the choice of Ubuntu or XP. I'll try booting right to the drive with Ubuntu on it.

---

### Post by confused57 on 2007-06-14
If you're not able to boot your Ubuntu drive, boot the live cd & post results of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by mastaphoo on 2007-06-14
Tried booting from the 160 through the BIOS, same exact result (error 2). Can't find my WinXP CD to do an MBR restore, but heres the result of that code:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS


Hope you get more out of this than I do :P. Just to explain my setup, I have an 80GB SATA that has WinXP on it, a 200GB IDE that is NTFS (extra windows stuff) and a 160GB IDE (Ubuntu, hopefully). Hope that helps!

---

### Post by confused57 on 2007-06-15
I'm at a loss as to what is going on with your system, but I can offer something you might try, if you don't mind reinstalling Ubuntu.
Set your hard drive boot order to 160 Gb IDE to be booted first, then your SATA with Windows  2nd, then your 200 Gb IDE 3rd...if you're not able to set your SATA drive to boot before your 200 Gb IDE, it would be OK to set the 200 Gb 2nd & the SATA 80 Gb 3rd.  Do this before you boot the live cd to install Ubuntu.

If you had access to another computer, you could download & make a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is a great utility for booting problems, both Windows & Ubuntu...it can boot either or restore Windows or Ubuntu IPL to the mbr.

I'll let you know if I can come up with anything else for you to try...or maybe someone else may have a suggestion...good luck.

---

### Post by mastaphoo on 2007-06-15
In a day or so I will have access to another computer and I'll try the SGD. I'll try switching the order of the drives, and I can make it 160, 80, 200. I think I know what you're trying to do there, and I hope it works. I'll post updates, and thanks a ton man!

---

### Post by mastaphoo on 2007-06-15
Ok, now I tried changing the boot order and reinstalling. No luck. I'm downloading the Super Grub Disk and burning it right now. It sounds like a great tool to have around, and I'm guessing it will work fine and I'll be back in business. Thanks a ton for the help, I'll edit this post with an update when I'm back on WinXP (or Ubuntu I guess).

---

