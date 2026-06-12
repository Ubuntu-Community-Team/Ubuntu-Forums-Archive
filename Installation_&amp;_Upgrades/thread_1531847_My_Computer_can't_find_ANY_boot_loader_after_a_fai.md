---
title: "My Computer can't find ANY boot loader after a failed attempt to fix the MBR"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Michael577 on 2010-07-15
Just as the title says. after installing the new 10.04 a awhile back, grub won't boot to my windows partition on my other hard drive. I know I should have check the forums to fix the problem but I had a piece of software on a disk that let's me boot into windows so I ignored it. Eventually I got tired of doing it so, Instead of giving Ubuntu the job to fix grub, I got lazy and let the Software I used to boot to windows to fix the MBR. Huge mistake](*,). The screen was blank and booting to intel's boot loader and that Only happens when it can't find the my hard drives. Worse, when I boot into a live CD and type in Sudo Grub, I get an error that it didn't exist:sad:  so I went into other grub install guides but it made things worse after realizing that I forgot where I installed Grub or how I install Grub in the MBR in the first place! I'm Asking everyone PLEASE HELP!!!![-o<[-o<

---

### Post by Rubi1200 on 2010-07-15
Assuming you can boot the computer with the LiveCD, choose to try not install.

Then, once you are at the Desktop and can connect to the Internet, click on the link at the bottom of my post.

Follow the instructions carefully and post the results back here.

We will then have a better idea of your setup and be in a position to offer some possible solutions.

Good luck!

---

### Post by Michael577 on 2010-07-15
Got it here's the results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 227944332 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

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
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 227944332 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdg1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdg1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   482,399,819   482,399,757   7 HPFS/NTFS
/dev/sda2         482,400,254   488,396,799     5,996,546   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5    *    482,400,256   488,396,799     5,996,544  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   227,673,179   227,673,117   7 HPFS/NTFS
/dev/sdb2         227,674,112   488,396,799   260,722,688  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4200812B0081274F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0ef2edf1-8fd6-4c55-bb8f-96507ab51b3f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2A2495FC2495CB69                       ntfs       D                             
/dev/sdb2        5580a04c-6acc-46c7-a23c-2a56afce83e6   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        649D-2020                              vfat                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/649D-2020         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 ro splash quiet vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 ro single splash quiet vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 ro splash quiet vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 ro single splash quiet vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 ro splash quiet vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 ro single splash quiet vga=773
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 5580a04c-6acc-46c7-a23c-2a56afce83e6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4200812b0081274f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=5580a04c-6acc-46c7-a23c-2a56afce83e6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27ff4913-cee0-407e-894d-1a7965a45bbc none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 243.4GB: boot/grub/core.img
 243.5GB: boot/grub/grub.cfg
 243.5GB: boot/initrd.img-2.6.32-21-generic
 247.6GB: boot/initrd.img-2.6.32-22-generic
 247.6GB: boot/initrd.img-2.6.32-23-generic
 243.5GB: boot/vmlinuz-2.6.32-21-generic
 245.5GB: boot/vmlinuz-2.6.32-22-generic
 245.5GB: boot/vmlinuz-2.6.32-23-generic
 247.6GB: initrd.img
 247.6GB: initrd.img.old
 245.5GB: vmlinuz
 245.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

hope it'll help

Also here's the text file.

---

### Post by andrewthomas on 2010-07-15
You have installed grub to quite a few places.  

I would change the order in BIOS to boot sdb first then use the instructions here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

to reinstall grub2 to the MBR of sdb.  

You may or may not have to fix the MBR of sda.

---

### Post by Michael577 on 2010-07-15
no such luck guys:frown:. I keep getting the message that it isn't working. Do you think just reinstalling ubuntu would do the trick? By the way I've been planning to wipe my hard drives for a while now so at this point it'll be the last resort.

---

### Post by andrewthomas on 2010-07-15
Exactly what error message did you get?
What commands did you use?
 
I should have said that out of the hard drives, you should have the drive that is sdb first.  You obviously need to have your CD/DVD drive first in order to boot from the live CD.

---

### Post by Michael577 on 2010-07-15
Well all of them said instillation was successful but each time I try to boot the hard drive I keep get getting this intel error saying it can't connect to the media or something like that. What's weird is that even though the computer won't boot to it, the CD software I mention earlier can boot to my windows partition. I did a quick pic of my screen with my dsi (Sorry about the quality but it was a fast thing)

---

### Post by Rallg on 2010-07-15
I can't solve your problem here, but I can give you good advice regarding how to prevent a future problem. This is because your Windows is XP (not Vista or 7).

If you can restore your computer to its original Windows boot environment, one way or another, then afterwards try using XP's own bootloader as the preface to Grub. This is well-document for Grub "one" and also works for Grub2 with Ubuntu 10.04.

When you install (in your case, re-install) Ubuntu, you go through several screens with questions. When it gets to the summary, just before it is going to start installing, you will see an "Advanced" button. Go there, and choose to install Grub in the same partition where you will install Ubuntu, NOT in the default choice, which is the hard drive root.

After installation completes, do not immediately reboot. Instead, "continue testing." Open the Terminal, and type this:

sudo dd if=/dev/sdXY of=bootubuntu.bin bs=512 count=1

Where X=the drive letter, Y is the partition number where Ubuntu is installed (perhaps it is sda6 or something similar).

The resulting file is placed in the home directory of your live CD, which means it will disappear! So, copy it elsewhere, if necessary to a USB.

Then, reboot, and you will not see Grub. When Windows launches, take the file you just created and place it in the top directory of the C drive. You can hide it and make it read-only, if you wish.

Then make your Windows hidden and system files all visible. Modity boot.ini so that it adds a line like this:

c:\bootubuntu.bin "Ubuntu on hard drive"

Again, this does not work for Vista or Windows 7, just XP.


Modify the above as necessary. You may need to temporary remove read-only from boot.ini.

Reboot. This time, you will see a boot menu. You are not yet in Grub. If you choose Ubuntu, then the XP bootloader will transfer control to Grub on your Ubuntu partition.

Advantage of doing it this way: You never change the MBR or the Windows boot loader. If you subsequently damage Ubuntu, it will not prevent Windows from booting. You can also remove the menu choice rom boot.ini.

If you are using an external hard drive, results may differ.

What if you forgot to create the bootubuntu.bin file before exiting the Ubuntu installer? Then find "dd for Windows" and use it. Works for me.

---

### Post by confused57 on 2010-07-15
See section 13 here to reinstall grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You have grub2 installed to the boot sector of your Windows partition, here's a fix:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by wilee-nilee on 2010-07-15
> **Rallg said:**
> I can't solve your problem here, but I can give you good advice regarding how to prevent a future problem. This is because your Windows is XP (not Vista or 7).

If you can restore your computer to its original Windows boot environment, one way or another, then afterwards try using XP's own bootloader as the preface to Grub. This is well-document for Grub "one" and also works for Grub2 with Ubuntu 10.04.

When you install (in your case, re-install) Ubuntu, you go through several screens with questions. When it gets to the summary, just before it is going to start installing, you will see an "Advanced" button. Go there, and choose to install Grub in the same partition where you will install Ubuntu, NOT in the default choice, which is the hard drive root.

After installation completes, do not immediately reboot. Instead, "continue testing." Open the Terminal, and type this:

sudo dd if=/dev/sdXY of=bootubuntu.bin bs=512 count=1

Where X=the drive letter, Y is the partition number where Ubuntu is installed (perhaps it is sda6 or something similar).

The resulting file is placed in the home directory of your live CD, which means it will disappear! So, copy it elsewhere, if necessary to a USB.

Then, reboot, and you will not see Grub. When Windows launches, take the file you just created and place it in the top directory of the C drive. You can hide it and make it read-only, if you wish.

Then make your Windows hidden and system files all visible. Modity boot.ini so that it adds a line like this:

c:\bootubuntu.bin "Ubuntu on hard drive"

Again, this does not work for Vista or Windows 7, just XP.


Modify the above as necessary. You may need to temporary remove read-only from boot.ini.

Reboot. This time, you will see a boot menu. You are not yet in Grub. If you choose Ubuntu, then the XP bootloader will transfer control to Grub on your Ubuntu partition.

Advantage of doing it this way: You never change the MBR or the Windows boot loader. If you subsequently damage Ubuntu, it will not prevent Windows from booting. You can also remove the menu choice rom boot.ini.

If you are using an external hard drive, results may differ.

What if you forgot to create the bootubuntu.bin file before exiting the Ubuntu installer? Then find "dd for Windows" and use it. Works for me.
[B]
Not a good answer[/B], lucid is on a separate HD sdb.

Thread starter clean this ntfs partition with this, and put sdb first to boot in bios.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: [B]Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 [/B]and
looks at sector 227944332 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM


You also look to have extra partitions on sda2=extended sda5=swap and sdb1=ntfs. You might want the sdb1 but you have the others to deal with,sda2, sda5.

---

### Post by Michael577 on 2010-07-15
>  				 				**Re: My Computer can't find ANY boot loader after a failed  attempt to fix the MBR** 			
 			 			 		   		 		 		I can't solve  your problem here, but I can give you good advice regarding how to  prevent a future problem. This is because your Windows is XP (not Vista  or 7).

If you can restore your computer to its original Windows boot  environment, one way or another, then afterwards try using XP's own  bootloader as the preface to Grub. This is well-document for Grub "one"  and also works for Grub2 with Ubuntu 10.04.

When you install (in your case, re-install) Ubuntu, you go through  several screens with questions. When it gets to the summary, just before  it is going to start installing, you will see an "Advanced" button. Go  there, and choose to install Grub in the same partition where you will  install Ubuntu, NOT in the default choice, which is the hard drive root.

After installation completes, do not immediately reboot. Instead,  "continue testing." Open the Terminal, and type this:

sudo dd if=/dev/sdXY of=bootubuntu.bin bs=512 count=1

Where X=the drive letter, Y is the partition number where Ubuntu is  installed (perhaps it is sda6 or something similar).

The resulting file is placed in the home directory of your live CD,  which means it will disappear! So, copy it elsewhere, if necessary to a  USB.

Then, reboot, and you will not see Grub. When Windows launches, take the  file you just created and place it in the top directory of the C drive.  You can hide it and make it read-only, if you wish.

Then make your Windows hidden and system files all visible. Modity  boot.ini so that it adds a line like this:

c:\bootubuntu.bin "Ubuntu on hard drive"

Again, this does not work for Vista or Windows 7, just XP.


Modify the above as necessary. You may need to temporary remove  read-only from boot.ini.

Reboot. This time, you will see a boot menu. You are not yet in Grub. If  you choose Ubuntu, then the XP bootloader will transfer control to Grub  on your Ubuntu partition.

Advantage of doing it this way: You never change the MBR or the Windows  boot loader. If you subsequently damage Ubuntu, it will not prevent  Windows from booting. You can also remove the menu choice rom boot.ini.

If you are using an external hard drive, results may differ.

What if you forgot to create the bootubuntu.bin file before exiting the  Ubuntu installer? Then find "dd for Windows" and use it. Works for me.


That gave me an Idea:KS. I have an image of my windows hard drive with the Grub boot loader (probably the old one as of 9.04 probably I don't know but it work before) so my solution is if I load the image on my windows drive (FYI I have one OS on one drive and Ubuntu on the other) then the MBR and grub with be back to normal. The only downside is I my need to reinstall Startcraft 2 etc. think it'll work.

---

### Post by wilee-nilee on 2010-07-15
> **Michael577 said:**
> That gave me an Idea:KS. I have an image of my windows hard drive with the Grub boot loader (probably the old one as of 9.04 probably I don't know but it work before) so my solution is if I load the image on my windows drive (FYI I have one OS on one drive and Ubuntu on the other) then the MBR and grub with be back to normal. The only downside is I my need to reinstall Startcraft 2 etc. think it'll work.

You don't have to reimage just follow the post above mine and mine with the testdisk clean of the ntfs containing grub, then use sdb to boot with since that is where the bootloadr is for lucid on that HD.

---

### Post by Michael577 on 2010-07-15
I just noticed it:-\" .I'm going to try it. I'll report back the result.

---

### Post by Michael577 on 2010-07-15
Hey guys I don't think it's not going to matter anymore. While I was putting the Hard drives back to it's regular jacks....I broke the lucid's Hard drive sata connector:sad:. taking the lucid AND ***_My entire backup with it_***#-o!!! So I'm going to see If I can get a new one and see if best buy can get the files transfered. By the way my computer can only take sata ports.

---

### Post by Rallg on 2010-07-15
It may be that my earlier suggestion does not work when Ubuntu is on an external hard drive (although it seems like it should work, if the correct drive paths are specified in boot.ini).

As for attempting to restore the MBR from an earlier disk image, which used a different installation: That MIGHT work if no partitions were created or moved. It certainly will NOT work if there were any partition changes. Comment from someone more knowledgeable?

---

### Post by Michael577 on 2010-07-15
Ok guys I'm back! I got a new 1 TB hard drive so now the only question now is will installing ubuntu fix the MBR on my new hard drive? BTW The hard drive is fresh because Best buy said that it'll be about $600+ to move the data.:shock:

---

### Post by Michael577 on 2010-07-20
Hey guys I installed ubuntu in my new hard drive and the computer is now working. Except that I now have the same setup I have in the first place (I still have to boot windows though that CD program..*sigh* oh well, at least grub loads now). So as far as I'm considered this Thread 	 is SOLVED! but expect a new thread by me.

---

