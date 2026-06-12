---
title: "Boot Manager Issues (BCD Load GRUB?)"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by corbin1 on 2010-01-01
Hi, I started installed Ubuntu earlier this afternoon, and I had expected it to be easy, but now a lot of hours later, I've just about given up.

Basically my goal is to triple boot Vista/7/Ubuntu.  Vista was installed first, then 7.  Anyway, my goal is to keep using the Vista BCD booter (I think my computer is actually using the Windows 7 one right now, but basically my point is that I want to keep the bootloader I have now).

So, my disk layout:

2 physical drives:

sda:
   ~230GB Windows partition
   ~8GB Recovery partition

sdb:
    ~500GB Data partition
    ~450GB extended partition
        ~40GB logical partition with Windows 7
        ~40GB empty space that might eventually have Windows XP (most likely when the Windows 7 beta expires :()
        ~27GB Ubuntu /
        ~3GB SWAP
        ~340GB empty space for something eventually.


Anyway, as for the specifics with names, I'm going to attach RESULTS.TXT from the script that I keep seeing people request results from in topics similar to my own.



So, here's what I've been trying for the past 2 hours:

My plan was to have the BCD loader load GRUB from the Ubuntu logical partition (is that even possible?  It is, right?  For BCD to load GRUB?)

I want to avoid having GRUB load BCD in case I decide to get rid of Ubuntu eventually (depends how often I want to use Windows only programs that don't run well in Wine).  I know I could do GRUB -> BCD, but I would rather do BCD->GRUB.

Anyway, I'm installing Ubuntu off a USB drive (Unetbootin created).  Just following the GUI from the live CD (well, live USB, I guess ;p).  So, I'm doing a manual partition setup.  At the end, I clicked on advanced and set it to installed GRUB to /dev/sdb10 (which is my Ubuntu partition).

Now the problem:  Whenever I use EasyBCD to add an entry for grub, I point it at the correct disk (in EasyBCD, it's partition 6, but it doesn't appear to automatically start counting at 5 for partitions inside an extended partition.

So, I restart, and select the Ubuntu option and get some bootpart not found, please insert primary disk message (if it's important, I can write down the actual message).  In other words, it seems to me that GRUB isn't ever getting reached.

Why not?  I'm sure I just lack understanding of how the MBR and partition boot sectors work and whatnot, but I don't see what's missing.


One weird thing I have noticed though is that under Ubuntu, a lot of the GRUB stuff seems kind of weird.  For example /boot/grub/setup1 doesn't exist (assuming / is the root under the Ubuntu install of course, not the live USB).  Also, /boot/grub/menu.lst doesn't exist.  Are those files gone with GRUB 2?  Or are they missing?  Or what?

I've tried to reinstall GRUB through the GRUB shell, but of course without /boot/grub/setup1 I can't get very far (and it's not in /lib/grub/... or where ever).


**tl;dr:** How do I get BCD to load GRUB off of a logical partition?




RESULTS.txt from the boot_info script:

> 
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb8: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   475,491,869   475,491,807   7 HPFS/NTFS
/dev/sda2         475,491,870   488,392,064    12,900,195   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8b766c5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,048,578,614 1,048,578,552   7 HPFS/NTFS
/dev/sdb2       1,048,578,615 1,953,520,064   904,941,450   5 Extended
/dev/sdb5       1,048,578,678 1,132,470,044    83,891,367   7 HPFS/NTFS
/dev/sdb6       1,132,470,108 1,174,415,759    41,945,652   7 HPFS/NTFS
/dev/sdb7       1,174,415,823 1,258,307,189    83,891,367  83 Linux
/dev/sdb8       1,321,217,793 1,953,520,064   632,302,272  83 Linux
/dev/sdb9       1,314,920,313 1,321,217,729     6,297,417  82 Linux swap / Solaris
/dev/sdb10   *  1,258,307,253 1,314,920,249    56,612,997  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="DA30944330942891" TYPE="ntfs" 
sda2: UUID="2C88743C8874071C" LABEL="Recovery" TYPE="ntfs" 
sdb1: UUID="3C88B7B188B76852" LABEL="Television" TYPE="ntfs" 
sdb5: UUID="C49E16BB9E16A5C8" LABEL="Win 7" TYPE="ntfs" 
sdb6: UUID="A06416F36416CC42" LABEL="pubic_html" TYPE="ntfs" 
sdb9: UUID="845ae427-15b6-4fb3-8602-fee789b4bc9b" TYPE="swap" 
sdb10: UUID="884c6a03-f39a-433f-93cc-2f6f034020a8" SEC_TYPE="ext2" TYPE="ext3" 
sdc1: LABEL="UBUNTU" UUID="E023-B4A1" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)


========================== sdb10/boot/grub/grub.cfg: ==========================

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
set root=(hd1,10)
search --no-floppy --fs-uuid --set 884c6a03-f39a-433f-93cc-2f6f034020a8
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,10)
	search --no-floppy --fs-uuid --set 884c6a03-f39a-433f-93cc-2f6f034020a8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=884c6a03-f39a-433f-93cc-2f6f034020a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,10)
	search --no-floppy --fs-uuid --set 884c6a03-f39a-433f-93cc-2f6f034020a8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=884c6a03-f39a-433f-93cc-2f6f034020a8 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set da30944330942891
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 2c88743c8874071c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb10 during installation
UUID=884c6a03-f39a-433f-93cc-2f6f034020a8 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=845ae427-15b6-4fb3-8602-fee789b4bc9b none            swap    sw              0       0

=================== sdb10: Location of files loaded by Grub: ===================


 644.2GB: boot/grub/core.img
 644.2GB: boot/grub/grub.cfg
 644.2GB: boot/initrd.img-2.6.31-14-generic
 644.2GB: boot/vmlinuz-2.6.31-14-generic
 644.2GB: initrd.img
 644.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 



---

### Post by darkod on 2010-01-01
I don't understand why are you making things more complicated. First of all, both your windows seem installed on sda and if you put grub with ubuntu on sdb, that will not harm windows bootloader on sda at all.
Second, even if you decide to get rid of ubuntu later and want to restore windows bootloader on any MBR, it's a two click process.
You lost hours just because of refusing to use grub2.
Yes, menu.lst doesn't exist because grub2 doesn't use it.
You said you specified to install grub2 on sdb10 but you can see in the results file in the partitions info at the start, under sdb10 no grub2 on the bootsector is mentioned. Grub 2 doesn't seem to be on sdb10 and you probably can't chainload it because of that. I don't know what happened there.
Also, sdb7 and sdb8 seem unregonized by the script. The results say unknown filesystem. sdb9 is swap and sdb10 is ubuntu root. What are sdb7 and sdb8?
IMHO, just keep windows bootloader in the MBR of sda and put grub2 in the MBR of sdb and enjoy your triple boot system.

---

### Post by corbin1 on 2010-01-01
Oh, sdb7 and sdb8 aren't formatted yet.


I guess the whole GRUB 2 not having menu.lst and all of that stuff makes sense.


One question though.  Is it possible to get BCD to chainload to the MBR of a different disk, or am I going to have to change the HDD boot order in the BIOS?  I guess instead of asking that I should just go try it lol.


Anyway, thanks!


Edit:  Oh!  You were saying put GRUB on the sdb, set the boot priority to sdb, then if I ever get rid of Ubuntu (and thus grub) just switch the priority back to sda....  Ahhh!

---

