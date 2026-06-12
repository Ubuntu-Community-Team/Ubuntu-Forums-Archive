---
title: "dualboot doesn't work anymore"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by frankyboy1211 on 2010-12-20
hello, I had my notebook set to dualboot with Ubuntu 10.10, OpenSUSE and Windows 7. After an update my grub only recognises the Ubuntu partition, so I cannot boot the other ones. Does anybody know how I can solve this?


Thanks in advance, Frank

---

### Post by Quackers on 2010-12-20
Have you tried running ```
sudo update-grub
``` in a terminal?

---

### Post by wilee-nilee on 2010-12-20
> **frankyboy1211 said:**
> hello, I had my notebook set to dualboot with Ubuntu 10.10, OpenSUSE and Windows 7. After an update my grub only recognises the Ubuntu partition, so I cannot boot the other ones. Does anybody know how I can solve this?


Thanks in advance, Frank

There is a bootscript link in my signature, generally since it gives a variety of what is where information,it helps to run it and post all the text from the generated file. 

Post it in code tags by opening a reply click on the # in the reply panel and paste all the text in between the code tags.

Quackers method though is the starting point, to see if that fixes the problem.

---

### Post by frankyboy1211 on 2010-12-20
When I use Quackers method, the system only recognizes the Ubuntu partition, so that one is unfortunately no good...

grtz, Frank

---

### Post by wilee-nilee on 2010-12-20
> **frankyboy1211 said:**
> When I use Quackers method, the system only recognizes the Ubuntu partition, so that one is unfortunately no good...

grtz, Frank

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Feel free to ask any questions the bootscript is a challenge the first time, at least it was for me.;)

---

### Post by garvinrick4 on 2010-12-20
All three use different grubs did you just install one? Something has changed or been done
to make it stop working. If you do not want to do the bootscript (takes 30 seconds) then what was changed?

---

### Post by frankyboy1211 on 2010-12-20
The outcome is saves in a txt file. when I copy the contents I cannot submit them because it is too long...

grtz, Frank

---

### Post by garvinrick4 on 2010-12-20
Highlight the whole text file and right click hit copy and then paste it in your thread in a message box. Highlight the whole thing again and hit the little # sign in upper right of message box  then hit submit on bottom.

---

### Post by wilee-nilee on 2010-12-20
> **frankyboy1211 said:**
> The outcome is saves in a txt file. when I copy the contents I cannot submit them because it is too long...

grtz, Frank

Open the file, click edit in the top panel-select all, the right click on the text-copy.

Open a reply or have one open, left click the mouse in the # in the panel and paste the text between the code tags.

---

### Post by garvinrick4 on 2010-12-20
Go ahead and help him wilee-nilee we keep typing at same time.

---

### Post by wilee-nilee on 2010-12-20
> **garvinrick4 said:**
> Go ahead and help him wilee-nilee we keep typing at same time.

I'm going to crash very soon, it happens.;)

---

### Post by frankyboy1211 on 2010-12-20
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 362528640 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

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

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,391,103   312,569,856   7 HPFS/NTFS
/dev/sda3         313,391,104   332,881,841    19,490,738   7 HPFS/NTFS
/dev/sda4         332,883,966   625,141,759   292,257,794   f W95 Ext d (LBA)
/dev/sda5         332,883,968   337,092,607     4,208,640  82 Linux swap / Solaris
/dev/sda6         337,094,656   379,037,695    41,943,040  83 Linux
/dev/sda7         379,039,744   524,388,186   145,348,443  83 Linux
/dev/sda8         524,388,352   620,929,023    96,540,672  83 Linux
/dev/sda9         620,931,072   625,141,759     4,210,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D85A356D5A354A10                       ntfs       SYSTEM                        
/dev/sda2        9AF43941F4392145                       ntfs       WINDOWS                       
/dev/sda3        A8D83B6DD83B38C0                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3f3cd8af-d879-4fcb-9d09-923a83f4d8b2   swap                                     
/dev/sda6        5ab1e298-4816-4d71-94a8-f916257c0a78   ext4                                     
/dev/sda7        9c4e6608-56a1-4461-83ca-ad5ca210dc5f   ext4                                     
/dev/sda8        9f332eec-11d8-4601-852f-3430efbf1de6   ext4                                     
/dev/sda9        a3b59cc2-f5c8-4a71-aa58-8e40efda7bef   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Mon Nov 29 19:20:01 CET 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,5)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.3 - 2.6.34.7-0.5
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.34.7-0.5-desktop root=/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part6 resume=/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part5 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.34.7-0.5-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3 - 2.6.34.7-0.5
    root (hd0,5)
    kernel /boot/vmlinuz-2.6.34.7-0.5-desktop root=/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part6 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.34.7-0.5-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    makeactive
    chainloader +1


=============================== sda6/etc/fstab: ===============================

/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part6 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part7 /home                ext4       acl,user_xattr        1 2
/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part2 /windows/C           ntfs-3g    defaults 0 0
/dev/disk/by-id/ata-TOSHIBA_MK3263GSXN_Z9VDS6W8S-part3 /windows/D           ntfs-3g    defaults 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda6: Location of files loaded by Grub: ===================


 187.8GB: boot/grub/menu.lst
 185.6GB: boot/grub/stage2
 185.7GB: boot/initrd
 185.7GB: boot/initrd-2.6.34.7-0.5-desktop
 185.7GB: boot/vmlinuz
 185.7GB: boot/vmlinuz-2.6.34.7-0.5-desktop

=========================== sda8/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9f332eec-11d8-4601-852f-3430efbf1de6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9f332eec-11d8-4601-852f-3430efbf1de6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9f332eec-11d8-4601-852f-3430efbf1de6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9f332eec-11d8-4601-852f-3430efbf1de6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 9f332eec-11d8-4601-852f-3430efbf1de6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=9f332eec-11d8-4601-852f-3430efbf1de6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=a3b59cc2-f5c8-4a71-aa58-8e40efda7bef none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 298.6GB: boot/grub/core.img
 303.0GB: boot/grub/grub.cfg
 312.4GB: boot/initrd.img-2.6.35-22-generic
 312.5GB: boot/initrd.img-2.6.35-23-generic
 298.6GB: boot/vmlinuz-2.6.35-22-generic
 298.6GB: boot/vmlinuz-2.6.35-23-generic
 312.5GB: initrd.img
 312.4GB: initrd.img.old
 298.6GB: vmlinuz
 298.6GB: vmlinuz.old
```

---

### Post by sikander3786 on 2010-12-20
The experts *Quackers*, *wilee-nilee* and *garvinrick4* seem away so I am jumping in :-)

It isn't even listing your OpenSUSE install. Do you want that to be detected or you just want to dual-boot Windows and Ubuntu and plan to format the OpenSUSE partition?

Regarding Windows, you'll need to boot a Windows install/repair disc and perform startup repair 3 times at least. Once you are able to boot Windows independent of Grub, you'll need to re-install Grub.

If you don't have a Windows repair/install disc, grab one here. Its legit :-)

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

If startup repair does't seem to fix the problem, try bootrec.exe from command prompt. See here.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once able to boot Windows, boot an Ubuntu _Maverick/Lucid/Karmic_ Live CD/USB and do these commands.

```
sudo mount /dev/sda8 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR="Red"]a[/COLOR]
```

Note, for the second command it is just sda without an integer.

Reboot and boot Ubuntu. Hopefully it should list Windows now. If it still doesn't, from installed Ubuntu's Terminal,

```
sudo update-grub
```

Good Luck!

---

### Post by theasprint on 2010-12-20
Hi,

To sikander3786: 
Just for learning purposes, what is in sda6?
And what does the command sudo mount /dev/sda8 /mnt do?
And for the sudo grub-install command, installing it at /dev/sda is because?

You're so PRO! :D

Thanks!

---

### Post by frankyboy1211 on 2010-12-20
When I load the windows repair disk and perform a startup repair, It doesn't do anything....

grtz, Frank

---

### Post by sikander3786 on 2010-12-20
> **frankyboy1211 said:**
> When I load the windows repair disk and perform a startup repair, It doesn't do anything....

grtz, Frank
Use bootrec.exe. Follow **wilee-nilee's** instructions here.

[http://newyork.ubuntuforums.org/showpost.php?p=10069174&postcount=11](http://newyork.ubuntuforums.org/showpost.php?p=10069174&postcount=11)

---

### Post by Quackers on 2010-12-20
> **theasprint said:**
> Hi,

To sikander3786: 
Just for learning purposes, what is in sda6?
And what does the command sudo mount /dev/sda8 /mnt do?
And for the sudo grub-install command, installing it at /dev/sda is because?

You're so PRO! :D

Thanks!

Opensuse is in sda6 (and grub legacy)
sudo mount /dev/sda8 /mnt  mounts the Ubuntu partition so that the grub-install command to /dev/sda (which is the mbr of the drive) knows where to look for the rest of the boot files for Ubuntu.

---

### Post by frankyboy1211 on 2010-12-20
ok, so the Windows repair disk helped a lot. I was able to boot W7. When I reinstalled Ubuntu and both systems where choosable in the grub menu. Unfortunately, after an update through Update-Manager, W7 did not appear in the menu anymore, so it is probably an error in the new kernel update. :cry:


grtz, Frank

---

### Post by rieckm on 2010-12-20
> **quackers said:**
> have you tried running ```
sudo update-grub
``` in a terminal?
i ;}

---

### Post by sikander3786 on 2010-12-20
Kernel Upgrade shouldn't cause a problem. I have updated my Maverick a few hours ago and everything is working fine. Then why it isn't at your end :confused:

You mean you repaired Windows 7 and then _re-installed_ the whole Ubuntu OS? That wasn't needed. Only Grub re-install would have solved the problem.

Anyhow, can you please post the output of boot script once more?

And in case you decide to repair Windows 7 startup and once again re-install Ubuntu, I would request to post the output of boot script of 2 times then. Once before applying the updates and once after applying the updates. So can see the difference then ;-)

Thanks.

---

### Post by frankyboy1211 on 2010-12-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   313,391,103   312,569,856   7 HPFS/NTFS
/dev/sda3         313,391,104   332,881,841    19,490,738   7 HPFS/NTFS
/dev/sda4         332,883,966   625,141,759   292,257,794   f W95 Ext d (LBA)
/dev/sda5         332,883,968   337,092,607     4,208,640  82 Linux swap / Solaris
/dev/sda6         620,931,072   625,141,759     4,210,688  82 Linux swap / Solaris
/dev/sda7         337,094,656   620,926,975   283,832,320  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D85A356D5A354A10                       ntfs       SYSTEM                        
/dev/sda2        9AF43941F4392145                       ntfs       WINDOWS                       
/dev/sda3        A8D83B6DD83B38C0                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3f3cd8af-d879-4fcb-9d09-923a83f4d8b2   swap                                     
/dev/sda6        a3b59cc2-f5c8-4a71-aa58-8e40efda7bef   swap                                     
/dev/sda7        52a4075e-d7eb-443e-9758-89ae30f2b94b   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/WINDOWS           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=52a4075e-d7eb-443e-9758-89ae30f2b94b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=52a4075e-d7eb-443e-9758-89ae30f2b94b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=52a4075e-d7eb-443e-9758-89ae30f2b94b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=52a4075e-d7eb-443e-9758-89ae30f2b94b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 52a4075e-d7eb-443e-9758-89ae30f2b94b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=52a4075e-d7eb-443e-9758-89ae30f2b94b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f3cd8af-d879-4fcb-9d09-923a83f4d8b2 none            swap    sw              0       0
/dev/sda6       none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 209.2GB: boot/grub/core.img
 224.3GB: boot/grub/grub.cfg
 173.8GB: boot/initrd.img-2.6.35-22-generic
 173.8GB: boot/initrd.img-2.6.35-23-generic
 209.2GB: boot/vmlinuz-2.6.35-22-generic
 209.2GB: boot/vmlinuz-2.6.35-23-generic
 173.8GB: initrd.img
 173.8GB: initrd.img.old
 209.2GB: vmlinuz
 209.2GB: vmlinuz.old
```

---

### Post by sikander3786 on 2010-12-20
I would recommend to do a startup repair once more and then try re-installing Grub and not the whole Ubuntu. Lets see how that goes.

For re-installing Grub, you need to replace sda8 from my previous post with sda7 as Ubuntu is lying on sda7 now. Else, the same commands.

---

### Post by garvinrick4 on 2010-12-20
# I noticed you removed OpenSUSE if you want to reinstall it when it gets to where
 you want to install grub, do not install any grub at all. The Install program that
OpenSUSE uses is called anaconda and it has a very straight forward place with a 
check mark not to install grub at all, very convenient for dual or more booters. (openSuse uses grub-legacy not grub2) do not play together well at all.
# When through installing OpenSuse go into Ubuntu and; (will put in grub-cfg and boot menu.)
```
sudo update-grub
```#This is practical experience not theoretical.
# Do this for any other Operating system you want to use.
# The grub2 is the way of the future in Ubuntu why not use it for all OS's.
## Looks like you have a boot partition labeled SYSTEM has to be mounted if you 
ever reinstall grub2. In Live CD (Boot ubuntu install cd and use Try Ubuntu). code below
```

[CODE]sudo mkdir /media/SYSTEM
``````
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/SYSTEM
``````
sudo mount /dev/sda7 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root  /dev/sda
``````
sudo umount /media/SYSTEM
``````
sudo umount /media/root
```# If you look in your boot script you will see sda1 is already labeled SYSTEM
# We used root as a directory for sda7 (ubuntu install) has no label.
[/code][U]
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[/U][Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

