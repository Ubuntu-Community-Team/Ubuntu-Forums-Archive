---
title: "ordinary PATA IDE disk not detected on 7.10 Gutsy install"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Wollongong on 2007-10-21
On a fairly 'vanilla' system: Intel Pentium CPU, Intel 865 graphics (D865 mainboard) Western Digital IDE disk, I've got a failure to install 7.10 due to no disks detected. The partitioning screen is blank. There is no way to nominate the root partition, as there are no partitions found.

This system works fine on Debian ETCH.

What I've done so far to resolve:
 1. checked the MD5 sum on the ISO downloaded, and on the CD burned.
 2. looked for /dev/hda hdb sda sdb etc: none found
 3. manually created /dev/hda using "mknod /dev/hda b 3 0
 4. tried 'fdisk /dev/hda' but it still said no such device

Here are the hardware details per Debian:

$ dmesg|grep hda
Kernel command line: root=/dev/hda5 ro
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    **hda: WDC WD1600BB-00RDA0, ATA DISK drive**
    hda: max request size: 512KiB
    hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
    hda: cache flushes supported
     hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 >
     Adding 1959920k swap on /dev/hda3.  Priority:-1 extents:1 across:1959920k
     EXT3 FS on hda5, internal journal
     EXT3 FS on hda6, internal journal

$ dmesg|grep -i intel
..
agpgart: Detected an Intel 865 Chipset.

$ cat /proc/cpuinfo
..
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz

---

### Post by Wollongong on 2007-10-25
Close this thread, same discussion over here:
[http://ubuntuforums.org/showthread.php?t=586894](http://ubuntuforums.org/showthread.php?t=586894)

---

