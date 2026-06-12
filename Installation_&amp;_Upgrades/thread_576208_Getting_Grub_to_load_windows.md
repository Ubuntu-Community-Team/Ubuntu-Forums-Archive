---
title: "Getting Grub to load windows"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by captncraig on 2007-10-15
I just installed Ubuntu, and the grub loader is having a problem finding the windows xp partition.

here's my drive configuration:

> sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       19451   156240126    f  W95 Ext'd (LBA)
/dev/sda5            5100       19451   115282408+   7  HPFS/NTFS
/dev/sda6               1         243     1951803   82  Linux swap / Solaris
/dev/sda7             244        5099    39005788+  83  Linux

Partition table entries are not in disk order


and here's the relevant grub stuff:

> title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1097c3dc-59bd-43d0-ba04-3bfe3c23f7f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Windows XP
root (hd0,5)
makeactive
chainloader +1 
### END DEBIAN AUTOMAGIC KERNELS LIST

I added in that last entry, but I'm not exactly sure how to make it work. It keeps giving me invalid partition or similar errors on restart when I try to select windows. Please help me.

---

### Post by PacketCollision on 2007-10-15
Linux starts numbering partitions at 1, GRUB starts at 0.  So sda5 is (hd0,4) , not (hd0,5) in GRUB.

---

### Post by captncraig on 2007-10-15
Even when I try using (hda0,4)
grub says invalid device or something along those lines.

The super grub disk can find a windows installation, but when it tries to boot it freezes at boot:

Is my windows installation toast at this point? Or is there anything else I should try

---

### Post by logos34 on 2007-10-15
> **captncraig said:**
> Even when I try using (hd**[COLOR="Red"]a[/COLOR]**0,4)
grub says invalid device or something along those lines.

typo -- should be (hd0,4).

Not sure even that will work though, since even super grub can't boot it. (you've got windows on a logical partition). 

What happened to sda1?

---

### Post by PacketCollision on 2007-10-15
Yeah, I've never heard of Windows being able to boot from a logical partition.  What it can probably do is boot the bootloader stored on a primary partition and then get the rest of the Windows files off of the logical.

Is there a windows primary partition at sda1?  If so, try using it to boot.

If that doesn't work, you might have to boot with the Windows install CD, go to the repair console, type fixmbr, type fixboot, then use the NT bootloader to load linux instead of the other way 'round.  There is documentation about how to do that floating around, but I've only done it once, and it's hardly a beginner-friendly task.

---

