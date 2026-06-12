---
title: "Ubuntu 21.04 partition table"
date: 2021-05-03
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2021-05-03
I replaced 20.10 with a clean install  of 21.04 using a usb iso. Everthing seems to work fine except that I get a message "invalid partition table" when I first turn it on. I just bypass this by hitting "enter" and all goes well. During installation I did no partitioning just intending that 21.04 take up all the space except, of course, the bios.

Dell Latitude E7240
256 GB ssd.

Partition 1  Bios Boot
Partition 2  538 MB EFI System
Partition 3 Linux Filesystem  All the rest

I realize that 538 MB is nothing; however I don't like error messages. Maybe I can just delete partition 2??

---

### Post by Impavidus on 2021-05-03
Uefi or bios/legacy? Mbr or gpt partitioning? If the computer is from later than 2012, uefi is recommended. Dell computers tend to be well-behaved, even for the older uefi models. If uefi, you should use gpt partitioning, else it's your choice. The bios boot partition is only required on bios/legacy systems on a gpt partitioned drive, the efi partition is only required on an uefi system, but I've heard that the installer may create one anyway.

---

### Post by oldfred on 2021-05-03
Post actual partitions:
sudo parted -l
sudo fdisk -lu

---

### Post by s9032g@comcast.net on 2021-05-04
Legacy

sudo] password for stevengarland: 
Model: ATA SK hynix SC210 m (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   256GB   256GB   ext4

$ sudo fdisk -lu
Disk /dev/loop0: 55.45 MiB, 58142720 bytes, 113560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 162.87 MiB, 170778624 bytes, 333552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 218.99 MiB, 229629952 bytes, 448496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 64.77 MiB, 67915776 bytes, 132648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 51.04 MiB, 53522432 bytes, 104536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 32.27 MiB, 33841152 bytes, 66096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 65.1 MiB, 68259840 bytes, 133320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk model: SK hynix SC210 m
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B089188C-AC6E-4059-93F2-4E62B8F25FF7

Device       Start       End   Sectors  Size Type
/dev/sda1     2048      4095      2048    1M BIOS boot
/dev/sda2     4096   1054719   1050624  513M EFI System
/dev/sda3  1054720 500117503 499062784  238G Linux filesystem
stevengarland@stevengarland-Latitude-E7240:~$

---

### Post by oldfred on 2021-05-04
It shows gpt partitioning with an ESP and a bios_grub partition.
So could be UEFI boot or BIOS/CSM boot depending on which version of grub is installed.

Partition table looks ok, what does this show.
sudo gdisk -l /dev/sda

---

### Post by s9032g@comcast.net on 2021-05-04
Thanks

GPT fdisk (gdisk) version 1.0.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Model: SK hynix SC210 m
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): B089188C-AC6E-4059-93F2-4E62B8F25FF7
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  
   2            4096         1054719   513.0 MiB   EF00  EFI System Partition
   3         1054720       500117503   238.0 GiB   8300  
stevengarland@stevengarland-Latitude-E7240:~$

---

### Post by oldfred on 2021-05-04
Normally gdisk would show any errors.
That entry is typical correct gpt table.

Do you still have live installer plugged in?
Depending on how you made live installer, it does not use partition table, but has hybrid DVD/flash drive configuration. That typically does show error on partition table.

---

### Post by s9032g@comcast.net on 2021-05-05
THe live installer usb was unplugged before the first boot after installation. A message came up to do so.

Is there anything I can do to eliminate the error message?

Thanks

---

### Post by oldfred on 2021-05-05
Check this:
sudo grep -E -i "error|warning" /var/log/dmesg 

And then see if you can find the error in dmesg and if it tells more info.
Perhaps like this?
[FONT=monospace][COLOR=#000000]sudo grep -E -i "partition" /var/log/dmesg[/COLOR]
[/FONT]

---

### Post by s9032g@comcast.net on 2021-05-05
stevengarland@stevengarland-Latitude-E7240:~$ sudo grep -E -i "error|warning" /var/log/dmesg
[sudo] password for stevengarland: 
[    0.454995] kernel: i8042: Warning: Keylock active
[    0.468988] kernel: RAS: Correctable Errors collector initialized.
[    1.907998] kernel: EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro. Quota mode: none.

stevengarland@stevengarland-Latitude-E7240:~$ sudo grep -E -i "partition" /var/log/dmesg            No result

Sorry I don't know how to interpret this

---

### Post by oldfred on 2021-05-05
Do you have some sort of lock in UEFI settings to prevent changes?]
Check your manual.

---

### Post by s9032g@comcast.net on 2021-05-07
The solution to getting rid of the "invalid partition"message at boot was (On Dell):

In bios   change to UEFI and apply

Go to Advance Boot Options and disable the "enable legacy rom".   Apply

Enable Secure boot.   Apply

Exit


The seemingly extra partition is still there, but it is small.

---

