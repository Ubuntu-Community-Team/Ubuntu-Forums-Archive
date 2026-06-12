---
title: "OOPS installed Ubuntu Twice Help!"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by sendarope on 2009-12-01
I ran into a problem when installing Ubuntu where my NIC and Wireless lost connectivity. So instead of fixing it, I like an idiot, just installed Ubuntu again. 

I fixed the first problem by doing this but in the process created a couple of others. The partitioner portion of the install created ANOTHER partition instead of overwriting the first install of Ubuntu. ( installed it again )

How do I resolve this? I'm installed on a Dell 1545 laptop and don't care (too much) about the original Windows as I'm content to throw that OS 9Vista upgraded to 7)in the trash. However I'm nervous about loosing it all together. and was hoping to keep it in a dual boot mode for a while.

Question: How do I delete the bad install of Ubuntu and restore it's partition for use on the good Ubuntu install?

I then ran the updates and the GRUB boot loader now shows 2 options to boot into the good Ubuntu, One to Windows 7 and another for the bad install. 
Question: Where can I find a good tutorial for GRUB configuration?

FYI: I'm new to Linux and am looking forward to converting all of my 4 PC's over. I've already got a friend using it and saved him from shelling out the cash on a MAC (he like me is sick of the windows crappy security and performance)

Thanks,

K

NOTE: I INSTALLED A SOLO INSTALL AND ERASED WINDOWS TONIGHT. FEELS SO GOOD TO BE FREE OF THAT MS TRASH

---

### Post by Megafag on 2009-12-01
> **sendarope said:**
> *OP*

What version are you using?

---

### Post by adaucourt on 2009-12-01
> **sendarope said:**
> I ran into a problem when installing Ubuntu where my NIC and Wireless lost connectivity. So instead of fixing it, I like an idiot, just installed Ubuntu again. 

I fixed the first problem by doing this but in the process created a couple of others. The partitioner portion of the install created ANOTHER partition instead of overwriting the first install of Ubuntu. ( installed it again )

How do I resolve this? I'm installed on a Dell 1545 laptop and don't care (too much) about the original Windows as I'm content to throw that OS 9Vista upgraded to 7)in the trash. However I'm nervous about loosing it all together. and was hoping to keep it in a dual boot mode for a while.

Question: How do I delete the bad install of Ubuntu and restore it's partition for use on the good Ubuntu install?

I then ran the updates and the GRUB boot loader now shows 2 options to boot into the good Ubuntu, One to Windows 7 and another for the bad install. 
Question: Where can I find a good tutorial for GRUB configuration?

FYI: I'm new to Linux and am looking forward to converting all of my 4 PC's over. I've already got a friend using it and saved him from shelling out the cash on a MAC (he like me is sick of the windows crappy security and performance)

Thanks,

K

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by darkod on 2009-12-01
In short, you can see all your partitions if you run in terminal:
sudo fdisk -l (small L)

In long, and if you want to start learning ;) , download the script from my signature. Then run the script, if for example it's on the desktop, with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. That contains your whole booting process, boot files, again all the partitions, whole loads of info.
If you still want further help for deleting the "bad" ubunu, copy the content of the results file here. Please wrap it in CODE tags for easier reading (after you copy it here select whole text and hit # button in the toolbar, this relates only to the text from results.txt)

---

### Post by sendarope on 2009-12-01
Ubuntu 9.10
                - the Karmic Koala

---

### Post by sendarope on 2009-12-01
Cool script!

> ============================= boot info summary: ==============================

 => grub1.97 is installed in the mbr of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.
 => no boot loader is installed in the mbr of /dev/sdc

sda1: _________________________________________________________________________

    file system:       Vfat
    boot sector type:  Dell utility: Fat16
    boot sector info:  No errors found in the boot parameter block.
    Operating system:  
    Boot files/dirs:   

Sda2: _________________________________________________________________________

    file system:       Ntfs
    boot sector type:  Windows vista
    boot sector info:  No errors found in the boot parameter block.
    Operating system:  Windows vista
    boot files/dirs:   /windows/system32/winload.exe

sda3: _________________________________________________________________________

    file system:       Ntfs
    boot sector type:  Windows vista
    boot sector info:  No errors found in the boot parameter block.
    Operating system:  Windows vista
    boot files/dirs:   /bootmgr /boot/bcd /windows/system32/winload.exe

sda4: _________________________________________________________________________

    file system:       Extended partition
    boot sector type:  -
    boot sector info:  

Sda5: _________________________________________________________________________

    file system:       Ext4
    boot sector type:  -
    boot sector info:  
    Operating system:  Ubuntu 9.10
    boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    file system:       Swap
    boot sector type:  -
    boot sector info:  

Sda7: _________________________________________________________________________

    file system:       Ext4
    boot sector type:  -
    boot sector info:  
    Operating system:  Ubuntu 9.10
    boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    file system:       Swap
    boot sector type:  -
    boot sector info:  

Sdc1: _________________________________________________________________________

    file system:       Vfat
    boot sector type:  Unknown
    boot sector info:  No errors found in the boot parameter block.
    Operating system:  
    Boot files/dirs:   

=========================== drive/partition info: =============================

drive: Sda ___________________ _____________________________________________________

disk /dev/sda: 160.0 gb, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
units = sectors of 1 * 512 = 512 bytes
disk identifier: 0x00638cbf

partition  boot         start           end          size  id system

/dev/sda1                  63        80,324        80,262  de dell utility
/dev/sda2              81,920    30,801,919    30,720,000   7 hpfs/ntfs
/dev/sda3    *     30,801,920   131,566,272   100,764,353   7 hpfs/ntfs
/dev/sda4         131,572,350   312,576,704   181,004,355   5 extended
/dev/sda5         191,912,553   307,564,424   115,651,872  83 linux
/dev/sda6         307,564,488   312,576,704     5,012,217  82 linux swap / solaris
/dev/sda7         131,572,476   189,326,024    57,753,549  83 linux
/dev/sda8         189,326,088   191,912,489     2,586,402  82 linux swap / solaris


drive: Sdc ___________________ _____________________________________________________

disk /dev/sdc: 1031 mb, 1031306752 bytes
32 heads, 63 sectors/track, 999 cylinders, total 2014271 sectors
units = sectors of 1 * 512 = 512 bytes
disk identifier: 0x00000000

partition  boot         start           end          size  id system

/dev/sdc1                 243     2,013,983     2,013,741   6 fat16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: Sec_type="msdos" label="dellutility" uuid="3030-3030" type="vfat" 
/dev/sda2: Uuid="9438de9a38de7aa6" label="recovery" type="ntfs" 
/dev/sda3: Uuid="6ccce26acce22dd0" label="os" type="ntfs" 
/dev/sda5: Uuid="da3fe346-0207-4cdf-b82a-a4defedd3945" type="ext4" 
/dev/sda6: Uuid="3233f1e5-3fe3-4cfd-a0c5-e7f6bad354e1" type="swap" 
/dev/sda7: Uuid="6e9385f4-1b93-4785-94be-78dbd8f1ece2" type="ext4" 
/dev/sda8: Uuid="04706e44-44c8-45bf-a298-c7f35f2bebf1" type="swap" 
/dev/sdc1: Sec_type="msdos" type="vfat" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kurtfeigel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kurtfeigel)
/dev/sr1 on /media/u3 system type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# do not edit this file
#
# it is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### begin /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set da3fe346-0207-4cdf-b82a-a4defedd3945
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # for backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### end /etc/grub.d/00_header ###

### begin /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### end /etc/grub.d/05_debian_theme ###

### begin /etc/grub.d/10_linux ###
menuentry "ubuntu, linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set da3fe346-0207-4cdf-b82a-a4defedd3945
    linux    /boot/vmlinuz-2.6.31-14-generic root=uuid=da3fe346-0207-4cdf-b82a-a4defedd3945 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "ubuntu, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set da3fe346-0207-4cdf-b82a-a4defedd3945
    linux    /boot/vmlinuz-2.6.31-14-generic root=uuid=da3fe346-0207-4cdf-b82a-a4defedd3945 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### end /etc/grub.d/10_linux ###

### begin /etc/grub.d/20_memtest86+ ###
menuentry "memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttys0,115200n8
}
### end /etc/grub.d/20_memtest86+ ###

### begin /etc/grub.d/30_os-prober ###
menuentry "windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6ccce26acce22dd0
    chainloader +1
}
### end /etc/grub.d/30_os-prober ###

### begin /etc/grub.d/40_custom ###
# this file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### end /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: Static file system information.
#
# use 'blkid -o value -s uuid' to print the universally unique identifier
# for a device; this may be used with uuid= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
uuid=da3fe346-0207-4cdf-b82a-a4defedd3945 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
uuid=3233f1e5-3fe3-4cfd-a0c5-e7f6bad354e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by grub: ===================


  98.2gb: Boot/grub/grub.cfg
  98.2gb: Boot/initrd.img-2.6.31-14-generic
  98.2gb: Boot/vmlinuz-2.6.31-14-generic
  98.2gb: Initrd.img
  98.2gb: Vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# do not edit this file
#
# it is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### begin /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,7)
search --no-floppy --fs-uuid --set 6e9385f4-1b93-4785-94be-78dbd8f1ece2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # for backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### end /etc/grub.d/00_header ###

### begin /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### end /etc/grub.d/05_debian_theme ###

### begin /etc/grub.d/10_linux ###
menuentry "ubuntu, linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 6e9385f4-1b93-4785-94be-78dbd8f1ece2
    linux    /boot/vmlinuz-2.6.31-15-generic root=uuid=6e9385f4-1b93-4785-94be-78dbd8f1ece2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "ubuntu, linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 6e9385f4-1b93-4785-94be-78dbd8f1ece2
    linux    /boot/vmlinuz-2.6.31-15-generic root=uuid=6e9385f4-1b93-4785-94be-78dbd8f1ece2 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "ubuntu, linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 6e9385f4-1b93-4785-94be-78dbd8f1ece2
    linux    /boot/vmlinuz-2.6.31-14-generic root=uuid=6e9385f4-1b93-4785-94be-78dbd8f1ece2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "ubuntu, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 6e9385f4-1b93-4785-94be-78dbd8f1ece2
    linux    /boot/vmlinuz-2.6.31-14-generic root=uuid=6e9385f4-1b93-4785-94be-78dbd8f1ece2 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### end /etc/grub.d/10_linux ###

### begin /etc/grub.d/20_memtest86+ ###
menuentry "memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttys0,115200n8
}
### end /etc/grub.d/20_memtest86+ ###

### begin /etc/grub.d/30_os-prober ###
menuentry "windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6ccce26acce22dd0
    chainloader +1
}
menuentry "ubuntu, linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set da3fe346-0207-4cdf-b82a-a4defedd3945
    linux /boot/vmlinuz-2.6.31-14-generic root=uuid=da3fe346-0207-4cdf-b82a-a4defedd3945 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "ubuntu, linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set da3fe346-0207-4cdf-b82a-a4defedd3945
    linux /boot/vmlinuz-2.6.31-14-generic root=uuid=da3fe346-0207-4cdf-b82a-a4defedd3945 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### end /etc/grub.d/30_os-prober ###

### begin /etc/grub.d/40_custom ###
# this file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### end /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: Static file system information.
#
# use 'blkid -o value -s uuid' to print the universally unique identifier
# for a device; this may be used with uuid= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
uuid=6e9385f4-1b93-4785-94be-78dbd8f1ece2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
uuid=04706e44-44c8-45bf-a298-c7f35f2bebf1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by grub: ===================


  67.3gb: Boot/grub/grub.cfg
  67.3gb: Boot/initrd.img-2.6.31-14-generic
  67.3gb: Boot/initrd.img-2.6.31-15-generic
  67.3gb: Boot/vmlinuz-2.6.31-14-generic
  67.3gb: Boot/vmlinuz-2.6.31-15-generic
  67.3gb: Initrd.img
  67.3gb: Initrd.img.old
  67.3gb: Vmlinuz
  67.3gb: Vmlinuz.old
=========================== unknown mbrs/boot sectors/etc =======================

unknown bootloader  on sdc1

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 20 01 00  |.<.msdos5.0.. ..|
00000010  02 00 02 00 00 f8 f6 00  3f 00 20 00 f3 00 00 00  |........?. .....|
00000020  2d ba 1e 00 80 00 29 00  00 00 00 4e 4f 20 4e 41  |-.....)....no na|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |me    fat16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..v.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |u."..~..n.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.e..8n$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..w.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....v....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.f...f..f..v.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.f....v.`.f..v..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...h...f..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |n.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..e.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.n....f..v......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.rp.sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.f..&...3......b|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..b...v$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.b.^.iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 53 79 73  |..'..invalid sys|
00000190  74 65 6d 20 44 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |i/o error...repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 50  72 65 73 73 20 41 6e 79  |d then press any|
000001d0  20 4b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....io      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |sysmsdos   sys..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.a...`fj..;...u.|
00000200


=======devices which don't seem to have a corresponding hard drive==============

sdb 

---

### Post by darkod on 2009-12-01
Your second, or "good" ubuntu is on sda7, partition #7. The swap partition is sda8.

From the previous ubuntu install / is on sda5 and swap on sda6.

You can delete sda5 and sda6 if you want to. After that you can even expand sda7 to use the free space that will be created.
Or you can delete both versions and install again, good practice. :) Up to you.

---

### Post by Megafag on 2009-12-01
> **darkod said:**
> Your second, or "good" ubuntu is on sda7, partition #7. The swap partition is sda8.

From the previous ubuntu install / is on sda5 and swap on sda6.

You can delete sda5 and sda6 if you want to. After that you can even expand sda7 to use the free space that will be created.
Or you can delete both versions and install again, good practice. :) Up to you.

If it was me i would just use Gparted to wipe all the partitions and start again.

That looks like a mess....

---

### Post by darkod on 2009-12-01
@Megafag
Indeed it is. :) Hence my last sentence. Start over if you want to.

---

### Post by sendarope on 2009-12-02
Did a clean install tonight. Goodbye windows.

---

