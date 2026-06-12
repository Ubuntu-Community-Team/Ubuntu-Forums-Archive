---
title: "DMA-DVD-drive falls back to non-DMA mode"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by Markus72 on 2007-02-02
Hi,

I'm confused.
I have my second PATA port equipped with two DVD drives.
The first is a Plextor PX-716A burner and the second (slave) a pioneer DVD drive.

When I boot, hdparm shows both drives in DMA mode. So far so good.
All in all, the slave drive works fine and fast.

But - as soon a I access a DVD inserted into the Plextor, the DMA mode switches off.
That is why copying 4.7GB data from a DVD to the hard disk takes about 1 hour (

What is going wrong?

Any ideas?

Thanks
Markus

---

### Post by Markus72 on 2007-02-03
Here is what dmesg | grep hdc quotes

[17179572.044000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179573.740000] hdc: PLEXTOR DVDR PX-716A, ATAPI CD/DVD-ROM drive
[17179574.644000] hdc: ATAPI 94X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(66)
[17180580.436000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.436000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.580000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.580000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.580000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: DMA disabled
[17180580.580000] hdc: ide_intr: huh? expected NULL handler on exit
[17180580.628000] hdc: ATAPI reset complete

---

### Post by yannis on 2007-03-09
I get exactly the same error on my Plextor-750A when I try to boot Ubuntu 6.10 and SuSe 10.2 (both KDE and GNOME) Live DVD. I guess that Plextor's DVD mode is incompatible with some Linux distributions?
Although I can boot normally KNOPPIX 5.1 Live DVD!!

[17179573.740000] hdc: PLEXTOR DVDR PX-750A, ATAPI CD/DVD-ROM drive
[17179574.644000] hdc: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17180580.436000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.436000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.580000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.580000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17180580.580000] hdc: cdrom_decode_status: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[17180580.580000] hdc: DMA disabled

---

### Post by kuja on 2007-11-05
Old post thought this may be, I've also been having this problem for a lengthy amount of time also,however I think I may have found a plausible solution (that seems to works for me).

```
sudo hdparm -d1 -x34 /dev/hdx
```
Where hdx is the device in question.

---

