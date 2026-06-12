---
title: "Boot fails LVM encryption"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by elektronaut on 2013-03-09
I'm having serious trouble with my 8.04 server installation. The beginning of the story is described [in this thread.]("http://ubuntuforums.org/showthread.php?t=2120477") As described there, there is only Ubuntu installed, no Windows, so no need for an UEFI based install. I don't know how grub was installed initially, if in the classic or the UEFI way. But I suspect now that it was in the classic way as there is no UEFI partition listed in /etc/fstab. Anyway, the problem is that boot sometimes works, but most often not. If it doesn't work (the HDD just clicks a couple of times and then stops spinning), I also can't enter the BIOS/UEFI settings, because the keyboard is obviously not recognized. Switching from a USB keyboard to a PS/2 version didn't help here. (Using PS/2 did help in the boot process where I have to enter the LUKS passphrase, but that is another story.) So I'm sitting in front of the ASRock welcome screen, can't enter the BIOS. Only thing that works now is clearing CMOS. Afterwards the keyboard works again. Strange, this happens again and again. I have the impression that the OS somehow influences UEFI settings so that the keyboard is not recognized anymore. I already flashed the UEFI to a new version and have run Boot-Repair from Linux Secure Remix a couple of times from a USB stick which was booted as a UEFI device. One thing that I also did, which might not have been such a good idea, was to install "grub-efi-amd64", as I thought I might need this. This might have complicated things further. I'm out of knowledge on this subject and am frightened to make things worse, so please give me some solid advice. OK, here some data: [Output of Boot Info Script on the first run]("http://paste.ubuntu.com/5568131/") (before installing grub-efi-amd64), [actual output]("http://paste.ubuntu.com/5597366/"), installed grub packages: 
```
me@server:~$ dpkg --get-selections > ~/installed_packages
me@server:~$ grep grub installed_packages
grub-common					install
grub-efi					install
grub-efi-amd64					install
grub-efi-amd64-bin				install
grub2-common					install
```
Contents of /boot:
```

me@server:~$ sudo ls -laR /boot/
/boot/:
total 31394
drwxr-xr-x  4 root root    1024 Mar  8 21:29 .
drwxr-xr-x 24 root root    4096 Feb 28 01:56 ..
-rw-r--r--  1 root root  791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r--  1 root root  792830 Feb 19 13:58 abi-3.2.0-38-generic
-rw-r--r--  1 root root  140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r--  1 root root  140488 Feb 19 13:58 config-3.2.0-38-generic
drwxr-xr-x  5 root root    7168 Feb 28 01:56 grub
-rw-r--r--  1 root root 8817030 Feb 27 23:35 initrd.img-3.2.0-29-generic
-rw-------  1 root root 5735733 Mar  8 21:29 initrd.img-3.2.0-38-generic
drwx------  2 root root   12288 Feb 26 15:20 lost+found
-rw-------  1 root root 2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw-------  1 root root 2887333 Feb 19 13:58 System.map-3.2.0-38-generic
-rw-------  1 root root 4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw-------  1 root root 4968592 Feb 19 13:58 vmlinuz-3.2.0-38-generic

/boot/grub:
total 266
drwxr-xr-x 5 root root   7168 Feb 28 01:56 .
drwxr-xr-x 4 root root   1024 Mar  8 21:29 ..
-rw-r--r-- 1 root root 123904 Feb 26 16:02 core.efi
drwxr-xr-x 2 root root   1024 Feb 28 00:31 fonts
-r--r--r-- 1 root root   4389 Feb 28 01:56 grub.cfg
-rw-r--r-- 1 root root 123904 Feb 26 16:02 grub.efi
-rw-r--r-- 1 root root   1024 Mar  9 00:09 grubenv
drwxr-xr-x 2 root root   7168 Feb 26 20:41 i386-pc
-rw-r--r-- 1 root root     82 Feb 26 16:02 load.cfg
drwxr-xr-x 2 root root   1024 Feb 26 19:50 locale

/boot/grub/fonts:
total 2509
drwxr-xr-x 2 root root    1024 Feb 28 00:31 .
drwxr-xr-x 5 root root    7168 Feb 28 01:56 ..
-rw-r--r-- 1 root root 2560080 Feb 28 00:25 unicode.pf2

/boot/grub/i386-pc:
total 1759
drwxr-xr-x 2 root root   7168 Feb 26 20:41 .
drwxr-xr-x 5 root root   7168 Feb 28 01:56 ..
-rw-r--r-- 1 root root   7268 Feb 26 20:41 915resolution.mod
-rw-r--r-- 1 root root  10152 Feb 26 20:41 acpi.mod
-rw-r--r-- 1 root root   1292 Feb 26 20:41 adler32.mod
-rw-r--r-- 1 root root   5632 Feb 26 20:41 affs.mod
-rw-r--r-- 1 root root   6876 Feb 26 20:41 afs.mod
-rw-r--r-- 1 root root   8692 Feb 26 20:41 ahci.mod
-rw-r--r-- 1 root root    705 Feb 26 20:41 all_video.mod
-rw-r--r-- 1 root root   1060 Feb 26 20:41 aout.mod
-rw-r--r-- 1 root root   5428 Feb 26 20:41 ata.mod
-rw-r--r-- 1 root root   4052 Feb 26 20:41 at_keyboard.mod
-rw-r--r-- 1 root root   1632 Feb 26 20:41 backtrace.mod
-rw-r--r-- 1 root root   7644 Feb 26 20:41 bfs.mod
-rw-r--r-- 1 root root   4676 Feb 26 20:41 biosdisk.mod
-rw-r--r-- 1 root root   2392 Feb 26 20:41 bitmap.mod
-rw-r--r-- 1 root root   3012 Feb 26 20:41 bitmap_scale.mod
-rw-r--r-- 1 root root   2036 Feb 26 20:41 blocklist.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 boot.img
-rw-r--r-- 1 root root   2448 Feb 26 20:41 boot.mod
-rw-r--r-- 1 root root  29524 Feb 26 20:41 bsd.mod
-rw-r--r-- 1 root root  14192 Feb 26 20:41 btrfs.mod
-rw-r--r-- 1 root root   2164 Feb 26 20:41 bufio.mod
-rw-r--r-- 1 root root   2232 Feb 26 20:41 cat.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 cdboot.img
-rw-r--r-- 1 root root   3500 Feb 26 20:41 chain.mod
-rw-r--r-- 1 root root   1536 Feb 26 20:41 cmostest.mod
-rw-r--r-- 1 root root   1988 Feb 26 20:41 cmp.mod
-rw-r--r-- 1 root root   3251 Feb 26 20:41 command.lst
-rw-r--r-- 1 root root   2208 Feb 26 20:41 configfile.mod
-rw-r--r-- 1 root root  26425 Feb 26 20:41 core.img
-rw-r--r-- 1 root root   4488 Feb 26 20:41 cpio_be.mod
-rw-r--r-- 1 root root   4380 Feb 26 20:41 cpio.mod
-rw-r--r-- 1 root root   1548 Feb 26 20:41 cpuid.mod
-rw-r--r-- 1 root root   1784 Feb 26 20:41 crc64.mod
-rw-r--r-- 1 root root   8688 Feb 26 20:41 cryptodisk.mod
-rw-r--r-- 1 root root    855 Feb 26 20:41 crypto.lst
-rw-r--r-- 1 root root   4376 Feb 26 20:41 crypto.mod
-rw-r--r-- 1 root root   3716 Feb 26 20:41 cs5536.mod
-rw-r--r-- 1 root root   1800 Feb 26 20:41 datehook.mod
-rw-r--r-- 1 root root   2176 Feb 26 20:41 date.mod
-rw-r--r-- 1 root root   1281 Feb 26 20:41 datetime.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 diskboot.img
-rw-r--r-- 1 root root   9696 Feb 26 20:41 diskfilter.mod
-rw-r--r-- 1 root root   1872 Feb 26 20:41 dm_nv.mod
-rw-r--r-- 1 root root   5380 Feb 26 20:41 drivemap.mod
-rw-r--r-- 1 root root   1964 Feb 26 20:41 echo.mod
-rw-r--r-- 1 root root   7432 Feb 26 20:41 efiemu32.o
-rw-r--r-- 1 root root  11137 Feb 26 20:41 efiemu64.o
-rw-r--r-- 1 root root  23960 Feb 26 20:41 efiemu.mod
-rw-r--r-- 1 root root  15624 Feb 26 20:41 ehci.mod
-rw-r--r-- 1 root root   4404 Feb 26 20:41 elf.mod
-rw-r--r-- 1 root root   5312 Feb 26 20:41 exfat.mod
-rw-r--r-- 1 root root   1468 Feb 26 20:41 exfctest.mod
-rw-r--r-- 1 root root   5784 Feb 26 20:41 ext2.mod
-rw-r--r-- 1 root root   4488 Feb 26 20:41 extcmd.mod
-rw-r--r-- 1 root root   5656 Feb 26 20:41 fat.mod
-rw-r--r-- 1 root root  12272 Feb 26 20:41 font.mod
-rw-r--r-- 1 root root   2208 Feb 26 20:41 freedos.mod
-rw-r--r-- 1 root root   2900 Feb 26 20:41 fshelp.mod
-rw-r--r-- 1 root root    194 Feb 26 20:41 fs.lst
-rw-r--r-- 1 root root   2764 Feb 26 20:41 functional_test.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 g2hdr.img
-rw-r--r-- 1 root root   1632 Feb 26 20:41 gcry_arcfour.mod
-rw-r--r-- 1 root root   8120 Feb 26 20:41 gcry_blowfish.mod
-rw-r--r-- 1 root root  34508 Feb 26 20:41 gcry_camellia.mod
-rw-r--r-- 1 root root  17224 Feb 26 20:41 gcry_cast5.mod
-rw-r--r-- 1 root root   2936 Feb 26 20:41 gcry_crc.mod
-rw-r--r-- 1 root root  19284 Feb 26 20:41 gcry_des.mod
-rw-r--r-- 1 root root   3124 Feb 26 20:41 gcry_md4.mod
-rw-r--r-- 1 root root   3808 Feb 26 20:41 gcry_md5.mod
-rw-r--r-- 1 root root   2448 Feb 26 20:41 gcry_rfc2268.mod
-rw-r--r-- 1 root root  19068 Feb 26 20:41 gcry_rijndael.mod
-rw-r--r-- 1 root root   8480 Feb 26 20:41 gcry_rmd160.mod
-rw-r--r-- 1 root root  16560 Feb 26 20:41 gcry_seed.mod
-rw-r--r-- 1 root root  16828 Feb 26 20:41 gcry_serpent.mod
-rw-r--r-- 1 root root   8672 Feb 26 20:41 gcry_sha1.mod
-rw-r--r-- 1 root root   3496 Feb 26 20:41 gcry_sha256.mod
-rw-r--r-- 1 root root   5700 Feb 26 20:41 gcry_sha512.mod
-rw-r--r-- 1 root root  11732 Feb 26 20:41 gcry_tiger.mod
-rw-r--r-- 1 root root  39520 Feb 26 20:41 gcry_twofish.mod
-rw-r--r-- 1 root root  24512 Feb 26 20:41 gcry_whirlpool.mod
-rw-r--r-- 1 root root  25716 Feb 26 20:41 gdb.mod
-rw-r--r-- 1 root root   5984 Feb 26 20:41 geli.mod
-rw-r--r-- 1 root root   4740 Feb 26 20:41 gettext.mod
-rw-r--r-- 1 root root  33108 Feb 26 20:41 gfxmenu.mod
-rw-r--r-- 1 root root  11728 Feb 26 20:41 gfxterm.mod
-rw-r--r-- 1 root root   3644 Feb 26 20:41 gptsync.mod
-rw-r--r-- 1 root root  10240 Feb 26 20:41 grldr.img
-rw-r--r-- 1 root root   8016 Feb 26 20:41 gzio.mod
-rw-r--r-- 1 root root   4064 Feb 26 20:41 halt.mod
-rw-r--r-- 1 root root   5076 Feb 26 20:41 hashsum.mod
-rw-r--r-- 1 root root   7176 Feb 26 20:41 hdparm.mod
-rw-r--r-- 1 root root   1204 Feb 26 20:41 hello.mod
-rw-r--r-- 1 root root   2548 Feb 26 20:41 help.mod
-rw-r--r-- 1 root root   3144 Feb 26 20:41 hexdump.mod
-rw-r--r-- 1 root root   7200 Feb 26 20:41 hfs.mod
-rw-r--r-- 1 root root   6596 Feb 26 20:41 hfsplus.mod
-rw-r--r-- 1 root root   5664 Feb 26 20:41 http.mod
-rw-r--r-- 1 root root  47780 Feb 26 20:41 hwmatch.mod
-rw-r--r-- 1 root root   2820 Feb 26 20:41 iorw.mod
-rw-r--r-- 1 root root   8724 Feb 26 20:41 iso9660.mod
-rw-r--r-- 1 root root   6552 Feb 26 20:41 jfs.mod
-rw-r--r-- 1 root root   6000 Feb 26 20:41 jpeg.mod
-rw-r--r-- 1 root root  28820 Feb 26 20:41 kernel.img
-rw-r--r-- 1 root root   4456 Feb 26 20:41 keylayouts.mod
-rw-r--r-- 1 root root   1944 Feb 26 20:41 keystatus.mod
-rw-r--r-- 1 root root   6796 Feb 26 20:41 ldm.mod
-rw-r--r-- 1 root root  28208 Feb 26 20:41 legacycfg.mod
-rw-r--r-- 1 root root   5948 Feb 26 20:41 linux16.mod
-rw-r--r-- 1 root root  11332 Feb 26 20:41 linux.mod
-rw-r--r-- 1 root root   1024 Feb 26 20:41 lnxboot.img
-rw-r--r-- 1 root root   5556 Feb 26 20:41 loadenv.mod
-rw-r--r-- 1 root root   2852 Feb 26 20:41 loopback.mod
-rw-r--r-- 1 root root   3608 Feb 26 20:41 lsacpi.mod
-rw-r--r-- 1 root root   2280 Feb 26 20:41 lsapm.mod
-rw-r--r-- 1 root root   1796 Feb 26 20:41 lsmmap.mod
-rw-r--r-- 1 root root   4344 Feb 26 20:41 ls.mod
-rw-r--r-- 1 root root   4816 Feb 26 20:41 lspci.mod
-rw-r--r-- 1 root root   6576 Feb 26 20:41 luks.mod
-rw-r--r-- 1 root root   6296 Feb 26 20:41 lvm.mod
-rw-r--r-- 1 root root   2816 Feb 26 20:41 lzma_decompress.img
-rw-r--r-- 1 root root   8676 Feb 26 20:41 lzopio.mod
-rw-r--r-- 1 root root   2008 Feb 26 20:41 mdraid09_be.mod
-rw-r--r-- 1 root root   1972 Feb 26 20:41 mdraid09.mod
-rw-r--r-- 1 root root   1968 Feb 26 20:41 mdraid1x.mod
-rw-r--r-- 1 root root   2004 Feb 26 20:41 memdisk.mod
-rw-r--r-- 1 root root   2840 Feb 26 20:41 memrw.mod
-rw-r--r-- 1 root root   3416 Feb 26 20:41 minicmd.mod
-rw-r--r-- 1 root root   3992 Feb 26 20:41 minix2_be.mod
-rw-r--r-- 1 root root   3872 Feb 26 20:41 minix2.mod
-rw-r--r-- 1 root root   3912 Feb 26 20:41 minix3_be.mod
-rw-r--r-- 1 root root   3848 Feb 26 20:41 minix3.mod
-rw-r--r-- 1 root root   3908 Feb 26 20:41 minix_be.mod
-rw-r--r-- 1 root root   3820 Feb 26 20:41 minix.mod
-rw-r--r-- 1 root root   9040 Feb 26 20:41 mmap.mod
-rw-r--r-- 1 root root   3973 Feb 26 20:41 moddep.lst
-rw-r--r-- 1 root root   2412 Feb 26 20:41 msdospart.mod
-rw-r--r-- 1 root root  12704 Feb 26 20:41 multiboot2.mod
-rw-r--r-- 1 root root  12196 Feb 26 20:41 multiboot.mod
-rw-r--r-- 1 root root  43860 Feb 26 20:41 net.mod
-rw-r--r-- 1 root root   4668 Feb 26 20:41 newc.mod
-rw-r--r-- 1 root root   6600 Feb 26 20:41 nilfs2.mod
-rw-r--r-- 1 root root 110404 Feb 26 20:41 normal.mod
-rw-r--r-- 1 root root   3416 Feb 26 20:41 ntfscomp.mod
-rw-r--r-- 1 root root  10276 Feb 26 20:41 ntfs.mod
-rw-r--r-- 1 root root   2552 Feb 26 20:41 ntldr.mod
-rw-r--r-- 1 root root   4468 Feb 26 20:41 odc.mod
-rw-r--r-- 1 root root  10372 Feb 26 20:41 ohci.mod
-rw-r--r-- 1 root root   1608 Feb 26 20:41 part_acorn.mod
-rw-r--r-- 1 root root   1752 Feb 26 20:41 part_amiga.mod
-rw-r--r-- 1 root root   2024 Feb 26 20:41 part_apple.mod
-rw-r--r-- 1 root root   2676 Feb 26 20:41 part_bsd.mod
-rw-r--r-- 1 root root   1428 Feb 26 20:41 part_dvh.mod
-rw-r--r-- 1 root root   2344 Feb 26 20:41 part_gpt.mod
-rw-r--r-- 1 root root    101 Feb 26 20:41 partmap.lst
-rw-r--r-- 1 root root   2260 Feb 26 20:41 part_msdos.mod
-rw-r--r-- 1 root root   1848 Feb 26 20:41 part_plan.mod
-rw-r--r-- 1 root root   1480 Feb 26 20:41 part_sun.mod
-rw-r--r-- 1 root root   1604 Feb 26 20:41 part_sunpc.mod
-rw-r--r-- 1 root root     17 Feb 26 20:41 parttool.lst
-rw-r--r-- 1 root root   4548 Feb 26 20:41 parttool.mod
-rw-r--r-- 1 root root   1896 Feb 26 20:41 password.mod
-rw-r--r-- 1 root root   2788 Feb 26 20:41 password_pbkdf2.mod
-rw-r--r-- 1 root root   4660 Feb 26 20:41 pata.mod
-rw-r--r-- 1 root root   1356 Feb 26 20:41 pbkdf2.mod
-rw-r--r-- 1 root root   1424 Feb 26 20:41 pci.mod
-rw-r--r-- 1 root root   6420 Feb 26 20:41 plan9.mod
-rw-r--r-- 1 root root   2432 Feb 26 20:41 play.mod
-rw-r--r-- 1 root root   6448 Feb 26 20:41 png.mod
-rw-r--r-- 1 root root   1548 Feb 26 20:41 priority_queue.mod
-rw-r--r-- 1 root root   2576 Feb 26 20:41 probe.mod
-rw-r--r-- 1 root root   1024 Feb 26 20:41 pxeboot.img
-rw-r--r-- 1 root root   2688 Feb 26 20:41 pxechain.mod
-rw-r--r-- 1 root root   3800 Feb 26 20:41 pxe.mod
-rw-r--r-- 1 root root   1372 Feb 26 20:41 raid5rec.mod
-rw-r--r-- 1 root root   2160 Feb 26 20:41 raid6rec.mod
-rw-r--r-- 1 root root   1492 Feb 26 20:41 read.mod
-rw-r--r-- 1 root root   1716 Feb 26 20:41 reboot.mod
-rw-r--r-- 1 root root  51684 Feb 26 20:41 regexp.mod
-rw-r--r-- 1 root root   9104 Feb 26 20:41 reiserfs.mod
-rw-r--r-- 1 root root  15104 Feb 26 20:41 relocator.mod
-rw-r--r-- 1 root root   4132 Feb 26 20:41 romfs.mod
-rw-r--r-- 1 root root   5120 Feb 26 20:41 scsi.mod
-rw-r--r-- 1 root root   3264 Feb 26 20:41 search_fs_file.mod
-rw-r--r-- 1 root root   3260 Feb 26 20:41 search_fs_uuid.mod
-rw-r--r-- 1 root root   3184 Feb 26 20:41 search_label.mod
-rw-r--r-- 1 root root   3636 Feb 26 20:41 search.mod
-rw-r--r-- 1 root root   7104 Feb 26 20:41 sendkey.mod
-rw-r--r-- 1 root root   7076 Feb 26 20:41 serial.mod
-rw-r--r-- 1 root root    706 Feb 26 20:41 setjmp.mod
-rw-r--r-- 1 root root   5360 Feb 26 20:41 setpci.mod
-rw-r--r-- 1 root root   5092 Feb 26 20:41 sfs.mod
-rw-r--r-- 1 root root   2224 Feb 26 20:41 sleep.mod
-rw-r--r-- 1 root root   7100 Feb 26 20:41 squash4.mod
-rw-r--r-- 1 root root   5208 Feb 26 20:41 tar.mod
-rw-r--r-- 1 root root    132 Feb 26 20:41 terminal.lst
-rw-r--r-- 1 root root   4152 Feb 26 20:41 terminal.mod
-rw-r--r-- 1 root root  11108 Feb 26 20:41 terminfo.mod
-rw-r--r-- 1 root root   1340 Feb 26 20:41 test_blockarg.mod
-rw-r--r-- 1 root root   2696 Feb 26 20:41 testload.mod
-rw-r--r-- 1 root root   4952 Feb 26 20:41 test.mod
-rw-r--r-- 1 root root   5160 Feb 26 20:41 tftp.mod
-rw-r--r-- 1 root root   2772 Feb 26 20:41 tga.mod
-rw-r--r-- 1 root root   1508 Feb 26 20:41 time.mod
-rw-r--r-- 1 root root   1691 Feb 26 20:41 trig.mod
-rw-r--r-- 1 root root   1204 Feb 26 20:41 true.mod
-rw-r--r-- 1 root root   7700 Feb 26 20:41 udf.mod
-rw-r--r-- 1 root root   5488 Feb 26 20:41 ufs1.mod
-rw-r--r-- 1 root root   5540 Feb 26 20:41 ufs2.mod
-rw-r--r-- 1 root root   6468 Feb 26 20:41 uhci.mod
-rw-r--r-- 1 root root   4032 Feb 26 20:41 usb_keyboard.mod
-rw-r--r-- 1 root root   9740 Feb 26 20:41 usb.mod
-rw-r--r-- 1 root root   7284 Feb 26 20:41 usbms.mod
-rw-r--r-- 1 root root   1988 Feb 26 20:41 usbserial_common.mod
-rw-r--r-- 1 root root   2340 Feb 26 20:41 usbserial_ftdi.mod
-rw-r--r-- 1 root root   2696 Feb 26 20:41 usbserial_pl2303.mod
-rw-r--r-- 1 root root   3604 Feb 26 20:41 usbtest.mod
-rw-r--r-- 1 root root   9540 Feb 26 20:41 vbe.mod
-rw-r--r-- 1 root root   4568 Feb 26 20:41 vga.mod
-rw-r--r-- 1 root root   2132 Feb 26 20:41 vga_text.mod
-rw-r--r-- 1 root root   5364 Feb 26 20:41 video_bochs.mod
-rw-r--r-- 1 root root   5688 Feb 26 20:41 video_cirrus.mod
-rw-r--r-- 1 root root  20016 Feb 26 20:41 video_fb.mod
-rw-r--r-- 1 root root   4032 Feb 26 20:41 videoinfo.mod
-rw-r--r-- 1 root root     33 Feb 26 20:41 video.lst
-rw-r--r-- 1 root root  10360 Feb 26 20:41 video.mod
-rw-r--r-- 1 root root   4168 Feb 26 20:41 videotest.mod
-rw-r--r-- 1 root root   6108 Feb 26 20:41 xfs.mod
-rw-r--r-- 1 root root  33168 Feb 26 20:41 xnu.mod
-rw-r--r-- 1 root root   2012 Feb 26 20:41 xnu_uuid.mod
-rw-r--r-- 1 root root  15200 Feb 26 20:41 xzio.mod
-rw-r--r-- 1 root root   5544 Feb 26 20:41 zfscrypt.mod
-rw-r--r-- 1 root root   6396 Feb 26 20:41 zfsinfo.mod
-rw-r--r-- 1 root root  36552 Feb 26 20:41 zfs.mod

/boot/grub/locale:
total 113
drwxr-xr-x 2 root root  1024 Feb 26 19:50 .
drwxr-xr-x 5 root root  7168 Feb 28 01:56 ..
-rw-r--r-- 1 root root   866 Feb 26 20:41 en_AU.mo
-rw-r--r-- 1 root root   466 Feb 26 20:41 en_CA.mo
-rw-r--r-- 1 root root  3531 Feb 26 20:41 en_GB.mo
-rw-r--r-- 1 root root 68774 Feb 26 20:41 es.mo
-rw-r--r-- 1 root root 30842 Feb 26 20:41 zh_CN.mo

/boot/lost+found:
total 13
drwx------ 2 root root 12288 Feb 26 15:20 .
drwxr-xr-x 4 root root  1024 Mar  8 21:29 ..

```

Please tell me if you need more information and thank you all for your help!

---

### Post by oldfred on 2013-03-09
Older computers do not have UEFI, just BIOS. Only Ubuntu with 11.04 or later would boot with UEFI. So you do not have UEFI.

But you do have LVM and encryption which makes it difficult. I think you may have to mount the encrypted LVM before running BootInfo or Boot-Repair for it to see the / (root) inside the encryption.

---

### Post by elektronaut on 2013-03-11
This is not an old computer, it just has a PS/2 port additionally. It's an ASRock E350M1 with an AMD Fusion chip and I have Ubuntu 12.04 installed. (Already tried to change the thread prefix, but there is no option in "thread tools"). So the root partition must definitely be mounted? I thought having /boot would suffice.

---

### Post by oldfred on 2013-03-11
Changed title.

While system boots from a /boot partition to reinstall grub it needs to see fstab and grub configuration files in / (root).

---

### Post by elektronaut on 2013-03-11
OK, so just to be sure now about the steps as I'm a little frightened to further destroy my system:

[list=1]
[*]Boot Linux Secure Remix
[*]Mount encrypted LVM
[*]Run Boot-Repair
[/list]
Is that correct? Anything else? Should I deinstall grub-efi-amd64 first? At the moment I can still do that as the system is running right now.

---

### Post by oldfred on 2013-03-11
You can run Boot-Repair from your install if it is running. 
Or you can manually uninstall grub-efi and install grub-pc.

---

### Post by elektronaut on 2013-03-11
Thanks for helping me out oldfred, appreciating it :)
I removed grub-efi and am confronted now with the question whether I want to install grub-pc to /dev/sda (1000204 MB; SAMSUNG_HD103SJ) or /dev/sda1 (499 MB; /boot). Which one should I choose?

---

### Post by elektronaut on 2013-03-11
OK, I now installed grub-pc to /dev/sda, I guess that should be right. Should I uninstall efibootmgr? 
Here is the output of boot-info-script. I'm frightened trying to reboot without your inspection :oops:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-root': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-usr': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-var': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-tmp': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-home': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-swap': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       976,895       974,848  83 Linux
/dev/sda2    *        976,896 1,953,523,711 1,952,546,816  83 Linux


Drive: sdb _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       976,895       974,848  83 Linux
/dev/sdb2    *        976,896 1,953,523,711 1,952,546,816  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/sda2_crypt xeVilN-lEBw-sTMF-e6Kt-DxYG-qByW-Kz8Qr5 LVM2_member 
/dev/mapper/vg01-home 7d7a7c88-799c-42af-add6-f221e5db5e9a   ext4       
/dev/mapper/vg01-root 740ff707-6cb2-4424-9ccf-955866171404   ext4       
/dev/mapper/vg01-swap a412acb0-bfae-4768-9129-21bc5479c53c   swap       
/dev/mapper/vg01-tmp ad8c13f5-3bed-4434-b3c9-3f357db9f743   ext4       
/dev/mapper/vg01-usr 0b595bbc-4de1-4705-bd27-19b741e80998   ext4       
/dev/mapper/vg01-var fc822b3e-d393-4f65-bb65-cd5278e30140   ext4       
/dev/sda1        ea3b7965-277e-4d9e-9a08-5a271f967422   ext4       
/dev/sda2        f7b214f1-6371-4465-abfa-3c3cb0f3c6a0   crypto_LUKS 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sda2_crypt
vg01-home
vg01-root
vg01-swap
vg01-tmp
vg01-usr
vg01-var

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg01-home /home                    ext4       (rw,usrquota,grpquota,acl,user_xattr)
/dev/mapper/vg01-root /                        ext4       (rw,errors=remount-ro,acl,user_xattr)
/dev/mapper/vg01-tmp /tmp                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-usr /usr                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-var /var                     ext4       (rw,acl,user_xattr)
/dev/sda1        /boot                    ext4       (rw,acl,user_xattr)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-38-generic ...'
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-38-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.010554314 = 0.011332608    grub/core.img                                  1
   0.263193130 = 0.282601472    grub/grub.cfg                                  1
   0.038486481 = 0.041324544    initrd.img-3.2.0-29-generic                    2
   0.053195000 = 0.057117696    initrd.img-3.2.0-38-generic                    1
   0.019269943 = 0.020690944    vmlinuz-3.2.0-29-generic                       1
   0.046621323 = 0.050059264    vmlinuz-3.2.0-38-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb


Unknown BootLoader on sda2

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 20  |............... |
00000070  84 9b 32 71 cc a9 09 ae  93 c8 de e5 b4 fa 58 e5  |..2q..........X.|
00000080  38 96 16 af 98 79 32 ea  00 5e e2 2f bd 31 f8 14  |8....y2..^./.1..|
00000090  39 21 3f bd e0 a8 bd 3c  34 cb 4f 79 d4 62 9d 5e  |9!?....<4.Oy.b.^|
000000a0  9d 3a 36 12 00 00 3d 09  66 37 62 32 31 34 66 31  |.:6...=.f7b214f1|
000000b0  2d 36 33 37 31 2d 34 34  36 35 2d 61 62 66 61 2d  |-6371-4465-abfa-|
000000c0  33 63 33 63 62 30 66 33  63 36 61 30 00 00 00 00  |3c3cb0f3c6a0....|
000000d0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 08 00 00 0f a0  |................|
00000100  00 ac 71 f3 00 01 0a e7  34 42 0a 01 ae 82 99 d0  |..q.....4B......|
00000110  95 37 31 12 e6 ac 0d de  95 b0 45 6a 6f 48 24 ec  |.71.......EjoH$.|
00000120  1e 2d ad 96 85 92 78 1b  00 00 01 08 00 00 0f a0  |.-....x.........|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on vg01-root'


Unknown BootLoader on vg01-usr'


Unknown BootLoader on vg01-var'


Unknown BootLoader on vg01-tmp'


Unknown BootLoader on vg01-home'


Unknown BootLoader on vg01-swap'



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb: No such file or directory
hexdump: /dev/sdb: No such file or directory
hexdump: /dev/sdb: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-root': No such file or directory
hexdump: /dev/mapper/vg01-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-usr': No such file or directory
hexdump: /dev/mapper/vg01-usr': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-var': No such file or directory
hexdump: /dev/mapper/vg01-var': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-tmp': No such file or directory
hexdump: /dev/mapper/vg01-tmp': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-home': No such file or directory
hexdump: /dev/mapper/vg01-home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-swap': No such file or directory
hexdump: /dev/mapper/vg01-swap': No such file or directory

```

And here is the content of /boot. I reckon there are still some remains from the efi installation. Should I delete those files?
```

me@server:~$ ls -laR /boot/
/boot/:
total 31395
drwxr-xr-x  4 root root    1024 Mar  8 21:29 .
drwxr-xr-x 26 root root    4096 Mar 10 18:18 ..
-rw-r--r--  1 root root  791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r--  1 root root  792830 Feb 19 13:58 abi-3.2.0-38-generic
-rw-r--r--  1 root root  140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r--  1 root root  140488 Feb 19 13:58 config-3.2.0-38-generic
drwxr-xr-x  5 root root    8192 Mar 11 22:33 grub
-rw-r--r--  1 root root 8817030 Feb 27 23:35 initrd.img-3.2.0-29-generic
-rw-------  1 root root 5735733 Mar  8 21:29 initrd.img-3.2.0-38-generic
drwx------  2 root root   12288 Feb 26 15:20 lost+found
-rw-------  1 root root 2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw-------  1 root root 2887333 Feb 19 13:58 System.map-3.2.0-38-generic
-rw-------  1 root root 4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw-------  1 root root 4968592 Feb 19 13:58 vmlinuz-3.2.0-38-generic

/boot/grub:
total 4270
drwxr-xr-x 5 root root    8192 Mar 11 22:33 .
drwxr-xr-x 4 root root    1024 Mar  8 21:29 ..
-rw-r--r-- 1 root root    7368 Mar 11 22:33 915resolution.mod
-rw-r--r-- 1 root root   10420 Mar 11 22:33 acpi.mod
-rw-r--r-- 1 root root    1848 Mar 11 22:33 adler32.mod
-rw-r--r-- 1 root root    4644 Mar 11 22:33 affs.mod
-rw-r--r-- 1 root root    5092 Mar 11 22:33 afs_be.mod
-rw-r--r-- 1 root root    4928 Mar 11 22:33 afs.mod
-rw-r--r-- 1 root root    1132 Mar 11 22:33 aout.mod
-rw-r--r-- 1 root root    8184 Mar 11 22:33 ata.mod
-rw-r--r-- 1 root root    2276 Mar 11 22:33 ata_pthru.mod
-rw-r--r-- 1 root root    4236 Mar 11 22:33 at_keyboard.mod
-rw-r--r-- 1 root root    5004 Mar 11 22:33 befs_be.mod
-rw-r--r-- 1 root root    4832 Mar 11 22:33 befs.mod
-rw-r--r-- 1 root root    4780 Mar 11 22:33 biosdisk.mod
-rw-r--r-- 1 root root    2560 Mar 11 22:33 bitmap.mod
-rw-r--r-- 1 root root    3084 Mar 11 22:33 bitmap_scale.mod
-rw-r--r-- 1 root root    2192 Mar 11 22:33 blocklist.mod
-rw-r--r-- 1 root root     512 Mar 11 22:33 boot.img
-rw-r--r-- 1 root root    2636 Mar 11 22:33 boot.mod
-rw-r--r-- 1 root root   27992 Mar 11 22:33 bsd.mod
-rw-r--r-- 1 root root   13588 Mar 11 22:33 btrfs.mod
-rw-r--r-- 1 root root    2032 Mar 11 22:33 bufio.mod
-rw-r--r-- 1 root root    2428 Mar 11 22:33 cat.mod
-rw-r--r-- 1 root root     512 Mar 11 22:33 cdboot.img
-rw-r--r-- 1 root root    2652 Mar 11 22:33 chain.mod
-rw-r--r-- 1 root root    1720 Mar 11 22:33 cmostest.mod
-rw-r--r-- 1 root root    2136 Mar 11 22:33 cmp.mod
-rw-r--r-- 1 root root    2830 Mar 11 22:33 command.lst
-rw-r--r-- 1 root root    2368 Mar 11 22:33 configfile.mod
-rw-r--r-- 1 root root  123904 Feb 26 16:02 core.efi
-rw-r--r-- 1 root root   26050 Mar 11 22:33 core.img
-rw-r--r-- 1 root root    2940 Mar 11 22:33 cpio.mod
-rw-r--r-- 1 root root    1684 Mar 11 22:33 cpuid.mod
-rw-r--r-- 1 root root     842 Mar 11 22:33 crypto.lst
-rw-r--r-- 1 root root    4464 Mar 11 22:33 crypto.mod
-rw-r--r-- 1 root root    4212 Mar 11 22:33 cs5536.mod
-rw-r--r-- 1 root root    1952 Mar 11 22:33 datehook.mod
-rw-r--r-- 1 root root    2336 Mar 11 22:33 date.mod
-rw-r--r-- 1 root root    1353 Mar 11 22:33 datetime.mod
-rw-r--r-- 1 root root     512 Mar 11 22:33 diskboot.img
-rw-r--r-- 1 root root    1968 Mar 11 22:33 dm_nv.mod
-rw-r--r-- 1 root root    5576 Mar 11 22:33 drivemap.mod
-rw-r--r-- 1 root root    2108 Mar 11 22:33 echo.mod
-rw-r--r-- 1 root root    7408 Mar 11 22:33 efiemu32.o
-rw-r--r-- 1 root root   11089 Mar 11 22:33 efiemu64.o
-rw-r--r-- 1 root root   24580 Mar 11 22:33 efiemu.mod
-rw-r--r-- 1 root root    4632 Mar 11 22:33 elf.mod
-rw-r--r-- 1 root root    1700 Mar 11 22:33 example_functional_test.mod
-rw-r--r-- 1 root root    5912 Mar 11 22:33 ext2.mod
-rw-r--r-- 1 root root    4572 Mar 11 22:33 extcmd.mod
-rw-r--r-- 1 root root    6112 Mar 11 22:33 fat.mod
-rw-r--r-- 1 root root   11976 Mar 11 22:33 font.mod
drwxr-xr-x 2 root root    1024 Feb 28 00:31 fonts
-rw-r--r-- 1 root root    2892 Mar 11 22:33 fshelp.mod
-rw-r--r-- 1 root root     149 Mar 11 22:33 fs.lst
-rw-r--r-- 1 root root    2556 Mar 11 22:33 functional_test.mod
-rw-r--r-- 1 root root     512 Mar 11 22:33 g2hdr.img
-rw-r--r-- 1 root root    1824 Mar 11 22:33 gcry_arcfour.mod
-rw-r--r-- 1 root root    8308 Mar 11 22:33 gcry_blowfish.mod
-rw-r--r-- 1 root root   34668 Mar 11 22:33 gcry_camellia.mod
-rw-r--r-- 1 root root   17412 Mar 11 22:33 gcry_cast5.mod
-rw-r--r-- 1 root root    3088 Mar 11 22:33 gcry_crc.mod
-rw-r--r-- 1 root root   19440 Mar 11 22:33 gcry_des.mod
-rw-r--r-- 1 root root    3304 Mar 11 22:33 gcry_md4.mod
-rw-r--r-- 1 root root    3988 Mar 11 22:33 gcry_md5.mod
-rw-r--r-- 1 root root    2632 Mar 11 22:33 gcry_rfc2268.mod
-rw-r--r-- 1 root root   19236 Mar 11 22:33 gcry_rijndael.mod
-rw-r--r-- 1 root root    8752 Mar 11 22:33 gcry_rmd160.mod
-rw-r--r-- 1 root root   16740 Mar 11 22:33 gcry_seed.mod
-rw-r--r-- 1 root root   18092 Mar 11 22:33 gcry_serpent.mod
-rw-r--r-- 1 root root    8856 Mar 11 22:33 gcry_sha1.mod
-rw-r--r-- 1 root root    3660 Mar 11 22:33 gcry_sha256.mod
-rw-r--r-- 1 root root    5868 Mar 11 22:33 gcry_sha512.mod
-rw-r--r-- 1 root root   11916 Mar 11 22:33 gcry_tiger.mod
-rw-r--r-- 1 root root   39688 Mar 11 22:33 gcry_twofish.mod
-rw-r--r-- 1 root root   24712 Mar 11 22:33 gcry_whirlpool.mod
-rw-r--r-- 1 root root    4012 Mar 11 22:33 gettext.mod
-rw-r--r-- 1 root root     699 Mar 11 22:33 gfxblacklist.txt
-rw-r--r-- 1 root root   32992 Mar 11 22:33 gfxmenu.mod
-rw-r--r-- 1 root root   11984 Mar 11 22:33 gfxterm.mod
-rw-r--r-- 1 root root    3780 Mar 11 22:33 gptsync.mod
-rw-r--r-- 1 root root   10240 Mar 11 22:33 grldr.img
-r--r--r-- 1 root root    4865 Mar 11 22:33 grub.cfg
-rw-r--r-- 1 root root  123904 Feb 26 16:02 grub.efi
-rw-r--r-- 1 root root    1024 Mar  9 00:09 grubenv
-rw-r--r-- 1 root root    8704 Mar 11 22:33 gzio.mod
-rw-r--r-- 1 root root    4076 Mar 11 22:33 halt.mod
-rw-r--r-- 1 root root    5136 Mar 11 22:33 hashsum.mod
-rw-r--r-- 1 root root    7404 Mar 11 22:33 hdparm.mod
-rw-r--r-- 1 root root    1292 Mar 11 22:33 hello.mod
-rw-r--r-- 1 root root    2548 Mar 11 22:33 help.mod
-rw-r--r-- 1 root root    3296 Mar 11 22:33 hexdump.mod
-rw-r--r-- 1 root root    6136 Mar 11 22:33 hfs.mod
-rw-r--r-- 1 root root    6024 Mar 11 22:33 hfsplus.mod
-rw-r--r-- 1 root root   38972 Mar 11 22:33 hwmatch.mod
drwxr-xr-x 2 root root    7168 Feb 26 20:41 i386-pc
-rw-r--r-- 1 root root    2928 Mar 11 22:33 iorw.mod
-rw-r--r-- 1 root root    6344 Mar 11 22:33 iso9660.mod
-rw-r--r-- 1 root root    6212 Mar 11 22:33 jfs.mod
-rw-r--r-- 1 root root    5908 Mar 11 22:33 jpeg.mod
-rw-r--r-- 1 root root   30168 Mar 11 22:33 kernel.img
-rw-r--r-- 1 root root    4588 Mar 11 22:33 keylayouts.mod
-rw-r--r-- 1 root root    2104 Mar 11 22:33 keystatus.mod
-rw-r--r-- 1 root root   27668 Mar 11 22:33 legacycfg.mod
-rw-r--r-- 1 root root    5768 Mar 11 22:33 linux16.mod
-rw-r--r-- 1 root root   10164 Mar 11 22:33 linux.mod
-rw-r--r-- 1 root root    1024 Mar 11 22:33 lnxboot.img
-rw-r--r-- 1 root root    5756 Mar 11 22:33 loadenv.mod
drwxr-xr-x 2 root root    1024 Feb 26 19:50 locale
-rw-r--r-- 1 root root    2988 Mar 11 22:33 loopback.mod
-rw-r--r-- 1 root root    3716 Mar 11 22:33 lsacpi.mod
-rw-r--r-- 1 root root    2308 Mar 11 22:33 lsapm.mod
-rw-r--r-- 1 root root    1804 Mar 11 22:33 lsmmap.mod
-rw-r--r-- 1 root root    4436 Mar 11 22:33 ls.mod
-rw-r--r-- 1 root root    4968 Mar 11 22:33 lspci.mod
-rw-r--r-- 1 root root    7216 Mar 11 22:33 lvm.mod
-rw-r--r-- 1 root root    9084 Mar 11 22:33 lzopio.mod
-rw-r--r-- 1 root root    1976 Mar 11 22:33 mdraid09.mod
-rw-r--r-- 1 root root    2380 Mar 11 22:33 mdraid1x.mod
-rw-r--r-- 1 root root    2144 Mar 11 22:33 memdisk.mod
-rw-r--r-- 1 root root    2948 Mar 11 22:33 memrw.mod
-rw-r--r-- 1 root root    3528 Mar 11 22:33 minicmd.mod
-rw-r--r-- 1 root root    3880 Mar 11 22:33 minix2.mod
-rw-r--r-- 1 root root    3880 Mar 11 22:33 minix.mod
-rw-r--r-- 1 root root    9300 Mar 11 22:33 mmap.mod
-rw-r--r-- 1 root root    3292 Mar 11 22:33 moddep.lst
-rw-r--r-- 1 root root    2492 Mar 11 22:33 msdospart.mod
-rw-r--r-- 1 root root   12984 Mar 11 22:33 multiboot2.mod
-rw-r--r-- 1 root root   12292 Mar 11 22:33 multiboot.mod
-rw-r--r-- 1 root root    6716 Mar 11 22:33 nilfs2.mod
-rw-r--r-- 1 root root  106448 Mar 11 22:33 normal.mod
-rw-r--r-- 1 root root    3540 Mar 11 22:33 ntfscomp.mod
-rw-r--r-- 1 root root    9612 Mar 11 22:33 ntfs.mod
-rw-r--r-- 1 root root    2636 Mar 11 22:33 ntldr.mod
-rw-r--r-- 1 root root   10432 Mar 11 22:33 ohci.mod
-rw-r--r-- 1 root root    1772 Mar 11 22:33 part_acorn.mod
-rw-r--r-- 1 root root    1856 Mar 11 22:33 part_amiga.mod
-rw-r--r-- 1 root root    2192 Mar 11 22:33 part_apple.mod
-rw-r--r-- 1 root root    2860 Mar 11 22:33 part_bsd.mod
-rw-r--r-- 1 root root    2452 Mar 11 22:33 part_gpt.mod
-rw-r--r-- 1 root root      82 Mar 11 22:33 partmap.lst
-rw-r--r-- 1 root root    2388 Mar 11 22:33 part_msdos.mod
-rw-r--r-- 1 root root    1644 Mar 11 22:33 part_sun.mod
-rw-r--r-- 1 root root    1776 Mar 11 22:33 part_sunpc.mod
-rw-r--r-- 1 root root      17 Mar 11 22:33 parttool.lst
-rw-r--r-- 1 root root    4568 Mar 11 22:33 parttool.mod
-rw-r--r-- 1 root root    2052 Mar 11 22:33 password.mod
-rw-r--r-- 1 root root    2940 Mar 11 22:33 password_pbkdf2.mod
-rw-r--r-- 1 root root    1416 Mar 11 22:33 pbkdf2.mod
-rw-r--r-- 1 root root    1272 Mar 11 22:33 pci.mod
-rw-r--r-- 1 root root    2568 Mar 11 22:33 play.mod
-rw-r--r-- 1 root root    6620 Mar 11 22:33 png.mod
-rw-r--r-- 1 root root    2740 Mar 11 22:33 probe.mod
-rw-r--r-- 1 root root    1024 Mar 11 22:33 pxeboot.img
-rw-r--r-- 1 root root    1408 Mar 11 22:33 pxecmd.mod
-rw-r--r-- 1 root root    6160 Mar 11 22:33 pxe.mod
-rw-r--r-- 1 root root    1472 Mar 11 22:33 raid5rec.mod
-rw-r--r-- 1 root root    2876 Mar 11 22:33 raid6rec.mod
-rw-r--r-- 1 root root    6536 Mar 11 22:33 raid.mod
-rw-r--r-- 1 root root    1640 Mar 11 22:33 read.mod
-rw-r--r-- 1 root root    1200 Mar 11 22:33 reboot.mod
-rw-r--r-- 1 root root   41940 Mar 11 22:33 regexp.mod
-rw-r--r-- 1 root root    9544 Mar 11 22:33 reiserfs.mod
-rw-r--r-- 1 root root   14644 Mar 11 22:33 relocator.mod
-rw-r--r-- 1 root root    4028 Mar 11 22:33 scsi.mod
-rw-r--r-- 1 root root    2980 Mar 11 22:33 search_fs_file.mod
-rw-r--r-- 1 root root    3008 Mar 11 22:33 search_fs_uuid.mod
-rw-r--r-- 1 root root    2912 Mar 11 22:33 search_label.mod
-rw-r--r-- 1 root root    2628 Mar 11 22:33 search.mod
-rw-r--r-- 1 root root    7260 Mar 11 22:33 sendkey.mod
-rw-r--r-- 1 root root    7128 Mar 11 22:33 serial.mod
-rw-r--r-- 1 root root     706 Mar 11 22:33 setjmp.mod
-rw-r--r-- 1 root root    5512 Mar 11 22:33 setpci.mod
-rw-r--r-- 1 root root    4052 Mar 11 22:33 sfs.mod
-rw-r--r-- 1 root root    2392 Mar 11 22:33 sleep.mod
-rw-r--r-- 1 root root    3972 Mar 11 22:33 squash4.mod
-rw-r--r-- 1 root root    2968 Mar 11 22:33 tar.mod
-rw-r--r-- 1 root root     132 Mar 11 22:33 terminal.lst
-rw-r--r-- 1 root root    3836 Mar 11 22:33 terminal.mod
-rw-r--r-- 1 root root   10296 Mar 11 22:33 terminfo.mod
-rw-r--r-- 1 root root    1508 Mar 11 22:33 test_blockarg.mod
-rw-r--r-- 1 root root    2816 Mar 11 22:33 testload.mod
-rw-r--r-- 1 root root    5100 Mar 11 22:33 test.mod
-rw-r--r-- 1 root root    2940 Mar 11 22:33 tga.mod
-rw-r--r-- 1 root root    1763 Mar 11 22:33 trig.mod
-rw-r--r-- 1 root root    1356 Mar 11 22:33 true.mod
-rw-r--r-- 1 root root    6572 Mar 11 22:33 udf.mod
-rw-r--r-- 1 root root    4740 Mar 11 22:33 ufs1.mod
-rw-r--r-- 1 root root    5052 Mar 11 22:33 ufs2.mod
-rw-r--r-- 1 root root    6004 Mar 11 22:33 uhci.mod
-rw-r--r-- 1 root root 2560080 Mar 11 22:33 unicode.pf2
-rw-r--r-- 1 root root    4300 Mar 11 22:33 usb_keyboard.mod
-rw-r--r-- 1 root root    9656 Mar 11 22:33 usb.mod
-rw-r--r-- 1 root root    5604 Mar 11 22:33 usbms.mod
-rw-r--r-- 1 root root    2048 Mar 11 22:33 usbserial_common.mod
-rw-r--r-- 1 root root    2452 Mar 11 22:33 usbserial_ftdi.mod
-rw-r--r-- 1 root root    2812 Mar 11 22:33 usbserial_pl2303.mod
-rw-r--r-- 1 root root    3756 Mar 11 22:33 usbtest.mod
-rw-r--r-- 1 root root    8840 Mar 11 22:33 vbe.mod
-rw-r--r-- 1 root root    4724 Mar 11 22:33 vga.mod
-rw-r--r-- 1 root root    2308 Mar 11 22:33 vga_text.mod
-rw-r--r-- 1 root root    5536 Mar 11 22:33 video_bochs.mod
-rw-r--r-- 1 root root    5860 Mar 11 22:33 video_cirrus.mod
-rw-r--r-- 1 root root   19164 Mar 11 22:33 video_fb.mod
-rw-r--r-- 1 root root    3748 Mar 11 22:33 videoinfo.mod
-rw-r--r-- 1 root root      33 Mar 11 22:33 video.lst
-rw-r--r-- 1 root root   10752 Mar 11 22:33 video.mod
-rw-r--r-- 1 root root    4268 Mar 11 22:33 videotest.mod
-rw-r--r-- 1 root root    6152 Mar 11 22:33 xfs.mod
-rw-r--r-- 1 root root   31736 Mar 11 22:33 xnu.mod
-rw-r--r-- 1 root root    2016 Mar 11 22:33 xnu_uuid.mod
-rw-r--r-- 1 root root   14468 Mar 11 22:33 xzio.mod
-rw-r--r-- 1 root root    6360 Mar 11 22:33 zfsinfo.mod
-rw-r--r-- 1 root root   33308 Mar 11 22:33 zfs.mod

/boot/grub/fonts:
total 2510
drwxr-xr-x 2 root root    1024 Feb 28 00:31 .
drwxr-xr-x 5 root root    8192 Mar 11 22:33 ..
-rw-r--r-- 1 root root 2560080 Feb 28 00:25 unicode.pf2

/boot/grub/i386-pc:
total 1760
drwxr-xr-x 2 root root   7168 Feb 26 20:41 .
drwxr-xr-x 5 root root   8192 Mar 11 22:33 ..
-rw-r--r-- 1 root root   7268 Feb 26 20:41 915resolution.mod
-rw-r--r-- 1 root root  10152 Feb 26 20:41 acpi.mod
-rw-r--r-- 1 root root   1292 Feb 26 20:41 adler32.mod
-rw-r--r-- 1 root root   5632 Feb 26 20:41 affs.mod
-rw-r--r-- 1 root root   6876 Feb 26 20:41 afs.mod
-rw-r--r-- 1 root root   8692 Feb 26 20:41 ahci.mod
-rw-r--r-- 1 root root    705 Feb 26 20:41 all_video.mod
-rw-r--r-- 1 root root   1060 Feb 26 20:41 aout.mod
-rw-r--r-- 1 root root   5428 Feb 26 20:41 ata.mod
-rw-r--r-- 1 root root   4052 Feb 26 20:41 at_keyboard.mod
-rw-r--r-- 1 root root   1632 Feb 26 20:41 backtrace.mod
-rw-r--r-- 1 root root   7644 Feb 26 20:41 bfs.mod
-rw-r--r-- 1 root root   4676 Feb 26 20:41 biosdisk.mod
-rw-r--r-- 1 root root   2392 Feb 26 20:41 bitmap.mod
-rw-r--r-- 1 root root   3012 Feb 26 20:41 bitmap_scale.mod
-rw-r--r-- 1 root root   2036 Feb 26 20:41 blocklist.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 boot.img
-rw-r--r-- 1 root root   2448 Feb 26 20:41 boot.mod
-rw-r--r-- 1 root root  29524 Feb 26 20:41 bsd.mod
-rw-r--r-- 1 root root  14192 Feb 26 20:41 btrfs.mod
-rw-r--r-- 1 root root   2164 Feb 26 20:41 bufio.mod
-rw-r--r-- 1 root root   2232 Feb 26 20:41 cat.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 cdboot.img
-rw-r--r-- 1 root root   3500 Feb 26 20:41 chain.mod
-rw-r--r-- 1 root root   1536 Feb 26 20:41 cmostest.mod
-rw-r--r-- 1 root root   1988 Feb 26 20:41 cmp.mod
-rw-r--r-- 1 root root   3251 Feb 26 20:41 command.lst
-rw-r--r-- 1 root root   2208 Feb 26 20:41 configfile.mod
-rw-r--r-- 1 root root  26425 Feb 26 20:41 core.img
-rw-r--r-- 1 root root   4488 Feb 26 20:41 cpio_be.mod
-rw-r--r-- 1 root root   4380 Feb 26 20:41 cpio.mod
-rw-r--r-- 1 root root   1548 Feb 26 20:41 cpuid.mod
-rw-r--r-- 1 root root   1784 Feb 26 20:41 crc64.mod
-rw-r--r-- 1 root root   8688 Feb 26 20:41 cryptodisk.mod
-rw-r--r-- 1 root root    855 Feb 26 20:41 crypto.lst
-rw-r--r-- 1 root root   4376 Feb 26 20:41 crypto.mod
-rw-r--r-- 1 root root   3716 Feb 26 20:41 cs5536.mod
-rw-r--r-- 1 root root   1800 Feb 26 20:41 datehook.mod
-rw-r--r-- 1 root root   2176 Feb 26 20:41 date.mod
-rw-r--r-- 1 root root   1281 Feb 26 20:41 datetime.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 diskboot.img
-rw-r--r-- 1 root root   9696 Feb 26 20:41 diskfilter.mod
-rw-r--r-- 1 root root   1872 Feb 26 20:41 dm_nv.mod
-rw-r--r-- 1 root root   5380 Feb 26 20:41 drivemap.mod
-rw-r--r-- 1 root root   1964 Feb 26 20:41 echo.mod
-rw-r--r-- 1 root root   7432 Feb 26 20:41 efiemu32.o
-rw-r--r-- 1 root root  11137 Feb 26 20:41 efiemu64.o
-rw-r--r-- 1 root root  23960 Feb 26 20:41 efiemu.mod
-rw-r--r-- 1 root root  15624 Feb 26 20:41 ehci.mod
-rw-r--r-- 1 root root   4404 Feb 26 20:41 elf.mod
-rw-r--r-- 1 root root   5312 Feb 26 20:41 exfat.mod
-rw-r--r-- 1 root root   1468 Feb 26 20:41 exfctest.mod
-rw-r--r-- 1 root root   5784 Feb 26 20:41 ext2.mod
-rw-r--r-- 1 root root   4488 Feb 26 20:41 extcmd.mod
-rw-r--r-- 1 root root   5656 Feb 26 20:41 fat.mod
-rw-r--r-- 1 root root  12272 Feb 26 20:41 font.mod
-rw-r--r-- 1 root root   2208 Feb 26 20:41 freedos.mod
-rw-r--r-- 1 root root   2900 Feb 26 20:41 fshelp.mod
-rw-r--r-- 1 root root    194 Feb 26 20:41 fs.lst
-rw-r--r-- 1 root root   2764 Feb 26 20:41 functional_test.mod
-rw-r--r-- 1 root root    512 Feb 26 20:41 g2hdr.img
-rw-r--r-- 1 root root   1632 Feb 26 20:41 gcry_arcfour.mod
-rw-r--r-- 1 root root   8120 Feb 26 20:41 gcry_blowfish.mod
-rw-r--r-- 1 root root  34508 Feb 26 20:41 gcry_camellia.mod
-rw-r--r-- 1 root root  17224 Feb 26 20:41 gcry_cast5.mod
-rw-r--r-- 1 root root   2936 Feb 26 20:41 gcry_crc.mod
-rw-r--r-- 1 root root  19284 Feb 26 20:41 gcry_des.mod
-rw-r--r-- 1 root root   3124 Feb 26 20:41 gcry_md4.mod
-rw-r--r-- 1 root root   3808 Feb 26 20:41 gcry_md5.mod
-rw-r--r-- 1 root root   2448 Feb 26 20:41 gcry_rfc2268.mod
-rw-r--r-- 1 root root  19068 Feb 26 20:41 gcry_rijndael.mod
-rw-r--r-- 1 root root   8480 Feb 26 20:41 gcry_rmd160.mod
-rw-r--r-- 1 root root  16560 Feb 26 20:41 gcry_seed.mod
-rw-r--r-- 1 root root  16828 Feb 26 20:41 gcry_serpent.mod
-rw-r--r-- 1 root root   8672 Feb 26 20:41 gcry_sha1.mod
-rw-r--r-- 1 root root   3496 Feb 26 20:41 gcry_sha256.mod
-rw-r--r-- 1 root root   5700 Feb 26 20:41 gcry_sha512.mod
-rw-r--r-- 1 root root  11732 Feb 26 20:41 gcry_tiger.mod
-rw-r--r-- 1 root root  39520 Feb 26 20:41 gcry_twofish.mod
-rw-r--r-- 1 root root  24512 Feb 26 20:41 gcry_whirlpool.mod
-rw-r--r-- 1 root root  25716 Feb 26 20:41 gdb.mod
-rw-r--r-- 1 root root   5984 Feb 26 20:41 geli.mod
-rw-r--r-- 1 root root   4740 Feb 26 20:41 gettext.mod
-rw-r--r-- 1 root root  33108 Feb 26 20:41 gfxmenu.mod
-rw-r--r-- 1 root root  11728 Feb 26 20:41 gfxterm.mod
-rw-r--r-- 1 root root   3644 Feb 26 20:41 gptsync.mod
-rw-r--r-- 1 root root  10240 Feb 26 20:41 grldr.img
-rw-r--r-- 1 root root   8016 Feb 26 20:41 gzio.mod
-rw-r--r-- 1 root root   4064 Feb 26 20:41 halt.mod
-rw-r--r-- 1 root root   5076 Feb 26 20:41 hashsum.mod
-rw-r--r-- 1 root root   7176 Feb 26 20:41 hdparm.mod
-rw-r--r-- 1 root root   1204 Feb 26 20:41 hello.mod
-rw-r--r-- 1 root root   2548 Feb 26 20:41 help.mod
-rw-r--r-- 1 root root   3144 Feb 26 20:41 hexdump.mod
-rw-r--r-- 1 root root   7200 Feb 26 20:41 hfs.mod
-rw-r--r-- 1 root root   6596 Feb 26 20:41 hfsplus.mod
-rw-r--r-- 1 root root   5664 Feb 26 20:41 http.mod
-rw-r--r-- 1 root root  47780 Feb 26 20:41 hwmatch.mod
-rw-r--r-- 1 root root   2820 Feb 26 20:41 iorw.mod
-rw-r--r-- 1 root root   8724 Feb 26 20:41 iso9660.mod
-rw-r--r-- 1 root root   6552 Feb 26 20:41 jfs.mod
-rw-r--r-- 1 root root   6000 Feb 26 20:41 jpeg.mod
-rw-r--r-- 1 root root  28820 Feb 26 20:41 kernel.img
-rw-r--r-- 1 root root   4456 Feb 26 20:41 keylayouts.mod
-rw-r--r-- 1 root root   1944 Feb 26 20:41 keystatus.mod
-rw-r--r-- 1 root root   6796 Feb 26 20:41 ldm.mod
-rw-r--r-- 1 root root  28208 Feb 26 20:41 legacycfg.mod
-rw-r--r-- 1 root root   5948 Feb 26 20:41 linux16.mod
-rw-r--r-- 1 root root  11332 Feb 26 20:41 linux.mod
-rw-r--r-- 1 root root   1024 Feb 26 20:41 lnxboot.img
-rw-r--r-- 1 root root   5556 Feb 26 20:41 loadenv.mod
-rw-r--r-- 1 root root   2852 Feb 26 20:41 loopback.mod
-rw-r--r-- 1 root root   3608 Feb 26 20:41 lsacpi.mod
-rw-r--r-- 1 root root   2280 Feb 26 20:41 lsapm.mod
-rw-r--r-- 1 root root   1796 Feb 26 20:41 lsmmap.mod
-rw-r--r-- 1 root root   4344 Feb 26 20:41 ls.mod
-rw-r--r-- 1 root root   4816 Feb 26 20:41 lspci.mod
-rw-r--r-- 1 root root   6576 Feb 26 20:41 luks.mod
-rw-r--r-- 1 root root   6296 Feb 26 20:41 lvm.mod
-rw-r--r-- 1 root root   2816 Feb 26 20:41 lzma_decompress.img
-rw-r--r-- 1 root root   8676 Feb 26 20:41 lzopio.mod
-rw-r--r-- 1 root root   2008 Feb 26 20:41 mdraid09_be.mod
-rw-r--r-- 1 root root   1972 Feb 26 20:41 mdraid09.mod
-rw-r--r-- 1 root root   1968 Feb 26 20:41 mdraid1x.mod
-rw-r--r-- 1 root root   2004 Feb 26 20:41 memdisk.mod
-rw-r--r-- 1 root root   2840 Feb 26 20:41 memrw.mod
-rw-r--r-- 1 root root   3416 Feb 26 20:41 minicmd.mod
-rw-r--r-- 1 root root   3992 Feb 26 20:41 minix2_be.mod
-rw-r--r-- 1 root root   3872 Feb 26 20:41 minix2.mod
-rw-r--r-- 1 root root   3912 Feb 26 20:41 minix3_be.mod
-rw-r--r-- 1 root root   3848 Feb 26 20:41 minix3.mod
-rw-r--r-- 1 root root   3908 Feb 26 20:41 minix_be.mod
-rw-r--r-- 1 root root   3820 Feb 26 20:41 minix.mod
-rw-r--r-- 1 root root   9040 Feb 26 20:41 mmap.mod
-rw-r--r-- 1 root root   3973 Feb 26 20:41 moddep.lst
-rw-r--r-- 1 root root   2412 Feb 26 20:41 msdospart.mod
-rw-r--r-- 1 root root  12704 Feb 26 20:41 multiboot2.mod
-rw-r--r-- 1 root root  12196 Feb 26 20:41 multiboot.mod
-rw-r--r-- 1 root root  43860 Feb 26 20:41 net.mod
-rw-r--r-- 1 root root   4668 Feb 26 20:41 newc.mod
-rw-r--r-- 1 root root   6600 Feb 26 20:41 nilfs2.mod
-rw-r--r-- 1 root root 110404 Feb 26 20:41 normal.mod
-rw-r--r-- 1 root root   3416 Feb 26 20:41 ntfscomp.mod
-rw-r--r-- 1 root root  10276 Feb 26 20:41 ntfs.mod
-rw-r--r-- 1 root root   2552 Feb 26 20:41 ntldr.mod
-rw-r--r-- 1 root root   4468 Feb 26 20:41 odc.mod
-rw-r--r-- 1 root root  10372 Feb 26 20:41 ohci.mod
-rw-r--r-- 1 root root   1608 Feb 26 20:41 part_acorn.mod
-rw-r--r-- 1 root root   1752 Feb 26 20:41 part_amiga.mod
-rw-r--r-- 1 root root   2024 Feb 26 20:41 part_apple.mod
-rw-r--r-- 1 root root   2676 Feb 26 20:41 part_bsd.mod
-rw-r--r-- 1 root root   1428 Feb 26 20:41 part_dvh.mod
-rw-r--r-- 1 root root   2344 Feb 26 20:41 part_gpt.mod
-rw-r--r-- 1 root root    101 Feb 26 20:41 partmap.lst
-rw-r--r-- 1 root root   2260 Feb 26 20:41 part_msdos.mod
-rw-r--r-- 1 root root   1848 Feb 26 20:41 part_plan.mod
-rw-r--r-- 1 root root   1480 Feb 26 20:41 part_sun.mod
-rw-r--r-- 1 root root   1604 Feb 26 20:41 part_sunpc.mod
-rw-r--r-- 1 root root     17 Feb 26 20:41 parttool.lst
-rw-r--r-- 1 root root   4548 Feb 26 20:41 parttool.mod
-rw-r--r-- 1 root root   1896 Feb 26 20:41 password.mod
-rw-r--r-- 1 root root   2788 Feb 26 20:41 password_pbkdf2.mod
-rw-r--r-- 1 root root   4660 Feb 26 20:41 pata.mod
-rw-r--r-- 1 root root   1356 Feb 26 20:41 pbkdf2.mod
-rw-r--r-- 1 root root   1424 Feb 26 20:41 pci.mod
-rw-r--r-- 1 root root   6420 Feb 26 20:41 plan9.mod
-rw-r--r-- 1 root root   2432 Feb 26 20:41 play.mod
-rw-r--r-- 1 root root   6448 Feb 26 20:41 png.mod
-rw-r--r-- 1 root root   1548 Feb 26 20:41 priority_queue.mod
-rw-r--r-- 1 root root   2576 Feb 26 20:41 probe.mod
-rw-r--r-- 1 root root   1024 Feb 26 20:41 pxeboot.img
-rw-r--r-- 1 root root   2688 Feb 26 20:41 pxechain.mod
-rw-r--r-- 1 root root   3800 Feb 26 20:41 pxe.mod
-rw-r--r-- 1 root root   1372 Feb 26 20:41 raid5rec.mod
-rw-r--r-- 1 root root   2160 Feb 26 20:41 raid6rec.mod
-rw-r--r-- 1 root root   1492 Feb 26 20:41 read.mod
-rw-r--r-- 1 root root   1716 Feb 26 20:41 reboot.mod
-rw-r--r-- 1 root root  51684 Feb 26 20:41 regexp.mod
-rw-r--r-- 1 root root   9104 Feb 26 20:41 reiserfs.mod
-rw-r--r-- 1 root root  15104 Feb 26 20:41 relocator.mod
-rw-r--r-- 1 root root   4132 Feb 26 20:41 romfs.mod
-rw-r--r-- 1 root root   5120 Feb 26 20:41 scsi.mod
-rw-r--r-- 1 root root   3264 Feb 26 20:41 search_fs_file.mod
-rw-r--r-- 1 root root   3260 Feb 26 20:41 search_fs_uuid.mod
-rw-r--r-- 1 root root   3184 Feb 26 20:41 search_label.mod
-rw-r--r-- 1 root root   3636 Feb 26 20:41 search.mod
-rw-r--r-- 1 root root   7104 Feb 26 20:41 sendkey.mod
-rw-r--r-- 1 root root   7076 Feb 26 20:41 serial.mod
-rw-r--r-- 1 root root    706 Feb 26 20:41 setjmp.mod
-rw-r--r-- 1 root root   5360 Feb 26 20:41 setpci.mod
-rw-r--r-- 1 root root   5092 Feb 26 20:41 sfs.mod
-rw-r--r-- 1 root root   2224 Feb 26 20:41 sleep.mod
-rw-r--r-- 1 root root   7100 Feb 26 20:41 squash4.mod
-rw-r--r-- 1 root root   5208 Feb 26 20:41 tar.mod
-rw-r--r-- 1 root root    132 Feb 26 20:41 terminal.lst
-rw-r--r-- 1 root root   4152 Feb 26 20:41 terminal.mod
-rw-r--r-- 1 root root  11108 Feb 26 20:41 terminfo.mod
-rw-r--r-- 1 root root   1340 Feb 26 20:41 test_blockarg.mod
-rw-r--r-- 1 root root   2696 Feb 26 20:41 testload.mod
-rw-r--r-- 1 root root   4952 Feb 26 20:41 test.mod
-rw-r--r-- 1 root root   5160 Feb 26 20:41 tftp.mod
-rw-r--r-- 1 root root   2772 Feb 26 20:41 tga.mod
-rw-r--r-- 1 root root   1508 Feb 26 20:41 time.mod
-rw-r--r-- 1 root root   1691 Feb 26 20:41 trig.mod
-rw-r--r-- 1 root root   1204 Feb 26 20:41 true.mod
-rw-r--r-- 1 root root   7700 Feb 26 20:41 udf.mod
-rw-r--r-- 1 root root   5488 Feb 26 20:41 ufs1.mod
-rw-r--r-- 1 root root   5540 Feb 26 20:41 ufs2.mod
-rw-r--r-- 1 root root   6468 Feb 26 20:41 uhci.mod
-rw-r--r-- 1 root root   4032 Feb 26 20:41 usb_keyboard.mod
-rw-r--r-- 1 root root   9740 Feb 26 20:41 usb.mod
-rw-r--r-- 1 root root   7284 Feb 26 20:41 usbms.mod
-rw-r--r-- 1 root root   1988 Feb 26 20:41 usbserial_common.mod
-rw-r--r-- 1 root root   2340 Feb 26 20:41 usbserial_ftdi.mod
-rw-r--r-- 1 root root   2696 Feb 26 20:41 usbserial_pl2303.mod
-rw-r--r-- 1 root root   3604 Feb 26 20:41 usbtest.mod
-rw-r--r-- 1 root root   9540 Feb 26 20:41 vbe.mod
-rw-r--r-- 1 root root   4568 Feb 26 20:41 vga.mod
-rw-r--r-- 1 root root   2132 Feb 26 20:41 vga_text.mod
-rw-r--r-- 1 root root   5364 Feb 26 20:41 video_bochs.mod
-rw-r--r-- 1 root root   5688 Feb 26 20:41 video_cirrus.mod
-rw-r--r-- 1 root root  20016 Feb 26 20:41 video_fb.mod
-rw-r--r-- 1 root root   4032 Feb 26 20:41 videoinfo.mod
-rw-r--r-- 1 root root     33 Feb 26 20:41 video.lst
-rw-r--r-- 1 root root  10360 Feb 26 20:41 video.mod
-rw-r--r-- 1 root root   4168 Feb 26 20:41 videotest.mod
-rw-r--r-- 1 root root   6108 Feb 26 20:41 xfs.mod
-rw-r--r-- 1 root root  33168 Feb 26 20:41 xnu.mod
-rw-r--r-- 1 root root   2012 Feb 26 20:41 xnu_uuid.mod
-rw-r--r-- 1 root root  15200 Feb 26 20:41 xzio.mod
-rw-r--r-- 1 root root   5544 Feb 26 20:41 zfscrypt.mod
-rw-r--r-- 1 root root   6396 Feb 26 20:41 zfsinfo.mod
-rw-r--r-- 1 root root  36552 Feb 26 20:41 zfs.mod

/boot/grub/locale:
total 114
drwxr-xr-x 2 root root  1024 Feb 26 19:50 .
drwxr-xr-x 5 root root  8192 Mar 11 22:33 ..
-rw-r--r-- 1 root root   866 Feb 26 20:41 en_AU.mo
-rw-r--r-- 1 root root   466 Feb 26 20:41 en_CA.mo
-rw-r--r-- 1 root root  3531 Feb 26 20:41 en_GB.mo
-rw-r--r-- 1 root root 68774 Feb 26 20:41 es.mo
-rw-r--r-- 1 root root 30842 Feb 26 20:41 zh_CN.mo
ls: cannot open directory /boot/lost+found: Permission denied
```

---

### Post by oldfred on 2013-03-11
If from command line you uninstall grub-efi and installed grub-pc, I would not worry about any files. But you grub in the MBR does not look correct.

   for ?? on this drive.

The ?? really should be more like this:
looks 
    for (,msdos1)/boot/grub on this drive.

Or something similar which seems to depend on grub version.

---

### Post by elektronaut on 2013-03-11
First time I was running boot-info-script, before messing around with grub-efi, I got this output:[http://paste.ubuntu.com/5568131/]("http://paste.ubuntu.com/5568131/")
Notice this, no mention of msdos1:
```

Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub
```
This line is also different, no mention of core.img:
```
Boot files:        /grub/grub.cfg
```
I'm wondering how I can get back to that state?

---

### Post by oldfred on 2013-03-11
Actually that looks good it says partition 1. Different versions of grub have somewhat different info from boot script.

---

### Post by elektronaut on 2013-03-12
> **oldfred said:**
> Actually that looks good it says partition 1. Different versions of grub have somewhat different info from boot script.

Yeah, but that was the old state before my attempts trying to 'fix' the boot. Now it says:
```
Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
```
Do you suggest to somehow install Grub2 (v1.97-1.98) to see if the information will become like this again?
```
Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub.
```

---

### Post by oldfred on 2013-03-12
Do all this with encryption mounted.

If you just uninstalled grub-efi, you may not have reinstalled grub-pc?

# purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common grub-efi
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

If it gives an error on grub-efi not installed it is just that you already deleted it.

You do not have to chroot if already into your install. But I do not think this includes the extra steps to also mount the lmv.
 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by elektronaut on 2013-03-12
OK, I followed your advice and executed these steps:
> **oldfred said:**
> 
sudo apt-get purge grub grub-pc grub-common grub-efi
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

But I don't understand what I should do with this information:
> 
You do not have to chroot if already into your install. But I do not think this includes the extra steps to also mount the lmv.
 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
LVM is mounted, even if the boot info script output might suggest otherwise. The system is running and I can use all LV's. Alas, it seems that the output of boot info script didn't change:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb4 starts 
                       at sector -875547592. But according to the info from 
                       fdisk, sdb4 starts at sector 3419419704.
    Operating System:  
    Boot files:        

vg01-root': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

vg01-usr': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-var': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-tmp': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-home': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-swap': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       976,895       974,848  83 Linux
/dev/sda2    *        976,896 1,953,523,711 1,952,546,816  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34 1,953,793,169 1,953,793,136 Data partition (Windows/Linux)
/dev/sdb3   1,953,796,784 3,419,419,703 1,465,622,920 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sdb4   3,419,419,704 3,907,024,064   487,604,361 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/sda2_crypt xeVilN-lEBw-sTMF-e6Kt-DxYG-qByW-Kz8Qr5 LVM2_member 
/dev/mapper/vg01-home 7d7a7c88-799c-42af-add6-f221e5db5e9a   ext4       
/dev/mapper/vg01-root 740ff707-6cb2-4424-9ccf-955866171404   ext4       
/dev/mapper/vg01-swap a412acb0-bfae-4768-9129-21bc5479c53c   swap       
/dev/mapper/vg01-tmp ad8c13f5-3bed-4434-b3c9-3f357db9f743   ext4       
/dev/mapper/vg01-usr 0b595bbc-4de1-4705-bd27-19b741e80998   ext4       
/dev/mapper/vg01-var fc822b3e-d393-4f65-bb65-cd5278e30140   ext4       
/dev/sda1        ea3b7965-277e-4d9e-9a08-5a271f967422   ext4       
/dev/sda2        f7b214f1-6371-4465-abfa-3c3cb0f3c6a0   crypto_LUKS 
/dev/sdb1        a4652f1f-d0a8-4ecd-9f09-11d689ef342e   ext4       linux
/dev/sdb3        9f7e12c6-20cb-3a59-8ba0-5761a24b2217   hfsplus    osx
/dev/sdb4        68F2-15DF                              vfat       FAT32

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sda2_crypt
vg01-home
vg01-root
vg01-swap
vg01-tmp
vg01-usr
vg01-var

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg01-home /home                    ext4       (rw,usrquota,grpquota,acl,user_xattr)
/dev/mapper/vg01-root /                        ext4       (rw,errors=remount-ro,acl,user_xattr)
/dev/mapper/vg01-tmp /tmp                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-usr /usr                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-var /var                     ext4       (rw,acl,user_xattr)
/dev/sda1        /boot                    ext4       (rw,acl,user_xattr)
/dev/sdb1        /mnt/2tb-linux           ext4       (rw,noexec,nosuid,nodev,acl,user_xattr)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-38-generic ...'
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-38-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.055994987 = 0.060124160    grub/core.img                                  1
   0.263208389 = 0.282617856    grub/grub.cfg                                  1
   0.038486481 = 0.041324544    initrd.img-3.2.0-29-generic                    2
   0.053195000 = 0.057117696    initrd.img-3.2.0-38-generic                    1
   0.019269943 = 0.020690944    vmlinuz-3.2.0-29-generic                       1
   0.046621323 = 0.050059264    vmlinuz-3.2.0-38-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 20  |............... |
00000070  84 9b 32 71 cc a9 09 ae  93 c8 de e5 b4 fa 58 e5  |..2q..........X.|
00000080  38 96 16 af 98 79 32 ea  00 5e e2 2f bd 31 f8 14  |8....y2..^./.1..|
00000090  39 21 3f bd e0 a8 bd 3c  34 cb 4f 79 d4 62 9d 5e  |9!?....<4.Oy.b.^|
000000a0  9d 3a 36 12 00 00 3d 09  66 37 62 32 31 34 66 31  |.:6...=.f7b214f1|
000000b0  2d 36 33 37 31 2d 34 34  36 35 2d 61 62 66 61 2d  |-6371-4465-abfa-|
000000c0  33 63 33 63 62 30 66 33  63 36 61 30 00 00 00 00  |3c3cb0f3c6a0....|
000000d0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 08 00 00 0f a0  |................|
00000100  00 ac 71 f3 00 01 0a e7  34 42 0a 01 ae 82 99 d0  |..q.....4B......|
00000110  95 37 31 12 e6 ac 0d de  95 b0 45 6a 6f 48 24 ec  |.71.......EjoH$.|
00000120  1e 2d ad 96 85 92 78 1b  00 00 01 08 00 00 0f a0  |.-....x.........|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on sdb4

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 5a 00  |.X.MSWIN4.1..@Z.|
00000010  02 00 00 00 00 f8 00 00  20 00 ff 00 38 34 d0 cb  |........ ...84..|
00000020  89 40 10 1d 7b e8 00 00  00 00 00 00 02 00 00 00  |.@..{...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 df 15 f2 68 4e  4f 20 4e 41 4d 45 20 20  |..)...hNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on vg01-root'


Unknown BootLoader on vg01-usr'


Unknown BootLoader on vg01-var'


Unknown BootLoader on vg01-tmp'


Unknown BootLoader on vg01-home'


Unknown BootLoader on vg01-swap'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-root': No such file or directory
hexdump: /dev/mapper/vg01-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-usr': No such file or directory
hexdump: /dev/mapper/vg01-usr': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-var': No such file or directory
hexdump: /dev/mapper/vg01-var': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-tmp': No such file or directory
hexdump: /dev/mapper/vg01-tmp': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-home': No such file or directory
hexdump: /dev/mapper/vg01-home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-swap': No such file or directory
hexdump: /dev/mapper/vg01-swap': No such file or directory
```
There is still this line:
```
...looks for ?? on this drive.
```
What should I do now? Maybe I should try to install Grub to sda1 instead of sda?

---

### Post by oldfred on 2013-03-12
I do not know RAID nor LVM. But with RAID you do install to root of the RAID as system boots that. 
But I do not think LVM works that way. BIOS does not know about RAID, so it still boots from MBR.

More info here:
[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

---

### Post by elektronaut on 2013-03-12
Stephen describes how to mount the LV's and then install grub to sda. But I'm thinking that in my situation I probably have to specify sda1 given the following output:
```
me@server:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088855

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      976895      487424   83  Linux
/dev/sda2   *      976896  1953523711   976273408   83  Linux
...
me@server:~$ sudo parted -l
Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  500MB   499MB   primary  ext4
 2      500MB   1000GB  1000GB  primary               boot
...
```
The 500MB partition should be the boot partition, but the bigger encrypted partition is marked with the boot flag. I guess there should be no harm in configuring sda1, or?

---

### Post by oldfred on 2013-03-12
Grub does not use boot flag, just boot loader in MBR, more code in core.img just after MBR (to find the boot partition) and grub menu in boot partition. Then it loads kernels in boot partition and starts system.
Windows uses its boot loader in the MBR, then uses boot flag to find partition and more code in that partition's PBR or partition boot sector. Then it loads Windows.

BIOS always boots from MBR, or if RAID the root of the RAID set. 
Only the new efi systems do not use MBR, but use efi partition.

---

### Post by elektronaut on 2013-03-13
Thanks for the clarification. I'm still hesitating to reboot given the strange output of boot-info-script. Even if the boot flag has no significance, it seems that something is not in order. Unfortunately I couldn't find any information anywhere which might help.

---

### Post by elektronaut on 2013-03-13
Further searching revealed that it might be necessary to execute ```
grub-mkimage
``` [This thread ]("http://ubuntuforums.org/showthread.php?t=1198433")mentions ```
$ sudo grub-mkimage --output=/boot/grub/core.img ext2 _chain pc gpt biosdisk lvm 
``` in order to load a LVM, and [this page]("http://xercestech.com/full-system-encryption-for-linux.geek") mentions ```
$ sudo grub-mkimage -o /boot/grub/core.img configfile sha1 fs_uuid biosdisk pc linux ext2 help minicmd crypto aes luks sha256 devmapper
``` While the latter page describes how to fully encrypt the disk, which is not what I have here - /boot is not encrypted and not even part of a LV - the command might still be necessary in my case. 
What do you think?

---

### Post by oldfred on 2013-03-13
Maybe one of the few that know something about LVM or encryption will come along. I just do not know. 

Only a few use full disk encryption. It seems that a fair number do use /home encryption as all user data is then encrypted. But I have not used encryption at all.

---

### Post by elektronaut on 2013-03-20
I gave this another shot and installed boot-repair in the running system. Using the default settings, ignoring Raid and encryption messages (all LVM partitions were already mounted and decrypted), I unfortunately got an error message in the end. 

Here is the new boot info: [http://paste.ubuntu.com/5632309/]("http://paste.ubuntu.com/5632309/") 

Isn't there anybody who can help me out? :?

---

### Post by darkod on 2013-03-21
Unfortunately I have no experience with encryption at all. Not sure if that can interfere and how.

So, in this latest situation, what error do you actually get? What happens when you boot?

The boot info looks correct to me.

---

### Post by elektronaut on 2013-03-21
I'm too afraid to boot given that boot info script output mentions "Mounting failed", "unknown filesystem type" for my LV partitions, and further on:
```
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda2 -> Error code 32
Disk /dev/mapper/sda2_crypt doesn't contain a valid partition table
Disk /dev/mapper/vg01-root doesn't contain a valid partition table
Disk /dev/mapper/vg01-usr doesn't contain a valid partition table
Disk /dev/mapper/vg01-var doesn't contain a valid partition table
Disk /dev/mapper/vg01-tmp doesn't contain a valid partition table
Disk /dev/mapper/vg01-home doesn't contain a valid partition table
Disk /dev/mapper/vg01-swap doesn't contain a valid partition table
```
It also seems that "/boot" is now inside the encrypted LV "vg01-root" whereas it used to be on an unencrypted separate partition before. :confused:

Boot-Repair ended with a pop-up displaying some general error message.

---

### Post by darkod on 2013-03-21
Well, if you don't have faith in boot-repair, do it manually. First decrypt the encryption, and after that you could use it as non-encrypted system.

Try rebooting but have the live cd at hand if it fails to boot. If it fails to boot you will boot the machine in live mode and try installing grub2 manually.

Don't worry about those partition table messages, they are normal when using LVM. It tries to check for partition tables on all LVs and of course there is no partition table there because it's only a LV not a physical disk with partitions on it.
I'm not sure about the mount problems, if that is related to boot-repair or not.

I would try booting and if it doesn't then try to sort it out. If it boots as it is, you have nothing to solve, right?

---

### Post by elektronaut on 2013-03-21
It just seems strange to me and I have gone through the process of clearing CMOS already a couple of times. Still not sure why this was always necessary - the keyboard was not recognized, neither USB nor PS/2, I even couldn't enter the UEFI setup. I'm also wondering where the kernel has gone now:
```
$ ls -la /boot/
total 20
drwxr-xr-x  3 root root  4096 Mar 20 21:39 .
drwxr-xr-x 26 root root  4096 Mar 20 21:31 ..
drwxr-xr-x  3 root root 12288 Mar 20 21:39 grub
$ sudo mkdir /mnt/boot
$ sudo mount /dev/sda1 /mnt/boot
$ ls -la /mnt/boot
total 31565
drwxr-xr-x 6 root root    1024 Mar 20 21:36 .
drwxr-xr-x 6 root root    4096 Mar 21 18:42 ..
-rw-r--r-- 1 root root  791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r-- 1 root root  792830 Feb 19 13:58 abi-3.2.0-38-generic
-rw-r--r-- 1 root root  140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r-- 1 root root  140488 Feb 19 13:58 config-3.2.0-38-generic
drwxr-xr-x 3 root root    7168 Mar 20 21:37 grub
drwxr-xr-x 2 root root    7168 Mar 20 21:35 grub.bak
-rw-r--r-- 1 root root 8817030 Feb 27 23:35 initrd.img-3.2.0-29-generic
-rw------- 1 root root 5896152 Mar 20 21:10 initrd.img-3.2.0-38-generic
drwx------ 2 root root   12288 Feb 26 15:20 lost+found
-rw------- 1 root root 2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw------- 1 root root 2887333 Feb 19 13:58 System.map-3.2.0-38-generic
-rw------- 1 root root 4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw------- 1 root root 4968592 Feb 19 13:58 vmlinuz-3.2.0-38-generic
```
As I wrote before, "/boot" is now inside the LV "/dev/vg01/root" while it used to be on the separate partition sda1. I have no idea how to revert that.

---

### Post by elektronaut on 2013-03-21
Running Boot-Repair again, in the stage where grub-pc is configured, I no longer have the option to install either to sda or to sda1, but only to sda or /dev/dm-1 (vg01-root). If I choose sda, it fails ("GRUB failed to install to the following devices"). I don't want to have /boot in my encrypted root LV, this will probably cause even more trouble.

Thanks for the help so far, you two!

---

### Post by darkod on 2013-03-21
I don't think boot is inside the root LV. In your post above, you can clearly see the kernels when you mounted sda1 which is your /boot partition outside the encrypted LVM which is on sda2. You only have to take care to specify this when installing grub2, I think you have to do the same in boot-repair, there is an option to specify separate /boot partition and which one is it.

Look in the Grub Location tab, there is option to specify separate /boot:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by elektronaut on 2013-03-21
In Boot-Repair, I selected the option for a separate boot partition, but couldn't choose anything else than sda (the line was greyed out). Afterwards, grub-pc confronts me with the options to install either to sda or to dm-1, but it won't accept it anymore if I choose sda. OK, there is a boot directory on sda1, but it is not mounted right now. The boot directory I can access in the running system is another one, which is inside the root LV. And there is only a grub directory inside /boot, nothing else.
```
$ mount
/dev/mapper/vg01-root on / type ext4 (rw,errors=remount-ro,acl,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=52428800)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/mapper/vg01-tmp on /tmp type ext4 (rw,acl,user_xattr)
/dev/mapper/vg01-usr on /usr type ext4 (rw,acl,user_xattr)
/dev/mapper/vg01-home on /home type ext4 (rw,usrquota,grpquota,acl,user_xattr)
/dev/mapper/vg01-var on /var type ext4 (rw,acl,user_xattr)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)
```

---

### Post by darkod on 2013-03-21
Selecting the /boot option should enable the drop down box where you can select the partition. Unless something is messed up with the partition table.

I think I already mentioned, since boot-repair obviously fails, why don't you try reinstalling grub2 manually? I prefer doing it manually anyway, it gives you better control.

PS. One more question, are you running this from the OS or you are booting the machine in live mode? You have the OS running, right? In that case purging and reinstalling grub2 is even easier if you have the OS already booted.

---

### Post by elektronaut on 2013-03-21
Yes, I'm working with the running system right now. So you advice me to do these steps?
> **oldfred said:**
> 
# purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common grub-efi
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

You do not have to chroot if already into your install. But I do not think this includes the extra steps to also mount the lmv.
 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Anything else? I guess I don't have to do anything special about LVM and LUKS, as all partitions are already mounted?
What about 'grub-mkimage' (see my post on the previous page)? Do I need to call it, and if so, with which parameters?
The last time I tried to fix it with these commands didn't seem to work. So I guess something has to be adjusted.

---

### Post by darkod on 2013-03-21
If the system is running right now, first post the output of:
df -h
cat /etc/fstab

---

### Post by elektronaut on 2013-03-21
Darko, I was a bit restless and already purged grub, deleted the grub directory in /boot (inside the root LVM) and mounted /dev/sda1 to /boot. Afterwards I reinstalled grub and chose sda1, this time it was possible. 
But I got this warning:
```
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
```
Anyway, here is the situation right now:
```
$ df -h
Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root  1.9G  629M  1.2G  36% /
udev                   808M   12K  808M   1% /dev
tmpfs                  325M  500K  325M   1% /run
none                    50M     0   50M   0% /run/lock
none                   812M  4.0K  812M   1% /run/shm
/dev/mapper/vg01-tmp   461M   17M  421M   4% /tmp
/dev/mapper/vg01-usr   3.7G  1.1G  2.4G  32% /usr
/dev/mapper/vg01-home   19G  204M   18G   2% /home
/dev/mapper/vg01-var   6.0G  3.1G  2.6G  55% /var
/dev/sda1              461M   50M  388M  12% /boot

$ cat /etc/fstab
#	/etc/fstab:	static	file	system	information.
#
#	Use	'blkid'	to	print	the	universally	unique	identifier	for	a
#	device;	this	may	be	used	with	UUID=	as	a	more	robust	way	to	name	devices
#	that	works	even	if	disks	are	added	and	removed.	See	fstab(5).
#
#	<file	system>	<mount	point>	<type>	<options>	<dump>	<pass>
proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/mapper/vg01-root	/	ext4	errors=remount-ro,acl,user_xattr	0	1
#	/boot	was	on	/dev/sda1	during	installation
UUID=ea3b7965-277e-4d9e-9a08-5a271f967422	/boot	ext4	defaults,acl,user_xattr	0	2
/dev/mapper/vg01-home	/home	ext4	defaults,usrquota,grpquota,acl,user_xattr	0	2
/dev/mapper/vg01-tmp	/tmp	ext4	defaults,acl,user_xattr	0	2
/dev/mapper/vg01-usr	/usr	ext4	defaults,acl,user_xattr	0	2
/dev/mapper/vg01-var	/var	ext4	defaults,acl,user_xattr	0	2
/dev/mapper/vg01-swap	none	swap	sw	0	0
UUID=a4652f1f-d0a8-4ecd-9f09-11d689ef342e	/mnt/2tb-linux	ext4	defaults,noauto,users,acl,user_xattr	0	2
none	/run/lock	tmpfs	rw,noexec,nosuid,nodev,size=52428800	0	0
```
I didn't execute yet these two commands:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

---

### Post by darkod on 2013-03-21
You chose sda1 as /boot partition or as grub2 destination? If you chose it for grub2 destination that is why you got the error, it's not supposed to be installed onto a partition.

The grub-install /dev/sda would try to install it onto the MBR.

Also, did the /boot entry in fstab have all those options or you added them? Try leaving only 'defaults' for the /boot options. Save and close the file. Try the grub-install and depending on the result reboot.

---

### Post by elektronaut on 2013-03-21
OK, I now reinstalled grub to sda. The mount line for /boot in fstab was automagically inserted, I didn't touch that line. Here is the output of boot_info_script:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 19010 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       ?? on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  

vg01-root': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

vg01-usr': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-var': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-tmp': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-home': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-swap': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       976,895       974,848  83 Linux
/dev/sda2    *        976,896 1,953,523,711 1,952,546,816  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/sda2_crypt xeVilN-lEBw-sTMF-e6Kt-DxYG-qByW-Kz8Qr5 LVM2_member 
/dev/mapper/vg01-home 7d7a7c88-799c-42af-add6-f221e5db5e9a   ext4       
/dev/mapper/vg01-root 740ff707-6cb2-4424-9ccf-955866171404   ext4       
/dev/mapper/vg01-swap a412acb0-bfae-4768-9129-21bc5479c53c   swap       
/dev/mapper/vg01-tmp ad8c13f5-3bed-4434-b3c9-3f357db9f743   ext4       
/dev/mapper/vg01-usr 0b595bbc-4de1-4705-bd27-19b741e80998   ext4       
/dev/mapper/vg01-var fc822b3e-d393-4f65-bb65-cd5278e30140   ext4       
/dev/sda1        ea3b7965-277e-4d9e-9a08-5a271f967422   ext4       
/dev/sda2        f7b214f1-6371-4465-abfa-3c3cb0f3c6a0   crypto_LUKS 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sda2_crypt
vg01-home
vg01-root
vg01-swap
vg01-tmp
vg01-usr
vg01-var

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg01-home /home                    ext4       (rw,usrquota,grpquota,acl,user_xattr)
/dev/mapper/vg01-root /                        ext4       (rw,errors=remount-ro,acl,user_xattr)
/dev/mapper/vg01-tmp /tmp                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-usr /usr                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-var /var                     ext4       (rw,acl,user_xattr)
/dev/sda1        /boot                    ext4       (rw)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-38-generic ...'
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-38-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.010554314 = 0.011332608    grub/core.img                                  1
   0.143564224 = 0.154150912    grub/grub.cfg                                  1
   0.038486481 = 0.041324544    initrd.img-3.2.0-29-generic                    2
   0.070929527 = 0.076160000    initrd.img-3.2.0-38-generic                    2
   0.019269943 = 0.020690944    vmlinuz-3.2.0-29-generic                       1
   0.046621323 = 0.050059264    vmlinuz-3.2.0-38-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 20  |............... |
00000070  84 9b 32 71 cc a9 09 ae  93 c8 de e5 b4 fa 58 e5  |..2q..........X.|
00000080  38 96 16 af 98 79 32 ea  00 5e e2 2f bd 31 f8 14  |8....y2..^./.1..|
00000090  39 21 3f bd e0 a8 bd 3c  34 cb 4f 79 d4 62 9d 5e  |9!?....<4.Oy.b.^|
000000a0  9d 3a 36 12 00 00 3d 09  66 37 62 32 31 34 66 31  |.:6...=.f7b214f1|
000000b0  2d 36 33 37 31 2d 34 34  36 35 2d 61 62 66 61 2d  |-6371-4465-abfa-|
000000c0  33 63 33 63 62 30 66 33  63 36 61 30 00 00 00 00  |3c3cb0f3c6a0....|
000000d0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 08 00 00 0f a0  |................|
00000100  00 ac 71 f3 00 01 0a e7  34 42 0a 01 ae 82 99 d0  |..q.....4B......|
00000110  95 37 31 12 e6 ac 0d de  95 b0 45 6a 6f 48 24 ec  |.71.......EjoH$.|
00000120  1e 2d ad 96 85 92 78 1b  00 00 01 08 00 00 0f a0  |.-....x.........|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on vg01-root'


Unknown BootLoader on vg01-usr'


Unknown BootLoader on vg01-var'


Unknown BootLoader on vg01-tmp'


Unknown BootLoader on vg01-home'


Unknown BootLoader on vg01-swap'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-root': No such file or directory
hexdump: /dev/mapper/vg01-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-usr': No such file or directory
hexdump: /dev/mapper/vg01-usr': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-var': No such file or directory
hexdump: /dev/mapper/vg01-var': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-tmp': No such file or directory
hexdump: /dev/mapper/vg01-tmp': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-home': No such file or directory
hexdump: /dev/mapper/vg01-home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-swap': No such file or directory
hexdump: /dev/mapper/vg01-swap': No such file or directory
```
This line here definitely puzzles me:
```
core.img is at this location and looks 
    for ?? on this drive.
```
Not sure, if this will work. [This page]("https://wiki.archlinux.org/index.php/GRUB2#Root_Encryption") mentions that /etc/default/grub needs to contain some information about the cryptdevice. Should I add that manually?

---

### Post by darkod on 2013-03-22
Not sure, haven't worked with encryption. On top of that, you have also LVM so the parameter won't be /dev/sda2:root like in that example. Maybe it should be something like "cryptdevice=/dev/sda2:vg01-root".

Try adding that to /etc/default/grub and run update-grub after that so that it can update grub.cfg.

The ?? in the core.img message might be because of the encryption.

---

### Post by elektronaut on 2013-03-22
Further googling revealed almost no results for Ubuntu + cryptdevice in /etc/default/grub. It seems that this is only needed for other distros, apparently the Ubuntu grub installer takes a look at /etc/crypttab and magically does the right thing. At least a commentor on [this page]("http://www.oxygenimpaired.com/ubuntu-with-grub2-luks-encrypted-lvm-root-hidden-usb-keyfile") says so, and another forum member whom I contacted with a LVM/LUKS setup has nothing special in /etc/default/grub. The strange output of boot info script is due to the old version of the script. I purged it and downloaded it again like this: ```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```
Here is the new output: ```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 19010 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/grub on this drive.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

vg01-root': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

vg01-usr': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-var': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-tmp': _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-home': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg01-swap': ____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       976,895       974,848  83 Linux
/dev/sda2    *        976,896 1,953,523,711 1,952,546,816  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/sda2_crypt xeVilN-lEBw-sTMF-e6Kt-DxYG-qByW-Kz8Qr5 LVM2_member 
/dev/mapper/vg01-home 7d7a7c88-799c-42af-add6-f221e5db5e9a   ext4       
/dev/mapper/vg01-root 740ff707-6cb2-4424-9ccf-955866171404   ext4       
/dev/mapper/vg01-swap a412acb0-bfae-4768-9129-21bc5479c53c   swap       
/dev/mapper/vg01-tmp ad8c13f5-3bed-4434-b3c9-3f357db9f743   ext4       
/dev/mapper/vg01-usr 0b595bbc-4de1-4705-bd27-19b741e80998   ext4       
/dev/mapper/vg01-var fc822b3e-d393-4f65-bb65-cd5278e30140   ext4       
/dev/sda1        ea3b7965-277e-4d9e-9a08-5a271f967422   ext4       
/dev/sda2        f7b214f1-6371-4465-abfa-3c3cb0f3c6a0   crypto_LUKS 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sda2_crypt
vg01-home
vg01-root
vg01-swap
vg01-tmp
vg01-usr
vg01-var

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg01-home /home                    ext4       (rw,usrquota,grpquota,acl,user_xattr)
/dev/mapper/vg01-root /                        ext4       (rw,errors=remount-ro,acl,user_xattr)
/dev/mapper/vg01-tmp /tmp                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-usr /usr                     ext4       (rw,acl,user_xattr)
/dev/mapper/vg01-var /var                     ext4       (rw,acl,user_xattr)
/dev/sda1        /boot                    ext4       (rw)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
if loadfont /grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-38-generic ...'
	linux	/vmlinuz-3.2.0-38-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-38-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root ea3b7965-277e-4d9e-9a08-5a271f967422
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/vmlinuz-3.2.0-29-generic root=/dev/mapper/vg01-root ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.010554314 = 0.011332608    grub/core.img                                  1
   0.143564224 = 0.154150912    grub/grub.cfg                                  1
   0.038486481 = 0.041324544    initrd.img-3.2.0-29-generic                    2
   0.070929527 = 0.076160000    initrd.img-3.2.0-38-generic                    2
   0.019269943 = 0.020690944    vmlinuz-3.2.0-29-generic                       1
   0.046621323 = 0.050059264    vmlinuz-3.2.0-38-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 20  |............... |
00000070  84 9b 32 71 cc a9 09 ae  93 c8 de e5 b4 fa 58 e5  |..2q..........X.|
00000080  38 96 16 af 98 79 32 ea  00 5e e2 2f bd 31 f8 14  |8....y2..^./.1..|
00000090  39 21 3f bd e0 a8 bd 3c  34 cb 4f 79 d4 62 9d 5e  |9!?....<4.Oy.b.^|
000000a0  9d 3a 36 12 00 00 3d 09  66 37 62 32 31 34 66 31  |.:6...=.f7b214f1|
000000b0  2d 36 33 37 31 2d 34 34  36 35 2d 61 62 66 61 2d  |-6371-4465-abfa-|
000000c0  33 63 33 63 62 30 66 33  63 36 61 30 00 00 00 00  |3c3cb0f3c6a0....|
000000d0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 08 00 00 0f a0  |................|
00000100  00 ac 71 f3 00 01 0a e7  34 42 0a 01 ae 82 99 d0  |..q.....4B......|
00000110  95 37 31 12 e6 ac 0d de  95 b0 45 6a 6f 48 24 ec  |.71.......EjoH$.|
00000120  1e 2d ad 96 85 92 78 1b  00 00 01 08 00 00 0f a0  |.-....x.........|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on vg01-root'


Unknown BootLoader on vg01-usr'


Unknown BootLoader on vg01-var'


Unknown BootLoader on vg01-tmp'


Unknown BootLoader on vg01-home'


Unknown BootLoader on vg01-swap'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-root': No such file or directory
hexdump: /dev/mapper/vg01-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-usr': No such file or directory
hexdump: /dev/mapper/vg01-usr': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-var': No such file or directory
hexdump: /dev/mapper/vg01-var': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-tmp': No such file or directory
hexdump: /dev/mapper/vg01-tmp': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-home': No such file or directory
hexdump: /dev/mapper/vg01-home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg01-swap': No such file or directory
hexdump: /dev/mapper/vg01-swap': No such file or directory
```
Sadly, rebooting didn't work. The drive clicks a couple of times, the UEFI welcome screen is shown, but I can't even enter the UEFI settings, as the keyboard (even borrowed a PS/2 keyboard from a friend) is not working. Than the only option used to be to erase CMOS, which I have just done. Afterwards I could enter the UEFI settings, but still no booting from hard disk, it's simply not recognized, doesn't even show up in UEFI boot options. Hopefully it might work after a couple of times switching on and off again, otherwise I will have to boot the install CD and then try something else.

---

### Post by darkod on 2013-03-22
But your setup is not uefi as far as I can see. Forget about uefi, disable it in bios, and boot in the standard legacy mode (good old bios boot). Because of the encryption root is not shown entirely, but from what I can see this is not an uefi setup.

First of all, for uefi setup you need FAT32 EFI System Partition where it stores the boot files, and you have none.

Disable uefi in the bios and try booting.

---

### Post by elektronaut on 2013-03-22
When I talk about UEFI I mean BIOS, I thought that would be the new name for this point and click tool. The thing is, I can rarely enter it, usually the keyboard is not recognized. Doesn't matter if USB or PS/2. Have no idea what is wrong, has never been a problem before this installation of 12.04 LTS. There is no option to enable or disable UEFI, only in boot options I can choose "AHCI: P0: The CD-Rom". There used to be the option "UEFI: ...CD-Rom", which I never chose. The hard disk is obviously not detected, I can't choose it. Booting Ubuntu from the CD-Rom doesn't help as there is no hard disk which I could mount.

EDIT: Turns out that AHCI for the SATA Controller was the culprit. After choosing IDE mode, rebooting works. Let me do further investigation (especially on the malfunctioning keyboard), but at the moment this looks good.

---

### Post by darkod on 2013-03-22
Hmm, the SATA mode should be AHCI so that the disks can work faster. IDE is an older compatibility mode and is little bit slower and with more limited capabilities. Any sata disk should work OK when the SATA mode is set to AHCI. If you had the UEFI:CD-ROM boot option then the board supports uefi and I suggest you look into bios and disable it if there is an option. It could be called Boot Mode, Boot Option, etc. But not all boards offer it.

---

### Post by elektronaut on 2013-03-22
I could reenable AHCI mode, I also need this for hotplugging of my external eSata disk. Somehow on first boot after grub install only IDE mode seems to work, maybe something that should be memorized somewhere if others are also concerned. 
Unfortunately there is no option to turn off this whole UEFI bull****. 
Luckily, also my USB keyboard now works in pre-boot, so I can change BIOS settings when I need to. Still confused why there was this keyboard trouble before.

Anyway, all is well if it ends well. Many kudos to you guys, oldfred and Darko! Thanks for being at my side during this hard and long trip ;)

---

### Post by darkod on 2013-03-22
Glad to help. Cheers. :)

If you consider the thread closed, you can mark it closed in Thread Tools above the first post on any page.

---

