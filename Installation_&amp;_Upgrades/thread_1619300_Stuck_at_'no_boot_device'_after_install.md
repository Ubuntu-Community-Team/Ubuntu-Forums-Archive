---
title: "Stuck at 'no boot device' after install"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by paulus333 on 2010-11-11
Today I received my brand new PC. Since I'm happy with Ubuntu 10.04 on my old PC I also wanted to install the 64 bit version of 10.04.1 on my new PC (i7 950, Intel DX58SQ, WD 2TB). No problem installing but, at restart, I get the BIOS message 'no boot device'. Tried everything, reinstalled GRUB, changed the BIOS settings to 'legacy' instead of 'native' but nothing works. 

Even deleted all partitions (BIOS, LINUX data, SWAP) on the harddisk with GParted and formatted and re-installed using the entire disk. Still nothing. I definitely need help. Somebody?

---

### Post by oldfred on 2010-11-11
Welcome to the forums.

Some older BIOS (often Intel) required a boot flag on a primary partition. 

Some newer systems do not use BIOS but are UEFI and require gpt partitions, or can be set to work as BIOS with MBR partitions. How is your system set up?

---

### Post by paulus333 on 2010-11-12
Thanks! I've been digging through my BIOS settings and I noticed that UEFI was disabled. Didn't know what it was anyway. Perhaps I should just try this setting and see what happens.

---

### Post by oldfred on 2010-11-12
Most of us still have BIOS and MBR. I did convert one drive to gpt to learn about it and it works just fine if set up correctly with BIOS. Do not have a new motherboard with UEFI to learn about that yet.

When you say you deleted the bios partition that may have been the efi or gpt boot partition that now it is asking for.

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)

[http://ubuntuforums.org/showthread.php?t=1566046&highlight=efi](http://ubuntuforums.org/showthread.php?t=1566046&highlight=efi)

---

### Post by paulus333 on 2010-11-12
My drive is GPT but that was not on purpose. No clue how that happened. I've tried a couple of things now but nothing worked. Last attempt was:

GRUB2 provides the ability to boot from GPT in both BIOS based systems  and UEFI based systems. All partition defining commands remain the same (  like (hd0,8) ). Just load the **part_gpt** grub2 module from grub2 shell or include **"insmod part_gpt"** line before **"set root="** line in **grub.cfg**  file. Usually grub-probe will automatically add this module to core.img  or grub.efi file if it detects the HDD to be using GPT. 

Still nothing.

Also googled for 'Ubuntu' 'Intel DX58SQ', no hits apart from my threads. Am I the first one trying Ubuntu on this motherboard?

Edit: Ah, stupid me I should have googled for DX58SO instead. There are issue with this motherboard!

---

### Post by paulus333 on 2010-11-12
Here's what GParted tells about partitioning:

Partition          File System    Mount Point                                                             Size        Used  Unused Flags
unallocated     unallocated                                                                                    1.00MiB  
/dev/sda1       unknown                                                                                        1.00MiB                    bios_grub
/dev/sda2       ext4              /media/684b7889-8bcd-4f2d-b59a-f0d1a54f7c2c  1.80TiB    31.36GiB 1.77TiB
/dev/sda3       linux-swap                                                                                     17.08GiB 

O.K.?

---

### Post by oldfred on 2010-11-12
That looks just like my 160GB drive (except mine is smaller). The bios_grub partition is not seen by most tools but works just fine. I had no issue booting the gpt drive, but then could not boot windows on another drive, without the extra parameters. With Maverick they have fixed that.

Are you using the MBR mode or the EFI mode?

Separate issue. Do you really just want one very large partition. I prefer several smaller partitions, both for backup size, and if every having to repair or recover it does not take forever. If you have 16GB of memory and plan on hibernating would you need 17GB of swap. With lots of memory swap is rarely if ever used. Some do not use any, but I still suggest a nominal 2GB. Only if running video editing in multiple virtual systems might you need swap.

---

### Post by paulus333 on 2010-11-12
I've disabled UEFI, so I'm going for the old-fashioned approach. Tried UEFI once but that didn't help.
I know the partitions for Ubuntu are way too large but for the first install attempt it should be good enough. Can't get it to boot as it is anyway. Straight after POST it tells me there's no boot device.

---

### Post by oldfred on 2010-11-12
That sounds more like a BIOS error than a grub error. I do not know if you can even add boot flags to gpt partitions as they are not really bootable separately. I would review BIOS settings and see what is there.

---

### Post by oldfred on 2010-11-12
Lets go back and run this to confirm that the install looks ok.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by paulus333 on 2010-11-12
Meanwhile I downloaded SuperGrub2 (bootCD) as a work-around. Ugly but it works. Here's the result (sorry didn't get that thing with #):
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 2000.4 GB, 2000398934016 bytes
255 koppen, 63 sectoren/spoor, 243201 cilinders, totaal 3907029168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 Bios Boot Partition
/dev/sda2           4,096 3,871,205,375 3,871,201,280 Linux or Data
/dev/sda3   3,871,205,376 3,907,028,991    35,823,616 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Schijf /dev/sdb: 8086 MB, 8086617600 bytes
255 koppen, 63 sectoren/spoor, 983 cilinders, totaal 15794175 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,794,174    15,794,112   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        f7fc39e7-1c1a-448d-aebc-c82a45e4ce90   ext4                                     
/dev/sda3        34493334-8f5f-460e-9014-b64cfcedaed2   swap                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        3C19-422F                              vfat       ADATA8GB                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/ADATA8GB          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
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
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, met Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f7fc39e7-1c1a-448d-aebc-c82a45e4ce90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-25-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
    echo    'Linux 2.6.32-25-generic laden ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f7fc39e7-1c1a-448d-aebc-c82a45e4ce90 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f7fc39e7-1c1a-448d-aebc-c82a45e4ce90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-24-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
    echo    'Linux 2.6.32-24-generic laden ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f7fc39e7-1c1a-448d-aebc-c82a45e4ce90 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f7fc39e7-1c1a-448d-aebc-c82a45e4ce90
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f7fc39e7-1c1a-448d-aebc-c82a45e4ce90 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=34493334-8f5f-460e-9014-b64cfcedaed2 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


1582.8GB: boot/grub/core.img
 635.9GB: boot/grub/grub.cfg
1582.9GB: boot/initrd.img-2.6.32-24-generic
1582.9GB: boot/initrd.img-2.6.32-25-generic
1582.8GB: boot/vmlinuz-2.6.32-24-generic
1582.8GB: boot/vmlinuz-2.6.32-25-generic
1582.9GB: initrd.img
1582.9GB: initrd.img.old
1582.8GB: vmlinuz
1582.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2f 00 20 08  |............/. .|
00000200

```

---

### Post by oldfred on 2010-11-12
the script does not parse the BIOS boot partition so it does not see part of grub. It looks ok.

If super grub is letting you boot, try reinstalling grub from inside your install.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by paulus333 on 2010-11-12
Sorry, didn't do the trick. However, there's a difference now: the message 'no boot device' is gone. Now I only get a blinking cursor. Not really an improvement. At least it did do something.

---

### Post by oldfred on 2010-11-12
That's after grub. It normally does that for a while. On mine it is about 20sec. One user waited 30 minutes and then it booted.

Since you have only one system grub does not normally show the menu. You have to hold the shift key down from BIOS until menu to get the menu.

Did system fully boot from supergrub? It may be adding additional boot parameters.

I have nvidia and have to use this.
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by paulus333 on 2010-11-12
The annoying message about the missing bootdevice is back. Because I restarted with SuperGrub??? So, there's nothing I can do holding 'e'. 
By grabbing the system's grub.cfg with SuperGrub the PC starts flawless.

---

### Post by srs5694 on 2010-11-12
On my GPT-only system, the Boot Info Script *does* correctly identify the presence of the core.img data in the BIOS Boot Partition:

```

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 976768065 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sda and looks on partition #2 for /grub.
...
/dev/sda5     976,768,065   976,768,464           400 Bios Boot Partition

```

Thus, comparing to your own system, it appears to me that GRUB is not correctly installed. I recommend booting using Super GRUB 2 Disk and then typing "sudo grub-install" at a shell prompt. That *should* get GRUB properly installed. (You can try using the Boot Info Script to check the results, or reboot and hope the system boots.)

One other comment: Some Intel BIOSes won't boot GPT disks unless the disk is modified to violate the GPT standard in a minor way. (This is highly ironic, since Intel invented GPT.) For details of this and other BIOS/GPT problems, see [this page](http://www.rodsbooks.com/gdisk/bios.html) of mine. The solution is to use Linux fdisk (or some other tool) to mark the EFI GPT (type-0xEE) partition in the MBR as active (aka bootable). This change makes the BIOS happy and lets it continue the boot process, which it normally halts if it can't find an MBR partition marked as bootable. This change violates the GPT specification, but only in the most minor way. I don't know of any OS or utility that reacts badly to this change, so you shouldn't hesitate to make it.

---

### Post by oldfred on 2010-11-12
My test gpt drive does not show the grub correctly.

 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 34 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34        16,064        16,031 Bios Boot Partition

If I directly boot sdb it boots just fine. Sector 34 is where grub should be, but script has not found it. 

I am still using version 055, so unless some changes were made but not a version change it should be the same. Or it could be the tools used have been updated. My results.txt is probably from Lucid, but my install on sdb is now Maverick. It will be a few days before I can confirm that running from Maverick is different or not.

---

### Post by paulus333 on 2010-11-13
I really have to dig into this GPT thing. For the time being: would it be wise to update the bios to the latest version? The BIOS version I've got now is one year old.

---

