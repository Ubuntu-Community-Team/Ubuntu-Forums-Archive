---
title: "dd'ing the Ubuntu .iso image creates two partitions on USB startup disk"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by pveurshout on 2014-12-31
I downloaded the Ubuntu 14.04.1 .iso image and used dd to 'burn' it to a USB flash drive (which I'll refer to as [FONT=Courier New]sdX[/FONT]).

```
dd  if=/path/to/ubuntu-14.04.1-desktop-amd64.iso  of=/dev/sdX
```

Afterwards, I noticed that this had created two partitions on the flash drive: [FONT=Courier New]sdX1[/FONT] and [FONT=Courier New]sdX2[/FONT]. [FONT=Courier New]sdX1[/FONT] is mountable and contains the files that the iso image contains. I wanted to know what sdX2 was for, and found a possible explanation for this in the Community Help Wiki:

[QUOTE=https://help.ubuntu.com/community/Installation/FromUSBStick]2. There may be a bug during the formatting which will cause two partitions to appear when booting from the USB flash drive. Try selecting each of them and one should work. If not, restart the computer and try booting from the USB flash drive again. [/QUOTE]

But this didn't sound like a satisfactory answer (after all, I didn't use the Startup Disk Creator, so a bug there wouldn't cause this for me), so I dug a little deeper. I noticed that [FONT=Courier New]sdX1[/FONT] was exactly the same size as the original .iso image and [FONT=Courier New]sdX2[/FONT] was a few MB in size. So I computed a checksum of [FONT=Courier New]/dev/sdX[/FONT] and verified it against the .iso image. Unsurprisingly, these did not match because the flash drive is much larger than the 981.0 MB Ubuntu image, so the checksum of the former is calculated over a lot of zeroes in addition to the dd'd (:)) image. What *did* struck me as a surprise, however, was that the sha256-checksums of the .iso image and the contents of [FONT=Courier New]/dev/sdX1[/FONT] matched exactly. But...the .iso image did not just create [FONT=Courier New]sdX1[/FONT], it also created [FONT=Courier New]sdX2[/FONT] as well as a partition table for the device [FONT=Courier New]sdX[/FONT] which holds the information of the existence of [FONT=Courier New]sdX1[/FONT] and [FONT=Courier New]sdX2[/FONT].

I've been trying to figure out what is going on, but the following still confuses me greatly: how can dd'ing an image (to [FONT=Courier New]sdX[/FONT], not [FONT=Courier New]sdX1[/FONT]!) have created a partition table on [FONT=Courier New]sdX[/FONT] with two partitions in it, where one of the partitions contained by it ([FONT=Courier New]sdX1[/FONT]) is **an exact copy** of the original image? In other words: if the information contained in the .iso image makes up the contents of [FONT=Courier New]sdX1[/FONT], where did the information for [FONT=Courier New]sdX2[/FONT] and a partition table for [FONT=Courier New]sdX[/FONT] come from in the first place?

I'd be very happy if someone could shed some light on this. After all, it's never a bad thing to start the new year as a slightly more knowledgeable person! :-D

---

### Post by oldfred on 2014-12-31
When you use dd to copy the ISO image it is copying a DVD which does not have partitions like a standard drive.

Do the partitions look like normal partitions? 

I have seem where very strange partition appear. I believe the random data that DVD has written into the first sector is close enough that then partition tools try to read that data as partitions.

The info on partition table is just a few entries in the MBR.
 Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

---

### Post by sudodus on 2014-12-31
Does your USB drive boot properly? There is an iso9660 file system, which is read-only. Don't worry about the other things, as long as it works.

But you should worry about using ***dd***, nicknamed 'disk destroyer', because there are ***no safely checks***. I made ***mkusb*** to wrap security around dd. See this link [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Ko_Char on 2014-12-31
I think you answer is here. 

[http://lists.gnu.org/archive/html/coreutils/2014-10/msg00012.html](http://lists.gnu.org/archive/html/coreutils/2014-10/msg00012.html)

---

### Post by pveurshout on 2015-01-18
> **Ko_Char said:**
> I think you answer is here. 

[http://lists.gnu.org/archive/html/coreutils/2014-10/msg00012.html](http://lists.gnu.org/archive/html/coreutils/2014-10/msg00012.html)

Thanks, this clears it up! I'll mark the thread as solved.

> **sudodus said:**
> Does your USB drive boot properly? There is an iso9660 file system, which is read-only. Don't worry about the other things, as long as it works.

But you should worry about using ***dd***, nicknamed 'disk destroyer', because there are ***no safely checks***. I made ***mkusb*** to wrap security around dd. See this link [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Yeah, the install worked just fine :)  I was just afraid that *if* something had gone wrong while creating the disk, it might've corrupted something that wouldn't have turned up until later (i.e., after a seemingly successful install). (And, also, I was curious ;).)

> **oldfred said:**
> When you use dd to copy the ISO image it is copying a DVD which does not have partitions like a standard drive.

Do the partitions look like normal partitions? 

I have seem where very strange partition appear. I believe the random data that DVD has written into the first sector is close enough that then partition tools try to read that data as partitions.

The info on partition table is just a few entries in the MBR.
 Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

Great and comprehensive read, thanks for the tip!

---

