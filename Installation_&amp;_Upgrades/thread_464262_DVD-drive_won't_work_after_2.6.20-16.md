---
title: "DVD-drive won't work after 2.6.20-16"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by ::: on 2007-06-04
Hi,

after updating to the new Kernel, my dvd-Drive doesn't work anymore.

The drive seems to be /dev/hdb now (although my fstab still says /dev/scd0 - which doesn't exist anymore) - at least thats what Gnome Hardware Information tells me.

So I changed my fstab to say /dev/hdb0 instead of /dev/scd0.

I now have two optical drives displayed in Nautilus (see attached screenshot) - the first two in the screenshots. (All the other icons refer to actual Partitions of my harddrive)

When I insert a CD-RW System gets really slow, and when I switch to Console (Ctrl+Alt+F1) It prints out weird stuff like

""hdb: ide_intr: huh? expected NULL handler on exit"
und
"Buffer I/O error on device hdb logical block 17" 

When I insert a (pressed) CD, it is identified as an audio-cd (even so it really is a data cd) and starts sound juicer when I click on it in Nautilus.


Can anyone help?

PS: It still works with the old Kernel. But I don't want to go back, because the new kernel fixes some other hardware issues I had.

---

### Post by merlinus on 2007-06-04
Try commenting out all the other lines referring to your cd drive

and adding

/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

Good luck!

-merlin

---

### Post by awaldram on 2007-06-04
just rem the lot out in fstab (cd entries) ...Hal will mount it just fine.

---

### Post by ::: on 2007-06-06
Thank you both for your replies!

Sadly, the behavior stays the same - regardless of what I enter into the fstab. I tried both, /dev/hdb and nothing at all. The second Drive in Nautilus did actualy disappear, but the CDs are still not properly read.

Heres some output from dmesg:
```

[ 1277.624000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1277.624000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1277.624000] ide: failed opcode was: unknown
[ 1286.844000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1286.844000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1286.844000] ide: failed opcode was: unknown
[ 1296.284000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1296.284000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1296.284000] ide: failed opcode was: unknown
[ 1305.680000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1305.680000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1305.680000] ide: failed opcode was: unknown
[ 1305.680000] hdb: DMA disabled
[ 1305.680000] hdb: ide_intr: huh? expected NULL handler on exit
[ 1305.728000] hdb: ATAPI reset complete
[ 1315.016000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1315.016000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1315.016000] ide: failed opcode was: unknown
[ 1324.556000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1324.556000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1324.556000] ide: failed opcode was: unknown
[ 1333.820000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[ 1333.820000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[ 1333.820000] ide: failed opcode was: unknown
[ 1333.820000] hdb: ide_intr: huh? expected NULL handler on exit
[ 1333.868000] hdb: ATAPI reset complete

```

And when I double-click the drive in Nautilus, it says "Unable to mount media. There is probably no media in the drive."

Additionaly, when I try to eject the disk, I sometimes get a message, saying the disk cannot be ejected.

Any other Ideas?

---

