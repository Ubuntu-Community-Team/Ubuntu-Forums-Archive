---
title: "I messed with my MBR"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by keevvv on 2010-10-07
Hey all,

I'm relatively new to Linux handling and here is what happened :

I have one HDD on my laptop which is partitionned to sda2 Windows (7) and sda3 Ubuntu. I installed Windows after Ubuntu, so I had to reinstall the GRUB, which is what I did. After this, the GRUB loader showed only Ubuntu and memtest as bootable, so being the newbie that I am, I tried reinstalling the MBR.

I did so with ms-sys package on sda, and now nothing will load as I have a message from Yukon PXE telling me there is no operating system to be found.

I have reinstalled GRUB on sda3, still nothing is recognized.

Now, here is the weird thing, there are three partitions, sda1 which I don't remember creating, is sized 1.6G and is the default boot (I cannot change on any partition the "bootable" tag under system-admin-disk utility).

Did I seriously mess something up with the MBR ? I'm thinking there is either some kind of special MBR for the laptop's hidden partitionned HDD or ms-sys did something wrong.

Any help is appreciated,

Thanks.

---

### Post by drs305 on 2010-10-07
keevvv,

Welcome to Ubuntu and the Ubuntu forums!  :-)

The extra partition could be a boot partition or a small recovery partition. Download and run the boot info script from the site linked below. Post the contents of the RESULTS.txt and we'll have a good idea how to put things back together again.

[_http://bootinfoscript.sourceforge.net_]("http://bootinfoscript.sourceforge.net")

It will help if you paste the contents between "code" tags, which you generate inside the post by clicking the # icon.

---

### Post by oldfred on 2010-10-07
Welcome to the forums.

We typically recommend lilo as it works like the windows boot loader over ms-sys as it is old. You could install the windows boot loader from the windows CD.

You may just have needed to run this to get grub's osprober to find windows:
sudo update-grub

Try reinstalling grub and booting into Ubuntu and run the update-grub.

New installs of windows 7 create a 100MB boot/recovery partition which has the first part of your boot and then the main install in the second partition. Vendors often add a recovery partition that is just an image of your drive to bring it back to like new & erasing everything.

If you want to know what is where  from Ubuntu or liveCD:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by keevvv on 2010-10-07
wow, wasn't expecting such a fast reply ! here is the code

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 367873560 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,084,479     3,082,432   7 HPFS/NTFS
/dev/sda2           3,084,480   249,569,774   246,485,295   7 HPFS/NTFS
/dev/sda3         249,571,328   488,396,799   238,825,472  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        58707C31707C17C8                       ntfs                                     
/dev/sda3        6aa0c236-9390-4b84-a918-c4c97c281231   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6aa0c236-9390-4b84-a918-c4c97c281231
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6aa0c236-9390-4b84-a918-c4c97c281231
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6aa0c236-9390-4b84-a918-c4c97c281231 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6aa0c236-9390-4b84-a918-c4c97c281231
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6aa0c236-9390-4b84-a918-c4c97c281231 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6aa0c236-9390-4b84-a918-c4c97c281231
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6aa0c236-9390-4b84-a918-c4c97c281231 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6aa0c236-9390-4b84-a918-c4c97c281231
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6aa0c236-9390-4b84-a918-c4c97c281231 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=6aa0c236-9390-4b84-a918-c4c97c281231 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 238.1GB: boot/grub/core.img
 186.9GB: boot/grub/grub.cfg
 188.3GB: boot/grub/stage2
 238.1GB: boot/initrd.img-2.6.31-14-generic
 130.6GB: boot/initrd.img-2.6.31-20-generic
 238.1GB: boot/vmlinuz-2.6.31-14-generic
 186.8GB: boot/vmlinuz-2.6.31-20-generic
 130.6GB: initrd.img
 238.1GB: initrd.img.old
 186.8GB: vmlinuz
 238.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 52 8e  |.1.......|...WR.|
00000010  c0 fb fc bf 00 06 b9 00  01 f3 a5 ea 20 06 00 00  |............ ...|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 83 c4 10 66  |..A......{.....f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 20 72 65 61  64 20 65 72 72 6f 72 20  |.... read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


```

---

### Post by oldfred on 2010-10-07
It looks like something is wrong with sda1. You should try testdisk and see if it will fix it. It looks like sda1 must have been your boot partition as it has the boot flag and your install in sda2 is missing bootmgr and BCD. If windows will see sda1 you can try running chkdsk from a windows repairCD.

If testdisk does not repair sda1, you may be able to repair sda2 and add the missing bootmgr and BCD to that partition to make it bootable. 

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Grub's osprober does not find the windows install. It must be looking for BCD or bootmgr which are missing or not visible in the sda1 partition.

---

### Post by drs305 on 2010-10-07
As *oldfred* has told you, getting Windows back is going to take some reconstruction.

You can get Ubuntu booting again a bit easier, and then work on restoring Windows as he describes. From a Karmic or later LiveCD Desktop, open a terminal and run the following.

```

sudo mkdir /mnt/temp
sudo mount /dev/sda3 /mnt/temp && sudo mount -B /dev /mnt/temp/dev && sudo mount -B /proc /mnt/temp/proc && sudo mount -B /sys /mnt/temp/sys && sudo mount -B /dev/pts /mnt/temp/dev/pts && sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf && sudo chroot /mnt/temp
sudo apt-get update # Note: Checks Internet connection. If this command doesn't run, don't do the rest.
apt-get purge grub grub-pc grub-common
apt-get install grub-pc
update-grub

```
As you uninstall, you may get a warning about uninstalling the bootloader. Tab to OK.
As you are installing grub-pc, TAB to OK except for the partitioning screen. In that screen, make sure an asterisk is in the "sda" listing (if not, use the SPACE key to select it). Do NOT select any partitions, just the drive. Then TAB to OK to complete the installation.

The details of what you are doing are located in this post:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by keevvv on 2010-10-07
Okay, so I've used testdisk to successfully rewrite a boot for sda1. If I restart without the LiveCD nothing happens, only an underscore flashing, which does not surprise me. However. If I try to reinstall grub here is what I get :

```
Creating config file /etc/default/grub with new version
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```note : For the instructions dsr gave I did not do all the mounting part beforehand and just used sudo at the start of each line as it was simpler and should work fine. I have restarted a few times to be sure I did not mount anything before, and it still did this.

---

### Post by drs305 on 2010-10-07
> **keevvv said:**
> Okay, so I've used testdisk to successfully rewrite a boot for sda1. If I restart without the LiveCD nothing happens, only an underscore flashing, which does not surprise me. However. If I try to reinstall grub here is what I get :

note : I did not do all the mounting part beforehand and just used sudo at the start of each line. I have restarted a few times to be sure I did not mount anything before, and it still did this.

You have to do the mounting; otherwise the commands will be run on the CD's files and not your real Ubuntu partition. The purpose of "chroot" is to allow the commands to act on the files in your actual install instead of failing when trying to write to the CD.

If you want to try to restore Windows before restoring Ubuntu, depending on whether or not your partition work with Windows is complete and successful, you can repair the Windows MBR with the following from the Ubuntu LiveCD:

```
sudo apt-get install lilo  # Don't do the complete install as a bootloader. Disregard any messages.
sudo lilo -M /dev/sda mbr

```
That should restore the Windows MBR and allow you to boot directly into Windows if you prefer to do that first. Note this does not require the same type of mounting as for installing Grub.

---

### Post by keevvv on 2010-10-08
okay, it worked fine after reinstalling GRUB - the mount wasn't working at first, but that was because I was installing stuff before.

As a token of my gratitude, here is a picture :
[IMG]http://oi55.tinypic.com/34q21yo.jpg[/IMG]

---

