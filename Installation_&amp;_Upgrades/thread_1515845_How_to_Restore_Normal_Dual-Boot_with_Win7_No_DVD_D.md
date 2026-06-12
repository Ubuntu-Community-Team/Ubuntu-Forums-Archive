---
title: "How to Restore Normal Dual-Boot with Win7: No DVD Drive"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by YouStoleMyLaptop on 2010-06-22
[SIZE=4][COLOR=Black][SIZE=2](this part was deleted for your confusion)

 [/SIZE][/COLOR][/SIZE]Edit: I  have a Sony Vaio FJ170 laptop with Phoenix BIOS version R0060X6 &  a  broken DVD Drive. The BIOS doesn't support booting from USB (it does   have 'External Drive Boot' option, but my USB stick doesn't get listed   under boot devices in BIOS when connected to the laptop).
   

A few days ago I upgraded to Windows7, then  installed Lucid through  WUBI. With the help of another thread of mine ([here)]("http://ubuntuforums.org/showthread.php?t=1498681"),   I changed the default boot option & timeout of Windows to zero to   directly boot into Ubuntu. So far it was good. But recently I tried to   get back to Windows for some reason but could not succeed as the F8 key   no longer brings up the Window's Advance Boot Menu. ([here's]("http://ubuntuforums.org/showpost.php?p=9462351&postcount=39") a suggested solution to my problem, but I   don't have a working DVD Drive to implement it!)
  

Is there another way to restore the dual boot menu  timeout to get back  to the Windows installation. Or even better, is  there some way to make a  fresh install of Windows & Ubuntu  side-by-side without DVD drive.
  Please mind that I am only 14 and absolutely new to Linux. The   network booting methods given on the Internet were too complex for me to   understand. I like Ubuntu but also need Windows for programming C++   & Photoshop CS4.

---

### Post by wilee-nilee on 2010-06-23
> **YouStoleMyLaptop said:**
> Recently I have installed the OS ubuntu through wubi. & it has dual booted my laptop with windiows 7. But I have noticed that after you install through wubi, microsoft disable the f8 key so you cant pop up the grub menu. So recently I have thought of becoming a programmer. & I need the C++ Program & i see that ubuntu doesnt support that, only in text editor forms,. So I am trying to reinstall windows 7 so i could just have the whole disk 1 OS, because i cant access the windows 7 now. So, How would i install windows 7 to my ubuntu system when my CD drive is broken? I have a .zip file of windows 7. So I can install from that. but someone has told me that I can't install from the .exe file in the .zip file so what do i do now? i have a Sony Vaio VGN-FJ170, thank you in advance

First change your font to the correct size and color black, then you might get some help. If this is just a W7 install go to the W7 forums and ask for their help.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

If you just want windows 7 fixed so it works post the bootscript in my signature in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

**Please change the font to look as the quote does in my response.**

---

### Post by inka1 on 2010-06-23
Hi.
I think your post is very unclear...
Try to give explain it a little more clearly what exactly do you need.

You could probably try to install Windows 7 from an usb, search for this topic on the net.
Even a working CD-rom can`t help you, because win7 comes on a DVD.

And about the C++, there is no "C++ program", maybe you mean MS Visual Studio?
On Linux you could try MonoDevelop.

Greetings.

---

### Post by YouStoleMyLaptop on 2010-06-23
I have the downloaded version iso file. & my laptop doesnt have a usb boot manager. It doesnt show the USB in the bios 

& Microsoft Visual C++
is the program i was talkign about.

& to willie nillie, it told me to post this

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,401,994     8,401,932   7 HPFS/NTFS
/dev/sda2    *      8,401,995   195,366,464   186,964,470   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8213 MB, 8213305856 bytes
255 heads, 63 sectors/track, 998 cylinders, total 16041613 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             58    16,016,804    16,016,747   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       637709fe-da43-407d-a06e-39b910a0b2ff   ext4                                     
/dev/sda1        748E-79CE                              vfat       ProNess                       
/dev/sda2        6AD077D3D077A44B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4802-7173                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/4802-7173         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
set default="4"
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


  14.7GB: boot/grub/grub.cfg
  11.0GB: boot/initrd.img-2.6.32-21-generic
  11.2GB: boot/initrd.img-2.6.32-22-generic
  11.0GB: boot/vmlinuz-2.6.32-21-generic
  11.2GB: boot/vmlinuz-2.6.32-22-generic
  11.2GB: initrd.img
  11.0GB: initrd.img.old
  11.2GB: vmlinuz
  11.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by YouStoleMyLaptop on 2010-06-23
**[U][B]**
[/U][/B]
I  have a Sony Vaio FJ170 laptop with Phoenix BIOS version R0060X6 & a  broken DVD Drive. The BIOS doesn't support booting from USB (it does  have 'External Drive Boot' option, but my USB stick doesn't get listed  under boot devices in BIOS when connected to the laptop).
   

A few days ago I upgraded to Windows7, then  installed Lucid through WUBI. With the help of another thread of mine ([here)]("http://ubuntuforums.org/showthread.php?t=1498681"),  I changed the default boot option & timeout of Windows to zero to  directly boot into Ubuntu. So far it was good. But recently I tried to  get back to Windows for some reason but could not succeed as the F8 key  no longer brings up the Window's Advance Boot Menu. ([here's]("http://ubuntuforums.org/showpost.php?p=9462351&postcount=39") a suggested solution to my problem, but I  don't have a working DVD Drive to implement it!)
  

Is there another way to restore the dual boot menu  timeout to get back to the Windows installation. Or even better, is  there some way to make a fresh install of Windows & Ubuntu  side-by-side without DVD drive.
  Please mind that I am only 14 and absolutely new to Linux. The  network booting methods given on the Internet were too complex for me to  understand. I like Ubuntu but also need Windows for programming C++  & Photoshop CS4.

---

### Post by cariboo on 2010-06-23
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by wilee-nilee on 2010-06-23
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

Your missing the boot files generally in the recovery partition, they are in sda2 though. And it is a recovery that is no good anyway since you have upgraded.

Since this was a upgrade as I suspected the upgrade provider will give you a ISO link download it burn it to a dvd and get the external cd/dvd reader and install.

You can only run the .exe from a running MS OS.

---

### Post by wilee-nilee on 2010-06-23
If you get the ISO burned, and get a external cd/reader then delete the recovry and the other upgrade and install W7 again your activation key should work if your first upgrade was activated. If it wasn't you can activate with the auto-phone activation option if you get the second upgrade installed and try to activate and get the prompt for the phone activation.

Otherwise MS will be glad to get you activated they want you to use their software.

When this is all done I would avoid the wubi and use a virtual like the sun vbox or just do a real dual boot.

**Also if the F8 option gets you to the windows boot options boot in and change the timeout that is what is causing you the problems never set that to 0**

---

### Post by YouStoleMyLaptop on 2010-06-23
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.


I am sorry, my friend has told me to because I will get more responses.

---

### Post by YouStoleMyLaptop on 2010-06-23
> **wilee-nilee said:**
> If you get the ISO burned, and get a external cd/reader then delete the recovry and the other upgrade and install W7 again your activation key should work if your first upgrade was activated. If it wasn't you can activate with the auto-phone activation option if you get the second upgrade installed and try to activate and get the prompt for the phone activation.

Otherwise MS will be glad to get you activated they want you to use their software.

When this is all done I would avoid the wubi and use a virtual like the sun vbox or just do a real dual boot.

**Also if the F8 option gets you to the windows boot options boot in and change the timeout that is what is causing you the problems never set that to 0**

The F8 key does work, but when i press on 
"Window's 7 Loader"
It just goes back to the same screen with 
"Linux Generic"

---

### Post by wilee-nilee on 2010-06-23
If this can be fixed the best people with the knowledge of this are on line now. If you get no response, burn the ISO to a DVD and get a external CD/DVD reader and reinstall. This is a fresh install anyway I doubt you have anything needed to save, am I right. If you need to save stuff boot a live Ubuntu CD and open the windows partition and extract it to a external device.

I gave pretty good instructions on how to reinstall and have the key verify, and if not, how to get it done.

---

### Post by varunendra on 2010-06-24
The OP's BIOS has the option to boot from external drive but his USB stick didn't get listed in the boot devices when connected. What may be wrong with that?

And if he gets himself an external optical drive with (obviously) USB interface, is there any chance that it wouldn't get listed there too?

An external drive would definitely much more reliable & possibly cheaper than an internal one. That's why I want to confirm.

---

### Post by wilee-nilee on 2010-06-24
> **varunendra said:**
> The OP's BIOS has the option to boot from external drive but his USB stick didn't get listed in the boot devices when connected. What may be wrong with that?

And if he gets himself an external optical drive with (obviously) USB interface, is there any chance that it wouldn't get listed there too?

An external drive would definitely much more reliable & possibly cheaper than an internal one. That's why I want to confirm.

A usb thumb or hard drive are different then a CD/DVD reader. I suspect that when they checked to see if it would boot from one none were plugged in the f prompt will only list what is in the bios stock and plugged in devices.

Here is link to that computer it will boot from a thumb or HD.
[http://esupport.sony.com/US/perl/swu-list.pl?mdl=VGN-FJ170](http://esupport.sony.com/US/perl/swu-list.pl?mdl=VGN-FJ170)

What the OP said was that usb didn't show in the bios they didn't confirm having it plugged in, it has to be plugged in and at the least a key prompt like f12 will bring up the boot from list. Mine is f12.

---

### Post by inka1 on 2010-06-24
> **YouStoleMyLaptop said:**
> 
Is there another way to restore the dual boot menu  timeout to get back to the Windows installation. Or even better, is  there some way to make a fresh install of Windows & Ubuntu  side-by-side without DVD drive.
  

To change the timeout for grub, try installing "startupmanager" from syanaptic, this provides a simple interface for some grub options, including the timeout or default boot option.


If you really need Visual Studio, you could use VirtualBox with Windows+VStudio I use this solution for WinXP+MSOffice.

---

### Post by wilee-nilee on 2010-06-24
> **inka1 said:**
> To change the timeout for grub, try installing "startupmanager" from syanaptic, this provides a simple interface for some grub options, including the timeout or default boot option.


If you really need Visual Studio, you could use VirtualBox with Windows+VStudio I use this solution for WinXP+MSOffice.
They set the time out in widows I think if you look at the script you will see in the grug.cfg ```
set timeout=10
```

Since it is a wubi install it should be defaulting to the windows bootloader anyway, not grub.

---

### Post by varunendra on 2010-06-24
> **wilee-nilee said:**
> What the OP said was that usb didn't show in the bios they didn't confirm having it plugged in, it has to be plugged in and at the least a key prompt like f12 will bring up the boot from list. Mine is f12.

I was chatting with him the moment he was doing it. He confirmed me that it was plugged in & was formatted as a USB startup disk in Ubuntu. That's why I suspect his laptop's capability to boot off USB.

I visited the link you provided, but couldn't get any hint about booting options there.


@inka1,
He already has changed the timeout in Grub. It is the Windows boot-menu he's having problem with. see [here]("http://ubuntuforums.org/showpost.php?p=9462351&postcount=39").
Network install was what I was thinking too, but my knowledge about it is same as you :)

---

### Post by inka1 on 2010-06-24
> **varunendra said:**
> 
@inka1,
He already has changed the timeout in Grub. It is the Windows boot-menu he's having problem with. see [here]("http://ubuntuforums.org/showpost.php?p=9462351&postcount=39").
Network install was what I was thinking too, but my knowledge about it is same as you :)

I removed that netword install line, because it seems you need floopy drive for it, and the laptop doesn`t have one.

About the boot time, maybe wubi has some config files that could be edited manually from linux? Just a wild guess...

---

### Post by wilee-nilee on 2010-06-24
> **varunendra said:**
> I was chatting with him the moment he was doing it. He confirmed me that it was plugged in & was formatted as a USB startup disk in Ubuntu. That's why I suspect his laptop's capability to boot off USB.

I visited the link you provided, but couldn't get any hint about booting options there.


@inka1,
He already has changed the timeout in Grub. It is the Windows boot-menu he's having problem with. see [here]("http://ubuntuforums.org/showpost.php?p=9462351&postcount=39").
Network install was what I was thinking too, but my knowledge about it is same as you :)

Any computer that new will boot from a usb.
I will tell you what I think here personally first the OP has a recovery that is from vista, a experienced user would have removed this it is not needed. Also If I remember this is a fresh install so trying to fix a setup with a not needed recovery on board and I suspect a fairly inexperienced user is not the way to go.

I can appreciate you all wanting to find some workaround to get this working but the boot is probably in the recovery and so a Fresh install that includes the removal of the recovery and set up correctly will be the best solution in the end. It is not about whether we can fix something in this situation, alone; but making sure the OP has a correctly set up OS. It is a fresh install there is nothing to be saved.

---

### Post by varunendra on 2010-06-24
> **wilee-nilee said:**
> Any computer that new will boot from a usb.
It was, & still is my belief too, > **varunendra said:**
> No problem if you have a usb stick (at least  1GB, or a usb hard disk), and your laptop can boot from usb (which I'm  damn sure it can - given the specs you posted) just a bit shaken.

> **wilee-nilee said:**
> so a Fresh install that includes the removal of the recovery and set up correctly will be the best solution in the end.
I totally agree, & that's what we want too. We just wanted to make sure that getting an external **USB DVD writer** would be a sure-shot solution for all the hassle.

---

### Post by wilee-nilee on 2010-06-24
> **varunendra said:**
> It was, & still is my belief too,  just a bit shaken.


I totally agree, & that's what we want too. We just wanted to make sure that getting an external **USB DVD writer** would be a sure-shot solution for all the hassle.

I think I understand now, if the OP has a ISO of W7 it unpacks to about 2.7 gigs so a thumb large enough for that is needed and should be loaded with the MS tool.
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)

So I suspect that in the bios of the computer, is a on off switch for the key prompt to choose the boot from menu, there was one in the bios of my aceraspire one d250

All of this could be found out with just a call to the manufacturers help line, I'm sure have one. The thumbloader has to be run from a MS environment and can be loaded with a DVD or ISO. 

I think your smart though to get the thumb boot worked out first.

---

### Post by YouStoleMyLaptop on 2010-06-24
Here's the bios pictures.

---

### Post by wilee-nilee on 2010-06-24
So the USB option for boot can only be accessed probably with having it plugged in and using the key prompt to boot from, that is outside of the bios. Call the manufacturer to find out what the key prompt is and whether you can boot from a External HD or thumb. It has a optical drive setting in bios so it will boot from a CD/DVD reader.

---

### Post by pac4639 on 2011-05-05
For over the past year I have enjoyed using Ubuntu 10.10 along side a windows 7 os on the same hdd.  I just upgraded to Unbuntu 11.04 and now do not have the "option" to select win7.  The computer automatically boots to U 11.04.  

What can I do to restore the ability to dual boot.  I seem to have "lost" any ability to choose which os I want to use.

I appreciate your help and guidance in this situation.  

Thanks,

John
[email]pac4639@gmail.com[/email]

---

### Post by oldfred on 2011-05-06
@pac4639

This is an old thread and most boot issues are unique. If thread did not have answers to your problem, you should start a new thread. Did you try.
```
sudo update-grub
```If that does not work start a new thread and put the boot info script in it. Links to boot script are in wilee-nilee's signature.

Remove your email. This site is scanned and your email will get filled with junk.

---

