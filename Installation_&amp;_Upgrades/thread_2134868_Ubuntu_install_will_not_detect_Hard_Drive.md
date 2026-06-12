---
title: "Ubuntu install will not detect Hard Drive"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by Comzee on 2013-04-12
I am trying to install Ubuntu 12.10 on [ASRock A75M FM1 AMD A75 (Hudson D3)]("http://www.asrock.com/mb/overview.asp?model=a75m-hvs") with a [wd2002fyps hard drive ]("http://www.wdc.com/wdproducts/library/SpecSheet/ENG/2879-701312.pdf").

I have tried these ISO : **ubuntu-12.10-desktop-amd64.iso** and **ubuntu-12.10-desktop-i386.iso** and **linux-secure-12.10-64bit.iso**

I have tried all three of these ISO using USB install method, and also trying to use a USB-DVD-ROM drive. 

Here is the issue, when you get to the screen to pick your HD (during install), nothing shows up, and if you click anything like** +** or **Install** it throws an error. The odd things is, if I start gparted the HD shows up fine, I partitioned it as ext4, but I have tried the install with it unallocated / ext2 / ext3. Pics below to make this clear:

[http://i.imgur.com/IbbzysC.jpg](http://i.imgur.com/IbbzysC.jpg)
[http://i.imgur.com/a8nKCks.jpg](http://i.imgur.com/a8nKCks.jpg)
[http://i.imgur.com/5UpdKtR.jpg](http://i.imgur.com/5UpdKtR.jpg)
[http://i.imgur.com/JfWe9zY.jpg](http://i.imgur.com/JfWe9zY.jpg)

Oh, and with the USB install method, I have booted the USB with uefi mode and bios mode. The CD-DVD-ROM only supports booting from bios mode. Either way all the things I've tried give the exact same results I listed above.

Any ideas ?

---

### Post by darkod on 2013-04-12
Usually this happens if the disk has been used in fakeraid before and has meta data leftovers. Gparted from live mode will show it OK but the installer is ignoring it thinking it's part of raid array.

If you are NOT running raid, you can try removing the meta data from live mode in terminal with:
```
sudo dmraid -Er /dev/sda
```

The above assumes your hdd is /dev/sda, if you boot from usb stick the stick can be sda and the hdd sdb, so simply adjust the command.

If that asks you to confirm removal of meta data, this was the issue. if it says there is no meta data on the disk, then you don't, and the problem is with something else.

---

### Post by Comzee on 2013-04-12
That worked! I love you and I love Ubuntu forums thanks!!

---

