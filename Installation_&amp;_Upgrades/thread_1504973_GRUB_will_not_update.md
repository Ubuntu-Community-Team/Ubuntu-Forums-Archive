---
title: "GRUB will not update"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by martintremblay on 2010-06-08
When I attempt to update GRUB in Ubuntu 10.04 with the following command in terminal:
$ sudo update-grub

I receive the following error:
/etc/default/grub: 1: GRUB: not found

why will my GRUB not update? (I believe I am using GRUB2 with Ubuntu 10.04)

Thanks in Advance

---

### Post by ronparent on 2010-06-08
Where do you think your grub2 is installed?

---

### Post by wilee-nilee on 2010-06-08
> **martintremblay said:**
> When I attempt to update GRUB in Ubuntu 10.04 with the following command in terminal:
$ sudo update-grub

I receive the following error:
/etc/default/grub: 1: GRUB: not found

why will my GRUB not update? (I believe I am using GRUB2 with Ubuntu 10.04)

Thanks in Advance

So you need to provide more information is this a dual boot and is it a wubi install.

Without some details it is difficult to find the problem.

---

### Post by martintremblay on 2010-06-08
GRUB loads with proper options at startup. (I dual boot XP)

I simply cannot update GRUB file when I have made changes by running
$ sudo update-grub

I believe GRUB is installed in the MBR of the primary drive 
(or wherever Ubuntu initially put it)

---

### Post by wilee-nilee on 2010-06-08
Post the reading from the terminal after running this command.
```
grub-install -v
```

---

### Post by darkod on 2010-06-08
Also check if the /etc/default/grub file is there. :)

---

### Post by martintremblay on 2010-06-08
Command entered
$ grub-install -v

Result
grub-install (GNU GRUB 1.98-1ubuntu6)

---

### Post by wilee-nilee on 2010-06-08
> **darkod said:**
> Also check if the /etc/default/grub file is there. :)

It's all yours.;)

---

### Post by martintremblay on 2010-06-08
and yes file is there... in etc/default/grub

---

### Post by darkod on 2010-06-08
I have no idea, but lets try recreating grub2 config files. I rarely use the command, but I think it was something like:

sudo grub-mkconfig

If anything is missing hopefully that should sort it out. You might also need

sudo update-grub

after that.

---

### Post by martintremblay on 2010-06-08
just in case it matters...

I have run both:

$ sudo update-grub
and
$ sudo update-grub2

both return the same error
/etc/default/grub: 1: GRUB: not found

---

### Post by martintremblay on 2010-06-08
tried running 
$ sudo grub-mkconfig

result (LOL - of course is)
/etc/default/grub: 1: GRUB: not found

---

### Post by martintremblay on 2010-06-08
I also tried running direct command to update GRUB:
$ sudo grub-mkconfig -o /boot/grub/grub.cfg

still results with same error:
/etc/default/grub: 1: GRUB: not found

---

### Post by martintremblay on 2010-06-08
Can anyone tell me if I will lose my settings to Dual boot if I try this?

sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub2 grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by ronparent on 2010-06-08
You have grub installed somewhere otherwise you would not be able to boot to 10.04, The question is what instance is it and where? It appears as if the grub you are using to boot doesn't belong to 10.04? Verify that the /boot/grub is actually populated. Also that /etc/default/grub exists. You have to run grub-update (and all of the other related commands) from the system it is installed to. Thus your alternative are to discover where it is installed or to install it within your 10.04 installation (ie sudo apt-get install grub-pc).

---

### Post by ronparent on 2010-06-08
The setting to dual boot should reset with grub-update and all valid OS should be automatically found on execution.

---

### Post by wilee-nilee on 2010-06-08
I suspect this is not a true dual boot or a partition was built with the wubi install.
Run this boot script and post it in code tags it will give the lowdown of your setup.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

There may other ways to find this out but this is the most efficient way to get the needed information.

---

### Post by martintremblay on 2010-06-08
I have run the boot info script and attached the results

---

### Post by wilee-nilee on 2010-06-08
Lets make this easy for the ones that can help.;)
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         409,609,305   488,392,064    78,782,760   5 Extended
/dev/sda5         409,609,368   485,066,609    75,457,242  83 Linux
/dev/sda6         485,066,673   488,392,064     3,325,392  82 Linux swap / Solaris
/dev/sda3         102,398,310   409,609,304   307,210,995   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7290C1CC90C1974F                       ntfs       WIndows XP                    
/dev/sda2: PTTYPE="dos" 
/dev/sda3        0DF7669F3C0C65A9                       ntfs       Ubuntu XP Storage             
/dev/sda5        31e67f7d-338f-4f5e-8971-23e8486a8cac   ext4       Ubuntu                        
/dev/sda6        3e7be0d2-85b5-4929-b7db-1ff24c705f76   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
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
search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=31e67f7d-338f-4f5e-8971-23e8486a8cac ro   quiet splash nomodeset acpi_backlight=vendor
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=31e67f7d-338f-4f5e-8971-23e8486a8cac ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=31e67f7d-338f-4f5e-8971-23e8486a8cac ro   quiet splash nomodeset acpi_backlight=vendor
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=31e67f7d-338f-4f5e-8971-23e8486a8cac ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 31e67f7d-338f-4f5e-8971-23e8486a8cac
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7290c1cc90c1974f
	drivemap -s (hd0) ${root}
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=31e67f7d-338f-4f5e-8971-23e8486a8cac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3e7be0d2-85b5-4929-b7db-1ff24c705f76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 209.9GB: boot/grub/core.img
 211.1GB: boot/grub/grub.cfg
 218.3GB: boot/initrd.img-2.6.31-20-generic
 211.4GB: boot/initrd.img-2.6.32-22-generic
 216.2GB: boot/vmlinuz-2.6.31-20-generic
 211.3GB: boot/vmlinuz-2.6.32-22-generic
 211.4GB: initrd.img
 211.4GB: initrd.img.old
 211.3GB: vmlinuz
 211.3GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-06-08
When you installed Ubuntu did you install grub to the Ubuntu partition? Also is your computer dual booting as it should? I'm still learning how to read the boot script so I tend to ask questions that may actually be answered within the script.

---

### Post by martintremblay on 2010-06-08
To answer your questions:

A- I followed the standard Ubuntu install 9.10, then recently upgraded to 10.04, 
although may have inadvertently changed  this in recent attempts to repair this issue.

B - Yes the computer dual boots as expected. I can boot either Ubuntu 10.04 or XP
(I can also access a third (storage) partition from either OS)

The only system issue I have is whenever I attempt to run "sudo update-grub" it results in 
"/etc/default/grub: 1: GRUB: not found"

---

### Post by wilee-nilee on 2010-06-08
I would suspect that in the process somewhere that grub was added to the Ubuntu partition. This is just a guess, I have had this happen as well, but I forget what caused this or how I fixed it. If the computers booting then for now you seem to be okay, but hopefully others who know more about this will have a better idea of the actual situation and can confirm it. Having grub in the Ubuntu partition from what I have seen posted on the forums is not a big deal, it is when put in the windows partition that it causes problems.

I don't know if having two grubs and it seeming to be the added grub being the bootloader, and not being able to update will cause kernels to not be added as being 1st in the boot order, probably not.

---

### Post by ronparent on 2010-06-09
If you really want to chase down your problem, you may want to study this reference: [http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html)

---

### Post by kansasnoob on 2010-06-09
While booted into Ubuntu post the output of the following commands:

```
aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
ls /boot/grub
```

```
ls /boot
```

---

### Post by martintremblay on 2010-06-09
1 - $ aptitude show grub|head -2 && aptitude show grub-pc|head  -2 && aptitude show grub-common|head -2 && aptitude show  os-prober|head -2
***results:***
```

Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed 
```
2 - ls /boot/grub
***results:***
```

915resolution.mod            gcry_rmd160.mod     part_sun.mod
acpi.mod                     gcry_seed.mod       parttool.lst
affs.mod                     gcry_serpent.mod    parttool.mod
afs_be.mod                   gcry_sha1.mod       password.mod
afs.mod                      gcry_sha256.mod     password_pbkdf2.mod
aout.mod                     gcry_sha512.mod     pbkdf2.mod
ata.mod                      gcry_tiger.mod      pci.mod
ata_pthru.mod                gcry_twofish.mod    play.mod
at_keyboard.mod              gcry_whirlpool.mod  png.mod
befs_be.mod                  gettext.mod         probe.mod
befs.mod                     gfxmenu.mod         pxeboot.img
biosdisk.mod                 gfxterm.mod         pxecmd.mod
bitmap.mod                   gptsync.mod         pxe.mod
bitmap_scale.mod             grldr.img           raid5rec.mod
blocklist.mod                grub.cfg            raid6rec.mod
boot.img                     grubenv             raid.mod
boot.mod                     gzio.mod            read.mod
bsd.mod                      halt.mod            reboot.mod
bufio.mod                    handler.lst         reiserfs.mod
cat.mod                      handler.mod         relocator.mod
cdboot.img                   hashsum.mod         scsi.mod
chain.mod                    hdparm.mod          search_fs_file.mod
charset.mod                  hello.mod           search_fs_uuid.mod
cmp.mod                      help.mod            search_label.mod
command.lst                  hexdump.mod         search.mod
configfile.mod               hfs.mod             serial.mod
core.img                     hfsplus.mod         setjmp.mod
cpio.mod                     iso9660.mod         setpci.mod
cpuid.mod                    jfs.mod             sfs.mod
crc.mod                      jpeg.mod            sh.mod
crypto.lst                   kernel.img          sleep.mod
crypto.mod                   keystatus.mod       tar.mod
datehook.mod                 linux16.mod         terminal.lst
date.mod                     linux.mod           terminal.mod
datetime.mod                 lnxboot.img         terminfo.mod
device.map                   loadenv.mod         test.mod
diskboot.img                 locale              tga.mod
dm_nv.mod                    loopback.mod        trig.mod
drivemap.mod                 lsmmap.mod          true.mod
echo.mod                     ls.mod              udf.mod
efiemu32.o                   lspci.mod           ufs1.mod
efiemu64.o                   lvm.mod             ufs2.mod
efiemu.mod                   mdraid.mod          uhci.mod
elf.mod                      memdisk.mod         unicode.pf2
example_functional_test.mod  memrw.mod           usb_keyboard.mod
ext2.mod                     minicmd.mod         usb.mod
extcmd.mod                   minix.mod           usbms.mod
fat.mod                      mmap.mod            usbtest.mod
font.mod                     moddep.lst          vbeinfo.mod
fshelp.mod                   msdospart.mod       vbe.mod
fs.lst                       multiboot2.mod      vbetest.mod
functional_test.mod          multiboot.mod       vga.mod
gcry_arcfour.mod             normal.mod          vga_text.mod
gcry_blowfish.mod            ntfscomp.mod        video_fb.mod
gcry_camellia.mod            ntfs.mod            video.lst
gcry_cast5.mod               ohci.mod            video.mod
gcry_crc.mod                 part_acorn.mod      videotest.mod
gcry_des.mod                 part_amiga.mod      xfs.mod
gcry_md4.mod                 part_apple.mod      xnu.mod
gcry_md5.mod                 part_gpt.mod        xnu_uuid.mod
gcry_rfc2268.mod             partmap.lst         zfsinfo.mod
gcry_rijndael.mod            part_msdos.mod      zfs.mod

```3 - ls /boot
***results:***
 ```

  abi-2.6.31-20-generic         memtest86+.bin
abi-2.6.32-22-generic         System.map-2.6.31-20-generic
config-2.6.31-20-generic      System.map-2.6.32-22-generic
config-2.6.32-22-generic      vmcoreinfo-2.6.31-20-generic
grub                          vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic 
```

---

### Post by ronparent on 2010-06-09
The first strange thing I note is that you have kernel version 2.6.31-20 and 2.6.32-22. This may not be material but the current Lucid distro comes with version 2.6.32-21?

Boot into 10.04 and now try running 'sudo grub-install /dev/<drive>' where <drive> is sda, sdb, or sdc - wherever you want to locate your grub2 MBR. Then whichever you choose makesure that it is selected as the 1st boot drive in bios. Although update-grub is part of that command, you should now be able to run it.

---

### Post by martintremblay on 2010-06-09
Based on the reference/guide Ronparent provided, I earlier attempted to reinstall/repair by running:
"sudo grub-install /dev/sda"

the system responds (almost immediately) with:
"Installation finished. No error reported"

then I run :
"sudo update-grub"

and same result
"/etc/default/grub: 1: GRUB: not found "(yet its there!!!)


I tried again just for kicks...
same result!

---

### Post by ronparent on 2010-06-09
Which kernel are you booting?

---

### Post by martintremblay on 2010-06-09
when I run uname -a tells me:

Linux martin-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

---

### Post by kansasnoob on 2010-06-09
Well, that all appears to be good :confused:

While this seems totally redundant please copy-n-paste these commands (do not type them):

```
sudo update-grub
```

```
sudo apt-get -f install
```

That may indicate that you need to "apt-get autoremove" so:

```
sudo apt-get autoremove
```

```
sudo update-grub
```

The reason I'm stressing to "copy-n-paste" rather than type is to rule out some odd keyboard vs. Xorg scenario :)

It also can't hurt to:

```
sudo dpkg --configure -a
```

You seem to have a unique problem and I'm intrigued.

---

### Post by martintremblay on 2010-06-09
thanks kansasnoob, I'm a firm believer in cut and paste (and horrible at typing) so...

results:

"sudo update-grub"
/etc/default/grub: 1: GRUB: not found

"sudo apt-get -f install"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

"sudo apt-get autoremove"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

"sudo update-grub"
/etc/default/grub: 1: GRUB: not found

"sudo dpkg --configure -a"
(returns me to prompt ~$ )

and just to check if it made a difference I ran "sudo update-grub" again
but obtained same results: /etc/default/grub: 1: GRUB: not found

---

### Post by kansasnoob on 2010-06-10
I'm totally puzzled :confused:

Try:

```
sudo apt-get clean
```

Then repeat.

This may be a good excuse to contact an old friend.

---

### Post by oldfred on 2010-06-10
If you are working from the live cd you have to mount the partition so grub know where to install from.

sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by kansasnoob on 2010-06-10
You know, what you were saying earlier:

> Can anyone tell me if I will lose my settings to Dual boot if I try this?

sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub2 grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

may not have been far off, but let me first respond to oldfred.

I'd use slightly different commands.

---

### Post by kansasnoob on 2010-06-10
> **oldfred said:**
> If you are working from the live cd you have to mount the partition so grub know where to install from.

sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

It seems like the OP can boot everything just fine but gets that terminal output any time (s)he runs "update-grub" so how does reinstalling to the mbr solve anything?

I'm thinking maybe because the OP has the old transitional package grub2 :confused:

I'm just considering how to do this properly.

---

### Post by kansasnoob on 2010-06-10
I really do suspect some package and/or file conflict so I'd do this while booted into Lucid:

```
sudo mv /boot/grub /boot/grub_OLD
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub2
```

```
sudo apt-get --purge remove grub-pc
```

```
sudo apt-get --purge remove grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

Then hold your breath and reboot.

---

### Post by ronparent on 2010-06-10
Boy, that ought to clean house. I bet you got it!

---

### Post by martintremblay on 2010-06-10
Try:
```
sudo apt-get clean
```Then repeat.

result:
```

$ sudo apt-get clean
$ sudo apt-get clean
$ sudo update-grub
/etc/default/grub: 1: GRUB: not found

```

---

### Post by martintremblay on 2010-06-10
Kudos to Kansasnoob and everyone else who helped me achieve success! 

This solved everything - I followed remove/purge instructions and reinstalled as follows:

> **kansasnoob said:**
> I really do suspect some package and/or file conflict so I'd do this while booted into Lucid:

```
sudo mv /boot/grub /boot/grub_OLD
``````
sudo mkdir /boot/grub
``````
sudo apt-get --purge remove grub2
``````
sudo apt-get --purge remove grub-pc
``````
sudo apt-get --purge remove grub-common
``````
sudo apt-get install grub-pc
``````
sudo update-grub
``````
sudo grub-install /dev/sda
```Then hold your breath and reboot.

I have no issues, can boot into all partitions, and "sudo update-grub" works like it should. Thanks again everyone - you all rock!!!

I'll post my results per command and mark as solved for anyone who may stumble across this in the future

---

### Post by martintremblay on 2010-06-10
Arrgh! maybe I wont post the results. Sorry folks but of course they are gone after rebooting

I can summarize by saying that:

```
sudo mv /boot/grub /boot/grub_OLD
```returned me to the "$ prompt"

```
sudo mkdir /boot/grub
```Returned me to the "$ prompt"


```
sudo apt-get --purge remove grub2
```indicated 2 pkgs to be removed - I followed prompts and removed all

```
sudo apt-get --purge remove grub-pc
```Indicated nothing installed - no changes made

```
sudo apt-get --purge remove grub-common
```Indicated nothing installed - However it did make changes to 1 Pkg

```
sudo apt-get install grub-pc
```I followed prompts and reinstalled GRUB2 into SDA 

```
sudo update-grub
```Worked perfectly and updated grub properly/as expected as follows:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done```
sudo grub-install /dev/sda
```System responded:
```
Installation finished. No error reported.
```

---

