---
title: "Gutsy install hangs then freezes"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by Kzin on 2008-01-09
Hi there Ubuntu community,
I have been trying to install Gutsy on an Alienware Area51 laptop.  The install partitions the disc, copies all the files, closes the progress window and hangs.  There is a /target on the desktop (see attached screenshot, I assume it is the target mount point on the drive).
You can see the terminal open down there, it is just tailing the kern.log in /var/log.  The spot at which it is hung is...
```
Jan  9 09:29:35 ubuntu kernel: <8e <3< Q
```
After a while, the /target on the desktop disappears, and the dmesg goes on to say...
```
Jan  9 09:45:23 ubuntu kernel: [ 2172.832889] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan  9 09:45:23 ubuntu kernel: [ 2172.832898] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
Jan  9 09:45:23 ubuntu kernel: [ 2172.832906] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
Jan  9 09:45:23 ubuntu kernel: [ 2172.832913] end_request: I/O error, dev sr0, sector 1316140
Jan  9 09:45:23 ubuntu kernel: [ 2172.832919] Buffer I/O error on device sr0, logical block 329035
Jan  9 09:45:23 ubuntu kernel: [ 2173.150003] SQUASHFS error: sb_bread failed reading block 0xa0176
Jan  9 09:45:23 ubuntu kernel: [ 2173.150011] SQUASHFS error: Unable to read cache block [2805d9f1:14bc]
Jan  9 09:45:23 ubuntu kernel: [ 2173.150217] SQUASHFS error: Fail reading block list [2805d9f1:14bc]

```
Another interesting point to note, when it is first mounting the hdd, dmesg says...
```
Jan  9 16:58:43 ubuntu kernel: [  241.036746] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
Jan  9 16:58:52 ubuntu kernel: [  249.767032] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
Jan  9 16:58:54 ubuntu kernel: [  252.153125] NTFS driver 2.1.28 [Flags: R/O MODULE].
Jan  9 16:58:54 ubuntu kernel: [  252.239388] QNX4 filesystem 0.2.3 registered.
Jan  9 16:58:54 ubuntu kernel: [  252.293539] cramfs: wrong magic
Jan  9 16:58:55 ubuntu kernel: [  252.380331] kjournald starting.  Commit interval 5 seconds
Jan  9 16:58:55 ubuntu kernel: [  252.380341] EXT3-fs: mounted filesystem with ordered data mode.
Jan  9 16:58:55 ubuntu kernel: [  253.046273] cramfs: wrong magic
Jan  9 16:58:55 ubuntu kernel: [  253.055857] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.055868] sda2: rw=0, want=4, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.055873] EXT3-fs: unable to read superblock
Jan  9 16:58:55 ubuntu kernel: [  253.059364] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.059374] sda2: rw=0, want=66, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.059379] isofs_fill_super: bread failed, dev=sda2, iso_blknum=16, block=32
Jan  9 16:58:55 ubuntu kernel: [  253.063117] SQUASHFS error: Can't find a SQUASHFS superblock on sda2
Jan  9 16:58:55 ubuntu kernel: [  253.066342] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.066350] sda2: rw=0, want=4, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.066355] EXT2-fs: unable to read superblock
Jan  9 16:58:55 ubuntu kernel: [  253.069758] FAT: bogus number of reserved sectors
Jan  9 16:58:55 ubuntu kernel: [  253.069767] VFS: Can't find a valid FAT filesystem on dev sda2.
Jan  9 16:58:55 ubuntu kernel: [  253.073046] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.073058] sda2: rw=0, want=72, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.073067] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.073070] sda2: rw=0, want=128, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.076339] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.076348] sda2: rw=0, want=18, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.076657] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 8, size 1024)
Jan  9 16:58:55 ubuntu kernel: [  253.076852] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.076856] sda2: rw=0, want=130, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.077072] ReiserFS: sda2: warning: sh-2006: read_super_block: bread failed (dev sda2, block 64, size 1024)
Jan  9 16:58:55 ubuntu kernel: [  253.077076] ReiserFS: sda2: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda2
Jan  9 16:58:55 ubuntu kernel: [  253.080556] attempt to access beyond end of device
Jan  9 16:58:55 ubuntu kernel: [  253.080564] sda2: rw=0, want=8, limit=2
Jan  9 16:58:55 ubuntu kernel: [  253.080572] XFS: SB read failed
Jan  9 16:58:55 ubuntu kernel: [  253.083987] FAT: bogus number of reserved sectors
Jan  9 16:58:55 ubuntu kernel: [  253.083996] VFS: Can't find a valid FAT filesystem on dev sda2.
Jan  9 16:58:55 ubuntu kernel: [  253.093828] attempt to access beyond end of device

```
etc.  See attached for the full kern.log (gzipped due to forum size restriction on .txt)
I have noted that similar errors exist in the following threads...
[http://ubuntuforums.org/showthread.php?t=518014](http://ubuntuforums.org/showthread.php?t=518014)
[http://ubuntuforums.org/showthread.php?t=650511](http://ubuntuforums.org/showthread.php?t=650511)
Neither of which have come to a solid resolution.  Restarting the install produces exact replication of symptoms.  Using managed/use full disc in safe graphics mode. Install disc is aok, used for installs before and after.  
Output of fdisk -l
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51210ebf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```
Output of mounting the drive!!!  (After install hangs then reboot.  Or you can wait for it to finish hanging and it actually freezes)  All the data is there!!
```
ubuntu@ubuntu:/mnt$ sudo mount /dev/sda1 ./hdd/
ubuntu@ubuntu:/mnt$ ls
hdd
ubuntu@ubuntu:/mnt$ cd hdd
ubuntu@ubuntu:/mnt/hdd$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
ubuntu@ubuntu:/mnt/hdd$ cd
```
Any help appreciated, my guess is that perhaps this computer is having trouble writing GRUB to the superblock or something.  I know lilo lets you write to the MBR, superblock and somewhere else, does grub have similar installation abilities?  Is there a way to test that theory?  Maybe its not even sound.  What does that specific kernel output mean where it hangs?  What is the next step after copying the files?
So, if anyone has the solution to this, please let me know.  I have included as much info as I can think of.
```
Case: Area-51m Case with 15.4" WideSXGA+ 1680x1050 LCD Display - Saucer Silver, 
Processor: Intel® Pentium® 4 Processor w/ HT Technology 3.4GHz 800MHz FSB w/ 512KB Cache, 
Motherboard: SiS648FX + SiS963L AGP8X Chipset, 
Memory: 1024MB DDR PC-3200 - 2x512 SO-DIMMs, 
Video Card: AREA-51M NVIDIA 5700FXGO WITH 128MB MODULE, 
Sound Card: Sound-Blaster Pro Compatible 3D Audio, 
Hard Drive: Hitachi 60GB 7200 RPM ATA100 with 8MB Cache
```

Update: Passed all Hitachi HDD tests.  HDD seems fine.  Memory next.
Update: Memory fine.  Wonder what else, perhaps I'll test CPU and (potentially) the CD drive?
Update: CPU and CD Drive fine.
Update: Same symptoms using the manual partition method.

---

### Post by thisllub on 2008-01-09
Did you try 
noapic nolapic ACPI=off   ??

I can't get any Linux to work on my laptop without those.

---

### Post by Kzin on 2008-01-10
> **thisllub said:**
> Did you try 
noapic nolapic ACPI=off   ??

I can't get any Linux to work on my laptop without those.

Tried what you suggested, did not work (same symptoms).  Thank you tho.

Any others?

---

### Post by kneehighspy on 2008-01-26
i'm having issues installing ubuntu 7.10 (from the 7.10 install dvd) on my alienware m9750.  i can install with no issues if i do not select to config a wireless network during install.

but when i do select to config a wireless network, my install gets to the point of installing the software / apps, gets to 85% then hangs everytime after it has installed some brittany application, i can't remember exactly what it's called, i'll try again and re-post what it is.

but if i don't select to config a wireless network during install (again from the 7.10 install dvd), it will install completely with no issues, of course i need to setup my video drivers.

any ideas?

thanks

---

### Post by Kzin on 2008-02-03
I will try an install w/out network...

---

