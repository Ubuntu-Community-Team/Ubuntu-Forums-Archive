---
title: "Ubuntu not booting from SATA HDD"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by Doublerob7 on 2008-08-29
Hey guys.

I just upgraded from my 2 old IDE drives to a single 500Gb SATA drive and have been running into some slight problems with it. I've been reading around about drivers and bios setting and such, but I just can't seem to get it working properly.

First things first, hardware.
Motherboard is an ASUS A8N-SLI running nForce4 drivers and an AMD 64-bit 3000+ CPU. Harddrive is a Western Digital 500Gb SATA 3Gb/s HDD, plugged into SATA slot 1.

Now to the problems...
Ubuntu / Windows will not boot off this drive. The BIOS recognizes it, the 'buntu liveCD sees it, even the windows setup CD sees it (albeit only 130GB of it) and i can completely go through with the installation of either OS. In fact, when I install it, and then boot a LiveCD, i can browse through the files it installed, and everything seems honky-dory.

But for the life of me it will not boot off the drive. When it goes through the boot device order during startup, it acts as if there aren't any HDD's present at all, and prints up an error saying 'no system disk found' (I presume because it didn't find an install CD)

Thanks in advance for any help :)

---

### Post by Pumalite on 2008-08-29
Post:
sudo lshw

---

### Post by Doublerob7 on 2008-08-29
here ya go:

```
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi4
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKS-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WMASY2031234
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=147728ba
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/disk
                version: 1.0
                serial: 0c3b4362-2998-43af-8a6b-7aad5e712fec
                size: 27GiB
                capacity: 27GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-08-28 12:13:50 filesystem=ext3 modified=2008-08-29 18:16:42 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2008-08-29 18:16:42 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: 1d7b5b6f-be2b-4675-be84-b5af30c9e448
                size: 3812MiB
                capacity: 3812MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sda3
                logical name: /media/disk-1
                version: 1.0
                serial: f08e396e-590f-44ed-9319-00ea0331ba95
                size: 434GiB
                capacity: 434GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-08-28 12:13:56 filesystem=ext3 modified=2008-08-29 18:16:46 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2008-08-29 18:16:46 state=mounted

```

---

### Post by spiderbatdad on 2008-08-29
I believe I have seen the boot option all_generic_ide used in this case.
Press f6 at startup screen. If you get a menu dialog, esc it. Otherwise, delete --quiet splash from the end of the kernel line and replace with all_generic_ide then enter to boot.

---

### Post by Doublerob7 on 2008-08-29
I don't get any menus when i spam f6. in fact, nothing happens at all...

how do i go about modifying the kernel? what file do i have to modify?

---

### Post by spiderbatdad on 2008-08-29
f6 is for "other options" from the startup screen of the live cd, as shown below. If you have already installed, the file to modify is /boot/grub/menu.lst
More info here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You can also edit the kernel line by pressing 'e' from the grub menu, then scrolling to the kernel line, and pressing 'e' again. Edit the end of the line, hit enter, and 'b' to boot.

---

