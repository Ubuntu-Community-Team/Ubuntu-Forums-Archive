---
title: "Ubuntu 22.04 desktop iso boot - snapd service failed, livecd service failed, rescue"
date: 2022-05-12
forum: Installation &amp; Upgrades
---

### Post by ag1233 on 2022-05-12
After downloading Ubuntu 22.04 LTS desktop iso and writing it to a DVD-R disc.
I tried booting the DVD.

It takes a long time (more than several minutes) booting (it is running on an Intel i7 4790 Haswell desktop, kind of old i know)
 and I watch various services started and ran - the systemd bootup mesages in the log on the console
finally it stalled at 2 messages

snapd service failed
livecd service failed
the disc light seemed to be on but there is no further progress. no gui etc.

Has anyone ran into the same issues? Is there a way to overcome it?

i didn't seemed to have the problem with the existing distribution earlier Ubuntu 20.10. it is installed on the same machine. I'm attempting a re-install, but first i'm checking the media.

in addition, is there a 'rescue' mode booting from the cd should I need to access the installed linux root system (on the ssd/hd) after installing?

thanks in advance.

---

### Post by sudodus on 2022-05-12
1. Did you try to create a bootable USB pendrive (by cloning from the Ubuntu 22.04 iso file to the pendrive) and boot from it? If not, please try it. I think it will be faster than from a DVD disk.

2. If you can run earlier versions of Ubuntu, and still have problems with 22.04, please

- download the [Ubuntu Forum's system-info script](https://github.com/UbuntuForums/system-info/),
- run it and let it upload the result to a pastebin, and
- put a link to the pastebin in a new post in this thread.

This will tell us a lot about your computer hardware and help us find a solution for you.

---

### Post by ag1233 on 2022-05-12
Thanks, I'd first try  using a usb pendrive. In case it could be my DVD drive starting to give problems after a few years, it is rarely used though.  

some abstracts from system-info are:
```

    Description: CPU
    Product: Intel(R) Core(TM) i7-4771 CPU @ 3.50GHz
    Vendor: Intel Corp.
    Physical id: 41
    Bus info: cpu@0
    Version: Intel(R) Core(TM) i7-4771 CPU @ 3.50GHz
    Slot: SOCKET 0
    Size: 1908MHz
    Capacity: 3900MHz
    Width: 64 bits
    Clock: 100MHz

Bios Vendor:         American Megatrends Inc.
Bios Version:        F10
Bios Release:        4.6
Board Vendor:        Gigabyte Technology Co., Ltd.
Board Name:          H87-D3H-CF

              total        used        free      shared  buff/cache   available
Mem:           15Gi       678Mi        10Gi        40Mi       4.3Gi        14Gi
Swap:          16Gi          0B        16Gi

Disk /dev/sda: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: M4-CT128M4SSD2  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FF57A7BC-CD33-4F13-AEDC-5E1E0AE1000A

Device         Start       End   Sectors  Size Type
/dev/sda1       2048    206847    204800  100M EFI System
/dev/sda2     206848 109258751 109051904   52G Linux filesystem
/dev/sda3  109258752 218310655 109051904   52G Linux filesystem
/dev/sda4  218310656 250069646  31758991 15.1G Linux swap

The current kernel version is:       5.8.0-63-generic 
The current release description is:  Ubuntu 20.10
Original Installation Media: Ubuntu 20.10 "Groovy Gorilla" - Release amd64 (20201022)


```
the cpu is a little earlier / slower than the Intel i7 4790 haswell, but has the same core count and is the same generation in design

dvd info isn't there and it looks like this from dvd+rw-mediainfo
```

INQUIRY:                [TSSTcorp][CDDVDW SH-224DB ][SB00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Media ID:              RITEK/F16
 Current Write Speed:   12.0x1385=16620KB/s
 Write Speed #0:        12.0x1385=16620KB/s
 Write Speed #1:        10.0x1385=13850KB/s
 Write Speed #2:        8.0x1385=11080KB/s
 Write Speed #3:        6.0x1385=8310KB/s
 Write Speed #4:        4.0x1385=5540KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     5.0x1385=6924KB/s@0 -> 12.0x1385=16620KB/s@2295103
 Speed Descriptor#0:    00/2295103 R@6.0x1385=8310KB/s W@12.0x1385=16620KB/s
 Speed Descriptor#1:    00/2295103 R@6.0x1385=8310KB/s W@10.0x1385=13850KB/s
 Speed Descriptor#2:    00/2295103 R@6.0x1385=8310KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#3:    00/2295103 R@6.0x1385=8310KB/s W@6.0x1385=8310KB/s
 Speed Descriptor#4:    00/2295103 R@6.0x1385=8310KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    2
 State of Last Session: empty
 "Next" Track:          2
 Number of Tracks:      2
READ TRACK INFORMATION[#1]:
 Track State:           invisible
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            1784656*2KB
 ROM Compatibility LBA: 270336
READ TRACK INFORMATION[#2]:
 Track State:           blank
 Track Start Address:   1786704*2KB
 Next Writable Address: 1786704*2KB
 Free Blocks:           508400*2KB
 Track Size:            508400*2KB
 ROM Compatibility LBA: 270336
FABRICATED TOC:
 Track#1  :             17@0
 Track#AA :             17@1784656
 Multi-session Info:    #1@0
READ CAPACITY:          1784656*2048=3654975488

```

the contents mounted ok
```

> sudo mount /dev/dvd /mnt/dvd
mount: /mnt/dvd: WARNING: source write-protected, mounted read-only.
> cd /mnt/dvd
> ls
boot  boot.catalog  casper  dists  EFI  install  md5sum.txt  pool  preseed  ubuntu
> head md5sum.txt 
d41b45afb922d3bd828d168ef2c1e380  ./dists/jammy/main/binary-amd64/Release
50c19236700101afc816586f808cf768  ./dists/jammy/main/binary-amd64/Packages.gz
d3b3df717bf7edcb5b6b9299e4c8011a  ./dists/jammy/main/binary-i386/Release
62e9482b6e74f40de9d3af06994b07e6  ./dists/jammy/main/binary-i386/Packages.gz
2defb55afa90da001df097444c643168  ./dists/jammy/restricted/binary-amd64/Release
9ad5c62e55fbd26ce06d018cca6383c2  ./dists/jammy/restricted/binary-amd64/Packages.gz
78cac51d29a8aec91041203d0ddf84e2  ./dists/jammy/restricted/binary-i386/Release
d251a1764385deb4bd7f67d8fcf0581b  ./dists/jammy/restricted/binary-i386/Packages.gz
55eaf1dfbdad672eacb1b4b2cba35782  ./dists/jammy/Release
c5cd4d40bc8106377c06314f7f778f58  ./dists/jammy/Release.gpg

> md5sum dists/jammy/Release
55eaf1dfbdad672eacb1b4b2cba35782  dists/jammy/Release

> md5sum dists/jammy/main/binary-amd64/Release 
d41b45afb922d3bd828d168ef2c1e380  dists/jammy/main/binary-amd64/Release


```

for now i think it could be related to all that DVD seeking, I'd try the usb approach.

---

### Post by sudodus on 2022-05-12
Thanks for those details. However, it would help if you let the system-info script upload the details to a pastebin, because there are other things to consider, for example the brand name and model of the computer.

Please notice that sensitive data are removed from the file uploaded to the pastebin, so it should not be risky.

[hr][/hr]
I'm looking forward to your test of the usb approach.

---

### Post by mgerstel on 2023-01-25
I just tried installing 22.04.1 from DVD (amd64 desktop). It's essentially impossible.
The files on the image are not laid out to facilitate fast reading from disk, which results in minutes and minutes of constant seeking. This is of course fine for USB boots, but the image won't work on an actual DVD. The service failures the original poster describes are likely timeouts. I hit the first one, but after 10 minutes I gave up anyway and abandoned the approach.

The DVD itself and the drive are fine.

---

