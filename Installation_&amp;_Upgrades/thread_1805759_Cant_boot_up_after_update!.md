---
title: "Cant boot up after update!"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by sebasbas7 on 2011-07-16
Recently i came home from vacation to find that there was an update for my ubuntu system here's my specs:

-samsung 9 series laptop
-64 bit i5 intel
-64 bit ubuntu 11.04

so i ran the update and the update popped up with a message that basically told me it was going to update my grub and asked me which partitions/disks to update. so me being somewhat of a novice checked all the partitions (sda1/sda2) because it advised me that if i didnt know what my main boot partition was to just install grub on all of them. So i had somewhat of an idea which one it was but i figured it couldn't hurt to install it on all of them. i restarted my computer to find this message:

error:invalid arch independent ELF magic.
grub rescue> _

i searched the forums pretty thoroughly and couldn't find any topics which were similar to my circumstances but if there is any i would appreciate it if someone could give me a link to that topic.

any help is greatly appreciated and if anyone needs any more information just let me know thanks.

---

### Post by TeoBigusGeekus on 2011-07-16
[Looks promising.]("http://ubuntuforums.org/showthread.php?t=1299653")

---

### Post by sebasbas7 on 2011-07-18
Thank you very much for pointing out that link however i searched through that fourum topic and found a process called chroot or something like that but all the links in that topic such as this one ([http://www.ubuntu-inside.me/2009/06/...r-windows.html](http://www.ubuntu-inside.me/2009/06/...r-windows.html)) are broken most likely due to the topic being so old. additionally will using these methods still work since im using 11.04 and their using older ubuntu versions.

thanks

---

### Post by TeoBigusGeekus on 2011-07-19
Reinstall grub2 using [this]("https://help.ubuntu.com/community/Grub2#ChRoot") method.

---

### Post by sebasbas7 on 2011-07-19
thank you very much ill try that method and let you know what happens

---

### Post by sebasbas7 on 2011-07-23
So i ended up trying the chroot method you supplied me with and i followed all the steps as precisely as i could mounting all the necessary partitions including my separate boot partition or at least what i believe to be separate boot partition and i ended up with this problem heres from my terminal:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
done
root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
root@ubuntu:/# 
```

i figured something was wrong with my partitions and didn't know where to go from there...

thanks

---

### Post by sebasbas7 on 2011-07-23
oh and here is also a look at my setup in terms of partitions and disks:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16ef1a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15567   125034839+  ee  GPT

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001af03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     7825423    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```

---

### Post by srs5694 on 2011-07-23
Your /dev/sda uses GUID Partition Table (GPT) partitions, so the fdisk output you provided isn't very helpful. You should instead post the results of one or both of the following commands:

```

sudo parted /dev/sda print
sudo gdisk -l /dev/sda

```

The second command requires that you install the gdisk package, which isn't installed by default.

IIRC, the Samsung Series 9 uses UEFI firmware rather than the old-style BIOS, but your grub-install output indicates it was trying to install in BIOS mode. This might be OK if your system was booting in BIOS mode before (most UEFI implementations include a BIOS compatibility mode), but if your system used UEFI mode to boot before, this won't work. Unfortunately, Ubuntu has a tendency to "upgrade" the grub-efi (UEFI mode) package to grub-pc (BIOS mode), which is inappropriate and can screw up your system in the way you describe. It's possible this is what's happened to you; however, it's also possible that your system should be booting in BIOS mode and that other changes have rendered block lists unworkable, in which case you'll need to add a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) to the disk. The parted or gdisk output may provide clues about what's going on; however, it may also be necessary to examine your [EFI System Partition (ESP),](http://en.wikipedia.org/wiki/EFI_System_partition) if you've got one, to know how the system was originally installed.

---

### Post by sebasbas7 on 2011-07-23
thank you very much for the advice i tried making sense of what you said and i think i understand a little more of what went wrong. so i installed gdisk and ran both of the command and this is what i got:

```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): BC47997E-4EF7-4EE4-B65E-C43C9E821DFF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 1-sector boundaries
Total free space is 16 sectors (8.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34           39096   19.1 MiB    EF00  
   2           39097       241855503   115.3 GiB   0700  
   3       241855504       250069630   3.9 GiB     8200  
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA SAMSUNG MZMPA128 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  20.0MB  20.0MB  fat16                 boot
 2      20.0MB  124GB   124GB   ext4
 3      124GB   128GB   4206MB  linux-swap(v1)

ubuntu@ubuntu:~$ 
```

Hopefully that provides a little more info as to what my disks look like

thanks again

---

### Post by srs5694 on 2011-07-23
It's starting to look like you may have originally installed in UEFI mode, but I can't yet be positive of that. Please run the following commands and post their output:

```

sudo mount /dev/sda1 /mnt
find /mnt

```This will show me what files are on the ESP, which should provide further evidence about the installation mode. If there are any GRUB files on the ESP, you've got at least three options for how to proceed:


[LIST]
[*]Using appropriate apt-get or dpkg options from an emergency disc, uninstall grub-pc and install grub-efi.
[*]Install GRUB by manually compiling it, as described [here.]("https://help.ubuntu.com/community/UEFIBooting") You'll need another working installation (perhaps on another computer) to compile the software, though.
[*]Abandon GRUB and use another (U)EFI-capable Linux boot loader, such as [ELILO.]("http://elilo.sourceforge.net") This is my preferred solution, since I've had serious reliability problems with GRUB under UEFI; however, Ubuntu's installer has created a puny little 19.1 MiB ESP, which isn't big enough for ELILO, since it requires the Linux kernel and initial RAM disk to be installed on the ESP (or on another partition that the firmware can read).
[/LIST]


There is one other factor that the gdisk output has shown that is a long-term problem with your installation: Your partitions are not properly aligned for an SSD, which is what I believe the Samsung Series 9 uses for storage. (Please correct me if I'm wrong.) I don't know precisely what the Samsung MZMPA128 you've got requires for alignment, but most tools today align partitions on 1 MiB (2048-sector) boundaries, and your partitions are clearly not aligned in that way (none of the start sector values is divisible by [noparse]2048)[/noparse]. Thus, you'll probably experience degraded performance and perhaps reduced lifespan on your SSD unless you fix this problem.

I'm mentioning this now because it might be wise to resize your partitions to align them on 1 MiB boundaries (or whatever you learn is optimal for your disk), and when you do so, to shrink /dev/sda2 from the start so as to make room for a 200-300 MiB ESP (/dev/sda1). This will give you room on the ESP to use ELILO, if you decide to do so in the end. Be aware, though, that partition resizing is inherently risky. You should do this only after backing up all data on the affected partitions.

---

### Post by sebasbas7 on 2011-07-24
I ran the following commands and received this:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ find /mnt
/mnt
/mnt/EFI
/mnt/EFI/ubuntu
/mnt/EFI/ubuntu/grubx64.efi
/mnt/boot
/mnt/boot/grub
/mnt/boot/grub/915resolution.mod
/mnt/boot/grub/acpi.mod
/mnt/boot/grub/affs.mod
/mnt/boot/grub/afs.mod
/mnt/boot/grub/afs_be.mod
/mnt/boot/grub/aout.mod
/mnt/boot/grub/at_keyboard.mod
/mnt/boot/grub/ata.mod
/mnt/boot/grub/ata_pthru.mod
/mnt/boot/grub/befs.mod
/mnt/boot/grub/befs_be.mod
/mnt/boot/grub/biosdisk.mod
/mnt/boot/grub/bitmap.mod
/mnt/boot/grub/bitmap_scale.mod
/mnt/boot/grub/blocklist.mod
/mnt/boot/grub/boot.mod
/mnt/boot/grub/bsd.mod
/mnt/boot/grub/btrfs.mod
/mnt/boot/grub/bufio.mod
/mnt/boot/grub/cat.mod
/mnt/boot/grub/chain.mod
/mnt/boot/grub/cmostest.mod
/mnt/boot/grub/cmp.mod
/mnt/boot/grub/configfile.mod
/mnt/boot/grub/cpio.mod
/mnt/boot/grub/cpuid.mod
/mnt/boot/grub/crypto.mod
/mnt/boot/grub/cs5536.mod
/mnt/boot/grub/date.mod
/mnt/boot/grub/datehook.mod
/mnt/boot/grub/datetime.mod
/mnt/boot/grub/dm_nv.mod
/mnt/boot/grub/drivemap.mod
/mnt/boot/grub/echo.mod
/mnt/boot/grub/efiemu.mod
/mnt/boot/grub/elf.mod
/mnt/boot/grub/example_functional_test.mod
/mnt/boot/grub/ext2.mod
/mnt/boot/grub/extcmd.mod
/mnt/boot/grub/fat.mod
/mnt/boot/grub/font.mod
/mnt/boot/grub/fshelp.mod
/mnt/boot/grub/functional_test.mod
/mnt/boot/grub/gcry_arcfour.mod
/mnt/boot/grub/gcry_blowfish.mod
/mnt/boot/grub/gcry_camellia.mod
/mnt/boot/grub/gcry_cast5.mod
/mnt/boot/grub/gcry_crc.mod
/mnt/boot/grub/gcry_des.mod
/mnt/boot/grub/gcry_md4.mod
/mnt/boot/grub/gcry_md5.mod
/mnt/boot/grub/gcry_rfc2268.mod
/mnt/boot/grub/gcry_rijndael.mod
/mnt/boot/grub/gcry_rmd160.mod
/mnt/boot/grub/gcry_seed.mod
/mnt/boot/grub/gcry_serpent.mod
/mnt/boot/grub/gcry_sha1.mod
/mnt/boot/grub/gcry_sha256.mod
/mnt/boot/grub/gcry_sha512.mod
/mnt/boot/grub/gcry_tiger.mod
/mnt/boot/grub/gcry_twofish.mod
/mnt/boot/grub/gcry_whirlpool.mod
/mnt/boot/grub/gettext.mod
/mnt/boot/grub/gfxmenu.mod
/mnt/boot/grub/gfxterm.mod
/mnt/boot/grub/gptsync.mod
/mnt/boot/grub/gzio.mod
/mnt/boot/grub/halt.mod
/mnt/boot/grub/hashsum.mod
/mnt/boot/grub/hdparm.mod
/mnt/boot/grub/hello.mod
/mnt/boot/grub/help.mod
/mnt/boot/grub/hexdump.mod
/mnt/boot/grub/hfs.mod
/mnt/boot/grub/hfsplus.mod
/mnt/boot/grub/hwmatch.mod
/mnt/boot/grub/iorw.mod
/mnt/boot/grub/iso9660.mod
/mnt/boot/grub/jfs.mod
/mnt/boot/grub/jpeg.mod
/mnt/boot/grub/keylayouts.mod
/mnt/boot/grub/keystatus.mod
/mnt/boot/grub/legacycfg.mod
/mnt/boot/grub/linux.mod
/mnt/boot/grub/linux16.mod
/mnt/boot/grub/loadenv.mod
/mnt/boot/grub/loopback.mod
/mnt/boot/grub/ls.mod
/mnt/boot/grub/lsacpi.mod
/mnt/boot/grub/lsapm.mod
/mnt/boot/grub/lsmmap.mod
/mnt/boot/grub/lspci.mod
/mnt/boot/grub/lvm.mod
/mnt/boot/grub/mdraid09.mod
/mnt/boot/grub/mdraid1x.mod
/mnt/boot/grub/memdisk.mod
/mnt/boot/grub/memrw.mod
/mnt/boot/grub/minicmd.mod
/mnt/boot/grub/minix.mod
/mnt/boot/grub/minix2.mod
/mnt/boot/grub/mmap.mod
/mnt/boot/grub/msdospart.mod
/mnt/boot/grub/multiboot.mod
/mnt/boot/grub/multiboot2.mod
/mnt/boot/grub/nilfs2.mod
/mnt/boot/grub/normal.mod
/mnt/boot/grub/ntfs.mod
/mnt/boot/grub/ntfscomp.mod
/mnt/boot/grub/ntldr.mod
/mnt/boot/grub/ohci.mod
/mnt/boot/grub/part_acorn.mod
/mnt/boot/grub/part_amiga.mod
/mnt/boot/grub/part_apple.mod
/mnt/boot/grub/part_bsd.mod
/mnt/boot/grub/part_gpt.mod
/mnt/boot/grub/part_msdos.mod
/mnt/boot/grub/part_sun.mod
/mnt/boot/grub/part_sunpc.mod
/mnt/boot/grub/parttool.mod
/mnt/boot/grub/password.mod
/mnt/boot/grub/password_pbkdf2.mod
/mnt/boot/grub/pbkdf2.mod
/mnt/boot/grub/pci.mod
/mnt/boot/grub/play.mod
/mnt/boot/grub/png.mod
/mnt/boot/grub/probe.mod
/mnt/boot/grub/pxe.mod
/mnt/boot/grub/pxecmd.mod
/mnt/boot/grub/raid.mod
/mnt/boot/grub/raid5rec.mod
/mnt/boot/grub/raid6rec.mod
/mnt/boot/grub/read.mod
/mnt/boot/grub/reboot.mod
/mnt/boot/grub/regexp.mod
/mnt/boot/grub/reiserfs.mod
/mnt/boot/grub/relocator.mod
/mnt/boot/grub/scsi.mod
/mnt/boot/grub/search.mod
/mnt/boot/grub/search_fs_file.mod
/mnt/boot/grub/search_fs_uuid.mod
/mnt/boot/grub/search_label.mod
/mnt/boot/grub/sendkey.mod
/mnt/boot/grub/serial.mod
/mnt/boot/grub/setjmp.mod
/mnt/boot/grub/setpci.mod
/mnt/boot/grub/sfs.mod
/mnt/boot/grub/sleep.mod
/mnt/boot/grub/squash4.mod
/mnt/boot/grub/tar.mod
/mnt/boot/grub/terminal.mod
/mnt/boot/grub/terminfo.mod
/mnt/boot/grub/test.mod
/mnt/boot/grub/test_blockarg.mod
/mnt/boot/grub/testload.mod
/mnt/boot/grub/tga.mod
/mnt/boot/grub/trig.mod
/mnt/boot/grub/true.mod
/mnt/boot/grub/udf.mod
/mnt/boot/grub/ufs1.mod
/mnt/boot/grub/ufs2.mod
/mnt/boot/grub/uhci.mod
/mnt/boot/grub/usb.mod
/mnt/boot/grub/usb_keyboard.mod
/mnt/boot/grub/usbms.mod
/mnt/boot/grub/usbserial_common.mod
/mnt/boot/grub/usbserial_ftdi.mod
/mnt/boot/grub/usbserial_pl2303.mod
/mnt/boot/grub/usbtest.mod
/mnt/boot/grub/vbe.mod
/mnt/boot/grub/vga.mod
/mnt/boot/grub/vga_text.mod
/mnt/boot/grub/video.mod
/mnt/boot/grub/video_bochs.mod
/mnt/boot/grub/video_cirrus.mod
/mnt/boot/grub/video_fb.mod
/mnt/boot/grub/videoinfo.mod
/mnt/boot/grub/videotest.mod
/mnt/boot/grub/xfs.mod
/mnt/boot/grub/xnu.mod
/mnt/boot/grub/xnu_uuid.mod
/mnt/boot/grub/xzio.mod
/mnt/boot/grub/zfs.mod
/mnt/boot/grub/zfsinfo.mod
/mnt/boot/grub/command.lst
/mnt/boot/grub/crypto.lst
/mnt/boot/grub/fs.lst
/mnt/boot/grub/moddep.lst
/mnt/boot/grub/partmap.lst
/mnt/boot/grub/parttool.lst
/mnt/boot/grub/terminal.lst
/mnt/boot/grub/video.lst
/mnt/boot/grub/boot.img
/mnt/boot/grub/cdboot.img
/mnt/boot/grub/diskboot.img
/mnt/boot/grub/g2hdr.img
/mnt/boot/grub/grldr.img
/mnt/boot/grub/kernel.img
/mnt/boot/grub/lnxboot.img
/mnt/boot/grub/pxeboot.img
/mnt/boot/grub/efiemu32.o
/mnt/boot/grub/efiemu64.o
/mnt/boot/grub/locale
/mnt/boot/grub/locale/en_AU.mo
/mnt/boot/grub/locale/en_CA.mo
/mnt/boot/grub/locale/en_GB.mo
/mnt/boot/grub/locale/es.mo
/mnt/boot/grub/locale/pt.mo
/mnt/boot/grub/locale/pt_BR.mo
/mnt/boot/grub/locale/zh_CN.mo
/mnt/boot/grub/core.img
/mnt/boot/grub/grubenv
/mnt/grub
/mnt/grub/915resolution.mod
/mnt/grub/acpi.mod
/mnt/grub/affs.mod
/mnt/grub/afs.mod
/mnt/grub/afs_be.mod
/mnt/grub/aout.mod
/mnt/grub/at_keyboard.mod
/mnt/grub/ata.mod
/mnt/grub/ata_pthru.mod
/mnt/grub/befs.mod
/mnt/grub/befs_be.mod
/mnt/grub/biosdisk.mod
/mnt/grub/bitmap.mod
/mnt/grub/bitmap_scale.mod
/mnt/grub/blocklist.mod
/mnt/grub/boot.mod
/mnt/grub/bsd.mod
/mnt/grub/btrfs.mod
/mnt/grub/bufio.mod
/mnt/grub/cat.mod
/mnt/grub/chain.mod
/mnt/grub/cmostest.mod
/mnt/grub/cmp.mod
/mnt/grub/configfile.mod
/mnt/grub/cpio.mod
/mnt/grub/cpuid.mod
/mnt/grub/crypto.mod
/mnt/grub/cs5536.mod
/mnt/grub/date.mod
/mnt/grub/datehook.mod
/mnt/grub/datetime.mod
/mnt/grub/dm_nv.mod
/mnt/grub/drivemap.mod
/mnt/grub/echo.mod
/mnt/grub/efiemu.mod
/mnt/grub/elf.mod
/mnt/grub/example_functional_test.mod
/mnt/grub/ext2.mod
/mnt/grub/extcmd.mod
/mnt/grub/fat.mod
/mnt/grub/font.mod
/mnt/grub/fshelp.mod
/mnt/grub/functional_test.mod
/mnt/grub/gcry_arcfour.mod
/mnt/grub/gcry_blowfish.mod
/mnt/grub/gcry_camellia.mod
/mnt/grub/gcry_cast5.mod
/mnt/grub/gcry_crc.mod
/mnt/grub/gcry_des.mod
/mnt/grub/gcry_md4.mod
/mnt/grub/gcry_md5.mod
/mnt/grub/gcry_rfc2268.mod
/mnt/grub/gcry_rijndael.mod
/mnt/grub/gcry_rmd160.mod
/mnt/grub/gcry_seed.mod
/mnt/grub/gcry_serpent.mod
/mnt/grub/gcry_sha1.mod
/mnt/grub/gcry_sha256.mod
/mnt/grub/gcry_sha512.mod
/mnt/grub/gcry_tiger.mod
/mnt/grub/gcry_twofish.mod
/mnt/grub/gcry_whirlpool.mod
/mnt/grub/gettext.mod
/mnt/grub/gfxmenu.mod
/mnt/grub/gfxterm.mod
/mnt/grub/gptsync.mod
/mnt/grub/gzio.mod
/mnt/grub/halt.mod
/mnt/grub/hashsum.mod
/mnt/grub/hdparm.mod
/mnt/grub/hello.mod
/mnt/grub/help.mod
/mnt/grub/hexdump.mod
/mnt/grub/hfs.mod
/mnt/grub/hfsplus.mod
/mnt/grub/hwmatch.mod
/mnt/grub/iorw.mod
/mnt/grub/iso9660.mod
/mnt/grub/jfs.mod
/mnt/grub/jpeg.mod
/mnt/grub/keylayouts.mod
/mnt/grub/keystatus.mod
/mnt/grub/legacycfg.mod
/mnt/grub/linux.mod
/mnt/grub/linux16.mod
/mnt/grub/loadenv.mod
/mnt/grub/loopback.mod
/mnt/grub/ls.mod
/mnt/grub/lsacpi.mod
/mnt/grub/lsapm.mod
/mnt/grub/lsmmap.mod
/mnt/grub/lspci.mod
/mnt/grub/lvm.mod
/mnt/grub/mdraid09.mod
/mnt/grub/mdraid1x.mod
/mnt/grub/memdisk.mod
/mnt/grub/memrw.mod
/mnt/grub/minicmd.mod
/mnt/grub/minix.mod
/mnt/grub/minix2.mod
/mnt/grub/mmap.mod
/mnt/grub/msdospart.mod
/mnt/grub/multiboot.mod
/mnt/grub/multiboot2.mod
/mnt/grub/nilfs2.mod
/mnt/grub/normal.mod
/mnt/grub/ntfs.mod
/mnt/grub/ntfscomp.mod
/mnt/grub/ntldr.mod
/mnt/grub/ohci.mod
/mnt/grub/part_acorn.mod
/mnt/grub/part_amiga.mod
/mnt/grub/part_apple.mod
/mnt/grub/part_bsd.mod
/mnt/grub/part_gpt.mod
/mnt/grub/part_msdos.mod
/mnt/grub/part_sun.mod
/mnt/grub/part_sunpc.mod
/mnt/grub/parttool.mod
/mnt/grub/password.mod
/mnt/grub/password_pbkdf2.mod
/mnt/grub/pbkdf2.mod
/mnt/grub/pci.mod
/mnt/grub/play.mod
/mnt/grub/png.mod
/mnt/grub/probe.mod
/mnt/grub/pxe.mod
/mnt/grub/pxecmd.mod
/mnt/grub/raid.mod
/mnt/grub/raid5rec.mod
/mnt/grub/raid6rec.mod
/mnt/grub/read.mod
/mnt/grub/reboot.mod
/mnt/grub/regexp.mod
/mnt/grub/reiserfs.mod
/mnt/grub/relocator.mod
/mnt/grub/scsi.mod
/mnt/grub/search.mod
/mnt/grub/search_fs_file.mod
/mnt/grub/search_fs_uuid.mod
/mnt/grub/search_label.mod
/mnt/grub/sendkey.mod
/mnt/grub/serial.mod
/mnt/grub/setjmp.mod
/mnt/grub/setpci.mod
/mnt/grub/sfs.mod
/mnt/grub/sleep.mod
/mnt/grub/squash4.mod
/mnt/grub/tar.mod
/mnt/grub/terminal.mod
/mnt/grub/terminfo.mod
/mnt/grub/test.mod
/mnt/grub/test_blockarg.mod
/mnt/grub/testload.mod
/mnt/grub/tga.mod
/mnt/grub/trig.mod
/mnt/grub/true.mod
/mnt/grub/udf.mod
/mnt/grub/ufs1.mod
/mnt/grub/ufs2.mod
/mnt/grub/uhci.mod
/mnt/grub/usb.mod
/mnt/grub/usb_keyboard.mod
/mnt/grub/usbms.mod
/mnt/grub/usbserial_common.mod
/mnt/grub/usbserial_ftdi.mod
/mnt/grub/usbserial_pl2303.mod
/mnt/grub/usbtest.mod
/mnt/grub/vbe.mod
/mnt/grub/vga.mod
/mnt/grub/vga_text.mod
/mnt/grub/video.mod
/mnt/grub/video_bochs.mod
/mnt/grub/video_cirrus.mod
/mnt/grub/video_fb.mod
/mnt/grub/videoinfo.mod
/mnt/grub/videotest.mod
/mnt/grub/xfs.mod
/mnt/grub/xnu.mod
/mnt/grub/xnu_uuid.mod
/mnt/grub/xzio.mod
/mnt/grub/zfs.mod
/mnt/grub/zfsinfo.mod
/mnt/grub/command.lst
/mnt/grub/crypto.lst
/mnt/grub/fs.lst
/mnt/grub/moddep.lst
/mnt/grub/partmap.lst
/mnt/grub/parttool.lst
/mnt/grub/terminal.lst
/mnt/grub/video.lst
/mnt/grub/boot.img
/mnt/grub/cdboot.img
/mnt/grub/diskboot.img
/mnt/grub/g2hdr.img
/mnt/grub/grldr.img
/mnt/grub/kernel.img
/mnt/grub/lnxboot.img
/mnt/grub/pxeboot.img
/mnt/grub/efiemu32.o
/mnt/grub/efiemu64.o
/mnt/grub/locale
/mnt/grub/locale/en_AU.mo
/mnt/grub/locale/en_CA.mo
/mnt/grub/locale/en_GB.mo
/mnt/grub/locale/es.mo
/mnt/grub/locale/pt.mo
/mnt/grub/locale/pt_BR.mo
/mnt/grub/locale/zh_CN.mo
/mnt/grub/load.cfg
/mnt/grub/grubenv
/mnt/grub/core.img
/mnt/grub/grub.cfg
/mnt/clean
/mnt/clean/sda2
ubuntu@ubuntu:~$ 
```

im thinking of using the third option you told me about just because it seems like the option that would solve any future problems. hopefully what i have set up will allow that. the good thing is that this is a fairly new computer that i bought, so with it being new it has no valuable information to me so theres no need to worry about losing anything.

also thank you very much for letting me know about my partition sizes and the extent of the future problems they could cause to my hard drive. i consider myself an intermediate computer user, being able to do a lot more than the common user however my knowledge on computers is more general and i lack the knowledge of the deeper more advanced tasks such as resizing boundaries. so if you wouldn't mind explaining a little more on how to do this it would really help.  im guessing i could use gparted partition editor to just move things around? and also how would i find what kind of boundaries would be optimal for my type of disk?

---

### Post by srs5694 on 2011-07-24
You've definitely got an EFI GRUB installation on your ESP, so your GRUB almost certainly installed that way initially. It may have broken because of the "upgrade" from grub-efi to grub-pc; or maybe you just need to locate a boot option in your firmware to re-enable the (U)EFI boot feature (it could be that it's trying to boot in BIOS mode by running the MBR code and that's running into problems).

One other thing I notice is that most (but not all) of your GRUB files are duplicated in the ESP: You've got both boot/grub and grub directories in the ESP with module (.mod) files. Only the grub directory contains the critical grub.cfg file. Both placements seem a bit odd to me, though; on my systems, I've got an EFI/grub directory in the ESP for these files. OTOH, I may have modified my configurations to use a locally-built GRUB, so perhaps one or even both of the directories you've got is normal.

As to resizing partitions, what you'd need to do is to go into GParted using an emergency disk and resize your partitions, being sure the "Align to" item is set to "MiB". When you resize the partition, this will align it on 1 MiB (2048-sector) boundaries. Note that you may need to shrink both ends by a small amount; GParted sometimes tries to *grow* an end you don't tell it to adjust in order to match an alignment you specify, resulting in an error about being unable to satisfy all constraints or about overlapping partitions being illegal. Of course, to resize /dev/sda1 to be 200 MiB or more, you'll need to move the start of /dev/sda2 by about 200 MiB. Once you're done with this, you can use gdisk or GParted's Partition->Information dialog box to verify that the partitions all start on sector values that are multiples of 2048.

An alignment of 1 MiB will probably be fine, but if you want to know precisely what your hardware requires, you'll have to dig up the technical specs on your model -- a Samsung MZMPA128, according to the parted output you posted earlier. Aligning to anything but a 1 MiB boundary could be tricky. Higher values would be easier than lower values, at least when using GParted. If your disk requires a lower value (say, 512 KiB), then aligning to 1 MiB would do no harm, so don't worry about it.

To use ELILO, you'll need to do the following:


[list=1]
[*]Create a directory on the ESP for it, as a subdirectory of the EFI directory (e.g., EFI/elilo, or /mnt/EFI/elilo if you mount the ESP at /mnt to do this).
[*]Copy the elilo.efi file from a 64-bit ELILO binary to that directory.
[*]Copy your Linux kernel (/boot/vmlinuz*) to the ELILO directory.
[*]Copy your Linux initial RAM disk (/boot/initrd*) to the ELILO directory.
[*]Create an elilo.conf file for ELILO in its directory on the ESP (see below).
[*]Add ELILO to your firmware's boot options. The details depend on your firmware, but there should be an option somewhere to either boot from a file or to add a boot option. If you can boot the system using ELILO in UEFI mode but the method is awkward, using the Linux efibootmgr command may be helpful in reconfiguring the boot order; post back if you have this problem.
[/list]


The elilo.conf file is pretty simple, compared to a GRUB configuration file. Here's an example:

```
prompt
timeout=50
default=linux
#chooser=textmenu

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda2
        append=""

```

You may need to change the kernel, initial RAM disk, and root device filenames. You can also add kernel options on the "append" line. The blank set shown here boots without the graphics you're probably accustomed to seeing, but with useful diagnostic information. Try copying options from your grub.cfg file if you want to get the boot graphics working.

---

### Post by labrazil on 2011-07-24
Hello,

I recently experienced the same thing. I got a notice to upgrade my system and got the exact same message. The best part of this thread is that I'm also on a samsung series 9 (128G) and following each command, I got the same results. Unfortunately, I had to reinstall ubuntu and this resulted in loosing all my settings and data (good news is that I use dropbox/chrome) so I really didn't lose anything but my time :(.

Anyhow, I decided to give the reinstall one last option and then when I was presented the option to 'partial upgrade' I didn't select the two check boxes when it asked to configure the grub-pc.  And when I restarted my machine, it went right in to my login.  I guess this worked...??

Now, I will try to fix the resizing partion.

---

### Post by labrazil on 2011-07-25
I hope I did the partition correctly.

```
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B13D1128-B024-4B14-BF3A-B3DDE961E9AE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2-sector boundaries
Total free space is 1056 sectors (528.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          450559   220.0 MiB   EF00  
   2          450560       241854463   115.1 GiB   0700  
   3       241855504       250069630   3.9 GiB     8200 
```

My start sector (450560) is now divisible by 2048.

I was trying to setup Elilo as you recommended, but I'm stuck at this step.
> Add ELILO to your firmware's boot options. The details depend on your firmware, but there should be an option somewhere to either boot from a file or to add a boot option. If you can boot the system using ELILO in UEFI mode but the method is awkward, using the Linux efibootmgr command may be helpful in reconfiguring the boot order; post back if you have this problem.


How do I edit my firmware boot option. Like the previous user I'm a bit of a novice when it comes to this. Any help guidance would be much appreciated.

---

### Post by srs5694 on 2011-07-25
> **labrazil said:**
> I hope I did the partition correctly.

```
Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B13D1128-B024-4B14-BF3A-B3DDE961E9AE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2-sector boundaries
Total free space is 1056 sectors (528.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          450559   220.0 MiB   EF00  
   2          450560       241854463   115.1 GiB   0700  
   3       241855504       250069630   3.9 GiB     8200 
```My start sector (450560) is now divisible by 2048.

Yes, but your swap partition (/dev/sda3) isn't, so swap performance may suffer. I don't know by how much, though. For that matter, I'm not sure that putting swap on an SSD is a great idea; it might put undue wear on the SSD, which has a limited number of writes before it dies.

I wouldn't worry too much about the ESP (starting on sector 34), since it's written so seldom. Still, adjusting it to start on sector 2048 rather than 34 might be worth doing if and when it becomes convenient.

> I was trying to setup Elilo as you recommended, but I'm stuck at this step.

[quote]Add ELILO to your firmware's boot options. The details depend on your  firmware, but there should be an option somewhere to either boot from a  file or to add a boot option. If you can boot the system using ELILO in  UEFI mode but the method is awkward, using the Linux efibootmgr command  may be helpful in reconfiguring the boot order; post back if you have  this problem. 			 		

How do I edit my firmware boot option. Like the previous user I'm a bit of a novice when it comes to this. Any help guidance would be much appreciated.[/QUOTE]

Unfortunately, I'm going to have to refer you to your motherboard's or computer's documentation on this one, since the way you change firmware boot settings varies a lot from one firmware implementation to another.

---

### Post by labrazil on 2011-07-25
> **srs5694 said:**
> Yes, but your swap partition (/dev/sda3) isn't, so swap performance may suffer. I don't know by how much, though. For that matter, I'm not sure that putting swap on an SSD is a great idea; it might put undue wear on the SSD, which has a limited number of writes before it dies.


Thanks!!

From what you are suggesting, my only option would be to remove this partition? And what would happen if I removed the sda3 partition and moved the 3gigs of space to sda2. Is this linux-swap essential for Ubuntu? Could Ubuntu function without it? My machine contains 4gig of RAM, not sure if an additional 4gig is worth sacrificing the lifespan of my SSD.

One last question, should I re-install Ubuntu after making these partition changes?

---

### Post by srs5694 on 2011-07-25
Linux does not require swap space, but it's a useful "safety net" in case you run a lot of big programs. It's also used in "suspend-to-disk" operations.

I'm not an expert on SSDs, so you may want to do some more research on the issue of SSDs and swap space before doing anything about it.

If you do decide to remove the swap partition, you should edit it out of /etc/fstab, but there's no need to re-install just because you rearrange or remove swap space.

---

### Post by rob@doryweather.org on 2011-07-26
Had a problem which smells pretty much the same as this... 
 
my setup:
clean install of natty with uefi on a system with an asrock P67 mb with UEFI.. 
 
here is the description of the problem and the fix that worked for me
 
[https://lists.ubuntu.com/archives/foundations-bugs/2011-July/011835.html](https://lists.ubuntu.com/archives/foundations-bugs/2011-July/011835.html)
 
used dpkg after everything was normal to put a hold on future updates of grub-uefi... no sense 'fixing' what isn't broken.
 
Robert

---

### Post by sebasbas7 on 2011-07-27
i decided to just perform a clean install of the whole system id just like to know how to prevent this type of thing in the future? its unfortunate that ubuntu encountered this problem its a real pain to deal with.

and as for the re sizing partitions i checked what they looked like in gparted and the align to box was already set to Mib. does this mean they were already aligned correctly? because the starting sector in the info box said 32 however that isn't a multiple of 2048. this left me a little confused and i don't really know if what i did was right. 

thanks again for the speedy response and sorry for the delay in reply's works kept me very busy lately and haven't had much free time.

---

### Post by srs5694 on 2011-07-27
To prevent this in the future, do one of two things:


[list]
[*]Watch the updates offered by apt, Synaptic, or whatever tool you use with an eagle eye and reject any update that involves grub, particularly if the software says it's going to replace grub-efi with grub-pc.
[*]Install and maintain GRUB or ELILO from *outside* the usual Ubuntu package management system so that Ubuntu's update policies can't mess it up. Personally, this is the way I'd go -- in fact, it's the way I *have* gone on two installations. Note that you can install both Ubuntu's GRUB and another boot loader (GRUB or ELILO) side-by-side, so you can try this route with little or no risk to your current installation, then either keep them both or uninstall Ubuntu's GRUB package, as you see fit.
[/list]


As to the partition alignment issue, the only way to be sure is to check the alignment with a tool that shows partition start or end points with sector precision, such as parted with "unit s" or gdisk. Check the partition start values and see if they're divisible by 2048 (or whatever value you're using as a target). GParted can produce this information, too, but you've got to select each partition in turn, select Partition->Information, and examine the "First sector" field in the resulting dialog box.

---

### Post by sebasbas7 on 2011-08-05
Sorry for the late response but how would i go about this process if i chose to just install elilo where it cant be harmed?

thanks

---

### Post by srs5694 on 2011-08-05
It's impossible to install *anything* "where it can't be harmed."

If you want to install ELILO, please see post #12 to this thread.

---

### Post by sebasbas7 on 2011-08-06
Oh sorry about that i just phrased it wrong i mean how would you go about installing elilo with this step you mentioned?:

>  Install and maintain GRUB or ELILO from outside the usual Ubuntu package management system so that Ubuntu's update policies can't mess it up. Personally, this is the way I'd go -- in fact, it's the way I have gone on two installations. Note that you can install both Ubuntu's GRUB and another boot loader (GRUB or ELILO) side-by-side, so you can try this route with little or no risk to your current installation, then either keep them both or uninstall Ubuntu's GRUB package, as you see fit.

---

### Post by srs5694 on 2011-08-06
> **sebasbas7 said:**
> Oh sorry about that i just phrased it wrong i mean how would you go about installing elilo with this step you mentioned?:

Again, please see my post #12. I cover it in detail there, at least for ELILO. For GRUB, see [this page.](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by sebasbas7 on 2011-08-11
oh okay thank you very much sorry about that. i just have one more question. since i wiped my computer and did a clean install i didnt lose anything important however it would be a pain installing each and every program i had one by one again. fortunately my desktop also runs ubuntu and pretty much every program i had is on there so if there would be a way were i could back up my desktop programs and transfer them to my laptop that would be great. would you know of any program like that by chance? thank you

---

### Post by progone on 2011-08-30
Any suggestions to fixing a boot that even fails with live CD (both Ubuntu and mint live CDs fails) . However windows vista duao boot running good. 

I just changed the ram too same issue. I looked at grub when we select which dis to to use and pressed 'e' I thought my Linux was ext4 and not ext2. I have a bad feeling I've been hacked.

---

