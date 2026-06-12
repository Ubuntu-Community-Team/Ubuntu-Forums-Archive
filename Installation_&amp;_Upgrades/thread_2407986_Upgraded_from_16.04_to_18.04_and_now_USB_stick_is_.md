---
title: "Upgraded from 16.04 to 18.04 and now USB stick is mounted as root"
date: 2018-12-12
forum: Installation &amp; Upgrades
---

### Post by jkbpower on 2018-12-12
Hi,
Just upgraded to 18.04 and everything seems to work besides that I cant write to any USB sticks I put in.
I have tried different USB and same problem.
The USB is mounted in /media/(username)/(usb name).
The /media/username folder is owned by root.I managed to change owner to me but the usb folder is still owned by root and I cant change this.
Yesterday it worked after some trix (dont know how :-)) but today not.
When I ran 16.04 I believe every USB was mounted under /media/USB0...USB1 etc.

Anyone know how to fix this issue?

/Jimmy

---

### Post by ajgreeny on 2018-12-12
Tell us more about the USB sticks.
Have you formatted them to a different filesystem from the usual fat32 on smaller sticks, or exfat on those over 64GB?

With a problem stick inserted and hopefully mounted, let's see the output of ```
sudo fdisk -l
``` which may give us more clues.

---

### Post by jkbpower on 2018-12-12
This is the output from fdisk. Sorry in swedish..-(
One formatted as FAT16 and the other one is a USB SD card reader with a 8Gb FAT32 card.
```
henningsson@henningsson-MS-7798:~$ sudo fdisk -l
Disk /dev/loop0: 88,2 MiB, 92483584 byte, 180632 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop1: 171,8 MiB, 180129792 byte, 351816 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop2: 89,5 MiB, 93818880 byte, 183240 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop3: 173,6 MiB, 182030336 byte, 355528 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop4: 140,7 MiB, 147496960 byte, 288080 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop5: 3,7 MiB, 3878912 byte, 7576 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop6: 171,8 MiB, 180129792 byte, 351816 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop7: 171,8 MiB, 180133888 byte, 351824 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/sda: 931,5 GiB, 1000204886016 byte, 1953525168 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 4096 byte
I/O-storlek (minsta/optimal): 4096 byte / 4096 byte
Disketikettstyp: dos
Diskidentifierare: 0x87096af0

Enhet      Start     Början     Slutet   Sektorer Storlek Id Typ
/dev/sda1  *           2048 1936885759 1936883712  923,6G 83 Linux
/dev/sda2        1936887806 1953523711   16635906      8G  5 Utökad
/dev/sda5        1936887808 1953523711   16635904      8G 82 Linux växling / Solaris

Partition 2 börjar inte på en fysisk sektorgräns.




Disk /dev/loop8: 13 MiB, 13619200 byte, 26600 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop9: 173,3 MiB, 181735424 byte, 354952 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop10: 2,3 MiB, 2355200 byte, 4600 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop11: 14,5 MiB, 15208448 byte, 29704 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop12: 87,9 MiB, 92114944 byte, 179912 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop13: 34,6 MiB, 36216832 byte, 70736 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/loop14: 173,3 MiB, 181760000 byte, 355000 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte


Disk /dev/sdb: 3,8 GiB, 4089446400 byte, 7987200 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte
Disketikettstyp: dos
Diskidentifierare: 0x9c83b7f0

Enhet      Start Början  Slutet Sektorer Storlek Id Typ
/dev/sdb1           512 7987199  7986688    3,8G  6 FAT16


Disk /dev/sdc: 7,5 GiB, 7990149120 byte, 15605760 sektorer
Enheter: sektorer av 1 * 512 = 512 byte
Sektorstorlek (logisk/fysisk): 512 byte / 512 byte
I/O-storlek (minsta/optimal): 512 byte / 512 byte
Disketikettstyp: dos
Diskidentifierare: 0xae7318fe

Enhet      Start Början   Slutet Sektorer Storlek Id Typ
/dev/sdc1          2048 15605759 15603712    7,5G  c W95 FAT32 (LBA)

```

---

### Post by jkbpower on 2018-12-16
I did a fresh install and now everything seems to work as it should.
Something must have gone wrong when i upgraded

---

