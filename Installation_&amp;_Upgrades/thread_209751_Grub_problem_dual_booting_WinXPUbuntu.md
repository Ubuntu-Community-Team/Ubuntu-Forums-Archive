---
title: "Grub problem dual booting WinXP/Ubuntu"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Akula on 2006-07-05
My problem is this: Every time I boot my computer without any boot cds or floppies, I get Grub menu, where I can choose OS to start (windows XP and Ubuntu).

When I try to start OS with this menu, I get an error message. This is what I get when I try to start Windows:

```

Booting 'Microsoft Windows XP Home Edition'
root (hd1,0)
  Filesystem type is ext2fs, partition type 0x83
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue . . .
```

After this I'm back in Grub menu and I get this kind of error every time I choose any option of the menu.

I happen to have Grub boot disk, and when I boot my computer using it, I can get to similar Grub menu by typing: "configfile (hd0,0)/boot/grub/menu.lst" and this menu is working (I can boot to WinXP or Ubuntu).

I have tried to get rid of the Grub menu on my disk by "fixmbr" command in repair mode of Windows XP Home Edition install cd, but had no effect.

I have 2 Hard Drives:

SATA HD 120GB - Master - Contains WindowsXP partition
PATA HD 80GB - Slave - Contains Ubuntu partitions, and Ext3 partition for files used both WinXP and Ubuntu.

I have some kind of idea that these hd0,0/hd1,0 kind of settings are not understood 'correctly' by Grub bootdisk, as I understand that hd0 should be master. Anyway I can see my master hd in ubuntu as /dev/sda and slave hd as /dev/hdb. Could this result that /dev/hdb -> hd0, I don't know.

Here's my previous post about situation I had before and from where I have advanced a bit: [http://www.ubuntuforums.org/showthread.php?t=209077](http://www.ubuntuforums.org/showthread.php?t=209077)

Any kind of help is welcome.

---

### Post by ajgreeny on 2006-07-05
What is your /boot/grub/menu.lst entry for windows?  It should look something like this:-

title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

I'm a bit confused about the grub messages appearing to load a ext2 filesystem when windows will always be either fat32 or more likely NTFS nowadays.

What does the grub message read when you use the floppy, what is different from the 

Booting 'Microsoft Windows XP Home Edition'
root (hd1,0)
  Filesystem type is ext2fs, partition type 0x83
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

that you see from a hard disk boot?

---

### Post by Akula on 2006-07-05
menu.lst entry for windows:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

and for ubuntu:

```
title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot
```

I can't quite see what it gives when I use windows option when bootig from floppy, they disappear so quickly. But using 'e' at windows option in menu, shows very similar lines as above (I't think they are same thing).

---

### Post by yabbadabbadont on 2006-07-05
Just out of curiostity, what does "sudo fdisk -l" show?

---

### Post by Akula on 2006-07-06
'sudo fdisk -l' gives following:

```
Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = 1008 * 512 = 516096 -byte cylinders

    Device Booting  Start   End        Blocks          Id    System
/dev/hdb1   *           1       35369    17825944+  83  Linux
/dev/hdb2           35370       39530     2097144   82  Linux / Solaris
swapfile
/dev/hdb3           39541      158802    60107197+  83  Linux
End of Partition 3 is not on border of cylinder.

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = 16065 * 512 = 8225280 -byte cylinderst

     Device Booting  Start   End        Blocks          Id    System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       14946    89337465    f  W95 Laaj (LBA)
/dev/sda5            3825       14946    89337433+   7  HPFS/NTFS
```

this is translation from finnish so some words may sound odd...
straight translation for that swapfile i've used there would have been 'throwshiftfile'.

---

### Post by Akula on 2006-07-06
Could there be any way to uninstall grub of the windows disk so that computer boots straight to windows, but I could still use the Grub boot disk to boot in linux? Then perhaps I could set the Grub again perhaps?

---

### Post by yabbadabbadont on 2006-07-06
Since grub is having to play the, "let's pretend that windows is on the first disk", game (that is what the map commands are trying to do), I would guess that you installed grub into the MBR of /dev/hdb.  If so, and your BIOS can boot directly from the SATA (or SCSI) drive that contains windows, then you should be able to do what you want.  Just set the bios to always boot the windows drive first, then use a grub boot disk (floppy, CD, whatever) when you want to boot into Ubuntu.

---

### Post by Akula on 2006-07-07
Ok, thanks. I'll have to try that too.

Before I installed ubuntu, there was windows on SATA disk and it worked fine. When Ubuntu, after install, did not boot at all (booted only to windows, normal way) I made grub boot disk, and used 'find /boot/grub/stage1' command to find out the Ubuntu drive, and it was found on hd0. So I installed the grub on hd1. This could be where I did wrong... I'm not sure.

And then one thing: I noted those boot flags on first partitions on BOTH hard drives (Windows XP partition and Ubuntu Ext3 partition). Is it normal?

---

### Post by yabbadabbadont on 2006-07-07
There can only be one partition marked bootable *per disk*, since that is what you have, it should be fine.

---

### Post by Akula on 2006-07-08
Hmm, I think I have found the source of the problem now, but I don't know how to fix it.

"cat /boot/grub/device.map" gives following:
```

(hd0)   /dev/hdb
(hd1)   /dev/sda

```
hd0 is my linux HD (set to slave, PATA)
hd1 is my windows HD (master, SATA)

When I boot to windows (possible only from grub boot disk (and from there using configfile on menu.lst)), I suppose /dev/sda disk would then be kind of hd0? Have I installed Grub on my slave disk, as when I boot my computer without boot disk, I get to grub menu, but none of the options work.

Should I install grub of grub boot disk to hd0 (which is seen as linux disk) and it would somehow 'magically' be set actually on windows HD (which is now hd1)  ?

---

### Post by yabbadabbadont on 2006-07-08
That device map is showing that the bios is currently set to boot the PATA slave drive before the SATA primary.  See if you can change that in the bios settings.

---

### Post by Akula on 2006-07-08
I looked at my bios settings and I think it boots from SATA disk. I could not find way to change their booting order except making other master and other slave from jumpers on HDs. I booted from HD (SATA), and got grub menu.

When I try to launch Ubuntu, it tells that: 
*Root = hd0
*Filesystem = unknown
*Partition type = 0x7
Then I get an error and gives me the menu again. 

If I try to launch Windows, it tells:
*Root = hd1
*Filesystem = Ext2fs
*partition type = 0x83
I get error here also.

I understand that 0x83 is linux partition and 0x7 (NTFS?) is not.

When I boot from grub bootdisk and use 'find /boot/grub/menu.lst', I get (hd0). So hd0 and hd1 seem to have changed places, so that the menu works when I type 'configfile (hd0,0)/boot/grub/menu.lst'. 

I think I just need to set grub to MBR in way where hd0 and hd1 change places, what do you think? and how do I change this? Do I just make the changes to /boot/grub/menu.lst?

---

### Post by Akula on 2006-07-09
Finally I just found guts to edit menu.lst:

1. I switched Ubuntu root from (hd0,0) -> (hd1,0) and Windows root from (hd1,0) -> (hd0,0)
3. removed 2 map lines from windows option

And then booted. So now it works without grub boot disk!

In addition I added some lines to menu.lst in case I have to boot using grub boot disk (new menuoptions do not work with boot disk, since with disk HDs switch places). For this I added the original menu options to the bottom with different title names.

Thanks for showing some directions!

And now to the next problem... =)

---

