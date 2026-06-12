---
title: "New hard drive won't boot after first restart"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by qianian on 2012-11-02
Clean install from 12.04.01 live CD on OCZ Vertex Plus SSD hangs on ubuntu page on shutdown, then boots to grub error. Before the first shutdown, I got the following. How can I make this new hard drive run Ubuntu?

$ sudo parted /dev/sda unit s print
[sudo] password for qian:
Model: ATA OCZ VERTEX PLUS (scsi)
Disk /dev/sda: 468862128s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
1      2048s       462589951s  462587904s  primary                   boot
2      462591998s  468860927s  6268930s    extended
5      462592000s  468860927s  6268928s    logical   linux-swap(v1)

$ sudo fdisk -l

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

---

### Post by oldfred on 2012-11-03
Parted list looks ok, so why is fdisk saying table is invalid?

Was drive every in RAID before, or partitioned with gpt partitioning before? Usually if either case it will not even install.

Run this as sometimes it just gives better error messages.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Sometimes BIOS settings can be import also. Is BIOS in AHCI?
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

---

### Post by qianian on 2012-11-03
Thanks for responding.

Here are Grub Rescue and boot-repair outputs from previous trials. The only difference was I had used gparted to manually partition the new SSD, then used fsarchiver or partimage to restore my original separate /home and / drives. I'll run them again since the clean install might be different. The black grub rescue page behaves the same, though.

[http://paste.ubuntu.com/1314100](http://paste.ubuntu.com/1314100)
[http://paste2.org/p/2398880](http://paste2.org/p/2398880)

---

### Post by qianian on 2012-11-03
To answer your question about RAID, the device is new from the factory but I did partition it manually before. It wouldn't boot except the first time after install from a live partimage CD with option: boot existing Linux system.

It turns out after that first restart, boot-rescue can't see the OS on the disk. I had to run rescue immediately after restoring or installing to get the above paste.

SATA has been set to AHCI (there are no other options). I tried to update the firmware from OCZ but dos can't see the hard drive in AHCI mode.

When boot goes to the grub rescue prompt, it hangs for a moment on DHCP, then reads PXE-E53: No boot filename received.

Thanks again for your help.

---

### Post by oldfred on 2012-11-03
I do not know if empty extended partition or something else in partition table is the issue. Second report also had this:

> File descriptor 7 (pipe:[13070]) leaked on lvscan invocation. Parent PID 13795: bash

I generally prefer clean install to a new drive and copy /home data into /home. I might copy the /home before the install so the new install updates settings unless you have a lot of custom setting you do not want overwritten. Then copy it after install.

With SSD the Arch site suggests gpt partitioning. I use gpt and it does not really seem different once created, but does required an additional bios_grub partition. You cannot use image copies to copy data into a gpt partition as it has internal data also. But cp or rsync are fine for coping data.

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

---

### Post by qianian on 2012-11-03
I realized the clean install vs restored manual partition seemed to make no difference in my boot problem. I'm considering flashing my BIOS so I can update the SSD firmware. Do you think it's worth a try? Currently my BIOS doesn't offer IDE mode, which the firmware update needs to read the SSD.

Here's biosdecode:

$ sudo biosdecode
# biosdecode 2.11
VPD present.
	BIOS Build ID: 7OET24WW 
	Box Serial Number: L3A7295
	Motherboard Serial Number: VF11A775196
	Machine Type/Model: 89329WU
SMBIOS 2.4 present.
	Structure Table Length: 2386 bytes
	Structure Table Address: 0x000E0010
	Number Of Structures: 71
	Maximum Structure Size: 120 bytes
BIOS32 Service Directory present.
	Revision: 0
	Calling Interface Address: 0x000FDCA0
ACPI 2.0 present.
	OEM Identifier: LENOVO
	RSD Table 32-bit Address: 0xBF6BCA94
	XSD Table 64-bit Address: 0x00000000BF6BCAEC
PNP BIOS 1.0 present.
	Event Notification: Not Supported
	Real Mode 16-bit Code Address: E2E4:CCCF
	Real Mode 16-bit Data Address: 0040:0000
	16-bit Protected Mode Code Address: 0x000FB75E
	16-bit Protected Mode Data Address: 0x00000400

---

### Post by qianian on 2012-11-04
I successfully updated the BIOS from .iso on Lenovo's website. It didn't see anything to boot from so I clean installed Ubuntu, which booted fine the first time, then hung on the shutdown page. I Ctrl+Alt+F1 but no keystrokes would work on the login. Ctrl+Alt+Del gave "unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus socket: No such file or directory

New: on restart

error: unknown filesystem 
grub rescue > ls
(hd0) (hd0,msdos5) (hd0,msdos1)

whereas before BIOS update it only gave 
(hd0) (hd0,msdos1)(hd1)

Where hd1 was probably my external hard drive, now disconnected.

There's still no IDE compatibility option to try the SSD firmware update.

Please help -- it seems if I could complete shutdown instead of forcing, the disk might not be written in an unreadable state.

---

### Post by darkod on 2012-11-04
I haven't worked with OCZ SSDs, are you sure it needs IDE mode for firmware update? That sounds silly, SSDs are designed to make full benefit of AHCI in the first place. If they designed it for firmware update only in IDE mode that would be very stupid design. Not to mention that your board should have option for IDE mode, but that also depends on the boards and the manufacturer of the PC (if it's branded, they cut out almost everything from the bios).

In any case it looks like hardware issue, doesn't look related to ubuntu at all. It almost sounds like the SSD is not working as it should.

What happens if you boot with the cd in live mode and run both:
sudo parted -l
sudo fdisk -l

---

### Post by qianian on 2012-11-04
It may be silly but IDE is required according to the manufacturer's documentation and the resulting dos interface does not see any connected drive when I use AHCI: [http://www.ocztechnology.com/ssd_tools/OCZ_Vertex_Plus/](http://www.ocztechnology.com/ssd_tools/OCZ_Vertex_Plus/)

When I run the SSD from a clean install:

$sudo parted -l
Model: ATA OCZ VERTEX PLUS (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  237GB  237GB   primary                   boot
 2      237GB   240GB  3210MB  extended
 5      237GB   240GB  3210MB  logical   linux-swap(v1)


Model: WD My Passport 070A (scsi)
Disk /dev/sdb: 499GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  499GB  499GB  primary  ext3         boot


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: The partition's data region doesn't occupy the entire partition.   
Ignore/Cancel? i
Error: Can't have a partition outside the disk!                           

$ sudo fdisk -l

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c9cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   462589951   231293952   83  Linux
/dev/sda2       462591998   468860927     3134465    5  Extended
/dev/sda5       462592000   468860927     3134464   82  Linux swap / Solaris

Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders, total 975400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0789

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   975400959   487699456   83  Linux


Please let me know if I should reboot to get you the live disk results.

---

### Post by darkod on 2012-11-05
```
$sudo parted -l
Model: ATA OCZ VERTEX PLUS (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 237GB 237GB [COLOR="red"]primary boot[/COLOR]
2 237GB 240GB 3210MB extended
5 237GB 240GB 3210MB [COLOR="red"]logical linux-swap(v1)[/COLOR]


Model: WD My Passport 070A (scsi)
Disk /dev/sdb: 499GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 499GB 499GB [COLOR="Red"]primary ext3 boot[/COLOR]
```

Somehow it doesn't recognize the filesystem of sda1. Notice how it can see your external hdd, sdb1 is ext3, that sda5 is swap, but there is no filesystem recognized for sda1. Just that the partition is primary and it has the boot flag set.

From live mode (because it needs to be unmounted), try running fsck:
sudo fsck /dev/sda1

See if that finds and repairs something.

PS. And that's exactly what the grub rescue message says:
error: unknown filesystem

---

### Post by qianian on 2012-11-05
fsck from live CD always turns up endless lines of errors to either clear or fix. I'm going to try replacing the SSD in case this particular machine is defective. 

Is it possible this model is incompatible with my 5-year-old laptop? It doesn't seem to be a Linux problem.

---

