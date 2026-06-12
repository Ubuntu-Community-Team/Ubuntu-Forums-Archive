---
title: "Repeating partion failure in dual-boot installation"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by mmmpancakes on 2008-06-16
I’m having difficulty creating a dual-boot installation of Hardy Heron, specifically, with the partitioning phase of the install with a Live CD. 

I recently formatted my 150GB hard drive and reinstalled Windows XP. I’ve added all updates, defragged the HD several times, and ran chkdsk /f. When this didn’t work, I attempted to run Gparted from a Live CD in order to partition, and this failed as well. 

The moment I try to do either a guided or manual install, I get an error message that says the process failed. No other details, and I have no choice but to abort the installation.

Any ideas?

---

### Post by prshah on 2008-06-16
> **mmmpancakes said:**
> I’m having difficulty creating a dual-boot installation of Hardy Heron, specifically, with the partitioning phase of the install with a Live CD. 

I recently formatted my 150GB hard drive and reinstalled Windows XP. 
 I attempted to run Gparted from a Live CD in order to partition, and this failed as well. 



First, ensure that the BIOS option for "Boot sector virus protection" / "boot sector write protect" / "Boot sector protection" / "Virus protection" is turned off.

Second, gparted will not work with mounted (active) partitions. If you are trying to resize your existing partition using gparted, first right-click it, then choose "unmount". Then continue with your resize attempt.

If all else fails, from the live CD, open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

fdisk -l
dmesg | tail -30

```

---

### Post by mmmpancakes on 2008-06-16
Still no luck. Here's the output you requested. I'm currently in the live CD. Any help, from anyone, would be appreciated. This is getting frustrating. 

ubuntu@ubuntu:~$ fdisk -l dmesg | tail -30
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ dmesg | tail -30
[  147.986347] Bluetooth: RFCOMM TTY layer initialized
[  147.986350] Bluetooth: RFCOMM ver 1.8
[  150.634599] NET: Registered protocol family 17
[  152.995110] NET: Registered protocol family 10
[  152.996108] lo: Disabled Privacy Extensions
[  159.370541] [drm] Initialized drm 1.1.0 20060810
[  159.913876] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[  159.913994] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[  163.979517] [drm] Setting GART location based on new memory map
[  163.980615] [drm] Loading R200 Microcode
[  163.980686] [drm] writeback test succeeded in 1 usecs
[  169.568969] eth0: no IPv6 routers present
[  224.934142] JFS: nTxBlock = 4016, nTxLock = 32129
[  225.361897] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[  225.367971] SGI XFS Quota Management subsystem
[  225.688330] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
[  238.301389] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  238.542975] QNX4 filesystem 0.2.3 registered.
[  238.758528] cramfs: wrong magic
[  257.129055] intel_rng: Firmware space is locked read-only. If you can't or
[  257.129058] intel_rng: don't want to disable this in firmware setup, and if
[  257.129060] intel_rng: you are certain that your system has a functional
[  257.129062] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  263.895542] intel_rng: Firmware space is locked read-only. If you can't or
[  263.895546] intel_rng: don't want to disable this in firmware setup, and if
[  263.895547] intel_rng: you are certain that your system has a functional
[  263.895549] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  281.059222] [drm] Setting GART location based on new memory map
[  281.060362] [drm] Loading R200 Microcode
[  281.060433] [drm] writeback test succeeded in 2 usecs
ubuntu@ubuntu:~$

---

### Post by mmmpancakes on 2008-06-16
bump

---

### Post by mmmpancakes on 2008-06-16
Anyone?

---

### Post by prshah on 2008-06-17
> **mmmpancakes said:**
> 
ubuntu@ubuntu:~$ fdisk -l dmesg | tail -30
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ dmesg | tail -30
[  281.060433] [drm] writeback test succeeded in 2 usecs
ubuntu@ubuntu:~$

Your dmesg output seems irrelevant to this problem. However that point that you get _no output_ for "fdisk -l" means that it can't see your hard disk at all.

If you have a SATA HDD, check your BIOS options to use the SATA drive as "Legacy" or "IDE" or "Native". Toggle the SATA related options till you can see the drive in ubuntu.

NOTE: While usually changing these options should not cause any data loss, you do so at your own risk and responsibility.

Once ubuntu is installed, you can switch back to the original setting which was in the BIOS. Both ubuntu and windows will continue working fine.

---

### Post by Ognid on 2008-07-16
what if you can't change your drive's settings?

---

### Post by prshah on 2008-07-17
> **prshah said:**
> However that point that you get _no output_ for "fdisk -l" means that it can't see your hard disk at all.


My face is red: :redface:

Obviously you will not get any output for "fdisk -l", you will only get for ```
sudo fdisk -l
```

Apologies to OP and others; can OP post back with information for the above command?

---

