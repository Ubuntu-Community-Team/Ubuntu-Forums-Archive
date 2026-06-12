---
title: "HELP!!!!  unable to boot into windows 7 after ubuntu installed!!!"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by captainapoorv on 2010-07-15
Hi, i have dell studio 1557 laptop......i installed ubuntu 10.04 yesterday and grub menu came up with ubuntu and "windows 7 (loader) (/dev/sda2)" so i booted into ubuntu and it worked fine.... then i restarted and booted in windows 7 and it worked fine too..... after i restarted there was message that "unable to load module" and " no os found" so i installed ubuntu again and got to know that windows loader overwrites MBR everytime it boots so i installed grub on /dev/sda2 where windows loader AND its recovery partition is....  

now problem is when i boot in ubuntu everything is great but when is select Windows 7 option in  grub screen goes black and again grub comes up.... so  i am not able to boot into windows........ and i dont want to resinstall.......!!!!

please please help!!!!

---

### Post by tommcd on 2010-07-15
Try booting into Ubuntu, open a terminal, and run:
```
sudo update-grub
```
Hopefully it will find your Win7 and add it to the grub menu.
If that does not help, boot into Ubuntu and run:
```
sudo fdisk -l
``` (That is a lowercase "L") and post the output here.
Also, run the swiss army knife for Ubuntu boot problems, the **bootinfo script** (from forum member meierfra), 
and post the output here. Just download it to your home directory:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
You may need to make it executable to run it:
```
chmod +x boot_info
``` and hit the TAB key to autocomplete the file name.
Then run the script with sudo. It will create a RESULTS.txt file. Post the output of that file here.

---

### Post by captainapoorv on 2010-07-16
thanks for replying..... when i run update-grub it finds "Windows 7 (loader) (on /dev/sda2)...... i think i messed with windows loader when i installed grub on sda2..... but then i removed it..... by the way i am posting results here....


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf5ac2f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       36364   276693667+   7  HPFS/NTFS
/dev/sda4           36365       38913    20474812    5  Extended
/dev/sda5           36365       38276    15358108+  83  Linux
/dev/sda6           38277       38913     5116671   82  Linux swap / Solaris

```




```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 595811915 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   584,187,659   553,387,335   7 HPFS/NTFS
/dev/sda4         584,187,721   625,137,344    40,949,624   5 Extended
/dev/sda5         584,187,723   614,903,939    30,716,217  83 Linux
/dev/sda6         614,904,003   625,137,344    10,233,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        2090464C9046289C                       ntfs       RECOVERY                      
/dev/sda3        C0F8486BF84861B0                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        401cb051-7222-4a84-a947-f18fc13bf9d5   ext3                                     
/dev/sda6        088c3dbb-b59b-41b4-8e14-587617c407c5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 401cb051-7222-4a84-a947-f18fc13bf9d5
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
search --no-floppy --fs-uuid --set 401cb051-7222-4a84-a947-f18fc13bf9d5
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
    search --no-floppy --fs-uuid --set 401cb051-7222-4a84-a947-f18fc13bf9d5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=401cb051-7222-4a84-a947-f18fc13bf9d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 401cb051-7222-4a84-a947-f18fc13bf9d5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=401cb051-7222-4a84-a947-f18fc13bf9d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 401cb051-7222-4a84-a947-f18fc13bf9d5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 401cb051-7222-4a84-a947-f18fc13bf9d5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2090464c9046289c
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
UUID=401cb051-7222-4a84-a947-f18fc13bf9d5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=088c3dbb-b59b-41b4-8e14-587617c407c5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 302.3GB: boot/grub/core.img
 302.3GB: boot/grub/grub.cfg
 302.2GB: boot/initrd.img-2.6.32-21-generic
 302.2GB: boot/vmlinuz-2.6.32-21-generic
 302.2GB: initrd.img
 302.2GB: vmlinuz
```

---

### Post by tommcd on 2010-07-16
This seems to be your problem as near as I can tell.
```

sda2:
_______________________________________________________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 595811915 of the same hard drive for 
                       core.img, [B]but core.img can not be found at this 
                       location.[/B] No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   **/bootmgr /Boot/BCD**

```
Were you trying to use another boot manager like EasyBCD or something?
Try booting from the Ubuntu live CD and reinstall grub2 to the MBR like it says in the first method (simplest) listed here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Then boot Ubuntu and run:
```
sudo update-grub
``` again and see if you can then boot Win7.
If that does not work I suppose you could try "method 2" in that link.
> i think i messed with windows loader when i installed grub on sda2..... but then i removed it.....
If you "messed with" any of the boot files on Win7 I would have no idea how to fix your Windows system. I have never used Windows 7.

---

### Post by oldfred on 2010-07-16
You need to get the windows boot into the windows boot sector of sda2.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Sef on 2010-07-16
How did you partition the hard drive?

---

### Post by wilee-nilee on 2010-07-16
> **oldfred said:**
> You need to get the windows boot into the windows boot sector of sda2.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I think this is the correct fix, check out this link for Dell Data Safe in add remove in windows.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

