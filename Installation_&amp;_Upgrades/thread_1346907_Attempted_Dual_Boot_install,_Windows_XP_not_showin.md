---
title: "Attempted Dual Boot install, Windows XP not showing up in GRUB"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Konichiwa on 2009-12-05
Good afternoon all,

I attempted a dual boot of Ubuntu and XP and ran into a problem, when I boot up my machine XP no longer shows up.

Before I installed ubuntu, I created a new partition in XP and left it unformatted.

I then booted into ubuntu and installed ubuntu, I selected the "install ubuntu on the largest block of free space option".

It showed the XP partition in blue, and the new ubuntu partition in orange.


I installed ubuntu, rebooted my machine, and now I can no longer boot into XP.

If I click on Places>Computer I can see my other hard drive partition, get into it, and view my windows files.

I did some googling, which stated that I would need to point GRUB to my windows partition.

The problem is, I dont know where that is, in the Places Bar it shows up as /media/058530A27

The GRUB guide used /dev/sda.

what confuses me is that I thought that the windows partition would be something like /dev/sda1 and the ubuntu /dev/sda2.

Any help would be greatly appreciated.

---

### Post by darkod on 2009-12-05
You are right, /dev/sda is just the hard drive as a device. It needs to have a number if it's partition. The first quick data you can find out is if you run in terminal:
sudo fdisk -l (small L)

That will show you all partitions on your drive and their filesystem. Post the result here if you need help with it.

---

### Post by Konichiwa on 2009-12-05
/dev/sdb1   *           1       13429   107868411    7  HPFS/NTFS

Thats my XP partition, it lists that partition at the boot partition, yet it does not work.

---

### Post by Konichiwa on 2009-12-05
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Thats the guide I was going off of, under the "Recovering GRUB after windows install".

Are those steps correct for my situation?

Many thanks for your input.

---

### Post by darkod on 2009-12-05
Post whole results. Where is your /dev/sda drive? Where is ubuntu installed?

---

### Post by Konichiwa on 2009-12-05
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13429   107868411    7  HPFS/NTFS
/dev/sdb2           36824       38912    16779892+   7  HPFS/NTFS
/dev/sdb3           13430       36823   187912305    5  Extended
/dev/sdb5           13430       35869   180249268+  83  Linux
/dev/sdb6           35870       36823     7662973+  82  Linux swap / Solaris

---

### Post by darkod on 2009-12-05
Try running:
sudo apt-get remove dmraid

If that doesn't help look at post #2 here and do the instructions. Post your results here.
[http://ubuntuforums.org/showthread.php?t=1346798](http://ubuntuforums.org/showthread.php?t=1346798)

---

### Post by Konichiwa on 2009-12-05
The sudo apt-get remove dmraid did nor work, should install dmraid again?

Output from script.

```
============================ Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

```

---

### Post by darkod on 2009-12-05
No, you don't need dmraid unless you are running raid. But your results.txt file does not show anything? No info about the partitions.

---

### Post by Konichiwa on 2009-12-05
Thats the output thats in the text file the script placed there.

I am unsure if I am running a raid, is there a easy way to tell?

---

### Post by darkod on 2009-12-05
You would have o set up raid youself (or bought the computer with raid setup) so it's difficult not to know. In RAID1 for example two hdd of same size would work as mirror, so you will actually have space like you have one hdd, the other is a copy of the first. If one fails, you still have your data.
The file is empty, you can see yourself. That's not good. :(

---

### Post by Konichiwa on 2009-12-05
All my data is intact, fdisk sees the disk, if I install 8.10 or something earlier would this help?

Is there a way I can point grub to /dev/sdb1 manually since thats my XP partition?

---

### Post by darkod on 2009-12-05
There is, but I'm worried that the results.txt file came back empty. Grub2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by presence1960 on 2009-12-05
> **Konichiwa said:**
> The sudo apt-get remove dmraid did nor work, should install dmraid again?

Output from script.

```
============================ Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

```

something is definitely not right. Just so you can see here is the result of my boot info script:

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4c62

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   203,896,979   203,896,917   5 Extended
/dev/sdb5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sdb6           8,385,993    46,138,679    37,752,687  83 Linux
/dev/sdb2         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sdc2         130,030,110   312,576,704   182,546,595   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
/dev/sdb2: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
/dev/sdb6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
/dev/sdc1: UUID="AE542F2F542EF9AB" LABEL="xp" TYPE="ntfs" 
/dev/sdc2: UUID="7FDEA4295B094456" LABEL="win_data" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sda1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set ae542f2f542ef9ab
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-14-generic
   4.2GB: boot/initrd.img-2.6.31-15-generic
   4.2GB: boot/vmlinuz-2.6.31-14-generic
   4.2GB: boot/vmlinuz-2.6.31-15-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  0a 00 01 0f 00 65 5d 04  a0 32 00 00 00 00 03 03  |.....e]..2......|
00000010  00 62 61 00 00 00 00 00  00 00 04 32 00 61 61 01  |.ba........2.aa.|
00000020  0c 00 00 00 00 00 05 33  00 64 64 00 00 00 00 00  |.......3.dd.....|
00000030  00 00 07 0f 00 52 3c ee  0a 97 0a 00 00 00 09 32  |.....R<........2|
00000040  00 5f 5f 40 11 00 00 00  00 00 0a 13 00 64 64 00  |.__@.........dd.|
00000050  00 00 00 00 00 00 0c 32  00 62 62 34 0a 00 00 00  |.......2.bb4....|
00000060  00 00 bb 32 00 64 64 00  00 00 00 00 00 00 bd 3a  |...2.dd........:|
00000070  00 64 64 00 00 00 00 00  00 00 be 22 00 47 39 1d  |.dd........".G9.|
00000080  00 1d 1d 00 00 00 c2 22  00 1d 2b 1d 00 00 00 12  |......."..+.....|
00000090  00 00 c3 1a 00 76 39 35  d3 d2 0b 00 00 00 c5 12  |.....v95........|
000000a0  00 64 64 00 00 00 00 00  00 00 c6 10 00 64 64 00  |.dd..........dd.|
000000b0  00 00 00 00 00 00 c7 3e  00 c8 c8 00 00 00 00 00  |.......>........|
000000c0  00 00 c8 00 00 64 fd 00  00 00 00 00 00 00 ca 32  |.....d.........2|
000000d0  00 64 fd 00 00 00 00 00  00 00 00 00 00 00 00 00  |.d..............|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 82 00 ae 01 00 5b  |...............[|
00000170  03 00 01 00 01 40 02 00  00 00 00 00 00 00 00 00  |.....@..........|
00000180  00 00 00 00 00 00 03 02  03 03 03 03 03 03 03 00  |................|
00000190  00 00 00 00 00 00 00 01  d9 53 13 16 00 00 00 00  |.........S......|
000001a0  01 00 af 1a 29 85 e3 01  00 00 00 00 00 00 00 00  |....)...........|
000001b0  00 00 00 00 d9 53 13 16  62 4c 0b 00 00 00 00 01  |.....S..bL......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by bellylint on 2011-03-03
Not sure if this was mentioned earlier but...:D

An easy way to have Grub2 redetect your missing Windows XP or Windows 7 partition is by installing and running **startupmanager**.

1. From a terminal window enter:  **sudo apt-get install startupmanager**

2. After installation completes, you can now run the program in the terminal by entering:  **sudo startupmanager**

3. A GUI will appear, from the drop-down menu you can see the other OS's on your machine.  You can change the default OS or leave it alone.  Click the CLOSE button and your done!

Now when you reboot...tadaaaa, you will see your missing Windows partition listed under Grub!

---

