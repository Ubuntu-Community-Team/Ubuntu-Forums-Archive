---
title: "GRUB fails to find XP"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by w4uoa on 2008-04-16
My desktop machine has 4 hard drives.  The boot drive runs XP.  I installed ubuntu 7.1 using the Live iso on one of the remaining drives.

If I select the Windows XP option from the grub menu.lst, I get NTLDR not found. 

If I tell the BIOS which drive to boot from, I can boot XP.  If I point the BIOS to boot from the ubuntu drive, I see grub's menu.lst and can select any of the ubuntu choices and boot ubuntu just fine.   

I've read many of the other posts on this issue but have not found one that seems to apply.  Note that I can successfully boot XP or ubuntu my pointing the bios to the correct drive.  But when I try to get grub to chain to ntldr it fails.  

When I use Places->Computer to look at the drives, I see the XP boot drive and can not absolutely confirm "x" where for hdx or sdx.  

I suspect the solution will involve using grub's MAP command but all attempts so far have failed and I really hate to try to keep guess about the proper solution.

Thanks for any help you can provide.

---

### Post by dstew on 2008-04-16
Boot your Ubuntu system and open a terminal (Applications --> Accessories --> Terminal). On the command line enter these commands```
sudo fdisk -l
cat /boot/grub/menu.lst
```Post the result to the forum.

---

### Post by w4uoa on 2008-04-16
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6f0684e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb174b174

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x854b6ae7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161   42  SFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff95a72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641    7  HPFS/NTFS

/boot/grub/menu.lst

# This entry added by Ferguson 4-16-2008
title Microsoft Windows XP Professional (Added by Ferguson 4-16-2008)
map (hd0) (hd1)
map (hd1) (hd0)
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by dstew on 2008-04-16
Your root statement in the Windows entry should be root (hd1,0). The map statements are OK.

---

### Post by w4uoa on 2008-04-16
No joy.  The same error.  The screen reads...

Starting up...

NTLDR is missing
Press Ctrl+Alt+Del to restart

If I go into the BIOS and make the XP drive the first boot drive, XP boots fine, so I assume the NTLDR is there and functional.

If I make the ubuntu drive the first boot drive, is see Grub's menu.lst and as indicated, all the choices except XP work fine.

Thanks for working with me....  Next?

---

### Post by dstew on 2008-04-16
I don't think it matters, but maybe try to put the root statement first:```
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```You're sure the bootable Windows partition is /dev/sdb1, right? And not /dev/sdd1...

---

### Post by w4uoa on 2008-04-16
Moving

```
root (hd1,0)
```

to the top still fails.

---

### Post by dstew on 2008-04-16
Are you sure that /dev/sdb1 is your Windows bootable partition? You might also try to boot /dev/sdd1:```
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
savedefault
makeactive
chainloader +1
```
Another thought: perhaps when you change the BIOS boot order, the enumeration of the disks also changes. That could effect the device names for grub. Please post your /boot/grub/device.map file. That will show what grub thought the mapping should be when it was installed.
One more thought: I notice you have an encrypted drive (SFS). Does your BIOS have the capacity to boot that drive? I see the boot flag is on.

---

### Post by w4uoa on 2008-04-16
carl@W4UOA-ubuntu:~$ cat /boot/grub/device.map
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
```

carl@W4UOA-ubuntu:~$ sudo fdisk -l

```

**This is clearly the ubuntu drive:**

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6f0684e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris
[B]
I THINK this is the XP drive[/B]s

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb174b174

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

**I THINK this is the PICTURES drive**

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x854b6ae7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161   42  SFS

**Because of its size, I know this is the BACKUPS drive**

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff95a72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641    7  HPFS/NTFS

```

This would lead me to believe that XP is on either sdb or sdc--hd1 or hd2.  I'm confident it is NOT on hd0 or hd3.

From the Desktop menu, **Places>Computer** shows each of the drives by drive name but I can not find a way to "map" that information back to sda, sdb, sdc, sdd.

Thanks again for hanging in there with me.

---

### Post by w4uoa on 2008-04-16
Well...XP is on hd3.  Go figure.  I DO NOT understand that give what I see when I run fdisk.  But...with hd3 specified, it works.

Thank you very much.  

You can show this case solved!

How do we mark it solved?

---

### Post by zvacet on 2008-04-17
> How do we mark it solved?

**Thread tools>mark as solved**

---

