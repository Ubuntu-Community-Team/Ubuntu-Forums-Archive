---
title: "Ubuntu10.04 don't load my Windows 7"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by northfly on 2011-01-15
Firstly, I installed my Windows 7 on sda2;

then, I installed Ubuntu 10.04 on sda1.

But the computer directly get into Ubuntu without listing the grub list.

How to get the Grub list back and make sure the Widows 7 is on the list? Thanks.

---

### Post by Quackers on 2011-01-15
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by lisati on 2011-01-15
There's a knack to calling the list up. If memory serves correctly (perhaps someone can correct me if I'm mistaken), with Grub2 it involves holding down the left shift key when booting.

---

### Post by northfly on 2011-01-15
> **Quackers said:**
> Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Thanks, Here we go!

>  
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  


---

### Post by northfly on 2011-01-15
> **Quackers said:**
> Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Thanks, Here we go!

>  
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  


---

### Post by Quackers on 2011-01-15
As half of your boot script is missing I can't tell where the boot flag is. I suspect it will be on sda2. Check that with gparted first.
Your Windows partition has 2 boot files missing. It will be necessary to replace those files by using the command prompt from within the Windows repair cd and entering bootrec.exe /fixmbr.
If this works, Windows will then boot directly. It will then be necessary to re-install grub via the Ubuntu live cd /usb

---

### Post by northfly on 2011-01-15
Again, the full information, please help, thanks!

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   199,999,487   199,997,440  83 Linux
/dev/sda2         199,999,488   399,998,975   199,999,488   7 HPFS/NTFS
/dev/sda3         400,001,022 2,866,266,111 2,466,265,090   5 Extended
/dev/sda5         400,001,024   599,998,463   199,997,440  83 Linux
/dev/sda6         600,000,512 2,647,994,367 2,047,993,856  83 Linux
/dev/sda7       2,647,996,416 2,866,266,111   218,269,696   7 HPFS/NTFS
/dev/sda4       2,866,266,112 2,930,276,351    64,010,240  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9   ext4                                     
/dev/sda2        387A90107A8FC8D8                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        c43363c3-d592-43fb-8604-d918755d8edc   swap                                     
/dev/sda5        cc66f8a9-7049-41d3-a408-18a99d8dfae2   ext4                                     
/dev/sda6        f10b6e08-a7ae-4207-9838-60ef2d68ff58   ext4                                     
/dev/sda7        2014AB9614AB6D8A                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sda5        /root                    ext4       (rw)
/dev/sda7        /D                       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9
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
search --no-floppy --fs-uuid --set 3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3ce4766f-d2a9-4307-aa7c-43a9f23ae8e9
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /D was on /dev/sda7 during installation
UUID=2014AB9614AB6D8A /D              ntfs    defaults,umask=007,gid=46 0       0
# /home was on /dev/sda6 during installation
UUID=f10b6e08-a7ae-4207-9838-60ef2d68ff58 /home           ext4    defaults        0       2
# /root was on /dev/sda5 during installation
UUID=cc66f8a9-7049-41d3-a408-18a99d8dfae2 /root           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=c43363c3-d592-43fb-8604-d918755d8edc none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
  47.3GB: boot/initrd.img-2.6.32-24-generic
  47.3GB: boot/vmlinuz-2.6.32-24-generic
  47.3GB: initrd.img
  47.3GB: vmlinuz


---

### Post by northfly on 2011-01-15
What can I do if I don't have the windows repair disk?

---

### Post by Quackers on 2011-01-15
From inside your Ubuntu desktop go to System > Admin > Synaptic Package Manager and install gparted (if you haven't already). Once installed it will be available under System > Admin > gparted. Open the program and when it has scanned your hard drive it will show your partitions. Right-click on sda2 and select "manage flags" then in the box that opens select "boot" then click OK. Then click on the green tick in the toolbar, to apply the change.
Then go here to download a Windows 7 recovery disc for your architecture (32 bit or 64 bit) and burn the image to a cd.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Then boot from that disc and repair the mbr by selecting the command prompt in the recovery console and running ```
bootrec.exe /fixmbr
``` Note the space between exe and /fixmbr
Then reboot and Windows should then boot directly. At that stage we can re-install grub.

---

### Post by northfly on 2011-01-15
I did what you said, but the system still cannot find windows 7 just like before.

---

### Post by Quackers on 2011-01-15
In 11 minutes? It took me longer than that to write it :-)

---

### Post by northfly on 2011-01-15
> **Quackers said:**
> From inside your Ubuntu desktop go to System > Admin > Synaptic Package Manager and install gparted (if you haven't already). Once installed it will be available under System > Admin > gparted. Open the program and when it has scanned your hard drive it will show your partitions. Right-click on sda2 and select "manage flags" then in the box that opens select "boot" then click OK. Then click on the green tick in the toolbar, to apply the change.
Then go here to download a Windows 7 recovery disc for your architecture (32 bit or 64 bit) and burn the image to a cd.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Then boot from that disc and repair the mbr by selecting the command prompt in the recovery console and running ```
bootrec.exe /fixmbr
``` Note the space between exe and /fixmbr
Then reboot and Windows should then boot directly. At that stage we can re-install grub.
Thanks, I did the bootrec.exe /fixmbr just now, it says successful, and then I reboot

and find there is no operating system in my hard disk.

and then I use ubuntu live cd method 1 to find the grub back.

now I can load ubuntu, while windows is still missing..

does the "gparted" do anything new? Should I try this again? Thanks.

---

### Post by Quackers on 2011-01-15
You need to move the boot flag first. Then run fixmbr with the Windows repair cd. No good the other way round!

---

### Post by northfly on 2011-01-15
Thanks, I did the gparted thing, and going to fix mbr now. Thanks.

---

### Post by northfly on 2011-01-15
Thanks, Quacker, I can load both systems now. But I still don't know what is the problem

What I did is only run the live cd to rescure grub after both systems are installed and windows is directly booted.

But that is the same status like after I ran ubuntu installation.

---

### Post by Quackers on 2011-01-15
So both Ubuntu and Windows now boot from the grub menu?

---

### Post by presence1960 on 2011-01-15
```
sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
[COLOR="Red"]Boot files/dirs: /Windows/System32/winload.exe[/COLOR]
```


You are missing boot files for windows 7. GRUB will never detect Windows nor will Windows boot without them. Compare mine:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
   [COLOR="Red"] Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]

```

---

