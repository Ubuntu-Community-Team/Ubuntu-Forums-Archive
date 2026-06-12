---
title: "Kernel Bug during IDE / hd probing"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2007-01-02
I appear to have stumbled upon a bug in the kernel that can, in certain circumstances, both cause the kernel-boot to get stuck in an endless loop, and possibly damage the IDE drives over time (based on experience).

I've described it as fully as I can here in the hope that kernel guru's can check my findings and fix the problem. Some of my assumptions may be wrong, but the report and procedures I followed are accurate.

**Scenario:**

PC with a Promise FastTrak TX2000 SoftRAID controller and 4x 60GB IDE parallel ATA drives configured as RAID 10 (Mirror + Stripe) to provide one logical 120GB drive.
The PC already has Windows 2003 Server installed and booting from the RAID 10, with 2 NTFS partitions.

I wanted to shrink the 2nd partition to make room to install Ubuntu 6.10 from the Live CD.

**[color=red]Bug:[/color]**

[https://launchpad.net/distros/ubuntu/+bug/77734](https://launchpad.net/distros/ubuntu/+bug/77734)

When starting Linux the kernel loads the Promise fasttrak controller module "pdc202xx" and then probes each of the connected IDE hard drives for a partition table.

Large drives use LBA addressing to overcome the CHS limitations of partition tables.

If the probe finds a partition table on any drive, it then tries to seek to the starting sector of each partition (presumably to read its boot-sector system-id byte), and also tries to seek into the last few sectors of the partition (looking for a superblock?).

On a RAID 0 array where the striping causes the partition table to represent a larger logical drive, the starting and ending sector numbers of some partitions are beyond the end of the physical drive the partition table is written on.

This causes the Disk Read Errors reported here.

The fix would be for the probe to compare the physical number of cylinders reported by the drive (as seen by e.g. fdisk /dev/hde or fdisk /dev/hdg) to the starting/ending sector numbers for the LBA device.

If the entries in the partition are beyond the end of the physical disk the probe should handle the situation gracefully (This could potentially be used as a cue to auto-loading dmraid).

Once dmraid is loaded "fdisk /dev/mapper/raidarrayname" shows the correct total number of logical sectors.

**Experience:**

During boot there was a lot of repetitive clicking from the drives, and when I removed the boot options "quiet splash" I saw a lot of drive read errors of the form (this is a vastly truncated list):
```
PDC202XX: Primary channel reset.
ide2: reset: success
hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hde: task_in_intr: error=0x04 { DriveStatusError }
ide: failed opcode was: unknown
end_request: I/O error, dev hde, sector 238276076
printk: 8 messages suppressed.
Buffer I/O error on device hde2, logical block 47279294
hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hde: task_in_intr: error=0x04 { DriveStatusError }
ide: failed opcode was: unknown
hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
```
This would continue for several seconds, with the error reports flashing past on the screen too quickly to be read properly. As the kernel eventually booted I didn't pay too much attention to this originally.

Once booted, I installed the dmraid package and then used it to manage the logical RAID volume successfully.

I then used ntfsresize to shrink the 2nd NTFS file-system, and then fdisk to shrink the partition containing it. Then I added 2 Linux partitions. 

After reboot the kernel-boot got stuck in an endless loop with similar errors to those above.

Sometimes even after a power-down the drives wouldn't start up successfully during the BIOS POST and it gave me concern the drives could be physically damaged trying to seek beyond the end of their physical capabilities so repetitively.

I then found Windows could no longer start completely although it could successfully complete a CHKDSK operation with no error reports on either of the 2 NTFS file-systems.

Using Norton's "diskedit /m" from a floppy disk boot I zeroed out the Linux partition-table entries and tried again. This didn't seem to improve matters.

I managed to get Linux to boot without errors by adding "hde=noprobe hdf=noprobe hdg=noprobe hdh=noprobe" to the boot command line.
This meant none of the drives was recognised and I couldn't find a way to probe for them after boot, and therefore dmraid had no drives to recognise a RAID array on.

I tried rebooting to Linux and left it for about an hour whilst it continued reporting the disk errors and it eventually managed to boot the Live CD.

I again installed dmraid, and then I reset the 2nd partition size to the original (larger) size  using fdisk, but left the NTFS file-system as it was.

After a reboot, the kernel-boot was reporting drive errors for a few seconds but then passed on and successfully started, as at the start of this process.

I again installed dmraid, and then examined the LBA sector start/end values using fdisk.

I noticed that the ending position of the shrunken partition had not been on a track boundary (not a multiple of 63 sectors-per-track).

I then shrank the partition size so it ended on a track boundary, and the following partition's starting sector number would be an exact multiple of the 63 sectors-per-track value.

I rebooted into Windows and was able to successfully start it for the first time in 24 hours.

Again I rebooted and Linux was able to start with the same few seconds of disk errors, but it didn't get stuck in an endless loop as the original partition-shrink had caused it to.

I then examined all the boot-time error messages that reported sector numbers using
```
$ grep sector /var/log/messages
```
and realised that the failing sector numbers were beyond the end of the physical disk, because the partition table represents the Striped Array, which is double the physical disk size, and therefore contains LBA sector numbers beyond the end of the physical disk.

That leads to the probing causing disk errors during boot before dmraid is loaded.

---

### Post by bapoumba on 2007-01-02
Hi,
I have nor read your entire post, not able to understand it. But have you filled a bug report, may be linking to your post for details ?

---

### Post by IntuitiveNipple on 2007-01-02
Yes, a bug report has been filed and is now linked to in the article.

---

### Post by IntuitiveNipple on 2007-01-25
I've been slowly working to isolate the source-code at the root of this error. The biggest problem I faced was the sheer number of errors reported at boot-time swamped the kernel's log buffer (128KB by default) and therefore I had no information about what was happening in the lead-up to this.

Yesterday I built a new kernel with the kernel log buffer size increased from 128KB to 1MB. 

Using **make menuconfig** I changed the **Kernel Hacking** Kernel Log Buffer size. I altered the log-buffer-shift parameter from 17 to 20. This is a bit-shift value, so the buffer size is 2^X.

The entry in the kernel configuration file **.config** is **CONFIG_LOG_BUF_SHIFT**.

Now finally I have the kernel messages leading up to bug:
```
[17179576.612000] AMD7441: IDE controller at PCI slot 0000:00:07.1
[17179576.612000] AMD7441: chipset revision 4
[17179576.612000] AMD7441: not 100% native mode: will probe irqs later
[17179576.612000] AMD7441: 0000:00:07.1 (rev 04) UDMA100 controller
[17179576.612000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
[17179576.612000]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:DMA
[17179576.612000] Probing IDE interface ide0...
[17179576.900000] hda: Maxtor 6Y120L0, ATA DISK drive
[17179577.180000] hdb: Maxtor 6Y060L0, ATA DISK drive
[17179577.236000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.236000] Probing IDE interface ide1...
[17179577.972000] hdc: PIONEER DVD-RW DVR-109, ATAPI CD/DVD-ROM drive
[17179578.756000] hdd: PIONEER DVD-RW DVR-103, ATAPI CD/DVD-ROM drive
[17179578.812000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.824000] hda: max request size: 128KiB
[17179578.832000] hda: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179578.836000] hda: cache flushes supported
[17179578.836000]  hda: hda1 hda2 hda3 < hda5 hda6 hda7 hda8 >
[17179578.884000] hdb: max request size: 128KiB
[17179578.884000] hdb: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179578.884000] hdb: cache flushes supported
[17179578.884000]  hdb: hdb1
[17179578.888000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
[17179578.888000] Uniform CD-ROM driver Revision: 3.20
[17179578.912000] hdd: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, DMA
[17179579.280000] PDC20271: IDE controller at PCI slot 0000:00:08.0
[17179579.280000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 20 (level, low) -> IRQ 169
[17179579.280000] PDC20271: chipset revision 2
[17179579.280000] PDC20271: ROM enabled at 0x88000000
[17179579.280000] PDC20271: 100% native mode on irq 169
[17179579.280000]     ide2: BM-DMA at 0xb000-0xb007, BIOS settings: hde:pio, hdf:pio
[17179579.280000]     ide3: BM-DMA at 0xb008-0xb00f, BIOS settings: hdg:pio, hdh:pio
[17179579.280000] Probing IDE interface ide2...
[17179579.572000] hde: Maxtor 6Y060L0, ATA DISK drive
[17179579.852000] hdf: Maxtor 6Y060L0, ATA DISK drive
[17179579.908000] ide2 at 0xd400-0xd407,0xd002 on irq 169
[17179579.908000] hde: max request size: 128KiB
[17179579.924000] hde: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179579.924000] hde: cache flushes supported
[17179579.924000]  hde: hde1 hde2 hde3 < >
[17179579.928000] hdf: max request size: 128KiB
[17179579.944000] hdf: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179579.944000] hdf: cache flushes supported
[17179579.944000]  hdf: unknown partition table
[17179579.952000] Probing IDE interface ide3...
[17179580.240000] hdg: Maxtor 6Y060L0, ATA DISK drive
[17179580.520000] hdh: Maxtor 6Y060L0, ATA DISK drive
[17179580.576000] ide3 at 0xb800-0xb807,0xb402 on irq 169
[17179580.576000] hdg: max request size: 128KiB
[17179580.592000] hdg: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179580.592000] hdg: cache flushes supported
[17179580.592000]  hdg: hdg1 hdg2 hdg3 < >
[17179580.616000] hdh: max request size: 128KiB
[17179580.632000] hdh: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179580.632000] hdh: cache flushes supported
[17179580.632000]  hdh: unknown partition table
[17179580.756000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.756000] hde: dma_intr: error=0x04 { DriveStatusError }
[17179580.756000] ide: failed opcode was: unknown
[17179580.756000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.756000] hde: dma_intr: error=0x04 { DriveStatusError }
[17179580.756000] ide: failed opcode was: unknown
[17179580.772000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.772000] hde: dma_intr: error=0x04 { DriveStatusError }
[17179580.772000] ide: failed opcode was: unknown
[17179580.772000] hde: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.772000] hde: dma_intr: error=0x04 { DriveStatusError }
[17179580.772000] ide: failed opcode was: unknown
[17179580.772000] hde: DMA disabled
[17179580.772000] hdf: DMA disabled
[17179580.772000] PDC202XX: Primary channel reset.
[17179580.820000] ide2: reset: success
[17179580.832000] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.832000] hdg: dma_intr: error=0x04 { DriveStatusError }
[17179580.832000] ide: failed opcode was: unknown
[17179580.832000] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.832000] hdg: dma_intr: error=0x04 { DriveStatusError }
[17179580.832000] ide: failed opcode was: unknown
[17179580.848000] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.848000] hdg: dma_intr: error=0x04 { DriveStatusError }
[17179580.848000] ide: failed opcode was: unknown
[17179580.848000] hdg: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179580.848000] hdg: dma_intr: error=0x04 { DriveStatusError }
[17179580.848000] ide: failed opcode was: unknown
[17179580.848000] hdg: DMA disabled
[17179580.848000] hdh: DMA disabled
[17179580.848000] PDC202XX: Secondary channel reset.
[17179580.864000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179580.864000] hde: task_in_intr: error=0x04 { DriveStatusError }
[17179580.864000] ide: failed opcode was: unknown
[17179580.896000] ide3: reset: success
[17179580.896000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179580.896000] hde: task_in_intr: error=0x04 { DriveStatusError }
[17179580.896000] ide: failed opcode was: unknown
[17179580.932000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179580.932000] hdg: task_in_intr: error=0x04 { DriveStatusError }
[17179580.932000] ide: failed opcode was: unknown
[17179580.956000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179580.956000] hde: task_in_intr: error=0x04 { DriveStatusError }
[17179580.956000] ide: failed opcode was: unknown
[17179580.964000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179580.964000] hdg: task_in_intr: error=0x04 { DriveStatusError }
[17179580.964000] ide: failed opcode was: unknown
[17179580.988000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179580.988000] hde: task_in_intr: error=0x04 { DriveStatusError }
[17179580.988000] ide: failed opcode was: unknown
[17179580.988000] PDC202XX: Primary channel reset.
[17179581.008000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179581.008000] hdg: task_in_intr: error=0x04 { DriveStatusError }
[17179581.008000] ide: failed opcode was: unknown
[17179581.036000] ide2: reset: success
[17179581.040000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179581.040000] hdg: task_in_intr: error=0x04 { DriveStatusError }
[17179581.040000] ide: failed opcode was: unknown
[17179581.040000] PDC202XX: Secondary channel reset.
[17179581.088000] ide3: reset: success
[17179581.096000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179581.096000] hde: task_in_intr: error=0x04 { DriveStatusError }
[17179581.096000] ide: failed opcode was: unknown
[17179581.096000] end_request: I/O error, dev hde, sector 135202804
[17179581.096000] Buffer I/O error on device hde2, logical block 21510976
[17179581.124000] hdg: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179581.124000] hdg: task_in_intr: error=0x04 { DriveStatusError }
[17179581.124000] ide: failed opcode was: unknown
[17179581.124000] end_request: I/O error, dev hdg, sector 135202804
[17179581.124000] Buffer I/O error on device hdg2, logical block 21510976
[17179581.132000] hde: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17179581.132000] hde: task_in_intr: error=0x04 { DriveStatusError }
[17179581.132000] ide: failed opcode was: unknown
```

---

### Post by IntuitiveNipple on 2007-01-31
I've finally identified the cause of this bug and produced a fix in the form of a kernel patch. The bug applies to all kernels up to and including 2.6.20-rc7

The patch is available as an attachment to the bug report.

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77734](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77734)

dmesg will now show something similar to this:
```
[17179577.728000] hde: max request size: 128KiB
[17179577.744000] hde: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179577.744000] hde: cache flushes supported
[17179577.744000]  hde:
[17179577.748000]  partition 2: end (sector 135203039) beyond end of disk (sector 120103199)
[17179577.748000] 
[17179577.748000]  partition 3: start (sector 135203040) beyond end of disk (sector 120103199)
[17179577.748000]  partition 3: end (sector 238276079) beyond end of disk (sector 120103199)
[17179577.748000]  unable to read partition table
```

---

### Post by dfenwick on 2007-02-18
> **IntuitiveNipple said:**
> I've finally identified the cause of this bug and produced a fix in the form of a kernel patch. The bug applies to all kernels up to and including 2.6.20-rc7

The patch is available as an attachment to the bug report.

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77734](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77734)

dmesg will now show something similar to this:
```
[17179577.728000] hde: max request size: 128KiB
[17179577.744000] hde: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179577.744000] hde: cache flushes supported
[17179577.744000]  hde:
[17179577.748000]  partition 2: end (sector 135203039) beyond end of disk (sector 120103199)
[17179577.748000] 
[17179577.748000]  partition 3: start (sector 135203040) beyond end of disk (sector 120103199)
[17179577.748000]  partition 3: end (sector 238276079) beyond end of disk (sector 120103199)
[17179577.748000]  unable to read partition table
```

I've been following the investigation you did here.  I had similar problems on a recent install and my google search ended up here.  I have a Fasttrak100 IDE in my machine with 2x 160GB drives in RAID-0 in it.  My biggest difference is I was installing Fedora Core 6 on the box.  If I let FC6 partition my hard drives and then do an install, all disk writes worked fine during the installation, including creating the filesystem, which spreads group blocks everywhere on the drive.  I know the filesystem writes were fine during install.

After booting, however, the kernel would panic after a multitude of buffer read failures.  I haven't done any extensive kernel debugging on it, but I believe it's a similar problem.  If I partition the volume to fit to make sure all partitiions fit under the maximum size for a single disk (< 160GB) and then install, everything works fine.  I can then go back after the fact, create a new partition in the leftover space, and use it to my heart's content.

The GUI partitioning software for Fedora always crams the swapfile to the end of the drive.  My assumption (which is what led me to this page) is that it's trying to figure out some geometry for physical disks before doing anything with the root and swap partitions.  Since the geometry doesn't make sense from a physical perspective until dmraid is loaded, it goes through the same failures you were encountering and eventually panics the kernel (it's the boot volume).

---

