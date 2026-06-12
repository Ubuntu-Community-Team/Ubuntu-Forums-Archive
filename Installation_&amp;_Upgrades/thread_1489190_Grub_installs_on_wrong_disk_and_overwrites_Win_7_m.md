---
title: "Grub installs on wrong disk and overwrites Win 7 mbr (more than once)"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by linuxmart on 2010-05-20
Hi there,
  I recently bought a new Gateway desktop. I use mostly Ubuntu but like to boot into Windows once in a while. Have used Ubuntu as my main OS for about 3 to 4 years, dual booting.
  After the Ubuntu 10.04 release, I decided to throw in another hard drive into the new computer and make it dual boot.
  I made a series of mistakes and need some help.

Mistakes:
1. I did not create the Gateway Recovery Disk in Windows before installing Ubuntu.
2. Installed Ubuntu 10.04 without disconnecting the Windows 7 drive.
3. The Ubuntu install never prompted me asking where to install Grub (apparently there is an advanced menu somewhere in the install process that lets you select), and it was installed to the first drive on the PC by default, which happened to be the Win 7 drive.

This left the Windows 7 unbootable because it did not appear in the Grub menu.

I did some searching and managed to install Grub on the second drive (the one with the Ubuntu install) and also managed to add Windows 7 to the Grub menu so I could boot into Windows. This last procedure added the Windows 7 option to the Grub on both drives.

I then managed to fix the Windows 7 mbr using /fixmbr and /fixboot.

The problems I still have are as following.

I can't create the Windows Gateway Recovery Disk in Windows. Every time I try, I get a message telling me "Hard drive configuration is not set to the factory default. Restore aborted.". I already disconnected the Ubuntu drive but get the same results. I know this one is not a Linux issue, but maybe someone had a similar issue and might be able to help.

The next problem I have is that it looks like after the las Kernel update in Ubuntu, Grub overwrote the Windows 7 mbr again. Is there a setting file somewhere that now tells Ubuntu that Grub is installed in two places and that whenever there is an update it updates both? Can I change this? I really would like to avoid re-installing Ubuntu to fix this.

Your help is greatly appreciated.

Thanks.

---

### Post by tgalati4 on 2010-05-20
Usually there is a hidden partition on the drive which allows the recovery data to be stored there.  Ubuntu/GRUB doesn't know about these partitions or you overwrote them sometime in the past.  You would have to do some research to find the parameters for the Gateway recovery partition.  It's typically a few GB and it's either at the very front of the drive or at the rear of the partitions.

So the error message is simply alerting you to this fact.

Moving your installed partitions around to make space for this partition is tricky.

---

### Post by confused57 on 2010-05-21
> The next problem I have is that it looks like after the las Kernel update in Ubuntu, Grub overwrote the Windows 7 mbr again. Is there a setting file somewhere that now tells Ubuntu that Grub is installed in two places and that whenever there is an update it updates both? Can I change this? I really would like to avoid re-installing Ubuntu to fix this.

I have the same problem, during the intial install of 10.04, grub was installed to /dev/sda's mbr, I later installed grub to /dev/sdb's mbr.  Now when update-grub is run, both sda & sdb mbr's are overwritten with the updated grub.cfg.  Haven't been able to find anything yet to set update-grub to just install to sdb.  I'll report back if I find a solution or hopefully someone will post it here.

Added:  I wasn't able to repeat the above by running "sudo update-grub" in Lucid,  sda mbr wasn't overwritten, just have to wait until the next kernel update to see if happens again.  Hopefully this helps the OP with this problem.

---

### Post by wilee-nilee on 2010-05-21
> **confused57 said:**
> I have the same problem, during the intial install of 10.04, grub was installed to /dev/sda's mbr, I later installed grub to /dev/sdb's mbr.  Now when update-grub is run, both sda & sdb mbr's are overwritten with the updated grub.cfg.  Haven't been able to find anything yet to set update-grub to just install to sdb.  I'll report back if I find a solution or hopefully someone will post it here.

If you want grub on sdb follow this grub2 wiki.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
I am going to assume that you know what your doing with the amount of beans you have if not ask questions. Also remember that you can just open gparted from the live cd to make sure you know the partition setup.

Thread starter post this boot script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
The easiest way to get the code tags is to highlight the post in the reply and click on # in the reply panel, I believe you have top have the flash on to see the # sign.

Now if any of you are trying to have separate bootloaders, it is much easier to just have one that chainloads.

Also the advanced button which makes sure grub is put on the correct hard drive in the MBR is on the last screen of the install, go slower next time and watch for it, it will default to sda if not told otherwise generally.

---

### Post by confused57 on 2010-05-21
Thanks, might be a good idea to run the bootinfo script, which may show something.  I initially allowed 10.04 to install grub2 to sda's mbr, then decided I'd rather have Hardy's legacy grub installed on sda(first boot drive)...did that, then installed Lucid's grub to sdb's mbr.  When the kernel was updated, Lucid's grub(boot.cfg?) was installed to both sda & sdb's mbr.  I was wondering if there was a configuration file or script that determined where update-grub installed grub2's PBL.  

I'm fairly fluent with legacy-grub & trying to learn a little bit about grub2.  I've picked up bits & pieces, so now it doesn't matter if grub2 is installed on the primary boot drive...just curious about why it installed to both sda & sdb's mbr.

---

### Post by wilee-nilee on 2010-05-21
> **confused57 said:**
> Thanks, might be a good idea to run the bootinfo script, which may show something.  I initially allowed 10.04 to install grub2 to sda's mbr, then decided I'd rather have Hardy's legacy grub installed on sda(first boot drive)...did that, then installed Lucid's grub to sdb's mbr.  When the kernel was updated, Lucid's grub(boot.cfg?) was installed to both sda & sdb's mbr.  I was wondering if there was a configuration file or script that determined where update-grub installed grub2's PBL.  

I'm fairly fluent with legacy-grub & trying to learn a little bit about grub2.  I've picked up bits & pieces, so now it doesn't matter if grub2 is installed on the primary boot drive...just curious about why it installed to both sda & sdb's mbr.

The script will be a good start, and start your own thread and send me a PM when you do. ;) Having individual threads in these sort of manners works best in that not everyones problems or fixes are the same usually.

Also I never got around to learning legacy grub stuff but grub2 is really easy in that it can be loaded with 2 commands from a live cd and then just running sudo update-grub in the reboot OS, will bring it altogether if everything is in place.

---

### Post by linuxmart on 2010-05-21
> **tgalati4 said:**
> Usually there is a hidden partition on the drive which allows the recovery data to be stored there.  Ubuntu/GRUB doesn't know about these partitions or you overwrote them sometime in the past.  You would have to do some research to find the parameters for the Gateway recovery partition.  It's typically a few GB and it's either at the very front of the drive or at the rear of the partitions.

So the error message is simply alerting you to this fact.

Moving your installed partitions around to make space for this partition is tricky.

Thanks for you response!
I hadn't done anything to the Windows 7 drive, except for accidentally installing Grub on it. Could Grub have overwritten partition information, so the partition is still there, but not visible?
I fixed the mbr on it but when I look at the drive with Gparted, it doesn't show a hidden partition. I attached a screenshot.

Thanks!

---

### Post by linuxmart on 2010-05-21
> **wilee-nilee said:**
> If you want grub on sdb follow this grub2 wiki.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
I am going to assume that you know what your doing with the amount of beans you have if not ask questions. Also remember that you can just open gparted from the live cd to make sure you know the partition setup.

Thread starter post this boot script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
The easiest way to get the code tags is to highlight the post in the reply and click on # in the reply panel, I believe you have top have the flash on to see the # sign.

Now if any of you are trying to have separate bootloaders, it is much easier to just have one that chainloads.

Also the advanced button which makes sure grub is put on the correct hard drive in the MBR is on the last screen of the install, go slower next time and watch for it, it will default to sda if not told otherwise generally.

Thanks for your response!
I actually don't want Grub on the Windows 7 drive. I can boot Windows 7 from Grub on my second drive. But when it seams like when there was a Kernal update, it knew that Grub had been on the Windows 7 drive a one point and it rewrote the Windows mbr again. So it updates Grub on both drives.
If I look at /var/cache/debconf/config.dat, there is grub info in it for both drives. Remember kind of got rid of Grub on the Windows drive. Now I am afraid to modify this setting file. Do you think if I reinstall Grub as per the Wiki it will not touch my Windows drive again?

I also ran the script you suggested. This is the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046   122,879,999   122,877,954   5 Extended
/dev/sdb5               2,048    99,442,687    99,440,640  83 Linux
/dev/sdb6          99,444,736   122,879,999    23,435,264  82 Linux swap / Solaris
/dev/sdb2         122,881,185   398,283,479   275,402,295   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AC24BE3D24BE0A7A                       ntfs       Gateway                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        7337960C1465C228                       ntfs       files                         
/dev/sdb5        5b68ad7f-54ed-45e3-a752-f9a619ce8309   ext4                                     
/dev/sdb6        80a6c1f1-9ba1-46c7-9ea1-42923161b39c   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /media/files             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/AppDrv1           udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=5b68ad7f-54ed-45e3-a752-f9a619ce8309 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=5b68ad7f-54ed-45e3-a752-f9a619ce8309 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5b68ad7f-54ed-45e3-a752-f9a619ce8309 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5b68ad7f-54ed-45e3-a752-f9a619ce8309 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 5b68ad7f-54ed-45e3-a752-f9a619ce8309
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ac24be3d24be0a7a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb5 :
UUID=5b68ad7f-54ed-45e3-a752-f9a619ce8309	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdb2 :
UUID=7337960C1465C228	/media/files	ntfs-3g	defaults,locale=en_CA.UTF-8	0	0
#Entry for /dev/sdb6 :
UUID=80a6c1f1-9ba1-46c7-9ea1-42923161b39c	none	swap	sw	0	0



=================== sdb5: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/core.img
  47.5GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.9GB: boot/initrd.img-2.6.32-22-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
  14.7GB: boot/vmlinuz-2.6.32-22-generic
  38.9GB: initrd.img
  38.8GB: initrd.img.old
  14.7GB: vmlinuz
  38.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

### Post by darkod on 2010-05-21
> **confused57 said:**
> I have the same problem, during the intial install of 10.04, grub was installed to /dev/sda's mbr, I later installed grub to /dev/sdb's mbr.  Now when update-grub is run, both sda & sdb mbr's are overwritten with the updated grub.cfg.  Haven't been able to find anything yet to set update-grub to just install to sdb.  I'll report back if I find a solution or hopefully someone will post it here.

Added:  I wasn't able to repeat the above by running "sudo update-grub" in Lucid,  sda mbr wasn't overwritten, just have to wait until the next kernel update to see if happens again.  Hopefully this helps the OP with this problem.

sudo dpkg-reconfigure grub-pc

will allow you to select/deselect disks that should be updated by grub2

---

### Post by linuxmart on 2010-05-21
> **darkod said:**
> sudo dpkg-reconfigure grub-pc

will allow you to select/deselect disks that should be updated by grub2

Thank you so much!
I ran the command and hit enter on all the options until I got to the part where I select the drive. Sure enough, the Windows drive was selected, so I unselected it and selected the Ubuntu drive.

Thanks again.

---

### Post by confused57 on 2010-05-21
> **linuxmart said:**
> Thank you so much!
I ran the command and hit enter on all the options until I got to the part where I select the drive. Sure enough, the Windows drive was selected, so I unselected it and selected the Ubuntu drive.

Thanks again.
+1

Thanks Darkod, I'll have to add the command to my Ubuntu/Linux cheatsheet notes.

---

### Post by darkod on 2010-05-21
No problem, you are welcome. I knew there was one, but couldn't remember it myself right now. Had to google a bit to find it. :)

---

### Post by confused57 on 2010-05-21
I can't help you with restoring your recovery partition, but you might want to check out the clonezilla live cd for making an image of your current Windows 7, which you could save to your Ubuntu hard drive, and restore if you ever have to:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

The image would probably be no more than approximately 10 GB.

---

### Post by wilee-nilee on 2010-05-21
Good job getting this fixed. I would contact the manufacturer and get the OEM recovery disc set, as you never know when you may have to reinstall and have it be a legitimate install that has a auto OEM key verification. I think a back up with clonezilla is a good idea as well, but while your still in the warranty a OEM install is what you want in case you need any repairs done.

I had to buy the OEM XP install for my netbook just to get acer to considor a repair legit, would not fix my computer with W7 installed even though I bought it from MS, it was considered to be a 3rd party install by acer. They didn't like the Ubuntu install either.

The OEM disc set will also allow you to remove the recovery partition which probably will not work now without knowing how to trick it to run.

Personally I don't like a partition being filled with a recovery when I can have a DVD of the install.

---

### Post by linuxmart on 2010-05-21
Thanks for all your help and advice!

I have just ordered the Recovery Media from Gateway (Acer). $22 with taxes.
For now, Windows 7 is working OK, but once I get the DVDs, I will do a factory install.
I mostly use Ubuntu anyways. I might do some Crystal Reports developing for which I would need Windows.

Thanks again!

---

### Post by wilee-nilee on 2010-05-22
> **linuxmart said:**
> Thanks for all your help and advice!

I have just ordered the Recovery Media from Gateway (Acer). $22 with taxes.
For now, Windows 7 is working OK, but once I get the DVDs, I will do a factory install.
I mostly use Ubuntu anyways. I might do some Crystal Reports developing for which I would need Windows.

Thanks again!

About the cheapest insurance you can get. ;)

---

### Post by teege1@live.com on 2010-05-22
How do I delete a post?

---

### Post by wilee-nilee on 2010-05-22
> **teege1@live.com said:**
> Perhaps I am just lucky, but I haven't had any issues with dual booting Ubuntu and Windows.  Using wubi, this procedure went very well.  I have since allowed KDE to automatically partition a portion of the HDD, and everything boots from its menu.  I essentially have 3 operating systems on one drive.  I don't quite understand why so many people are not using the windows installer for Ubuntu 10.04.  In all fairness, I am not using Windows7, but XP  SP3. I have installed a couple of Linux OSs, and each one has taken over the boot screen, but always presents the windows/ubuntu option.

When you say windows installer I assume you mean wubi. There are inherent problems with wubi, glad it's worked for you but it was designed as a quick way to try out Ubuntu then a dual boot is used to get the full use of the distro. 

I wont list the problems with wubi but it is as I said a tryout the distro without messing with the MBR method.

---

### Post by teege1@live.com on 2010-05-22
Perhaps I am just lucky, but I haven't had any issues with dual booting Ubuntu and Windows.  Using wubi, this procedure went very well.  I have since allowed KDE to automatically partition a portion of the HDD, and everything boots from its menu.  I essentially have 3 operating systems on one drive.  I don't quite understand why so many people are not using the windows installer for Ubuntu 10.04.  In all fairness, I am not using Windows7, but XP  SP3. I have installed a couple of Linux OSs, and each one has taken over the boot screen, but always presents the windows/ubuntu option. I am very much a novice at partitioning, etc. and have had a load of good luck when it comes to allowing the OS being installed to do it automatically.  I only have a 200GB hdd, but even with Ubuntu, Windows XP, and PCLinux2010 KDE, installed on it, I still have around 140GB free.

---

### Post by teege1@live.com on 2010-05-22
Thanks.  Yes, it worked like a charm.  I can't remember the last time I booted xp, as I am having a ball with Ubuntu.  Love it.  Can't say the same for the new PC Linux 2010 releases however.  I am partial to the Gnome desktop, did not care for open box, and currently configuring KDE.  Incidentally, does this mean Ubuntu is going to disappear from my computer?  Like I said, I guess I just got lucky. It may be interesting to note that Ubuntu's web site provided this product without any warning of it being a potential problem.  I am just happy it worked, and wish all the other OS's I burned would have been as painless.

---

