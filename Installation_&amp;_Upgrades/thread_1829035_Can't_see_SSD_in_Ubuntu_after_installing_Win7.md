---
title: "Can't see SSD in Ubuntu after installing Win7"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by foilboy on 2011-08-20
Hi,

I am trying to build a shiny new desktop that dual boots Windows 7 and Ubuntu, but having some trouble.  I have two hard drives, a 60GB SSD and a 2TB HDD.  I wanted to have Win7 and Ubuntu both installed to the SSD, then have my /home directory and a shared file storage (for movies/music/etc) on the HDD.  The problem is with the SSD...

If there is nothing installed on the SSD, I can see the drive just fine in Ubuntu.  I can even partition it in GPartED (running off a LiveUSB).  However, once Win7 is installed to it, it immediately becomes unavailable.  It shows up as /dev/sda, but I can't see any partitions, it doesn't even show up in GPartED, and if I try installing Ubuntu the drive isn't in the dropdown.  

I have tried this:
[LIST]
[*]Partitioning the drive with the Win7 installer
[*]Partitioning the drive while booted to the LiveUSB
[*]Partitioning the drive while booted to the LiveUSB and installing Win7 on the *second* partition
[/LIST]

I know I could just install Ubuntu first, then Win7, and try to fix the MBR myself, or install Win7 to one drive, Ubuntu to another, and fiddle with the BIOS boot order every time I want to switch OSes, but I'd really like to figure out why this isn't working.  Anyone have any ideas?

---

### Post by oldfred on 2011-08-20
Sometimes Windows needs a chkdsk after an install. Not sure about the difference with SSDs. But Ubuntu & gparted will not mount a NTFS drive that needs chkdsk to prevent damage that then chkdsk could not fix.

Also the NTFS driver seems more sensitive than windows to issues. My XP install on sda would boot, but gparted would not even see sda and would take forever to then load sdb & sdc. But after a chkdsk then gparted immediately loaded sda.

---

### Post by foilboy on 2011-08-20
Alright so I booted into Windows, scheduled a chkdsk run (as described [here]("http://answers.microsoft.com/en-us/windows/forum/windows_7-performance/using-windows-7-how-do-i-run-chkdsk/a68b3e4d-1a42-e011-9767-d8d385dcbb12") ), and rebooted.  I watched it run (everything was fine), then did another reboot just to be safe.  Booted to the LiveUSB, and still no good.


Also some more information:

```
ubuntu@ubuntu:~$ ls /dev | grep sd
sda
sdb
sdc
sdc1
```

sda is the SSD, sdb is the HDD, and sdc is the USB drive I'm booting from.  It can't see sda1 or sda2 :(

```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda /media/abc
Failed to read bootsector (size=0)
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
Makes sense...so I try this:
```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/abc
ntfs-3g: Failed to access volume '/dev/sda1': No such file or directory

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

<Copyright lines>

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org
```
Ok, so it's just calling ntfs-3g...I'll try that:
```
ubuntu@ubuntu:~$ sudo ntfs-3g /dev/sda /media/abc/
Failed to read bootsector (size=0)
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
Hmph.

---

### Post by oldfred on 2011-08-20
All NTFS partitions have to have a valid NTFS partition boot sector. Did you write grub to it or something?

Try this but it may not mount the NTFS partitions either:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
New Version 060 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

---

### Post by tofagerl on 2011-08-20
Removed

---

### Post by oldfred on 2011-08-20
@   	tofagerl
You confused me, I thought you were the OP, please start you own thread as your issues are different. Did/do you have partitions on sdb? It shows a gpt (GUID) but no partitions.

This also may help, but do you want gpt or MBR? Windows only boot from gpt with UEFI. If not using Windows then gpt may be better.
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by foilboy on 2011-08-20
Thanks for all the help so far!

> **oldfred said:**
> All NTFS partitions have to have a valid NTFS partition boot sector. Did you write grub to it or something?


Nope.  Before installing Win7 (so, when Ubuntu could see the drive) I put two partitions on it - the first as ext4 and the second as ntfs.  Then I installed Win7 to the NTFS partition (I could see both in the Win7 install sequence).

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.......(+.4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1427200 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1030 MB, 1030750208 bytes
32 heads, 62 sectors/track, 1014 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     2,011,775     2,011,714   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       39c56a6e-99d5-45ed-a94d-765baf251afa   ext3       
/dev/sdc1        BF52-4BB0                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Ok so it looks like there's still a Windows entry in the MBR on sdb - I did install Windows on there for a day or two while I was waiting for the SSD to come in the mail.  I deleted the partition when I first started this a week ago. I'd venture to guess that's not the problem, though, considering all the errors on /dev/sda.

---

### Post by srs5694 on 2011-08-20
Two things exist in the Master Boot Record (MBR; aka the first sector, or "sector 0") of a typical hard disk:


[list]
[*]The MBR boot loader code, which can be used by the BIOS to boot a computer.
[*]The MBR partition table, which defines up to four "primary" partitions on the disk.
[/list]


The Boot Info Script has detected a Windows MBR boot loader on /dev/sdb, but not MBR partition table entries. This is consistent with a Windows installation having been done and then removed; removing an OS often removes the OS's partitions, but its MBR boot loader code often remains behind. As you surmise, this isn't the root of the problem you're experiencing; I just mention it because you seemed a bit puzzled about it.

It seems that Linux is having problems reading from /dev/sda (presumably your SSD) -- it's assigned a device node to the drive, but as you noted, the Boot Info Script is reporting read errors, and there's no data about partitions, boot code, or other data on /dev/sda. Based on the Boot Info Script output, this looks like a hardware fault -- a bad disk, a bad cable, or a bad disk controller, in all probability, although it could be a driver bug, too. Your first post suggests that the drive worked fine before you installed Windows, though, which I wouldn't expect of a hardware fault. Still, it's possible that the hardware fault developed only after you installed Windows. It's therefore worth looking into the possibility. Among other things, you could try:


[list]
[*]Re-attaching the drive's data cable at both ends
[*]Replacing the drive's data cable
[*]Re-attaching the drive's power cable
[*]Plugging the drive into a different port on the motherboard
[*]Running a SMART utility, such as smartctl, GSmartControl, or a manufacturer-provided utility, to diagnose drive failures
[*]Using a plug-in disk controller card or a USB adapter to access the drive, at least for test purposes
[*]Using the drive in an entirely different computer, at least for test purposes
[/list]


With any luck, one or more of those actions will produce useful information, or even fix the problem entirely.

Failing that, you could try using a different Linux distribution -- it's conceivable that a kernel bug would be absent in another distribution's kernel, so if that's the problem it's worth trying another distribution.

You might also find some diagnostic messages in the kernel ring buffer, which you can view by typing "dmesg" at a shell prompt. This will produce copious output, so you might want to pipe it through less ("dmesg | less") or redirect it to a file ("dmesg > dmesg.txt"). If you do the latter, you can post the output here for us to view; perhaps somebody knowledgeable in such matters could spot some useful tidbit.

---

### Post by foilboy on 2011-08-20
> **srs5694 said:**
> 
Your first post suggests that the drive worked fine before you installed Windows, though, which I wouldn't expect of a hardware fault. Still, it's possible that the hardware fault developed only after you installed Windows. 
I don't think it's a hardware fault - I've been through the cycle 3 times now.  Every time I wipe the Windows partitions, the drive shows up again in Linux.  It's definitely something with the Win7 install process.
> 
...

With any luck, one or more of those actions will produce useful information, or even fix the problem entirely.

I'll look into a SMART utility.

> 
Failing that, you could try using a different Linux distribution -- it's conceivable that a kernel bug would be absent in another distribution's kernel, so if that's the problem it's worth trying another distribution.

I've also tried it with Linux Mint (didn't work)- but I know that's very similar to Ubuntu.  I'll also try an older version (Ubuntu 9.10 or something)

> 
You might also find some diagnostic messages in the kernel ring buffer, which you can view by typing "dmesg" at a shell prompt. This will produce copious output, so you might want to pipe it through less ("dmesg | less") or redirect it to a file ("dmesg > dmesg.txt"). If you do the latter, you can post the output here for us to view; perhaps somebody knowledgeable in such matters could spot some useful tidbit.

Here's the output from dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bfef1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfef1000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF80000 mask FFFF80000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff80000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  modified: 00000000bfee0000 - 00000000bfef0000 (ACPI data)
[    0.000000]  modified: 00000000bfef0000 - 00000000bfef1000 (ACPI NVS)
[    0.000000]  modified: 00000000bfef1000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f6930] f6930
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfee0000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfee0000 page 4k
[    0.000000] kernel direct mapping tables up to bfee0000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 19000-1f000
[    0.000000] RAMDISK: 7f4c1000 - 80000000
[    0.000000] ACPI: RSDP 00000000000f6900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bfee90d5 0006C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bfeefd7e 000F4 (v03 INTEL  SEABURG  06040000 PTL  00000003)
[    0.000000] ACPI: DSDT 00000000bfeeb42a 048E0 (v01  Intel SEABURG  06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000bfef0fc0 00040
[    0.000000] ACPI: _MAR 00000000bfeefe72 00030 (v01 Intel  OEMDMAR  06040000 LOHR 00000001)
[    0.000000] ACPI: TCPA 00000000bfeefea2 00032 (v01 Intel  SEABURG  06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 00000000bfeefed4 000C8 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000bfeeff9c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bfeeffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bfeea5ec 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 00000000bfeea546 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 00000000bfee9141 01405 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff8801039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bfee0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048173
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3925 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767768 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec88000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec88000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfef0000
[    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bfef1000
[    0.000000] PM: Registered nosave memory: 00000000bfef1000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030253
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (61 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [007f4c1000 - 0080000000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18158]             BRK
[    0.000000]   #4 [00000f6940 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f6930 - 00000f6940]    MP-table mpf
[    0.000000]   #6 [000009d800 - 000009dd71]   BIOS reserved
[    0.000000]   #7 [000009df5d - 00000f6930]   BIOS reserved
[    0.000000]   #8 [000009dd71 - 000009df5d]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 000001a000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18180 - 0001d19180]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103a00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19180 - 0001d31180]         BOOTMEM
[    0.000000]   #21 [0001d31180 - 0001d37180]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17646]         BOOTMEM
[    0.000000]   #24 [0001d17680 - 0001d17958]         BOOTMEM
[    0.000000]   #25 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #26 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #27 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #28 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #29 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #30 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #31 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #32 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #33 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #34 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #35 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #36 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #37 [0001d17f80 - 0001d17fa0]         BOOTMEM
[    0.000000]   #38 [0001d17fc0 - 0001d17fe0]         BOOTMEM
[    0.000000]   #39 [0001d37180 - 0001d37203]         BOOTMEM
[    0.000000]   #40 [0001d37240 - 0001d372c3]         BOOTMEM
[    0.000000]   #41 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #42 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #43 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #44 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #45 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #46 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #47 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #48 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #49 [0001d37300 - 0001d37308]         BOOTMEM
[    0.000000]   #50 [0001d37340 - 0001d37348]         BOOTMEM
[    0.000000]   #51 [0001d37380 - 0001d373a0]         BOOTMEM
[    0.000000]   #52 [0001d373c0 - 0001d37400]         BOOTMEM
[    0.000000]   #53 [0001d37400 - 0001d37520]         BOOTMEM
[    0.000000]   #54 [0001d37540 - 0001d37588]         BOOTMEM
[    0.000000]   #55 [0001d375c0 - 0001d37608]         BOOTMEM
[    0.000000]   #56 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #57 [0001fde000 - 0005fde000]         BOOTMEM
[    0.000000]   #58 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #59 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #60 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4043276k/5242880k available (5708k kernel code, 1050188k absent, 149416k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:1152
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.958 MHz processor.
[    0.020013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.91 BogoMIPS (lpj=18619580)
[    0.020019] pid_max: default: 32768 minimum: 301
[    0.020058] Security Framework initialized
[    0.020088] AppArmor: AppArmor initialized
[    0.020090] Yama: becoming mindful.
[    0.020687] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.023433] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.024696] Mount-cache hash table entries: 256
[    0.024909] Initializing cgroup subsys ns
[    0.024916] Initializing cgroup subsys cpuacct
[    0.024921] Initializing cgroup subsys memory
[    0.024935] Initializing cgroup subsys devices
[    0.024938] Initializing cgroup subsys freezer
[    0.024941] Initializing cgroup subsys net_cls
[    0.024983] CPU: Physical Processor ID: 0
[    0.024985] CPU: Processor Core ID: 0
[    0.024988] mce: CPU supports 6 MCE banks
[    0.024999] CPU0: Thermal monitoring enabled (TM2)
[    0.025004] using mwait in idle threads.
[    0.025006] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.025013] PEBS disabled due to CPU errata.
[    0.025018] ... version:                2
[    0.025020] ... bit width:              40
[    0.025022] ... generic registers:      2
[    0.025024] ... value mask:             000000ffffffffff
[    0.025026] ... max period:             000000007fffffff
[    0.025028] ... fixed-purpose events:   3
[    0.025030] ... event mask:             0000000700000003
[    0.028112] ACPI: Core revision 20100428
[    0.039834] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.039841] ftrace: allocating 22680 entries in 89 pages
[    0.050083] Setting APIC routing to flat
[    0.050485] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.159695] CPU0: Intel(R) Xeon(R) CPU           E5320  @ 1.86GHz stepping 07
[    0.160000] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    1.340010] Brought up 8 CPUs
[    1.340015] Total of 8 processors activated (29834.34 BogoMIPS).
[    1.345175] devtmpfs: initialized
[    1.345175] regulator: core version 0.5
[    1.345175] Time: 23:10:31  Date: 12/31/06
[    1.345175] NET: Registered protocol family 16
[    1.345175] ACPI: bus type pci registered
[    1.345175] Trying to unpack rootfs image as initramfs...
[    1.345175] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xe0000000-0xe1ffffff] (base 0xe0000000)
[    1.345175] PCI: MMCONFIG at [mem 0xe0000000-0xe1ffffff] reserved in E820
[    1.353917] PCI: Using configuration type 1 for base access
[    1.354795] bio: create slab <bio-0> at 0
[    1.354795] ACPI: EC: Look up EC in DSDT
[    1.360251] ACPI: SSDT 00000000bfeea84b 001DD (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.360506] ACPI: Dynamic OEM Table Load:
[    1.360510] ACPI: SSDT (null) 001DD (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.361156] ACPI: SSDT 00000000bfeeaa28 0016E (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.361414] ACPI: Dynamic OEM Table Load:
[    1.361418] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.362060] ACPI: SSDT 00000000bfeeab96 0016E (v01  PmRef  Cpu2Ist 00003000 INTL 20050228)
[    1.362314] ACPI: Dynamic OEM Table Load:
[    1.362318] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu2Ist 00003000 INTL 20050228)
[    1.362956] ACPI: SSDT 00000000bfeead04 0016E (v01  PmRef  Cpu3Ist 00003000 INTL 20050228)
[    1.363213] ACPI: Dynamic OEM Table Load:
[    1.363216] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu3Ist 00003000 INTL 20050228)
[    1.363860] ACPI: SSDT 00000000bfeeae72 0016E (v01  PmRef  CPU4Ist 00003000 INTL 20050228)
[    1.364119] ACPI: Dynamic OEM Table Load:
[    1.364122] ACPI: SSDT (null) 0016E (v01  PmRef  CPU4Ist 00003000 INTL 20050228)
[    1.364851] ACPI: SSDT 00000000bfeeafe0 0016E (v01  PmRef  CPU5Ist 00003000 INTL 20050228)
[    1.365112] ACPI: Dynamic OEM Table Load:
[    1.365116] ACPI: SSDT (null) 0016E (v01  PmRef  CPU5Ist 00003000 INTL 20050228)
[    1.365762] ACPI: SSDT 00000000bfeeb14e 0016E (v01  PmRef  Cpu6Ist 00003000 INTL 20050228)
[    1.366024] ACPI: Dynamic OEM Table Load:
[    1.366028] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu6Ist 00003000 INTL 20050228)
[    1.366671] ACPI: SSDT 00000000bfeeb2bc 0016E (v01  PmRef  Cpu7Ist 00003000 INTL 20050228)
[    1.366935] ACPI: Dynamic OEM Table Load:
[    1.366939] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu7Ist 00003000 INTL 20050228)
[    1.367004] ACPI: Interpreter enabled
[    1.367007] ACPI: (supports S0 S1 S3 S4 S5)
[    1.367030] ACPI: Using IOAPIC for interrupt routing
[    1.372371] ACPI: No dock devices found.
[    1.372375] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    1.373459] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.375558] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    1.375562] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    1.375565] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    1.375568] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    1.375571] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    1.375574] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    1.375577] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    1.375581] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xfebfffff] (ignored)
[    1.375584] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    1.375646] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.375650] pci 0000:00:00.0: PME# disabled
[    1.375713] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.375718] pci 0000:00:01.0: PME# disabled
[    1.375779] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.375783] pci 0000:00:05.0: PME# disabled
[    1.375845] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.375849] pci 0000:00:09.0: PME# disabled
[    1.376215] pci 0000:00:1b.0: reg 10: [mem 0xd3504000-0xd3507fff 64bit]
[    1.376263] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.376267] pci 0000:00:1b.0: PME# disabled
[    1.376342] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.376346] pci 0000:00:1c.0: PME# disabled
[    1.376403] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    1.376467] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    1.376524] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    1.376585] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    1.376642] pci 0000:00:1d.7: reg 10: [mem 0xd3508000-0xd35083ff]
[    1.376697] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.376702] pci 0000:00:1d.7: PME# disabled
[    1.376828] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    1.376854] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    1.376861] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    1.376868] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    1.376875] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    1.376882] pci 0000:00:1f.1: reg 20: [io  0x1880-0x188f]
[    1.376924] pci 0000:00:1f.2: reg 10: [io  0x18c0-0x18c7]
[    1.376931] pci 0000:00:1f.2: reg 14: [io  0x18b8-0x18bb]
[    1.376937] pci 0000:00:1f.2: reg 18: [io  0x18b0-0x18b7]
[    1.376943] pci 0000:00:1f.2: reg 1c: [io  0x1894-0x1897]
[    1.376950] pci 0000:00:1f.2: reg 20: [io  0x18a0-0x18af]
[    1.376957] pci 0000:00:1f.2: reg 24: [mem 0xd3508400-0xd35087ff]
[    1.376980] pci 0000:00:1f.2: PME# supported from D3hot
[    1.376984] pci 0000:00:1f.2: PME# disabled
[    1.377035] pci 0000:00:1f.3: reg 20: [io  0x1100-0x111f]
[    1.377101] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.377106] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.377111] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.377117] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.377174] pci 0000:05:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    1.377185] pci 0000:05:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.377195] pci 0000:05:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit]
[    1.377201] pci 0000:05:00.0: reg 24: [io  0x2000-0x207f]
[    1.377208] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    1.390016] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    1.390021] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    1.390026] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    1.390033] pci 0000:00:05.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.390141] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    1.390145] pci 0000:09:00.0: PME# disabled
[    1.390210] pci 0000:09:00.3: PME# supported from D0 D3hot D3cold
[    1.390215] pci 0000:09:00.3: PME# disabled
[    1.390232] pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390243] pci 0000:00:09.0: PCI bridge to [bus 09-10]
[    1.390247] pci 0000:00:09.0:   bridge window [io  0x3000-0x3fff]
[    1.390251] pci 0000:00:09.0:   bridge window [mem 0xd3000000-0xd31fffff]
[    1.390257] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390353] pci 0000:0a:00.0: PME# supported from D0 D3hot D3cold
[    1.390358] pci 0000:0a:00.0: PME# disabled
[    1.390372] pci 0000:0a:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390439] pci 0000:0a:02.0: PME# supported from D0 D3hot D3cold
[    1.390444] pci 0000:0a:02.0: PME# disabled
[    1.390458] pci 0000:0a:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390491] pci 0000:09:00.0: PCI bridge to [bus 0a-0f]
[    1.390495] pci 0000:09:00.0:   bridge window [io  0x3000-0x3fff]
[    1.390500] pci 0000:09:00.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    1.390507] pci 0000:09:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390551] pci 0000:0a:00.0: PCI bridge to [bus 0b-0b]
[    1.390556] pci 0000:0a:00.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.390561] pci 0000:0a:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.390568] pci 0000:0a:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390639] pci 0000:0f:00.0: reg 10: [mem 0xd3000000-0xd301ffff]
[    1.390652] pci 0000:0f:00.0: reg 18: [io  0x3000-0x301f]
[    1.390705] pci 0000:0f:00.0: PME# supported from D0 D3hot D3cold
[    1.390710] pci 0000:0f:00.0: PME# disabled
[    1.390754] pci 0000:0f:00.1: reg 10: [mem 0xd3020000-0xd303ffff]
[    1.390767] pci 0000:0f:00.1: reg 18: [io  0x3020-0x303f]
[    1.390820] pci 0000:0f:00.1: PME# supported from D0 D3hot D3cold
[    1.390825] pci 0000:0f:00.1: PME# disabled
[    1.390849] pci 0000:0f:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390862] pci 0000:0a:02.0: PCI bridge to [bus 0f-0f]
[    1.390866] pci 0000:0a:02.0:   bridge window [io  0x3000-0x3fff]
[    1.390871] pci 0000:0a:02.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    1.390878] pci 0000:0a:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390964] pci 0000:09:00.3: PCI bridge to [bus 10-10]
[    1.390968] pci 0000:09:00.3:   bridge window [io  0xf000-0x0000] (disabled)
[    1.390973] pci 0000:09:00.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.390980] pci 0000:09:00.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.391036] pci 0000:00:1c.0: PCI bridge to [bus 1f-1f]
[    1.391040] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.391045] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.391052] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.391112] pci 0000:20:04.0: reg 10: [mem 0xd3200000-0xd320ffff]
[    1.391198] pci 0000:20:05.0: reg 10: [mem 0xd3214000-0xd32147ff]
[    1.391206] pci 0000:20:05.0: reg 14: [mem 0xd3210000-0xd3213fff]
[    1.391255] pci 0000:20:05.0: supports D1 D2
[    1.391257] pci 0000:20:05.0: PME# supported from D0 D1 D2 D3hot
[    1.391262] pci 0000:20:05.0: PME# disabled
[    1.391318] pci 0000:00:1e.0: PCI bridge to [bus 20-20] (subtractive decode)
[    1.391331] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.391335] pci 0000:00:1e.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    1.391342] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.391345] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    1.391348] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[    1.391373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.391689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.391760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.391829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    1.391900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0._PRT]
[    1.392040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0.BPD0._PRT]
[    1.392122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0.BPD2._PRT]
[    1.392193] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMF3._PRT]
[    1.392297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.392395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.403664] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 14 15) *9
[    1.403766] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 14 15)
[    1.403866] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[    1.403964] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[    1.404062] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    1.404161] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 6 7 10 *11 14 15)
[    1.404258] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 *15)
[    1.404355] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 6 7 *10 11 14 15)
[    1.404406] HEST: Table is not found!
[    1.404501] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.404509] vgaarb: loaded
[    1.404673] SCSI subsystem initialized
[    1.404692] libata version 3.00 loaded.
[    1.404692] usbcore: registered new interface driver usbfs
[    1.404692] usbcore: registered new interface driver hub
[    1.404692] usbcore: registered new device driver usb
[    1.404692] ACPI: WMI: Mapper loaded
[    1.404692] PCI: Using ACPI for IRQ routing
[    1.404692] PCI: pci_cache_line_size set to 64 bytes
[    1.404692] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.404692] reserve RAM buffer: 00000000bfee0000 - 00000000bfffffff 
[    1.404692] NetLabel: Initializing
[    1.404692] NetLabel:  domain hash size = 128
[    1.404692] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.404692] NetLabel:  unlabeled traffic allowed by default
[    1.404692] hpet clockevent registered
[    1.404692] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    1.404692] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.404692] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    3.420085] Switching to clocksource tsc
[    3.435178] AppArmor: AppArmor Filesystem Enabled
[    3.435211] pnp: PnP ACPI init
[    3.435248] ACPI: bus type pnp registered
[    3.439578] pnp: PnP ACPI: found 11 devices
[    3.439584] ACPI: ACPI bus type pnp unregistered
[    3.439614] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    3.439618] system 00:01: [io  0x0800-0x080f] has been reserved
[    3.439621] system 00:01: [io  0x1000-0x107f] has been reserved
[    3.439625] system 00:01: [io  0x1180-0x11bf] has been reserved
[    3.439631] system 00:01: [io  0xfe00] has been reserved
[    3.439637] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    3.439640] system 00:01: [mem 0xfee00000-0xfee0ffff] could not be reserved
[    3.439643] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    3.439646] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    3.439650] system 00:01: [mem 0xfec88000-0xfec88fff] could not be reserved
[    3.439653] system 00:01: [mem 0xfe000000-0xfe01ffff] has been reserved
[    3.439656] system 00:01: [mem 0xfe600000-0xfe6fffff] has been reserved
[    3.446470] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd3300000-0xd34fffff]
[    3.446478] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.446483] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    3.446487] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.446489] pci 0000:00:01.0:   bridge window [io  disabled]
[    3.446494] pci 0000:00:01.0:   bridge window [mem disabled]
[    3.446498] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    3.446505] pci 0000:05:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    3.446508] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    3.446512] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    3.446516] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    3.446521] pci 0000:00:05.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.446527] pci 0000:0a:00.0: PCI bridge to [bus 0b-0b]
[    3.446529] pci 0000:0a:00.0:   bridge window [io  disabled]
[    3.446535] pci 0000:0a:00.0:   bridge window [mem disabled]
[    3.446539] pci 0000:0a:00.0:   bridge window [mem pref disabled]
[    3.446546] pci 0000:0a:02.0: PCI bridge to [bus 0f-0f]
[    3.446550] pci 0000:0a:02.0:   bridge window [io  0x3000-0x3fff]
[    3.446555] pci 0000:0a:02.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    3.446560] pci 0000:0a:02.0:   bridge window [mem pref disabled]
[    3.446567] pci 0000:09:00.0: PCI bridge to [bus 0a-0f]
[    3.446570] pci 0000:09:00.0:   bridge window [io  0x3000-0x3fff]
[    3.446575] pci 0000:09:00.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    3.446580] pci 0000:09:00.0:   bridge window [mem pref disabled]
[    3.446587] pci 0000:09:00.3: PCI bridge to [bus 10-10]
[    3.446589] pci 0000:09:00.3:   bridge window [io  disabled]
[    3.446594] pci 0000:09:00.3:   bridge window [mem disabled]
[    3.446598] pci 0000:09:00.3:   bridge window [mem pref disabled]
[    3.446605] pci 0000:00:09.0: PCI bridge to [bus 09-10]
[    3.446608] pci 0000:00:09.0:   bridge window [io  0x3000-0x3fff]
[    3.446613] pci 0000:00:09.0:   bridge window [mem 0xd3000000-0xd31fffff]
[    3.446617] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    3.446622] pci 0000:00:1c.0: PCI bridge to [bus 1f-1f]
[    3.446625] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    3.446631] pci 0000:00:1c.0:   bridge window [mem 0xd3300000-0xd34fffff]
[    3.446636] pci 0000:00:1c.0:   bridge window [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.446643] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    3.446645] pci 0000:00:1e.0:   bridge window [io  disabled]
[    3.446651] pci 0000:00:1e.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    3.446655] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    3.446687]   alloc irq_desc for 16 on node -1
[    3.446690]   alloc kstat_irqs on node -1
[    3.446708] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.446713] pci 0000:00:01.0: setting latency timer to 64
[    3.446722] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.446726] pci 0000:00:05.0: setting latency timer to 64
[    3.446734] pci 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.446738] pci 0000:00:09.0: setting latency timer to 64
[    3.446751] pci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.446756] pci 0000:09:00.0: setting latency timer to 64
[    3.446766] pci 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.446770] pci 0000:0a:00.0: setting latency timer to 64
[    3.446780]   alloc irq_desc for 18 on node -1
[    3.446782]   alloc kstat_irqs on node -1
[    3.446787] pci 0000:0a:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.446791] pci 0000:0a:02.0: setting latency timer to 64
[    3.446802] pci 0000:09:00.3: setting latency timer to 64
[    3.446812]   alloc irq_desc for 21 on node -1
[    3.446814]   alloc kstat_irqs on node -1
[    3.446818] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.446823] pci 0000:00:1c.0: setting latency timer to 64
[    3.446831] pci 0000:00:1e.0: setting latency timer to 64
[    3.446836] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    3.446838] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    3.446841] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    3.446844] pci_bus 0000:05: resource 1 [mem 0xd0000000-0xd2ffffff]
[    3.446847] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.446850] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    3.446852] pci_bus 0000:09: resource 1 [mem 0xd3000000-0xd31fffff]
[    3.446855] pci_bus 0000:0a: resource 0 [io  0x3000-0x3fff]
[    3.446857] pci_bus 0000:0a: resource 1 [mem 0xd3000000-0xd30fffff]
[    3.446860] pci_bus 0000:0f: resource 0 [io  0x3000-0x3fff]
[    3.446863] pci_bus 0000:0f: resource 1 [mem 0xd3000000-0xd30fffff]
[    3.446866] pci_bus 0000:1f: resource 0 [io  0x4000-0x4fff]
[    3.446868] pci_bus 0000:1f: resource 1 [mem 0xd3300000-0xd34fffff]
[    3.446871] pci_bus 0000:1f: resource 2 [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.446874] pci_bus 0000:20: resource 1 [mem 0xd3200000-0xd32fffff]
[    3.446876] pci_bus 0000:20: resource 4 [io  0x0000-0xffff]
[    3.446879] pci_bus 0000:20: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    3.446954] NET: Registered protocol family 2
[    3.447224] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.449038] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.453977] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.454612] TCP: Hash tables configured (established 524288 bind 65536)
[    3.454616] TCP reno registered
[    3.454628] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    3.454682] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    3.454900] NET: Registered protocol family 1
[    3.455066] pci 0000:00:1f.0: rerouting interrupts for [8086:2670]
[    3.455094] pci 0000:05:00.0: Boot video device
[    3.455104] PCI: CLS mismatch (32 != 64), using 64 bytes
[    3.455117] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.455121] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    3.455124] software IO TLB at phys 0x1fde000 - 0x5fde000
[    3.455191] Simple Boot Flag at 0x40 set to 0x1
[    3.455850] Scanning for low memory corruption every 60 seconds
[    3.456029] audit: initializing netlink socket (disabled)
[    3.456042] type=2000 audit(1167606632.450:1): initialized
[    3.472849] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.474943] VFS: Disk quotas dquot_6.5.2
[    3.475012] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.475722] fuse init (API version 7.14)
[    3.475841] msgmni has been set to 7897
[    3.477106] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.477110] io scheduler noop registered
[    3.477113] io scheduler deadline registered
[    3.477163] io scheduler cfq registered (default)
[    3.477361] pcieport 0000:00:01.0: setting latency timer to 64
[    3.477392]   alloc irq_desc for 64 on node -1
[    3.477394]   alloc kstat_irqs on node -1
[    3.477420] pcieport 0000:00:01.0: irq 64 for MSI/MSI-X
[    3.477493] pcieport 0000:00:05.0: setting latency timer to 64
[    3.477519]   alloc irq_desc for 65 on node -1
[    3.477521]   alloc kstat_irqs on node -1
[    3.477529] pcieport 0000:00:05.0: irq 65 for MSI/MSI-X
[    3.477594] pcieport 0000:00:09.0: setting latency timer to 64
[    3.477620]   alloc irq_desc for 66 on node -1
[    3.477622]   alloc kstat_irqs on node -1
[    3.477628] pcieport 0000:00:09.0: irq 66 for MSI/MSI-X
[    3.477699] pcieport 0000:00:1c.0: setting latency timer to 64
[    3.477733]   alloc irq_desc for 67 on node -1
[    3.477735]   alloc kstat_irqs on node -1
[    3.477743] pcieport 0000:00:1c.0: irq 67 for MSI/MSI-X
[    3.477836] pcieport 0000:09:00.0: setting latency timer to 64
[    3.477912] pcieport 0000:0a:00.0: setting latency timer to 64
[    3.477946]   alloc irq_desc for 68 on node -1
[    3.477948]   alloc kstat_irqs on node -1
[    3.477957] pcieport 0000:0a:00.0: irq 68 for MSI/MSI-X
[    3.478020] pcieport 0000:0a:02.0: setting latency timer to 64
[    3.478054]   alloc irq_desc for 69 on node -1
[    3.478056]   alloc kstat_irqs on node -1
[    3.478066] pcieport 0000:0a:02.0: irq 69 for MSI/MSI-X
[    3.478145] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    3.478152] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    3.478159] aer 0000:00:09.0:pcie02: AER service couldn't init device: no _OSC support
[    3.478183] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.478234] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.478334] intel_idle: MWAIT substates: 0x20
[    3.478337] intel_idle: does not run on family 6 model 15
[    3.478475] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0C:00/input/input0
[    3.478483] ACPI: Power Button [PWRB]
[    3.478537] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.478541] ACPI: Power Button [PWRF]
[    3.478742] ACPI: acpi_idle registered with cpuidle
[    4.248756] ERST: Table is not found!
[    4.248895] Linux agpgart interface v0.103
[    4.248924] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.249038] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.249422] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.250844] brd: module loaded
[    4.251445] loop: module loaded
[    4.251643] ata_piix 0000:00:1f.1: version 2.13
[    4.251660]   alloc irq_desc for 20 on node -1
[    4.251662]   alloc kstat_irqs on node -1
[    4.251671] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.251724] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.251879] scsi0 : ata_piix
[    4.251995] scsi1 : ata_piix
[    4.252518] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    4.252522] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    4.252548]   alloc irq_desc for 23 on node -1
[    4.252551]   alloc kstat_irqs on node -1
[    4.252557] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    4.252562] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.252773] ata2: port disabled. ignoring.
[    4.266572] Freeing initrd memory: 11516k freed
[    4.410688] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.410801] scsi2 : ata_piix
[    4.410918] scsi3 : ata_piix
[    4.410963] ata3: SATA max UDMA/133 cmd 0x18c0 ctl 0x18b8 bmdma 0x18a0 irq 23
[    4.410967] ata4: SATA max UDMA/133 cmd 0x18b0 ctl 0x1894 bmdma 0x18a8 irq 23
[    4.411390] Fixed MDIO Bus: probed
[    4.411428] PPP generic driver version 2.4.2
[    4.411468] tun: Universal TUN/TAP device driver, 1.6
[    4.411470] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.411574] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.411598] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.411624] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.411627] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.411683] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.411718] ehci_hcd 0000:00:1d.7: debug port 1
[    4.415601] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    4.415619] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd3508000
[    4.430649] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.430824] hub 1-0:1.0: USB hub found
[    4.430831] hub 1-0:1.0: 8 ports detected
[    4.430927] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.430944] uhci_hcd: USB Universal Host Controller Interface driver
[    4.431003] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.431009] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.431013] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.431048] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.431073] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[    4.431203] hub 2-0:1.0: USB hub found
[    4.431208] hub 2-0:1.0: 2 ports detected
[    4.431281] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.431288] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.431291] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.431330] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.431368] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[    4.431496] hub 3-0:1.0: USB hub found
[    4.431500] hub 3-0:1.0: 2 ports detected
[    4.431574]   alloc irq_desc for 22 on node -1
[    4.431576]   alloc kstat_irqs on node -1
[    4.431583] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.431589] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.431592] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.431640] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.431672] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
[    4.431798] hub 4-0:1.0: USB hub found
[    4.431802] hub 4-0:1.0: 2 ports detected
[    4.431888] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.431894] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.431898] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.431933] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.431957] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001860
[    4.432080] hub 5-0:1.0: USB hub found
[    4.432085] hub 5-0:1.0: 2 ports detected
[    4.432216] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.434678] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.434687] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.434820] mice: PS/2 mouse device common for all mice
[    4.434982] rtc_cmos 00:04: RTC can wake from S4
[    4.435033] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.435062] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.435175] device-mapper: uevent: version 1.0.3
[    4.435288] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    4.435712] device-mapper: multipath: version 1.1.1 loaded
[    4.435716] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.436591] cpuidle: using governor ladder
[    4.436594] cpuidle: using governor menu
[    4.436937] TCP cubic registered
[    4.437077] NET: Registered protocol family 10
[    4.437547] lo: Disabled Privacy Extensions
[    4.437770] NET: Registered protocol family 17
[    4.439858] PM: Resume from disk failed.
[    4.439874] registered taskstats version 1
[    4.440273]   Magic number: 2:425:202
[    4.440381] rtc_cmos 00:04: setting system clock to 2006-12-31 23:10:34 UTC (1167606634)
[    4.440385] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.440387] EDD information not available.
[    4.462740] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.570285] ata3.01: NODEV after polling detection
[    4.590250] ata3.00: ATAPI: LITE-ON DVDRW LH-16A1S, CL04, max UDMA/100
[    4.610175] ata4.00: ATA-8: OCZ-VERTEX2, 1.33, max UDMA/133
[    4.610179] ata4.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.610348] ata4.01: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    4.610354] ata4.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.630211] ata3.00: configured for UDMA/100
[    4.632231] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-16A1S   CL04 PQ: 0 ANSI: 5
[    4.637744] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.637749] Uniform CD-ROM driver Revision: 3.20
[    4.637916] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.637985] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    4.650251] ata4.00: configured for UDMA/133
[    4.670697] ata4.01: configured for UDMA/133
[    4.670906] scsi 3:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.33 PQ: 0 ANSI: 5
[    4.671110] sd 3:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.671121] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.671191] sd 3:0:0:0: [sda] Write Protect is off
[    4.671194] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.671234] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.671249] scsi 3:0:1:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    4.671399] sd 3:0:1:0: Attached scsi generic sg2 type 0
[    4.671460] sd 3:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.671610]  sda:
[    4.671618] sd 3:0:1:0: [sdb] Write Protect is off
[    4.671623] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.671667] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.671912]  sda1 sda2
[    4.672175]  sdb:
[    4.813789] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    5.082650] 
[    5.082760] sd 3:0:0:0: [sda] Attached SCSI disk
[    5.082968] sd 3:0:1:0: [sdb] Attached SCSI disk
[    5.083018] Freeing unused kernel memory: 908k freed
[    5.083459] Write protecting the kernel read-only data: 10240k
[    5.083677] Freeing unused kernel memory: 416k freed
[    5.084100] Freeing unused kernel memory: 1644k freed
[    5.114002] udev[159]: starting version 163
[    5.149364] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    5.149368] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    5.149445] e1000e 0000:0f:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.149465] e1000e 0000:0f:00.0: setting latency timer to 64
[    5.149633]   alloc irq_desc for 70 on node -1
[    5.149636]   alloc kstat_irqs on node -1
[    5.149655] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[    5.167662] [drm] Initialized drm 1.1.0 20060810
[    5.181226] Initializing USB Mass Storage driver...
[    5.181452] scsi4 : usb-storage 1-8:1.0
[    5.181598] usbcore: registered new interface driver usb-storage
[    5.181600] USB Mass Storage support registered.
[    5.185450] firewire_ohci 0000:20:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.209879] nouveau 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.209887] nouveau 0000:05:00.0: setting latency timer to 64
[    5.215727] [drm] nouveau 0000:05:00.0: Detected an NV50 generation card (0x094100a1)
[    5.224102] [drm] nouveau 0000:05:00.0: Attempting to load BIOS image from PRAMIN
[    5.241935] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.243232] firewire_ohci: Added fw-ohci device 0000:20:05.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    5.251206] e1000e 0000:0f:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:e0:81:79:19:2c
[    5.251210] e1000e 0000:0f:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.251309] e1000e 0000:0f:00.0: eth0: MAC: 5, PHY: 5, PBA No: ffffff-0ff
[    5.251353]   alloc irq_desc for 19 on node -1
[    5.251356]   alloc kstat_irqs on node -1
[    5.251367] e1000e 0000:0f:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.251383] e1000e 0000:0f:00.1: setting latency timer to 64
[    5.251557]   alloc irq_desc for 71 on node -1
[    5.251560]   alloc kstat_irqs on node -1
[    5.251574] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[    5.277849] [drm] nouveau 0000:05:00.0: ... appears to be valid
[    5.277854] [drm] nouveau 0000:05:00.0: BIT BIOS found
[    5.277858] [drm] nouveau 0000:05:00.0: Bios version 62.94.11.00
[    5.277862] [drm] nouveau 0000:05:00.0: TMDS table revision 2.0 not currently supported
[    5.277866] [drm] nouveau 0000:05:00.0: Found Display Configuration Block version 4.0
[    5.277869] [drm] nouveau 0000:05:00.0: Raw DCB entry 0: 02000300 00000028
[    5.277873] [drm] nouveau 0000:05:00.0: Raw DCB entry 1: 01000302 00020030
[    5.277876] [drm] nouveau 0000:05:00.0: Raw DCB entry 2: 04011310 00000028
[    5.277878] [drm] nouveau 0000:05:00.0: Raw DCB entry 3: 02011312 00020030
[    5.277881] [drm] nouveau 0000:05:00.0: Raw DCB entry 4: 010223f1 00c0c080
[    5.277885] [drm] nouveau 0000:05:00.0: DCB connector table: VHER 0x40 5 16 4
[    5.277889] [drm] nouveau 0000:05:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    5.277892] [drm] nouveau 0000:05:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    5.277895] [drm] nouveau 0000:05:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    5.277898] [drm] nouveau 0000:05:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    5.277902] [drm] nouveau 0000:05:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    5.277910] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 0 at offset 0xCD72
[    5.338549] e1000e 0000:0f:00.1: eth1: (PCI Express:2.5GB/s:Width x4) 00:e0:81:79:19:2d
[    5.338553] e1000e 0000:0f:00.1: eth1: Intel(R) PRO/1000 Network Connection
[    5.338634] e1000e 0000:0f:00.1: eth1: MAC: 5, PHY: 5, PBA No: ffffff-0ff
[    5.370219] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 1 at offset 0xD15B
[    5.420054] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 2 at offset 0xE0B6
[    5.420063] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 3 at offset 0xE1E5
[    5.433663] usbcore: registered new interface driver hiddev
[    5.440163] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 4 at offset 0xE3F5
[    5.440167] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table at offset 0xE45A
[    5.446755] input: Dynex 5-Button Wired Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    5.446861] generic-usb 0003:0461:4D42.0001: input,hidraw0: USB HID v1.11 Mouse [Dynex 5-Button Wired Optical Mouse] on usb-0000:00:1d.1-1/input0
[    5.446890] usbcore: registered new interface driver usbhid
[    5.446893] usbhid: USB HID core driver
[    5.470059] [drm] nouveau 0000:05:00.0: 0xE45A: Condition still not met after 20ms, skipping following opcodes
[    5.470068] [drm] nouveau 0000:05:00.0: 0xBD6A: parsing output script 0
[    5.470092] [drm] nouveau 0000:05:00.0: 0xBD6A: parsing output script 0
[    5.470095] [drm] nouveau 0000:05:00.0: 0xA7A6: parsing output script 0
[    5.470102] [drm] nouveau 0000:05:00.0: Detected 512MiB VRAM
[    5.553377] [TTM] Zone  kernel: Available graphics memory: 2028880 kiB.
[    5.553380] [TTM] Initializing pool allocator.
[    5.597596] [drm] nouveau 0000:05:00.0: 512 MiB GART (aperture)
[    5.597607] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[    5.598015] [drm] nouveau 0000:05:00.0: Allocating FIFO number 1
[    5.608398] [drm] nouveau 0000:05:00.0: nouveau_channel_alloc: initialised FIFO 1
[    5.609725] [drm] nouveau 0000:05:00.0: Detected a DAC output
[    5.609728] [drm] nouveau 0000:05:00.0: Detected a TMDS output
[    5.609732] [drm] nouveau 0000:05:00.0: Detected a DAC output
[    5.609734] [drm] nouveau 0000:05:00.0: Detected a TMDS output
[    5.609737] [drm] nouveau 0000:05:00.0: DCB encoder 1 unknown
[    5.609740] [drm] nouveau 0000:05:00.0: Detected a DVI-I connector
[    5.609805] [drm] nouveau 0000:05:00.0: Detected a DVI-I connector
[    5.609839] [drm] nouveau 0000:05:00.0: Detected a TV connector
[    5.609843] [drm] nouveau 0000:05:00.0:   no encoders, ignoring
[    5.744516] firewire_core: created device fw0: GUID 00e08100002804f8, S400
[    5.798550] [drm] nouveau 0000:05:00.0: allocated 1920x1200 fb: 0x40250000, bo ffff8801397e0800
[    5.801582] Console: switching to colour frame buffer device 240x75
[    5.801597] [drm] nouveau 0000:05:00.0: 0xBD6E: parsing output script 1
[    5.801606] [drm] nouveau 0000:05:00.0: 0xBD6F: parsing output script 2
[    5.801627] [drm] nouveau 0000:05:00.0: 0xBA7F: parsing clock script 0
[    5.801935] [drm] nouveau 0000:05:00.0: 0xB32D: parsing clock script 1
[    5.803888] fb0: nouveaufb frame buffer device
[    5.803890] drm: registered panic notifier
[    5.803894] Slow work thread pool: Starting up
[    5.803991] Slow work thread pool: Ready
[    5.803999] [drm] Initialized nouveau 0.0.16 20090420 for 0000:05:00.0 on minor 0
[    6.068464] Btrfs loaded
[    6.075118] xor: automatically using best checksumming function: generic_sse
[    6.123777]    generic_sse:  6636.000 MB/sec
[    6.123780] xor: using function: generic_sse (6636.000 MB/sec)
[    6.126573] device-mapper: dm-raid45: initialized v0.2594b
[    6.192507] scsi 4:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[    6.193337] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.194008] sd 4:0:0:0: [sdc] 2013184 512-byte logical blocks: (1.03 GB/983 MiB)
[    6.194502] sd 4:0:0:0: [sdc] Write Protect is off
[    6.194506] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    6.194509] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.196610] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.196622]  sdc: sdc1
[    6.202755] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.202759] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    6.212175] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   37.040053] ata4: lost interrupt (Status 0x50)
[   37.040075] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   37.040079] ata4.00: failed command: FLUSH CACHE
[   37.040088] ata4.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   37.040089]          res 40/00:01:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[   37.040093] ata4.00: status: { DRDY }
[   37.040106] ata4: soft resetting link
[   37.290213] ata4.00: configured for UDMA/133
[   37.320539] ata4.01: configured for UDMA/133
[   37.320547] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[   52.320082] ata4.00: qc timeout (cmd 0xe7)
[   52.320085] ata4.00: FLUSH failed Emask 0x4
[   52.320098] ata4: soft resetting link
[   52.560187] ata4.00: configured for UDMA/133
[   52.580464] ata4.01: configured for UDMA/133
[   52.580469] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[   67.580042] ata4.00: qc timeout (cmd 0xe7)
[   67.580045] ata4.00: FLUSH failed Emask 0x4
[   67.580050] ata4.00: limiting speed to UDMA/133:PIO3
[   67.580059] ata4: soft resetting link
[   67.820175] ata4.00: configured for UDMA/133
[   67.840399] ata4.01: configured for UDMA/133
[   67.840404] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[   97.840047] ata4.00: qc timeout (cmd 0xe7)
[   97.840051] ata4.00: FLUSH failed Emask 0x4
[   97.840054] ata4.00: disabled
[   97.840063] ata4.00: device reported invalid CHS sector 0
[   97.840078] ata4: soft resetting link
[   98.040997] ata4.01: configured for UDMA/133
[   98.041020] ata4: EH complete
[   98.041059] end_request: I/O error, dev sda, sector 0
[   98.041198] sd 3:0:0:0: [sda] READ CAPACITY(16) failed
[   98.041202] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   98.041207] sd 3:0:0:0: [sda] Sense not available.
[   98.041256] sd 3:0:0:0: [sda] READ CAPACITY failed
[   98.041259] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   98.041262] sd 3:0:0:0: [sda] Sense not available.
[   98.041330] sd 3:0:0:0: [sda] Asking for cache data failed
[   98.041333] sd 3:0:0:0: [sda] Assuming drive cache: write through
[   98.041340] sda: detected capacity change from 60022480896 to 0
[   99.760364] sd 3:0:0:0: [sda] READ CAPACITY(16) failed
[   99.760370] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   99.760375] sd 3:0:0:0: [sda] Sense not available.
[   99.760408] sd 3:0:0:0: [sda] READ CAPACITY failed
[   99.760410] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   99.760414] sd 3:0:0:0: [sda] Sense not available.
[   99.760461] sd 3:0:0:0: [sda] Asking for cache data failed
[   99.760464] sd 3:0:0:0: [sda] Assuming drive cache: write through
[  100.005460] aufs 2-standalone.tree-35-rcN-20100705
[  100.025566] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[  101.402704] EXT3-fs: barriers not enabled
[  101.404460] kjournald starting.  Commit interval 5 seconds
[  101.405305] EXT3-fs (loop1): using internal journal
[  101.405310] EXT3-fs (loop1): recovery complete
[  101.405316] EXT3-fs (loop1): mounted filesystem with ordered data mode
[  101.412560] aufs test_add:252:exe[819]: uid/gid/perm //filesystem.squashfs 0/0/0755, 1000/1000/0755
[  111.824941] udev[2402]: starting version 163
[  112.170706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  112.190217] intel_rng: FWH not detected
[  112.320661] EDAC MC: Ver: 2.1.0 Sep 19 2010
[  112.348787] tpm_tis 00:0a: 1.2 TPM (device-id 0xB, rev-id 16)
[  112.372275] cfg80211: Calling CRDA to update world regulatory domain
[  112.374783] EDAC MC0: Giving out device to 'i5400_edac.c' 'I5400': DEV 0000:00:10.0
[  112.374815] EDAC PCI0: Giving out device to module 'i5400_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[  112.525753] ppdev: user-space parallel port driver
[  112.610559] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[  112.651668] cfg80211: World regulatory domain updated:
[  112.651673]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  112.651678]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  112.651681]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  112.651684]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  112.651687]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  112.651690]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  112.670233] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[  112.671018] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  112.702778] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[  112.740571] ath5k 0000:20:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  112.740714] ath5k 0000:20:04.0: registered as 'phy0'
[  112.764476] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[  112.765295] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  112.911461]   alloc irq_desc for 17 on node -1
[  112.911466]   alloc kstat_irqs on node -1
[  112.911478] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  112.911581]   alloc irq_desc for 72 on node -1
[  112.911584]   alloc kstat_irqs on node -1
[  112.911596] HDA Intel 0000:00:1b.0: irq 72 for MSI/MSI-X
[  112.911632] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  113.018619] hda_codec: ALC888: BIOS auto-probing.
[  113.340312] ath: EEPROM regdomain: 0x10
[  113.340319] ath: EEPROM indicates we should expect a direct regpair map
[  113.340324] ath: Country alpha2 being used: CO
[  113.340326] ath: Regpair used: 0x10
[  113.380141] phy0: Selected rate control algorithm 'minstrel'
[  113.380920] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  113.381160] cfg80211: Calling CRDA for country: CO
[  113.392993] cfg80211: Regulatory domain changed to country: CO
[  113.392998]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  113.393002]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  113.393005]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[  113.393008]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[  113.393011]     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[  113.402469] parport_pc 00:09: reported by Plug and Play ACPI
[  113.402594] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  113.418622] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  113.550952] lp0: using parport0 (interrupt-driven).
[  114.699609] [drm] nouveau 0000:05:00.0: Allocating FIFO number 2
[  114.711194] [drm] nouveau 0000:05:00.0: nouveau_channel_alloc: initialised FIFO 2
[  115.459348] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[  115.460353] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  125.540028] eth0: no IPv6 routers present
[ 2293.339822] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2293.650008] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2293.650014] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2294.094056] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2294.404240] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2294.846201] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2294.846207] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2295.156383] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2295.156391] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2295.602323] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2295.602331] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2295.912502] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2295.912509] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2296.356519] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2296.356529] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2296.666699] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2296.666709] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2297.110824] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2297.110834] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2297.421006] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2297.861777] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2297.861786] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2298.171961] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2298.171970] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2298.616895] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2298.616903] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2298.927075] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2298.927085] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2300.694578] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2300.694587] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2301.004761] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2301.004770] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2305.036509] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2305.036517] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2305.346687] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2305.346692] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2305.346700] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2306.666937] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2306.666947] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 2306.981848] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 2306.981861] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4298.338574] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4298.338583] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4298.648732] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4298.648739] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4299.088581] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4299.088591] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4299.398763] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4299.398771] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4299.839767] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4299.839775] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4300.149948] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4300.149957] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4300.595084] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4300.595092] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4300.905265] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4300.905273] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4301.348420] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4301.348428] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4301.658601] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4302.097606] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4302.097615] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4302.407788] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4302.846892] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4302.846901] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4303.157077] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4303.157086] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4303.595107] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4303.595116] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4303.905292] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4303.905300] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4305.666955] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4305.666963] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4305.977136] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4305.977144] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4310.010164] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4310.010173] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4310.320343] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4310.320352] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4311.637054] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4311.637060] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[ 4311.947233] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[ 4311.947241] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14241.336544] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14241.336552] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14241.646718] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14241.646727] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14242.085483] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14242.395665] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14242.395673] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14242.837845] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14242.837852] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14243.148029] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14243.590930] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14243.590939] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14243.901113] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14244.342984] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14244.342992] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14244.653168] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14245.092771] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14245.092780] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14245.402953] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14245.402961] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14245.848040] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14245.848048] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14246.158224] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14246.158233] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14246.600140] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14246.600148] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14246.910322] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14246.910331] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14248.676451] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14248.676460] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14248.986633] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14248.986642] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14253.011413] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14253.011421] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14253.321595] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14253.321602] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14254.643188] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14254.643198] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[14254.953373] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[14254.953381] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16704.971341] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16704.971349] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16705.281515] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16705.281524] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16705.724296] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16705.724304] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16706.034477] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16706.034485] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16706.480776] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16706.480784] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16706.790956] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16706.790965] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16707.232027] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16707.542208] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16707.542216] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16707.984017] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16707.984026] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16708.294198] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16708.735990] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16708.735998] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16709.046171] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16709.482912] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16709.793089] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16709.793099] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16710.235362] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16710.235370] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16710.545543] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16710.545552] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16712.308092] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16712.618273] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16712.618281] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16716.647319] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16716.647327] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16716.957501] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16716.957510] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16718.272614] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16718.272622] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[16718.582796] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[16718.582805] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17700.974590] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17700.974597] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17701.284766] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17701.284774] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17701.728655] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17701.728664] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17702.038838] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17702.038846] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17702.481841] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17702.481849] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17702.792021] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17702.792028] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17703.231995] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17703.542174] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17703.542183] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17703.982150] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17703.982158] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17704.292330] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17704.292339] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17704.736346] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17704.736355] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17705.046525] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17705.491747] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17705.491755] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17705.801927] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17706.247830] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17706.247838] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17706.558010] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17706.558019] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17708.326296] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17708.636480] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17708.636487] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17712.671296] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17712.671304] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17712.981477] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17712.981485] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17714.297062] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17714.297070] [drm] nouveau 0000:05:00.0: unplugged DVI-I-1
[17714.607244] [drm] nouveau 0000:05:00.0: plugged DVI-I-1
[17714.607253] [drm] nouveau 0000:05:00.0: plugged DVI-I-1

```

---

### Post by srs5694 on 2011-08-20
There are several lines in the dmesg output that are informative:

> ```

[    4.610175] ata4.00: ATA-8: OCZ-VERTEX2, 1.33, max UDMA/133
[    4.610179] ata4.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
...
[    4.670906] scsi 3:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.33 PQ: 0 ANSI: 5
[    4.671110] sd 3:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.671121] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.671191] sd 3:0:0:0: [sda] Write Protect is off
[    4.671194] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.671234] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
[    4.671610]  sda:
[    4.671912]  sda1 sda2
...
[    6.212175] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   37.040053] ata4: lost interrupt (Status 0x50)
[   37.040075] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   37.040079] ata4.00: failed command: FLUSH CACHE
[   37.040088] ata4.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   37.040089]          res 40/00:01:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[   37.040093] ata4.00: status: { DRDY }
[   37.040106] ata4: soft resetting link
...
[   98.041059] end_request: I/O error, dev sda, sector 0
[   98.041198] sd 3:0:0:0: [sda] READ CAPACITY(16) failed
[   98.041202] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   98.041207] sd 3:0:0:0: [sda] Sense not available.
[   98.041256] sd 3:0:0:0: [sda] READ CAPACITY failed
[   98.041259] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   98.041262] sd 3:0:0:0: [sda] Sense not available.
[   98.041330] sd 3:0:0:0: [sda] Asking for cache data failed
[   98.041333] sd 3:0:0:0: [sda] Assuming drive cache: write through
[   98.041340] sda: detected capacity change from 60022480896 to 0
[   99.760364] sd 3:0:0:0: [sda] READ CAPACITY(16) failed
[   99.760370] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   99.760375] sd 3:0:0:0: [sda] Sense not available.
[   99.760408] sd 3:0:0:0: [sda] READ CAPACITY failed
[   99.760410] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   99.760414] sd 3:0:0:0: [sda] Sense not available.
[   99.760461] sd 3:0:0:0: [sda] Asking for cache data failed
[   99.760464] sd 3:0:0:0: [sda] Assuming drive cache: write through

```

In this output, "ata4.00" is another name for /dev/sda. It looks like something is causing a hardware reset on the disk. Unfortunately, I don't know enough about the specific hardware messages being reported to say what it is, but it does look like a hardware fault. Given what you say about the problem disappearing when you remove Windows and recurring when you re-install Windows, my best guess (which is *very* tentative) is that accessing certain sectors in certain ways is triggering a hardware fault that's causing the disk to disappear from the SATA bus. Presumably this precise pattern doesn't occur under Windows, or perhaps Windows recovers from it better than does Linux. There's a chance that you could work around the problem by partitioning the disk in a significantly different way, but that might not be practical; and even if it were, the underlying cause would remain and might recur in the future.

My second guess would be that it's a driver bug. If so, switching to a different motherboard port (if your motherboard has more than one disk controller) might work around the problem. Upgrading the driver might also work, but for that you'll need to upgrade the kernel; downgrading is less likely to work, although it might if you've got sufficiently old hardware. (With newer hardware, it's much more likely for bugs to be fixed in later versions; with old hardware, new bugs sometimes creep in temporarily with increases in version numbers.)

Perhaps somebody else will have more suggestions, but that's about all I can think of at the moment.

Best of luck getting this fixed!

---

### Post by oldfred on 2011-08-20
You say shiny new computer, are you using the new SATA3 6GB/s ports? and are you using a Intel internal video not a separate video card? Those I believe have been reported as issues, but I have not followed details to know more.

---

### Post by srs5694 on 2011-08-21
> **oldfred said:**
> You say shiny new computer

It occurs to me that this could conceivably be related to UEFI vs. BIOS compatibility boot mode. If, say, the computer boots in BIOS compatibility mode when Windows is *not* installed on the SSD and in UEFI mode when Windows *is* installed on the SSD, or vice-versa, then the boot mode would be associated with Windows being installed or not installed on the disk. If there's a problem with one of the two modes that causes Ubuntu to be unable to see the disk, then that would account for the pattern you see. One possible workaround would then be to get Windows to install using whichever mode it doesn't normally use. On a new UEFI-based computer, this should be possible, but you'll need to figure out how to get the computer to switch modes.

One way to test this hypothesis is to examine the Linux kernel ring buffer, which you can do by typing "dmesg". In UEFI mode, the output will include a number of references to EFI, as in:

```

$ **dmesg | grep EFI**
[    0.000000] Command line: BOOT_IMAGE=atapi0:\EFI\ELILO\vmlinuz-2.6.38-8-generic root=/dev/seeker/u1104  ro
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000048000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000048000-0x0000000000097000) (0MB)
...
[    0.000000] Kernel command line: BOOT_IMAGE=atapi0:\EFI\ELILO\vmlinuz-2.6.38-8-generic root=/dev/seeker/u1104  ro
[    4.505149] fb0: EFI VGA frame buffer device
[    5.532814] EFI Variables Facility v0.08 2004-May-17
[   13.469888] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver

```

I've cut a number of the lines about EFI memory ranges for brevity's sake, but you can see that the output is copious. If the computer boots in BIOS mode, you'll see few or no lines that reference EFI, and if there are any such lines, they'll exist because of some coincidental match of the string "EFI", perhaps as part of another word.

Of course, you'll need to fiddle around to reconfigure the disk to get Linux to both be able to recognize it and not. If you find a correlation, post back with details, and also check your firmware's settings to find any options that refer to EFI or UEFI boot modes. (They aren't always labelled very clearly, and they vary a lot from one firmware to another. The motherboard's make and model might be useful information, since with that information I or others can track down a manual.)

---

### Post by foilboy on 2011-08-21
> **oldfred said:**
> You say shiny new computer, are you using the new SATA3 6GB/s ports? and are you using a Intel internal video not a separate video card? Those I believe have been reported as issues, but I have not followed details to know more.

SATA2.  [Here is the motherboard]("http://www.tyan.com/product_board_detail.aspx?pid=562") (bottom left is the SATA ports), and [here is the SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227550").  Also it's using a separate video card.

> **srs5694 said:**
> One way to test this hypothesis is to examine the Linux kernel ring buffer, which you can do by typing "dmesg". In UEFI mode, the output will include a number of references to EFI

I put the entire dmesg output in my previous post.  There aren't any references to EFI.  Or should I wipe the Windows installation, boot to the LiveUSB, and get that output as well?  Unless I misread your post, it should only show up when Windows is installed, but I guess that could provide other info.

> **srs5694 said:**
> Of course, you'll need to fiddle around to reconfigure the disk to get Linux to both be able to recognize it and not. If you find a correlation, post back with details, and also check your firmware's settings to find any options that refer to EFI or UEFI boot modes. (They aren't always labelled very clearly, and they vary a lot from one firmware to another. The motherboard's make and model might be useful information, since with that information I or others can track down a manual.)
I admit ignorance in even knowing where to start looking to figure out how to reconfigure the disk.  Do you just mean BIOS settings?  I can go dig around in there again and play with settings, but it doesn't look like it's using UEFI (not in the dmesg output)...

> **srs5694 said:**
> The motherboard's make and model might be useful information
The link to the mobo is higher up, the manual is [here]("http://www.tyan.com/manuals/m_s5396_120.pdf").  I searched it for "efi" and didn't see anything that looked useful.

---

### Post by srs5694 on 2011-08-21
Based on the manual's date (2007) and contents, it seems unlikely that the firmware is based on UEFI, so that pretty much nixes my UEFI differences hypothesis.

---

### Post by oldfred on 2011-08-21
Many Intel motherboards have a BIOS that will not boot without a boot flag on a primary partition. Grub does not use one, Windows does, but if BIOS needs it you have to have one. Do you have a boot flag on any primary partition on your SSD? If not put one on any primary partition or on the Windows NTFS which would normally have it anyway.

---

### Post by srs5694 on 2011-08-21
> **oldfred said:**
> Many Intel motherboards have a BIOS that will not boot without a boot flag on a primary partition. Grub does not use one, Windows does, but if BIOS needs it you have to have one. Do you have a boot flag on any primary partition on your SSD? If not put one on any primary partition or on the Windows NTFS which would normally have it anyway.

I've never heard of this BIOS bug causing the hardware to disconnect once Linux is booted. It's a simple enough thing to try and is unlikely to do any harm, so I certainly can't recommend *against* trying it, but I wouldn't hold out much hope that it would do any good.

---

### Post by foilboy on 2011-08-24
Sorry for being a little unresponsive - I'm always really busy during the week.  I'll have some time again this weekend to keep playing with it.

Thanks again!

---

### Post by foilboy on 2011-08-27
Alright, so I've had a little time today.  I wiped the Windows partition and booted into Ubuntu.  Here's the outputs of dmesg and that boot info script:

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bfef1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfef1000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF80000 mask FFFF80000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff80000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  modified: 00000000bfee0000 - 00000000bfef0000 (ACPI data)
[    0.000000]  modified: 00000000bfef0000 - 00000000bfef1000 (ACPI NVS)
[    0.000000]  modified: 00000000bfef1000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f6930] f6930
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfee0000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfee0000 page 4k
[    0.000000] kernel direct mapping tables up to bfee0000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 19000-1f000
[    0.000000] RAMDISK: 7f490000 - 80000000
[    0.000000] ACPI: RSDP 00000000000f6900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bfee90d5 0006C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bfeefd7e 000F4 (v03 INTEL  SEABURG  06040000 PTL  00000003)
[    0.000000] ACPI: DSDT 00000000bfeeb42a 048E0 (v01  Intel SEABURG  06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000bfef0fc0 00040
[    0.000000] ACPI: _MAR 00000000bfeefe72 00030 (v01 Intel  OEMDMAR  06040000 LOHR 00000001)
[    0.000000] ACPI: TCPA 00000000bfeefea2 00032 (v01 Intel  SEABURG  06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 00000000bfeefed4 000C8 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000bfeeff9c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bfeeffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bfeea5ec 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 00000000bfeea546 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 00000000bfee9141 01405 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff8801039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bfee0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048173
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3925 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767768 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec88000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec88000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfef0000
[    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bfef1000
[    0.000000] PM: Registered nosave memory: 00000000bfef1000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030253
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (61 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [007f490000 - 0080000000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18158]             BRK
[    0.000000]   #4 [00000f6940 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f6930 - 00000f6940]    MP-table mpf
[    0.000000]   #6 [000009d800 - 000009dd71]   BIOS reserved
[    0.000000]   #7 [000009df5d - 00000f6930]   BIOS reserved
[    0.000000]   #8 [000009dd71 - 000009df5d]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 000001a000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18180 - 0001d19180]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103a00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19180 - 0001d31180]         BOOTMEM
[    0.000000]   #21 [0001d31180 - 0001d37180]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17646]         BOOTMEM
[    0.000000]   #24 [0001d17680 - 0001d17958]         BOOTMEM
[    0.000000]   #25 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #26 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #27 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #28 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #29 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #30 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #31 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #32 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #33 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #34 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #35 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #36 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #37 [0001d17f80 - 0001d17fa0]         BOOTMEM
[    0.000000]   #38 [0001d17fc0 - 0001d17fe0]         BOOTMEM
[    0.000000]   #39 [0001d37180 - 0001d37203]         BOOTMEM
[    0.000000]   #40 [0001d37240 - 0001d372c3]         BOOTMEM
[    0.000000]   #41 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #42 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #43 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #44 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #45 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #46 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #47 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #48 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #49 [0001d37300 - 0001d37308]         BOOTMEM
[    0.000000]   #50 [0001d37340 - 0001d37348]         BOOTMEM
[    0.000000]   #51 [0001d37380 - 0001d373a0]         BOOTMEM
[    0.000000]   #52 [0001d373c0 - 0001d37400]         BOOTMEM
[    0.000000]   #53 [0001d37400 - 0001d37520]         BOOTMEM
[    0.000000]   #54 [0001d37540 - 0001d37588]         BOOTMEM
[    0.000000]   #55 [0001d375c0 - 0001d37608]         BOOTMEM
[    0.000000]   #56 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #57 [0001fde000 - 0005fde000]         BOOTMEM
[    0.000000]   #58 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #59 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #60 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4043080k/5242880k available (5708k kernel code, 1050188k absent, 149612k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:1152
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.906 MHz processor.
[    0.020013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.81 BogoMIPS (lpj=18619060)
[    0.020018] pid_max: default: 32768 minimum: 301
[    0.020058] Security Framework initialized
[    0.020087] AppArmor: AppArmor initialized
[    0.020089] Yama: becoming mindful.
[    0.020688] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.023456] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.024725] Mount-cache hash table entries: 256
[    0.024939] Initializing cgroup subsys ns
[    0.024947] Initializing cgroup subsys cpuacct
[    0.024952] Initializing cgroup subsys memory
[    0.024966] Initializing cgroup subsys devices
[    0.024969] Initializing cgroup subsys freezer
[    0.024972] Initializing cgroup subsys net_cls
[    0.025014] CPU: Physical Processor ID: 0
[    0.025016] CPU: Processor Core ID: 0
[    0.025019] mce: CPU supports 6 MCE banks
[    0.025029] CPU0: Thermal monitoring enabled (TM2)
[    0.025034] using mwait in idle threads.
[    0.025037] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.025044] PEBS disabled due to CPU errata.
[    0.025049] ... version:                2
[    0.025051] ... bit width:              40
[    0.025053] ... generic registers:      2
[    0.025055] ... value mask:             000000ffffffffff
[    0.025057] ... max period:             000000007fffffff
[    0.025059] ... fixed-purpose events:   3
[    0.025061] ... event mask:             0000000700000003
[    0.028140] ACPI: Core revision 20100428
[    0.039549] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.039556] ftrace: allocating 22680 entries in 89 pages
[    0.040086] Setting APIC routing to flat
[    0.040491] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.149419] CPU0: Intel(R) Xeon(R) CPU           E5320  @ 1.86GHz stepping 07
[    0.150000] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    1.330010] Brought up 8 CPUs
[    1.330014] Total of 8 processors activated (29792.76 BogoMIPS).
[    1.335158] devtmpfs: initialized
[    1.335158] regulator: core version 0.5
[    1.335158] Time: 17:37:44  Date: 08/27/11
[    1.335158] NET: Registered protocol family 16
[    1.335158] ACPI: bus type pci registered
[    1.335158] Trying to unpack rootfs image as initramfs...
[    1.335158] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xe0000000-0xe1ffffff] (base 0xe0000000)
[    1.335158] PCI: MMCONFIG at [mem 0xe0000000-0xe1ffffff] reserved in E820
[    1.343901] PCI: Using configuration type 1 for base access
[    1.344777] bio: create slab <bio-0> at 0
[    1.344777] ACPI: EC: Look up EC in DSDT
[    1.350207] ACPI: SSDT 00000000bfeea84b 001DD (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.350462] ACPI: Dynamic OEM Table Load:
[    1.350466] ACPI: SSDT (null) 001DD (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.351152] ACPI: SSDT 00000000bfeeaa28 0016E (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.351410] ACPI: Dynamic OEM Table Load:
[    1.351414] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.352065] ACPI: SSDT 00000000bfeeab96 0016E (v01  PmRef  Cpu2Ist 00003000 INTL 20050228)
[    1.352320] ACPI: Dynamic OEM Table Load:
[    1.352323] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu2Ist 00003000 INTL 20050228)
[    1.352961] ACPI: SSDT 00000000bfeead04 0016E (v01  PmRef  Cpu3Ist 00003000 INTL 20050228)
[    1.353218] ACPI: Dynamic OEM Table Load:
[    1.353222] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu3Ist 00003000 INTL 20050228)
[    1.353864] ACPI: SSDT 00000000bfeeae72 0016E (v01  PmRef  CPU4Ist 00003000 INTL 20050228)
[    1.354122] ACPI: Dynamic OEM Table Load:
[    1.354126] ACPI: SSDT (null) 0016E (v01  PmRef  CPU4Ist 00003000 INTL 20050228)
[    1.354833] ACPI: SSDT 00000000bfeeafe0 0016E (v01  PmRef  CPU5Ist 00003000 INTL 20050228)
[    1.355094] ACPI: Dynamic OEM Table Load:
[    1.355097] ACPI: SSDT (null) 0016E (v01  PmRef  CPU5Ist 00003000 INTL 20050228)
[    1.355743] ACPI: SSDT 00000000bfeeb14e 0016E (v01  PmRef  Cpu6Ist 00003000 INTL 20050228)
[    1.356006] ACPI: Dynamic OEM Table Load:
[    1.356009] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu6Ist 00003000 INTL 20050228)
[    1.356654] ACPI: SSDT 00000000bfeeb2bc 0016E (v01  PmRef  Cpu7Ist 00003000 INTL 20050228)
[    1.356918] ACPI: Dynamic OEM Table Load:
[    1.356922] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu7Ist 00003000 INTL 20050228)
[    1.356987] ACPI: Interpreter enabled
[    1.356990] ACPI: (supports S0 S1 S3 S4 S5)
[    1.357013] ACPI: Using IOAPIC for interrupt routing
[    1.362337] ACPI: No dock devices found.
[    1.362341] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    1.363424] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.365522] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    1.365526] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    1.365530] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    1.365533] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    1.365536] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    1.365539] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    1.365542] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    1.365546] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xfebfffff] (ignored)
[    1.365549] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    1.365612] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.365616] pci 0000:00:00.0: PME# disabled
[    1.365679] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.365683] pci 0000:00:01.0: PME# disabled
[    1.365745] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.365749] pci 0000:00:05.0: PME# disabled
[    1.365811] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.365815] pci 0000:00:09.0: PME# disabled
[    1.366181] pci 0000:00:1b.0: reg 10: [mem 0xd3504000-0xd3507fff 64bit]
[    1.366228] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.366233] pci 0000:00:1b.0: PME# disabled
[    1.366307] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.366312] pci 0000:00:1c.0: PME# disabled
[    1.366368] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    1.366425] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    1.366486] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    1.366547] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    1.366603] pci 0000:00:1d.7: reg 10: [mem 0xd3508000-0xd35083ff]
[    1.366659] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.366664] pci 0000:00:1d.7: PME# disabled
[    1.366791] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    1.366817] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    1.366824] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    1.366831] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    1.366838] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    1.366845] pci 0000:00:1f.1: reg 20: [io  0x1880-0x188f]
[    1.366887] pci 0000:00:1f.2: reg 10: [io  0x18c0-0x18c7]
[    1.366893] pci 0000:00:1f.2: reg 14: [io  0x18b8-0x18bb]
[    1.366900] pci 0000:00:1f.2: reg 18: [io  0x18b0-0x18b7]
[    1.366906] pci 0000:00:1f.2: reg 1c: [io  0x1894-0x1897]
[    1.366913] pci 0000:00:1f.2: reg 20: [io  0x18a0-0x18af]
[    1.366919] pci 0000:00:1f.2: reg 24: [mem 0xd3508400-0xd35087ff]
[    1.366942] pci 0000:00:1f.2: PME# supported from D3hot
[    1.366946] pci 0000:00:1f.2: PME# disabled
[    1.366997] pci 0000:00:1f.3: reg 20: [io  0x1100-0x111f]
[    1.367064] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.367069] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.367073] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.367079] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.367137] pci 0000:05:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    1.367147] pci 0000:05:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.367158] pci 0000:05:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit]
[    1.367164] pci 0000:05:00.0: reg 24: [io  0x2000-0x207f]
[    1.367171] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    1.380016] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    1.380022] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    1.380026] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    1.380033] pci 0000:00:05.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.380141] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    1.380145] pci 0000:09:00.0: PME# disabled
[    1.380210] pci 0000:09:00.3: PME# supported from D0 D3hot D3cold
[    1.380215] pci 0000:09:00.3: PME# disabled
[    1.380232] pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.380243] pci 0000:00:09.0: PCI bridge to [bus 09-10]
[    1.380247] pci 0000:00:09.0:   bridge window [io  0x3000-0x3fff]
[    1.380251] pci 0000:00:09.0:   bridge window [mem 0xd3000000-0xd31fffff]
[    1.380256] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.380353] pci 0000:0a:00.0: PME# supported from D0 D3hot D3cold
[    1.380357] pci 0000:0a:00.0: PME# disabled
[    1.380372] pci 0000:0a:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.380441] pci 0000:0a:02.0: PME# supported from D0 D3hot D3cold
[    1.380446] pci 0000:0a:02.0: PME# disabled
[    1.380460] pci 0000:0a:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.380493] pci 0000:09:00.0: PCI bridge to [bus 0a-0f]
[    1.380497] pci 0000:09:00.0:   bridge window [io  0x3000-0x3fff]
[    1.380501] pci 0000:09:00.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    1.380508] pci 0000:09:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.380553] pci 0000:0a:00.0: PCI bridge to [bus 0b-0b]
[    1.380557] pci 0000:0a:00.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.380562] pci 0000:0a:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.380569] pci 0000:0a:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.380640] pci 0000:0f:00.0: reg 10: [mem 0xd3000000-0xd301ffff]
[    1.380653] pci 0000:0f:00.0: reg 18: [io  0x3000-0x301f]
[    1.380706] pci 0000:0f:00.0: PME# supported from D0 D3hot D3cold
[    1.380711] pci 0000:0f:00.0: PME# disabled
[    1.380755] pci 0000:0f:00.1: reg 10: [mem 0xd3020000-0xd303ffff]
[    1.380768] pci 0000:0f:00.1: reg 18: [io  0x3020-0x303f]
[    1.380821] pci 0000:0f:00.1: PME# supported from D0 D3hot D3cold
[    1.380826] pci 0000:0f:00.1: PME# disabled
[    1.380850] pci 0000:0f:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.380863] pci 0000:0a:02.0: PCI bridge to [bus 0f-0f]
[    1.380867] pci 0000:0a:02.0:   bridge window [io  0x3000-0x3fff]
[    1.380872] pci 0000:0a:02.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    1.380878] pci 0000:0a:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.380964] pci 0000:09:00.3: PCI bridge to [bus 10-10]
[    1.380969] pci 0000:09:00.3:   bridge window [io  0xf000-0x0000] (disabled)
[    1.380974] pci 0000:09:00.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.380980] pci 0000:09:00.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.381037] pci 0000:00:1c.0: PCI bridge to [bus 1f-1f]
[    1.381041] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.381046] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.381053] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.381113] pci 0000:20:04.0: reg 10: [mem 0xd3200000-0xd320ffff]
[    1.381199] pci 0000:20:05.0: reg 10: [mem 0xd3214000-0xd32147ff]
[    1.381207] pci 0000:20:05.0: reg 14: [mem 0xd3210000-0xd3213fff]
[    1.381256] pci 0000:20:05.0: supports D1 D2
[    1.381259] pci 0000:20:05.0: PME# supported from D0 D1 D2 D3hot
[    1.381264] pci 0000:20:05.0: PME# disabled
[    1.381320] pci 0000:00:1e.0: PCI bridge to [bus 20-20] (subtractive decode)
[    1.381325] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.381337] pci 0000:00:1e.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    1.381344] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.381347] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    1.381351] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[    1.381375] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.381674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.381761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.381831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    1.381902] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0._PRT]
[    1.382042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0.BPD0._PRT]
[    1.382124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0.BPD2._PRT]
[    1.382195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMF3._PRT]
[    1.382299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.382396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.393699] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 14 15) *9
[    1.393802] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 14 15)
[    1.393901] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[    1.393999] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[    1.394097] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    1.394196] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 6 7 10 *11 14 15)
[    1.394293] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 *15)
[    1.394391] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 6 7 *10 11 14 15)
[    1.394441] HEST: Table is not found!
[    1.394537] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.394545] vgaarb: loaded
[    1.394710] SCSI subsystem initialized
[    1.394729] libata version 3.00 loaded.
[    1.394729] usbcore: registered new interface driver usbfs
[    1.394729] usbcore: registered new interface driver hub
[    1.394729] usbcore: registered new device driver usb
[    1.394729] ACPI: WMI: Mapper loaded
[    1.394729] PCI: Using ACPI for IRQ routing
[    1.394729] PCI: pci_cache_line_size set to 64 bytes
[    1.394729] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.394729] reserve RAM buffer: 00000000bfee0000 - 00000000bfffffff 
[    1.394729] NetLabel: Initializing
[    1.394729] NetLabel:  domain hash size = 128
[    1.394729] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.394729] NetLabel:  unlabeled traffic allowed by default
[    1.394729] hpet clockevent registered
[    1.394729] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    1.394729] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.394729] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    3.520090] Switching to clocksource tsc
[    3.535070] AppArmor: AppArmor Filesystem Enabled
[    3.535106] pnp: PnP ACPI init
[    3.535140] ACPI: bus type pnp registered
[    3.539492] pnp: PnP ACPI: found 11 devices
[    3.539497] ACPI: ACPI bus type pnp unregistered
[    3.539525] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    3.539529] system 00:01: [io  0x0800-0x080f] has been reserved
[    3.539532] system 00:01: [io  0x1000-0x107f] has been reserved
[    3.539536] system 00:01: [io  0x1180-0x11bf] has been reserved
[    3.539540] system 00:01: [io  0xfe00] has been reserved
[    3.539547] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    3.539550] system 00:01: [mem 0xfee00000-0xfee0ffff] could not be reserved
[    3.539554] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    3.539557] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    3.539560] system 00:01: [mem 0xfec88000-0xfec88fff] could not be reserved
[    3.539564] system 00:01: [mem 0xfe000000-0xfe01ffff] has been reserved
[    3.539567] system 00:01: [mem 0xfe600000-0xfe6fffff] has been reserved
[    3.546394] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd3300000-0xd34fffff]
[    3.546402] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.546407] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    3.546411] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.546414] pci 0000:00:01.0:   bridge window [io  disabled]
[    3.546418] pci 0000:00:01.0:   bridge window [mem disabled]
[    3.546423] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    3.546430] pci 0000:05:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    3.546433] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    3.546437] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    3.546441] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    3.546446] pci 0000:00:05.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.546452] pci 0000:0a:00.0: PCI bridge to [bus 0b-0b]
[    3.546454] pci 0000:0a:00.0:   bridge window [io  disabled]
[    3.546459] pci 0000:0a:00.0:   bridge window [mem disabled]
[    3.546464] pci 0000:0a:00.0:   bridge window [mem pref disabled]
[    3.546471] pci 0000:0a:02.0: PCI bridge to [bus 0f-0f]
[    3.546474] pci 0000:0a:02.0:   bridge window [io  0x3000-0x3fff]
[    3.546480] pci 0000:0a:02.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    3.546484] pci 0000:0a:02.0:   bridge window [mem pref disabled]
[    3.546491] pci 0000:09:00.0: PCI bridge to [bus 0a-0f]
[    3.546495] pci 0000:09:00.0:   bridge window [io  0x3000-0x3fff]
[    3.546500] pci 0000:09:00.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    3.546505] pci 0000:09:00.0:   bridge window [mem pref disabled]
[    3.546512] pci 0000:09:00.3: PCI bridge to [bus 10-10]
[    3.546514] pci 0000:09:00.3:   bridge window [io  disabled]
[    3.546519] pci 0000:09:00.3:   bridge window [mem disabled]
[    3.546523] pci 0000:09:00.3:   bridge window [mem pref disabled]
[    3.546530] pci 0000:00:09.0: PCI bridge to [bus 09-10]
[    3.546533] pci 0000:00:09.0:   bridge window [io  0x3000-0x3fff]
[    3.546538] pci 0000:00:09.0:   bridge window [mem 0xd3000000-0xd31fffff]
[    3.546541] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    3.546547] pci 0000:00:1c.0: PCI bridge to [bus 1f-1f]
[    3.546550] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    3.546556] pci 0000:00:1c.0:   bridge window [mem 0xd3300000-0xd34fffff]
[    3.546561] pci 0000:00:1c.0:   bridge window [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.546568] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    3.546570] pci 0000:00:1e.0:   bridge window [io  disabled]
[    3.546576] pci 0000:00:1e.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    3.546580] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    3.546614]   alloc irq_desc for 16 on node -1
[    3.546617]   alloc kstat_irqs on node -1
[    3.546634] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.546640] pci 0000:00:01.0: setting latency timer to 64
[    3.546649] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.546653] pci 0000:00:05.0: setting latency timer to 64
[    3.546661] pci 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.546665] pci 0000:00:09.0: setting latency timer to 64
[    3.546678] pci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.546682] pci 0000:09:00.0: setting latency timer to 64
[    3.546692] pci 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.546697] pci 0000:0a:00.0: setting latency timer to 64
[    3.546707]   alloc irq_desc for 18 on node -1
[    3.546709]   alloc kstat_irqs on node -1
[    3.546714] pci 0000:0a:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.546718] pci 0000:0a:02.0: setting latency timer to 64
[    3.546729] pci 0000:09:00.3: setting latency timer to 64
[    3.546739]   alloc irq_desc for 21 on node -1
[    3.546741]   alloc kstat_irqs on node -1
[    3.546745] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.546750] pci 0000:00:1c.0: setting latency timer to 64
[    3.546758] pci 0000:00:1e.0: setting latency timer to 64
[    3.546763] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    3.546765] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    3.546768] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    3.546771] pci_bus 0000:05: resource 1 [mem 0xd0000000-0xd2ffffff]
[    3.546774] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.546777] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    3.546779] pci_bus 0000:09: resource 1 [mem 0xd3000000-0xd31fffff]
[    3.546782] pci_bus 0000:0a: resource 0 [io  0x3000-0x3fff]
[    3.546784] pci_bus 0000:0a: resource 1 [mem 0xd3000000-0xd30fffff]
[    3.546787] pci_bus 0000:0f: resource 0 [io  0x3000-0x3fff]
[    3.546790] pci_bus 0000:0f: resource 1 [mem 0xd3000000-0xd30fffff]
[    3.546793] pci_bus 0000:1f: resource 0 [io  0x4000-0x4fff]
[    3.546795] pci_bus 0000:1f: resource 1 [mem 0xd3300000-0xd34fffff]
[    3.546798] pci_bus 0000:1f: resource 2 [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.546801] pci_bus 0000:20: resource 1 [mem 0xd3200000-0xd32fffff]
[    3.546803] pci_bus 0000:20: resource 4 [io  0x0000-0xffff]
[    3.546806] pci_bus 0000:20: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    3.546883] NET: Registered protocol family 2
[    3.547154] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.548998] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.554041] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.554679] TCP: Hash tables configured (established 524288 bind 65536)
[    3.554682] TCP reno registered
[    3.554694] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    3.554748] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    3.554970] NET: Registered protocol family 1
[    3.555134] pci 0000:00:1f.0: rerouting interrupts for [8086:2670]
[    3.555163] pci 0000:05:00.0: Boot video device
[    3.555172] PCI: CLS mismatch (32 != 64), using 64 bytes
[    3.555187] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.555190] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    3.555193] software IO TLB at phys 0x1fde000 - 0x5fde000
[    3.555273] Simple Boot Flag at 0x40 set to 0x1
[    3.555919] Scanning for low memory corruption every 60 seconds
[    3.556098] audit: initializing netlink socket (disabled)
[    3.556112] type=2000 audit(1314466665.550:1): initialized
[    3.572918] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.575017] VFS: Disk quotas dquot_6.5.2
[    3.575086] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.575791] fuse init (API version 7.14)
[    3.575909] msgmni has been set to 7896
[    3.578611] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.578614] io scheduler noop registered
[    3.578616] io scheduler deadline registered
[    3.578660] io scheduler cfq registered (default)
[    3.578823] pcieport 0000:00:01.0: setting latency timer to 64
[    3.578854]   alloc irq_desc for 64 on node -1
[    3.578856]   alloc kstat_irqs on node -1
[    3.578882] pcieport 0000:00:01.0: irq 64 for MSI/MSI-X
[    3.578954] pcieport 0000:00:05.0: setting latency timer to 64
[    3.578980]   alloc irq_desc for 65 on node -1
[    3.578982]   alloc kstat_irqs on node -1
[    3.578990] pcieport 0000:00:05.0: irq 65 for MSI/MSI-X
[    3.579056] pcieport 0000:00:09.0: setting latency timer to 64
[    3.579082]   alloc irq_desc for 66 on node -1
[    3.579084]   alloc kstat_irqs on node -1
[    3.579091] pcieport 0000:00:09.0: irq 66 for MSI/MSI-X
[    3.579160] pcieport 0000:00:1c.0: setting latency timer to 64
[    3.579194]   alloc irq_desc for 67 on node -1
[    3.579196]   alloc kstat_irqs on node -1
[    3.579204] pcieport 0000:00:1c.0: irq 67 for MSI/MSI-X
[    3.579294] pcieport 0000:09:00.0: setting latency timer to 64
[    3.579370] pcieport 0000:0a:00.0: setting latency timer to 64
[    3.579404]   alloc irq_desc for 68 on node -1
[    3.579406]   alloc kstat_irqs on node -1
[    3.579415] pcieport 0000:0a:00.0: irq 68 for MSI/MSI-X
[    3.579476] pcieport 0000:0a:02.0: setting latency timer to 64
[    3.579509]   alloc irq_desc for 69 on node -1
[    3.579511]   alloc kstat_irqs on node -1
[    3.579521] pcieport 0000:0a:02.0: irq 69 for MSI/MSI-X
[    3.579592] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    3.579599] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    3.579606] aer 0000:00:09.0:pcie02: AER service couldn't init device: no _OSC support
[    3.579631] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.579681] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.579780] intel_idle: MWAIT substates: 0x20
[    3.579783] intel_idle: does not run on family 6 model 15
[    3.579920] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0C:00/input/input0
[    3.579928] ACPI: Power Button [PWRB]
[    3.579980] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.579984] ACPI: Power Button [PWRF]
[    3.580187] ACPI: acpi_idle registered with cpuidle
[    4.292756] ERST: Table is not found!
[    4.292899] Linux agpgart interface v0.103
[    4.292929] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.293044] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.293450] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.294857] brd: module loaded
[    4.295473] loop: module loaded
[    4.295669] ata_piix 0000:00:1f.1: version 2.13
[    4.295686]   alloc irq_desc for 20 on node -1
[    4.295688]   alloc kstat_irqs on node -1
[    4.295697] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.295751] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.295934] scsi0 : ata_piix
[    4.296053] scsi1 : ata_piix
[    4.296573] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    4.296576] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    4.296601]   alloc irq_desc for 23 on node -1
[    4.296603]   alloc kstat_irqs on node -1
[    4.296609] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    4.296615] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.296832] ata2: port disabled. ignoring.
[    4.314316] Freeing initrd memory: 11712k freed
[    4.460674] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.460789] scsi2 : ata_piix
[    4.460931] scsi3 : ata_piix
[    4.460991] ata3: SATA max UDMA/133 cmd 0x18c0 ctl 0x18b8 bmdma 0x18a0 irq 23
[    4.460994] ata4: SATA max UDMA/133 cmd 0x18b0 ctl 0x1894 bmdma 0x18a8 irq 23
[    4.461458] Fixed MDIO Bus: probed
[    4.461500] PPP generic driver version 2.4.2
[    4.461540] tun: Universal TUN/TAP device driver, 1.6
[    4.461542] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.461644] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.461667] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.461694] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.461699] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.461752] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.461786] ehci_hcd 0000:00:1d.7: debug port 1
[    4.465680] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    4.465695] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd3508000
[    4.490678] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.490849] hub 1-0:1.0: USB hub found
[    4.490856] hub 1-0:1.0: 8 ports detected
[    4.490957] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.490974] uhci_hcd: USB Universal Host Controller Interface driver
[    4.491037] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.491044] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.491048] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.491083] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.491108] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[    4.491239] hub 2-0:1.0: USB hub found
[    4.491244] hub 2-0:1.0: 2 ports detected
[    4.491318] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.491324] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.491328] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.491367] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.491401] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[    4.491528] hub 3-0:1.0: USB hub found
[    4.491533] hub 3-0:1.0: 2 ports detected
[    4.491608]   alloc irq_desc for 22 on node -1
[    4.491610]   alloc kstat_irqs on node -1
[    4.491616] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.491623] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.491626] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.491675] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.491708] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
[    4.491835] hub 4-0:1.0: USB hub found
[    4.491840] hub 4-0:1.0: 2 ports detected
[    4.491921] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.491928] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.491931] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.491967] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.491991] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001860
[    4.492115] hub 5-0:1.0: USB hub found
[    4.492119] hub 5-0:1.0: 2 ports detected
[    4.492251] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.494965] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.494974] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.495099] mice: PS/2 mouse device common for all mice
[    4.495259] rtc_cmos 00:04: RTC can wake from S4
[    4.495307] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.495335] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.495448] device-mapper: uevent: version 1.0.3
[    4.495566] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    4.496008] device-mapper: multipath: version 1.1.1 loaded
[    4.496012] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.496924] cpuidle: using governor ladder
[    4.496927] cpuidle: using governor menu
[    4.497296] TCP cubic registered
[    4.497440] NET: Registered protocol family 10
[    4.497912] lo: Disabled Privacy Extensions
[    4.498135] NET: Registered protocol family 17
[    4.500235] PM: Resume from disk failed.
[    4.500251] registered taskstats version 1
[    4.500651]   Magic number: 7:426:644
[    4.500753] rtc_cmos 00:04: setting system clock to 2011-08-27 17:37:47 UTC (1314466667)
[    4.500773] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.500775] EDD information not available.
[    4.520849] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.620220] ata3.01: NODEV after polling detection
[    4.640257] ata3.00: ATAPI: LITE-ON DVDRW LH-16A1S, CL04, max UDMA/100
[    4.660205] ata4.00: ATA-8: OCZ-VERTEX2, 1.33, max UDMA/133
[    4.660209] ata4.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.660377] ata4.01: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    4.660383] ata4.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.680224] ata3.00: configured for UDMA/100
[    4.700210] ata4.00: configured for UDMA/133
[    4.701345] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-16A1S   CL04 PQ: 0 ANSI: 5
[    4.706894] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.706899] Uniform CD-ROM driver Revision: 3.20
[    4.707074] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.707144] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    4.720948] ata4.01: configured for UDMA/133
[    4.721115] scsi 3:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.33 PQ: 0 ANSI: 5
[    4.721259] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.721391] sd 3:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.721414] scsi 3:0:1:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    4.721493] sd 3:0:0:0: [sda] Write Protect is off
[    4.721497] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.721537] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.721559] sd 3:0:1:0: Attached scsi generic sg2 type 0
[    4.721596] sd 3:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.721718] sd 3:0:1:0: [sdb] Write Protect is off
[    4.721723] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.721805] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.721916]  sda:
[    4.722351]  sdb:
[    4.873789] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    5.120038] 
[    5.120223] sd 3:0:0:0: [sda] Attached SCSI disk
[    5.120337] sd 3:0:1:0: [sdb] Attached SCSI disk
[    5.120363] Freeing unused kernel memory: 908k freed
[    5.120801] Write protecting the kernel read-only data: 10240k
[    5.121018] Freeing unused kernel memory: 416k freed
[    5.121438] Freeing unused kernel memory: 1644k freed
[    5.151220] udev[159]: starting version 163
[    5.182024] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    5.182028] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    5.182102] e1000e 0000:0f:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.182123] e1000e 0000:0f:00.0: setting latency timer to 64
[    5.182290]   alloc irq_desc for 70 on node -1
[    5.182293]   alloc kstat_irqs on node -1
[    5.182312] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[    5.204514] [drm] Initialized drm 1.1.0 20060810
[    5.220393] Initializing USB Mass Storage driver...
[    5.220606] scsi4 : usb-storage 1-8:1.0
[    5.220798] usbcore: registered new interface driver usb-storage
[    5.220813] USB Mass Storage support registered.
[    5.222017] firewire_ohci 0000:20:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.247297] nouveau 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.247305] nouveau 0000:05:00.0: setting latency timer to 64
[    5.252497] [drm] nouveau 0000:05:00.0: Detected an NV50 generation card (0x094100a1)
[    5.261240] [drm] nouveau 0000:05:00.0: Attempting to load BIOS image from PRAMIN
[    5.261717] e1000e 0000:0f:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:e0:81:79:19:2c
[    5.261721] e1000e 0000:0f:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.261802] e1000e 0000:0f:00.0: eth0: MAC: 5, PHY: 5, PBA No: ffffff-0ff
[    5.261841]   alloc irq_desc for 19 on node -1
[    5.261843]   alloc kstat_irqs on node -1
[    5.261854] e1000e 0000:0f:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.261868] e1000e 0000:0f:00.1: setting latency timer to 64
[    5.262025]   alloc irq_desc for 71 on node -1
[    5.262027]   alloc kstat_irqs on node -1
[    5.262061] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[    5.282608] firewire_ohci: Added fw-ohci device 0000:20:05.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    5.311892] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.315193] [drm] nouveau 0000:05:00.0: ... appears to be valid
[    5.315199] [drm] nouveau 0000:05:00.0: BIT BIOS found
[    5.315202] [drm] nouveau 0000:05:00.0: Bios version 62.94.11.00
[    5.315207] [drm] nouveau 0000:05:00.0: TMDS table revision 2.0 not currently supported
[    5.315211] [drm] nouveau 0000:05:00.0: Found Display Configuration Block version 4.0
[    5.315214] [drm] nouveau 0000:05:00.0: Raw DCB entry 0: 02000300 00000028
[    5.315218] [drm] nouveau 0000:05:00.0: Raw DCB entry 1: 01000302 00020030
[    5.315221] [drm] nouveau 0000:05:00.0: Raw DCB entry 2: 04011310 00000028
[    5.315223] [drm] nouveau 0000:05:00.0: Raw DCB entry 3: 02011312 00020030
[    5.315226] [drm] nouveau 0000:05:00.0: Raw DCB entry 4: 010223f1 00c0c080
[    5.315230] [drm] nouveau 0000:05:00.0: DCB connector table: VHER 0x40 5 16 4
[    5.315234] [drm] nouveau 0000:05:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    5.315237] [drm] nouveau 0000:05:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    5.315241] [drm] nouveau 0000:05:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    5.315244] [drm] nouveau 0000:05:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    5.315247] [drm] nouveau 0000:05:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    5.315256] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 0 at offset 0xCD72
[    5.354868] e1000e 0000:0f:00.1: eth1: (PCI Express:2.5GB/s:Width x4) 00:e0:81:79:19:2d
[    5.354871] e1000e 0000:0f:00.1: eth1: Intel(R) PRO/1000 Network Connection
[    5.354953] e1000e 0000:0f:00.1: eth1: MAC: 5, PHY: 5, PBA No: ffffff-0ff
[    5.420864] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 1 at offset 0xD15B
[    5.460655] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 2 at offset 0xE0B6
[    5.460664] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 3 at offset 0xE1E5
[    5.490764] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 4 at offset 0xE3F5
[    5.490767] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table at offset 0xE45A
[    5.510908] usbcore: registered new interface driver hiddev
[    5.520678] [drm] nouveau 0000:05:00.0: 0xE45A: Condition still not met after 20ms, skipping following opcodes
[    5.520686] [drm] nouveau 0000:05:00.0: 0xBD6A: parsing output script 0
[    5.520690] [drm] nouveau 0000:05:00.0: 0xBD6A: parsing output script 0
[    5.520694] [drm] nouveau 0000:05:00.0: 0xA7A6: parsing output script 0
[    5.520701] [drm] nouveau 0000:05:00.0: Detected 512MiB VRAM
[    5.524116] input: Dynex 5-Button Wired Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
[    5.524241] generic-usb 0003:0461:4D42.0001: input,hidraw0: USB HID v1.11 Mouse [Dynex 5-Button Wired Optical Mouse] on usb-0000:00:1d.2-2/input0
[    5.524267] usbcore: registered new interface driver usbhid
[    5.524270] usbhid: USB HID core driver
[    5.604471] [TTM] Zone  kernel: Available graphics memory: 2028880 kiB.
[    5.604474] [TTM] Initializing pool allocator.
[    5.648580] [drm] nouveau 0000:05:00.0: 512 MiB GART (aperture)
[    5.648591] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[    5.649013] [drm] nouveau 0000:05:00.0: Allocating FIFO number 1
[    5.659337] [drm] nouveau 0000:05:00.0: nouveau_channel_alloc: initialised FIFO 1
[    5.660601] [drm] nouveau 0000:05:00.0: Detected a DAC output
[    5.660605] [drm] nouveau 0000:05:00.0: Detected a TMDS output
[    5.660630] [drm] nouveau 0000:05:00.0: Detected a DAC output
[    5.660633] [drm] nouveau 0000:05:00.0: Detected a TMDS output
[    5.660636] [drm] nouveau 0000:05:00.0: DCB encoder 1 unknown
[    5.660638] [drm] nouveau 0000:05:00.0: Detected a DVI-I connector
[    5.660689] [drm] nouveau 0000:05:00.0: Detected a DVI-I connector
[    5.660758] [drm] nouveau 0000:05:00.0: Detected a TV connector
[    5.660762] [drm] nouveau 0000:05:00.0:   no encoders, ignoring
[    5.770765] firewire_core: created device fw0: GUID 00e08100002804f8, S400
[    5.853479] [drm] nouveau 0000:05:00.0: allocated 1920x1200 fb: 0x40250000, bo ffff88013b20e400
[    5.854758] [drm] nouveau 0000:05:00.0: 0xBD6E: parsing output script 1
[    5.854770] [drm] nouveau 0000:05:00.0: 0xBD6F: parsing output script 2
[    5.854796] [drm] nouveau 0000:05:00.0: 0xBA7F: parsing clock script 0
[    5.855093] [drm] nouveau 0000:05:00.0: 0xB32D: parsing clock script 1
[    5.856469] Console: switching to colour frame buffer device 240x75
[    5.858775] fb0: nouveaufb frame buffer device
[    5.858777] drm: registered panic notifier
[    5.858781] Slow work thread pool: Starting up
[    5.858911] Slow work thread pool: Ready
[    5.858918] [drm] Initialized nouveau 0.0.16 20090420 for 0000:05:00.0 on minor 0
[    6.160997] Btrfs loaded
[    6.167653] xor: automatically using best checksumming function: generic_sse
[    6.210613]    generic_sse:  6635.600 MB/sec
[    6.210616] xor: using function: generic_sse (6635.600 MB/sec)
[    6.213380] device-mapper: dm-raid45: initialized v0.2594b
[    6.215145] scsi 4:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[    6.216158] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.216824] sd 4:0:0:0: [sdc] 2013184 512-byte logical blocks: (1.03 GB/983 MiB)
[    6.217360] sd 4:0:0:0: [sdc] Write Protect is off
[    6.217364] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    6.217368] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.219480] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.219488]  sdc: sdc1
[    6.224752] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.224757] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    6.430777] aufs 2-standalone.tree-35-rcN-20100705
[    6.449195] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    7.339212] EXT3-fs: barriers not enabled
[    7.502323] kjournald starting.  Commit interval 5 seconds
[    7.502371] EXT3-fs (loop1): using internal journal
[    7.502385] ext3_orphan_cleanup: deleting unreferenced inode 4246
[    7.507110] ext3_orphan_cleanup: deleting unreferenced inode 4244
[    7.507125] ext3_orphan_cleanup: deleting unreferenced inode 16
[    7.507870] ext3_orphan_cleanup: deleting unreferenced inode 15
[    7.507909] ext3_orphan_cleanup: deleting unreferenced inode 14
[    7.507922] EXT3-fs (loop1): 5 orphan inodes deleted
[    7.507926] EXT3-fs (loop1): recovery complete
[    7.508258] EXT3-fs (loop1): mounted filesystem with ordered data mode
[    7.514953] aufs test_add:252:exe[743]: uid/gid/perm //filesystem.squashfs 0/0/0755, 1000/1000/0755
[   48.971887] udev[2331]: starting version 163
[   49.339505] intel_rng: FWH not detected
[   49.402402] EDAC MC: Ver: 2.1.0 Sep 19 2010
[   49.454337] cfg80211: Calling CRDA to update world regulatory domain
[   49.455924] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.465581] EDAC MC0: Giving out device to 'i5400_edac.c' 'I5400': DEV 0000:00:10.0
[   49.465613] EDAC PCI0: Giving out device to module 'i5400_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[   49.560410] parport_pc 00:09: reported by Plug and Play ACPI
[   49.560530] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   49.634779] tpm_tis 00:0a: 1.2 TPM (device-id 0xB, rev-id 16)
[   49.715009] ath5k 0000:20:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   49.715108] ath5k 0000:20:04.0: registered as 'phy0'
[   49.727272] ppdev: user-space parallel port driver
[   49.771780] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[   49.819916] cfg80211: World regulatory domain updated:
[   49.819922]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   49.819925]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.819929]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   49.819932]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   49.819935]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.819938]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.831452] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[   49.832216] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.861549] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[   49.920161] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[   49.920911] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   49.985440]   alloc irq_desc for 17 on node -1
[   49.985445]   alloc kstat_irqs on node -1
[   49.985458] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   49.985557]   alloc irq_desc for 72 on node -1
[   49.985567]   alloc kstat_irqs on node -1
[   49.985579] HDA Intel 0000:00:1b.0: irq 72 for MSI/MSI-X
[   49.985625] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   50.120928] hda_codec: ALC888: BIOS auto-probing.
[   50.314862] ath: EEPROM regdomain: 0x10
[   50.314867] ath: EEPROM indicates we should expect a direct regpair map
[   50.314871] ath: Country alpha2 being used: CO
[   50.314873] ath: Regpair used: 0x10
[   50.349658] phy0: Selected rate control algorithm 'minstrel'
[   50.350487] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   50.350925] cfg80211: Calling CRDA for country: CO
[   50.366307] cfg80211: Regulatory domain changed to country: CO
[   50.366312]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.366315]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.366319]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   50.366322]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   50.366325]     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   50.405895] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.372073] [drm] nouveau 0000:05:00.0: Allocating FIFO number 2
[   51.383601] [drm] nouveau 0000:05:00.0: nouveau_channel_alloc: initialised FIFO 2
[   52.929472] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   52.930475] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   56.991396] ata4: lost interrupt (Status 0x58)
[   56.991785] ata4: drained 512 bytes to clear DRQ.
[   56.991795] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   56.991801] ata4.00: failed command: IDENTIFY DEVICE
[   56.991808] ata4.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   56.991810]          res 40/00:00:00:00:00/00:00:00:00:00/10 Emask 0x4 (timeout)
[   56.991813] ata4.00: status: { DRDY }
[   56.991825] ata4: soft resetting link
[   57.234582] ata4.00: configured for UDMA/133
[   57.255450] ata4.01: configured for UDMA/133
[   57.255488] ata4: EH complete
[   60.830750] lp0: using parport0 (interrupt-driven).
[   63.460034] eth1: no IPv6 routers present

```

boot info script:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.......(+.4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1427200 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1030 MB, 1030750208 bytes
32 heads, 62 sectors/track, 1014 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     2,011,775     2,011,714   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       39c56a6e-99d5-45ed-a94d-765baf251afa   ext3       
/dev/sdc1        BF52-4BB0                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

I'm going to try installing an older version of Windows (I have an XP disc around somewhere...) to see if the drive shows up when that is installed.

---

### Post by foilboy on 2011-08-27
Same problem with Windows XP - can't see the drive once it's installed.  Here are the dmesg and boot info script outputs with XP installed.

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bfef1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfef1000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF80000 mask FFFF80000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff80000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  modified: 00000000bfee0000 - 00000000bfef0000 (ACPI data)
[    0.000000]  modified: 00000000bfef0000 - 00000000bfef1000 (ACPI NVS)
[    0.000000]  modified: 00000000bfef1000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f6930] f6930
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfee0000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfee0000 page 4k
[    0.000000] kernel direct mapping tables up to bfee0000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 19000-1f000
[    0.000000] RAMDISK: 7f490000 - 80000000
[    0.000000] ACPI: RSDP 00000000000f6900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bfee90d5 0006C (v01 PTLTD  ? XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bfeefd7e 000F4 (v03 INTEL  SEABURG  06040000 PTL  00000003)
[    0.000000] ACPI: DSDT 00000000bfeeb42a 048E0 (v01  Intel SEABURG  06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000bfef0fc0 00040
[    0.000000] ACPI: _MAR 00000000bfeefe72 00030 (v01 Intel  OEMDMAR  06040000 LOHR 00000001)
[    0.000000] ACPI: TCPA 00000000bfeefea2 00032 (v01 Intel  SEABURG  06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 00000000bfeefed4 000C8 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000bfeeff9c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bfeeffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bfeea5ec 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 00000000bfeea546 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050228)
[    0.000000] ACPI: SSDT 00000000bfee9141 01405 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff8801039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bfee0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048173
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3925 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767768 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec88000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 32, address 0xfec88000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfef0000
[    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bfef1000
[    0.000000] PM: Registered nosave memory: 00000000bfef1000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030253
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (61 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [007f490000 - 0080000000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d18158]             BRK
[    0.000000]   #4 [00000f6940 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f6930 - 00000f6940]    MP-table mpf
[    0.000000]   #6 [000009d800 - 000009dd71]   BIOS reserved
[    0.000000]   #7 [000009df5d - 00000f6930]   BIOS reserved
[    0.000000]   #8 [000009dd71 - 000009df5d]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 000001a000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18180 - 0001d19180]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103a00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19180 - 0001d31180]         BOOTMEM
[    0.000000]   #21 [0001d31180 - 0001d37180]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17646]         BOOTMEM
[    0.000000]   #24 [0001d17680 - 0001d17958]         BOOTMEM
[    0.000000]   #25 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #26 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #27 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #28 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #29 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #30 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #31 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #32 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #33 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #34 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #35 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #36 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #37 [0001d17f80 - 0001d17fa0]         BOOTMEM
[    0.000000]   #38 [0001d17fc0 - 0001d17fe0]         BOOTMEM
[    0.000000]   #39 [0001d37180 - 0001d37203]         BOOTMEM
[    0.000000]   #40 [0001d37240 - 0001d372c3]         BOOTMEM
[    0.000000]   #41 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #42 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #43 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #44 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #45 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #46 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #47 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #48 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #49 [0001d37300 - 0001d37308]         BOOTMEM
[    0.000000]   #50 [0001d37340 - 0001d37348]         BOOTMEM
[    0.000000]   #51 [0001d37380 - 0001d373a0]         BOOTMEM
[    0.000000]   #52 [0001d373c0 - 0001d37400]         BOOTMEM
[    0.000000]   #53 [0001d37400 - 0001d37520]         BOOTMEM
[    0.000000]   #54 [0001d37540 - 0001d37588]         BOOTMEM
[    0.000000]   #55 [0001d375c0 - 0001d37608]         BOOTMEM
[    0.000000]   #56 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #57 [0001fde000 - 0005fde000]         BOOTMEM
[    0.000000]   #58 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #59 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #60 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4043080k/5242880k available (5708k kernel code, 1050188k absent, 149612k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:1152
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.934 MHz processor.
[    0.020013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.86 BogoMIPS (lpj=18619340)
[    0.020018] pid_max: default: 32768 minimum: 301
[    0.020058] Security Framework initialized
[    0.020088] AppArmor: AppArmor initialized
[    0.020090] Yama: becoming mindful.
[    0.020687] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.023427] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.024690] Mount-cache hash table entries: 256
[    0.024905] Initializing cgroup subsys ns
[    0.024913] Initializing cgroup subsys cpuacct
[    0.024918] Initializing cgroup subsys memory
[    0.024932] Initializing cgroup subsys devices
[    0.024935] Initializing cgroup subsys freezer
[    0.024938] Initializing cgroup subsys net_cls
[    0.024980] CPU: Physical Processor ID: 0
[    0.024982] CPU: Processor Core ID: 0
[    0.024985] mce: CPU supports 6 MCE banks
[    0.024995] CPU0: Thermal monitoring enabled (TM2)
[    0.025000] using mwait in idle threads.
[    0.025003] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.025010] PEBS disabled due to CPU errata.
[    0.025015] ... version:                2
[    0.025017] ... bit width:              40
[    0.025018] ... generic registers:      2
[    0.025021] ... value mask:             000000ffffffffff
[    0.025023] ... max period:             000000007fffffff
[    0.025025] ... fixed-purpose events:   3
[    0.025027] ... event mask:             0000000700000003
[    0.028112] ACPI: Core revision 20100428
[    0.039662] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.039669] ftrace: allocating 22680 entries in 89 pages
[    0.050085] Setting APIC routing to flat
[    0.050490] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.152041] CPU0: Intel(R) Xeon(R) CPU           E5320  @ 1.86GHz stepping 07
[    0.160000] APIC calibration not consistent with PM-Timer: 96ms instead of 100ms
[    0.160000] APIC delta adjusted to PM-Timer: 1662499 (1605391)
[    0.160000] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    1.340010] Brought up 8 CPUs
[    1.340015] Total of 8 processors activated (29792.38 BogoMIPS).
[    1.345218] devtmpfs: initialized
[    1.345218] regulator: core version 0.5
[    1.345218] Time: 18:38:58  Date: 08/27/11
[    1.345218] NET: Registered protocol family 16
[    1.345218] ACPI: bus type pci registered
[    1.345218] Trying to unpack rootfs image as initramfs...
[    1.345218] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xe0000000-0xe1ffffff] (base 0xe0000000)
[    1.345218] PCI: MMCONFIG at [mem 0xe0000000-0xe1ffffff] reserved in E820
[    1.353998] PCI: Using configuration type 1 for base access
[    1.354878] bio: create slab <bio-0> at 0
[    1.354878] ACPI: EC: Look up EC in DSDT
[    1.360263] ACPI: SSDT 00000000bfeea84b 001DD (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.360518] ACPI: Dynamic OEM Table Load:
[    1.360522] ACPI: SSDT (null) 001DD (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)
[    1.361202] ACPI: SSDT 00000000bfeeaa28 0016E (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.361460] ACPI: Dynamic OEM Table Load:
[    1.361464] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)
[    1.362133] ACPI: SSDT 00000000bfeeab96 0016E (v01  PmRef  Cpu2Ist 00003000 INTL 20050228)
[    1.362387] ACPI: Dynamic OEM Table Load:
[    1.362391] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu2Ist 00003000 INTL 20050228)
[    1.363054] ACPI: SSDT 00000000bfeead04 0016E (v01  PmRef  Cpu3Ist 00003000 INTL 20050228)
[    1.363311] ACPI: Dynamic OEM Table Load:
[    1.363314] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu3Ist 00003000 INTL 20050228)
[    1.363985] ACPI: SSDT 00000000bfeeae72 0016E (v01  PmRef  CPU4Ist 00003000 INTL 20050228)
[    1.364243] ACPI: Dynamic OEM Table Load:
[    1.364247] ACPI: SSDT (null) 0016E (v01  PmRef  CPU4Ist 00003000 INTL 20050228)
[    1.364979] ACPI: SSDT 00000000bfeeafe0 0016E (v01  PmRef  CPU5Ist 00003000 INTL 20050228)
[    1.365240] ACPI: Dynamic OEM Table Load:
[    1.365243] ACPI: SSDT (null) 0016E (v01  PmRef  CPU5Ist 00003000 INTL 20050228)
[    1.365913] ACPI: SSDT 00000000bfeeb14e 0016E (v01  PmRef  Cpu6Ist 00003000 INTL 20050228)
[    1.366175] ACPI: Dynamic OEM Table Load:
[    1.366179] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu6Ist 00003000 INTL 20050228)
[    1.366851] ACPI: SSDT 00000000bfeeb2bc 0016E (v01  PmRef  Cpu7Ist 00003000 INTL 20050228)
[    1.367115] ACPI: Dynamic OEM Table Load:
[    1.367119] ACPI: SSDT (null) 0016E (v01  PmRef  Cpu7Ist 00003000 INTL 20050228)
[    1.367185] ACPI: Interpreter enabled
[    1.367188] ACPI: (supports S0 S1 S3 S4 S5)
[    1.367210] ACPI: Using IOAPIC for interrupt routing
[    1.372570] ACPI: No dock devices found.
[    1.372574] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    1.373671] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.375791] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    1.375795] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    1.375798] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    1.375802] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    1.375805] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    1.375808] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    1.375811] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    1.375814] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xfebfffff] (ignored)
[    1.375818] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    1.375881] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.375885] pci 0000:00:00.0: PME# disabled
[    1.375948] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.375952] pci 0000:00:01.0: PME# disabled
[    1.376014] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.376018] pci 0000:00:05.0: PME# disabled
[    1.376080] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.376084] pci 0000:00:09.0: PME# disabled
[    1.376450] pci 0000:00:1b.0: reg 10: [mem 0xd3504000-0xd3507fff 64bit]
[    1.376498] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.376502] pci 0000:00:1b.0: PME# disabled
[    1.376577] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.376581] pci 0000:00:1c.0: PME# disabled
[    1.376638] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    1.376694] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    1.376755] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    1.376812] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    1.376868] pci 0000:00:1d.7: reg 10: [mem 0xd3508000-0xd35083ff]
[    1.376923] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.376928] pci 0000:00:1d.7: PME# disabled
[    1.377055] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    1.377081] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    1.377088] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    1.377095] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    1.377102] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    1.377109] pci 0000:00:1f.1: reg 20: [io  0x1880-0x188f]
[    1.377151] pci 0000:00:1f.2: reg 10: [io  0x18c0-0x18c7]
[    1.377157] pci 0000:00:1f.2: reg 14: [io  0x18b8-0x18bb]
[    1.377164] pci 0000:00:1f.2: reg 18: [io  0x18b0-0x18b7]
[    1.377170] pci 0000:00:1f.2: reg 1c: [io  0x1894-0x1897]
[    1.377177] pci 0000:00:1f.2: reg 20: [io  0x18a0-0x18af]
[    1.377183] pci 0000:00:1f.2: reg 24: [mem 0xd3508400-0xd35087ff]
[    1.377206] pci 0000:00:1f.2: PME# supported from D3hot
[    1.377211] pci 0000:00:1f.2: PME# disabled
[    1.377262] pci 0000:00:1f.3: reg 20: [io  0x1100-0x111f]
[    1.377328] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.377333] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.377338] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.377344] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.377401] pci 0000:05:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    1.377412] pci 0000:05:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.377422] pci 0000:05:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit]
[    1.377429] pci 0000:05:00.0: reg 24: [io  0x2000-0x207f]
[    1.377435] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    1.390016] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    1.390021] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    1.390026] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    1.390033] pci 0000:00:05.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.390141] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    1.390145] pci 0000:09:00.0: PME# disabled
[    1.390210] pci 0000:09:00.3: PME# supported from D0 D3hot D3cold
[    1.390215] pci 0000:09:00.3: PME# disabled
[    1.390232] pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390243] pci 0000:00:09.0: PCI bridge to [bus 09-10]
[    1.390247] pci 0000:00:09.0:   bridge window [io  0x3000-0x3fff]
[    1.390251] pci 0000:00:09.0:   bridge window [mem 0xd3000000-0xd31fffff]
[    1.390257] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390353] pci 0000:0a:00.0: PME# supported from D0 D3hot D3cold
[    1.390358] pci 0000:0a:00.0: PME# disabled
[    1.390372] pci 0000:0a:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390436] pci 0000:0a:02.0: PME# supported from D0 D3hot D3cold
[    1.390440] pci 0000:0a:02.0: PME# disabled
[    1.390454] pci 0000:0a:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390488] pci 0000:09:00.0: PCI bridge to [bus 0a-0f]
[    1.390492] pci 0000:09:00.0:   bridge window [io  0x3000-0x3fff]
[    1.390497] pci 0000:09:00.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    1.390504] pci 0000:09:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390548] pci 0000:0a:00.0: PCI bridge to [bus 0b-0b]
[    1.390553] pci 0000:0a:00.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.390557] pci 0000:0a:00.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.390564] pci 0000:0a:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390636] pci 0000:0f:00.0: reg 10: [mem 0xd3000000-0xd301ffff]
[    1.390649] pci 0000:0f:00.0: reg 18: [io  0x3000-0x301f]
[    1.390702] pci 0000:0f:00.0: PME# supported from D0 D3hot D3cold
[    1.390707] pci 0000:0f:00.0: PME# disabled
[    1.390751] pci 0000:0f:00.1: reg 10: [mem 0xd3020000-0xd303ffff]
[    1.390764] pci 0000:0f:00.1: reg 18: [io  0x3020-0x303f]
[    1.390817] pci 0000:0f:00.1: PME# supported from D0 D3hot D3cold
[    1.390827] pci 0000:0f:00.1: PME# disabled
[    1.390851] pci 0000:0f:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    1.390863] pci 0000:0a:02.0: PCI bridge to [bus 0f-0f]
[    1.390868] pci 0000:0a:02.0:   bridge window [io  0x3000-0x3fff]
[    1.390872] pci 0000:0a:02.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    1.390879] pci 0000:0a:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.390965] pci 0000:09:00.3: PCI bridge to [bus 10-10]
[    1.390970] pci 0000:09:00.3:   bridge window [io  0xf000-0x0000] (disabled)
[    1.390974] pci 0000:09:00.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.390981] pci 0000:09:00.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.391037] pci 0000:00:1c.0: PCI bridge to [bus 1f-1f]
[    1.391041] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.391046] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.391053] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.391114] pci 0000:20:04.0: reg 10: [mem 0xd3200000-0xd320ffff]
[    1.391200] pci 0000:20:05.0: reg 10: [mem 0xd3214000-0xd32147ff]
[    1.391208] pci 0000:20:05.0: reg 14: [mem 0xd3210000-0xd3213fff]
[    1.391277] pci 0000:20:05.0: supports D1 D2
[    1.391279] pci 0000:20:05.0: PME# supported from D0 D1 D2 D3hot
[    1.391284] pci 0000:20:05.0: PME# disabled
[    1.391330] pci 0000:00:1e.0: PCI bridge to [bus 20-20] (subtractive decode)
[    1.391335] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.391340] pci 0000:00:1e.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    1.391346] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.391350] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    1.391353] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[    1.391377] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.391688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.391759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    1.391828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    1.391899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0._PRT]
[    1.392039] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0.BPD0._PRT]
[    1.392122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMD0.BPD2._PRT]
[    1.392194] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMF3._PRT]
[    1.392297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.392396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.403702] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 14 15) *9
[    1.403805] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 14 15)
[    1.403905] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[    1.404003] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[    1.404101] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    1.404201] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 6 7 10 *11 14 15)
[    1.404299] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 *15)
[    1.404396] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 6 7 *10 11 14 15)
[    1.404446] HEST: Table is not found!
[    1.404542] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.404550] vgaarb: loaded
[    1.404715] SCSI subsystem initialized
[    1.404733] libata version 3.00 loaded.
[    1.404733] usbcore: registered new interface driver usbfs
[    1.404733] usbcore: registered new interface driver hub
[    1.404733] usbcore: registered new device driver usb
[    1.404733] ACPI: WMI: Mapper loaded
[    1.404733] PCI: Using ACPI for IRQ routing
[    1.404733] PCI: pci_cache_line_size set to 64 bytes
[    1.404733] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.404733] reserve RAM buffer: 00000000bfee0000 - 00000000bfffffff 
[    1.404733] NetLabel: Initializing
[    1.404733] NetLabel:  domain hash size = 128
[    1.404733] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.404733] NetLabel:  unlabeled traffic allowed by default
[    1.404733] hpet clockevent registered
[    1.404733] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    1.404733] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.404733] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    3.530090] Switching to clocksource tsc
[    3.545164] AppArmor: AppArmor Filesystem Enabled
[    3.545195] pnp: PnP ACPI init
[    3.545225] ACPI: bus type pnp registered
[    3.549253] pnp: PnP ACPI: found 11 devices
[    3.549255] ACPI: ACPI bus type pnp unregistered
[    3.549274] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    3.549278] system 00:01: [io  0x0800-0x080f] has been reserved
[    3.549281] system 00:01: [io  0x1000-0x107f] has been reserved
[    3.549284] system 00:01: [io  0x1180-0x11bf] has been reserved
[    3.549287] system 00:01: [io  0xfe00] has been reserved
[    3.549291] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    3.549295] system 00:01: [mem 0xfee00000-0xfee0ffff] could not be reserved
[    3.549298] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    3.549301] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    3.549305] system 00:01: [mem 0xfec88000-0xfec88fff] could not be reserved
[    3.549308] system 00:01: [mem 0xfe000000-0xfe01ffff] has been reserved
[    3.549311] system 00:01: [mem 0xfe600000-0xfe6fffff] has been reserved
[    3.555783] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd3300000-0xd34fffff]
[    3.555788] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.555792] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
[    3.555795] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    3.555798] pci 0000:00:01.0:   bridge window [io  disabled]
[    3.555802] pci 0000:00:01.0:   bridge window [mem disabled]
[    3.555806] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    3.555813] pci 0000:05:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    3.555816] pci 0000:00:05.0: PCI bridge to [bus 05-05]
[    3.555819] pci 0000:00:05.0:   bridge window [io  0x2000-0x2fff]
[    3.555824] pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd2ffffff]
[    3.555828] pci 0000:00:05.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.555835] pci 0000:0a:00.0: PCI bridge to [bus 0b-0b]
[    3.555837] pci 0000:0a:00.0:   bridge window [io  disabled]
[    3.555842] pci 0000:0a:00.0:   bridge window [mem disabled]
[    3.555846] pci 0000:0a:00.0:   bridge window [mem pref disabled]
[    3.555853] pci 0000:0a:02.0: PCI bridge to [bus 0f-0f]
[    3.555857] pci 0000:0a:02.0:   bridge window [io  0x3000-0x3fff]
[    3.555862] pci 0000:0a:02.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    3.555867] pci 0000:0a:02.0:   bridge window [mem pref disabled]
[    3.555873] pci 0000:09:00.0: PCI bridge to [bus 0a-0f]
[    3.555877] pci 0000:09:00.0:   bridge window [io  0x3000-0x3fff]
[    3.555883] pci 0000:09:00.0:   bridge window [mem 0xd3000000-0xd30fffff]
[    3.555887] pci 0000:09:00.0:   bridge window [mem pref disabled]
[    3.555894] pci 0000:09:00.3: PCI bridge to [bus 10-10]
[    3.555896] pci 0000:09:00.3:   bridge window [io  disabled]
[    3.555901] pci 0000:09:00.3:   bridge window [mem disabled]
[    3.555905] pci 0000:09:00.3:   bridge window [mem pref disabled]
[    3.555912] pci 0000:00:09.0: PCI bridge to [bus 09-10]
[    3.555915] pci 0000:00:09.0:   bridge window [io  0x3000-0x3fff]
[    3.555920] pci 0000:00:09.0:   bridge window [mem 0xd3000000-0xd31fffff]
[    3.555923] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    3.555929] pci 0000:00:1c.0: PCI bridge to [bus 1f-1f]
[    3.555933] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    3.555938] pci 0000:00:1c.0:   bridge window [mem 0xd3300000-0xd34fffff]
[    3.555943] pci 0000:00:1c.0:   bridge window [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.555950] pci 0000:00:1e.0: PCI bridge to [bus 20-20]
[    3.555953] pci 0000:00:1e.0:   bridge window [io  disabled]
[    3.555958] pci 0000:00:1e.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    3.555963] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    3.555980]   alloc irq_desc for 16 on node -1
[    3.555983]   alloc kstat_irqs on node -1
[    3.555991] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.555997] pci 0000:00:01.0: setting latency timer to 64
[    3.556005] pci 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.556009] pci 0000:00:05.0: setting latency timer to 64
[    3.556017] pci 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.556021] pci 0000:00:09.0: setting latency timer to 64
[    3.556033] pci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.556038] pci 0000:09:00.0: setting latency timer to 64
[    3.556047] pci 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.556052] pci 0000:0a:00.0: setting latency timer to 64
[    3.556061]   alloc irq_desc for 18 on node -1
[    3.556063]   alloc kstat_irqs on node -1
[    3.556068] pci 0000:0a:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.556072] pci 0000:0a:02.0: setting latency timer to 64
[    3.556083] pci 0000:09:00.3: setting latency timer to 64
[    3.556092]   alloc irq_desc for 21 on node -1
[    3.556094]   alloc kstat_irqs on node -1
[    3.556098] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.556103] pci 0000:00:1c.0: setting latency timer to 64
[    3.556110] pci 0000:00:1e.0: setting latency timer to 64
[    3.556115] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    3.556118] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    3.556121] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    3.556123] pci_bus 0000:05: resource 1 [mem 0xd0000000-0xd2ffffff]
[    3.556126] pci_bus 0000:05: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    3.556129] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    3.556132] pci_bus 0000:09: resource 1 [mem 0xd3000000-0xd31fffff]
[    3.556134] pci_bus 0000:0a: resource 0 [io  0x3000-0x3fff]
[    3.556137] pci_bus 0000:0a: resource 1 [mem 0xd3000000-0xd30fffff]
[    3.556140] pci_bus 0000:0f: resource 0 [io  0x3000-0x3fff]
[    3.556142] pci_bus 0000:0f: resource 1 [mem 0xd3000000-0xd30fffff]
[    3.556145] pci_bus 0000:1f: resource 0 [io  0x4000-0x4fff]
[    3.556148] pci_bus 0000:1f: resource 1 [mem 0xd3300000-0xd34fffff]
[    3.556150] pci_bus 0000:1f: resource 2 [mem 0xd3600000-0xd37fffff 64bit pref]
[    3.556153] pci_bus 0000:20: resource 1 [mem 0xd3200000-0xd32fffff]
[    3.556156] pci_bus 0000:20: resource 4 [io  0x0000-0xffff]
[    3.556159] pci_bus 0000:20: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    3.556212] NET: Registered protocol family 2
[    3.556462] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.558331] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.563548] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.564191] TCP: Hash tables configured (established 524288 bind 65536)
[    3.564195] TCP reno registered
[    3.564210] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    3.564261] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    3.564477] NET: Registered protocol family 1
[    3.564643] pci 0000:00:1f.0: rerouting interrupts for [8086:2670]
[    3.564671] pci 0000:05:00.0: Boot video device
[    3.564681] PCI: CLS mismatch (32 != 64), using 64 bytes
[    3.564694] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.564698] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    3.564701] software IO TLB at phys 0x1fde000 - 0x5fde000
[    3.564765] Simple Boot Flag at 0x40 set to 0x1
[    3.565393] Scanning for low memory corruption every 60 seconds
[    3.565584] audit: initializing netlink socket (disabled)
[    3.565598] type=2000 audit(1314470339.560:1): initialized
[    3.582399] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.584468] VFS: Disk quotas dquot_6.5.2
[    3.584541] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.585256] fuse init (API version 7.14)
[    3.585371] msgmni has been set to 7896
[    3.588050] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.588055] io scheduler noop registered
[    3.588057] io scheduler deadline registered
[    3.588101] io scheduler cfq registered (default)
[    3.588266] pcieport 0000:00:01.0: setting latency timer to 64
[    3.588296]   alloc irq_desc for 64 on node -1
[    3.588299]   alloc kstat_irqs on node -1
[    3.588323] pcieport 0000:00:01.0: irq 64 for MSI/MSI-X
[    3.588395] pcieport 0000:00:05.0: setting latency timer to 64
[    3.588421]   alloc irq_desc for 65 on node -1
[    3.588423]   alloc kstat_irqs on node -1
[    3.588431] pcieport 0000:00:05.0: irq 65 for MSI/MSI-X
[    3.588497] pcieport 0000:00:09.0: setting latency timer to 64
[    3.588523]   alloc irq_desc for 66 on node -1
[    3.588525]   alloc kstat_irqs on node -1
[    3.588532] pcieport 0000:00:09.0: irq 66 for MSI/MSI-X
[    3.588601] pcieport 0000:00:1c.0: setting latency timer to 64
[    3.588635]   alloc irq_desc for 67 on node -1
[    3.588638]   alloc kstat_irqs on node -1
[    3.588646] pcieport 0000:00:1c.0: irq 67 for MSI/MSI-X
[    3.588737] pcieport 0000:09:00.0: setting latency timer to 64
[    3.588813] pcieport 0000:0a:00.0: setting latency timer to 64
[    3.588847]   alloc irq_desc for 68 on node -1
[    3.588849]   alloc kstat_irqs on node -1
[    3.588858] pcieport 0000:0a:00.0: irq 68 for MSI/MSI-X
[    3.588919] pcieport 0000:0a:02.0: setting latency timer to 64
[    3.588953]   alloc irq_desc for 69 on node -1
[    3.588955]   alloc kstat_irqs on node -1
[    3.588965] pcieport 0000:0a:02.0: irq 69 for MSI/MSI-X
[    3.589037] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    3.589044] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    3.589051] aer 0000:00:09.0:pcie02: AER service couldn't init device: no _OSC support
[    3.589075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.589126] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.589225] intel_idle: MWAIT substates: 0x20
[    3.589228] intel_idle: does not run on family 6 model 15
[    3.589367] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/PNP0C0C:00/input/input0
[    3.589374] ACPI: Power Button [PWRB]
[    3.589428] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.589432] ACPI: Power Button [PWRF]
[    3.589633] ACPI: acpi_idle registered with cpuidle
[    4.302837] ERST: Table is not found!
[    4.302982] Linux agpgart interface v0.103
[    4.303011] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.303122] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.303526] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.304945] brd: module loaded
[    4.305559] loop: module loaded
[    4.305766] ata_piix 0000:00:1f.1: version 2.13
[    4.305783]   alloc irq_desc for 20 on node -1
[    4.305785]   alloc kstat_irqs on node -1
[    4.305793] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.305845] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.306023] scsi0 : ata_piix
[    4.306153] scsi1 : ata_piix
[    4.306666] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    4.306670] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    4.306697]   alloc irq_desc for 23 on node -1
[    4.306699]   alloc kstat_irqs on node -1
[    4.306705] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    4.306711] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.306929] ata2: port disabled. ignoring.
[    4.324458] Freeing initrd memory: 11712k freed
[    4.470674] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.470791] scsi2 : ata_piix
[    4.470934] scsi3 : ata_piix
[    4.470974] ata3: SATA max UDMA/133 cmd 0x18c0 ctl 0x18b8 bmdma 0x18a0 irq 23
[    4.470982] ata4: SATA max UDMA/133 cmd 0x18b0 ctl 0x1894 bmdma 0x18a8 irq 23
[    4.471405] Fixed MDIO Bus: probed
[    4.471443] PPP generic driver version 2.4.2
[    4.471487] tun: Universal TUN/TAP device driver, 1.6
[    4.471489] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.471577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.471600] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.471628] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.471631] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.471669] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.471706] ehci_hcd 0000:00:1d.7: debug port 1
[    4.475599] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    4.475613] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd3508000
[    4.500677] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.500867] hub 1-0:1.0: USB hub found
[    4.500874] hub 1-0:1.0: 8 ports detected
[    4.500967] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.500987] uhci_hcd: USB Universal Host Controller Interface driver
[    4.501047] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.501053] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.501057] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.501092] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.501117] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[    4.501246] hub 2-0:1.0: USB hub found
[    4.501252] hub 2-0:1.0: 2 ports detected
[    4.501325] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.501331] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.501335] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.501384] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.501417] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[    4.501549] hub 3-0:1.0: USB hub found
[    4.501554] hub 3-0:1.0: 2 ports detected
[    4.501628]   alloc irq_desc for 22 on node -1
[    4.501631]   alloc kstat_irqs on node -1
[    4.501637] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.501643] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.501647] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.501697] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.501730] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
[    4.501855] hub 4-0:1.0: USB hub found
[    4.501860] hub 4-0:1.0: 2 ports detected
[    4.501942] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    4.501949] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.501952] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.501988] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.502012] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001860
[    4.502139] hub 5-0:1.0: USB hub found
[    4.502144] hub 5-0:1.0: 2 ports detected
[    4.502275] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.504743] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.504752] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.504838] mice: PS/2 mouse device common for all mice
[    4.505000] rtc_cmos 00:04: RTC can wake from S4
[    4.505041] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.505068] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.505170] device-mapper: uevent: version 1.0.3
[    4.505291] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    4.505743] device-mapper: multipath: version 1.1.1 loaded
[    4.505747] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.506658] cpuidle: using governor ladder
[    4.506661] cpuidle: using governor menu
[    4.507014] TCP cubic registered
[    4.507160] NET: Registered protocol family 10
[    4.507630] lo: Disabled Privacy Extensions
[    4.507851] NET: Registered protocol family 17
[    4.509932] PM: Resume from disk failed.
[    4.509949] registered taskstats version 1
[    4.510348]   Magic number: 7:532:646
[    4.510356] scsi_host host0: hash matches
[    4.510359] scsi host0: hash matches
[    4.510452] rtc_cmos 00:04: setting system clock to 2011-08-27 18:39:01 UTC (1314470341)
[    4.510456] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.510458] EDD information not available.
[    4.532901] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.630219] ata3.01: NODEV after polling detection
[    4.650256] ata3.00: ATAPI: LITE-ON DVDRW LH-16A1S, CL04, max UDMA/100
[    4.670194] ata4.00: ATA-8: OCZ-VERTEX2, 1.33, max UDMA/133
[    4.670198] ata4.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.670388] ata4.01: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
[    4.670395] ata4.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.690223] ata3.00: configured for UDMA/100
[    4.710203] ata4.00: configured for UDMA/133
[    4.711338] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-16A1S   CL04 PQ: 0 ANSI: 5
[    4.730311] ata4.01: configured for UDMA/133
[    4.735501] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.735506] Uniform CD-ROM driver Revision: 3.20
[    4.735698] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.735788] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    4.736023] scsi 3:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.33 PQ: 0 ANSI: 5
[    4.736224] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.736293] sd 3:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.736374] scsi 3:0:1:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
[    4.736416] sd 3:0:0:0: [sda] Write Protect is off
[    4.736420] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.736457] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.736518] sd 3:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.736544] sd 3:0:1:0: Attached scsi generic sg2 type 0
[    4.736619] sd 3:0:1:0: [sdb] Write Protect is off
[    4.736623] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.736745] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.736751]  sda: sda1
[    4.737386]  sdb:
[    4.755798] sd 3:0:0:0: [sda] Attached SCSI disk
[    4.756039] sd 3:0:1:0: [sdb] Attached SCSI disk
[    4.756064] Freeing unused kernel memory: 908k freed
[    4.756501] Write protecting the kernel read-only data: 10240k
[    4.756716] Freeing unused kernel memory: 416k freed
[    4.757139] Freeing unused kernel memory: 1644k freed
[    4.786932] udev[159]: starting version 163
[    4.817219] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    4.817223] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    4.817323] e1000e 0000:0f:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.817349] e1000e 0000:0f:00.0: setting latency timer to 64
[    4.817510]   alloc irq_desc for 70 on node -1
[    4.817513]   alloc kstat_irqs on node -1
[    4.817534] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[    4.839247] [drm] Initialized drm 1.1.0 20060810
[    4.858824] firewire_ohci 0000:20:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.876975] nouveau 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.876984] nouveau 0000:05:00.0: setting latency timer to 64
[    4.882236] [drm] nouveau 0000:05:00.0: Detected an NV50 generation card (0x094100a1)
[    4.883889] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    4.890729] [drm] nouveau 0000:05:00.0: Attempting to load BIOS image from PRAMIN
[    4.901441] e1000e 0000:0f:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:e0:81:79:19:2c
[    4.901445] e1000e 0000:0f:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.901527] e1000e 0000:0f:00.0: eth0: MAC: 5, PHY: 5, PBA No: ffffff-0ff
[    4.901572]   alloc irq_desc for 19 on node -1
[    4.901575]   alloc kstat_irqs on node -1
[    4.901587] e1000e 0000:0f:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.901603] e1000e 0000:0f:00.1: setting latency timer to 64
[    4.901730]   alloc irq_desc for 71 on node -1
[    4.901732]   alloc kstat_irqs on node -1
[    4.901746] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[    4.921976] firewire_ohci: Added fw-ohci device 0000:20:05.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    4.944975] [drm] nouveau 0000:05:00.0: ... appears to be valid
[    4.944980] [drm] nouveau 0000:05:00.0: BIT BIOS found
[    4.944983] [drm] nouveau 0000:05:00.0: Bios version 62.94.11.00
[    4.944988] [drm] nouveau 0000:05:00.0: TMDS table revision 2.0 not currently supported
[    4.944992] [drm] nouveau 0000:05:00.0: Found Display Configuration Block version 4.0
[    4.944995] [drm] nouveau 0000:05:00.0: Raw DCB entry 0: 02000300 00000028
[    4.944998] [drm] nouveau 0000:05:00.0: Raw DCB entry 1: 01000302 00020030
[    4.945001] [drm] nouveau 0000:05:00.0: Raw DCB entry 2: 04011310 00000028
[    4.945004] [drm] nouveau 0000:05:00.0: Raw DCB entry 3: 02011312 00020030
[    4.945006] [drm] nouveau 0000:05:00.0: Raw DCB entry 4: 010223f1 00c0c080
[    4.945011] [drm] nouveau 0000:05:00.0: DCB connector table: VHER 0x40 5 16 4
[    4.945014] [drm] nouveau 0000:05:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    4.945018] [drm] nouveau 0000:05:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    4.945021] [drm] nouveau 0000:05:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    4.945024] [drm] nouveau 0000:05:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    4.945027] [drm] nouveau 0000:05:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    4.945036] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 0 at offset 0xCD72
[    4.995418] e1000e 0000:0f:00.1: eth1: (PCI Express:2.5GB/s:Width x4) 00:e0:81:79:19:2d
[    4.995422] e1000e 0000:0f:00.1: eth1: Intel(R) PRO/1000 Network Connection
[    4.995503] e1000e 0000:0f:00.1: eth1: MAC: 5, PHY: 5, PBA No: ffffff-0ff
[    5.043397] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 1 at offset 0xD15B
[    5.044937] Initializing USB Mass Storage driver...
[    5.045102] scsi4 : usb-storage 1-8:1.0
[    5.045256] usbcore: registered new interface driver usb-storage
[    5.045259] USB Mass Storage support registered.
[    5.083176] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 2 at offset 0xE0B6
[    5.083186] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 3 at offset 0xE1E5
[    5.103245] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table 4 at offset 0xE3F5
[    5.103248] [drm] nouveau 0000:05:00.0: Parsing VBIOS init table at offset 0xE45A
[    5.133175] [drm] nouveau 0000:05:00.0: 0xE45A: Condition still not met after 20ms, skipping following opcodes
[    5.133184] [drm] nouveau 0000:05:00.0: 0xBD6A: parsing output script 0
[    5.133188] [drm] nouveau 0000:05:00.0: 0xBD6A: parsing output script 0
[    5.133191] [drm] nouveau 0000:05:00.0: 0xA7A6: parsing output script 0
[    5.133199] [drm] nouveau 0000:05:00.0: Detected 512MiB VRAM
[    5.217100] [TTM] Zone  kernel: Available graphics memory: 2028880 kiB.
[    5.217103] [TTM] Initializing pool allocator.
[    5.261200] [drm] nouveau 0000:05:00.0: 512 MiB GART (aperture)
[    5.261211] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[    5.261642] [drm] nouveau 0000:05:00.0: Allocating FIFO number 1
[    5.272015] [drm] nouveau 0000:05:00.0: nouveau_channel_alloc: initialised FIFO 1
[    5.273325] [drm] nouveau 0000:05:00.0: Detected a DAC output
[    5.273329] [drm] nouveau 0000:05:00.0: Detected a TMDS output
[    5.273332] [drm] nouveau 0000:05:00.0: Detected a DAC output
[    5.273335] [drm] nouveau 0000:05:00.0: Detected a TMDS output
[    5.273338] [drm] nouveau 0000:05:00.0: DCB encoder 1 unknown
[    5.273340] [drm] nouveau 0000:05:00.0: Detected a DVI-I connector
[    5.273403] [drm] nouveau 0000:05:00.0: Detected a DVI-I connector
[    5.273433] [drm] nouveau 0000:05:00.0: Detected a TV connector
[    5.273437] [drm] nouveau 0000:05:00.0:   no encoders, ignoring
[    5.310176] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.420125] firewire_core: created device fw0: GUID 00e08100002804f8, S400
[    5.464862] [drm] nouveau 0000:05:00.0: allocated 1920x1200 fb: 0x40250000, bo ffff88013b0f6c00
[    5.466160] [drm] nouveau 0000:05:00.0: 0xBD6E: parsing output script 1
[    5.466172] [drm] nouveau 0000:05:00.0: 0xBD6F: parsing output script 2
[    5.466198] [drm] nouveau 0000:05:00.0: 0xBA7F: parsing clock script 0
[    5.466500] [drm] nouveau 0000:05:00.0: 0xB32D: parsing clock script 1
[    5.467876] Console: switching to colour frame buffer device 240x75
[    5.470190] fb0: nouveaufb frame buffer device
[    5.470192] drm: registered panic notifier
[    5.470197] Slow work thread pool: Starting up
[    5.470307] Slow work thread pool: Ready
[    5.470314] [drm] Initialized nouveau 0.0.16 20090420 for 0000:05:00.0 on minor 0
[    5.501387] usbcore: registered new interface driver hiddev
[    5.514127] input: Dynex 5-Button Wired Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
[    5.514233] generic-usb 0003:0461:4D42.0001: input,hidraw0: USB HID v1.11 Mouse [Dynex 5-Button Wired Optical Mouse] on usb-0000:00:1d.2-2/input0
[    5.514262] usbcore: registered new interface driver usbhid
[    5.514264] usbhid: USB HID core driver
[    5.791016] Btrfs loaded
[    5.797616] xor: automatically using best checksumming function: generic_sse
[    5.841278]    generic_sse:  6636.000 MB/sec
[    5.841281] xor: using function: generic_sse (6636.000 MB/sec)
[    5.844057] device-mapper: dm-raid45: initialized v0.2594b
[    6.053960] scsi 4:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[    6.054804] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    6.055629] sd 4:0:0:0: [sdc] 2013184 512-byte logical blocks: (1.03 GB/983 MiB)
[    6.056756] sd 4:0:0:0: [sdc] Write Protect is off
[    6.056761] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    6.056764] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.078387] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.078395]  sdc: sdc1
[    6.084387] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    6.084392] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   37.920045] ata4: lost interrupt (Status 0x50)
[   37.920065] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   37.920070] ata4.00: failed command: FLUSH CACHE
[   37.920078] ata4.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   37.920079]          res 40/00:01:00:00:00/00:00:00:00:00/e0 Emask 0x4 (timeout)
[   37.920083] ata4.00: status: { DRDY }
[   37.920096] ata4: soft resetting link
[   38.160168] ata4.00: configured for UDMA/133
[   38.180312] ata4.01: configured for UDMA/133
[   38.180320] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[   53.180625] ata4.00: qc timeout (cmd 0xe7)
[   53.180628] ata4.00: FLUSH failed Emask 0x4
[   53.180642] ata4: soft resetting link
[   53.420176] ata4.00: configured for UDMA/133
[   53.444443] ata4.01: configured for UDMA/133
[   53.444452] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[   68.440656] ata4.00: qc timeout (cmd 0xe7)
[   68.440661] ata4.00: FLUSH failed Emask 0x4
[   68.440666] ata4.00: limiting speed to UDMA/133:PIO3
[   68.440679] ata4: soft resetting link
[   68.680181] ata4.00: configured for UDMA/133
[   68.700565] ata4.01: configured for UDMA/133
[   68.700570] ata4.00: retrying FLUSH 0xe7 Emask 0x4
[   98.700550] ata4.00: qc timeout (cmd 0xe7)
[   98.700553] ata4.00: FLUSH failed Emask 0x4
[   98.700556] ata4.00: disabled
[   98.700564] ata4.00: device reported invalid CHS sector 0
[   98.700578] ata4: soft resetting link
[   98.900553] ata4.01: configured for UDMA/133
[   98.900570] ata4: EH complete
[   98.900603] end_request: I/O error, dev sda, sector 0
[   98.900699] sd 3:0:0:0: [sda] READ CAPACITY(16) failed
[   98.900703] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   98.900708] sd 3:0:0:0: [sda] Sense not available.
[   98.900737] end_request: I/O error, dev sda, sector 0
[   98.900766] sd 3:0:0:0: [sda] READ CAPACITY failed
[   98.900768] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   98.900772] sd 3:0:0:0: [sda] Sense not available.
[   98.900823] sd 3:0:0:0: [sda] Asking for cache data failed
[   98.900825] sd 3:0:0:0: [sda] Assuming drive cache: write through
[   98.900833] sda: detected capacity change from 60022480896 to 0
[  100.575506] sd 3:0:0:0: [sda] READ CAPACITY(16) failed
[  100.575511] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  100.575516] sd 3:0:0:0: [sda] Sense not available.
[  100.575550] sd 3:0:0:0: [sda] READ CAPACITY failed
[  100.575553] sd 3:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  100.575556] sd 3:0:0:0: [sda] Sense not available.
[  100.575605] sd 3:0:0:0: [sda] Asking for cache data failed
[  100.575607] sd 3:0:0:0: [sda] Assuming drive cache: write through
[  100.803213] aufs 2-standalone.tree-35-rcN-20100705
[  100.821909] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[  102.205091] EXT3-fs: barriers not enabled
[  102.451922] kjournald starting.  Commit interval 5 seconds
[  102.451981] EXT3-fs (loop1): using internal journal
[  102.452001] ext3_orphan_cleanup: deleting unreferenced inode 4127
[  102.452082] ext3_orphan_cleanup: deleting unreferenced inode 4115
[  102.452106] ext3_orphan_cleanup: deleting unreferenced inode 4119
[  102.457088] ext3_orphan_cleanup: deleting unreferenced inode 4118
[  102.457102] ext3_orphan_cleanup: deleting unreferenced inode 16
[  102.457760] ext3_orphan_cleanup: deleting unreferenced inode 15
[  102.457802] ext3_orphan_cleanup: deleting unreferenced inode 14
[  102.457812] EXT3-fs (loop1): 7 orphan inodes deleted
[  102.457815] EXT3-fs (loop1): recovery complete
[  102.458002] EXT3-fs (loop1): mounted filesystem with ordered data mode
[  102.464580] aufs test_add:252:exe[793]: uid/gid/perm //filesystem.squashfs 0/0/0755, 1000/1000/0755
[  130.428335] udev[2372]: starting version 163
[  130.895872] intel_rng: FWH not detected
[  130.899485] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  131.017608] EDAC MC: Ver: 2.1.0 Sep 19 2010
[  131.024124] parport_pc 00:09: reported by Plug and Play ACPI
[  131.024248] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  131.043090] cfg80211: Calling CRDA to update world regulatory domain
[  131.072214] EDAC MC0: Giving out device to 'i5400_edac.c' 'I5400': DEV 0000:00:10.0
[  131.072454] EDAC PCI0: Giving out device to module 'i5400_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[  131.102345] tpm_tis 00:0a: 1.2 TPM (device-id 0xB, rev-id 16)
[  131.128117] ppdev: user-space parallel port driver
[  131.160448] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[  131.220162] e1000e 0000:0f:00.0: irq 70 for MSI/MSI-X
[  131.220925] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  131.273318] cfg80211: World regulatory domain updated:
[  131.273323]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.273327]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  131.273331]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  131.273334]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  131.273337]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  131.273340]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  131.291691] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[  131.308399] ath5k 0000:20:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  131.308542] ath5k 0000:20:04.0: registered as 'phy0'
[  131.351440] e1000e 0000:0f:00.1: irq 71 for MSI/MSI-X
[  131.352325] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  131.440190]   alloc irq_desc for 17 on node -1
[  131.440196]   alloc kstat_irqs on node -1
[  131.440218] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  131.440299]   alloc irq_desc for 72 on node -1
[  131.440301]   alloc kstat_irqs on node -1
[  131.440314] HDA Intel 0000:00:1b.0: irq 72 for MSI/MSI-X
[  131.440359] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  131.568128] hda_codec: ALC888: BIOS auto-probing.
[  131.908052] ath: EEPROM regdomain: 0x10
[  131.908056] ath: EEPROM indicates we should expect a direct regpair map
[  131.908060] ath: Country alpha2 being used: CO
[  131.908062] ath: Regpair used: 0x10
[  131.964379] phy0: Selected rate control algorithm 'minstrel'
[  131.965131] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  131.965446] cfg80211: Calling CRDA for country: CO
[  131.972009] cfg80211: Regulatory domain changed to country: CO
[  131.972014]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.972018]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  131.972021]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[  131.972024]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[  131.972027]     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[  132.004735] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  132.277337] lp0: using parport0 (interrupt-driven).
[  132.829905] [drm] nouveau 0000:05:00.0: Allocating FIFO number 2
[  132.843498] [drm] nouveau 0000:05:00.0: nouveau_channel_alloc: initialised FIFO 2
[  134.163765] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[  134.164768] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  144.551297] eth1: no IPv6 routers present

```

boot info script:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714 ...........>...r>.......(+.4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1427200 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1030 MB, 1030750208 bytes
32 heads, 62 sectors/track, 1014 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     2,011,775     2,011,714   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       39c56a6e-99d5-45ed-a94d-765baf251afa   ext3       
/dev/sdc1        BF52-4BB0                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sda" to 137438913024
ERROR: pdc: seeking device "/dev/sda" to 137438920192
ERROR: pdc: seeking device "/dev/sda" to 137438927360
ERROR: pdc: seeking device "/dev/sda" to 137438934528
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by srs5694 on 2011-08-27
The dmesg output in your post #18, which is associated with Boot Info Script being able to find your disk, still produces "lost interrupt" and other hardware errors:

```

[   56.991396] ata4: lost interrupt (Status 0x58)
[   56.991785] ata4: drained 512 bytes to clear DRQ.
[   56.991795] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   56.991801] ata4.00: failed command: IDENTIFY DEVICE
[   56.991808] ata4.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   56.991810]          res 40/00:00:00:00:00/00:00:00:00:00/10 Emask 0x4 (timeout)
[   56.991813] ata4.00: status: { DRDY }
[   56.991825] ata4: soft resetting link

```

I don't know enough about what this means to give you a precise diagnosis, but my estimate is that you're looking at a 90%+ probability of a hardware problem. Have you tried any of the hardware diagnostics and fixes I mentioned in post #8 in this thread? If not, I'd like to reiterate that advice.

Sometimes hardware faults can interact with software. For instance, in the mid-1990s, a common hardware fault was RAM that would work fine under DOS or Windows (both 16-bit OSes at the time), but that would fail under OS/2, Linux, or other 32-bit OSes. The cause was different access patterns under the 16- vs. 32-bit OSes, which revealed memory flaws in one case but not another. You could be seeing something analogous here, in which a combination of particular data on the disk and access patterns to the disk is creating errors that cause the disk to "drop out". If I'm right, you'll need to replace or reconfigure your hardware. If you're lucky, replacing a cable might fix the problem; but it could be you'll need to replace the SSD drive.

---

### Post by foilboy on 2011-09-04
Alright I brought my drive to a friend's house and plugged the drive in with new cables.  The dmesg output looks clean, but the SATA port on this motherboard is SATA1 (1.5Gbps).  I would say the drive is fine, unless there's something wrong with the way the it tries to use SATA2?  [S]I'm going to install Windows to it and see if it's still visible in Ubuntu[/S].  Just kidding he doesn't have a DVD drive.  Ugh.


Here's the dmesg output (my SSD is sdc/ata3 here):
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e8000000 old size 32 MB
[    0.000000] Aperture from AGP @ e8000000 size 64 MB (APSIZE f30)
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-CFFFF uncachable
[    0.000000]   D0000-D7FFF write-back
[    0.000000]   D8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 00E8000000 mask FFFC000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d400 (usable)
[    0.000000]  modified: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f58b0] f58b0
[    0.000000] init_memory_mapping: 0000000000000000-000000003fff0000
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 3fff0000 @ 16000-19000
[    0.000000] RAMDISK: 3f4b1000 - 3fff0000
[    0.000000] ACPI: RSDP 00000000000f7360 00014 (v00 VIAK8T)
[    0.000000] ACPI: RSDT 000000003fff3000 00030 (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 000000003fff3040 00074 (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 000000003fff30c0 04C79 (v01 VIAK8T AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 000000003fff0000 00040
[    0.000000] ACPI: BOOT 000000003fff7d40 00028 (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 000000003fff7d80 0005A (v01 VIAK8T AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fff0000
[    0.000000] Initmem setup node 0 0000000000000000-000000003fff0000
[    0.000000]   NODE_DATA [0000000001d180c0 - 0000000001d1d0bf]
[    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880002600000-ffff8800033fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262013
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3925 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3528 pages used for memmap
[    0.000000]   DMA32 zone: 254504 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [17000 - 177ff]
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u2097152
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 258429
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e8000000 old size 32 MB
[    0.000000] Aperture from AGP @ e8000000 size 64 MB (APSIZE f30)
[    0.000000] Node 0: aperture @ e8000000 size 64 MB
[    0.000000] Subtract (44 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [003f4b1000 - 003fff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d180be]             BRK
[    0.000000]   #4 [00000f58c0 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f58b0 - 00000f58c0]    MP-table mpf
[    0.000000]   #6 [000009d400 - 00000f0c00]   BIOS reserved
[    0.000000]   #7 [00000f0d50 - 00000f58b0]   BIOS reserved
[    0.000000]   #8 [00000f0c00 - 00000f0d50]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000017000]         PGTABLE
[    0.000000]   #12 [0001d180c0 - 0001d1d0c0]       NODE_DATA
[    0.000000]   #13 [0001d1d0c0 - 0001d1e0c0]         BOOTMEM
[    0.000000]   #14 [0001d17140 - 0001d17200]         BOOTMEM
[    0.000000]   #15 [000251f000 - 0002520000]         BOOTMEM
[    0.000000]   #16 [0002520000 - 0002521000]         BOOTMEM
[    0.000000]   #17 [0002600000 - 0003400000]        MEMMAP 0
[    0.000000]   #18 [0001d17200 - 0001d17380]         BOOTMEM
[    0.000000]   #19 [0001d1e0c0 - 0001d240c0]         BOOTMEM
[    0.000000]   #20 [0001d25000 - 0001d26000]         BOOTMEM
[    0.000000]   #21 [0001d17380 - 0001d173c3]         BOOTMEM
[    0.000000]   #22 [0001d17400 - 0001d17630]         BOOTMEM
[    0.000000]   #23 [0001d17640 - 0001d176a8]         BOOTMEM
[    0.000000]   #24 [0001d176c0 - 0001d17728]         BOOTMEM
[    0.000000]   #25 [0001d17740 - 0001d177a8]         BOOTMEM
[    0.000000]   #26 [0001d177c0 - 0001d17828]         BOOTMEM
[    0.000000]   #27 [0001d17840 - 0001d178a8]         BOOTMEM
[    0.000000]   #28 [0001d178c0 - 0001d17928]         BOOTMEM
[    0.000000]   #29 [0001d17940 - 0001d179a8]         BOOTMEM
[    0.000000]   #30 [0001d179c0 - 0001d17a28]         BOOTMEM
[    0.000000]   #31 [0001d17a40 - 0001d17aa8]         BOOTMEM
[    0.000000]   #32 [0001d17ac0 - 0001d17ae0]         BOOTMEM
[    0.000000]   #33 [0001d17b00 - 0001d17b55]         BOOTMEM
[    0.000000]   #34 [0001d17b80 - 0001d17bd5]         BOOTMEM
[    0.000000]   #35 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #36 [0001d17c00 - 0001d17c08]         BOOTMEM
[    0.000000]   #37 [0001d17c40 - 0001d17c48]         BOOTMEM
[    0.000000]   #38 [0001d17c80 - 0001d17c84]         BOOTMEM
[    0.000000]   #39 [0001d17cc0 - 0001d17cc8]         BOOTMEM
[    0.000000]   #40 [0001d17d00 - 0001d17e50]         BOOTMEM
[    0.000000]   #41 [0001d17e80 - 0001d17f00]         BOOTMEM
[    0.000000]   #42 [0001d17f00 - 0001d17f80]         BOOTMEM
[    0.000000]   #43 [0001d26000 - 0001d2e000]         BOOTMEM
[    0.000000] Memory: 1008548k/1048512k available (5708k kernel code, 460k absent, 39504k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 10485760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2247.444 MHz processor.
[    0.010013] Calibrating delay loop (skipped), value calculated using timer frequency.. 4494.88 BogoMIPS (lpj=22474440)
[    0.010018] pid_max: default: 32768 minimum: 301
[    0.010054] Security Framework initialized
[    0.010083] AppArmor: AppArmor initialized
[    0.010084] Yama: becoming mindful.
[    0.010277] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.011495] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.012096] Mount-cache hash table entries: 256
[    0.012311] Initializing cgroup subsys ns
[    0.012317] Initializing cgroup subsys cpuacct
[    0.012321] Initializing cgroup subsys memory
[    0.012337] Initializing cgroup subsys devices
[    0.012340] Initializing cgroup subsys freezer
[    0.012343] Initializing cgroup subsys net_cls
[    0.012382] tseg: 0000000000
[    0.012405] mce: CPU supports 5 MCE banks
[    0.012424] Performance Events: AMD PMU driver.
[    0.012433] ... version:                0
[    0.012435] ... bit width:              48
[    0.012436] ... generic registers:      4
[    0.012438] ... value mask:             0000ffffffffffff
[    0.012440] ... max period:             00007fffffffffff
[    0.012442] ... fixed-purpose events:   0
[    0.012444] ... event mask:             000000000000000f
[    0.012490] SMP alternatives: switching to UP code
[    0.026859] Freeing SMP alternatives: 24k freed
[    0.026884] ACPI: Core revision 20100428
[    0.039584] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.039600] ftrace: allocating 22680 entries in 89 pages
[    0.040152] Setting APIC routing to flat
[    0.040964] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.147359] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[    0.150000] Brought up 1 CPUs
[    0.150000] Total of 1 processors activated (4494.88 BogoMIPS).
[    0.150000] devtmpfs: initialized
[    0.150000] regulator: core version 0.5
[    0.150000] Time: 15:41:50  Date: 09/04/11
[    0.150000] NET: Registered protocol family 16
[    0.150000] node 0 link 0: io port [1000, fffff]
[    0.150000] TOM: 0000000040000000 aka 1024M
[    0.150000] node 0 link 0: mmio [a0000, bffff]
[    0.150000] node 0 link 0: mmio [40000000, ff70ffff]
[    0.150000] bus: [00, ff] on node 0 link 0
[    0.150000] bus: 00 index 0 [io  0x0000-0xffff]
[    0.150000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.150000] bus: 00 index 2 [mem 0x40000000-0xfcffffffff]
[    0.150000] ACPI: bus type pci registered
[    0.150000] PCI: Using configuration type 1 for base access
[    0.150000] bio: create slab <bio-0> at 0
[    0.150000] ACPI: EC: Look up EC in DSDT
[    0.150000] ACPI: Interpreter enabled
[    0.150000] ACPI: (supports S0 S1 S4 S5)
[    0.150000] ACPI: Using IOAPIC for interrupt routing
[    0.152898] ACPI: No dock devices found.
[    0.152902] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.153015] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.153224] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.153227] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.153230] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.153233] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.153235] pci_root PNP0A03:00: host bridge window [mem 0x40100000-0xfebfffff] (ignored)
[    0.153259] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xebffffff pref]
[    0.153496] pci 0000:00:01.0: supports D1
[    0.153530] pci 0000:00:0c.0: reg 10: [mem 0xee004000-0xee0047ff]
[    0.153536] pci 0000:00:0c.0: reg 14: [mem 0xee000000-0xee003fff]
[    0.153570] pci 0000:00:0c.0: supports D2
[    0.153572] pci 0000:00:0c.0: PME# supported from D2 D3hot
[    0.153576] pci 0000:00:0c.0: PME# disabled
[    0.153601] pci 0000:00:0e.0: reg 10: [io  0xb000-0xb0ff]
[    0.153606] pci 0000:00:0e.0: reg 14: [mem 0xee005000-0xee0050ff]
[    0.153636] pci 0000:00:0e.0: supports D1 D2
[    0.153638] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.153641] pci 0000:00:0e.0: PME# disabled
[    0.153665] pci 0000:00:0f.0: reg 10: [io  0xb400-0xb407]
[    0.153671] pci 0000:00:0f.0: reg 14: [io  0xb800-0xb803]
[    0.153676] pci 0000:00:0f.0: reg 18: [io  0xbc00-0xbc07]
[    0.153682] pci 0000:00:0f.0: reg 1c: [io  0xc000-0xc003]
[    0.153687] pci 0000:00:0f.0: reg 20: [io  0xc400-0xc40f]
[    0.153692] pci 0000:00:0f.0: reg 24: [io  0xc800-0xc8ff]
[    0.153750] pci 0000:00:0f.1: reg 20: [io  0xcc00-0xcc0f]
[    0.153814] pci 0000:00:10.0: reg 20: [io  0xd000-0xd01f]
[    0.153834] pci 0000:00:10.0: supports D1 D2
[    0.153836] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.153840] pci 0000:00:10.0: PME# disabled
[    0.153874] pci 0000:00:10.1: reg 20: [io  0xd400-0xd41f]
[    0.153894] pci 0000:00:10.1: supports D1 D2
[    0.153896] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.153900] pci 0000:00:10.1: PME# disabled
[    0.153934] pci 0000:00:10.2: reg 20: [io  0xd800-0xd81f]
[    0.153954] pci 0000:00:10.2: supports D1 D2
[    0.153956] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.153960] pci 0000:00:10.2: PME# disabled
[    0.153995] pci 0000:00:10.3: reg 20: [io  0xdc00-0xdc1f]
[    0.154015] pci 0000:00:10.3: supports D1 D2
[    0.154017] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.154020] pci 0000:00:10.3: PME# disabled
[    0.154042] pci 0000:00:10.4: reg 10: [mem 0xee006000-0xee0060ff]
[    0.154075] pci 0000:00:10.4: supports D1 D2
[    0.154077] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.154080] pci 0000:00:10.4: PME# disabled
[    0.154129] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.154172] pci 0000:00:11.5: reg 10: [io  0xe000-0xe0ff]
[    0.154208] pci 0000:00:11.5: supports D1 D2
[    0.154286] PCI: peer root bus 00 res updated from pci conf
[    0.154321] pci 0000:01:00.0: reg 10: [mem 0xec000000-0xecffffff]
[    0.154326] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff pref]
[    0.154338] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.154369] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.154373] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.154377] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff]
[    0.154381] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
[    0.154390] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.199256] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[    0.199423] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.199592] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[    0.199740] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.199905] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 *10 11 12)
[    0.200064] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.200217] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 *10 11 12)
[    0.200356] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.200568] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *11
[    0.200737] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.200905] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.201106] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[    0.201140] HEST: Table is not found!
[    0.201248] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.201250] vgaarb: loaded
[    0.201424] SCSI subsystem initialized
[    0.201531] libata version 3.00 loaded.
[    0.201593] usbcore: registered new interface driver usbfs
[    0.201604] usbcore: registered new interface driver hub
[    0.201633] usbcore: registered new device driver usb
[    0.201766] ACPI: WMI: Mapper loaded
[    0.201768] PCI: Using ACPI for IRQ routing
[    0.201772] PCI: pci_cache_line_size set to 64 bytes
[    0.201782] pci 0000:00:00.0: address space collision: [mem 0xe8000000-0xebffffff pref] conflicts with GART [mem 0xe8000000-0xebffffff]
[    0.201858] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    0.201861] reserve RAM buffer: 000000003fff0000 - 000000003fffffff 
[    0.201982] NetLabel: Initializing
[    0.201984] NetLabel:  domain hash size = 128
[    0.201986] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.202005] NetLabel:  unlabeled traffic allowed by default
[    0.202063] Switching to clocksource tsc
[    0.211296] AppArmor: AppArmor Filesystem Enabled
[    0.211330] pnp: PnP ACPI init
[    0.211361] ACPI: bus type pnp registered
[    0.211775] pnp 00:00: disabling [mem 0x000d0000-0x000d3fff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.211780] pnp 00:00: disabling [mem 0x000dc400-0x000dffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.211784] pnp 00:00: disabling [mem 0x000f0000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.211787] pnp 00:00: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.211791] pnp 00:00: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.211795] pnp 00:00: disabling [mem 0x00100000-0x3ffeffff] because it overlaps 0000:00:00.0 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.214896] pnp: PnP ACPI: found 12 devices
[    0.214898] ACPI: ACPI bus type pnp unregistered
[    0.214914] system 00:00: [mem 0x40000000-0x400fffff] has been reserved
[    0.214917] system 00:00: [mem 0x3fff0000-0x3fffffff] could not be reserved
[    0.214919] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
[    0.214922] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.214925] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.214928] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.214935] system 00:02: [io  0x4000-0x407f] has been reserved
[    0.214943] system 00:02: [io  0x5000-0x500f] has been reserved
[    0.214948] system 00:03: [io  0x0b78-0x0b7b] has been reserved
[    0.214951] system 00:03: [io  0x0f78-0x0f7b] has been reserved
[    0.214953] system 00:03: [io  0x0a78-0x0a7b] has been reserved
[    0.214956] system 00:03: [io  0x0e78-0x0e7b] has been reserved
[    0.214958] system 00:03: [io  0x0bbc-0x0bbf] has been reserved
[    0.214961] system 00:03: [io  0x0fbc-0x0fbf] has been reserved
[    0.214969] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.214971] system 00:03: [io  0x0290-0x0297] has been reserved
[    0.220998] pci 0000:01:00.0: BAR 6: assigned [mem 0xed000000-0xed01ffff pref]
[    0.221003] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.221005] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.221011] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff]
[    0.221014] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
[    0.221030] pci 0000:00:01.0: setting latency timer to 64
[    0.221034] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.221037] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.221039] pci_bus 0000:00: resource 6 [mem 0x40000000-0xfcffffffff]
[    0.221042] pci_bus 0000:01: resource 1 [mem 0xec000000-0xedffffff]
[    0.221045] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xe7ffffff pref]
[    0.221097] NET: Registered protocol family 2
[    0.221199] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.221874] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.224340] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.225524] TCP: Hash tables configured (established 131072 bind 65536)
[    0.225528] TCP reno registered
[    0.225542] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.225571] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.225704] NET: Registered protocol family 1
[    0.225740] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.225856] pci 0000:01:00.0: Boot video device
[    0.225859] PCI: CLS 32 bytes, default 64
[    0.226110] Trying to unpack rootfs image as initramfs...
[    2.133474] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0282]
[    2.135889] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[    2.135982] Simple Boot Flag at 0x37 set to 0x80
[    2.136097] Scanning for low memory corruption every 60 seconds
[    2.136233] audit: initializing netlink socket (disabled)
[    2.136248] type=2000 audit(1315150912.130:1): initialized
[    2.149769] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.151216] VFS: Disk quotas dquot_6.5.2
[    2.151270] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.151894] fuse init (API version 7.14)
[    2.151988] msgmni has been set to 1969
[    2.152320] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.152324] io scheduler noop registered
[    2.152326] io scheduler deadline registered
[    2.152362] io scheduler cfq registered (default)
[    2.152543] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.152566] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.152758] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.152767] ACPI: Power Button [PWRB]
[    2.152827] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.152830] ACPI: Power Button [PWRF]
[    2.153090] ACPI: acpi_idle registered with cpuidle
[    2.155575] ERST: Table is not found!
[    2.155738] Linux agpgart interface v0.103
[    2.155744] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.155854] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.156157] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.157295] brd: module loaded
[    2.157824] loop: module loaded
[    2.158537] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 11, using IRQ 20
[    2.158539] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    2.158547]   alloc irq_desc for 20 on node 0
[    2.158549]   alloc kstat_irqs on node 0
[    2.158563] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    2.158652] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    2.159006] Fixed MDIO Bus: probed
[    2.159038] PPP generic driver version 2.4.2
[    2.159110] tun: Universal TUN/TAP device driver, 1.6
[    2.159112] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.159192] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.159233]   alloc irq_desc for 21 on node 0
[    2.159235]   alloc kstat_irqs on node 0
[    2.159240] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.159268] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.159304] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.159378] ehci_hcd 0000:00:10.4: irq 21, io mem 0xee006000
[    2.170051] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.170260] hub 1-0:1.0: USB hub found
[    2.170267] hub 1-0:1.0: 8 ports detected
[    2.170391] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.170408] uhci_hcd: USB Universal Host Controller Interface driver
[    2.180133] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.180150] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.180261] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.180293] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d000
[    2.180465] hub 2-0:1.0: USB hub found
[    2.180472] hub 2-0:1.0: 2 ports detected
[    2.180623] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.180630] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.180661] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.180681] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d400
[    2.180798] hub 3-0:1.0: USB hub found
[    2.180801] hub 3-0:1.0: 2 ports detected
[    2.180875] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.180881] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.180918] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.180939] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    2.181049] hub 4-0:1.0: USB hub found
[    2.181053] hub 4-0:1.0: 2 ports detected
[    2.181127] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.181133] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.181169] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.181188] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000dc00
[    2.181310] hub 5-0:1.0: USB hub found
[    2.181313] hub 5-0:1.0: 2 ports detected
[    2.181424] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.181426] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.182055] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.182124] mice: PS/2 mouse device common for all mice
[    2.182223] rtc_cmos 00:05: RTC can wake from S4
[    2.182271] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.182322] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.182464] device-mapper: uevent: version 1.0.3
[    2.186419] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    2.190235] device-mapper: multipath: version 1.1.1 loaded
[    2.190241] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.198611] cpuidle: using governor ladder
[    2.198617] cpuidle: using governor menu
[    2.198968] TCP cubic registered
[    2.199132] NET: Registered protocol family 10
[    2.199525] lo: Disabled Privacy Extensions
[    2.199731] NET: Registered protocol family 17
[    2.199773] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    2.199818] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20100428/processor_perflib-322)
[    2.204150] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    2.204235] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.204342] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20100428/processor_perflib-322)
[    2.204440] PM: Resume from disk failed.
[    2.204456] registered taskstats version 1
[    2.204710]   Magic number: 11:42:689
[    2.204830] rtc_cmos 00:05: setting system clock to 2011-09-04 15:41:52 UTC (1315150912)
[    2.204833] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.204835] EDD information not available.
[    3.202488] Freeing initrd memory: 11516k freed
[    3.215622] Freeing unused kernel memory: 908k freed
[    3.216654] Write protecting the kernel read-only data: 10240k
[    3.216823] Freeing unused kernel memory: 416k freed
[    3.217408] Freeing unused kernel memory: 1644k freed
[    3.249760] udev[77]: starting version 163
[    3.478464] Floppy drive(s): fd0 is 1.44M
[    3.510682] VIA Networking Velocity Family Gigabit Ethernet Adapter Driver Ver. 1.15
[    3.510687] Copyright (c) 2002, 2003 VIA Networking Technologies, Inc.
[    3.510689] Copyright (c) 2004 Red Hat Inc.
[    3.510709]   alloc irq_desc for 22 on node 0
[    3.510711]   alloc kstat_irqs on node 0
[    3.510724] via-velocity 0000:00:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.511910] eth0: VIA Networking Velocity Family Gigabit Ethernet Adapter
[    3.511914] eth0: Ethernet Address: 00:50:8d:64:43:9d
[    3.516356] FDC 0 is a post-1991 82077
[    3.542906] pata_via 0000:00:0f.1: version 0.3.4
[    3.542929] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    3.543136] scsi0 : pata_via
[    3.543340] scsi1 : pata_via
[    3.545043] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xcc00 irq 14
[    3.545046] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xcc08 irq 15
[    3.545518] sata_via 0000:00:0f.0: version 2.6
[    3.545537] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    3.545583] sata_via 0000:00:0f.0: routed to hard irq line 11
[    3.545672] scsi2 : sata_via
[    3.545789] scsi3 : sata_via
[    3.545836] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xc400 irq 20
[    3.545839] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xc408 irq 20
[    3.546563] [drm] Initialized drm 1.1.0 20060810
[    3.546619] firewire_ohci 0000:00:0c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.610009] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.720435] firewire_ohci: Added fw-ohci device 0000:00:0c.0, OHCI v1.0, 4 IR + 8 IT contexts, quirks 0x2
[    3.741624] ata1.00: ATA-6: WDC WD1200JB-00GVA0, 08.02D08, max UDMA/100
[    3.741627] ata1.00: 234441648 sectors, multi 16: LBA48 
[    3.742662] ata1.01: ATA-6: WDC WD400LB-00DNA0, 77.07W77, max UDMA/100
[    3.742665] ata1.01: 78165360 sectors, multi 16: LBA48 
[    3.750009] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.781493] ata1.00: configured for UDMA/100
[    3.821175] ata1.01: configured for UDMA/100
[    3.821323] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5
[    3.821513] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.821823] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400LB-00DN 77.0 PQ: 0 ANSI: 5
[    3.821939] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    3.822245] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    3.822295] sd 0:0:0:0: [sda] Write Protect is off
[    3.822298] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.822320] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.822474]  sda: sda1
[    3.844864] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.844901] sd 0:0:1:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    3.844940] sd 0:0:1:0: [sdb] Write Protect is off
[    3.844943] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.844961] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.845085]  sdb: sdb1
[    3.871595] sd 0:0:1:0: [sdb] Attached SCSI disk
[    3.930187] ata3.00: ATA-8: OCZ-VERTEX2, 1.33, max UDMA/133
[    3.930190] ata3.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.970191] ata3.00: configured for UDMA/133
[    4.000330] ata2.00: ATAPI: CW099D ATAPI CD-R/RW, VER 120M, max UDMA/33
[    4.040244] ata2.00: configured for UDMA/33
[    4.040679] scsi 1:0:0:0: CD-ROM            CyberDrv CW099D CD-R/RW   120M PQ: 0 ANSI: 5
[    4.041899] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    4.041903] Uniform CD-ROM driver Revision: 3.20
[    4.042021] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.042096] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    4.042426] scsi 2:0:0:0: Direct-Access     ATA      OCZ-VERTEX2      1.33 PQ: 0 ANSI: 5
[    4.042560] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    4.042917] sd 2:0:0:0: [sdc] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.042966] sd 2:0:0:0: [sdc] Write Protect is off
[    4.042969] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.042991] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.043138]  sdc: sdc1
[    4.043864] sd 2:0:0:0: [sdc] Attached SCSI disk
[    4.220106] firewire_core: created device fw0: GUID 00309526b0151034, S400
[    4.250011] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.287627] usbcore: registered new interface driver hiddev
[    4.302914] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input3
[    4.303125] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:10.1-1/input0
[    4.303246] usbcore: registered new interface driver usbhid
[    4.303248] usbhid: USB HID core driver
[    4.352795]   alloc irq_desc for 16 on node 0
[    4.352800]   alloc kstat_irqs on node 0
[    4.352813] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.359367] [drm] nouveau 0000:01:00.0: Detected an NV30 generation card (0x035200a1)
[    4.359511] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    4.397120] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    4.397344] [drm] nouveau 0000:01:00.0: BMP BIOS found
[    4.397346] [drm] nouveau 0000:01:00.0: BMP version 5.41
[    4.397350] [drm] nouveau 0000:01:00.0: Bios version 04.35.20.45
[    4.397353] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.2
[    4.397357] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00009c40
[    4.397361] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02010310 00009c40
[    4.397363] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02110312 00000010
[    4.397366] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02020321 00000703
[    4.397510] [drm] nouveau 0000:01:00.0: Loading NV17 power sequencing microcode
[    4.397514] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xEEDF
[    4.397789] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xF1CF
[    4.410012] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xF05D
[    4.410053] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xF461
[    4.410177] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xF47E
[    4.410300] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 5 at offset 0xF49B
[    4.450019] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 6 at offset 0xF7CC
[    4.450025] [drm] nouveau 0000:01:00.0: Detected 128MiB VRAM
[    4.460298] [TTM] Zone  kernel: Available graphics memory: 511528 kiB.
[    4.460300] [TTM] Initializing pool allocator.
[    4.460398] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[    4.460414] agpgart: work_for_cpu tried to set rate=x12. Setting to AGP3 x8 mode.
[    4.460421] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[    4.460486] nouveau 0000:01:00.0: putting AGP V3 device into 8x mode
[    4.460490] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[    4.460997] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[    4.462488] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[    4.462495] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[    4.462501] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[    4.500730] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    4.501419] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[    4.501505] [drm] nouveau 0000:01:00.0: Detected a TV connector
[    4.502712] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[    4.502715] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[    4.502719] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
[    4.502723] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[    4.740458] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x49000, bo ffff88003b8a4400
[    4.751782] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output B
[    4.751787] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 2)
[    4.751790] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output B
[    4.753987] Console: switching to colour frame buffer device 160x64
[    4.754704] fb0: nouveaufb frame buffer device
[    4.754706] drm: registered panic notifier
[    4.754711] Slow work thread pool: Starting up
[    4.754800] Slow work thread pool: Ready
[    4.754810] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    5.231069] Btrfs loaded
[    5.237859] xor: automatically using best checksumming function: generic_sse
[    5.280004]    generic_sse:  7236.800 MB/sec
[    5.280007] xor: using function: generic_sse (7236.800 MB/sec)
[    5.283591] device-mapper: dm-raid45: initialized v0.2594b
[    5.855482] EXT3-fs: barriers not enabled
[    5.855667] kjournald starting.  Commit interval 5 seconds
[    5.855752] EXT3-fs (sdc1): mounted filesystem with ordered data mode
[    6.847737] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.869634] ISO 9660 Extensions: RRIP_1991A
[    6.958127] aufs 2-standalone.tree-35-rcN-20100705
[    7.017576] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   46.370117] udev[1309]: starting version 163
[   48.999121] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.536891] EDAC MC: Ver: 2.1.0 Sep 19 2010
[   49.720468] EDAC amd64_edac:  Ver: 3.3.0 Sep 19 2010
[   49.726463] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   49.726472] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   49.726474]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   49.726476]  (Note that use of the override may cause unknown side effects.)
[   49.726496] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   49.941043] parport_pc 00:0a: reported by Plug and Play ACPI
[   49.941079] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   50.597618] ppdev: user-space parallel port driver
[   51.890066] via-velocity 0000:00:0e.0: BAR 0: set to [io  0xb000-0xb0ff] (PCI address [0xb000-0xb0ff]
[   51.890075] via-velocity 0000:00:0e.0: BAR 1: set to [mem 0xee005000-0xee0050ff] (PCI address [0xee005000-0xee0050ff]
[   51.930020] via-velocity 0000:00:0e.0: BAR 0: set to [io  0xb000-0xb0ff] (PCI address [0xb000-0xb0ff]
[   51.930028] via-velocity 0000:00:0e.0: BAR 1: set to [mem 0xee005000-0xee0050ff] (PCI address [0xee005000-0xee0050ff]
[   51.975081] via-velocity 0000:00:0e.0: BAR 0: set to [io  0xb000-0xb0ff] (PCI address [0xb000-0xb0ff]
[   51.975089] via-velocity 0000:00:0e.0: BAR 1: set to [mem 0xee005000-0xee0050ff] (PCI address [0xee005000-0xee0050ff]
[   52.010032] via-velocity 0000:00:0e.0: BAR 0: set to [io  0xb000-0xb0ff] (PCI address [0xb000-0xb0ff]
[   52.010040] via-velocity 0000:00:0e.0: BAR 1: set to [mem 0xee005000-0xee0050ff] (PCI address [0xee005000-0xee0050ff]
[   52.025605] Velocity is AUTO mode
[   52.764927] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   52.765080] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   53.612860] eth0: failed to detect cable link
[   53.719595] lp0: using parport0 (interrupt-driven).
[   56.316145] eth0: Link auto-negotiation speed 100M bps full duplex
[   62.739196] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   62.739650] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   62.760030] eth0: no IPv6 routers present
[   80.897613] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
[   97.342652] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 2)

```

---

