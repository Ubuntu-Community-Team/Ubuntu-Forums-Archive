---
title: "Windows 7 not load on grub"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by jerguy1928 on 2011-09-18
I recently switched my ubuntu over from wubi to an actual partition. however, when using grub to boot windows 7, the screen goes dark for a second and goes right back to the main grub menu.

---

### Post by Rubi1200 on 2011-09-18
Hi,
please post the full specifications for the computer, especially RAM and graphics card.

I also recommend you post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by jerguy1928 on 2011-09-18
Alright here is the output:
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 441572840 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       610,469       610,407  de Dell Utility
/dev/sda2    *        610,470    15,229,619    14,619,150   7 NTFS / exFAT / HPFS
/dev/sda3          15,229,620   332,238,472   317,008,853   7 NTFS / exFAT / HPFS
/dev/sda4         332,238,846   488,396,799   156,157,954   5 Extended
/dev/sda5         332,238,848   480,090,111   147,851,264  83 Linux
/dev/sda6         480,092,160   488,396,799     8,304,640  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        BA2A08D42A088F95                       ntfs       RECOVERY
/dev/sda3        BA2E0AEA2E0AA00D                       ntfs       OS
/dev/sda5        620519ea-f939-427d-831a-ed7c19e59f3c   ext4       
/dev/sda6        3a9cb65e-c5ef-48a8-8238-42054b69d33a   swap       
/dev/sdc1        A0E04200E041DD62                       ntfs       Jeremy's External Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/Jeremy's External Drive fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=620519ea-f939-427d-831a-ed7c19e59f3c ro   
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=620519ea-f939-427d-831a-ed7c19e59f3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=620519ea-f939-427d-831a-ed7c19e59f3c ro   
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=620519ea-f939-427d-831a-ed7c19e59f3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 620519ea-f939-427d-831a-ed7c19e59f3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root BA2A08D42A088F95
	chainloader +1
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=620519ea-f939-427d-831a-ed7c19e59f3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3a9cb65e-c5ef-48a8-8238-42054b69d33a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 210.558364868 = 226.085322752  boot/grub/core.img                             1
 192.716228485 = 206.927474688  boot/grub/grub.cfg                             1
 164.468635559 = 176.596852736  boot/initrd.img-2.6.38-11-generic              2
 160.134765625 = 171.943395328  boot/initrd.img-2.6.38-8-generic               2
 159.451484680 = 171.209728000  boot/vmlinuz-2.6.38-11-generic                 1
 210.556644440 = 226.083475456  boot/vmlinuz-2.6.38-8-generic                  1
 164.468635559 = 176.596852736  initrd.img                                     2
 160.134765625 = 171.943395328  initrd.img.old                                 2
 159.451484680 = 171.209728000  vmlinuz                                        1
 210.556644440 = 226.083475456  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  31 2d 30 38 2d 31 33 20  31 36 3a 31 33 3a 31 31  |1-08-13 16:13:11|
00000010  2c 20 49 6e 66 6f 20 20  20 20 20 20 20 20 20 20  |, Info          |
00000020  20 20 20 20 20 20 20 20  43 42 53 20 20 20 20 41  |        CBS    A|
00000030  70 70 6c 3a 20 64 65 74  65 63 74 20 50 61 72 65  |ppl: detect Pare|
00000040  6e 74 2c 20 50 61 63 6b  61 67 65 3a 20 50 61 63  |nt, Package: Pac|
00000050  6b 61 67 65 5f 66 6f 72  5f 4b 42 32 35 31 32 37  |kage_for_KB25127|
00000060  31 35 7e 33 31 62 66 33  38 35 36 61 64 33 36 34  |15~31bf3856ad364|
00000070  65 33 35 7e 61 6d 64 36  34 7e 7e 36 2e 31 2e 31  |e35~amd64~~6.1.1|
00000080  2e 31 2c 20 50 61 72 65  6e 74 3a 20 4d 69 63 72  |.1, Parent: Micr|
00000090  6f 73 6f 66 74 2d 57 69  6e 64 6f 77 73 2d 52 65  |osoft-Windows-Re|
000000a0  6d 6f 74 65 53 65 72 76  65 72 41 64 6d 69 6e 69  |moteServerAdmini|
000000b0  73 74 72 61 74 69 6f 6e  54 6f 6f 6c 73 2d 50 61  |strationTools-Pa|
000000c0  63 6b 61 67 65 7e 33 31  62 66 33 38 35 36 61 64  |ckage~31bf3856ad|
000000d0  33 36 34 65 33 35 7e 61  6d 64 36 34 7e 74 68 2d  |364e35~amd64~th-|
000000e0  54 48 7e 36 2e 31 2e 37  36 30 30 2e 31 36 33 38  |TH~6.1.7600.1638|
000000f0  35 2c 20 44 69 73 70 6f  73 69 74 69 6f 6e 20 3d  |5, Disposition =|
00000100  20 44 65 74 65 63 74 2c  20 56 65 72 73 69 6f 6e  | Detect, Version|
00000110  43 6f 6d 70 3a 20 45 51  2c 20 53 65 72 76 69 63  |Comp: EQ, Servic|
00000120  65 43 6f 6d 70 3a 20 45  51 2c 20 42 75 69 6c 64  |eComp: EQ, Build|
00000130  43 6f 6d 70 3a 20 45 51  2c 20 44 69 73 74 72 69  |Comp: EQ, Distri|
00000140  62 75 74 69 6f 6e 43 6f  6d 70 3a 20 47 45 2c 20  |butionComp: GE, |
00000150  52 65 76 69 73 69 6f 6e  43 6f 6d 70 3a 20 47 45  |RevisionComp: GE|
00000160  2c 20 45 78 69 73 74 3a  20 70 72 65 73 65 6e 74  |, Exist: present|
00000170  0d 0a 32 30 31 31 2d 30  38 2d 31 33 20 31 36 3a  |..2011-08-13 16:|
00000180  31 33 3a 31 31 2c 20 49  6e 66 6f 20 20 20 20 20  |13:11, Info     |
00000190  20 20 20 20 20 20 20 20  20 20 20 20 20 43 42 53  |             CBS|
000001a0  20 20 20 20 41 70 70 6c  3a 20 64 65 74 65 63 74  |    Appl: detect|
000001b0  50 61 72 65 6e 74 3a 20  70 61 63 6b 61 67 00 fe  |Parent: packag..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 d0 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  d0 08 00 c0 7e 00 00 00  |............~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Rubi1200 on 2011-09-18
Reinstalling GRUB should fix the problem. Make sure you install to the MBR of the drive and not to the partition.
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Once back in Ubuntu, run this to pick up the Windows install:

```
sudo update-grub
```

---

### Post by bcbc on 2011-09-19
you installed grub to the windows partition:
> sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 441572840 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.

??? Grub fixed this problem a while back - so it must be a regression. Unless you forced it and did it manually i.e. grub-install --force /dev/xxxx

Anyway - you can fix it with a windows repair cd (bootrec.exe /fixboot) or you can use testdisk which I understand is easier: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Do that after reinstalling grub as Rubi1200 suggested, or it will just boot Windows/wubi again.

---

### Post by rpk94 on 2011-09-19
I'm having same problem, i installed ubuntu 11.04 through wubi and  yesterday installed windows 7 (i had xp when i installed ubuntu) Now no  matter what i do, i can't get grub. I am a total beginner. so please be  patient with me and it would help if you gave me step bystep  instructions. I'll include a copy of my boot report.

[http://paste.ubuntu.com/692741/](http://paste.ubuntu.com/692741/)

---

### Post by bcbc on 2011-09-19
> **rpk94 said:**
> I'm having same problem, i installed ubuntu 11.04 through wubi and  yesterday installed windows 7 (i had xp when i installed ubuntu) Now no  matter what i do, i can't get grub. I am a total beginner. so please be  patient with me and it would help if you gave me step bystep  instructions. I'll include a copy of my boot report.

[http://paste.ubuntu.com/692741/](http://paste.ubuntu.com/692741/)

Your problem is not the same - you should create a new thread. But basically you need to add an entry to your BCD that points at \ubuntu\winboot\wubildr.mbr

You can use easybcd (i've never used it and would personally just manually use bcdedit, but I don't have the commands for that on hand): [http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

---

### Post by jerguy1928 on 2011-09-19
> **Rubi1200 said:**
> Reinstalling GRUB should fix the problem. Make sure you install to the MBR of the drive and not to the partition.
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Once back in Ubuntu, run this to pick up the Windows install:

```
sudo update-grub
```
So I need to boot from a live CD, try Ubuntu, and run that code in terminal, update grub, and then i will be OK?

---

### Post by Rubi1200 on 2011-09-19
Yes, but make sure to run the update command back in Ubuntu.

Also refer to the post by bcbc regarding the Windows boot sector.

Let us know how you get on.

---

### Post by jerguy1928 on 2011-09-24
> **Rubi1200 said:**
> Yes, but make sure to run the update command back in Ubuntu.

Also refer to the post by bcbc regarding the Windows boot sector.

Let us know how you get on.

can't i just run the commands in my ubuntu partition, do i have to run the commands from a live cd?

---

### Post by oldfred on 2011-09-24
You are actually booting due to two errors.

Your Windows boot loader is like a chainload that it just jumps to a partition to boot. It is jumping to the partition with the boot flag and happens to be where you have grub2's boot loader installed. 

If you are in Ubuntu you can just run this to install the grub2 boot loader to the MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
sudo update-grub

Then to get Windows to work you have to repair the Window's partition boot sector that has grub2' s boot loader back to a Windows NTFS partition with its links to Windows boot.

See above post by bcbc. If the backup is valid it is the easiest way. If not you have to use a Windows repair CD.

Then in Ubuntu rerun the 
sudo update-grub

---

### Post by Hakunka-Matata on 2011-09-24
post# 8 > **jerguy1928 said:**
> So I need to boot from a live CD, try Ubuntu, and run that code in terminal, _**update grub**_, and then i will be OK?

No, well ... half & half - you do not run **update-grub** until you have rebooted back into regular (from HDD) ubuntu.  
**Edit:   **from Rubi1200 post# 4: "Once back in Ubuntu, run this to pick up the Windows install:": as he says.  It's OK it run update-grub whilst still running off liveCD but you won't pickup Windows in the Grub menu until you reboot to your normal system and run update-grub again.  I've confused myself now!

---

### Post by oldfred on 2011-09-24
If you are in the liveCD you have to run Rubi1200's commands. If you are in your install on the hard drive you just need to reinstall grub with the command I posted. 

You still have to run testdisk or Windows repairCD to fix Windows as bcbc posted.

After each update and after you are in your install of Ubuntu on the hard drive
sudo update-grub

---

### Post by jerguy1928 on 2011-09-25
Alright after decoding what you guys said, here is what i did.
1.(in Ubuntu partition) installed grub and updated grub)
2.(in Ubuntu partition) ran testdisk, it sad i have a bad backup boot sector and use fixboot on windows CD
3.(with windows 7 CD)went to repair options from disk and a pop-up appears asking if i wanted to fix my start-up, i chose yes.
4.(in Ubuntu partition)after fixing the boot, ran update grub, and checked testdisk for hahas to see if anything was changed, nothing changed it still said bad backup boot sector.
5.(in grub startup) chose windows to see if anything had happened, a little _ kept flashing and for 20 minutes nothing happened so i turned it off.
What should i do now?

---

### Post by oldfred on 2011-09-25
If you did auto repair in Windows that only runs one fix. You have to run the auto repair 3 times at least and then it will also write the Windows boot loader to the MBR, so you then have to reinstall grub2's boot loader to the MBR from the liveCD.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by jerguy1928 on 2011-09-25
**@oldfred**
Unfortunately, same result. i didn't run the boot repair tool, because you said it wasn't that effective, and i didn't run *bootrec.exe/fixMBR* because I wanted grub. When running the rest of the commands they said they ran successfully, but when the commands are run, some of the output says found 0 windows installations.
So what do I do from here?

---

### Post by oldfred on 2011-09-26
Sometimes the chkdsk & fixboot commands have to be run more than once. Each seems to depend on the other.

Fixboot should return it to a bootable state, but chkdsk also does some things to the NTFS PBR - partition boot sector as well as checking partition.

Until the PBR is fixed Windows will not see its install ever if all the files are in the partition.

---

### Post by maul9999 on 2011-09-26
> **jerguy1928 said:**
> I recently switched my ubuntu over from wubi to an actual partition. however, when using grub to boot windows 7, the screen goes dark for a second and goes right back to the main grub menu.

Try to press F8 many time until you get screen of choose.  It might work.  I do that last time and it work.

---

### Post by jerguy1928 on 2011-09-26
**@oldfred**
I ran the commands several times and even tried the auto fix, it still said no partition found, and it still says error saving to log file status 50

**@maul9999**
i tried pressing F8 in grub boot menu, no luck

What do i do now?

---

### Post by oldfred on 2011-09-27
do you have grub2's boot loader in the MBR? And does that boot ok?

Rerun boot script just to see if Windows PBR looks like a NTFS boot sector or still has grub in it. The windows fixes should have changed it back to NTFS boot sector, so then it can see it to boot.

---

### Post by maul9999 on 2011-09-27
> **oldfred said:**
> do you have grub2's boot loader in the MBR? And does that boot ok?

Rerun boot script just to see if Windows PBR looks like a NTFS boot sector or still has grub in it. The windows fixes should have changed it back to NTFS boot sector, so then it can see it to boot.

Hmm.  I think that CD live might have a way to reinstall GRUB2's boot loader?  I know i did it but that is long ago.

---

### Post by jerguy1928 on 2011-09-27
> **oldfred said:**
> do you have grub2's boot loader in the MBR? And does that boot ok?

Rerun boot script just to see if Windows PBR looks like a NTFS boot sector or still has grub in it. The windows fixes should have changed it back to NTFS boot sector, so then it can see it to boot.
I am a little confused as to what you are saying, but here is the output of the boot info script which might help, i just ran it a minute ago:
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: __________________________________________________________________________

```

---

### Post by bcbc on 2011-09-27
That's not the whole bootinfoscript result. Also, it looks like you are missing /Windows/System32/winload.exe

---

### Post by oldfred on 2011-09-27
Good catch bcbc, it was missing in the first boot script.

I have seen where script does not show it, but users say it is there. I think then the path must be moved/damaged or something else which also causes issues with Windows booting.

sda3 shows Windows 7 in the operating system, but sda2 does not and it is the boot partition. 

Or it seems like there are lots of issues with the Windows install.

---

### Post by jerguy1928 on 2011-10-03
so what sohould i do?

---

### Post by oldfred on 2011-10-03
In sda3 do you have these files & folders and that they are not somewhere else (like you accidentally moved them)

/Boot/BCD
/Windows
/Windows/System32
/Windows/System32/winload.exe

If these are missing you do not have Windows. If somewhere else they were moved, if really there then it may be repairable.

---

### Post by jerguy1928 on 2011-10-03
> **oldfred said:**
> In sda3 do you have these files & folders and that they are not somewhere else (like you accidentally moved them)

/Boot/BCD
/Windows
/Windows/System32
/Windows/System32/winload.exe

If these are missing you do not have Windows. If somewhere else they were moved, if really there then it may be repairable.
The only things missing is Boot/BCD. boot is there but BCD is NOT there.

---

### Post by oldfred on 2011-10-03
Oops, bootmgr & /Boot/BCD are in sda2 as shown in boot info script. 

From a Windows repair CD move active partition flag to sda3 or use gparted in LivecD to move boot flag to sda3. And then run the Windows repairCD. Try chkdsk first and run it until there are no errors. Then run the other fixes.

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by jerguy1928 on 2011-10-31
> **oldfred said:**
> Oops, bootmgr & /Boot/BCD are in sda2 as shown in boot info script. 

From a Windows repair CD move active partition flag to sda3 or use gparted in LivecD to move boot flag to sda3. And then run the Windows repairCD. Try chkdsk first and run it until there are no errors. Then run the other fixes.

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)
Sorry i haven't responded in a while, but i don't quite understand how to move active partition flag, could you please explain, thanks.

---

### Post by oldfred on 2011-11-01
I prefer gparted or Disk Utility, but from command line:
set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda
or
parted /dev/sdb set 3 boot on
OR:
    #make a partition active 
    parttool (hd0,3) boot+


Or use gparted, click on partition, right click on flags set boot flag
Or use Disk Utility, click on partition, edit partition, edit flags

there is also a way in Windows from the repair command line, but I do not have that handy. Windows calls it active partition.

---

### Post by jerguy1928 on 2011-11-01
> **oldfred said:**
> I prefer gparted or Disk Utility, but from command line:
set boot flag on for sda3 (off on others)
```
sudo sfdisk -A3 /dev/sda
```
or
parted /dev/sdb set 3 boot on
OR:
    #make a partition active 
    parttool (hd0,3) boot+


Or use gparted, click on partition, right click on flags set boot flag
Or use Disk Utility, click on partition, edit partition, edit flags

there is also a way in Windows from the repair command line, but I do not have that handy. Windows calls it active partition.
Okay so i ran```
sudo sfdisk -A3 /dev/sda
``` in terminal and it said warning, linux and dos will understand the filesystem differently.
So i went and ran chkdsk a bunch of times, until no errors.
I ran the previous commands like fixboot and scan os and rebuild bcd, all said they were sucessful. So i tried from the windows repair disc the startup repair option to automatically fix,it said everything was okay, but for one thing it said :**Root cause found: Boot manager is missing or corrupt.**
So i went to restart my computer, chose windows 7 in Grub, and it said this:
error: unknown filesystem
grub rescue> _



So whats next?

---

### Post by oldfred on 2011-11-01
Well bootmgr was in sda2, but we were trying to repair sda3. If not fully repaired the only "bootable" partition was sda2, but sda3 still would have to have the rest of Windows and be fully working. You could try moving boot flag back to sda2. 

How/what is booting? You are booting grub and then with a Windows boot you get grub rescue? That would only be if grub was in the Windows partition.

Repost boot script.

---

### Post by jerguy1928 on 2011-11-01
Alright here is the reposted boot script output
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 412525568 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  sudo bash ~/Desktop/boot_info_script.sh

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       610,469       610,407  de Dell Utility
/dev/sda2             610,470    15,229,619    14,619,150   7 NTFS / exFAT / HPFS
/dev/sda3    *     15,229,620   332,238,472   317,008,853   7 NTFS / exFAT / HPFS
/dev/sda4         332,238,846   488,396,799   156,157,954   5 Extended
/dev/sda5         480,092,160   488,396,799     8,304,640  82 Linux swap / Solaris
/dev/sda6         332,238,848   471,785,471   139,546,624  83 Linux
/dev/sda7         471,787,520   480,086,015     8,298,496  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        BA2A08D42A088F95                       ntfs       RECOVERY
/dev/sda3        BA2E0AEA2E0AA00D                       ntfs       OS
/dev/sda5        3a9cb65e-c5ef-48a8-8238-42054b69d33a   swap       
/dev/sda6        b1442df2-0478-4844-b458-61ebdf0cb7f2   ext4       
/dev/sda7        be69288d-ece3-4881-b531-0f7c1ca8b371   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###sudo bash ~/Desktop/boot_info_script.sh
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=b1442df2-0478-4844-b458-61ebdf0cb7f2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=b1442df2-0478-4844-b458-61ebdf0cb7f2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=b1442df2-0478-4844-b458-61ebdf0cb7f2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=b1442df2-0478-4844-b458-61ebdf0cb7f2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b1442df2-0478-4844-b458-61ebdf0cb7f2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b1442df2-0478-4844-b458-61ebdf0cb7f2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root b1442df2-0478-4844-b458-61ebdf0cb7f2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root BA2A08D42A088F95
	chainloader +1
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
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=be69288d-ece3-4881-b531-0f7c1ca8b371 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 166.582424164 = 178.866515968  boot/grub/core.img                             1
 182.862327576 = 196.346929152  boot/grub/grub.cfg                             1
 160.057483673 = 171.860414464  boot/initrd.img-2.6.38-11-generic              2
 164.290462494 = 176.405540864  boot/initrd.img-2.6.38-12-generic              2
 160.134765625 = 171.943395328  boot/initrd.img-2.6.38-8-generic               2
 160.646797180 = 172.493185024  boot/vmlinuz-2.6.38-11-generic                 1
 164.701484680 = 176.846872576  boot/vmlinuz-2.6.38-12-generic                 1
 166.577072144 = 178.860769280  boot/vmlinuz-2.6.38-8-generic                  1
 164.290462494 = 176.405540864  initrd.img                                     2
 160.057483673 = 171.860414464  initrd.img.old                                 2
 164.701484680 = 176.846872576  vmlinuz                                        1
 160.646797180 = 172.493185024  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  31 2d 30 38 2d 31 33 20  31 36 3a 31 33 3a 31 31  |1-08-13 16:13:11|
00000010  2c 20 49 6e 66 6f 20 20  20 20 20 20 20 20 20 20  |, Info          |
00000020  20 20 20 20 20 20 20 20  43 42 53 20 20 20 20 41  |        CBS    A|
00000030  70 70 6c 3a 20 64 65 74  65 63 74 20 50 61 72 65  |ppl: detect Pare|
00000040  6e 74 2c 20 50 61 63 6b  61 67 65 3a 20 50 61 63  |nt, Package: Pac|
00000050  6b 61 67 65 5f 66 6f 72  5f 4b 42 32 35 31 32 37  |kage_for_KB25127|
00000060  31 35 7e 33 31 62 66 33  38 35 36 61 64 33 36 34  |15~31bf3856ad364|
00000070  65 33 35 7e 61 6d 64 36  34 7e 7e 36 2e 31 2e 31  |e35~amd64~~6.1.1|
00000080  2e 31 2c 20 50 61 72 65  6e 74 3a 20 4d 69 63 72  |.1, Parent: Micr|
00000090  6f 73 6f 66 74 2d 57 69  6e 64 6f 77 73 2d 52 65  |osoft-Windows-Re|
000000a0  6d 6f 74 65 53 65 72 76  65 72 41 64 6d 69 6e 69  |moteServerAdmini|
000000b0  73 74 72 61 74 69 6f 6e  54 6f 6f 6c 73 2d 50 61  |strationTools-Pa|
000000c0  63 6b 61 67 65 7e 33 31  62 66 33 38 35 36 61 64  |ckage~31bf3856ad|
000000d0  33 36 34 65 33 35 7e 61  6d 64 36 34 7e 74 68 2d  |364e35~amd64~th-|
000000e0  54 48 7e 36 2e 31 2e 37  36 30 30 2e 31 36 33 38  |TH~6.1.7600.1638|
000000f0  35 2c 20 44 69 73 70 6f  73 69 74 69 6f 6e 20 3d  |5, Disposition =|
00000100  20 44 65 74 65 63 74 2c  20 56 65 72 73 69 6f 6e  | Detect, Version|
00000110  43 6f 6d 70 3a 20 45 51  2c 20 53 65 72 76 69 63  |Comp: EQ, Servic|
00000120  65 43 6f 6d 70 3a 20 45  51 2c 20 42 75 69 6c 64  |eComp: EQ, Build|
00000130  43 6f 6d 70 3a 20 45 51  2c 20 44 69 73 74 72 69  |Comp: EQ, Distri|
00000140  62 75 74 69 6f 6e 43 6f  6d 70 3a 20 47 45 2c 20  |butionComp: GE, |
00000150  52 65 76 69 73 69 6f 6e  43 6f 6d 70 3a 20 47 45  |RevisionComp: GE|
00000160  2c 20 45 78 69 73 74 3a  20 70 72 65 73 65 6e 74  |, Exist: present|
00000170  0d 0a 32 30 31 31 2d 30  38 2d 31 33 20 31 36 3a  |..2011-08-13 16:|
00000180  31 33 3a 31 31 2c 20 49  6e 66 6f 20 20 20 20 20  |13:11, Info     |
00000190  20 20 20 20 20 20 20 20  20 20 20 20 20 43 42 53  |             CBS|
000001a0  20 20 20 20 41 70 70 6c  3a 20 64 65 74 65 63 74  |    Appl: detect|
000001b0  50 61 72 65 6e 74 3a 20  70 61 63 6b 61 67 00 fe  |Parent: packag..|
000001c0  ff ff 82 fe ff ff 02 10  d0 08 00 b8 7e 00 00 fe  |............~...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 50 51 08 00 00  |...........PQ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by oldfred on 2011-11-01
How did you get grub2 installed to sda2?

Move boot flag back to sda2.

sudo sfdisk -A2 /dev/sda
NTFS partitions keep a backup of the boot sector. If the backup is valid you can restore it. Or from Windows you have to run repairs on sda2 (after moving boot flag back to sda2).

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by jerguy1928 on 2011-11-01
> **oldfred said:**
> How did you get grub2 installed to sda2?

Move boot flag back to sda2.

sudo sfdisk -A2 /dev/sda
NTFS partitions keep a backup of the boot sector. If the backup is valid you can restore it. Or from Windows you have to run repairs on sda2 (after moving boot flag back to sda2).

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Ran *sudo sfdisk -A2 /dev/sda* and output was:
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Done
```
Rebooted and chose windows 7 from grub and still said:
```
error: unknown filesystem
grub rescue> _

```
So i proceeded to testdisk option. I followed its instructions and the output was:
```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 3 P HPFS - NTFS            948   0  1 20680 226 35  317008853 [OS]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```
After running testdisk I rebooted my computer, but there was another windows 7 seven boot option that wasn't there before in grub. The two options for windows 7 in grub are:
Windows 7(loader)(on /dev/sda2)
Windows 7(loader)(on /dev/sda3)

So I tried each option. The first option gave like it had before:
```
error: unknown filesystem
grub rescue> _

```

However the second option gave something very weird which I don't have symbols to describe(sorry for the poor quality):
[[IMG]http://img847.imageshack.us/img847/5813/downloadnu.jpg[/IMG]](http://imageshack.us/photo/my-images/847/downloadnu.jpg/)

How should I proceed?

---

### Post by oldfred on 2011-11-01
If it was yesterday then it was Halloween!!

Ignore the extended partition on cylinder boundry issue. That has not applied since drives went over 8GB and drives change from cylinders to LBA or large block allocation.

Did you run testdisk on sda2, it looks like you used sda3?

---

### Post by jerguy1928 on 2011-11-02
> **oldfred said:**
> If it was yesterday then it was Halloween!!

Ignore the extended partition on cylinder boundry issue. That has not applied since drives went over 8GB and drives change from cylinders to LBA or large block allocation.

Did you run testdisk on sda2, it looks like you used sda3?
It turns out i was doing that, because that was the partition label Os (corresponding to the windows partition). So i re-ran testdisk on sda 2 and when choosing sda 2 from grub, i just get a blinking cursor and nothing loads.

How should i proceed?

---

### Post by oldfred on 2011-11-02
That could be grub has loaded without seeing the Windows partition and Ubuntu has a Video issue. Grub auto boots without menu when only one system is seen.
If you hold shift key down from BIOS until menu appears, do you get menu?

---

### Post by jerguy1928 on 2011-11-02
> **oldfred said:**
> That could be grub has loaded without seeing the Windows partition and Ubuntu has a Video issue. Grub auto boots without menu when only one system is seen.
If you hold shift key down from BIOS until menu appears, do you get menu?
Assuming I understood your directions correctly, here is what i did:
Went to bios, hit exit and held down shift, eventually there was a screen saying "Grub is loading", and then it went to menu.

---

### Post by oldfred on 2011-11-02
Then if you can get to menu you can try recovery mode. Or edit grub to add nomodeset or other parameters. Sometimes some experimentation is required, othertimes, a setting for your video is all that is  required.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by jerguy1928 on 2011-11-06
> **oldfred said:**
> Then if you can get to menu you can try recovery mode. Or edit grub to add nomodeset or other parameters. Sometimes some experimentation is required, othertimes, a setting for your video is all that is  required.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0
Okay so I tried nomodeset with no luck . the other parameters listed were not relevent to my problem.
I tried the i915.modeset=1 ,and i915.modeset=0, i didn't try the others because they were either regarding x and there is nothing worng with x. and the others you listed i didn't try because i know i have a intel video card.
How should i proceed?

---

### Post by oldfred on 2011-11-06
Are you able to boot into Windows ok now?

Does liveCD video work ok?

What video do you have?

From liveCD:
```

sudo lshw | grep -A 11 display
```

---

### Post by jerguy1928 on 2011-11-06
> **oldfred said:**
> Are you able to boot into Windows ok now?

Does liveCD video work ok?

What video do you have?

From liveCD:
```

sudo lshw | grep -A 11 display
```
windows still does not boot. live cd worked ok.
here is the output from the code:```
*-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f6b00000-f6bfffff

```

---

