---
title: "Trouble Getting Into Ubuntu after Accidentaly Restoring EFI Partition"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by daniel181 on 2014-09-14
Hello everyone! Second time posting here for help. 

So Friday night I was playing around with GParted and accidentally deleted several partitions. One of the was an unnamed. After doing this, I restarted and I was greeted with the "Reboot and select proper boot device". Knowing I had screwed up, I looked up the  problem and arrived to the conclusion that I had nuked the EFI  partition that basically held the boot loader. One of the proposed ways to fix it was to use the Windows Boot Repair option for an installation disk. This morning I tried that option and it worked! I can now boot into Windows. 

After doing that,  I booted into a live CD and I tried to reinstall GRUB2 via the Boot Repair guide over at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
This is where my problem begins. 
I can't seem to get GRUB to show up as my default bootloader.

I followed another guide that said I needed to point at the bootloader from within Windows by using 
```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```
But even this doesn't seem to work as I am greeted with the following: 

```

Microsoft Windows [Version 6.3.9600]
(c) 2013 Microsoft Corporation. All rights reserved.

C:\WINDOWS\system32>bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
The parameter is incorrect.


```

Running bcdedit returns the following:

```

C:\WINDOWS\system32>bcdedit

Windows Boot Manager
--------------------
identifier              {bootmgr}
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
integrityservices       Enable
default                 {current}
resumeobject            {cbbe29da-23e7-11e4-9d02-bbb0e4fcb58b}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \WINDOWS\system32\winload.efi
description             Windows 8.1
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {cbbe29d8-23e7-11e4-9d02-bbb0e4fcb58b}
integrityservices       Enable
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \WINDOWS
resumeobject            {cbbe29da-23e7-11e4-9d02-bbb0e4fcb58b}
nx                      OptIn
bootmenupolicy          Standard
The parameter is incorrect.

C:\WINDOWS\system32>

```

I am at a loss of how I could get around this issue, but more importantly, how I can get GRUB2 as my bootloader so I can get into Ubuntu Partition. Any help is appreciated. Thank you for your time.

[U][B]ADDITIONAL INFO


[/B][/U]Running the command efibootmgr -v yields me the following,
```


BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0004,2003,2001,2002
Boot0000* Windows Boot Manager    HD(4,96800,32000,d5769c5b-3c38-11e4-9237-c832b0e56206)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...\................
Boot0001* UEFI: Network Card     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(202564958e96,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: Network Card     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(202564958e96,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* UEFI: M4-CT256M4SSD2    ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000HD(1,96800,32000,d5769c5b-3c38-11e4-9237-c832b0e56206)..BO
Boot0004* ubuntu    HD(1,96800,32000,d5769c5b-3c38-11e4-9237-c832b0e56206)File(\EFI\ubuntu\grubx64.efi)
Boot0005* UEFI: TSSTcorp CDDVDW SU-208FB    ACPI(a0341d0,0)PCI(1f,2)03120a000500ffff0000CD-ROM(1,76991,1240)..BO
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


```

FDisk returns: 

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4a6f69c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   500118191   250059095+  ee  GPT


```

I ran GDisk and it returned me this:

```


GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 5657A54D-73E9-4B33-8700-A8E287822B16
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 879213 sectors (429.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          616448          821247   100.0 MiB   EF00  
   2         1083392       395257855   188.0 GiB   0700  Basic data partition
   3       395257856       500117503   50.0 GiB    8300  


```

The third partition is where Ubuntu is installed the 100MB partition is the EFI partition and the second one is Windows.

---

### Post by ubfan1 on 2014-09-14
Do you actually have the /EFI/ubuntu directory in the EFI partition, and does it contain the grubx64.efi.  Is secure boot off (since if it is on, you would need to be booting shimx64.efi instead of grubx63.efi)? Can you use the efi menu to select the device/os and select ubuntu to boot (Some machines you might have to seled the HDD, then a second window pops up to select ubuntu vs. Windows.)?

---

### Post by daniel181 on 2014-09-14
> **ubfan1 said:**
> Do you actually have the /EFI/ubuntu directory in the EFI partition, and does it contain the grubx64.efi?  
This I'm not sure about. How can I confirm this? The EFI partiton was acutally created by the Windows Boot Repair utility from the install USB. I had been planning on manually doing it, but my attempts to do it were not succesful.

> **ubfan1 said:**
>  Is secure boot off (since if it is on, you would need to be booting shimx64.efi instead of grubx63.efi)? 
Yes, it is off. 

> **ubfan1 said:**
> 
Can you use the efi menu to select the device/os and select ubuntu to boot (Some machines you might have to seled the HDD, then a second window pops up to select ubuntu vs. Windows.)? 
I cannot. It immediately boots into Windows.

---

### Post by westie457 on 2014-09-14
Have you gone into the Power options for Windows and disabled the Fastboot setting?
Whether you have or not could you boot your computer using the installation media. Go here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and take the second option.
Do not attempt repairs just yet. Take the option to create a Boot report and post the resulting link here.
We should then be able give the relevant advice.

Thank you.

---

### Post by ubfan1 on 2014-09-14
In the UEFI Settings/BIOS, you should have a boot speed parameter which should be set to something other than 0 or fast.  This should give you a chance to hit a function key like F12 (varies by machine, check your manual), to bring up the efi boot menu to allow device  and OS selection.  If you time things just right, you can still use the function keys even without the extra time, but that is really tricky sometimes, like having to hold down the key before power on.  Anyway, you should be able to invoke it one way or another, but it sounds like it will only have the Windows bootloaders.
  You can look at the EFI partition's FAT32 filesystem by just mounting it when running the live media.  Usually mounts are done under the /mnt directory, just make a suitable directory there for the mount target:  sudo mkdir -p /mnt/tmp     for instance.  Then mount the EFI partition
sudo mount -tvfat /dev/sda1 /mnt/tmp
Now look there: ls /mnt/tmp
Any ubuntu directory?  The installer should create it when installing grub (in  UEFI mode), and make a nvram entry to boot it.  The only other file needed in the /EFI/ubuntu directory other than the grubx64.efi is a grub.cfg file, which can be a 3 line stub which brings in the maintained grub.cfg file from /boot/grub.  Possible to do it all yourself, but much easier to let the installer do it.  Another trick is to put a copy of grubx64.efi into /EFI/Boot/bootx64.efi (renamed to bootx64.efi), this may be tried when a nvram entry fails, but every machine may be different.

---

### Post by fantab on 2014-09-15
> I tried to reinstall GRUB2 via the Boot Repair
Post the 'bootinfo summary' url.

When you ran boot-repair did you go to 'Advanced options' -> 'Grub location' and set it to EFI system partition?

---

