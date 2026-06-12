---
title: "new 'buntu install - can't boot to windows"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by etheesdad on 2010-06-24
Ive put ubuntu on my desktop machine and now I cant get into windows. 

When I select 'Windows 7' from the bootloader menu, the machine displays a black screen with a blinking cursor at top left

I had a look at some grub editing info, but I cant see the file in /boot/grub so cant even get to it to edit it. sudo gedit /boot/grub/menu.lst just brings up a blank file

```

jim@jimbuntu:/boot/grub$ ls
915resolution.mod            gcry_seed.mod       parttool.lst
acpi.mod                     gcry_serpent.mod    parttool.mod
affs.mod                     gcry_sha1.mod       password.mod
afs_be.mod                   gcry_sha256.mod     password_pbkdf2.mod
afs.mod                      gcry_sha512.mod     pbkdf2.mod
aout.mod                     gcry_tiger.mod      pci.mod
ata.mod                      gcry_twofish.mod    play.mod
ata_pthru.mod                gcry_whirlpool.mod  png.mod
at_keyboard.mod              gettext.mod         probe.mod
befs_be.mod                  gfxmenu.mod         pxeboot.img
befs.mod                     gfxterm.mod         pxecmd.mod
biosdisk.mod                 gptsync.mod         pxe.mod
bitmap.mod                   grldr.img           raid5rec.mod
bitmap_scale.mod             grub.cfg            raid6rec.mod
blocklist.mod                grubenv             raid.mod
boot.img                     gzio.mod            read.mod
boot.mod                     halt.mod            reboot.mod
bsd.mod                      handler.lst         reiserfs.mod
bufio.mod                    handler.mod         relocator.mod
cat.mod                      hashsum.mod         scsi.mod
cdboot.img                   hdparm.mod          search_fs_file.mod
chain.mod                    hello.mod           search_fs_uuid.mod
charset.mod                  help.mod            search_label.mod
cmp.mod                      hexdump.mod         search.mod
command.lst                  hfs.mod             serial.mod
configfile.mod               hfsplus.mod         setjmp.mod
core.img                     iso9660.mod         setpci.mod
cpio.mod                     jfs.mod             sfs.mod
cpuid.mod                    jpeg.mod            sh.mod
crc.mod                      kernel.img          sleep.mod
crypto.lst                   keystatus.mod       tar.mod
crypto.mod                   linux16.mod         terminal.lst
datehook.mod                 linux.mod           terminal.mod
date.mod                     lnxboot.img         terminfo.mod
datetime.mod                 load.cfg            test.mod
device.map                   loadenv.mod         tga.mod
diskboot.img                 locale              trig.mod
dm_nv.mod                    loopback.mod        true.mod
drivemap.mod                 lsmmap.mod          udf.mod
echo.mod                     ls.mod              ufs1.mod
efiemu32.o                   lspci.mod           ufs2.mod
efiemu64.o                   lvm.mod             uhci.mod
efiemu.mod                   mdraid.mod          unicode.pf2
elf.mod                      memdisk.mod         usb_keyboard.mod
example_functional_test.mod  memrw.mod           usb.mod
ext2.mod                     minicmd.mod         usbms.mod
extcmd.mod                   minix.mod           usbtest.mod
fat.mod                      mmap.mod            vbeinfo.mod
font.mod                     moddep.lst          vbe.mod
fshelp.mod                   msdospart.mod       vbetest.mod
fs.lst                       multiboot2.mod      vga.mod
functional_test.mod          multiboot.mod       vga_text.mod
gcry_arcfour.mod             normal.mod          video_fb.mod
gcry_blowfish.mod            ntfscomp.mod        video.lst
gcry_camellia.mod            ntfs.mod            video.mod
gcry_cast5.mod               ohci.mod            videotest.mod
gcry_crc.mod                 part_acorn.mod      xfs.mod
gcry_des.mod                 part_amiga.mod      xnu.mod
gcry_md4.mod                 part_apple.mod      xnu_uuid.mod
gcry_md5.mod                 part_gpt.mod        zfsinfo.mod
gcry_rfc2268.mod             partmap.lst         zfs.mod
gcry_rijndael.mod            part_msdos.mod
gcry_rmd160.mod              part_sun.mod

```

Can anyone help? - I need to get back to windows as I use it for work!

---

### Post by whoya on 2010-06-24
yeah i got the same problem but with xp. after i select win xp in grub all i get is a black screen with a blinking cursor in the top left corner.
can anybody help??

---

### Post by wilee-nilee on 2010-06-24
Thread starter post the boot script in my sig in code tags.[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

To the second post start your own thread with the same information, each boot problem is different so keeping them separate makes it easier to analyze.

---

### Post by darkod on 2010-06-24
Run the boot info script and post the results as suggested. And don't try to create the /boot/grub/menu.lst file because that's for grub1 and ubuntu since 9.10 is using grub2. Be careful not to mix them up and always check for which ubuntu version the instructions you find are.

---

### Post by etheesdad on 2010-06-24
> **wilee-nilee said:**
> Thread starter post the boot script in my sig in code tags.[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1280594343 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 1280591783 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1280601999 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   320,384,294   320,384,232   7 HPFS/NTFS
/dev/sda2         320,384,295 1,280,316,239   959,931,945   7 HPFS/NTFS
/dev/sda3       1,280,316,240 1,953,520,064   673,203,825   5 Extended
/dev/sda5       1,280,316,303 1,933,856,504   653,540,202  83 Linux
/dev/sda6       1,933,856,568 1,953,520,064    19,663,497  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  42 SFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DEF87E97F87E6DA1                       ntfs       SYSTEM                        
/dev/sda2        3FF2DA4A0260A4F6                       ntfs       DOCUMENTS                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        89528a39-d9d1-4674-bdfb-54b58dc0886b   ext4                                     
/dev/sda6        c772543d-de52-4f69-9e67-c63ef0a4ccf4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F224F84424F80CFB                       ntfs       CURRENT                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        69DEA6EF628AAA57                       ntfs       STORAGE                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/CURRENT           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/DOCUMENTS         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/STORAGE           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=89528a39-d9d1-4674-bdfb-54b58dc0886b ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=89528a39-d9d1-4674-bdfb-54b58dc0886b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
	linux	/boot/vmlinuz-2.6.31-22-generic-pae root=UUID=89528a39-d9d1-4674-bdfb-54b58dc0886b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
	echo	'Loading Linux 2.6.31-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-22-generic-pae root=UUID=89528a39-d9d1-4674-bdfb-54b58dc0886b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 89528a39-d9d1-4674-bdfb-54b58dc0886b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set def87e97f87e6da1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda5 :
UUID=89528a39-d9d1-4674-bdfb-54b58dc0886b	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb1 :
UUID=F224F84424F80CFB	/media/CURRENT	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda2 :
UUID=3FF2DA4A0260A4F6	/media/DOCUMENTS	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda1 :
UUID=DEF87E97F87E6DA1	/media/SYSTEM	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sdc1 :
UUID=69DEA6EF628AAA57	/media/STORAGE	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda6 :
UUID=c772543d-de52-4f69-9e67-c63ef0a4ccf4	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sda5: Location of files loaded by Grub: ===================


 655.6GB: boot/grub/core.img
 666.7GB: boot/grub/grub.cfg
 657.7GB: boot/initrd.img-2.6.31-22-generic-pae
 657.7GB: boot/initrd.img-2.6.32-22-generic-pae
 656.0GB: boot/vmlinuz-2.6.31-22-generic-pae
 657.2GB: boot/vmlinuz-2.6.32-22-generic-pae
 657.7GB: initrd.img
 657.7GB: initrd.img.old
 657.2GB: vmlinuz
 656.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by darkod on 2010-06-24
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 1280594343 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe [COLOR=Red]/grldr[/COLOR]

You have installed grub2 on your win7 partition /dev/sda1. Boot ubuntu and open your win7 partition from Places and delete the grldr file. After that unmount it (on desktop right-click on the icon and Unmount), and use this procedure to remove grub2 from the boot sector:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by etheesdad on 2010-06-24
> **darkod said:**
> 
You have installed grub2 on your win7 partition /dev/sda1. Boot ubuntu and open your win7 partition from Places and delete the grldr file. After that unmount it (on desktop right-click on the icon and Unmount), and use this procedure to remove grub2 from the boot sector:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Managed to boot to Windows following your instructions

OMG thats such a relief!

Thankyou so much for your help!!!!!!!!!

---

### Post by etheesdad on 2010-06-25
Now when I boot into windows it says "this version of windows is not genuine". It IS a genuine copy of Windows (I am a MDSN subscriber, which is where the key came from). Its bought, legal, and paid for. 

I didnt realise it when I followed the suggestion above but grldr file has a relationship to windows WGA protection. 

Anyone able to advise how to get windows to recognise my legit license key as legit again?

---

### Post by wilee-nilee on 2010-06-25
> **etheesdad said:**
> Now when I boot into windows it says "this version of windows is not genuine". It IS a genuine copy of Windows (I am a MDSN subscriber, which is where the key came from). Its bought, legal, and paid for. 

I didnt realise it when I followed the suggestion above but grldr file has a relationship to windows WGA protection. 

Anyone able to advise how to get windows to recognise my legit license key as legit again?

This has happened to some MS users, since you have a install key when you try to activate again do you get an auto phone activation option? If you don't, call MS they will help you get it activated. I'm not sure how we could help you but maybe others have ideas. I have a upgrade of W7 and every time I install it I have to do a crack to get to the auto-phone in option, or call MS. Were on your side but I think you may get the best help from MS since your all legit.

---

### Post by darkod on 2010-06-26
> **etheesdad said:**
> 

I didnt realise it when I followed the suggestion above but grldr file has a relationship to windows WGA protection. 


That is very unlikely. I'm pretty sure grldr is short for grub loader. It should have no relation at all to windows.

We've seen plenty of those results files here and almost all of them don't have the grldr present for win7. If it's part of any win7 process, all results would have it.

As already mentioned, just call MS with your license and they will guide you what to do.

---

