---
title: "Windows won't boot and I'm at my wits' end"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by AndyC_772 on 2005-10-22
My laptop originally had a 40GB disc, partitioned into two:

1) Dell Utility, 45MB, FAT32 - usually hidden and, as far as I can tell, a complete waste of space;
2) Windows XP, nearly 40GB, NTFS - my bootable XP partition containing the OS and all my data.

The disc was getting full so I decided to get a new 80GB disc and partition it as follows:

1) Windows XP, 40GB, NTFS - an exact clone of my original XP partition
2) Shared files, 7.5GB, FAT32 - shared area readable and writable from both XP and Linux
3) Swap partition, 2GB
4) Ubuntu, 25GB, ext3 - my new Ubuntu OS and data

I've used dd to clone my old Windows partition onto the new disc, and I have GRUB installed. I can boot into Ubuntu with no problems, and I can mount both the NTFS and FAT32 partitions and all my data is there. However, for some reason, selecting Windows from the GRUB menu fails to actually boot the Windows OS.

The interesting bit of my /boot/grub/menu.lst file is:

```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin  
boot

title		Microsoft Windows
rootnoverify	(hd0,0)
makeactive
chainloader	+1

```

I've modified the partition number from (2) to (1) in my windows BOOT.INI, which now reads:

```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


```

The BOOT flag is set on /dev/hda1, ie. the XP partition. and no others.

My BIOS doesn't include the option to force LBA on a disc, and in any case my old drive worked just fine. I'm now totally at a loss as to why Windows won't boot. All my data is there, there's just something broken in the boot process for Windows.

When I select Windows from the GRUB menu, the screen shows the three lines:

```
rootnoverify	(hd0,0)
makeactive
chainloader	+1
```

...and at that point, the PC just stops, and I have to reset.

Could anyone please suggest what it might be? :confused:

---

### Post by paddyg on 2005-10-22
Probably when you cloned the Windows partition you didn't "clone" the bootloader.
When grub calls it, the Windows loader isn't there to answer.

---

### Post by oxiw on 2005-10-22
also think that you must install first windows on disk, and then from my exp. linux, or maybe exist something to creat bootloader without installing and then copy data, but ....
 I am shure, that windows disc partition must be first on hda to boot, without, it can't boot. grub will automatically read this and set it up in menu.lst

---

### Post by AndyC_772 on 2005-10-22
OK, so theoretically maybe I could clone the whole of the original drive onto the new one, then create the FAT32, swap and EXT3 partitions, then reinstall Ubuntu - but that seems rather drastic if all that's missing is the Windows boot loader.

Where does it normally reside, and how might I reinstall it or copy it across from the old disc?

---

### Post by paddyg on 2005-10-22
When you install Windows it installs its loader to the very first part of the disk (MBR), and as far as i know you can't normally access it.

You should ask some Windows guru for some special program to access that disk sector.

If you back up all your data, and then decide to install windows again, please remember that the win loader will overwrite grub, and you'll not be able to get to your ubuntu partition. So, ubuntu must be installed again.

---

### Post by oxiw on 2005-10-22
If you have all data on your old disc, not loosing anything so, bootloader is the most important think, and if you want to use also winxp, must be there, cloning depends on platform, for xp there is [http://www.pcstats.com/articleview.cfm?articleID=418]("http://www.pcstats.com/articleview.cfm?articleID=418") dont forget to put it on first partition, and then linux / , swap and share. seems to me the most nonproblematic, share should be also ntfs, if you kompile kernel with ntfs write feature, you will have to mount it through /media by edit etc/fstab

---

### Post by estel on 2005-10-22
You're missing the line
```
boot
```
Beneath the Windows bit of menu.lst

---

### Post by Sirin on 2005-10-22
[QUOTE=estel]You're missing the line
```
boot
```
Beneath the Windows bit of menu.lst[/QUOTE]

No boot tag means no go, my friend. ;)

---

### Post by estel on 2005-10-22
Hmmm
Made that post in haste, sorry.

Was annoyed at my own GRUB problems (i.e. it acted as if it wasn't there and booted straight to Windoze). Sorted with RESCUE :D

Sorry ;)

---

### Post by paddyg on 2005-10-23
No boot line in menu.lst is necessary to boot windows.
I don't have it and grub boots it wonderfully all the same.

i think the problem is cloning isn't the right way to make a disk bootable.

---

