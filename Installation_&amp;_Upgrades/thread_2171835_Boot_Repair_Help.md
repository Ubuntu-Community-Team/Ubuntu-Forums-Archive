---
title: "Boot Repair Help"
date: 2013-09-01
forum: Installation &amp; Upgrades
---

### Post by revzalot on 2013-09-01
I attempted to use boot repair off a Live CD and I was able to create a report.  
However, Boot repair kept complaining about turning off Software update managers and never completed after turning off all the software updates.
I've posted my boot repair here: [http://paste.ubuntu.com/6052997/](http://paste.ubuntu.com/6052997/)

My LVM2 filesystem was composed of two 750Gig drives running mdadm and 3 500 gigs drive using a Dell CERC Raid controller - sda5.  

I've attempted to mount my LVM partition to /mnt via LiveCD but kept getting wrong fs type.

---

### Post by revzalot on 2013-09-01
Here's the actual boot repair report: 
 Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 28Aug2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sda.
 [COLOR=#666666]=[/COLOR]> Grub Legacy is installed in the MBR of /dev/sdb and looks at sector 48193 
    on boot drive [COLOR=#008800]*#2 for the stage2 file, but no stage2 files can be found at *[/COLOR]
    this location..
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/grub on this drive.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

ubuntu-root[COLOR=#BB4444]': __________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       [/COLOR]
[COLOR=#BB4444]    Boot sector type:  Unknown[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]
[COLOR=#BB4444]    Mounting failed:   mount: unknown filesystem type ''[/COLOR]
[COLOR=#BB4444]mount: unknown filesystem type ''[/COLOR]

[COLOR=#BB4444]ubuntu-swap_1'[/COLOR]: ________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]
mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]
mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1                  63 1,465,144,064 1,465,144,002  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1               2,048 1,465,147,391 1,465,145,344  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.1 GB, 1000146337792 bytes
255 heads, 63 sectors/track, 121594 cylinders, total 1953410816 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdc1    *          2,048       499,711       497,664  83 Linux
/dev/sdc2             501,758 1,953,409,023 1,952,907,266   5 Extended
/dev/sdc5             501,760 1,953,409,023 1,952,907,264  8e Linux LVM


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/ubuntu-swap_1 21881d55-cc68-4d28-911b-906310f9c0f5   swap       
/dev/sda1        b9435ceb-429d-382e-f2e3-94d14ed70b2c   linux_raid_member 
/dev/sdb1        b9435ceb-429d-382e-f2e3-94d14ed70b2c   linux_raid_member 
/dev/sdc5        ktGiZe-Umzk-Ghij-3fBn-15xt-U496-6BjnFj LVM2_member 
/dev/sr0                                                iso9660    Xubuntu 13.04 [COLOR=#B8860B]i386[/COLOR]

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -R /dev/mapper/"[/COLOR] output: [COLOR=#666666]=========================[/COLOR]

/dev/mapper:
control
ubuntu-swap_1

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sr0         /cdrom                   iso9660    [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]


[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sdc1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ca 60  |............. .[COLOR=#BB4444]`[/COLOR]|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 80 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 4e 3c  |............. N<|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 20 9d  |.............  .|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 fb 3d  |............. .[COLOR=#666666]=[/COLOR]|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ff 9f  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 24 3f  |............. [COLOR=#B8860B]$?[/COLOR]|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 4a 9e  |............. J.|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 91 3e  |............. .>|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 41 9a  |............. A.|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 9a 3a  |............. .:|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 f4 9b  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 2f 3b  |............. /;|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 2b 99  |............. +.|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 f0 39  |............. .9|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 9e 98  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 45 38  |............. E8|
00000200

Unknown BootLoader on sdc2

00000000  70 73 70 6f 74 25 32 45  63 6f 6d 25 32 46 34 30  |pspot%2Ecom%2F40|
00000010  30 78 30 78 38 35 25 32  46 25 33 46 75 72 6c 25  |0x0x85%2F%3Furl%|
00000020  33 44 68 74 74 70 25 32  35 33 41 25 32 35 32 46  |3Dhttp%253A%252F|
00000030  25 32 35 32 46 73 33 25  32 45 62 6f 78 65 65 25  |%252Fs3%2Eboxee%|
00000040  32 45 74 76 25 32 35 32  46 74 69 74 6c 65 74 68  |2Etv%252Ftitleth|
00000050  75 6d 62 73 25 32 35 32  46 36 25 32 35 32 46 30  |umbs%252F6%252F0|
00000060  25 32 35 32 46 36 66 63  32 30 64 32 62 37 63 34  |%252F6fc20d2b7c4|
00000070  37 32 31 30 66 37 31 61  30 37 63 61 30 61 65 62  |7210f71a07ca0aeb|
00000080  63 31 65 25 32 45 6a 70  67 27 20 61 6e 64 20 28  |c1e%2Ejpg[COLOR=#BB4444]' and (|[/COLOR]
[COLOR=#BB4444]00000090  65 78 70 69 72 65 5f 74  69 6d 65 20 69 73 20 6e  |expire_time is n|[/COLOR]
[COLOR=#BB4444]000000a0  75 6c 6c 20 6f 72 20 65  78 70 69 72 65 5f 74 69  |ull or expire_ti|[/COLOR]
[COLOR=#BB4444]000000b0  6d 65 20 3c 20 31 33 30  38 37 35 38 39 33 31 29  |me < 1308758931)|[/COLOR]
[COLOR=#BB4444]000000c0  0a 30 39 3a 30 39 3a 32  34 20 54 3a 31 34 30 31  |.09:09:24 T:1401|[/COLOR]
[COLOR=#BB4444]000000d0  37 35 37 39 32 31 35 38  34 36 34 20 4d 3a 34 35  |75792158464 M:45|[/COLOR]
[COLOR=#BB4444]000000e0  31 35 34 33 30 34 30 20  20 20 45 52 52 4f 52 3a  |1543040   ERROR:|[/COLOR]
[COLOR=#BB4444]000000f0  20 45 78 63 65 70 74 69  6f 6e 20 63 61 75 67 68  | Exception caugh|[/COLOR]
[COLOR=#BB4444]00000100  74 20 6f 6e 20 71 75 65  72 79 2e 20 45 72 72 6f  |t on query. Erro|[/COLOR]
[COLOR=#BB4444]00000110  72 20 3d 20 31 31 2c 20  6d 73 67 3d 20 64 61 74  |r = 11, msg= dat|[/COLOR]
[COLOR=#BB4444]00000120  61 62 61 73 65 20 64 69  73 6b 20 69 6d 61 67 65  |abase disk image|[/COLOR]
[COLOR=#BB4444]00000130  20 69 73 20 6d 61 6c 66  6f 72 6d 65 64 0a 30 39  | is malformed.09|[/COLOR]
[COLOR=#BB4444]00000140  3a 30 39 3a 32 34 20 54  3a 31 34 30 31 37 35 37  |:09:24 T:1401757|[/COLOR]
[COLOR=#BB4444]00000150  39 32 31 35 38 34 36 34  20 4d 3a 34 35 31 35 34  |92158464 M:45154|[/COLOR]
[COLOR=#BB4444]00000160  33 30 34 30 20 20 20 45  52 52 4f 52 3a 20 53 51  |3040   ERROR: SQ|[/COLOR]
[COLOR=#BB4444]00000170  4c 69 74 65 3a 20 54 68  65 20 64 61 74 61 62 61  |Lite: The databa|[/COLOR]
[COLOR=#BB4444]00000180  73 65 20 64 69 73 6b 20  69 6d 61 67 65 20 69 73  |se disk image is|[/COLOR]
[COLOR=#BB4444]00000190  20 6d 61 6c 66 6f 72 6d  65 64 0a 20 20 20 20 20  | malformed.     |[/COLOR]
[COLOR=#BB4444]000001a0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |[/COLOR]
[COLOR=#BB4444]000001b0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 00 3b  |              .;|[/COLOR]
[COLOR=#BB4444]000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 00 67 74 00 00  |............gt..|[/COLOR]
[COLOR=#BB4444]000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]*[/COLOR]
[COLOR=#BB4444]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]

[COLOR=#BB4444]Unknown BootLoader on ubuntu-root'[/COLOR]


Unknown BootLoader on ubuntu-swap_1[COLOR=#BB4444]'[/COLOR]



[COLOR=#BB4444]=============================== StdErr Messages: ===============================[/COLOR]

[COLOR=#BB4444]File descriptor 8 (/proc/11189/mounts) leaked on lvscan invocation. Parent PID 17045: bash[/COLOR]
[COLOR=#BB4444]  Couldn'[/COLOR]t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.
File descriptor 8 [COLOR=#666666]([/COLOR]/proc/11189/mounts[COLOR=#666666])[/COLOR] leaked on lvdisplay invocation. Parent PID 17050: bash
  Couldn[COLOR=#BB4444]'t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.[/COLOR]
[COLOR=#BB4444]  One or more specified logical volume(s) not found.[/COLOR]
[COLOR=#BB4444]File descriptor 8 (/proc/11189/mounts) leaked on lvdisplay invocation. Parent PID 17055: bash[/COLOR]
[COLOR=#BB4444]  Couldn'[/COLOR]t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.
  One or more specified logical volume[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR] not found.
File descriptor 8 [COLOR=#666666]([/COLOR]/proc/11189/mounts[COLOR=#666666])[/COLOR] leaked on lvchange invocation. Parent PID 16580: bash
  Couldn[COLOR=#BB4444]'t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.[/COLOR]
[COLOR=#BB4444]  One or more specified logical volume(s) not found.[/COLOR]
[COLOR=#BB4444]hexdump: /dev/mapper/ubuntu-root'[/COLOR]: No such file or directory
hexdump: /dev/mapper/ubuntu-root[COLOR=#BB4444]': No such file or directory[/COLOR]
[COLOR=#BB4444]File descriptor 8 (/proc/11189/mounts) leaked on lvdisplay invocation. Parent PID 17089: bash[/COLOR]
[COLOR=#BB4444]  Couldn'[/COLOR]t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.
  One or more specified logical volume[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR] not found.
File descriptor 8 [COLOR=#666666]([/COLOR]/proc/11189/mounts[COLOR=#666666])[/COLOR] leaked on lvdisplay invocation. Parent PID 17093: bash
  Couldn[COLOR=#BB4444]'t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.[/COLOR]
[COLOR=#BB4444]  One or more specified logical volume(s) not found.[/COLOR]
[COLOR=#BB4444]File descriptor 8 (/proc/11189/mounts) leaked on lvchange invocation. Parent PID 16580: bash[/COLOR]
[COLOR=#BB4444]  Couldn'[/COLOR]t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.
  One or more specified logical volume[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR] not found.
hexdump: /dev/mapper/ubuntu-swap_1[COLOR=#BB4444]': No such file or directory[/COLOR]
[COLOR=#BB4444]hexdump: /dev/mapper/ubuntu-swap_1'[/COLOR]: No such file or directory

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2013-09-01__22h03 [COLOR=#666666]===================[/COLOR]
boot-repair version : 3.199~ppa24~raring
boot-sav version : 3.199~ppa24~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa24~raring
BLKID BEFORE LVM ACTIVATION:
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sr0: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Xubuntu 13.04 i386"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"iso9660"[/COLOR]
/dev/sda1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"b9435ceb-429d-382e-f2e3-94d14ed70b2c"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdb1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"b9435ceb-429d-382e-f2e3-94d14ed70b2c"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdc5: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ktGiZe-Umzk-Ghij-3fBn-15xt-U496-6BjnFj"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"LVM2_member"[/COLOR]
/dev/mapper/ubuntu-swap_1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"21881d55-cc68-4d28-911b-906310f9c0f5"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
MODPROBE
VGSCAN
File descriptor 8 [COLOR=#666666]([/COLOR]/proc/11189/mounts[COLOR=#666666])[/COLOR] leaked on vgscan invocation. Parent PID 11197: /bin/bash
Reading all physical volumes.  This may take a [COLOR=#AA22FF]**while**[/COLOR]...
Couldn[COLOR=#BB4444]'t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.[/COLOR]
[COLOR=#BB4444]Found volume group "ubuntu" using metadata type lvm2[/COLOR]
[COLOR=#BB4444]VGCHANGE[/COLOR]
[COLOR=#BB4444]File descriptor 8 (/proc/11189/mounts) leaked on vgchange invocation. Parent PID 11197: /bin/bash[/COLOR]
[COLOR=#BB4444]Couldn'[/COLOR]t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.
Refusing activation of partial LV root. Use --partial to override.
1 logical volume[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR] in volume group [COLOR=#BB4444]"ubuntu"[/COLOR] now active
File descriptor 8 [COLOR=#666666]([/COLOR]/proc/11189/mounts[COLOR=#666666])[/COLOR] leaked on lvscan invocation. Parent PID 11197: /bin/bash
Couldn[COLOR=#BB4444]'t find device with uuid QOUN3V-Mh26-peW3-fz45-sSnn-HqfF-XJLtvs.[/COLOR]
[COLOR=#BB4444]LVSCAN:[/COLOR]
[COLOR=#BB4444]inactive          '[/COLOR]/dev/ubuntu/root[COLOR=#BB4444]' [1.49 TiB] inherit[/COLOR]
[COLOR=#BB4444]ACTIVE            '[/COLOR]/dev/ubuntu/swap_1[COLOR=#BB4444]' [1.99 GiB] inherit[/COLOR]
[COLOR=#BB4444]Warning: inactive LVM[/COLOR]

[COLOR=#BB4444]BLKID BEFORE RAID ACTIVATION:[/COLOR]
[COLOR=#BB4444]/dev/loop0: TYPE="squashfs"[/COLOR]
[COLOR=#BB4444]/dev/sr0: LABEL="Xubuntu 13.04 i386" TYPE="iso9660"[/COLOR]
[COLOR=#BB4444]/dev/sda1: UUID="b9435ceb-429d-382e-f2e3-94d14ed70b2c" TYPE="linux_raid_member"[/COLOR]
[COLOR=#BB4444]/dev/sdb1: UUID="b9435ceb-429d-382e-f2e3-94d14ed70b2c" TYPE="linux_raid_member"[/COLOR]
[COLOR=#BB4444]/dev/sdc5: UUID="ktGiZe-Umzk-Ghij-3fBn-15xt-U496-6BjnFj" TYPE="LVM2_member"[/COLOR]
[COLOR=#BB4444]/dev/mapper/ubuntu-swap_1: UUID="21881d55-cc68-4d28-911b-906310f9c0f5" TYPE="swap"[/COLOR]
[COLOR=#BB4444]dmraid -si -c: no raid disks[/COLOR]
[COLOR=#BB4444]No DMRAID disk.[/COLOR]
[COLOR=#BB4444]RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y --force-yes mdadm --no-install-recommends)[/COLOR]
[COLOR=#BB4444]Warning: no DMRAID nor MD_ARRAY.[/COLOR]
[COLOR=#BB4444]boot-repair is executed in live-session (Ubuntu 13.04, raring, Ubuntu, i686)[/COLOR]
[COLOR=#BB4444]ls: cannot access /home/usr/.config: No such file or directory[/COLOR]
[COLOR=#BB4444]file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity[/COLOR]
[COLOR=#BB4444]Disk /dev/mapper/ubuntu-swap_1 doesn'[/COLOR]t contain a valid partition [COLOR=#B8860B]table[/COLOR]

[COLOR=#666666]===================[/COLOR] os-prober:


[COLOR=#666666]===================[/COLOR] blkid:
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sr0: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Xubuntu 13.04 i386"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"iso9660"[/COLOR]
/dev/sda1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"b9435ceb-429d-382e-f2e3-94d14ed70b2c"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdb1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"b9435ceb-429d-382e-f2e3-94d14ed70b2c"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdc5: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ktGiZe-Umzk-Ghij-3fBn-15xt-U496-6BjnFj"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"LVM2_member"[/COLOR]
/dev/mapper/ubuntu-swap_1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"21881d55-cc68-4d28-911b-906310f9c0f5"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]

[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	63 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA SAMSUNG HD753LJ [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 750GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  750GB  750GB  primary               raid


Model: ATA ST3750640AS [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 750GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  750GB  750GB  primary               raid


Model: CERC nasr5 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdc: 1000GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      1049kB  256MB   255MB   primary                boot
2      257MB   1000GB  1000GB  extended
5      257MB   1000GB  1000GB  logical                lvm


Model: Linux device-mapper [COLOR=#666666]([/COLOR]linear[COLOR=#666666])[/COLOR] [COLOR=#666666]([/COLOR]dm[COLOR=#666666])[/COLOR]
Disk /dev/mapper/ubuntu-swap_1: 2139MB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
1      0.00B  2139MB  2139MB  linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]



                                                                          
Warning: Unable to open /dev/sr0 [COLOR=#AA22FF]read[/COLOR]-write [COLOR=#666666]([/COLOR]Read-only file system[COLOR=#666666])[/COLOR].  /dev/sr0
has been opened [COLOR=#AA22FF]read[/COLOR]-only.

                                                                          
Error: Can[COLOR=#BB4444]'t have a partition outside the disk![/COLOR]

[COLOR=#BB4444]=================== parted -lm:[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/sda:750GB:scsi:512:512:msdos:ATA SAMSUNG HD753LJ;[/COLOR]
[COLOR=#BB4444]1:32.3kB:750GB:750GB:::raid;[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/sdb:750GB:scsi:512:512:msdos:ATA ST3750640AS;[/COLOR]
[COLOR=#BB4444]1:1049kB:750GB:750GB:::raid;[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/sdc:1000GB:scsi:512:512:msdos:CERC nasr5;[/COLOR]
[COLOR=#BB4444]1:1049kB:256MB:255MB:::boot;[/COLOR]
[COLOR=#BB4444]2:257MB:1000GB:1000GB:::;[/COLOR]
[COLOR=#BB4444]5:257MB:1000GB:1000GB:::lvm;[/COLOR]

[COLOR=#BB4444]BYT;[/COLOR]
[COLOR=#BB4444]/dev/mapper/ubuntu-swap_1:2139MB:dm:512:512:loop:Linux device-mapper (linear);[/COLOR]
[COLOR=#BB4444]1:0.00B:2139MB:2139MB:linux-swap(v1)::;[/COLOR]


[COLOR=#BB4444]                                                                          [/COLOR]
[COLOR=#BB4444]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/COLOR]
[COLOR=#BB4444]has been opened read-only.[/COLOR]

[COLOR=#BB4444]                                                                          [/COLOR]
[COLOR=#BB4444]Error: Can'[/COLOR]t have a partition outside the disk!


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sr0 on /cdrom [COLOR=#AA22FF]type [/COLOR]iso9660 [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/xubuntu/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]xubuntu[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/dm-0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 sdc5 size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  agpgart alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dm-0 dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdc1 sdc2 sdc5 sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout ubuntu uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control ubuntu-swap_1
Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition [COLOR=#B8860B]table[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1003M  172M  832M  18% /
udev           devtmpfs   992M   12K  992M   1% /dev
tmpfs          tmpfs      201M  804K  200M   1% /run
/dev/sr0       iso9660    789M  789M     0 100% /cdrom
/dev/loop0     squashfs   756M  756M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1003M   12K 1003M   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     1003M  148K 1003M   1% /run/shm
none           tmpfs      100M   20K  100M   1% /run/user

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x000c5134

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1465144064   732572001   fd  Linux raid autodetect

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x000a8d2f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1465147391   732572672   fd  Linux raid autodetect

Disk /dev/sdc: 1000.1 GB, 1000146337792 bytes
255 heads, 63 sectors/track, 121594 cylinders, total 1953410816 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00068c01

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758  1953409023   976453633    5  Extended
/dev/sdc5          501760  1953409023   976453632   8e  Linux LVM

Disk /dev/mapper/ubuntu-swap_1: 2139 MB, 2139095040 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4177920 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00000000


Error: no partitions
Partition outside the disk detected.

[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would reinstall the  of .
Additional repair would be performed:  repair-filesystems

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

---

