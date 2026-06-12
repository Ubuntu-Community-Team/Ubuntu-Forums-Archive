---
title: "Unable to boot Windows7 from a second HDD"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by M10-85 on 2010-12-28
Hi All,

I want to create a dual boot between Windows 7 and Ubuntu.

 I have done the following:
1. I installed Win7 on my second SATA drive WD740AD.
 2. Then I installed Ubuntu on my first SATA drive WD5000A.
 
 When I boot my machine, the machine will always boot linux. 
I can't even choose Windows 7.
 
My knowledge of Linux is very limited. I have looked for information on the web and found some information about grub but I cant make it work. Mostly all the information is about installing Win7 and Linux on 1 HDD.

If you need some screenshots or additional information, please let me know.

 Regards,
 Maarten

---

### Post by dino99 on 2010-12-28
welcome,

dont mind about how much hdds are on the system and where OS are installed, grub2 will find them. You only need to boot on the first drive (hdd) into the bios.

Boot on ubuntu, then into a terminal (Applications Accessories Terminal) run the command:

sudo update-grub

---

### Post by M10-85 on 2010-12-28
> **dino99 said:**
> welcome,

dont mind about how much hdds are on the system and where OS are installed, grub2 will find them. You only need to boot on the first drive (hdd) into the bios.

I don't exactly know what you mean by this. Since I am on Linux on my first HDD this should be okay?

> **dino99 said:**
> Boot on ubuntu, then into a terminal (Applications Accessories Terminal) run the command:

sudo update-grub


This is the result of the command sudo update grub:

maarten@PC-linux:~$ sudo update-grub
[sudo] password for maarten: 

Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found Sabily background: sabily-manarat.png
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

I will restart now and test if it worked.

---

### Post by M10-85 on 2010-12-28
Didn't work.
After a reboot the machine automatically opens a Linux start-up screen (see attachment).
I still can't choose Windows 7.

---

### Post by Quackers on 2010-12-28
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by M10-85 on 2010-12-28
Done, hopefully you can explane the problem in noob-language ;-)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 74.4 GB, 74355769344 bytes
255 koppen, 63 sectoren/spoor, 9039 cilinders, totaal 145226112 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   139,214,847   139,212,800  83 Linux
/dev/sda2         139,216,894   145,225,727     6,008,834   5 Extended
/dev/sda5         139,216,896   145,225,727     6,008,832  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Schijf /dev/sdb: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        303e458d-d7e3-430b-b9d7-c5ecb5fac612   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9d6a8836-ff8a-47e0-8766-f48466afd865   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        701229EC1229B7CC                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/05_sabily_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
insmod png
if background_image /usr/share/images/grub/sabily-manarat.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_sabily_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=303e458d-d7e3-430b-b9d7-c5ecb5fac612 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=303e458d-d7e3-430b-b9d7-c5ecb5fac612 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=303e458d-d7e3-430b-b9d7-c5ecb5fac612 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=303e458d-d7e3-430b-b9d7-c5ecb5fac612 ro single  splash
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 303e458d-d7e3-430b-b9d7-c5ecb5fac612
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=303e458d-d7e3-430b-b9d7-c5ecb5fac612 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9d6a8836-ff8a-47e0-8766-f48466afd865 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
   2.2GB: boot/initrd.img-2.6.35-22-generic
   2.6GB: boot/initrd.img-2.6.35-24-generic
   4.4GB: boot/vmlinuz-2.6.35-22-generic
   4.4GB: boot/vmlinuz-2.6.35-24-generic
   2.6GB: initrd.img
   2.2GB: initrd.img.old
   4.4GB: vmlinuz
   4.4GB: vmlinuz.old

```

---

### Post by oldfred on 2010-12-28
Normally it is better to install windows on the first drive, as that is what it wants to boot from. Windows installs a hidden 100MB boot/recovery partition that starts the boot process. It looks like it installed that hidden partition on sda and you overwrote it when you installed Ubuntu.

Some have had issues with windows on sdb and Ubuntu on sda. You might want to switch drives in computer case, if you can. If you do this, do it before running the repairs below as windows has to know drive it is on and does not like changes. Ubuntu will search for correct drive and boot just fine even if it is moved about.

You need to run windows repairs on the windows partition. It will repair & replace the missing boot files, but I am not sure if it recreates the windows recovery environment or not. If you do not have a windows repair CD you need to have one anyway.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Quackers on 2010-12-28
Grub cannot find Windows, and Windows will not boot, because its first 2 boot files are missing. As is its boot flag. Did you move Windows by any chance?

What I would suggest is frist to install gparted via synaptic package manager and then run it. It will scan your discs and display all recognised partitions.
Near the top right is a small box which will at first display /dev/sda. It will have a small downward arrow next to it. Click on that and select /dev/sdb from the drop down menu.
This will display the sdb1 partition (which is Windows). Right-click on this partition and select "Manage flags", then in the box that pops up check the box marked "boot", then close that window. 
Now click on the green tick mark in the toolbar (if it's lit) to apply the change.

You will now need to replace the missing boot files.
Do you have a Windows installation disc or repair disc (not a recovery dvd)?

---

### Post by M10-85 on 2010-12-28
> **Quackers said:**
> Grub cannot find Windows, and Windows will not boot, because its first 2 boot files are missing. As is its boot flag. Did you move Windows by any chance?

No, I didn't move Windows

I did the following:

1. I formatted both the HDD's with KillDisk. 
2. Installed Windows on the second (biggest) HDD. 

Windows worked and I installed the drivers etc. 
The first HDD wasn't visible because KillDisk made it entirely clean.

3. The next day I installed Ubuntu on my first HDD.

After a reboot it's only possible to boot Linux (this thread).

> **Quackers said:**
> What I would suggest is frist to install gparted via synaptic package manager and then run it. It will scan your discs and display all recognised partitions.
Near the top right is a small box which will at first display /dev/sda. It will have a small downward arrow next to it. Click on that and select /dev/sdb from the drop down menu.
This will display the sdb1 partition (which is Windows). Right-click on this partition and select "Manage flags", then in the box that pops up check the box marked "boot", then close that window.

Done, see attachment (ongebruikt is dutch for unused).

> **Quackers said:**
> Now click on the green tick mark in the toolbar (if it's lit) to apply the change.

No need to press this button?

> **Quackers said:**
>  You will now need to replace the missing boot files.
Do you have a Windows installation disc or repair disc (not a recovery dvd)?

The system doesn't ask me for missing boot files, the option boot is now enabled for the Windows-disk.

I'll restart and check again.

---

### Post by M10-85 on 2010-12-28
After a reboot the system didn't even show the bios (just a black screen). 
There was one long  beeb and three or four short beebs. 
This happed twice, the third time it  booted Linux without the possibility to select Windows.

> **Quackers said:**
> You will now need to replace the missing boot files.
Do you have a Windows installation disc or repair disc (not a recovery dvd)?

I have a installation disk of Windows 7, how can I add the missing boot files?

---

### Post by Quackers on 2010-12-28
If you can select the second hard drive (Windows drive) and make it the first boot device it should make it easier to repair the boot files.
If you then boot from the Windows installation disc and press any key to boot from it then press the R when prompted to enter the recovery console. Then select "repair my computer" then run the "startup repair". It may, or may not find your Windows installation first time. It may require 3 runs of the startup repair, as it can only repair one thing at a time.

---

### Post by M10-85 on 2010-12-28
Thnx for all the help guys!
I am going to reinstall Windows 7 on my first HDD and Ubuntu on my second HDD, hopfully this will solve the problem.

I'll try this tommorow.

---

### Post by Quackers on 2010-12-28
As oldfred suggested before, can't you physically swap the drives over in the case?

---

### Post by M10-85 on 2010-12-28
It was easier for me to reinstall both OS' s.
Its working fine now!!

Now its time to find a way to change the boot default and cleaning up the menu.

---

