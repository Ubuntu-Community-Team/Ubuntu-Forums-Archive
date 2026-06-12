---
title: "Grub: Error 17  Cannot mount selected partition"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by mandi1989 on 2011-04-19
Hey, first post here, I've tried everything to solve this, been browsing  the forums for the last 2 days and no solution has worked.

So I got a new netbook (Samsung n150 dated 03/2011) it had ubuntu 10.10  installed but I already use ubuntu on my macbook
so I'm trying out  knoppix, I booted it from usb and ran the HD installer, it gets  through all that and then installs grub ok, but when I reboot I get  "Error 17: Cannot mount selected partition"

Things I already tried:
*Grub setup (grub, root (hd0,1), setup (hd0), quit) and every variation.
*I tried removing the usb and setting the HDD back to first boot in the bios and
then changing the menu.lst accordingly, still I get error 17.

Below is the information just after boot with the usb still plugged in and set as first boot in bios.

fdisk -l
```

[COLOR=Red]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
  
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052257   82  Linux swap / Solaris
/dev/sda2   *         132       30401   243143775   83  Linux
  
  [COLOR=Lime]Disk /dev/sdb: 2062 MB, 2062024704 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x285b5c9e
    
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         250     2008093+   c  W95 FAT32 (LBA)[/COLOR][/COLOR]
```[COLOR=Red]Red[/COLOR] = HDD
[COLOR=Lime]Green[/COLOR] = USB

menu.lst from  /media/sda2/boot/grub

```
default 0
timeout 30
color cyan/blue white/blue

title Knoppix
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda2 rootwait lang=us apm=power-off nomce libata.force=noncq tz=localtime loglevel=1  rw
```(The above menu.lst gets error 15 cannot find file until I unplug the usb and change to (hd0) to boot from HDD)

Please help me, really want to get this working. Thanks in advance.

--Mandi

---

### Post by alterpinguin on 2011-04-19
the file "menu.lst"
is for the old grub-boot-loader.
Not for the newer grub-2
that comes with ubuntu-10.04, ubuntu-10.10 etc.
-
I know old knoppix versions using syslinux for boot
and grub (thats grub-1, the old version with menu.lst
as boot-menu-file)
-
You should get a grub-super-boot-rescue CD(usb) to boot with
and try to fix it or only boot the installed system
with it and then do the grub-install out of this running
system.
-
use google to search for: grup super boot
and read the docs, because you have to enter the boot-commands
for your sda2-linux-system by hand.
-
you may, get the same with the installed version if you can
edit the menu-entry -- and i am not quite shure,
but it might be that with the usb-harddisk the numbering is 
one off - thats at boot-time with usb-harddisk as boot-device
it inserts this hd as number 0

---

### Post by mandi1989 on 2011-04-19
Thanks for the reply, landed on [http://www.bootproblems.com/](http://www.bootproblems.com/) which distro do I need to get?
[COLOR=Red]
EDIT[/COLOR]: Got the second one, that sees knoppix but then while loading gets "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

---

### Post by oldfred on 2011-04-21
If you want to know where everything is installed: Works from Ubuntu liveCD, should work from Knoppix liveCD also.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

