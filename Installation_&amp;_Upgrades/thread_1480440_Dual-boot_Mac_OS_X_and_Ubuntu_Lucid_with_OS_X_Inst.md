---
title: "Dual-boot Mac OS X and Ubuntu Lucid with OS X Installed First"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by lancerocke on 2010-05-11
Was wondering how to do this. I was trying to do achieve this from looking at different guides, but I haven't had any luck.
I am on a custom PC, with dual screens; one LCD, and one CRT, from which I installed OS X 10.5.6 from a retail DVD.

I installed OS X first, because I needed to format my HDD to use GUID partition table, because you can't install from a retail DVD without using GUID. Once OS X was installed, I partitioned my hard-drive into 4 partitions from the OS X disk utility. These partitions were HFS. I then used the Ubuntu Lucid x64 Live disk to format the 3 nre HFS partitions to use ext4, for two of them, and one swap. I installed Ubuntu as normal.

I re-booted, and GRUB recognized my OS X instillation, so I tried to boot into it. It went into OS X, but with some major problems. My LCD screen was going haywire, but my CRT seemed to be working, but it took on my LCD's screen resolution and place as the main screen.

I thought my OS X instillation was badly damages, so with Ubuntu still installed on the other partitions, I re-installed OS X, which I am on now.

I want to know how to boot back into Ubuntu, while still having the option to boot into OS X.

Thanks in advance for any help.

---

### Post by srs5694 on 2010-05-11
The moderators here frown upon discussions of OS X installed on PC hardware, since this violates Apple's EULA. You may therefore need to ask your question elsewhere, to the extent that you need OS X-centric advice.

At least part of the answer to your question, though, is Ubuntu-centric. Specifically, you need to get Ubuntu to boot by using the Ubuntu install disc or a tool such as the [Super GRUB Disk.](http://www.supergrubdisk.org/) Once Ubuntu is booted, you should:


[list=1]
[*]Back up your MBR's boot loader by typing "sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1" at a text-mode shell. This creates a copy of the current boot loader in a file called /boot/chameleon.mbr. (Note: Although you used GPT, you've still got an MBR, which contains a boot loader and an MBR partition data structure with a single protective partition to keep GPT-unaware tools from messing with the disk.)
[*]Re-install GRUB by typing "sudo grub-install /dev/sda". This wipes out whatever is in the MBR right now, hence the need for the backup in the first step. Alternatively, you can try installing to the Ubuntu boot partition by typing "sudo grub-install /dev/sda3" (or whatever the Ubuntu's installation or /boot partition is). This doesn't always work, though.
[/list]


If you install GRUB to the MBR, you'll be back to where you started, and you'll need to reconfigure GRUB to boot your other OS in some other way. If you can get GRUB to install to the boot sector of your Ubuntu installation, though, some boot loaders will detect GRUB and give you the option to boot it. Sometimes GRUB Legacy works better than GRUB 2 in this respect. (Ubuntu 9.10 and 10.04 use GRUB 2 by default, but you can replace them with GRUB Legacy.)

One other point: GRUB 2 works best on GPT disks if you give it a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) This can be quite small (a few tens of kilobytes), so you should be able to find room for it one way or another.

Generally speaking, GRUB can be set to boot another OS by redirecting its boot process to another partition's boot loader. This is how GRUB boots Windows. Here's a typical Windows installation:

```

menuentry "Windows" {
set root=(hd0,3)
chainloader +1
}

```

Similar configurations work for other OSes with their own boot loaders, such as FreeBSD. Sometimes it's helpful to chain-load to a dd backup of another OS's boot loader, rather than to a partition; for instance, you could specify:

```

set root=(hd0,2)
chainloader (hd0,3)/boot/dd-backup.mbr +1

```

I *think* the above will work, depending of course on partition numbers and filenames, but I'm not positive of that; I don't have any exact analogs in GRUB 2 among my systems at the moment, although I do have one for GRUB Legacy to boot a Solaris setup.

---

### Post by lancerocke on 2010-05-11
[edit]WOW, i really appreciate your detailed reply.
I'm going to follow your instructions the best I can.
Thank you much

---

### Post by lancerocke on 2010-05-11
I'm getting an error message
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

danny@danny-desktop:~$ sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1[sudo] password for danny: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.2825e-05 s, 15.6 MB/s
danny@danny-desktop:~$ sudo grub-install /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
danny@danny-desktop:~$ sudo grub-install /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
danny@danny-desktop:~$ 

```
is this because my partition table is 'GUID'?
im writing this from my ubuntu install, booted using Super Grub Disk

---

### Post by srs5694 on 2010-05-11
Try creating a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) and see if that helps. (In addition to the site to which I've just linked, you might check out the page for my [GPT fdisk.](http://www.rodsbooks.com/gdisk/) Particularly if you're familiar with Linux fdisk, GPT fdisk makes it easy to create a BIOS Boot Partition -- just create a partition of 35KiB to 1MiB of type EF02.) If that's not possible, use the --force option to grub-install, or switch from GRUB 2 to GRUB Legacy (uninstall the grub-pc package and install grub). If you switch to GRUB Legacy, though, you may run into other problems, since it's not currently configured at all for this system, so it's entirely possible that it will do something unexpected.

---

### Post by lancerocke on 2010-05-12
> **srs5694 said:**
> The moderators here frown upon discussions of OS X installed on PC hardware, since this violates Apple's EULA. You may therefore need to ask your question elsewhere, to the extent that you need OS X-centric advice.

At least part of the answer to your question, though, is Ubuntu-centric. Specifically, you need to get Ubuntu to boot by using the Ubuntu install disc or a tool such as the [Super GRUB Disk.](http://www.supergrubdisk.org/) Once Ubuntu is booted, you should:


[list=1]
[*]Back up your MBR's boot loader by typing "sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1" at a text-mode shell. This creates a copy of the current boot loader in a file called /boot/chameleon.mbr. (Note: Although you used GPT, you've still got an MBR, which contains a boot loader and an MBR partition data structure with a single protective partition to keep GPT-unaware tools from messing with the disk.)
[*]Re-install GRUB by typing "sudo grub-install /dev/sda". This wipes out whatever is in the MBR right now, hence the need for the backup in the first step. Alternatively, you can try installing to the Ubuntu boot partition by typing "sudo grub-install /dev/sda3" (or whatever the Ubuntu's installation or /boot partition is). This doesn't always work, though.
[/list]


If you install GRUB to the MBR, you'll be back to where you started, and you'll need to reconfigure GRUB to boot your other OS in some other way. If you can get GRUB to install to the boot sector of your Ubuntu installation, though, some boot loaders will detect GRUB and give you the option to boot it. Sometimes GRUB Legacy works better than GRUB 2 in this respect. (Ubuntu 9.10 and 10.04 use GRUB 2 by default, but you can replace them with GRUB Legacy.)

One other point: GRUB 2 works best on GPT disks if you give it a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) This can be quite small (a few tens of kilobytes), so you should be able to find room for it one way or another.

Generally speaking, GRUB can be set to boot another OS by redirecting its boot process to another partition's boot loader. This is how GRUB boots Windows. Here's a typical Windows installation:

```

menuentry "Windows" {
set root=(hd0,3)
chainloader +1
}

```

Similar configurations work for other OSes with their own boot loaders, such as FreeBSD. Sometimes it's helpful to chain-load to a dd backup of another OS's boot loader, rather than to a partition; for instance, you could specify:

```

set root=(hd0,2)
chainloader (hd0,3)/boot/dd-backup.mbr +1

```

I *think* the above will work, depending of course on partition numbers and filenames, but I'm not positive of that; I don't have any exact analogs in GRUB 2 among my systems at the moment, although I do have one for GRUB Legacy to boot a Solaris setup.thanks
how do i restore after i've done 'sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1'?

---

### Post by srs5694 on 2010-05-12
> **lancerocke said:**
> thanks
how do i restore after i've done 'sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1'?

The point of that is to chain-load to the file rather than to boot using the original MBR. It's not always necessary, but sometimes it is. Alternatively, you can reverse the if= and of= terms to restore the original MBR backup to the disk; however, this will wipe out your GRUB installation if you put it in the MBR.

---

### Post by lancerocke on 2010-05-22
> **srs5694 said:**
> The point of that is to chain-load to the file rather than to boot using the original MBR. It's not always necessary, but sometimes it is. Alternatively, you can reverse the if= and of= terms to restore the original MBR backup to the disk; however, this will wipe out your GRUB installation if you put it in the MBR.so 
```
sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1
```
then
```
sudo grub-install --force /dev/sda5
```
then edit /boot/grub/grub.cfg:
```
set root=(hd0,1)
chainloader (hd0,5)/boot/chameleon.mbr +1
```
?
```
danny@danny-desktop:~$ sudo fdisk -l
[sudo] password for danny: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd246ec1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20267   162793472   af  HFS / HFS+
/dev/sda2           20267       40534   162794496    7  HPFS/NTFS
/dev/sda3           40534       60802   162796544    5  Extended
/dev/sda5           40535       48178    61395968   83  Linux
/dev/sda6           48178       58312    81396736   83  Linux
/dev/sda7           58312       60802    20000768   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6b5bf83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77826   625128448    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c09cb02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      121602   976759808    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06ffe2fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38914   312567804    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         488     3913727+  ee  GPT
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 1) logical=(0, 0, 2)
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(487, 60, 21)

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         978     7847935   ee  GPT
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 254, 63) logical=(0, 0, 2)
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(977, 5, 51)
danny@danny-desktop:~$ 

```
?

---

### Post by srs5694 on 2010-05-22
> **lancerocke said:**
> so 
```
sudo dd if=/dev/sda of=/boot/chameleon.mbr bs=512 count=1
```then
```
sudo grub-install --force /dev/sda5
```

Yes, although this configuration relies on another boot loader in the MBR that's capable of chain-loading GRUB on /dev/sda5. In this case, the dd backup will be for emergency use only.

> then edit /boot/grub/grub.cfg:
```
set root=(hd0,1)
chainloader (hd0,5)/boot/chameleon.mbr +1
```?

If you put GRUB on /dev/sda5, it shouldn't be necessary to create this GRUB entry, since it'll just re-start the boot loader in the MBR.

I'm cutting big chunks from the below to highlight a problem....

> ```
danny@danny-desktop:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38914   312567804    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         488     3913727+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         978     7847935   ee  GPT

```?

You got "GPT... detected on..." messages for three disks -- /dev/sde, /dev/sdf, and /dev/sdg. The messages for /dev/sdf and /dev/sdg seem fine, since these disks have 0xEE (EFI GPT) partitions. The message for /dev/sde, though, indicates a problem: The MBR contains a single 0x07 (NTFS) partition. Either the MBR table is incorrect or the MBR table is correct and there's stray GPT data from a previous use of the disk as GPT. Either way is asking for trouble.

I recommend you download and install my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program and run gdisk on /dev/sde. It will probably inform you that it's found conflicting MBR and GPT data, and ask you which to use. Check out both of them on subsequent runs and decide which one is the correct partition table. After checking each way, exit by typing 'q' at a command prompt. *Do not exit by typing 'w'!* Then:


[list]
[*]If the GPT side is correct, launch gdisk on /dev/sde, tell it to use the GPT side, and save the partition table via the 'w' command.
[*]If the MBR side is correct, type "sudo sgdisk --zap /dev/sde". This procedure will erase the invalid old GPT data, leaving the MBR data intact. Alternatively, you can use gdisk and the 'z' option on the experts' menu -- but be sure to answer 'N' to the question about wiping out the MBR!
[/list]

---

### Post by lancerocke on 2010-05-23
i resolved this by not trying to kill grub, but making it work for me.
I'm using it now, instead of trying to use chameleon by default. chameleon still doesn't see my Linux install, but grub sees, and boots snow leopard after edits.
grub did have os x entries, but they we're long and complicated, and made os x boot with gui problems.
my os x boot entry:
```
menuentry "Mac OS X: Snow Leopard" --class macosx {
  set root=(hd0,1)
  multiboot /boot
}
```

---

