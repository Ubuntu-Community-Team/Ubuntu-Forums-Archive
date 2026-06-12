---
title: "Grub error 21"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by fermulator on 2006-10-14
Hey there fellow ubuntu-ers!
[EDIT:  New information available to my problem...]

**So firstly, my setup:**
AMD Athlon XP 3200+
DFI LanParty NFII ULtra B
2x512MB DDR400
**On my Silicon 3114 Sata Controller:**
SATA 0 - 250GB Seagate (Raid 0)
SATA 1 - 250GB Seagate (Raid 0)
SATA 2 - 160GB Maxtor (Single)

**Partitioning:**
_2x250GB = 500GB RAID ARRAY_
/dev/mapper/sil_agaiagdcdfei1    52428092       19468512  32959580  38% /media/mapper_sil_agaiag dcdfei1 (Windows XP)
/dev/mapper/sil_agaiagdcdfei2 52428124  10082548  42345576  20% /media/mapper_sil_agaiag dcdfei2 (Windows Vista)
/dev/mapper/sil_agaiagdcdfei5 157284348 106426600  50857748  68% /media/mapper_sil_agaiag dcdfei5
/dev/mapper/sil_agaiagdcdfei6 313444180 152784892 160659288  49% /media/mapper_sil_agaiag dcdfei6
/dev/mapper/sil_agaiagdcdfei7 10482380   3338740   7143640  32% /media/mapper_sil_agaiag dcdfei7


_1x160GB = single drive_
/dev/sdc1             20972824     88396  20884428   1% /media/sdc1
/dev/sdc3             97161116  22950972  74210144  24% /media/sdc3
/dev/sdc4             20972856   6166568  14806288  30% /media/sdc4
/dev/sdc5             19607924   2199636  16412260  12% / (ubuntu)




I've got Windows Vista and Windows XP Dual booting on the Raid array.
  The boot sector for Vista resides on the first partition of HD0. (hd0,0).  

So I boot ubuntu 6.06...
Start the install off of the live CD!
I tell it to install on the 19GB partition set aside for ubuntu.

It finishes...I reboot...
BAM:

```
Grub Loading Stage 1.5
Grub Loading please wait....
Error 21
```

Odd....
Then I think to myself....ubuntu installer never asked me WHERE it wanted me to install the GRUB Boot Loader to!!  What's the deal with this?
I don't really know WHERE it installed itself to?

I WANT to install grub to the master boot record (mbr) of the SINGLE drive...NOT the RAID ARRAY...

Either way...grub seems to be unable to boot itself...or any other operating system because I receive that error 21.



NOTE:  I've also tried the whole sequence agian, but this time installing dmraid (FakeRaid) before conducting the installation....same "Grub error 21".


EDIT: (Added grub menu.lst)
Here's my /boot/grub/menu.lst file:
```

default         0
timeout         3
hiddenmenu

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sdc5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sdc5 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin 
boot

title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader +1

```

Here's my device.map file:
```

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

```

I can use the [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") to boot linux & Windows!

When I say. "Linux", boot linux...it brings up the grub menu that I have, and i can boot any of the OSes I have defined in my menu.lst file!

Initially when grub installed, it THOUGHT that linux resided on (hd2,4), because it didn't notice that the RAID array existed.

SOO....I ASSUME grub thinks it exists on hd2...when really...it should be on hd1 because of the RAID array being only one disk according to the BIOS.?


I've tried editing the device.map file to remove the "(hd2), and replace with (hd1)  /dev/sdc...but that didn't work either.

I've also tried many, (many), of the "SuperGrubBootCD" automated and manual "fix boot" options...but none seem to fix the initial "error 21" error from grub.


Does anyone have any idea what I need to do to get grub to realize it's on the hd1 drive, and NOT the hd2 drive?



Any help / suggestions would be greatly appreciated.

Thanks!

---

### Post by fermulator on 2006-10-15
Bump please :-)

---

### Post by UberBlue on 2006-10-20
I'm having the same problem.

From what I gather, it has to do with the raid controller writing to the first few sectors of something (I have a bad memory for details). These first few sectors of something are also what GRUB needs. See the conflict?


Here's the google links:

[http://www.google.com/search?sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-38,GGGL:en&q=GRUB+error+21+hpt]("http://www.google.com/search?sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-38,GGGL:en&q=GRUB+error+21+hpt")

My particular raid controller is a Highpoint 370/372, but I can imagine the same problem with other fake-raids.

Don't know if it's any help, but it's better than nothing.

---

### Post by russianpirate on 2006-10-20
Check bios settings to make sure all drives are enabled and raid is enabled (?) and try to reinstall grub (grub-install) from the livecd.

---

### Post by adrian15 on 2006-10-23
> **UberBlue said:**
> I'm having the same problem.

From what I gather, it has to do with the raid controller writing to the first few sectors of something (I have a bad memory for details). These first few sectors of something are also what GRUB needs. See the conflict?


Here's the google links:

[http://www.google.com/search?sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-38,GGGL:en&q=GRUB+error+21+hpt]("http://www.google.com/search?sourceid=navclient-ff&ie=UTF-8&rls=GGGL,GGGL:2006-38,GGGL:en&q=GRUB+error+21+hpt")

My particular raid controller is a Highpoint 370/372, but I can imagine the same problem with other fake-raids.

Don't know if it's any help, but it's better than nothing.

Check #8 on:
[http://adrian15.raulete.net/grub/tiki-index.php?page=EnFaq](http://adrian15.raulete.net/grub/tiki-index.php?page=EnFaq) if what UberBlue is talking about is your raid writing in the same place as stage1_5 you would need to link stage1 to stage2 directly.

adrian15

---

### Post by gn2 on 2006-10-23
To ensure Grub gets written to the single Ubuntu drive, install it with the raid drives power disconnected.

This should get you sorted with a safe set-up: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

You may need to run "fixmbr" from Recovery in Windows CD.

---

