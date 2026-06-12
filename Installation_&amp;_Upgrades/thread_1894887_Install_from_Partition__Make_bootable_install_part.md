---
title: "Install from Partition / Make bootable install partition"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by whoshotdk on 2011-12-13
Hi there,

I've got a 500GB external USB HDD attached to my Mac. Ive just partitioned it into two partitions; 863MB 'Install' and 499.03GB 'Disk'.

I downloaded the Ubuntu install CD image named 'ubuntu-11.10-desktop-amd64.iso'.

Ive got a spare computer knocking about, but access to no CD drive.

What I'm trying to do is get the install CD onto the 863MB partition so I can then dismantle the USB drive (already done actually) and then once the 'Install' partition is ready, move the HDD into the spare computer as a normal SATA drive and install Ubuntu from the 'Install' partition to the bigger 'Disk' partition.

Im attempting to follow the instructions for Installation from USB Stick here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

And have got as far as converting the .iso file to a .img file. The instructions now tell me I need to find out which  device node my USB HDD has by using Disk Utility, then running the following command:

sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m

(obviously I altered the command with respect to the location of the CD image file)

However, I cant see where Disk Utility tells me the device node of the USD HDD and furthermore I suspect that wouldn't help so much; I need to make a specific partition bootable, not the whole device.

Im fairly tech savvy but my knowledge isnt great when it comes to this sort of stuff; so if anyone can give me any pointers Id very much appreciate it. Perhaps Im following the wrong instructions or more likely Im too daft to understand :) But I'd still like to give it a go if possible.

I would've tried a network boot, but suspect setting up a PXE boot environment would melt my brain.

Thanks much
Dave

---

### Post by garolou on 2011-12-13
dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m

means '**d**isk **d**uplicate from **i**nput file  /path/to/downloaded.img to **o**utput file /dev/rdiskN'

run:
```
sudo fdisk -l
```
to show you all the partitions you have on every disks.

You will probably see a 'disk' entry such as /dev/sdb
which is followed by a line for each partition it contains.

Here is an example of my dual boot laptop drive:
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          39      307200    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              39       18610   149174272    7  HPFS/NTFS
/dev/sda3           18610       38914   163087361    5  Extended
/dev/sda5           18610       38400   158959616   83  Linux
/dev/sda6           38400       38914     4126720   82  Linux swap / Solaris

```

Find the partition which you wish to copy to. Don't make a mistake or you may overwrite data you don't want to lose.

---

### Post by darkod on 2011-12-13
I have never tried anything similar, but in:
of=/dev/rdiskN

isn't the N the partition number?

You can always get the device with:
sudo fdisk -l
or
cat /proc/partitions

---

### Post by whoshotdk on 2011-12-13
Aha, thats exactly the info I needed!

I didnt realise that each volume was a seperate 'device' as such. Now I do. :)

Thanks very much for the advice guys; now I can get this little beastie up and running tonight!

Dave

---

