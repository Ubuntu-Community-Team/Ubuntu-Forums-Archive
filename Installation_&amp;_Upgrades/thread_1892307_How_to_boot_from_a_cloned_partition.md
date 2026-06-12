---
title: "How to boot from a cloned partition"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by thegreeneyes on 2011-12-07
Hi, I have Ubuntu 11.10 running on a 20GB partition. 

I created another partition in the same (and only) harddisk of 20GB. 

I cloned the sda1 working partition on to sda2 empty partition using clonezilla. 

I could boot from sda1 and redefine UUID for sda2, and modified /dev/sda2/etc/fstab  with the new UUID for sda2. Then I ran

    sudo update-grub

and expected to be able to boot from sda2 as I do from sda1. Grub shows the line to boot from sda2, but when I choose it, after a few seconds it says "error no such device" followed by some uuid.

Any advice about how to proceed to be able to boot from sda2 as I do from sda1?

Thanks

---

### Post by oldfred on 2011-12-07
Grub still has a UUID that is wrong. You could try manually editing the grub stanza, by using e on grub menu, but I do not know correct entry.

Post this to see details. Then we may know what is wrong.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by thegreeneyes on 2011-12-08
Thanks oldfred, I downloaded unzipped and ran the bash script you sent me, (I didn't install mawk), and the RESULTS.txt file follows at the end of these initial paragraphs.

My first question was a simplification of the real situation, I have several partitions on my sda and sdb. The working partition in my sda disk (where grub is installed I think) is sda9. The cloned partition which I want to be able to boot from is sda11.

I don't know if it is of interest, but this is the output of 

sudo blkid :

```
$ sudo blkid
[sudo] password for vhg: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda10: LABEL="SYS_BACKUPS" UUID="82017acc-d6db-45ef-a9de-5b909c12efa1" TYPE="ext4" 
/dev/sda2: LABEL="OS_MSWIN" UUID="A0888EEC888EC070" TYPE="ntfs" 
/dev/sda5: LABEL="_CentOS-6.0-x86_" UUID="edc69754-7af9-4df6-86ef-8d5ebba96d20" TYPE="ext4" 
/dev/sda6: LABEL="11.10.01Nov11" UUID="11311fdc-b9ad-47ca-953c-5d2a0dd65b4f" TYPE="ext4" 
/dev/sda7: LABEL="11.10.02Dec11" UUID="b4dcab56-fe5d-4931-a1d7-a27fc476136d" TYPE="ext4" 
/dev/sdb1: LABEL="MyHome" UUID="642fcc4c-eb6d-4225-a83e-86c61e4daf28" TYPE="ext2" 
/dev/sdb5: LABEL="EXTRA" UUID="a3084ee6-9c95-40fc-8944-3599bca69f43" TYPE="ext2" 
/dev/sdb6: LABEL="BACKUPS" UUID="12043f13-e9fa-444d-b164-6f119c4cfc6f" TYPE="ext2" 
/dev/sda8: UUID="d5fe0a97-baa8-47f5-9703-dd510bd94425" TYPE="swap" 
/dev/sda9: UUID="7c9e1deb-a067-439b-af4b-ebe15ff3f528" TYPE="ext4" 
/dev/sda11: LABEL="11.10_07Dec11_v2" UUID="74a1391b-7646-4dbd-9a53-9dfe2d206e52" TYPE="ext4" 


```


And this is the RESUTS.txt file. Thanks again!!!



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid c0998a04-7f0f-47c7-a374-4653516f0833 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS Linux release 6.0 
                       (Final) Kernel on an
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         81,920   125,276,626   125,194,707   7 NTFS / exFAT / HPFS
/dev/sda3         125,280,254   617,019,391   491,739,138   5 Extended
/dev/sda5         125,280,256   166,240,255    40,960,000  83 Linux
/dev/sda6         207,204,352   248,164,351    40,960,000  83 Linux
/dev/sda7         166,242,304   207,202,303    40,960,000  83 Linux
/dev/sda8         596,539,392   617,019,391    20,480,000  82 Linux swap / Solaris
/dev/sda9         248,166,400   289,124,351    40,957,952  83 Linux
/dev/sda10        289,126,400   330,086,399    40,960,000  83 Linux
/dev/sda11        330,088,448   371,048,447    40,960,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 2,048,002,047 2,048,000,000  83 Linux
/dev/sdb2       2,048,002,048 3,907,028,991 1,859,026,944   5 Extended
/dev/sdb5       2,048,004,096 3,072,004,095 1,024,000,000  83 Linux
/dev/sdb6       3,072,006,144 3,907,028,991   835,022,848  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda10       82017acc-d6db-45ef-a9de-5b909c12efa1   ext4       SYS_BACKUPS
/dev/sda11       74a1391b-7646-4dbd-9a53-9dfe2d206e52   ext4       11.10_07Dec11_v2
/dev/sda2        A0888EEC888EC070                       ntfs       OS_MSWIN
/dev/sda5        edc69754-7af9-4df6-86ef-8d5ebba96d20   ext4       _CentOS-6.0-x86_
/dev/sda6        11311fdc-b9ad-47ca-953c-5d2a0dd65b4f   ext4       11.10.01Nov11
/dev/sda7        b4dcab56-fe5d-4931-a1d7-a27fc476136d   ext4       11.10.02Dec11
/dev/sda8        d5fe0a97-baa8-47f5-9703-dd510bd94425   swap       
/dev/sda9        7c9e1deb-a067-439b-af4b-ebe15ff3f528   ext4       
/dev/sdb1        642fcc4c-eb6d-4225-a83e-86c61e4daf28   ext2       MyHome
/dev/sdb5        a3084ee6-9c95-40fc-8944-3599bca69f43   ext2       EXTRA
/dev/sdb6        12043f13-e9fa-444d-b164-6f119c4cfc6f   ext2       BACKUPS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /mnt/dev                 none       (rw,bind)
/dev/sda11       /mnt                     ext4       (rw)
/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

========================== sda5/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/vmlinuz-version ro root=/dev/sda8
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz
hiddenmenu
#
title CentOS Linux (2.6.32-71.29.1.el6.x86_64)
	root (hd0,7)
	kernel /boot/vmlinuz-2.6.32-71.29.1.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.29.1.el6.x86_64.img
#
title CentOS Linux (2.6.32-71.el6.x86_64)
	root (hd0,7)
	kernel /boot/vmlinuz-2.6.32-71.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.el6.x86_64.img
#
title WINDOWS
	rootnoverify (hd0,1)
	chainloader +1
# 
title UBUNTU 11.04
      root (hd0,4)
      kernel /boot/vmlinuz-2.6.38-8-generic ro
root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833
# 
title UBUNTU 11.04
      kernet (hd0,4)/vmlinuz 
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Fri Aug 19 11:39:37 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 /                       ext4    defaults        1 1
UUID=642fcc4c-eb6d-4225-a83e-86c61e4daf28 /home                   ext2    defaults        1 2
# UUID=9223cdbb-fcf8-49de-81c9-3b44c1a2ffb2 swap                    swap    defaults        0 0
# from ubuntu : UUID=8d7f78e8-baed-42d6-b1c3-b207b546d62c none            swap    sw              0       0
UUID=8d7f78e8-baed-42d6-b1c3-b207b546d62c swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.conf                            1
               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               1
               =                boot/initramfs-2.6.32-71.29.1.el6.x86_64.img   1
               =                boot/initramfs-2.6.32-71.el6.x86_64.img        1
               =                boot/vmlinuz-2.6.32-71.29.1.el6.x86_64         1
               =                boot/vmlinuz-2.6.32-71.el6.x86_64              1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
  set locale_dir=($root)/boot/grub/locale
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root A0888EEC888EC070
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro single
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f6dc7250-c45b-4f06-827c-8bd5f7350a6f
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f6dc7250-c45b-4f06-827c-8bd5f7350a6f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f6dc7250-c45b-4f06-827c-8bd5f7350a6f
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f6dc7250-c45b-4f06-827c-8bd5f7350a6f ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "CentOS Linux (2.6.32-71.29.1.el6.x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.29.1.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.29.1.el6.x86_64.img
}
menuentry "CentOS Linux (2.6.32-71.el6.x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.el6.x86_64.img
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root b09d15a0-b792-4a28-9522-be1f1e2e7be7
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=b09d15a0-b792-4a28-9522-be1f1e2e7be7 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root b09d15a0-b792-4a28-9522-be1f1e2e7be7
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=b09d15a0-b792-4a28-9522-be1f1e2e7be7 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information. 02DEC2011
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f /               ext4    errors=remount-ro 0       1
# /dev/sda6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=21897255-47f8-496d-abc8-33ad5663912e none            swap    sw              0       0
# /dev/sda8 none            swap    sw              0       0
#
# This looks like BIG HOME disk
# /dev/sdb1: UUID="642fcc4c-eb6d-4225-a83e-86c61e4daf28" TYPE="ext2"
# UUID=642fcc4c-eb6d-4225-a83e-86c61e4daf28 /home ext2 defaults 0 0 
/dev/sdb1 /home ext2 defaults 0 0 
#
# ---------------------------------------------------------------------------------------------
# 
# 02DEC2011
# $ sudo blkid
# /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
# /dev/sda2: LABEL="OS" UUID="A0888EEC888EC070" TYPE="ntfs" 
# /dev/sda5: UUID="c0998a04-7f0f-47c7-a374-4653516f0833" TYPE="ext4" 
# /dev/sda6: UUID="8d7f78e8-baed-42d6-b1c3-b207b546d62c" TYPE="swap" 
# /dev/sda7: UUID="f6dc7250-c45b-4f06-827c-8bd5f7350a6f" TYPE="ext4" 
# /dev/sda8: LABEL="_CentOS-6.0-x86_" UUID="edc69754-7af9-4df6-86ef-8d5ebba96d20" TYPE="ext4" 
# /dev/sda9: UUID="11311fdc-b9ad-47ca-953c-5d2a0dd65b4f" TYPE="ext4" 
# /dev/sda10: UUID="b4dcab56-fe5d-4931-a1d7-a27fc476136d" TYPE="ext4" 
# /dev/sdb1: UUID="642fcc4c-eb6d-4225-a83e-86c61e4daf28" TYPE="ext2" 
# /dev/sdb5: UUID="a3084ee6-9c95-40fc-8944-3599bca69f43" TYPE="ext2" 
# /dev/sdb6: UUID="12043f13-e9fa-444d-b164-6f119c4cfc6f" TYPE="ext2"
#
#
# 02DEC2011
# $ df
# Filesystem           1K-blocks      Used Available Use% Mounted on
# /dev/sda2             62597348  48216688  14380660  78% /media/OS
# /dev/sda5             28327932   5994276  20894640  23% /media/c0998a04-7f0f-47c7-a374-4653516f0833
# /dev/sda7             21083372  10100440   9911932  51% /media/f6dc7250-c45b-4f06-827c-8bd5f7350a6f
# /dev/sda8             40323792   4833296  35080940  13% /media/_CentOS-6.0-x86_
# /dev/sda9            113454752   6423968 101267560   6% /
# /dev/sda10            28829692   2626608  24738612  10% /media/b4dcab56-fe5d-4931-a1d7-a27fc476136d
# udev                   1954756        12   1954744   1% /dev
# tmpfs                   785068       816    784252   1% /run
# none                      5120         0      5120   0% /run/lock
# none                   1962668       300   1962368   1% /run/shm
# /dev/sdb1            1007931684 501333028 455398656  53% /media/642fcc4c-eb6d-4225-a83e-86c61e4daf28
# /dev/sdb5            503964904     71520 478293384   1% /media/a3084ee6-9c95-40fc-8944-3599bca69f43
# /dev/sdb6            410959136 206854664 183228904  54% /media/12043f13-e9fa-444d-b164-6f119c4cfc6f
#
#
# TO BE REMOVED : 
# sda5 , sda7 , sda10 if doesn reboot
#
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic              79
               =                boot/vmlinuz-3.0.0-12-generic                 10
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                   10

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos10)'
  search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
  set locale_dir=($root)/boot/grub/locale
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root A0888EEC888EC070
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro single
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root c0998a04-7f0f-47c7-a374-4653516f0833
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0998a04-7f0f-47c7-a374-4653516f0833 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f6dc7250-c45b-4f06-827c-8bd5f7350a6f
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f6dc7250-c45b-4f06-827c-8bd5f7350a6f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root f6dc7250-c45b-4f06-827c-8bd5f7350a6f
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=f6dc7250-c45b-4f06-827c-8bd5f7350a6f ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "CentOS Linux (2.6.32-71.29.1.el6.x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.29.1.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.29.1.el6.x86_64.img
}
menuentry "CentOS Linux (2.6.32-71.el6.x86_64) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.el6.x86_64.img
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=642fcc4c-eb6d-4225-a83e-86c61e4daf28 /home           ext2    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=8d7f78e8-baed-42d6-b1c3-b207b546d62c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos9)'
  search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
  set locale_dir=($root)/boot/grub/locale
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set=root 7c9e1deb-a067-439b-af4b-ebe15ff3f528
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root A0888EEC888EC070
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "CentOS Linux (2.6.32-71.29.1.el6.x86_64) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.29.1.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.29.1.el6.x86_64.img
}
menuentry "CentOS Linux (2.6.32-71.el6.x86_64) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.el6.x86_64.img
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=7c9e1deb-a067-439b-af4b-ebe15ff3f528 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d5fe0a97-baa8-47f5-9703-dd510bd94425 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================== sda11/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos11)'
  search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
  set locale_dir=($root)/boot/grub/locale
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=74a1391b-7646-4dbd-9a53-9dfe2d206e52 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=74a1391b-7646-4dbd-9a53-9dfe2d206e52 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=74a1391b-7646-4dbd-9a53-9dfe2d206e52 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=74a1391b-7646-4dbd-9a53-9dfe2d206e52 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set=root 74a1391b-7646-4dbd-9a53-9dfe2d206e52
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root A0888EEC888EC070
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "CentOS Linux (2.6.32-71.29.1.el6.x86_64) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.29.1.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.29.1.el6.x86_64.img
}
menuentry "CentOS Linux (2.6.32-71.el6.x86_64) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root edc69754-7af9-4df6-86ef-8d5ebba96d20
	linux /boot/vmlinuz-2.6.32-71.el6.x86_64 ro root=UUID=edc69754-7af9-4df6-86ef-8d5ebba96d20 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us-acentos crashkernel=auto rhgb quiet
	initrd /boot/initramfs-2.6.32-71.el6.x86_64.img
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 11311fdc-b9ad-47ca-953c-5d2a0dd65b4f
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11311fdc-b9ad-47ca-953c-5d2a0dd65b4f ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root b4dcab56-fe5d-4931-a1d7-a27fc476136d
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=b4dcab56-fe5d-4931-a1d7-a27fc476136d ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=74a1391b-7646-4dbd-9a53-9dfe2d206e52 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=d5fe0a97-baa8-47f5-9703-dd510bd94425 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by darkod on 2011-12-08
Are you actually trying to put grub2 from sda11 on the MBR, or keep the grub2 from sda9 that is there currently (under assumption grub2 you are using is from sda9)?

In case you want to keep the current grub, you just boot your sda9 install and in terminal do:
sudo update-grub

That should locate the newly cloned partition with correct UUID etc. Not sure if you need to do something else after the cloning.

Since you are adding the cloned partition, not actually replacing your main root, you shouldn't need to do much except run update-grub.

---

### Post by thegreeneyes on 2011-12-08
Hi Darko, Hi oldfred.

Darko, I was just going to answer you "I already tried that", but ... I don't know why, I decided to try again, not making any additional changes but those already mentioned of the UUID redefinition and convenient changes in fstab, and ... of course, it worked!!!

I do not understand what happened in between, but ... I will move on.

Thanks again!!!

tge

PS) I remember the old joke of the IT guy suggesting to turn the power off and power the car on again just to check if the problem still is there... ;-)

---

### Post by oldfred on 2011-12-08
Glad you got it working. 

It does look like the grub in sdb refers to a UUID that does not exist, and your Centos has in its fstab a swap UUID that does not exist. I did not throughly check all settings.

I cannot tell you how many times, a power off/on, reboot or check of power cords has solved problems. I cannot open the case of my system without bumping something and invariably I have to recheck every connector to make sure it is tight.:)

---

### Post by thegreeneyes on 2011-12-19
I have found the right procedure to update grub after having cloned with clonezilla live CD, from one partition to another. My current system is UBUNTU 11.10 

1) Initial situation : Working System on partition sda3, empty partition on sda6.
2) Boot with Clonezilla Live CD, follow the screens with defaults, only choose "Partition to Partition" cloning, and fill sda6 as a clone of sda3. When the process ends reboot.
3) Login to sda3

4) find out UUIDs of the disks using 

> sudo blkid

you will notice sda3 and sda6 have the same UUID, you must modify UUID for sda6. You can do it typing

> uuidgen
> sudo tune2fs /dev/sda6 -U enter-the-new-UUID-just-generated

you can verify UUID changed typing again

> sudo blkid

5) now you must correct all the files in sda6 so that grub works ok when booting from that partition. Follow these steps:

> sudo mount /dev/sda6 /mnt
> sudo mount -o bind /dev /mnt/dev
> sudo mount -o bind /proc /mnt/proc
> sudo mount -o bind /sys /mnt/sys
> sudo chroot /mnt bash
# sudo update-grub
# exit
> sudo umount /mnt/dev
> sudo umount /mnt/proc
> sudo umount /mnt/sys
> sudo umount /mnt

6) now you can upgrade the local brub, typing

> sudo update-grub

7) et voila!!! you can reboot now, and booting from sda6 should be ok.

LAST COMMENT/SUGGESTION : remember to follow all these steps making use of very much good luck, otherwise, anything else could happen. ;-)

---

