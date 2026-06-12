---
title: "Dual-boot failure on upgrade; testdisk clarification"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Peter Lenny on 2010-05-08
I have what is becoming a common problem. From a peaceful, existing dual-boot setup (XP and Ubuntu on separate disks) I upgraded from 9.10 to 10.4 and now cannot boot XP.

OK, for a week I have been trying solutions, but I am definitely a noob.

Following advice from other threads, I got to screen 3 of TestDisk, only to meet:

> TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - ATA ST3320613AS

[COLOR=Red]Hidden sectors are present.

size       625142448 sectors
user_max   625142448 sectors
native_max 4385456 sectors
dco        625142448 sectors
Device Configuration Overlay (DCO) present.


[ Continue ]  Continue even if there are hidden data[/COLOR]
- which is not the way they said it would be.

Can anyone tell me what's happening and how I might respond?

What other information is needed?

Thanks in advance.

---

### Post by cosaki on 2010-05-11
I have that same screen too... The only option was to continue.  Still no luck getting my Windows 7 to boot back up :(

---

### Post by omalsa04 on 2010-05-11
I got that screen too.
I just pressed continue, continued as normal and everything worked fine XD

This is the steps I used (in order):
[No Log]
selected /dev/sda (my windows partition is on HD0) [Proceed]
[Continue]
[Intel]
[Advanced]
selected Partition 3 (with the * next to it, this is where my MBR is kept) [BackupBS]
Type "Y"
then press q until testdisk exits

then run "sudo update-grub"
Hope this helps!

---

### Post by Peter Lenny on 2010-05-24
When you say:

> then run "sudo update-grub"

- does that mean that, after restoring from the backup XP boot sector, you were then able to boot into Ubuntu or did you run sudo  at the Grub screen (i.e. was Grub still working)?

I have hesitated to complete the TestDisk procedure for fear of losing Ubuntu too, despite some great feedback from Christophe GRENIER (below).

> > I think Grub has overwritten something on my "Windows disk" (in a
> dual-boot setup): why am I getting a DCO report?

The boot sector of your NTFS partition may be damaged.
In Advanced, select the NTFS partition, choose Boot, BackupBS, confirm,
Quit and reboot

Sometimes the report about DCO was erronous with previous previous.
Can you try using TestDisk 6.12-WIP ?
wget -N [http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.12-WIP.linux26.tar.bz2)
tar xjf testdisk-6.12-WIP.linux26.tar.bz2
cd testdisk-6.12-WIP
sudo ./testdisk_static


---

### Post by dino99 on 2010-05-24
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Peter Lenny on 2010-05-24
Sorry, I just don't understand how this is an answer to my question. When I restore the XP boot sector using  TestDisk, I assume I'm going to be able to boot into XP OK, but will my existing Grub installation still work?

---

### Post by darkod on 2010-05-24
> **Peter Lenny said:**
> Sorry, I just don't understand how this is an answer to my question. When I restore the XP boot sector using  TestDisk, I assume I'm going to be able to boot into XP OK, but will my existing Grub installation still work?

Yes, don't worry, grub will still work. Dino just loves that mini how-to which basically tells you how to install ubuntu from scratch but has nothing to do with your problem. So he keeps posting it around. And confusing people. :)

---

### Post by Peter Lenny on 2010-05-24
Finally screwed up courage, ignored the DCO issue and my incomplete data  backup, followed Christophe's instructions and it worked just fine!
Seems to have left  Ubuntu with a few  hiccups, but nothing that a  reboot doesn't cure.
Thanks to all involved.

---

### Post by ManyouRisms on 2010-07-15
Hey guys, having the exact same issue, i stumbled upon this thread after searching.

Rather than beat a dead horse, i'll just use his description.

Anyways, same issue, only after trying this with testdisk, and updating grub, the same issue happens.

After referring to [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I tried running my Windows 7 startup disk, and attempting to use the repair option,  It says it isn't the correct disk.  Lmao? It's the only i used to install windows 7.

Maybe my issues go deeper, and point to a bad sector?

Any help appreciated. 
Thanks

---

### Post by oldfred on 2010-07-16
Post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by ManyouRisms on 2010-07-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 48238519 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 10930991 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   236,075,174   236,075,112  83 Linux
/dev/sda2    *    236,075,175   470,254,679   234,179,505   7 HPFS/NTFS
/dev/sda3         470,254,680   488,392,064    18,137,385   5 Extended
/dev/sda5         470,254,743   488,392,064    18,137,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4337295c-f3dc-4bf4-b865-fba64f5c8343   ext4                                     
/dev/sda2        141E4A201365DFCD                       ntfs       Win7                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        1b9d5e68-6087-46af-9139-80bc2ff7f09e   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 ro  vga=791 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 ro single  vga=791 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 ro  vga=791 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 ro single  vga=791 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 ro  vga=791 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    echo    'Loading Linux 2.6.31-19-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 ro single  vga=791 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4337295c-f3dc-4bf4-b865-fba64f5c8343
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 141e4a201365dfcd
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4337295c-f3dc-4bf4-b865-fba64f5c8343 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1b9d5e68-6087-46af-9139-80bc2ff7f09e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0 

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
  73.7GB: boot/initrd.img-2.6.31-19-generic-pae
  24.7GB: boot/initrd.img-2.6.32-23-generic
  80.6GB: boot/initrd.img-2.6.32-23-generic-pae
   3.1GB: boot/vmlinuz-2.6.31-19-generic-pae
   4.5GB: boot/vmlinuz-2.6.32-23-generic
  71.0GB: boot/vmlinuz-2.6.32-23-generic-pae
  80.6GB: initrd.img
  24.7GB: initrd.img.old
  71.0GB: vmlinuz
   4.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

This definitely confirms grub was installed to sda2 at some point.  I just wish testdisk worked, seemed too good to be true.  I was reading up a bit on ms-sys but from what i understand, messing with the MBR is sketchy business at best.

Thanks for your prompt reply.  Let me know if you see something in "RESULTS" that i don't.

---

### Post by oldfred on 2010-07-16
You do have grub installed to the windows partition boot sector. Testdisk should solve it. If not you need to run the fixboot command from windows. 

The only other things to try are chkdsk to make sure it can see the NTFS partition. If chkdsk does not work testdisk has another repair for that.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Then see if the windows fixboot works.

There is nothing wrong with the grub2 installed in the MBR as it should work to boot Ubuntu. Grub only will boot working windows systems.

Testdisk also has a rebuild function, not sure it works with win7 as the boot sector is different than XPs:
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk, reboot and see whether you can boot windows.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by amarendra on 2011-02-10
But what if I've messed up Windows 7 partition afterr recovering Ubuntu 10.10 partition which is not booting. The error I am getting is "BBOTMGR msissing"

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #8 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd1 and 
                       looks at sector 109460673 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2          73,433,115   230,757,659   157,324,545   f W95 Ext d (LBA)
/dev/sda5    *    104,904,513   165,132,128    60,227,616  83 Linux
/dev/sda3                  63       192,779       192,717  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
248 heads, 62 sectors/track, 1020 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,683,519    15,683,458   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1cacbc9e-7185-46a0-96e4-a892c25e15d5   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1c5aa9a0-8df5-473a-89cf-b0f45ff0111a   ext3       boot-part                     
/dev/sda5        b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7   ext4       ubuntu-10.10                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BC15-545F                              vfat       FAKEER                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4130DD442010141E                       ntfs       Transcend                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        C0EA523FEA523240                       ntfs       Passport                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/1cacbc9e-7185-46a0-96e4-a892c25e15d5 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Transcend         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/Passport          fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d436d96036d943e0
	chainloader +1
}
menuentry "Arch (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0b882b2b-ab64-43bf-aa70-d36e659e25ad
	linux /boot/vmlinuz26 root=/dev/sda2
	initrd /boot/kernel26.img
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=263b8dcd-7517-4230-bd9d-6ae68ccff794 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  63.4GB: boot/grub/grub.cfg
  54.4GB: boot/initrd.img-2.6.32-27-generic
    ??GB: boot/initrd.img-2.6.35-24-generic
  79.3GB: boot/initrd.img-2.6.35-25-generic
  54.0GB: boot/vmlinuz-2.6.32-27-generic
    ??GB: boot/vmlinuz-2.6.35-24-generic
    ??GB: boot/vmlinuz-2.6.35-25-generic
  79.3GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old

=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d436d96036d943e0
	chainloader +1
}
menuentry "Arch (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0b882b2b-ab64-43bf-aa70-d36e659e25ad
	linux /boot/vmlinuz26 root=/dev/sda2
	initrd /boot/kernel26.img
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

=================== sda3: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.32-27-generic
    .0GB: boot/initrd.img-2.6.35-24-generic
    .0GB: boot/initrd.img-2.6.35-25-generic
    .0GB: boot/vmlinuz-2.6.32-27-generic
    .0GB: boot/vmlinuz-2.6.35-24-generic
    .0GB: boot/vmlinuz-2.6.35-25-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 81 00 00 3d 05 00 00  ee 28 ee 4b ee 28 ee 4b  |....=....(.K.(.K|
00000010  39 fd 1d 49 00 00 00 00  00 00 01 00 08 00 00 00  |9..I............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 74 bc 00 00  |............t...|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 2a d9 11 3f  00 00 00 00 00 00 00 00  |....*..?........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 94 de d2 3b  00 00 00 00 00 00 00 00  |.......;........|
00000090  ee 28 ee 4b 94 de d2 3b  00 00 00 00 00 00 00 00  |.(.K...;........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 f2 01 00 00  ee 28 ee 4b ee 28 ee 4b  |.........(.K.(.K|
00000110  39 fd 1d 49 00 00 00 00  00 00 01 00 08 00 00 00  |9..I............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 75 bc 00 00  |............u...|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 2b d9 11 3f  00 00 00 00 00 00 00 00  |....+..?........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 94 de d2 3b  00 00 00 00 00 00 00 00  |.......;........|
00000190  ee 28 ee 4b 94 de d2 3b  00 00 00 00 00 00 00 00  |.(.K...;........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 fe  |................|
000001c0  ff ff 83 fe ff ff 26 37  e0 01 20 00 97 03 00 00  |......&7.. .....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Peter Lenny on 2011-02-10
Amarendra,

I'm replying only because your query was addressed to me, but I am certainly not the person to answer.

That is, you are talking to someone who, on his last Ubuntu update/reinstall attempt, managed to overwrite part of his (unbackedup) Windows install. My data were recovered only with expensive professional assistance.

Be afraid!

For the good of all involved, I am unsubscribing from this thread.

Best,
Peter

---

### Post by oldfred on 2011-02-10
Ubuntu's menu says it is trying to boot sda1 Vista, but you show no sda1. But you have space before sda2? Did you in testdisk delete sda1? I would go back into testdisk and see if you can recover a sda1 NTFS partition at the beginning of sda.

Since Ubuntu's menu showed it, it was there when you installed Ubuntu. It may have just needed chkdsk or other minor windows repairs.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by amarendra on 2011-02-10
> **oldfred said:**
> Ubuntu's menu says it is trying to boot sda1 Vista, but you show no sda1. But you have space before sda2? Did you in testdisk delete sda1? I would go back into testdisk and see if you can recover a sda1 NTFS partition at the beginning of sda.

Since Ubuntu's menu showed it, it was there when you installed Ubuntu. It may have just needed chkdsk or other minor windows repairs.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Wouldn't, checking for the Lost Windows 7 or the first 101MB (sda1) partition that 7 had created, cause the now found Ubuntu-10.10 (sda5) to go away now? I mean it happened before. Whenever I tried to recover some partition I always got an entirely new partition table. Not that in addition to whatever I already had. Or should I just try it? How about "chkdsk"? I don't have any Windows partition remaining and when I tried to boot form 7 DVD, it started to install straight forward, I just couldn't get repair option to fix MBR.

---

### Post by oldfred on 2011-02-11
If the sda1 overlapped the sda2 extended, they yes it will have to delete one or the other. But they should never overlap, unless you deleted it before you created the new partition. The original partition before you made it smaller will definitely overlap, but you should have a smaller version also to recover.

You have to have a NTFS primary partition with the boot flag for windows to repair or run chkdsk. Windows also does not see Linux partitions. If you have a full install DVD, you can install to a new NTFS primary partition. If it is just a recovery DVD then all it does is reformat drive and make it like the day you purchased it.

---

### Post by oldfred on 2011-02-11
amarendra see this post:

[http://ubuntuforums.org/showthread.php?t=1677734](http://ubuntuforums.org/showthread.php?t=1677734)

---

### Post by amarendra on 2011-02-14
> **oldfred said:**
> amarendra see this post:

[http://ubuntuforums.org/showthread.php?t=1677734](http://ubuntuforums.org/showthread.php?t=1677734)
Hey..thanks a lot.. I tried a lot.. But seemed I was not able to get the Windows partition back or resuse the Ubuntu partition as it was. So, what I did was I wiped everything from hard disk after copying /home and reinstalled everything - first Win 7 and then Ubuntu 10.10 on another and created another partition for /home and later put my stuff back. I have bought another external hard disk where I will keep an image of my working system..just in case..

Thank you all.. I could try to recover a lil more but I was really having little or no time after office. Thanks

---

