---
title: "Help with external installtion and grub"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by silentj408 on 2010-06-28
I have a external device which im installing Gos (Googles ubuntu) on .
the external device has 2 partitions , both were fat32 until i installed the gos on the 1st partition. Im trying to install GOS and leave the other fat32 partition intact  so I can still use the external device .. my problem is when install the os and grub on the dev/sdc1 I get a grub 17 error? I do not want grub on my internal HD , as this is meant to be a portable os . any help would be nice

---

### Post by darkod on 2010-06-28
If you also put grub on the partition sdc1, what will you boot with? The bootloader needs to be on the MBR of the disk to be able to boot.
I understand why you don't want it on the MBR of the int disk, but why sdc1?

---

