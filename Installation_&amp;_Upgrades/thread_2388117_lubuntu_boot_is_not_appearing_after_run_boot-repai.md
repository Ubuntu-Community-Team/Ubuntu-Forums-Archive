---
title: "lubuntu boot is not appearing after run boot-repair"
date: 2018-03-28
forum: Installation &amp; Upgrades
---

### Post by jonnytobaios on 2018-03-28
Hello ,


i have mbr disk .pre installed windows 8 ,then i chose the option install lubuntu 17.10 alongside windows 8 . then i boot and lubuntu starts without boot option for windows. After run boot -repair and disapear lubuntu boot option and only windows are being loaded . Can someone help me solve the problem 

my pc is laptom Asus X 501a. thank you in advance

---

### Post by oldfred on 2018-03-28
Post link to Summary Report from Boot-Repair.

If Windows 8 was pre-installed it should be gpt and UEFI. 
Only if you installed it might it be BIOS with MBR(msdos) partitioning.

---

### Post by jonnytobaios on 2018-03-28
[http://paste.ubuntu.com/p/s4fxzbfhpr/](http://paste.ubuntu.com/p/s4fxzbfhpr/)   ..yes u right ,i installed windows again .. after a problem i have experienced

---

### Post by jonnytobaios on 2018-03-28
```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]





============================= Boot Info Summary: ===============================



 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.



sda1: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows 8/2012: NTFS

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files:        /bootmgr /Boot/BCD



sda2: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows 8/2012: NTFS

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows 8

    Boot files:        /bootmgr /Windows/System32/winload.exe



sda3: __________________________________________________________________________



    File system:       Extended Partition

    Boot sector type:  -

    Boot sector info: 



sda5: __________________________________________________________________________



    File system:       ext4

    Boot sector type:  -

    Boot sector info: 

    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,

       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so





============================ Drive/Partition Info: =============================



Drive: sda _____________________________________________________________________



Disk /dev/sda: 320.1 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes



Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS

/dev/sda2             718,848   204,802,047   204,083,200   7 NTFS / exFAT / HPFS

/dev/sda3         204,804,094   625,141,759   420,337,666   5 Extended

/dev/sda5         204,804,096   625,141,759   420,337,664  83 Linux





"blkid" output: ________________________________________________________________



Device           UUID                                   TYPE       LABEL



/dev/loop0                                              squashfs   

/dev/sda1        3CE07120E070E196                       ntfs       &#926;”&#926;µ&#927;ƒ&#926;&#908;&#926;µ&#927;…&#926;&#908;&#926;*&#926;½&#926;&#911; &#926;±&#927;€&#927;&#65533; &#927;„&#926;&#911; &#927;ƒ&#927;&#65533;&#927;ƒ&#927;„&#926;·&#926;&#908;&#926;±

/dev/sda2        82927D11927D0AC5                       ntfs       

/dev/sda5        4d5f9d69-f72c-4947-811d-1d5f7d993bfa   ext4       

/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit



================================ Mount points: =================================



Device           Mount_Point              Type       Options



/dev/loop0       /rofs                    squashfs   (ro,noatime)

/dev/sr0         /cdrom                   iso9660    (ro,noatime)





=============================== StdErr Messages: ===============================



File descriptor 8 (/proc/2668/mounts) leaked on lvscan invocation. Parent PID 9526: bash

  No volume groups found



ADDITIONAL INFORMATION :

=================== log of boot-repair 2018-03-28__23h16 ===================

boot-repair version : 3.198~ppa16~raring

boot-sav version : 3.198~ppa16~raring

glade2script version : 3.2.2~ppa45~raring

boot-sav-extra version : 3.198~ppa16~raring

File descriptor 8 (/proc/2668/mounts) leaked on lvs invocation. Parent PID 4253: /bin/sh

No volume groups found

boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)

ls: cannot access /home/usr/.config: No such file or directory

CPU op-mode(s):        32-bit, 64-bit

file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

mount: wrong fs type, bad option, bad superblock on /dev/sda5,

missing codepage or helper program, or other error

In some cases useful info is found in syslog - try

dmesg | tail  or so



mount /dev/sda5 -> Error code 32



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





=================== os-prober:

/dev/sda1:Windows 8 (loader):Windows:chain



=================== blkid:

/dev/loop0: TYPE="squashfs"

/dev/sda1: LABEL="M-NM-^TM-NM-5M-OM-^CM-NM-<M-NM-5M-OM-^EM-NM-<M-NM--M-NM-=M-NM-? M-NM-1M-OM-^@M-OM-^L M-OM-^DM-NM-? M-OM-^CM-OM-^MM-OM-^CM-OM-^DM-NM-7M-NM-<M-NM-1" UUID="3CE07120E070E196" TYPE="ntfs"

/dev/sda2: UUID="82927D11927D0AC5" TYPE="ntfs"

/dev/sda5: UUID="4d5f9d69-f72c-4947-811d-1d5f7d993bfa" TYPE="ext4"

/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"





1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.



mount: wrong fs type, bad option, bad superblock on /dev/sda5,

missing codepage or helper program, or other error

In some cases useful info is found in syslog - try

dmesg | tail  or so



mount /dev/sda5 -> Error code 32

Windows not detected by os-prober on sda2.



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.



Warning: extended partition does not start at a cylinder boundary.

DOS and Linux will interpret the contents differently.



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== UEFI/Legacy mode:

This live-session is not in EFI-mode.

SecureBoot maybe enabled.





=================== PARTITIONS & DISKS:

sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.

sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda2.

sda5	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.



sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes





=================== parted -l:



Model: ATA WDC WD3200BPVT-8 (scsi)

Disk /dev/sda: 320GB

Sector size (logical/physical): 512B/4096B

Partition Table: msdos



Number  Start   End    Size   Type      File system  Flags

1      1049kB  368MB  367MB  primary   ntfs         boot

2      368MB   105GB  104GB  primary   ntfs

3      105GB   320GB  215GB  extended

5      105GB   320GB  215GB  logical   ext4





,mode=0755)

/dev/sr0 on /cdrom type iso9660 (ro,noatime)

/dev/loop0 on /rofs type squashfs (ro,noatime)

none on /sys/fs/cgroup type tmpfs (rw)

none on /sys/fs/fuse/connections type fusectl (rw)

none on /sys/kernel/debug type debugfs (rw)

none on /sys/kernel/security type securityfs (rw)

tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)

none on /run/shm type tmpfs (rw,nosuid,nodev)

none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)

gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)

/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)





=================== ls:

/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 size slaves stat subsystem trace uevent

/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent

/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net
 video0 zero

ls /dev/mapper:  control



=================== hexdump -n512 -C /dev/sda1

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|

00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|

00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|

00000040  f6 00 00 00 01 00 00 00  96 e1 70 e0 20 71 e0 3c  |..........p. q.<|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|

00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|

00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|

00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|

000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|

000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|

000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|

000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|

000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|

00000200



=================== hexdump -n512 -C /dev/sda2

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f8 0a 00  |........?.......|

00000020  00 00 00 00 80 00 80 00  ff 0f 2a 0c 00 00 00 00  |..........*.....|

00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|

00000040  f6 00 00 00 01 00 00 00  c5 0a 7d 92 11 7d 92 82  |..........}..}..|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|

00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|

00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|

00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|

000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|

000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|

000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|

000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|

000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|

00000200



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





=================== df -Th:



Filesystem     Type       Size  Used Avail Use% Mounted on

/cow           overlayfs  1.9G   20M  1.9G   2% /

udev           devtmpfs   1.9G   12K  1.9G   1% /dev

tmpfs          tmpfs      384M  796K  384M   1% /run

/dev/sr0       iso9660    508M  508M     0 100% /cdrom

/dev/loop0     squashfs   435M  435M     0 100% /rofs

none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup

tmpfs          tmpfs      1.9G  8.0K  1.9G   1% /tmp

none           tmpfs      5.0M     0  5.0M   0% /run/lock

none           tmpfs      1.9G     0  1.9G   0% /run/shm

none           tmpfs      100M   12K  100M   1% /run/user

/dev/sda1      fuseblk    350M  240M  111M  69% /mnt/boot-sav/sda1

/dev/sda2      fuseblk     98G   48G   50G  50% /mnt/boot-sav/sda2



=================== fdisk -l:



Disk /dev/sda: 320.1 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk identifier: 0x6f3aabf5



Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT

/dev/sda2          718848   204802047   102041600    7  HPFS/NTFS/exFAT

/dev/sda3       204804094   625141759   210168833    5  Extended

Partition 3 does not start on physical sector boundary.

/dev/sda5       204804096   625141759   210168832   83  Linux







=================== Recommended repair

Recommended-Repair

This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.

Additional repair will be performed: unhide-bootmenu-10s repair-filesystems  fix-windows-boot





Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





ntfsfix /dev/sda1

Refusing to operate on read-write mounted device /dev/sda1.



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





ntfsfix /dev/sda2

Refusing to operate on read-write mounted device /dev/sda2.



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





fsck -fyM /dev/sda5

fsck from util-linux 2.20.1

e2fsck 1.42.5 (29-Jul-2012)

/dev/sda5 has unsupported feature(s): metadata_csum

e2fsck: Get a newer version of e2fsck!

mount: wrong fs type, bad option, bad superblock on /dev/sda5,

missing codepage or helper program, or other error

In some cases useful info is found in syslog - try

dmesg | tail  or so



mount /dev/sda5 -> Error code 32

Quantity of real Windows: 1

Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda

dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

0+1 records in

0+1 records out



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.





Boot successfully repaired.



You can now reboot your computer.
```

---

### Post by oldfred on 2018-03-28
Link is not working.
And you need to use code tags on longer text or terminal output.
Easy to add code tags with Forum's advanced editor and # icon. But right now forum is not letting me add them for you.

How you boot install media UEFI or BIOS, for both Windows & Ubuntu is then how it installs.

So when you installed Windows in BIOS boot mode, it converted drive from the newer gpt to now 35 year old MBR(msdos) configuration.
And Windows does not know how to do the conversion correctly. It leaves the backup gpt partition table at end of drive.
Then Linux tools see both MBR & gpt and cannot work with that, and fail.
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt. So unless you want to totally reinstall Windows keep drive as MBR.
But with Windows 8 or 10, it turns fast start up on and will  turn it on with major updates. But that is just hibernation and Linux NTFS then cannot use the NTFS partition and grub will not boot Windows. You then have to temporarily reinstall the Windows boot loader to fix Windows & then restore grub.
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    
With UEFI, you can directly boot Windows in UEFI mode from UEFI boot menu as both Windows & Ubuntu have boot loaders in ESP - efi system  partition. With BIOS, one only boot loader can be in MBR for booting that system.

If you have to reinstall Windows you may want to consider converting to UEFI, but for now probably easier just to stay with BIOS/MBR.
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by jonnytobaios on 2018-04-06
i have removed gpt paritition as u told me and got a fresh installed of lubuntu and  now i get this ...


```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]




============================= Boot Info Summary: ===============================



 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.



sda1: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows 8/2012: NTFS

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files:        /bootmgr /Boot/BCD



sda2: __________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows 8/2012: NTFS

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows 8

    Boot files:        /bootmgr /Windows/System32/winload.exe



sda3: __________________________________________________________________________



    File system:       Extended Partition

    Boot sector type:  -

    Boot sector info: 



sda5: __________________________________________________________________________



    File system:       ext4

    Boot sector type:  -

    Boot sector info: 

    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,

       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try

       dmesg | tail  or so





============================ Drive/Partition Info: =============================



Drive: sda _____________________________________________________________________



Disk /dev/sda: 320.1 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes



Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS

/dev/sda2             718,848   204,802,047   204,083,200   7 NTFS / exFAT / HPFS

/dev/sda3         204,804,094   625,141,759   420,337,666   5 Extended

/dev/sda5         204,804,096   625,141,759   420,337,664  83 Linux





"blkid" output: ________________________________________________________________



Device           UUID                                   TYPE       LABEL



/dev/loop0                                              squashfs   

/dev/sda1        3CE07120E070E196                       ntfs       &#926;”&#926;µ&#927;ƒ&#926;&#908;&#926;µ&#927;…&#926;&#908;&#926;*&#926;½&#926;&#911; &#926;±&#927;€&#927;&#65533; &#927;„&#926;&#911; &#927;ƒ&#927;&#65533;&#927;ƒ&#927;„&#926;·&#926;&#908;&#926;±

/dev/sda2        82927D11927D0AC5                       ntfs       

/dev/sda5        b4da01fb-1803-43ea-8139-ca08d242c0ae   ext4       

/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit



================================ Mount points: =================================



Device           Mount_Point              Type       Options



/dev/loop0       /rofs                    squashfs   (ro,noatime)

/dev/sr0         /cdrom                   iso9660    (ro,noatime)





=============================== StdErr Messages: ===============================



File descriptor 8 (/proc/2655/mounts) leaked on lvscan invocation. Parent PID 9634: bash

  No volume groups found



ADDITIONAL INFORMATION :

=================== log of boot-repair 2018-04-06__18h21 ===================

boot-repair version : 3.198~ppa16~raring

boot-sav version : 3.198~ppa16~raring

glade2script version : 3.2.2~ppa45~raring

boot-sav-extra version : 3.198~ppa16~raring

File descriptor 8 (/proc/2655/mounts) leaked on lvs invocation. Parent PID 4247: /bin/sh

No volume groups found

boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)

ls: cannot access /home/usr/.config: No such file or directory

CPU op-mode(s):        32-bit, 64-bit

file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda1': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda1': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda2': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda2': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

mount: wrong fs type, bad option, bad superblock on /dev/sda5,

missing codepage or helper program, or other error

In some cases useful info is found in syslog - try

dmesg | tail  or so



mount /dev/sda5 -> Error code 32



=================== os-prober:

/dev/sda1:Windows 8 (loader):Windows:chain



=================== blkid:

/dev/loop0: TYPE="squashfs"

/dev/sda1: LABEL="M-NM-^TM-NM-5M-OM-^CM-NM-<M-NM-5M-OM-^EM-NM-<M-NM--M-NM-=M-NM-? M-NM-1M-OM-^@M-OM-^L M-OM-^DM-NM-? M-OM-^CM-OM-^MM-OM-^CM-OM-^DM-NM-7M-NM-<M-NM-1" UUID="3CE07120E070E196" TYPE="ntfs"

/dev/sda2: UUID="82927D11927D0AC5" TYPE="ntfs"

/dev/sda5: UUID="b4da01fb-1803-43ea-8139-ca08d242c0ae" TYPE="ext4"

/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"





1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.



The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda1': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda1': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda2': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2

The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda2': Operation not permitted

The NTFS partition is in an unsafe state. Please resume and shutdown

Windows fully (no hibernation or fast restarting), or mount the volume

read-only with the 'ro' mount option.

mount: wrong fs type, bad option, bad superblock on /dev/sda5,

missing codepage or helper program, or other error

In some cases useful info is found in syslog - try

dmesg | tail  or so



mount /dev/sda5 -> Error code 32

Warning: extended partition does not start at a cylinder boundary.

DOS and Linux will interpret the contents differently.

=================== UEFI/Legacy mode:

This live-session is not in EFI-mode.

SecureBoot maybe enabled.





=================== PARTITIONS & DISKS:

sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.

sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda2.

sda5	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.



sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes





=================== parted -l:



Model: ATA WDC WD3200BPVT-8 (scsi)

Disk /dev/sda: 320GB

Sector size (logical/physical): 512B/4096B

Partition Table: msdos



Number  Start   End    Size   Type      File system  Flags

1      1049kB  368MB  367MB  primary   ntfs         boot

2      368MB   105GB  104GB  primary   ntfs

3      105GB   320GB  215GB  extended

5      105GB   320GB  215GB  logical   ext4






                                                                          FS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|

00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|

00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|

00000040  f6 00 00 00 01 00 00 00  96 e1 70 e0 20 71 e0 3c  |..........p. q.<|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|

00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|

00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|

00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|

000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|

000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|

000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|

000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|

000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|

00000200



=================== hexdump -n512 -C /dev/sda2

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f8 0a 00  |........?.......|

00000020  00 00 00 00 80 00 80 00  ff 0f 2a 0c 00 00 00 00  |..........*.....|

00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|

00000040  f6 00 00 00 01 00 00 00  c5 0a 7d 92 11 7d 92 82  |..........}..}..|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|

00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|

00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|

00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|

000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|

000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|

000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|

000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|

000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|

00000200



=================== df -Th:



Filesystem     Type       Size  Used Avail Use% Mounted on

/cow           overlayfs  1.9G   20M  1.9G   2% /

udev           devtmpfs   1.9G   12K  1.9G   1% /dev

tmpfs          tmpfs      384M  796K  384M   1% /run

/dev/sr0       iso9660    508M  508M     0 100% /cdrom

/dev/loop0     squashfs   435M  435M     0 100% /rofs

none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup

tmpfs          tmpfs      1.9G  8.0K  1.9G   1% /tmp

none           tmpfs      5.0M     0  5.0M   0% /run/lock

none           tmpfs      1.9G     0  1.9G   0% /run/shm

none           tmpfs      100M   12K  100M   1% /run/user



=================== fdisk -l:



Disk /dev/sda: 320.1 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk identifier: 0x6f3aabf5



Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT

/dev/sda2          718848   204802047   102041600    7  HPFS/NTFS/exFAT

/dev/sda3       204804094   625141759   210168833    5  Extended

Partition 3 does not start on physical sector boundary.

/dev/sda5       204804096   625141759   210168832   83  Linux







=================== Recommended repair

Recommended-Repair

This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.

Additional repair will be performed: unhide-bootmenu-10s repair-filesystems





Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var



ntfsfix /dev/sda1

Mounting volume... The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

FAILED

Attempting to correct errors...

Processing $MFT and $MFTMirr...

Comparing $MFTMirr to $MFT... OK

Processing of $MFT and $MFTMirr completed successfully.

Setting required flags on partition... OK

Going to empty the journal ($LogFile)... OK

Checking the alternate boot sector... OK

NTFS volume version is 3.1.

NTFS partition /dev/sda1 was processed successfully.



ntfsfix /dev/sda2

Mounting volume... The disk contains an unclean file system (0, 0).

Metadata kept in Windows cache, refused to mount.

FAILED

Attempting to correct errors...

Processing $MFT and $MFTMirr...

Comparing $MFTMirr to $MFT... OK

Processing of $MFT and $MFTMirr completed successfully.

Setting required flags on partition...
 OK

Going to empty the journal ($LogFile)... OK

Checking the alternate boot sector... OK

NTFS volume version is 3.1.

NTFS partition /dev/sda2 was processed successfully.



fsck -fyM /dev/sda5

fsck from util-linux 2.20.1

e2fsck 1.42.5 (29-Jul-2012)

/dev/sda5 has unsupported feature(s): metadata_csum

e2fsck: Get a newer version of e2fsck!

mount: wrong fs type, bad option, bad superblock on /dev/sda5,

missing codepage or helper program, or other error

In some cases useful info is found in syslog - try

dmesg | tail  or so



mount /dev/sda5 -> Error code 32

Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda

dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

0+1 records in

0+1 records out



Boot successfully repaired.



You can now reboot your computer.





```

---

