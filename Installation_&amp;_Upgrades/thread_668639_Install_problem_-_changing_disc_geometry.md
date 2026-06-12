---
title: "Install problem - changing disc geometry"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by stdPikachu on 2008-01-15
Howdy there, long time lurker, first time poster.

The time has come for Kubuntu on more than my laptop but I'm running into a problem with the way my hard drive geometry is detected. When I plug in the discs in the way my BIOS detects them as (i.e. OS drive as first SATA, docs drive as second SATA, hotplug drives as second and third SATA), the live CD boots and sees them as sdb, sdc, sda and sdd respectively. However, if I boot without the hotswap drives in the two internal drives are detected normally as sda and sdb.

Now, obviously if I install in this state presumably GRUB/boot kernel will be b0rked, as it'll detect the hard drives wrongly depending on whether the hotswap hard drives wrongly (I get the expected sda and sdb when I boot without them plugged in at boot) and it'll try and boot from the wrong drive, since the kernel command line doesn't follow things like UUID's. Booting without the hotswap drives in isn't a workable workaround as I sometimes need to reboot or power the machine on remotely.

Hardware is an Asus A8N Premium, with four SATA ports hanging off the nVidia chipset, as well as a Silicon Image chipset with another four hanging off that (which, incidentally, behave just fine, I don't use them because they're slower than the nV ones). All four ports on the nV controller are hooked up to either the two internal drives or the two hotswap drives.

Has anyone run into this problem before? Has there been a change in recent kernels that mean the kernel/udev detect the drives in a  different order to the BIOS?

---

### Post by stdPikachu on 2008-01-15
Well, sort of fixed for now.

Found out that the GRUB in Ubuntu *does* support UUID's as well as fstab so attempted an install anyway. Install worked OK but of course when it came to grub-install the boot drive was identified as hd2 rather than hd0 as GRUB sees it on reboot. Anyway, an edit to the GRUB options and it boots.

Presumably this is because an installed GRUB grabs info from the BIOS whereas the GRUB on the live CD bases its info on data from the running kernel...?

Still not tested what'll happen as I add and remove hard drives yet though, so it might all go wrong.

One thing that does bother me though - every time grub-install is run, won't it misdetect by boot drive as something other than hd0 every time (since what the kernel sees as sda will change depending on what drives are plugged in)?

Finally, is it worth editing my udev rules for persistent storage to "force" more sensible/consistent device names?

---

### Post by polmir on 2008-01-15
please post the output of the following command:

```
sudo lshw
```

---

### Post by stdPikachu on 2008-01-16
Edited for brevity;
```
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi6
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: WDC WD2500JD-00G
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 02.0
             serial: WD-WMAEP3092627
             size: 232GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume
                description: W95 FAT32 (LBA) partition
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                capacity: 232GB
                capabilities: primary
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi7
          logical name: scsi8
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk:0
             description: SCSI Disk
             product: WDC WD1500AHFD-0
             vendor: ATA
             physical id: 0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             version: 20.0
             serial: WD-WMAP41338585
             size: 139GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdc1
                capacity: 67GB
                capabilities: primary bootable
           *-volume:1
                description: Linux filesystem partition
                physical id: 2
                bus info: scsi@7:0.0.0,2
                logical name: /dev/sdc2
                capacity: 31MB
                capabilities: primary bootable
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@7:0.0.0,3
                logical name: /dev/sdc3
                size: 72GB
                capacity: 72GB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdc5
                   capacity: 29GB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sdc6
                   capacity: 42GB
        *-disk:1
             description: SCSI Disk
             product: WDC WD7500AAKS-0
             vendor: ATA
             physical id: 1
             bus info: scsi@8:0.0.0
             logical name: /dev/sdd
             version: 30.0
             serial: WD-WCAPT0016136
             size: 698GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: Linux swap / Solaris partition
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdd1
                capacity: 972MB
                capabilities: primary nofs
           *-volume:1
                description: Linux filesystem partition
                physical id: 2
                bus info: scsi@8:0.0.0,2
                logical name: /dev/sdd2
                capacity: 558GB
                capabilities: primary
           *-volume:2
                description: W95 FAT32 (LBA) partition
                physical id: 3
                bus info: scsi@8:0.0.0,3
                logical name: /dev/sdd3
                capacity: 138GB
                capabilities: primary
     *-pci:0
        *-storage
             description: RAID bus controller
             product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller
             vendor: Silicon Image, Inc.
             physical id: a
             bus info: pci@0000:05:0a.0
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=sata_sil latency=32 module=sata_sil
           *-disk
                description: SCSI Disk
                product: WDC WD3200JD-00K
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 08.0
                serial: WD-WMAMR1175929
                size: 298GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux swap / Solaris partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 2002MB
                   capabilities: primary bootable nofs
              *-volume:1
                   description: W95 FAT32 (LBA) partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 114GB
                   capabilities: primary
              *-volume:2
                   description: W95 FAT32 (LBA) partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 181GB
                   capabilities: primary
     *-scsi
          physical id: f
          bus info: usb@1:9
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: CompactFlash
             vendor: OEI-USB
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sde
             version: 2.0
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             product: SM/MS/SD
             vendor: OEI-USB
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdf
             version: 2.0
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdf
```

As you can see, the 320GB drive is plugged into the SI controller at the moment. But the order of the sd[a-c] drives is all b0rked - the 150GB drive should be sda, the 750GB drive should be sdb and the 250GB drive should be sdc or sdd.

You can see the same sort of thing here:

```
std@tybalt:~$ ls -l /dev/disk/by-path/
total 0
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:02.0-usb-0:9:1.0-scsi-0:0:0:0 -> ../../sde
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:02.0-usb-0:9:1.0-scsi-0:0:0:1 -> ../../sdf
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:06.0-ide-0:1 -> ../../hdb
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:06.0-ide-1:0 -> ../../hdc
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:06.0-ide-1:1 -> ../../hdd
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:07.0-scsi-1:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:07.0-scsi-1:0:0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:08.0-scsi-0:0:0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-0:0:0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-0:0:0:0-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-0:0:0:0-part3 -> ../../sdc3
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-0:0:0:0-part5 -> ../../sdc5
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-0:0:0:0-part6 -> ../../sdc6
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:00:08.0-scsi-1:0:0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-1:0:0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-1:0:0:0-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:00:08.0-scsi-1:0:0:0-part3 -> ../../sdd3
lrwxrwxrwx 1 root root  9 2008-01-16 20:11 pci-0000:05:0a.0-scsi-2:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:05:0a.0-scsi-2:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:05:0a.0-scsi-2:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-01-16 20:11 pci-0000:05:0a.0-scsi-2:0:0:0-part3 -> ../../sda3
```

Yet GRUB will only work with this:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=7ad9b5c7-bbb7-42b2-9e22-0abf251b7e3a ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet
```

Since GRUB sees the precedence order correctly, unlike the running kernel.

---

### Post by polmir on 2008-01-16
I think, Your problem is RAID.
Please, red this:
[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid]("http://ubuntuforums.org/showthread.php?t=630644&highlight=raid")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[https://help.ubuntu.com/community/FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug")
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0")

---

### Post by stdPikachu on 2008-01-16
I'm not using RAID.

---

