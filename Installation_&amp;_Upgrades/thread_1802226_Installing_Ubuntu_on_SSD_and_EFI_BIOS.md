---
title: "Installing Ubuntu on SSD and EFI BIOS"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by zoff_ita on 2011-07-11
Hi,
I recently bought a new computer using EFI BIOS (MB: ASUS P8P67-M) and SSD (ATA Corsair Force 3).

I can boot a live CD and install ubuntu but i can't boot, in any way, the installation.

Do I need to do something particular during installation?
Which bootloader should I use? Is grub2 compatible?
How I should configure the bootloader?
Is there any guide about this?

Any suggestion is appreciated!

Regards,
-zoff-

PS: Side-effect: after installing windows, ubuntu installer can't recognize GPT partions created and sees disk as empty and with no partition even if win is working fine.

---

### Post by lmarmisa on 2011-07-11
Hi Zoff,

[GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table") is a new standard for partition tables of devices that will substitute to MS-DOS / MBR in the future and is mandatory if your hard disk is bigger than 2 Gbytes. I think that this is not your case because your SSD is 120 GBytes.

The experts say that GPT is not a problem for Ubuntu but I have read a lot of troubles about it in the forums.

I would recommend to define a MS-DOS table partition in your SDD and then repeat your Ubuntu installation. Use Gparted and Device -> Create Partition Table.

Best regards,

Luis

---

### Post by srs5694 on 2011-07-11
No matter the disk size, Windows *requires* GPT on its boot disk when booting from a UEFI-based computer. Thus, if the computer is dual-booting with Windows in UEFI mode, the disk *must* use GPT.

That's a big "if," though; many (perhaps all) current UEFI-based x86-64 computers ship with a BIOS compatibility layer that enables the computer to boot in BIOS mode as well as in UEFI mode.

I'm not really sure what's going on in your case, zoff_ita. I recommend that you boot with the Ubuntu installer in "try it now" mode, or use some other Linux emergency disk, and type the following three commands:

```

sudo fdisk -lu /dev/sda
sudo parted /dev/sda print
dmesg | grep EFI

```

If you've got more than one disk, repeat the first two commands for each one. Post the results of the first two commands here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to preserve legibility. You needn't post the entire output of the dmesg command; just note whether it produces anything at all. On an EFI system, it will produce quite a few lines like the following:

```
[    0.000000] Command line: BOOT_IMAGE=atapi0:\EFI\ELILO\bzImage-2.6.39 root=/dev/seeker/u1104  reboot=a,w ro
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000048000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000048000-0x0000000000097000) (0MB)

```

These memory range lines continue on for quite a while. On a BIOS-based system (including one with a UEFI booting in BIOS compatibility mode), you'll see nothing, except possibly an accidental hit because of some other word that includes the string "EFI".

From this output, I'm trying to figure out how your disk is currently partitioned, and therefore how Windows is using the computer, and whether the Ubuntu installer is seeing the computer as BIOS-based or UEFI-based. I may then be able to offer a recommendation, or I may need to see more commands' outputs before offering a recommendation.

As to GPT's problems with Ubuntu, my observation is that most of these problems relate to users' unfamiliarity with GPT. The desirability of a [url=http://en.wikipedia.org/wiki/BIOS_Boot_partition]BIOS Boot Partition[/quote] on BIOS-based computers, in particular, can be an issue. There can also be cross-OS issues, such as Windows' inability to boot from GPT on a BIOS-based computer. Note that Windows ties the partition table type quite firmly to the firmware type -- BIOS to MBR, UEFI to GPT. Linux is much more flexible on this score. If you know what you're doing, GPT works just as well as, if not better than, MBR, at least on a Linux-only installation. When dual-booting Linux with Windows in UEFI mode, GPT is a must.

---

### Post by zoff_ita on 2011-07-12
Thanks for replies.

ATM I can't boot LiveCD in UEFI mode, it simply try booting on disk...

If I boot in compatibility mode LiveCD here the outputs:
```
$ sudo fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9cfed527

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   122882047    61337600    7  HPFS/NTFS

```

```
$ sudo parted /dev/sda print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? Yes                                                               
Model: ATA Corsair Force 3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


```

```
$ dmesg | grep EFI

```

Now I'm in the case described in post-scriptum, where I installed win7 and Ubuntu installer can't detect GPT.

---

### Post by srs5694 on 2011-07-12
The partition table problem is because your disk is an MBR disk with leftover GPT data. Perhaps you installed Ubuntu in UEFI mode, which used GPT, and then you ran the Windows installer in BIOS mode, which used MBR and overwrote the GPT's "protective MBR" (part of the GPT data structures), but not the rest of the GPT data structures. It's also possible that the disk was once used in a Mac, which uses GPT by default. Either way, the disk is technically an MBR disk, but the leftover GPT data confuses libparted and most tools based on it, such as parted and the Ubuntu installer. The result is typically that these libparted-based tools claim that the disk is empty.

The solution to this immediate problem is to erase the old GPT data; however, you should only do this if you realize that you'll then have a disk with nothing but the two NTFS partitions shown by fdisk. If you've got any important data in GPT partitions, you should try to recover those data first. This task will most likely be difficult, since the NTFS partitions may well overlap the non-NTFS partitions you want to recover. If you want to attempt such a recovery, it's possible that [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) will be useful to recover whole partitions, since it looks like the NTFS partitions don't fill the whole disk; or you might need to use [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) to do a file-level recovery.

If you don't care about recovering GPT data, you should wipe the leftover GPT data structures. The easiest way to do this is to use my [FixParts](http://www.rodsbooks.com/fixparts/) program; launch it, tell it to wipe the GPT data when it asks about this, and then type "q" to quit without changing the MBR data structures. After you do this, the Linux installer should see the MBR partitions and enable you to proceed with installation.

---

### Post by zoff_ita on 2011-07-12
I have no important data on the disk... It's the first installation.

What's the best way to erase the GPT data? I could remove all partition too, I would lose only few hours for reinstalling and reconfiguring windows.

Can you tell me what to do exactly?

---

### Post by srs5694 on 2011-07-12
> **zoff_ita said:**
> What's the best way to erase the GPT data?

As I said:

[quote=srs5694]If you don't care about recovering GPT data, you should wipe the  leftover GPT data structures. The easiest way to do this is to use my [FixParts]("http://www.rodsbooks.com/fixparts/")  program; launch it, tell it to wipe the GPT data when it asks about  this, and then type "q" to quit without changing the MBR data  structures. After you do this, the Linux installer should see the MBR  partitions and enable you to proceed with installation. [/quote]

---

### Post by zoff_ita on 2011-07-13
It worked like a charm!

Thank you!

Installer saw partitions and installed ubuntu correctly.

Now I can boot it!

---

### Post by alphaamanitin on 2011-07-14
Do you have any graphical errors with your install of Ubuntu in UEFI booting mode?  Mine installed correctly but the graphic errors make it impossible to use.  I admit though I have not had the time to do what srs5694 suggested for me.

AlphaA

---

### Post by srs5694 on 2011-07-14
It appears that zoff_ita is *not* booting in UEFI mode, so any graphical problems s/he does or does not have aren't relevant to your problems in UEFI mode, alphaamanitin.

---

### Post by ratcheer on 2011-07-14
> **lmarmisa said:**
> Hi Zoff,

The experts say that GPT is not a problem for Ubuntu but I have read a lot of troubles about it in the forums.



I am using GPT on two systems with four Ubuntu installations - no troubles, at all.

Tim

---

