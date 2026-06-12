---
title: "problem dual boot for windows 7"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by NEBRU on 2010-06-04
[FONT=Calibri][SIZE=3]I am having a problem with dual booting W7 + Ubuntu 10.04, when I try to boot W7 I get the blue screen of death and it sets back to the grub. My machine is a Thinkpath T41 with ATI mobility radeon 9000 chipset. I don’t have any problem booting into ubuntu the OS I had in this machine prior to dual boot was just W7 and I never had any problem before. I have tried to restore W7 with the installation CD (bootrec.exe /fixmbr, /fixboot, /rebuldbcd etc.) and also did the testdisk command at terminal but so far nothing seems to work, I am getting the message: the system partition was not found, the requested system device cannot be found, and for testdisk in step 6 the “backupBS” option is missing. I used the option install side by side to partition the HD when I did the Ubuntu installation to shrink W7. (Fresh install). If anyone can shine some light into this problem for me would be greatly appreciated.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Please let me know if you need more information. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]This is my partition table and boot info summary:[/SIZE][/FONT]
```
 

``````
ubuntu@ubuntu-laptop:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40a5f6c9
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4939    39668016+   7  HPFS/NTFS
/dev/sda2            4939        7296    18935809    5  Extended
/dev/sda5            4939        7192    18100224   83  Linux
/dev/sda6            7193        7296      834560   82  Linux swap / Solaris
Disk /dev/sdb: 2031 MB, 2031091712 bytes
63 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ef631df
This doesn't look like a partition table
Probably you selected the wrong device.
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      540844     1042316   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(540843, 53, 21)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(1042315, 32, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      883091     1892906  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(883090, 54, 52)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(793323, 43, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      839687     1339804   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(839686, 2, 39)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(240221, 51, 28)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1069986     1072116     4161550   6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(1069985, 6, 11)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(1072115, 59, 44)
Partition 4 does not end on cylinder boundary.
Partition table entries are not in disk order
 

```
 
```
 
Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS /COMMAND.COM
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
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
sdb: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb has 
                       1939136 sectors.. But according to the info from the 
                       partition table , it has 3966976 sectors.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    79,336,095    79,336,033   7 HPFS/NTFS
/dev/sda2          79,337,470   117,209,087    37,871,618   5 Extended
/dev/sda5          79,337,472   115,537,919    36,200,448  83 Linux
/dev/sda6         115,539,968   117,209,087     1,669,120  82 Linux swap / Solaris
 
blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        38A883B6A88370E4                       ntfs       IBM_PRELOAD                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b   ext4                                     
/dev/sda6        622aba91-650d-40a7-9ea2-951556f1e855   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         49ED-21FF                              vfat                                     
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb         /media/49ED-21FF         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
 
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
search --no-floppy --fs-uuid --set 1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b
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
search --no-floppy --fs-uuid --set 1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b ro   quiet splash
 initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b
 echo 'Loading Linux 2.6.32-21-generic ...'
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set 38a883b6a88370e4
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1c851f8c-f4ff-4d5a-9d3b-4a3e12a7384b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=622aba91-650d-40a7-9ea2-951556f1e855 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=================== sda5: Location of files loaded by Grub: ===================
 
  43.3GB: boot/grub/core.img
  43.7GB: boot/grub/grub.cfg
  43.8GB: boot/initrd.img-2.6.32-21-generic
  43.7GB: boot/vmlinuz-2.6.32-21-generic
  43.8GB: initrd.img
  43.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda2
00000000  2e 30 2e 35 30 37 32 37  2e 38 39 2e 36 36 33 33  |.0.50727.89.6633|
00000010  32 36 35 32 5f 39 43 32  38 5f 35 38 42 31 5f 46  |2652_9C28_58B1_F|
00000020  46 31 46 5f 43 38 42 33  42 39 41 31 45 31 38 45  |F1F_C8B3B9A1E18E|
00000030  6b 65 79 66 6f 72 6d 7c  78 38 36 5f 70 6f 6c 69  |keyform|x86_poli|
00000040  63 79 2e 38 2e 30 2e 4d  69 63 72 6f 73 6f 66 74  |cy.8.0.Microsoft|
00000050  2e 56 43 38 30 2e 41 54  4c 5f 31 66 63 38 62 33  |.VC80.ATL_1fc8b3|
00000060  62 39 61 31 65 31 38 65  33 62 5f 38 2e 30 2e 35  |b9a1e18e3b_8.0.5|
00000070  30 37 32 37 2e 38 39 5f  78 2d 77 77 5f 62 32 38  |0727.89_x-ww_b28|
00000080  38 31 36 34 62 3a 68 34  61 75 77 7a 63 79 2e 72  |8164b:h4auwzcy.r|
00000090  73 68 70 61 79 6c 6f 61  64 2e 38 2e 30 2e 35 30  |shpayload.8.0.50|
000000a0  37 32 37 2e 38 39 2e 36  38 42 37 43 36 44 39 5f  |727.89.68B7C6D9_|
000000b0  31 44 46 32 5f 35 34 43  31 5f 46 46 31 46 5f 43  |1DF2_54C1_FF1F_C|
000000c0  38 42 33 42 39 41 31 45  31 38 45 6b 65 79 66 6f  |8B3B9A1E18Ekeyfo|
000000d0  72 6d 7c 78 38 36 5f 70  6f 6c 69 63 79 2e 38 2e  |rm|x86_policy.8.|
000000e0  30 2e 4d 69 63 72 6f 73  6f 66 74 2e 56 43 38 30  |0.Microsoft.VC80|
000000f0  2e 4d 46 43 5f 31 66 63  38 62 33 62 39 61 31 65  |.MFC_1fc8b3b9a1e|
00000100  31 38 65 33 62 5f 38 2e  30 2e 35 30 37 32 37 2e  |18e3b_8.0.50727.|
00000110  38 39 5f 78 2d 77 77 5f  32 32 63 65 39 62 64 63  |89_x-ww_22ce9bdc|
00000120  3a 74 31 73 77 31 6f 30  6b 2e 39 68 69 6b 65 79  |:t1sw1o0k.9hikey|
00000130  66 6f 72 6d 7c 78 38 36  5f 4d 69 63 72 6f 73 6f  |form|x86_Microso|
00000140  66 74 2e 56 43 38 30 2e  4d 46 43 4c 4f 43 5f 31  |ft.VC80.MFCLOC_1|
00000150  66 63 38 62 33 62 39 61  31 65 31 38 65 33 62 5f  |fc8b3b9a1e18e3b_|
00000160  38 2e 30 2e 35 30 37 32  37 2e 38 39 5f 78 2d 77  |8.0.50727.89_x-w|
00000170  77 5f 33 34 31 39 66 37  64 33 3a 70 65 66 6e 30  |w_3419f7d3:pefn0|
00000180  34 6d 6b 2e 76 65 36 6b  65 79 66 6f 72 6d 7c 78  |4mk.ve6keyform|x|
00000190  38 36 5f 4d 69 63 72 6f  73 6f 66 74 2e 56 43 38  |86_Microsoft.VC8|
000001a0  30 2e 41 54 4c 5f 31 66  63 38 62 33 62 39 61 31  |0.ATL_1fc8b3b9a1|
000001b0  65 31 38 65 33 62 5f 38  2e 30 2e 35 30 37 00 fe  |e18e3b_8.0.507..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 28 02 00 fe  |...........`(...|
000001d0  ff ff 05 fe ff ff 1a 66  28 02 e8 79 19 00 00 00  |.......f(..y....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
 

```

---

### Post by darkod on 2010-06-04
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   [COLOR=Blue]/bootmgr /Boot/BCD /Windows/System32/winload.exe [/COLOR]
                       /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS /COMMAND.COM

Why do you have so many boot files on the win7 partition? Only the ones marked with blue are from win7. This looks like boot files not from two, but from three different systems.

Boot ubuntu and open the win7 partition from Places. It might just say 20GB filesystem there.
Once you have opened it, try moving all the other files except the three marked in blue to your home folder for example. That way you can put them back if needed later. Don't delete them, just move them.

Restart and see if that helped.

---

### Post by oldfred on 2010-06-04
NEBRU, Welcome to the forums.

(I just saw Darko beat me to it on the extra system files from XP & DOS?)

We have seen in the past where if the partition for win7 is at sector 63 it may have been moved from its default of 2048. But you have already done the typical repairs of fixboot and rebuild bcd. After you remove the extra files you may want to try the fixes again.

---

### Post by frantid on 2010-06-04
Nebru,

The thinkpad t41 has a special bios and hard drive geometry filter driver.  You need to be careful with it.  You need to do some reading before attempting any repairs or additions.

Are you aware of the HPA?

[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)


that is why your fdisk is giving all those extra error type lines.

---

### Post by darkod on 2010-06-04
> **frantid said:**
> Nebru,

The thinkpad t41 has a special bios and hard drive geometry filter driver.  You need to be careful with it.  You need to do some reading before attempting any repairs or additions.

Are you aware of the HPA?

[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)


that is why your fdisk is giving all those extra error type lines.

The errors are not on the hdd but are reported about the 2GB usb stick it seems. There doesn't seem to be any HPA present on the hdd because it would be shown in the partitions I guess.

---

### Post by NEBRU on 2010-06-04
> **darkod said:**
> sda1: _________________________________________________________________________
 
Boot ubuntu and open the win7 partition from Places. It might just say 20GB filesystem there.
Once you have opened it, try moving all the other files except the three marked in blue to your home folder for example. That way you can put them back if needed later. Don't delete them, just move them.
 
Restart and see if that helped.
 
Thank you for the quick respond. Will give it a try.

---

### Post by frantid on 2010-06-04
> **darkod said:**
> The errors are not on the hdd but are reported about the 2GB usb stick it seems. There doesn't seem to be any HPA present on the hdd because it would be shown in the partitions I guess.


you're right about the usb stick, I read that too fast.  

The only sure way of seeing if the hpa is there is to see if it's disabled in the bios.


some more links about hpa & recovery steps:

[http://forum.thinkpads.com/viewtopic.php?p=323212#323212](http://forum.thinkpads.com/viewtopic.php?p=323212#323212)
[http://forum.thinkpads.com/viewtopic.php?p=326599#326599](http://forum.thinkpads.com/viewtopic.php?p=326599#326599)

---

### Post by NEBRU on 2010-06-04
> **darkod said:**
> sda1: _________________________________________________________________________
 
Boot ubuntu and open the win7 partition from Places. It might just say 20GB filesystem there.
Once you have opened it, try moving all the other files except the three marked in blue to your home folder for example. That way you can put them back if needed later. Don't delete them, just move them.
 
Restart and see if that helped.
 
 
[COLOR=black][FONT=Verdana]I've moved the files and restarted but I am still getting the blue screen and resetting back to the grub. Have I used all the alternatives to this problem and my last option would be to reinstall the two OSs? [/FONT][/COLOR]

---

### Post by NEBRU on 2010-06-04
> **oldfred said:**
> NEBRU, Welcome to the forums.
 
(I just saw Darko beat me to it on the extra system files from XP & DOS?)
 
We have seen in the past where if the partition for win7 is at sector 63 it may have been moved from its default of 2048. But you have already done the typical repairs of fixboot and rebuild bcd. After you remove the extra files you may want to try the fixes again.
 
I am working on the W7 restore from live CD, I'll let you know how it went.

---

### Post by oldfred on 2010-06-04
We have seen where grub creates another /boot directory that interfers with the /Boot directory of windows. Usually the script shows if it has any grub files but even an empty directory can cause issues.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Also more advanced BCD rebuild:

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

How to fix Vista/Window 7 when the boot files are missing
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

---

### Post by NEBRU on 2010-06-04
> **NEBRU said:**
> I am working on the W7 restore from live CD, I'll let you know how it went.
 
I used W7 installation CD and testdisk after removing the extra files but still not working.

---

### Post by NEBRU on 2010-06-04
> **oldfred said:**
> We have seen where grub creates another /boot directory that interfers with the /Boot directory of windows. Usually the script shows if it has any grub files but even an empty directory can cause issues.
 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)
 
Also more advanced BCD rebuild:
 
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
 
How to fix Vista/Window 7 when the boot files are missing
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
 
[COLOR=black][FONT=Verdana]Thank you for the information oldfred, after some reading I already used some of the links and apparently the system does not recognize the partition for windows thru the CLI. For the testdisk procedure all I get in screen 6 is (**Rebuild BS**, **[FONT=Verdana]Org. BS or Dump[/FONT]**) no (**Backup BS**).[/FONT][/COLOR]

---

### Post by NEBRU on 2010-06-05
Thank you for all your time helping me with this problem. Is there anything else you think I should try? Or is my last option to reinstall? I am not an expert at this type of problems and this is all new to me, I already try everything I know for this.

---

### Post by oldfred on 2010-06-05
The script shows it as a valid windows, so I do not knwo why windows does not think it is windows. Are you not able to run checkdisk (chkdsk)?

Also the rebuildBCD in test disk is a choice when recover back up one does not work.

---

### Post by NEBRU on 2010-06-05
> **oldfred said:**
> The script shows it as a valid windows, so I do not knwo why windows does not think it is windows. Are you not able to run checkdisk (chkdsk)?
 
Also the rebuildBCD in test disk is a choice when recover back up one does not work.
 
I have tried chkdsk /r and chkdsk /f, but i still get the message no OS found. Do you think it would be a good idea to use RebuildBS at screen 6 with testdisk?

---

### Post by oldfred on 2010-06-05
At this point we seem to be grasping at straws, so I would say yes. I still do not know why windows cannot see a NTFS partition and fix it itself.

---

### Post by NEBRU on 2010-06-06
> **oldfred said:**
> At this point we seem to be grasping at straws, so I would say yes. I still do not know why windows cannot see a NTFS partition and fix it itself.
 
[COLOR=black][FONT=Verdana][SIZE=2]It is now 12:47 am, after working on my problem for a few hours I did a testdisk rebuildBS and then I’ve used windows installation disk to recover my boot partition and I have Win 7 working but I seem to have lost my ubuntu partition somehow which is ok I will try to reinstall it later. Thank you so much to all the people for helping me solved this problem.[/SIZE][/FONT][/COLOR]

---

### Post by darkod on 2010-06-06
Probably just grub2 got overwritten with the win7 boot fils restore. No need to reinstall ubuntu again, just grub2. Since your ubuntu partition is /dev/sda5 you can reinstall from the cd in live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by NEBRU on 2010-06-06
> **darkod said:**
> Probably just grub2 got overwritten with the win7 boot fils restore. No need to reinstall ubuntu again, just grub2. Since your ubuntu partition is /dev/sda5 you can reinstall from the cd in live mode with:
 
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
 
Thank you darkod, one question. I don't see the ubuntu partition in the RESULT.TXT file or the partition table. will that command still work without it there? 
 
here is the RESULT file:
```
 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40a5f6c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5248    39668016+   7  HPFS/NTFS
/dev/sda2            7035        7297     1988280    c  W95 FAT32 (LBA)

Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for /boot/grub.
sda1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Windows/System32/winload.exe
sda2: _________________________________________________________________________
File system: vfat
Boot sector type: MSWIN4.1: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /IO.SYS /MSDOS.SYS /COMMAND.COM
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 * 63 79,336,095 79,336,033 7 HPFS/NTFS
/dev/sda2 106,354,080 110,330,639 3,976,560 c W95 FAT32 (LBA)
 
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/loop0 squashfs 
/dev/sda1 38A883B6A88370E4 ntfs IBM_PRELOAD 
/dev/sda2 3D4F-15F0 vfat IBM_SERVICE 
/dev/sda: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)

```

---

### Post by frantid on 2010-06-06
Nebru,

I'm glad you have it working.  Here you see the effect of the HPA.  From your last print out:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40a5f6c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5248    39668016+   7  HPFS/NTFS
/dev/sda2            7035        7297     1988280    c  W95 FAT32 (LBA)

```And from your first print out after Ubuntu install:

```
ubuntu@ubuntu-laptop:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40a5f6c9
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4939    39668016+   7  HPFS/NTFS
/dev/sda2            4939        7296    18935809    5  Extended
/dev/sda5            4939        7192    18100224   83  Linux
/dev/sda6            7193        7296      834560   82  Linux swap / Solaris

```

Note the difference in the number of heads. 240 vs. 255.  The disk actually has 255, but the hpa reports via the bios 240 heads.  

I do not know how to repartion on install so that the ubuntu install uses the bios 240 head over the drives 255 heads.  But I'm sure one of the others will know.

---

### Post by NEBRU on 2010-06-06
> **NEBRU said:**
> Thank you darkod, one question. I don't see the ubuntu partition in the RESULT.TXT file or the partition table. will that command still work without it there? 
 
here is the RESULT file:
```
 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40a5f6c9
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5248    39668016+   7  HPFS/NTFS
/dev/sda2            7035        7297     1988280    c  W95 FAT32 (LBA)
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for /boot/grub.
sda1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Windows/System32/winload.exe
sda2: _________________________________________________________________________
File system: vfat
Boot sector type: MSWIN4.1: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /IO.SYS /MSDOS.SYS /COMMAND.COM
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 * 63 79,336,095 79,336,033 7 HPFS/NTFS
/dev/sda2 106,354,080 110,330,639 3,976,560 c W95 FAT32 (LBA)
 
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/loop0 squashfs 
/dev/sda1 38A883B6A88370E4 ntfs IBM_PRELOAD 
/dev/sda2 3D4F-15F0 vfat IBM_SERVICE 
/dev/sda: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)

```
 
one question?

---

### Post by darkod on 2010-06-06
Your ubuntu partition seems gone, or at least not recognized. No, in that case the command will not work.

You weren't deleting any partitions with the win7 installer right? Did you just use the same partition to install onto?

---

### Post by NEBRU on 2010-06-06
> **darkod said:**
> Your ubuntu partition seems gone, or at least not recognized. No, in that case the command will not work.
 
You weren't deleting any partitions with the win7 installer right? Did you just use the same partition to install onto?
  I just used the bootrec.exe to fix boot and MBR. But before that windows did a self repair and then when into partition not found rescue grub> after that I did the bootrec. exe fix and boot into windows 7.

---

### Post by darkod on 2010-06-06
> **NEBRU said:**
> I just used the bootrec.exe to fix boot and MBR. But before that windows did a self repair and then when into partition not found rescue grub> after that I did the bootrec. exe fix and boot into windows 7.

What is this self-repair? If it's a process running the recovery/restore process, very often it involves deleting partitions on your disk. Maybe that's one of the reasons.

---

### Post by NEBRU on 2010-06-06
Yes, I think that is what happened, I will try to install lucid again on its own partition and hopefully I won't have any problems that way. Thank you darkod. catch you later.

---

