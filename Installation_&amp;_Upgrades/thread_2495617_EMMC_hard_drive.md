---
title: "EMMC hard drive"
date: 2024-02-24
forum: Installation &amp; Upgrades
---

### Post by gordie692 on 2024-02-24
Hi guys wasn't sure where to put this but I have a question to ask I have a new Acer laptop nothing special just has a EMMC 120 gig hd with Windows 11 which I really hate Ubuntu or Mint or Debian would would right I am just looking for one to install and still have a space to put documents and some pics on

---

### Post by Rex Bouwense on 2024-02-25
Not sure what your question is but Ubuntu will certainly fit on that hard drive with plenty of space left over for "documents and some pictures"

---

### Post by gordie692 on 2024-02-25
Thanks Rex sorry I worked all but this Acer has 4 gigs of just a check email, browse, bank look at my docs and pics so Ubuntu would okay maybe Mint

---

### Post by TheFu on 2024-02-25
eMMC is more like an SSD than a HDD.  Basically, it is SSD chips soldered directly onto the motherboard.  Ensure you have excellent backups, since those ships will eventually fail, just like SSDs fail.  If the system if over 4 yrs old, I'd definitely backup data at least weekly, if not daily.

My main desktop with Linux Mind on it uses ..... let me check ....
```
$ sudo parted -l /dev/vda
Model: Virtio Block Device (virtblk)
Disk /dev/vda: 42.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  2097kB  1049kB                                        bios_grub
 2      2097kB  540MB   538MB   fat32           EFI System Partition  boot, esp
 3      540MB   2504MB  1964MB  linux-swap(v1)                        swap
 4      2504MB  4624MB  2120MB  zfs
 5      4624MB  42.9GB  38.3GB  zfs
```

Looks like about 45GB.  My laptops over the last 15 yrs have had between 16GB and 500GB of storage.  I've run with extra storage for many years in 64GB of space.  I keep most media on network storage, not on the laptop.  For media, you could easily get a $20 flash drive (microSD/SDHC/USB) for 100GB of extra storage to be added. If the laptop has a SDHC slot like many do, a 128GB microSD with a microSD-to-SDHC converter works well.  I use that for pure media.

I know many people who don't bother with any internal storage at all and just boot off a USB3 flash drive. Those come in all sizes and prices.  If you want even better performance, you could make that external storage a USB3 SSD.  Flash storage will be much slower than SSD storage, but it is still faster than HDD storage.

Bloat in Ubuntu keeps growing.  10 yrs ago, it was easy to fit Ubuntu onto a 16GB storage device.  Today, for a desktop, 35G would be a little tight.  64G is roomy, assuming no huge video files or games are stored on it.  100+ is so much storage, it is hard to imagine ... lots of room for music. Of course, you'll still need to be selective about videos.

Just some things for your consideration.

---

### Post by gordie692 on 2024-02-25
Thanks guys all installed works great

---

### Post by TheFu on 2024-02-26
> **gordie692 said:**
> Thanks guys all installed works great

The way to tell everyone you've gotten the answer you needed is to use the Thread Tools button and mark this thread as SOLVED.  Please do that.

---

