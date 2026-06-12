---
title: "System won't boot after update.."
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by qwerty123321 on 2010-01-11
I just allowed Update Manager to install the latest security updates to the Linux kernel, header and xorg and clicked on restart system. After selecting Ubuntu from the system's boot manager I'm dropped into a Grub command line and don't have any idea what to do next.

I'm running Ubuntu 9.10 inside Windows 7 on a Toshiba L500 laptop using the Wubi setup.

---

### Post by ajgreeny on 2010-01-11
Boot into windows and follow this info.  That should do it.
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

---

### Post by qwerty123321 on 2010-01-11
> **ajgreeny said:**
> Boot into windows and follow this info.  That should do it.
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)
thank you so much!!

---

### Post by Raditude on 2010-01-18
Had the same problem, and this worked for me. Thank You.

---

### Post by rlridenour on 2010-01-31
Thanks, this cleared up what I thought was a mysterious problem.

---

### Post by ostlerc on 2010-03-04
Thank you that also fixed the problem for me!

---

### Post by ng0n on 2010-03-05
BRILLIANT !!!  I'm too embarassed to tell you how long I've been working on making my system boot from the grub: prompt  :)
THANK YOU VERY MUCH.  / ng0n

---

### Post by badriias on 2010-03-05
hey i'm new to linux and i didnt understand how to do what u said.. can u say in detail? 
if what u said means, i need to alter the file in /boot/grub/menu, then  i don have that file there.. i have no file named menu in that directory..

---

### Post by johnny9966 on 2010-03-05
Thanks! My problem i also solved.

---

### Post by altheablue on 2010-03-05
Thank you!

@ badriias - just follow the link here and then the next link & save that file ("wubildr") under your c: drive. (it will replace the one already there.) then reboot.

---

### Post by badriias on 2010-03-05
thanks for replying.. Actually i didnt have that file in c:. But anyway i have pasted it there and tried restarting.. It didnt work

---

### Post by presence1960 on 2010-03-05
> **badriias said:**
> thanks for replying.. Actually i didnt have that file in c:. But anyway i have pasted it there and tried restarting.. It didnt work

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by badriias on 2010-03-05
Hi.. thanks a lot for replying.. I did that and this is wat i have got..

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x032c032c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,560,639   230,645,205   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372   7 HPFS/NTFS
/dev/sda6         163,830,933   188,410,319    24,579,387  83 Linux
/dev/sda7         188,410,383   306,263,159   117,852,777  83 Linux
/dev/sda8         306,263,223   310,456,124     4,192,902  82 Linux swap / Solaris
/dev/sda9    *    310,456,188   312,560,639     2,104,452  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        92E83B53E83B3537                       ntfs       Windows                       
/dev/sda5        A8E4A32DE4A2FCA6                       ntfs                                     
/dev/sda6        83f9bef0-f69a-4981-a000-64ef2faa5a42   ext3       root                          
/dev/sda7        6bd2b21f-6652-4fb1-a6b6-7000811f5eaf   ext3                                     
/dev/sda8        d0a6ff66-6685-4579-ac3c-f9157d5203ff   swap                                     
/dev/sda9        4694a36f-7cd7-4438-8961-24bf39fe3bbd   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw)
/dev/sda9        /boot                    ext3       (rw)
/dev/sr0         /media/cdrom0            iso9660    (rw,nosuid,nodev,utf8,user=santiago)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=83f9bef0-f69a-4981-a000-64ef2faa5a42 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda9 during installation
UUID=4694a36f-7cd7-4438-8961-24bf39fe3bbd /boot           ext3    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=6bd2b21f-6652-4fb1-a6b6-7000811f5eaf /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=d0a6ff66-6685-4579-ac3c-f9157d5203ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  83.9GB: initrd.img
  83.8GB: vmlinuz

============================= sda9/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 83f9bef0-f69a-4981-a000-64ef2faa5a42
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4694a36f-7cd7-4438-8961-24bf39fe3bbd
    linux    /vmlinuz-2.6.31-14-generic root=UUID=83f9bef0-f69a-4981-a000-64ef2faa5a42 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4694a36f-7cd7-4438-8961-24bf39fe3bbd
    linux    /vmlinuz-2.6.31-14-generic root=UUID=83f9bef0-f69a-4981-a000-64ef2faa5a42 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 92e83b53e83b3537
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda9: Location of files loaded by Grub: ===================


 159.9GB: grub/core.img
 159.9GB: grub/grub.cfg
 159.9GB: grub/stage2
 158.9GB: initrd.img-2.6.31-14-generic
 158.9GB: vmlinuz-2.6.31-14-generic
```

---

### Post by presence1960 on 2010-03-05
> **badriias said:**
> Hi.. thanks a lot for replying.. I did that and this is wat i have got..

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x032c032c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   312,560,639   230,645,205   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372   7 HPFS/NTFS
/dev/sda6         163,830,933   188,410,319    24,579,387  83 Linux
/dev/sda7         188,410,383   306,263,159   117,852,777  83 Linux
/dev/sda8         306,263,223   310,456,124     4,192,902  82 Linux swap / Solaris
/dev/sda9    *    310,456,188   312,560,639     2,104,452  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        92E83B53E83B3537                       ntfs       Windows                       
/dev/sda5        A8E4A32DE4A2FCA6                       ntfs                                     
/dev/sda6        83f9bef0-f69a-4981-a000-64ef2faa5a42   ext3       root                          
/dev/sda7        6bd2b21f-6652-4fb1-a6b6-7000811f5eaf   ext3                                     
/dev/sda8        d0a6ff66-6685-4579-ac3c-f9157d5203ff   swap                                     
/dev/sda9        4694a36f-7cd7-4438-8961-24bf39fe3bbd   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda7        /home                    ext3       (rw)
/dev/sda9        /boot                    ext3       (rw)
/dev/sr0         /media/cdrom0            iso9660    (rw,nosuid,nodev,utf8,user=santiago)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=83f9bef0-f69a-4981-a000-64ef2faa5a42 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda9 during installation
UUID=4694a36f-7cd7-4438-8961-24bf39fe3bbd /boot           ext3    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=6bd2b21f-6652-4fb1-a6b6-7000811f5eaf /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=d0a6ff66-6685-4579-ac3c-f9157d5203ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  83.9GB: initrd.img
  83.8GB: vmlinuz

============================= sda9/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 83f9bef0-f69a-4981-a000-64ef2faa5a42
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4694a36f-7cd7-4438-8961-24bf39fe3bbd
    linux    /vmlinuz-2.6.31-14-generic root=UUID=83f9bef0-f69a-4981-a000-64ef2faa5a42 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4694a36f-7cd7-4438-8961-24bf39fe3bbd
    linux    /vmlinuz-2.6.31-14-generic root=UUID=83f9bef0-f69a-4981-a000-64ef2faa5a42 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 92e83b53e83b3537
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda9: Location of files loaded by Grub: ===================


 159.9GB: grub/core.img
 159.9GB: grub/grub.cfg
 159.9GB: grub/stage2
 158.9GB: initrd.img-2.6.31-14-generic
 158.9GB: vmlinuz-2.6.31-14-generic
```

Is there a reason you made your boot partition (sda9) at the end of the disk? Usually when one creates a boot partition it is because they have a BIOS that can not read past a certain point on the disk (usually 137 GB). In that case the boot partition must be within the area readable by BIOS or booting will fail.

Also those instructions you followed were for a wubi install which you do not have. You can safely delete that wubuilder file from your windows partition- it is not needed.

Everything seems to be in order - the only thing I can think is your BIOS can not read your sda9 /boot partition? You need to find out if your BIOS can read the entire disk. 

Here is the location of the files your sda9 uses to boot:

```
=================== sda9: Location of files loaded by Grub: ===================


 159.9GB: grub/core.img
 159.9GB: grub/grub.cfg
 159.9GB: grub/stage2
 158.9GB: initrd.img-2.6.31-14-generic
 158.9GB: vmlinuz-2.6.31-14-generic
```

---

### Post by Barryathome on 2010-03-06
Thanks! That patch did the job. :p

---

### Post by badriias on 2010-03-06
> **presence1960 said:**
> Is there a reason you made your boot partition (sda9) at the end of the disk? Usually when one creates a boot partition it is because they have a BIOS that can not read past a certain point on the disk (usually 137 GB). In that case the boot partition must be within the area readable by BIOS or booting will fail.

Also those instructions you followed were for a wubi install which you do not have. You can safely delete that wubuilder file from your windows partition- it is not needed.

Everything seems to be in order - the only thing I can think is your BIOS can not read your sda9 /boot partition? You need to find out if your BIOS can read the entire disk. 

Here is the location of the files your sda9 uses to boot:

```
=================== sda9: Location of files loaded by Grub: ===================


 159.9GB: grub/core.img
 159.9GB: grub/grub.cfg
 159.9GB: grub/stage2
 158.9GB: initrd.img-2.6.31-14-generic
 158.9GB: vmlinuz-2.6.31-14-generic
```


Hey presence!! thanks a lot.. i have repartitioned boot to sda6 and now its working great.. thanks a lot.. if i hadnt got the solution, i would have hated ubuntu big time and would ve continued with windows.. i ll also explore more and try to help people with ubuntu.. :)

---

### Post by presence1960 on 2010-03-06
> **badriias said:**
> Hey presence!! thanks a lot.. i have repartitioned boot to sda6 and now its working great.. thanks a lot.. if i hadnt got the solution, i would have hated ubuntu big time and would ve continued with windows.. i ll also explore more and try to help people with ubuntu.. :)

Glad you got it working, enjoy ubuntu! If you want to increase your knowledge about linux and computers in general this community is the place to be.

---

### Post by TheBane on 2010-03-06
> **ajgreeny said:**
> Boot into windows and follow this info.  That should do it.
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

Gawd, I love you guys... :p lol Yeah this worked like a charm for me. Only issue I have is that I have to manually alter the insmod ntfs line every time I boot grub. Is this something that's a one shot deal? Or do I have to make that command change permanent? If so, which file do I edit in Ubuntu?

KTHXBAI

---

### Post by Akaevad on 2010-09-20
Awesome! Worked like a charm On Acer Aspire One with Windoze7 Farter. Cheers! :P

---

### Post by khairul nizam on 2010-11-26
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   161,292,599   161,292,537   7 HPFS/NTFS
/dev/sda2         161,292,661   312,580,095   151,287,435   f W95 Ext d (LBA)
/dev/sda5         161,292,663   265,350,979   104,058,317   7 HPFS/NTFS
/dev/sda6         265,351,168   310,532,095    45,180,928  83 Linux
/dev/sda7         310,534,144   312,580,095     2,045,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bbd1a499-4e8d-472a-a3c7-51704ae6d9a0   ext4                                     
/dev/sda1        D078565878563E02                       ntfs       OS                            
/dev/sda2: PTTYPE="dos" 
/dev/sda5        92F42C30F42C194D                       ntfs       Kerol                         
/dev/sda6        02d1bf07-ca7d-4657-a368-c5995ae6a87a   ext4                                     
/dev/sda7        282d5b24-f714-4b52-acf0-9057035eb868   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B67452AB74526E5D                       ntfs       thesevenstring                
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/window            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
search --no-floppy --fs-uuid --set 02d1bf07-ca7d-4657-a368-c5995ae6a87a
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 02d1bf07-ca7d-4657-a368-c5995ae6a87a
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
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 02d1bf07-ca7d-4657-a368-c5995ae6a87a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=02d1bf07-ca7d-4657-a368-c5995ae6a87a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 02d1bf07-ca7d-4657-a368-c5995ae6a87a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=02d1bf07-ca7d-4657-a368-c5995ae6a87a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 02d1bf07-ca7d-4657-a368-c5995ae6a87a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 02d1bf07-ca7d-4657-a368-c5995ae6a87a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d078565878563e02
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=02d1bf07-ca7d-4657-a368-c5995ae6a87a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=282d5b24-f714-4b52-acf0-9057035eb868 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 151.0GB: boot/grub/core.img
 144.6GB: boot/grub/grub.cfg
 151.0GB: boot/initrd.img-2.6.32-21-generic
 151.0GB: boot/vmlinuz-2.6.32-21-generic
 151.0GB: initrd.img
 151.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 01  |................|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 cd cd 33 06 00 fe  |............3...|
000001d0  ff ff 05 fe ff ff cf cd  33 06 bc 68 b1 02 00 00  |........3..h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script055.sh: line 892: 12221 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error
loop: can't delete device /dev/loop1: Device or resource busy
umount: /media/thesevenstring: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```


how about me?

---

### Post by mehta.mishal on 2010-12-18
hey thanks mate that solved my problem even if I am using 10.04

---

### Post by mschap on 2011-01-01
Well before I tried this I would get a list of places that Wubildr was not found which ended with no GRLDR found.  

After doing the copy of the file wubildr download I get only part way through the list and it sends me back to the boot list.  

How do I fix this? 

To be honest I need three files of the ubuntu desktop and the e-mail file for mozilla thunderbird which is stuck there.  Is there any way to fine access to these files?  Oh, to make it fun it is a laptop.

Frustrated and clueless.

In advance, thanks for any help

---

