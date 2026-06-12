---
title: "grub fails (?)"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2011-05-22
Hi all

I have read about 10 forum-threads about [FONT="Courier New"]grub[/FONT]  and its errors, but nothing helped.


I have configured a wonderful distro at /dev/sda2 (sda1 is swap).
I backed up /dev/sda2 completely using [FONT="Courier New"]dd[/FONT].

Now, I want to restore everything (for that test, I deleted the whole content on /dev/sda, repartitioned it and restored the content using dd as well).


I forgot to backup the boot-sector on /dev/sda and want to generate a new boot-sector on /dev/sda using grub.

For that, I start a life-distro (ubuntu 10.10) and first check, if /dev/sda2 is visible and mounted (so I mount it on /media/rose).

Now, I install grub using
```
sudo bash
apt-get install grub
```
and start it
```
grub
```

Now I follow the main stream in the forum-threads in different forums:
```
grub> find /boot/grub/stage1

Error 15: File not found
```
Even omitting "/boot" and finding "/grub/stage1" leads to the same error.

I then tried to "chroot" to "/media/rose", which works fine, but even there I get the same errors.

Any help is welcome.

phi





Here are my Configs:

mount:
```

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/5A6456DE1A39FC1E type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/rose type ext4 (rw)

```

df:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   4088204     97360   3990844   3% /
none                   4080960       256   4080704   1% /dev
/dev/sr0                711674    711674         0 100% /cdrom
/dev/loop0              672384    672384         0 100% /rofs
none                   4088204       176   4088028   1% /dev/shm
tmpfs                  4088204        52   4088152   1% /tmp
none                   4088204        88   4088116   1% /var/run
none                   4088204         4   4088200   1% /var/lock
/dev/sda3             56669180     67716  56601464   1% /media/5A6456DE1A39FC1E
/dev/sda2             57673724  11253800  43490260  21% /media/rose
```

grub-probe /dev/sda
```
grub-probe: error: cannot find a device for /dev/sda (is /dev mounted?).

```

grub> setup (hd0,2)
```
setup (hd0,2)

Error 12: Invalid device requested

``` (this happens for ANY device)

ls /media/rose/boot/grub
```
915resolution.mod            gcry_seed.mod       part_sunpc.mod
acpi.mod                     gcry_serpent.mod    parttool.lst
affs.mod                     gcry_sha1.mod       parttool.mod
afs_be.mod                   gcry_sha256.mod     password.mod
afs.mod                      gcry_sha512.mod     password_pbkdf2.mod
aout.mod                     gcry_tiger.mod      pbkdf2.mod
ata.mod                      gcry_twofish.mod    pci.mod
ata_pthru.mod                gcry_whirlpool.mod  play.mod
at_keyboard.mod              gettext.mod         png.mod
befs_be.mod                  gfxmenu.mod         probe.mod
befs.mod                     gfxterm.mod         pxeboot.img
biosdisk.mod                 gptsync.mod         pxecmd.mod
bitmap.mod                   grldr.img           pxe.mod
bitmap_scale.mod             grub.cfg            raid5rec.mod
blocklist.mod                grubenv             raid6rec.mod
boot.img                     gzio.mod            raid.mod
boot.mod                     halt.mod            read.mod
bsd.mod                      handler.lst         reboot.mod
bufio.mod                    hashsum.mod         regexp.mod
cat.mod                      hdparm.mod          reiserfs.mod
cdboot.img                   hello.mod           relocator.mod
chain.mod                    help.mod            scsi.mod
cmostest.mod                 hexdump.mod         search_fs_file.mod
cmp.mod                      hfs.mod             search_fs_uuid.mod
command.lst                  hfsplus.mod         search_label.mod
configfile.mod               iorw.mod            search.mod
core.img                     iso9660.mod         serial.mod
cpio.mod                     jfs.mod             setjmp.mod
cpuid.mod                    jpeg.mod            setpci.mod
crc.mod                      kernel.img          sfs.mod
crypto.lst                   keystatus.mod       sleep.mod
crypto.mod                   linux16.mod         tar.mod
cs5536.mod                   linux.mod           terminal.lst
datehook.mod                 lnxboot.img         terminal.mod
date.mod                     loadenv.mod         terminfo.mod
datetime.mod                 locale              test.mod
device.map                   loopback.mod        tga.mod
diskboot.img                 lsmmap.mod          trig.mod
dm_nv.mod                    ls.mod              true.mod
drivemap.mod                 lspci.mod           udf.mod
echo.mod                     lvm.mod             ufs1.mod
efiemu32.o                   mdraid.mod          ufs2.mod
efiemu64.o                   memdisk.mod         uhci.mod
efiemu.mod                   memrw.mod           usb_keyboard.mod
elf.mod                      minicmd.mod         usb.mod
example_functional_test.mod  minix.mod           usbms.mod
ext2.mod                     mmap.mod            usbtest.mod
extcmd.mod                   moddep.lst          vbeinfo.mod
fat.mod                      msdospart.mod       vbe.mod
font.mod                     multiboot2.mod      vbetest.mod
fshelp.mod                   multiboot.mod       vga.mod
fs.lst                       nilfs2.mod          vga_text.mod
functional_test.mod          normal.mod          video_bochs.mod
gcry_arcfour.mod             ntfscomp.mod        video_cirrus.mod
gcry_blowfish.mod            ntfs.mod            video_fb.mod
gcry_camellia.mod            ohci.mod            video.lst
gcry_cast5.mod               part_acorn.mod      video.mod
gcry_crc.mod                 part_amiga.mod      videotest.mod
gcry_des.mod                 part_apple.mod      xfs.mod
gcry_md4.mod                 part_bsd.mod        xnu.mod
gcry_md5.mod                 part_gpt.mod        xnu_uuid.mod
gcry_rfc2268.mod             partmap.lst         zfsinfo.mod
gcry_rijndael.mod            part_msdos.mod      zfs.mod
gcry_rmd160.mod              part_sun.mod


```

grub-install --root-directory=/media/rose/ /dev/sda
```
/dev/sda does not have any corresponding BIOS drive.
```

fdisk -l:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         244        7538    58593280   83  Linux
/dev/sda3            7538       14593    56669184    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007566d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117219328    7  HPFS/NTFS

```

---

### Post by ronparent on 2011-05-22
From what you list it is apparent that you are using grub 2 and trying to find your problem with a combination of original grub and grub 2 commands. The simplest thing you can do to fix it is by doing an easy reinstall of grub 2. What has worked well for me is a simple two step process from a live cd session as outlined here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

First you mount the partition you had installed to (/dev/sda2) to an empty partition in your live cd filesystem:
> sudo mount /dev/sda2 /mnt
Then you install grub there and put the boot loader on /dev/sda:
> sudo grub-install --root-directory=/mnt/ /dev/sda

You should now be ready to successfully reboot.

---

### Post by phibuntu on 2011-05-22
After posting my own thread I have found out, that I used grub2 (instead of grub, what I was expecting).

It is always like that: After a day of research I post a thread, and after some minutes I solve it myself ;-)

I don't really know what caused the effect of making my restore work again, because I have tried different approaches before using the following finally working command:

```
grub-install --boot-directory=/media/rose /dev/sda
```


Here are some commands I have tried.
```
apt-get install grub-pc
```
```
upgrade-from-grub-legacy
```
```
update-grub
```

By the way, thanks ronparent

---

