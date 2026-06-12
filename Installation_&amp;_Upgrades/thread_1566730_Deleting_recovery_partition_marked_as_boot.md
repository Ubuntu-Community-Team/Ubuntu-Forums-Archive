---
title: "Deleting recovery partition marked as boot?"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2010-09-02
Hello,
I have just bought a new computer and I want to partition it to be dual booting as I have done a few times in the past.

Currently (alternatively, see attached screenshot):
There are three partitions:
/dev/sda1: FAT16 DellUtility (takes very little space and is of no concern)
/dev/sda2: ntfs RECOVERY (takes up 17.58GB and is marked boot)
/dev/sda3: ntfs OS (the rest of the computer, on which windows is currently installed)

Basically, I want to get rid of sda2 and do it like this:

/dev/sda1: Same as before
/dev/sda2: ntfs (will contain windows)
/dev/sda3: FAT32 (shared partition)
/dev/sda4: extended partition
The extended partition would contain an ext logical partition (not sure which one) for Ubuntu and a linux swap partition.


I am wondering if it is safe to delete the current boot partition. I am also not quite clear on when the recovery partition would be used and whether it is really all that necessary (18GB doing nothing seems like a lot to me). Should I make a system recovery media for windows before repartitioning? Also, I am not sure which type of ext partition to use. Finally, I am not sure how big to make the swap space. I think I recall the normal rule being twice the RAM (6GB RAM in my case), but 12GB swap space seems like a lot. Although I do sometimes run memory intensive programs (simulations for research). I normally use other computers for such simulations since they have far more RAM than my computer can possibly have even with a large swap space.

I appreciate advice on any issue here.

---

### Post by wilee-nilee on 2010-09-02
Post the boot script in my signature in code tags as described.

This will let us see the boot files in sda2, and more info.

I don't know if Dell will allow you to get a regular iso/dvd of a install that can be oem activated without all the extra Dell stuff. This would be what I would want, just the  OS. This would allow you to do what you want, much easier.

In the mean time it is advised to do the one time backup, which will restore your computer to purchased state like the recovery.

The thing is your in good shape to dual boot as it is. You would have to shrink the windows partition with its partition manager though. This though may make the recovery hard to activate, maybe not though hard to say.

---

### Post by presence1960 on 2010-09-02
Dell does have the DVD of just an OEM Windows install. You have to call customer support and ask for it, at a charge of course. Just be sure to specify you do not want the DVD to restore the factory image, that you just want to install windows. Tell them your recovery partition is not operational.

---

### Post by EricDallal on 2010-09-02
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    36,944,324    36,864,000   7 HPFS/NTFS
/dev/sda3          36,944,325   976,771,119   939,826,795   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        B278DFC178DF8311                       ntfs       RECOVERY                      
/dev/sda3        BA94E1E794E1A65B                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by wilee-nilee on 2010-09-02
So as far as I know removing the sda2 right now would stop you from booting into Windows, the  **/bootmgr /Boot/BCD** files which are needed to boot are in sda2. 

Others may have other options they know about.

You could using the disk manager in Windows shrink sda3 and leave a open space and install Ubuntu with a auto install in free space, or make a extended partition and put a logical and swap partitions inside. It really depends on what you really want.

---

### Post by EricDallal on 2010-09-02
Is there any way to reclaim that 18GB? Would Gparted be able to move the boot for windows into the partition where the OS is actually installed?

---

### Post by EricDallal on 2010-09-02
To clarify: I was thinking that I could partition the computer as I was planning, then to use the fixboot command as described in [http://gparted.sourceforge.net/faq.php]("http://gparted.sourceforge.net/faq.php") (part 14). The problem is that I'm not exactly sure what this command does ad how to use beyond the vague description provided.

---

### Post by wilee-nilee on 2010-09-02
> **EricDallal said:**
> To clarify: I was thinking that I could partition the computer as I was planning, then to use the fixboot command as described in [http://gparted.sourceforge.net/faq.php]("http://gparted.sourceforge.net/faq.php") (part 14). The problem is that I'm not exactly sure what this command does ad how to use beyond the vague description provided.

If you go to the Windows 7 forums they might have some info on setting up sda3 to be the boot partition. This has to be done fixboot will not fix removing sda2; I think but I could be wrong. I recognize the commands in the link in the last paragraph.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

Yes gparted can be used in building a ntfs for W7 and resizing the partitions. When resizing though you have to untick the round to cylinders in the resize gui. This will hopefully at the most result in a auto chkdsk, otherwise you can set one up.

---

### Post by Mark Phelps on 2010-09-03
You could also try going to the NeoSmart Technology forums and asking your question there.  They make a free product knows as EasyBCD and one of its options allows you to move the boot loader stuff to a different partition, in this case, your Win7 OS partition.

It's a little tricky, so you should go to their forums and seek their advice before you do this.

If you have a restore CD, that is too small to contain an OEM image and most probably, only boots you into WinPE, from which it launches the restore operation -- looking for the image in the Recovery partition.  

You do realize, though, that once you remove the Recovery partition, you will be completely unable to restore your Win7 install -- right?  That partition is so large because it most probably contains an OEM version of a Win7 "image" file.  Once this is gone, you will NOT be able to restore Win7.

---

### Post by garvinrick4 on 2010-09-04
Windows 7 sda1 boot -- sda2 OS -- sda3 Extended --sda4 recovery sda5 thru sda12 logical: HP machine: 
fedora-OpenSuSe installed choosing not to install grub at installation. Why remove recovery sda4 when not over 4 Primarys?

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for (,msdos6)/boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 366506973.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 13 (Goddard) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   256,794,621   256,385,022   7 HPFS/NTFS
/dev/sda3         256,796,670   578,435,054   321,638,385   5 Extended
/dev/sda5         342,955,620   366,506,909    23,551,290  83 Linux
/dev/sda6         256,799,088   279,322,154    22,523,067  83 Linux
/dev/sda7         279,322,218   342,955,619    63,633,402  83 Linux
/dev/sda8         366,506,973   407,954,609    41,447,637   b W95 FAT32
/dev/sda9         407,954,673   429,047,954    21,093,282  83 Linux
/dev/sda10        429,048,018   472,070,024    43,022,007  83 Linux
/dev/sda11        472,072,192   492,910,591    20,838,400  83 Linux
/dev/sda12        492,922,458   513,951,479    21,029,022  83 Linux
/dev/sda4         578,436,390   625,137,344    46,700,955   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="SYSTEM" UUID="C6EECCF3EECCDCB5" TYPE="ntfs" 
sda2: LABEL="OS" UUID="66B0BDBFB0BD95D1" TYPE="ntfs" 
sda5: LABEL="maverick" UUID="10f25c5b-a306-4546-b02f-87a1664b5c05" TYPE="ext4" 
sda6: LABEL="lucid" UUID="d03f894f-94ce-4c00-9c43-19c25f2af12c" TYPE="ext4" 
sda7: LABEL="home" UUID="0f7c5de9-c3b4-4c50-b288-d34e9ef6e119" TYPE="ext4" 
sda8: LABEL="DATA" UUID="267C-BED1" TYPE="vfat" 
sda9: LABEL="redhat" UUID="928df639-e6cf-4c3b-9c17-965a91e60efc" TYPE="ext4" 
sda10: LABEL="netbook" UUID="cbb12bc7-02fe-46b5-b7b0-edf1cc02833d" TYPE="ext4" 
sda11: LABEL="suse" UUID="0f8b5dba-fa33-46e5-ae44-862e454430af" TYPE="ext4" 
sda12: LABEL="kde" UUID="ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f" TYPE="ext4" 
sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rick)
/dev/sda7 on /media/home type ext4 (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux    /boot/vmlinuz-2.6.35-17-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    echo    'Loading Linux 2.6.35-17-generic ...'
    linux    /boot/vmlinuz-2.6.35-17-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 0f8b5dba-fa33-46e5-ae44-862e454430af
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/sda11
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 0f8b5dba-fa33-46e5-ae44-862e454430af
    linux /boot/vmlinux-2.6.34-12-default.gz root=/dev/sda11
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/sda12
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f
    linux /boot/vmlinux-2.6.34-12-default.gz root=/dev/sda12
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.33.6-147.fc13.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.33.6-147.fc13.x86_64.img
}
menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.33.8-149.fc13.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.33.8-149.fc13.x86_64.img
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 175.5GB: boot/grub/core.img
 175.5GB: boot/grub/grub.cfg
 175.5GB: boot/initrd.img-2.6.35-17-generic
 175.5GB: boot/initrd.img-2.6.35-19-generic
 175.5GB: boot/vmlinuz-2.6.35-17-generic
 175.5GB: boot/vmlinuz-2.6.35-19-generic
 175.5GB: initrd.img
 175.5GB: initrd.img.old
 175.5GB: vmlinuz
 175.5GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 0f8b5dba-fa33-46e5-ae44-862e454430af
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/sda11
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 0f8b5dba-fa33-46e5-ae44-862e454430af
    linux /boot/vmlinux-2.6.34-12-default.gz root=/dev/sda11
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/sda12
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f
    linux /boot/vmlinux-2.6.34-12-default.gz root=/dev/sda12
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro quiet splash
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-19-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro single
    initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro quiet splash
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro single
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.33.6-147.fc13.x86_64 root=/dev/sda9
}
menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.33.8-149.fc13.x86_64 root=/dev/sda9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c /               ext4    errors=remount-ro 0       1


=================== sda6: Location of files loaded by Grub: ===================


 131.4GB: boot/grub/core.img
 131.4GB: boot/grub/grub.cfg
 131.4GB: boot/initrd.img-2.6.32-23-generic
 131.4GB: boot/initrd.img-2.6.32-25-generic
 131.4GB: boot/vmlinuz-2.6.32-23-generic
 131.4GB: boot/vmlinuz-2.6.32-25-generic
 131.4GB: initrd.img
 131.4GB: vmlinuz

=============================== sda9/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Fri Jun 25 09:33:30 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=928df639-e6cf-4c3b-9c17-965a91e60efc /                       ext4    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda9: Location of files loaded by Grub: ===================


 208.8GB: boot/vmlinuz-2.6.33.6-147.fc13.x86_64
 208.8GB: boot/vmlinuz-2.6.33.8-149.fc13.x86_64

========================== sda10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 0f8b5dba-fa33-46e5-ae44-862e454430af
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/sda11
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set 0f8b5dba-fa33-46e5-ae44-862e454430af
    linux /boot/vmlinux-2.6.34-12-default.gz root=/dev/sda11
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/sda12
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "openSUSE 11.3 (i586) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set ee959c5d-ed91-4f6f-a8b6-8d9fb73ab89f
    linux /boot/vmlinux-2.6.34-12-default.gz root=/dev/sda12
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro quiet splash
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-17-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro single
    initrd /boot/initrd.img-2.6.35-17-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro quiet splash
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.35-16-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 10f25c5b-a306-4546-b02f-87a1664b5c05
    linux /boot/vmlinuz-2.6.35-16-generic root=UUID=10f25c5b-a306-4546-b02f-87a1664b5c05 ro single
    initrd /boot/initrd.img-2.6.35-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.33.6-147.fc13.x86_64 root=/dev/sda9
}
menuentry "Fedora release 13 (Goddard) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.33.8-149.fc13.x86_64 root=/dev/sda9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d /               ext4    errors=remount-ro 0       1

=================== sda10: Location of files loaded by Grub: ===================


 219.6GB: boot/grub/core.img
 219.6GB: boot/grub/grub.cfg
 219.6GB: boot/initrd.img-2.6.32-24-generic-pae
 219.6GB: boot/vmlinuz-2.6.32-24-generic-pae
 219.6GB: initrd.img
 219.6GB: vmlinuz

=============================== sda11/etc/fstab: ===============================

UUID=0f8b5dba-fa33-46e5-ae44-862e454430af /                    ext4       acl,user_xattr        1 1

proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0


=================== sda11: Location of files loaded by Grub: ===================


 241.7GB: boot/grub/stage2
 241.7GB: boot/initrd
 241.7GB: boot/initrd-2.6.34-12-default
 241.7GB: boot/vmlinuz
 241.7GB: boot/vmlinuz-2.6.34-12-default

=============================== sda12/etc/fstab: ===============================

/dev/disk/by-id/ata-ST9320325AS_5VD1V0B4-part12 /                    ext4       acl,user_xattr        1 1

proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda12: Location of files loaded by Grub: ===================


 252.3GB: boot/grub/stage2
 252.3GB: boot/initrd
 252.3GB: boot/initrd-2.6.34-12-default
 252.3GB: boot/vmlinuz
 252.3GB: boot/vmlinuz-2.6.34-12-default
```

---

### Post by efflandt on 2010-09-04
Dell only provides a drivers and utilities disk and no longer provides system discs.  So you should create the recovery DVD's, do a system backup, and back up any user (data) files you need before tampering with your hard drive.

My system had trouble writing the DVD's to back up the system, and after they replaced my DVD and hard drives, the RECOVERY partition on the replacement drive was empty.  They did not even have recovery discs for my system, so they sent me a Win7 system disc.  Although, apparently the recovery discs I wrote were good and I was able to totally restore the hard drive to factory original (just system backup DVD's continued to be corrupt and fail).

Since I never had trouble writing CD-R's (other than RW), I did not realize until then that DVD+/-R  rarely writes successfully 100% of the time.  So make sure that any DVD's you write actually work.

---

