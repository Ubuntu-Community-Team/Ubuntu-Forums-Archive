---
title: "Dual Boot XP and Kubuntu 10.10 GRUB Question"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by HonkingAntelope on 2010-11-20
Hi,

My system has 2 hard drives, a 400gb master and a 250gb slave.

sda (my main 400gb Windows drive) has XP on it.

The slave (sdb) has 3 partitions:

sdb1 is for my downloads (NTFS ~180gb)
sdb2 has Kubuntu 8.10 installed (ext3, 60gb) 
and sdb3 is the swap (3gb).

I want to do a destructive upgrade to Kubuntu 10.10 - I have the CD already and burnt.

I know I have to select the partitions manually due to the complicated setup, I know I need to format the sdb2 partition to ext4, mount point /, and the swap can stay the same.

On which hard drive should I install the bootloader? I can't remember where it is installed now, all I know is I had a lot of problems with the install ... :|

Thanks
Ryan

---

### Post by sikander3786 on 2010-11-20
If you get Grub menu at the start and use it for booting both Ubuntu and Windows, you can simply find out which HDD it is by going to the Bios menu and finding out the first boot device.

Or you can run bootinfoscript as per instructions here from your existing Kubuntu install and it will tell us some more useful information also.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please post the output and wrap it with proper code tags # from the post menu.

However, in my opinion, you should install Grub to the same HDD as the previous one or you might need to fixmbr for Windows XP.

---

### Post by HonkingAntelope on 2010-11-20
> **sikander3786 said:**
> If you get Grub menu at the start and use it for booting both Ubuntu and Windows, you can simply find out which HDD it is by going to the Bios menu and finding out the first boot device.

Or you can run bootinfoscript as per instructions here from your existing Kubuntu install and it will tell us some more useful information also.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please post the output and wrap it with proper code tags # from the post menu.

However, in my opinion, you should install Grub to the same HDD as the previous one or you might need to fixmbr for Windows XP.

Hi, thanks for the swift reply!

Here are the contents of RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xace22e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  1b Hidden W95 FAT32
/dev/sda2    *     16,370,235   781,401,599   765,031,365   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00011306

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   362,570,984   362,570,922   7 HPFS/NTFS
/dev/sdb2         362,570,985   488,392,064   125,821,080   5 Extended
/dev/sdb5         362,571,048   482,383,754   119,812,707  83 Linux
/dev/sdb6         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2C88-4712                              vfat       BACKUP                        
/dev/sda2        283CF0BD3CF086DA                       ntfs       HDD                           
/dev/sdb1        5628F6EA28F6C84F                       ntfs       Downloads                     
/dev/sdb5        02f48b0d-29f2-4f20-9aca-6b5f0d2151a6   ext3                                     
/dev/sdb6        e83c3dcd-d092-41a4-8a01-28f656694fdb   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..."

================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=02f48b0d-29f2-4f20-9aca-6b5f0d2151a6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=02f48b0d-29f2-4f20-9aca-6b5f0d2151a6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		02f48b0d-29f2-4f20-9aca-6b5f0d2151a6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=02f48b0d-29f2-4f20-9aca-6b5f0d2151a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		02f48b0d-29f2-4f20-9aca-6b5f0d2151a6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=02f48b0d-29f2-4f20-9aca-6b5f0d2151a6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		02f48b0d-29f2-4f20-9aca-6b5f0d2151a6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=02f48b0d-29f2-4f20-9aca-6b5f0d2151a6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=e83c3dcd-d092-41a4-8a01-28f656694fdb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 206.1GB: boot/grub/menu.lst
 206.2GB: boot/grub/stage2
 206.2GB: boot/initrd.img-2.6.27-7-generic
 206.2GB: boot/vmlinuz-2.6.27-7-generic
 206.2GB: initrd.img
 206.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by sikander3786 on 2010-11-20
Actually Grub is installed in the MBR of both HDDs.

The one that is working and letting you dual boot is in the MBR of sda i.e, the one with Windows install.

I have not much experience with Grub Legacy so I suggest you wait for some other opinions.

In my opinion, it would be better to install Grub to the second HDD i.e, sdb which will hold Ubuntu and let the Windows bootloader lie in MBR of sda.

I am not sure if you'll need to fixmbr for sda and how to get rid of Grub legacy on that drive as it used to boot in stages.

You can simply install Grub to the MBR of sda as well and I'm sure you won't get any problem that way but it is not the recommended method though.

Hang in there and some more experience members might be coming soon.

---

### Post by HonkingAntelope on 2010-11-20
Ok, I think I'll hang around, hopefully someone will confirm what I have to do to keep Ubuntu and Windows happy.

Thanks for your help.

---

### Post by wilee-nilee on 2010-11-20
I will assume that destructive upgrade means fresh install here. Put grub in the same HD as Ubuntu and you can put the MS bootloader back into sda; here it is just fixmbr from a XP install cd at the repair console, pointed at the sda HD.

Since grub will be the bootloader put that HD as the first to be read in the bios.

You probably had problems before as you have grub-legacy as suggested by the other post, you had to have added a stanza's to the grub menu list to have sda as the booting HD. The script can at times be incorrect in showing the actual order of the HD in the bios though.

I would say here that waiting for more consensus is warranted here as well. 10.10 is grub2 and even if you get them mixed it can be fixed probably but your smart to ask questions.;)

---

### Post by HonkingAntelope on 2010-11-20
Hi,

Thanks for all the replies so far! 

I have a possible solution - thought I'd run it past the experts first.

Would the following work:

1) Boot into XP
2) Restore the default Windows bootloader (therefore removing GRUB)
3) Boot the Kubuntu CD, install to sdb2 and 3 like 8.10 is now, then put the bootloader on sda?

Would this work?

Thanks
Ryan

---

### Post by sikander3786 on 2010-11-20
> Would the following work:

1) Boot into XP
2) Restore the default Windows bootloader (therefore removing GRUB)
3) Boot the Kubuntu CD, install to sdb2 and 3 like 8.10 is now, then put the bootloader on sda?

[s]To me, it sounds the best way around. And it should definitely work.[/s]

Edit: I was lazy to notice that you said bootloader on sda and I read it sdb. However wilee-nilee kept a good eye and advised accordingly.

---

### Post by HonkingAntelope on 2010-11-20
> **sikander3786 said:**
> To me, it sounds the best way around. And it should definitely work.

Right, thanks.

I'm off to try it, if I have problems, I'll post from my netbook running Kubuntu 10.10. :)

Thanks
Ryan

---

### Post by oldfred on 2010-11-20
You do not have to reinstall the windows boot loader unless you want to be sure to be able to boot windows.

Which drive to install grub to may depend on your hardware. Older systems with just IDE may only be able to boot from primary master. Newer systems that also have SATA usually let you boot any drive, and newest systems let you boot just about anything. Check your BIOS and see if it lets you choose which drive to boot. Sometimes it is part of the selection of boot device CD, Floppy, HD where HD then also gives choices and others have a totally separate BIOS entry to choose which drive to boot when you have chosen HD in the other selection.

As long as you can boot the liveCD you can reinstall to the
 MBR a grub boot loader or a windows style boot loader (Lilo) that will boot windows.

Note that your main install is in sdb5 and swap is sdb6. The sdb2 is the extended partition that just hold the logicals sdb5 & 6. And you are booting from sda as that has the grub that points to sdb5.

---

### Post by sikander3786 on 2010-11-20
> **HonkingAntelope said:**
> Right, thanks.

I'm off to try it, if I have problems, I'll post from my netbook running Kubuntu 10.10. :)

Thanks
Ryan
Even if you don't get any problems (and I hope so), it'd be better to post the output of bootinfoscript once again after everything is setup. Say for posterity purposes only :P

Good Luck.

---

### Post by HonkingAntelope on 2010-11-20
Ok, I'll do that to be on the safe side.

Waiting for Windows to finish booting ... :|

Thanks
Ryan

---

### Post by wilee-nilee on 2010-11-20
> **HonkingAntelope said:**
> Hi,

Thanks for all the replies so far! 

I have a possible solution - thought I'd run it past the experts first.

Would the following work:

1) Boot into XP
2) Restore the default Windows bootloader (therefore removing GRUB)
3) Boot the Kubuntu CD, install to sdb2 and 3 like 8.10 is now, then put the bootloader on sda?

Would this work?

Thanks
Ryan

Just a observation here if you put the MS bootloader back in sda it will be overwritten by grub being put there, if I understand you correctly. Did you mean grub to sdb?

We see a lot of people who have problems with grub not being in the actual HD MBR of where the Linux OS is installed, and not being the first in line in the bios. But this is a forum where people come for help so this is not necessarily a empirical look at this sort of setup.

---

### Post by HonkingAntelope on 2010-11-20
> **wilee-nilee said:**
> Just a observation here if you put the MS bootloader back in sda it will be overwritten by grub being put there, if I understand you correctly. Did you mean grub to sdb?

We see a lot of people who have problems with grub not being in the actual HD MBR of where the Linux OS is installed, and not being the first in line in the bios. But this is a forum where people come for help so this is not necessarily a empirical look at this sort of setup.

Hi,

Thanks for the reply.

I know GRUB will overwrite the MS MBR, I know the MS MBR will be replaced with GRUB after I install Kubuntu.

Or will GRUB overwrite the MS MBR upon reboot to install Kubuntu?

I'm a bit confused so will hang fire before someone responds.

Thanks
Ryan

---

### Post by wilee-nilee on 2010-11-20
> **HonkingAntelope said:**
> Hi,

Thanks for the reply.

I know GRUB will overwrite the MS MBR, I know the MS MBR will be replaced with GRUB after I install Kubuntu.

Or will GRUB overwrite the MS MBR upon reboot to install Kubuntu?

I'm a bit confused so will hang fire before someone responds.

Thanks
Ryan

Grub will overwrite the sda mbr when you install Kubuntu if you point grub at that sda mbr. I hope this works, but personally I wouldn't do it this way. If I had two HD and I had MS on one and Linux on the other I would have the corresponding OS bootloaders in the MBR of each HD. I would rely on grub as I am a open source user and know it works quite well. I would just have the HD with Linux in it as the first read.

The cool thing about having the MS bootloader with MS and grub with the Linux install is that, there is a post bios boot from menu, that can be triggered with a key prompt like the bios is mine is f12. So if at any time you need to boot straight into MS the bootloader is already in the mbr no need to reload with the fixmbr.

I am not familiar though with using a master and a slave nomenclature as far as what that actually means in a OS setup. And actually as a student of African American history I wish there were different words used.;) But that is my own opinion. I'm not critical of your use of them it is part of the computer language to identify setups, it is just a blind use by the OS industry to what those words mean to this population.

---

### Post by HonkingAntelope on 2010-11-20
> **wilee-nilee said:**
> Grub will overwrite the sda mbr when you install Kubuntu if you point grub at that sda mbr. I hope this works, but personally I wouldn't do it this way. If I had two HD and I had MS on one and Linux on the other I would have the corresponding OS bootloaders in the MBR of each HD. I would rely on grub as I am a open source user and know it works quite well. I would just have the HD with Linux in it as the first read.

The cool thing about having the MS bootloader with MS and grub with the Linux install is that, there is a post bios boot from menu, that can be triggered with a key prompt like the bios is mine is f12. So if at any time you need to boot straight into MS the bootloader is already in the mbr no need to reload with the fixmbr.

I am not familiar though with using a master and a slave nomenclature as far as what that actually means in a OS setup. And actually as a student of African American history I wish there were different words used.;) But that is my own opinion.

So what I should do is the following:

1) Restore the MS MBR using mbrfix in Windows
2) Install Kubuntu putting the bootloader on **/sdb** (my slave)

If I put the bootloader onto /sda, which I think is where I put it before, will I be able to access both Kubuntu and XP?

Thanks
Ryan

PS I apologise if I have caused any upset, I did not mean any offence with the terminology I have used. :|

---

### Post by wilee-nilee on 2010-11-20
> **HonkingAntelope said:**
> So what I should do is the following:

1) Restore the MS MBR using mbrfix in Windows
2) Install Kubuntu putting the bootloader on **/sdb** (my slave)

If I put the bootloader onto /sda, which I think is where I put it before, will I be able to access both Kubuntu and XP?

Thanks
Ryan

PS I apologise if I have caused any upset, I did not mean any offence with the terminology I have used. :|

No offenses don't worry about it; I'm a pasty white guy, just concerned.;)

I don't know how this sort of set up works M/S. I can't confirm that this will work, as I said we see problems with this in general in this sort of setup, but this is a forum where people come with problems. So it or what I think may not be true in the real world. I will say though that the people I have learned from on the forums will say the same thing basically about bootloaders and the MBR.

---

### Post by HonkingAntelope on 2010-11-20
> **wilee-nilee said:**
> No offenses don't worry about it; I'm a pasty white guy, just concerned.;)

I don't know how this sort of set up works M/S. I can't confirm that this will work, as I said we see problems with this in general in this sort of setup, but this is a forum where people come with problems. So it or what I think may not be true in the real world. I will say though that the people I have learned from on the forums will say the same thing basically about bootloaders and the MBR.

Ah right, thanks.

I had a problem like this when I installed Kubuntu back in 08, I had to boot into Windows to restore the MS MBR and then reinstall Kubuntu as I installed the MBR to sdb, and the MS MBR didn't pick up Kubuntu ... it's all coming back to me now.

I'll try it and post back my results. If it all goes wrong, I'll be back here quicker than a Veyron ... :P

Edit: MBR 'fixed', now rebooting to see if the MS MBR is working properly or not ... :|

Edit 2: GRUB is gone, booting into Windows to restart with the Kubuntu 10.10 CD in ...

Will post when Kubuntu 10.10 has installed ok.

Thanks
Ryan

---

### Post by wilee-nilee on 2010-11-20
n

---

### Post by wilee-nilee on 2010-11-20
> **oldfred said:**
> You do not have to reinstall the windows boot loader unless you want to be sure to be able to boot windows.

Which drive to install grub to may depend on your hardware. Older systems with just IDE may only be able to boot from primary master. Newer systems that also have SATA usually let you boot any drive, and newest systems let you boot just about anything. Check your BIOS and see if it lets you choose which drive to boot. Sometimes it is part of the selection of boot device CD, Floppy, HD where HD then also gives choices and others have a totally separate BIOS entry to choose which drive to boot when you have chosen HD in the other selection.

As long as you can boot the liveCD you can reinstall to the
 MBR a grub boot loader or a windows style boot loader (Lilo) that will boot windows.

Note that your main install is in sdb5 and swap is sdb6. The sdb2 is the extended partition that just hold the logicals sdb5 & 6. And you are booting from sda as that has the grub that points to sdb5.

Missed your post oldfred, thanks for the help here I'm just am not familiar with the M/S setups.

---

### Post by HonkingAntelope on 2010-11-20
Well.

It's installed fine.

Windows is fine as well.

I've logged in, it's got to a bit of the Settings icon ... and stopped.

There's been HDD activity ... now nothing.

Going to shut it down and try it again ...

EDIT: It works. Problem solved. 

Can this be changed to solved now?

Huge thanks to everyone for their time.

---

### Post by wilee-nilee on 2010-11-20
> **HonkingAntelope said:**
> Well.

It's installed fine.

Windows is fine as well.

I've logged in, it's got to a bit of the Settings icon ... and stopped.

There's been HDD activity ... now nothing.

Going to shut it down and try it again ...

EDIT: It works. Problem solved. 

Can this be changed to solved now?

Huge thanks to everyone for their time.

Glad it works click on thread tools for solve.

---

