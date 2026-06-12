---
title: "Low Disk Space on &quot;efi&quot;. The volume &quot;efi&quot; has only 0 bytes disk space remaining"
date: 2020-09-13
forum: Installation &amp; Upgrades
---

### Post by gnuoob-l on 2020-09-13
Hello,

I'm getting that error (in title) upon logging onto my desktop. 
I've attached a picture but it says exactly what I have in the title.
My system runs smoothly otherwise and it is a ASUS x203ma.

Thank you for any help you might be able to provide.

Dave :)

---

### Post by ubfan1 on 2020-09-13
How big is the EFI partition and what's on it?  From a terminal look at the output of df and see what the /boot/efi mount says.  My EFI is 300MB, but with an ASUS, Boot, Microsoft, and ubuntu directory under /boot/efi/EFI, the total space used is only 47MB.

---

### Post by gnuoob-l on 2020-09-15
*(I'm not sure why pictures are upside down as they aren't on my system)*

EFI partician is 512mb
df command is in 2nd attached picture

System originally had Win10"S" on it but I wiped the thing clean and went default ubunty 19.10 and have since upgraded to 20.04 some months past. 
I do have encryption on the unit as its only 11 inches and weighs just 2lbs and can grow legs and walk away as I use the thing over my lunch hours in public places.

---

### Post by ubfan1 on 2020-09-15
Well, something's filling up your EFI partition.  It's mounted at /boot/efi, so take a look.  sudo ls /boot/efi/EFI  to see the directories.  sudo du -s /boot/efi/EFI/* to see how big they are.  I bet there's a big Microsoft driectory you no longer need, but even that shouldn't take up that much space.  Boot, ubuntu are the minimum directories.  Each should have a few .efi files.

---

### Post by gnuoob-l on 2020-09-15
$ sudo ls /boot/efi/EFI 
returns...
BOOT ubuntu


$ sudo du -s /boot/eft/EFI/*
returns...
du: cannot access '/boot/efi/EFT/*': No such file or directory

There isn't a M$ directory as I purged/cleaned the recovery/install stuff so there isn't going back*. The system has 64gb and linux/gparted shows total space of 57gb which sounds just about right. On top of that I have the 512mb efi partician and a 732mb ext4 boot partician.
*(I did create a USB recovery drive however cause you never know)

---

### Post by gnuoob-l on 2020-09-15
By the way, thank you for your efforts :)

---

### Post by Dennis N on 2020-09-15
To see what's using the space, use the command I use here and post everything inside code tags (select and click the #) to make it easy to read. This tells us the directories and files and the size of each in bytes. Then someone can advise what should be done.

```
dmn@Tyana:~$ sudo ls -Rs -1 /boot/efi/
/boot/efi/:
total 1
1 EFI

/boot/efi/EFI:
total 2
1 BOOT
1 manjaro
1 ubuntu

/boot/efi/EFI/BOOT:
total 3729
1304 BOOTX64.EFI
1185 fbx64.efi
1240 mmx64.efi

/boot/efi/EFI/manjaro:
total 152
152 grubx64.efi

/boot/efi/EFI/ubuntu:
total 3959
   1 BOOTX64.CSV
   1 grub.cfg
1414 grubx64.efi
1240 mmx64.efi
1304 shimx64.efi


```

---

### Post by gnuoob-l on 2020-09-15
```
dave@daveUbu-E203MA:~$ sudo ls -Rs -1 /boot/efi
[sudo] password for dave: 
/boot/efi:
total 68492
    4 boot
    4 casper
    4 dists
    4 EFI
    4 install
    4 ISOLINUX
    4 preseed
    4 README.diskdefines
60280 ubninit
 8176 ubnkern
    4 ubnpathl.txt


/boot/efi/boot:
total 4
4 grub


/boot/efi/boot/grub:
total 2372
2336 efi.img
   8 font.pf2
   4 grub.cfg
   4 loopback.cfg
  20 x86_64-efi


/boot/efi/boot/grub/x86_64-efi:
total 2536
16 acpi.mod
 4 adler32.mod
24 ahci.mod
 4 all_video.mod
 4 aout.mod
 8 appleldr.mod
 8 archelp.mod
12 ata.mod
 8 at_keyboard.mod
 4 backtrace.mod
12 bfs.mod
 4 bitmap.mod
 8 bitmap_scale.mod
 4 blocklist.mod
 4 boot.mod
48 bsd.mod
 4 bswap_test.mod
20 btrfs.mod
 4 bufio.mod
 8 cat.mod
 8 cbfs.mod
 8 cbls.mod
 4 cbmemc.mod
 4 cbtable.mod
 8 cbtime.mod
20 chain.mod
 8 cmdline_cat_test.mod
 4 cmp.mod
 8 cmp_test.mod
 4 command.lst
 8 cpio_be.mod
 8 cpio.mod
 4 cpuid.mod
 4 crc64.mod
16 cryptodisk.mod
 4 crypto.lst
 8 crypto.mod
 4 cs5536.mod
 4 ctz_test.mod
 4 datehook.mod
 4 date.mod
 4 datetime.mod
16 diskfilter.mod
 4 disk.mod
 4 div.mod
12 div_test.mod
 4 dm_nv.mod
 4 echo.mod
 4 efifwsetup.mod
16 efi_gop.mod
12 efinet.mod
 8 efi_uga.mod
28 ehci.mod
 8 elf.mod
 4 eval.mod
 8 exfat.mod
 4 exfctest.mod
12 ext2.mod
 8 fat.mod
28 file.mod
 4 fixvideo.mod
20 font.mod
 4 fs.lst
 4 gcry_arcfour.mod
12 gcry_blowfish.mod
28 gcry_camellia.mod
16 gcry_cast5.mod
 4 gcry_crc.mod
20 gcry_des.mod
 4 gcry_dsa.mod
 4 gcry_idea.mod
 8 gcry_md4.mod
 8 gcry_md5.mod
 4 gcry_rfc2268.mod
24 gcry_rijndael.mod
 8 gcry_rmd160.mod
 4 gcry_rsa.mod
16 gcry_seed.mod
20 gcry_serpent.mod
 8 gcry_sha1.mod
 8 gcry_sha256.mod
 8 gcry_sha512.mod
16 gcry_tiger.mod
36 gcry_twofish.mod
24 gcry_whirlpool.mod
12 geli.mod
12 gettext.mod
60 gfxmenu.mod
 8 gfxterm_background.mod
 8 gfxterm_menu.mod
20 gfxterm.mod
 8 gptsync.mod
 4 grub.cfg
12 gzio.mod
 8 halt.mod
12 hashsum.mod
12 hdparm.mod
 4 help.mod
 8 hexdump.mod
12 hfs.mod
 8 hfspluscomp.mod
12 hfsplus.mod
12 http.mod
 8 iorw.mod
12 jfs.mod
12 jpeg.mod
 8 keylayouts.mod
 4 keystatus.mod
 8 ldm.mod
44 legacycfg.mod
16 legacy_password_test.mod
16 linux16.mod
12 linuxefi.mod
24 linux.mod
 8 loadbios.mod
12 loadenv.mod
 8 loopback.mod
 8 lsacpi.mod
 4 lsefimmap.mod
 8 lsefi.mod
 8 lsefisystab.mod
 4 lsmmap.mod
 8 ls.mod
 8 lspci.mod
 4 lssal.mod
12 luks.mod
12 lvm.mod
 8 lzopio.mod
 8 macbless.mod
12 macho.mod
 4 mdraid09_be.mod
 4 mdraid09.mod
 4 mdraid1x.mod
 8 memrw.mod
 8 minicmd.mod
 8 minix2_be.mod
 8 minix2.mod
 8 minix3_be.mod
 8 minix3.mod
 8 minix_be.mod
12 mmap.mod
 8 moddep.lst
 4 morse.mod
44 mpi.mod
 4 msdospart.mod
 4 mul_test.mod
24 multiboot2.mod
20 multiboot.mod
 8 nativedisk.mod
88 net.mod
 8 newc.mod
 8 ntfscomp.mod
16 ntfs.mod
 8 odc.mod
 4 offsetio.mod
16 ohci.mod
 4 part_acorn.mod
 4 part_amiga.mod
 4 part_apple.mod
 8 part_bsd.mod
 4 part_dfly.mod
 4 part_dvh.mod
 4 part_gpt.mod
 4 partmap.lst
 4 part_msdos.mod
 4 part_plan.mod
 4 part_sun.mod
 4 part_sunpc.mod
 4 parttool.lst
 8 parttool.mod
 4 password.mod
 8 password_pbkdf2.mod
 8 pata.mod
 4 pbkdf2.mod
 4 pbkdf2_test.mod
 4 pcidump.mod
 4 play.mod
12 png.mod
 4 priority_queue.mod
 8 probe.mod
 4 procfs.mod
 4 progress.mod
 4 raid5rec.mod
 4 raid6rec.mod
 4 random.mod
 4 read.mod
 4 reboot.mod
76 regexp.mod
16 reiserfs.mod
28 relocator.mod
 8 romfs.mod
 8 scsi.mod
16 serial.mod
 4 setjmp.mod
 4 setjmp_test.mod
12 setpci.mod
 4 shift_test.mod
12 signature_test.mod
 4 sleep.mod
 4 sleep_test.mod
 4 spkmodem.mod
12 squash4.mod
32 syslinuxcfg.mod
 4 terminal.lst
 8 terminal.mod
20 terminfo.mod
 4 test_blockarg.mod
 4 testload.mod
 8 test.mod
 4 testspeed.mod
12 tftp.mod
 8 tga.mod
 4 time.mod
 4 trig.mod
 4 tr.mod
 4 true.mod
12 udf.mod
 8 ufs1_be.mod
 8 ufs1.mod
 8 ufs2.mod
12 uhci.mod
 8 usb_keyboard.mod
16 usb.mod
12 usbms.mod
 4 usbserial_common.mod
 4 usbserial_ftdi.mod
 4 usbserial_pl2303.mod
 4 usbserial_usbdebug.mod
 8 usbtest.mod
20 verify.mod
12 video_bochs.mod
12 video_cirrus.mod
12 video_colors.mod
32 video_fb.mod
 8 videoinfo.mod
 4 video.lst
12 video.mod
 4 videotest_checksum.mod
 8 videotest.mod
12 xfs.mod
44 xnu.mod
 4 xnu_uuid.mod
 4 xnu_uuid_test.mod
20 xzio.mod
12 zfscrypt.mod


/boot/efi/casper:
total 440848
     4 filesystem.size
440840 filesystem.squashfs
     4 README.diskdefines


/boot/efi/dists:
total 4
4 pool


/boot/efi/dists/pool:
total 0


/boot/efi/EFI:
total 8
4 BOOT
4 ubuntu


/boot/efi/EFI/BOOT:
total 4720
1172 BOOTx64.EFI
1188 fbx64.efi
1120 grubx64.efi
1240 mmx64.efi


/boot/efi/EFI/ubuntu:
total 4200
   4 BOOTX64.CSV
   4 fw
   4 grub.cfg
1644 grubx64.efi
1240 mmx64.efi
1304 shimx64.efi


/boot/efi/EFI/ubuntu/fw:
total 0


/boot/efi/install:
total 0


/boot/efi/ISOLINUX:
total 44
 4 isohdpfx.bin
40 isolinux.bin


/boot/efi/preseed:
total 0
dave@daveUbu-E203MA:~$ ^C
dave@daveUbu-E203MA:~$
```

---

### Post by ubfan1 on 2020-09-15
Oh my, looks like all the grub files which should have been put into root's  /boot/grub got dumped into the efi's  /boot/efi/boot/grub. 
This may be necessary by your disk encryption, of which I don't know much.  If all those files are necessary, maybe you do need a bigger EFI partition.
The EFI partition should minimal contain:  
/EFI/Boot/bootx64.efi  -- this the bootloader used, so make it a copy of  shimx64.efi for secure boot, otherwise a copy of   grubx64.efi
/EFI/Boot/grubx64.efi  -- When bootx64.efi is a copy of shimx64.efi, put the  signed grubx64.efi in the same directory.
/EFI/ubuntu/grub.cfg   -- The grub stub configuration file.

Example of the grub.cfg stub file, with the root on the eighth partition:
search.fs_uuid Your-UUID-here root hd0,gpt8 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


The /EFI/ubuntu file may also contain copies of grubx64.efi and shimx64.efi, and it is these files that are typically set up in nvram for the EFI ubuntu boot selection.  the /EFI/Boot files may be booted by booting the device, so the device may be moved to other machines and boot EFI without any nvram entries needed.

---

### Post by gnuoob-l on 2020-09-16
Okay, so how do I fix it? 
Do I ignore the error and hope things don't go south?
Is it easier to just fdisk the thing and start over again with(out?) the encryption?
I've had the worst luck with linux as a whole but for some reason I keep coming back.

---

### Post by ubfan1 on 2020-09-16
No experience on my part for disk encryption, but check out [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)  Their example did have a 768MB EFI partition (with only 195MB used. But practically, grub itself hardly ever changes, so you can probably run the way you are just fine.

---

### Post by blockchainhead on 2021-04-06
Hey all. Not sure if this is too late to help gnuoob-l, but I noted that you have one partition mounted at /boot/efi and another one mounted at /boot, which could be causing you and the system a little confusion when listing the files present in those overlapping /boot directories.

For all who have arrived on this page because you have Windows 10 installed on your primary harddisk, and Ubuntu installed either on the same disk in a newly created partition (after shrinking the Windows partition) or on a second hard disk, and are now getting a message every time that you boot your system complaining that the EFI Partition is low on disk space ... I may have useful information for you. I hope.

After installing the original Windows 10, I also installed Visual Studio with all the bells and whistles with vague intent to dive in and use as much as possible from the examples given. Still on the todo list, but what I did not realise was Microsoft now uses an EFI System Partition of just 260Mb, and Visual Studio places a huge amount of Kernal Debug software into the same EFI partition, basically filling it. Adding the Ubuntu 20.04.2.0 LTE installation, using the same EFI System Partition, left zero bytes available - yet miraculously worked and Ubuntu starts up.

I started looking for online solutions to free some space in the EFI Partition, and learned a lot about Windows and Linux tools that did not solve the problem. Short of uninstalling Visual Studio, (and hoping the uninstall removed those KDnet files), I was left with just one option: Extend the EFI System Partition to give it some more breathing room. However, I found a mysterious Microsoft Reserved (MSR) Partition located right between the EFI System Partition (ESP) and the Windows 10 partition. More research revealed little about whether I could move/resize that, and I was overthinking if Windows 10 expects to find these partitions in specific places on the harddisk.

Finally I bit the bullet and did the following steps:

1) Create (using Rufus) one USB Pen for the latest version (groovy) of CloneZilla.
2) Create (also Rufus) one USB Pen for the latest Ubuntu Live 20.04.2.0 with 4Gb of Persistence, (a virtual HD for Ubuntu Live to use for installing extra Ubuntu software on the same USB Pen)
3) Booted into CloneZilla and cloned the entire Windows disk to an external 4Tb USB hard drive.
4) Used CloneZilla to clone the Windows partition to the same external drive.
5) Used CloneZilla to restore the cloned partition to the Windows partition of the internal harddisk, just to test the backup works well. It did for me.
6) Booted up into Ubuntu Live using the USB Pen, and then used "Ubuntu Software" to install GParted onto the same pen.
7) Used GParted to reduce the size of the Windows partition on the internal harddisk, introducing 240Mb free space between the MSR and Windows partitions.
8) Used GParted to move the MSR partition to the end of the 240Mb of free space, leaving 1Mb between MSR and Windows partitions, and introducing 239Mb free space between the EFI and MSR partitions.
* Note: I felt that I had seen a 1Mb unallocated space there in Windows, but GParted and Windows Disk Management can play tricks on the mind after two days of deciding what to do.
9) Used GParted to extend the EFI partition to use the 239Mb of free space, delivering an EFI System Partition of almost 500Mb and only 50% occupied.
10) Restarted into Windows 10. Sighed with relief. No restore of a 1Tb disk required from CloneZilla.
11) Restarted in Ubuntu 20.04.2.0 and smiled as no "EFI Partition low on disk space" complaint appeared.
12) Used CloneZilla to create a new clone of the entire internal Windows harddisk, and a separate one of the now smaller Windows partition, (plus one of the Ubuntu harddisk for safe measure).

I hope that this helps. Please be paranoid about backing up and testing your restore process, (in general), but don't let fear of the unknown stop you from finding and testing your own solutions.

Good luck! Don't be a blockhead. ;-)

---

