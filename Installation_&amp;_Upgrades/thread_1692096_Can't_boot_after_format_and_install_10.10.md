---
title: "Can't boot after format and install 10.10"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by mdouble on 2011-02-20
Recently I removed Windows XP pro using Kill Disk and a 000 overwrite on the drive.  After that I used GParted format the drive and create a new ext 3 partition then I installed Ubuntu 10.10 from a live CD.

This system has only 10.10 installed.  There are no other OS's present.  

Installing of 10.10 went well and all the the files are now on the drive.  However, now the system will not reboot from the drive.  When attempting to boot I get a an error message which advise that the medium is not bootable.  I am then forced to use the live CD to boot from the CD.

I'm not sure if formatting a drive creates a new mbr or not.  If not then I would have to create one and I don't know how to do that.  I've read a number of forum posts on how to use GRUB to repair the mbr - however I haven't found any that specifically deal with replacing a missing mbr.     

I suspect that when I used Kill Disk it trashed the MBR.  I could really use some help figuring out the nature of the problem and how to fix it.  I'm fairly new to Ubuntu so please be as exact as possible if you reply.  

Thanks in advance

---

### Post by mikewhatever on 2011-02-20
Have you changed the default grub location during the installation by any chance? If so, you'd have to reinstall grub making sure it is in the MBR. If not, get the [bootinfo script]("http://sourceforge.net/projects/bootinfoscript/"), run it from the live cd and post the output.

---

### Post by deconstrained on 2011-02-20
Maybe the 'bootable' flag on your boot partition isn't set.

---

### Post by mdouble on 2011-02-20
> **deconstrained said:**
> Maybe the 'bootable' flag on your boot partition isn't set.

I've tried to boot with the boot flag set and without it with the same result.  I read in another Linux forum, that the boot flag actually makes no difference, the OS just ignores it.  I found that comment to be kind of an odd idea since, I assume the flag exists for a reason.  If the system actually does ignore it then setting it should make no difference, so there would be no harm in doing so.

---

### Post by Bucky Ball on 2011-02-20
Killdisk and rewriting with zeros makes the drive *completely* blank. You are right; there will be no MBR to write grub to unless you put one there. Grub is probably written to the same partition as Ubuntu and that partition no doubt starts at the very beginning of the drive; where MBR should be. 

I had the same problem with DBan some years ago and spent the best part of a day figuring it out. Can't remember how I resolved now though unfortunately.

---

### Post by mdouble on 2011-02-20
> **mikewhatever said:**
> Have you changed the default grub location during the installation by any chance? If so, you'd have to reinstall grub making sure it is in the MBR. If not, get the [bootinfo script]("http://sourceforge.net/projects/bootinfoscript/"), run it from the live cd and post the output.

Hi and thanks for your prompt reply.  Sometime tomorrow I will run the bootinfo script and post the output here.  I can't do that right at this moment but will get to it ASAP.  

Before I do that, perhaps you could answer one question from my original post.  Do you know if when formatting a drive, if the formatting process creates a new MBR, assuming that the old one was destroyed by overwriting the drive with 0's using Kill Disk?

---

### Post by Bucky Ball on 2011-02-20
Read my last post. #5

---

### Post by mikewhatever on 2011-02-21
> **mdouble said:**
> Hi and thanks for your prompt reply.  Sometime tomorrow I will run the bootinfo script and post the output here.  I can't do that right at this moment but will get to it ASAP.

That's ok, I am not in a hurry.;)

> Before I do that, perhaps you could answer one question from my original post.  Do you know if when formatting a drive, if the formatting process creates a new MBR, assuming that the old one was destroyed by overwriting the drive with 0's using Kill Disk?

The tool you used may have formatted the MBR as well, but that shouldn't matter, because by default, the Ubuntu installer overwrites the MBR and puts its own code there.
PS: Forgot to ask, are there more then one hdds?

---

### Post by mdouble on 2011-02-21
Hi again,  
Following is the output from boot_info_script*.sh  There are a couple of sections that might benefit from an explanation.  Sde1 shows Windows XP as being installed.  It shows up in this result because it is attached to a network router on the system.  You can disregard it as it has nothing to do with the boot on the main system.  

There are three internal drives on the system.  Ubuntu is installed on sda.  

It might be important to note that I have a live CD for Gparted.  When I run this CD Gparted correctly reports 3 internal drives with 2 different drive types, hda1 74.60 GIB  hdb 74.53 GIB and sda 149.05 GIB  Ubuntu is installed on hda1

Partition table for hda1 is msdos  files system is ext4 on all drives.  

When I use the Gparted program in Ubuntu 10.10 it reports all the drives as being sd type, which is not correct.

That information might not be entirely relevant to fixing my boot issues, however I felt it was worth mentioning.  The difference in reporting drive types between the live Gparted CD and the internal Ubuntu version of Gparted is confusing.  I came to rely on the live CD report as being accurate.  

Having now said all that, following is the output of the boot_info_script


 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sde

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,159,359   150,157,312  83 Linux
/dev/sda2         150,161,406   156,301,311     6,139,906   5 Extended
/dev/sda5         150,161,408   156,301,311     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,296,384   156,296,322  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63     7,822,079     7,822,017   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        de974183-953b-4dda-a8b7-ce7912fd7bfd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8266bc9f-3d64-43f2-9e0e-65ae9007c61b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        e37b244b-85fb-46f6-900a-918306e1a6f7   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        d6c70031-ccac-4b6c-b179-24f0550ffbaf   ext3                                     
/dev/sdc: PTTYPE="dos" 
/dev/sde1        1813-2387                              vfat                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/de974183-953b-4dda-a8b7-ce7912fd7bfd ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sde1        /media/1813-2387         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set de974183-953b-4dda-a8b7-ce7912fd7bfd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set de974183-953b-4dda-a8b7-ce7912fd7bfd
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de974183-953b-4dda-a8b7-ce7912fd7bfd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=de974183-953b-4dda-a8b7-ce7912fd7bfd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de974183-953b-4dda-a8b7-ce7912fd7bfd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=de974183-953b-4dda-a8b7-ce7912fd7bfd ro single 
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
    search --no-floppy --fs-uuid --set de974183-953b-4dda-a8b7-ce7912fd7bfd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de974183-953b-4dda-a8b7-ce7912fd7bfd
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8266bc9f-3d64-43f2-9e0e-65ae9007c61b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
   2.3GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
    .3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd

---

### Post by mdouble on 2011-02-21
Thanks for your reply, your answer pretty much confirms my original suspicion.  However, previously, when looking at the drive with Gparted I noted there was a 1 MiB bit of unallocated space ahead of the hda1 partition.  I'm not sure if this is still there and will have to go back and check again.  If it is, could this be an indication that when Ubuntu installed it assumed there should be an MBR in the first sector and let that space unused?

---

### Post by mdouble on 2011-02-21
Hi again,  You will now find the output from my boot_info_script in post 9.  In addition to that I've been researching methods of creating a new MBR, assuming that a part of my problem might be that the original MBR was toasted when I used Kill Disk to overwrite the drive - as I noted in my original post.  What I turned up is a page from the Ubuntu manual on how this can be done using some tools Linux / Ubuntu Tools.  

If you have an interest in checking these out you can find the page here [http://manpages.ubuntu.com/manpages/lucid/man8/gdisk.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/gdisk.8.html)

I read through these instructions and made an attempt to create a new MBR after downloading 2 of the tool mentioned.  Unfortunately I don't have enough experience to use these correctly so failed.  I'm not sure what exactly I'm doing wrong and admit to being a bit over my head.  All the same this looks like a  promising approach for someone who knows more than I do.

I will keep looking for ways to create a new MBR using Linux / Ubuntu and, if I find something that is easy to follow will report it here.  In the meantime if anyone knows how to do this and can offer a step by step method I can follow please feel free to offer it in a post on this thread.  

The big problem seems to be that I used the 0 overwrite method of removing all the data from the drive in the first place.  At least that's my working theory.  Please check out the output I posted in 9 and see if this makes sense to any of you.

---

### Post by Hakunka-Matata on 2011-02-21
```
sudo apt-get install mbr
```

or you can install 'mbr' via synaptic

---

### Post by mdouble on 2011-02-21
I also found the following information on Wikipedia regarding a tool called ms-sys.  This also looks like a promising solution to creating a new mbr but I have no idea how to use it.  If you have used this in the past or know someone who has I'd be grateful for some instruction.  

In [Linux]("http://en.wikipedia.org/wiki/Linux"), ms-sys may be used to install a standard MBR. The [GRUB]("http://en.wikipedia.org/wiki/GRUB") and [LILO]("http://en.wikipedia.org/wiki/LILO") projects have tools for writing code to the MBR sector, namely grub-install and lilo -mbr. The GRUB Legacy grub interactive console also has commands to write to the MBR, as it has the setup and embed commands, however grub-install in GRUB2 can so far only be run on an already booted *IX system. dd is also a commonly used POSIX command to copy or overwrite any sector, MBR included.

---

### Post by mdouble on 2011-02-21
Thanks for the help re mbr.  I have run the code and the system advised that it was setting up mbr.  Is there something more to do or is this it?

---

### Post by oldfred on 2011-02-21
You are booting with grub2, you do not want ms-sys, mbr, lilo or any other boot loader. Those will boot windows or other system that use boot flag.

If you have installed one of those other boot loaders, you will have to reinstall grub2.

The boot script shows grub installed to the MBR and it shows the partition table. You would not see sda1, sda2 & sd5 if you did not have MBR.
> Grub 2 is installed in the MBRWhen you did kill disk you did overwrite the MBR, but the MBR is just the 1st sector of the drive. It has a boot loader and a partition table. Any partitioning restores a partition table and installing grub2 put a boot loader into the MBR.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Windows (and lilo) use the boot flag in the partition to know which partition to jump to. More boot code is then in the paritition boot sector which is at the start of the partition. Some BIOS will not let you boot without the boot flag, but grub does not use it.

Is your gparted disk older? Linux changed to a unified driver for all disks. hda is not used any more. All IDE/SATA/USB etc drives are sda, sdb etc.

---

### Post by Hakunka-Matata on 2011-02-21
[http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/]("http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/")

The above link describes how to install the mbr program, 
after that you have to execute the program to create the mbr on a drive
after creating the mbr, you have to install a boot loader into it (for instance)

this is a new problem for me that you're evidently experiencing

---

### Post by Hakunka-Matata on 2011-02-21
although the article is written for a pendrive/USB drive, it should work the same on any drive

---

### Post by oldfred on 2011-02-21
Hakunka-Matata's link is for a flash drive that boots with syslinux, not a full install that boots with grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Is grub actually booting and you get a system error? If you only have one system, grub does not show menu, unless you hold down shift key from BIOS until menu appears.

---

### Post by Hakunka-Matata on 2011-02-21
@oldfred, thanks for correcting that.  That being said, why (I wonder) is there a 'mbr package' anyway.  I thought creating a msdos partition table would also create the MBR area.  Is it not true that any drive (USB/Floppy/SSD/harddrive) with a msdos partition table has the same MBR structure.  If this question is considered a 'hijack', I apologize

---

### Post by Hakunka-Matata on 2011-02-21
after reading post #15, I understand.  oldfred's post slipped in there while I was preparing a reply, I didn't see it before posting my reply.  so Ubuntu's mbr package is in fact another boot loader?

---

### Post by oldfred on 2011-02-21
The MBR structure is the same but the code that goes into the beginning can be anything. mbr actually is a boot loader like lilo, windows boot loader, grub or grub2.

---

### Post by mdouble on 2011-02-21
> **oldfred said:**
> You are booting with grub2, you do not want ms-sys, mbr, lilo or any other boot loader. Those will boot windows or other system that use boot flag.

If you have installed one of those other boot loaders, you will have to reinstall grub2.

The boot script shows grub installed to the MBR and it shows the partition table. You would not see sda1, sda2 & sd5 if you did not have MBR.
When you did kill disk you did overwrite the MBR, but the MBR is just the 1st sector of the drive. It has a boot loader and a partition table. Any partitioning restores a partition table and installing grub2 put a boot loader into the MBR.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Windows (and lilo) use the boot flag in the partition to know which partition to jump to. More boot code is then in the paritition boot sector which is at the start of the partition. Some BIOS will not let you boot without the boot flag, but grub does not use it.

Is your gparted disk older? Linux changed to a unified driver for all disks. hda is not used any more. All IDE/SATA/USB etc drives are sda, sdb etc.

Thanks for your response, all that is very good information to have.  I feel enlightened.  I will look at how to install Grub2.

---

### Post by oldfred on 2011-02-21
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by mikewhatever on 2011-02-21
So, people, any ideas why the originally installed system wasn't booting? It's pretty clear that zeroing the disk wasn't the problem, and also, everything looked correct MBR wise. I am inclined to think, given the multiple hdds, that the OP (mdouble) simply wasn't booting from /dev/sda.

---

### Post by mdouble on 2011-02-21
> **oldfred said:**
> How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Hi again, and thanks for your response to my problem.  I followed the sequence precisely and it worked as expected, however, regrettably it still did not fix the original boot problem.  After I rebooted and removed the live CD, the system still will not boot of the HD. After the bios loads I get the following error message.  (Reboot and Select proper Boot device or Insert Boot Media in Selected Boot Device and press a key).  

It is important to note that Ubuntu is fully installed on sda in the partition sda1.  According to everything I did under the directions above I should now have GRUB installed and functional.  Yet I still can't boot normally from the HD.  Something seems to be amiss with the first segment where the MBR is supposed to be located.  

Ideas and suggestions are still most welcome.  I'm grateful for all the help I've had so far, I've learned a lot about Linux, but I also need to get my system functional.

---

### Post by mikewhatever on 2011-02-21
Can you make sure you actually boot from sda. Enter the BIOS boot section and check which of the hdds comes first.

---

### Post by Bucky Ball on 2011-02-21
> **mikewhatever said:**
> can you make sure you actually boot from sda. Enter the bios boot section and check which of the hdds comes first.

+1.

---

### Post by mdouble on 2011-02-21
sda is the drive where Ubuntu is installed and it is first in the list of 3 internal drives in this machine.

---

### Post by mdouble on 2011-02-21
> **mikewhatever said:**
> Can you make sure you actually boot from sda. Enter the BIOS boot section and check which of the hdds comes first.

I just realised that I didn't actually answer your question in my last post.  Sorry about that, here's what you need to know.  I have the boot order set to boot from the CD Drive first and the primary HD second.  When I have a the live CD in the drive it boots from that drive.  If I remove the CD the bios defaults to the primary HD which is sda.  

I will reconfigure the bios as a test and reboot, but I doubt this will make any difference.  Before I overwrote the drive using Kill Disk I have on many occasions set the CD Drive as first in the boot order when using certain programs that needed to boot before the primary drive.  

This always worked in the past.  The only thing that has changed since then was that I overwrote the drive using Kill Disk and then reformatted.  I am suspecting now that perhaps something went amiss with the format.  It may be best if I go back and reformat again to be sure I've gotten it right from that basic step.

If you have any suggestions about the best way to format the drive prior to reinstalling Ubuntu I'd be interested to have them.  If I missed something in that first step this could have caused all the problems that followed.  

Something is obviously still wrong or all that I've done since should have fixed the problem.

---

### Post by mdouble on 2011-02-21
> **Bucky Ball said:**
> +1.

Just for the sake of offering additional information I'm posting a list of drive info below.  As you can see from the top of the out put I used the command lshw -C disk to probe the drives for a complete description. Every drive in the system is shown here.  

  	 	 	 	p { margin-bottom: 0.08in; }  ubuntu@ubuntu:~$ sudo lshw -C disk  
   *-disk:0                 
        description: ATA Disk  
        product: WDC WD800JB-00JJ  
        vendor: Western Digital  
        physical id: 0.0.0  
        bus info: scsi@0:0.0.0  
        logical name: /dev/sda  
        version: 05.0  
        serial: WD-WCAM9L894126  
        size: 74GiB (80GB)  
        capabilities: partitioned partitioned:dos  
        configuration: ansiversion=5 signature=00062aa5  
   *-disk:1  
        description: ATA Disk  
        product: ST380011A  
        vendor: Seagate  
        physical id: 0.1.0  
        bus info: scsi@0:0.1.0  
        logical name: /dev/sdb  
        version: 8.01  
        serial: 3JVD9Y2X  
        size: 74GiB (80GB)  
        capabilities: partitioned partitioned:dos  
        configuration: ansiversion=5 signature=1f31cd03  
   *-disk  
        description: ATA Disk  
        product: ST3160815AS  
        vendor: Seagate  
        physical id: 0  
        bus info: scsi@2:0.0.0  
        logical name: /dev/sdc  
        version: 3.AA  
        serial: 9RA9VD97  
        size: 149GiB (160GB)  
        capabilities: partitioned partitioned:dos  
        configuration: ansiversion=5 signature=000a4f73  
   *-cdrom  
        description: DVD-RAM writer  
        product: DVDRAM GH22NS50  
        vendor: HL-DT-ST  
        physical id: 1  
        bus info: scsi@3:0.0.0  
        logical name: /dev/cdrom  
        logical name: /dev/cdrw  
        logical name: /dev/dvd  
        logical name: /dev/dvdrw  
        logical name: /dev/scd0  
        logical name: /dev/sr0  
        logical name: /cdrom  
        version: TN00  
        capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
        configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready  
      *-medium  
           physical id: 0  
           logical name: /dev/cdrom  
           logical name: /cdrom  
           configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted  
   *-disk  
        description: SCSI Disk  
        physical id: 0.0.0  
        bus info: scsi@4:0.0.0  
        logical name: /dev/sdd  
        size: 4008MiB (4203MB)  
        capabilities: partitioned partitioned:dos  
        configuration: signature=0001c7c7  
 ubuntu@ubuntu:~$

---

### Post by oldfred on 2011-02-22
I have not paid attention to some of the details. Are these IDE or SATA drives? Is sdb different somehow? BIOS determines boot order, but with IDE drives, jumpers or locations on cable may control primary master or boot drive. I do not know if physical id or bus info are telling us something or not.

sda:
physical id: 0.0.0  
        bus info: scsi@[COLOR=Red]0[/COLOR]:0.0.0  
        logical name: /dev/sda  

physical id: 0.1.0  
        bus info: scsi@[COLOR=Red]0:0.1.0  [/COLOR]
        logical name: /dev/sdb  

physical id: 0  
        bus info: scsi@[COLOR=Red]2[/COLOR]:0.0.0  
        logical name: /dev/sdc  

physical id: 0.0.0  
        bus info: scsi@[COLOR=Red]4:[/COLOR]0.0.0  
        logical name: /dev/sdd  

physical id: 1  
        bus info: scsi@[COLOR=Red]3[/COLOR]:0.0.0  
        logical name: /dev/cdrom

---

### Post by mdouble on 2011-02-22
Hi again,
I'm pleased to report that I've solved my boot issues, but the solution was somewhat more involved that I expected. My originally started with 3 drives -,2 of these are 80 Gig and one is a 160 Gig.  The master was an 80 Gig drive, with the second 80 Gid and the 160 Gig as slaves.  I was attempting to install Ubuntu on the master 80 Gig drive, but as you will be aware the install failed over and over again.  I tried all the suggestions I could find in forums as well as those offered by others contributing to this thread.  

Nothing I tried worked and the drive would not boot.  After giving myself a night to reflect, I came the conclusion that the issue must be related to how Ubuntu was seeing the devices.  To test my theory I physically removed the Mater drive, reset the second 80 Gig drive in the chain as the master and reinstalled Ubuntu to that drive.  I kept the install simple and had Ubuntu format and use the whole drive.  As requested I also created a second virtual partition for the swap area.

After a full install the drive still refused to boot.  The problem was exactly the same as had been the case with the first drive.  At this point I noticed that the last drive in the sequence, a 160 Gig SATA drive, was not attached to the same IO ribbon as the first 2 drives.  It had it's own dedicated data ribbon and power supply.  While looking at the jumpers on the back of the second 80 Gig drive I note that one there were three possible settings listed.  1) master 2) slave 3)cable select.  It has been set to slave.  

I removed the second drive leaving the 160 Gig drive in the machine.  I set the jumpers on this drive to master and reinstalled Ubuntu.  As before I created a new partition and set the flag to root.  I then created a virtual partition for the swap area.  After the install completed I rebooted the machine as usual, after removing the live CD and it booted directly off the drive.  This drive is obviously now Sda and the root partition is sda1.  

It is important to note that I had previously run windows XP Pro on this machine with a WUBI installation of 10.04 on this machine with all three drives in place.  In that configuration with that software the machine worked perfectly, until my GRUB was overwritten making Lucid unavailable.  I spent a good deal of time trying to fix that problem before I decided to format the drive, get rid of XP and go with 10.10.  

That is when I discovered the boot problems which prompted me to start this thread.  In summary the underlying issue which seems to have caused this has something to do with an issue that occurred between Ubuntu and the drives and their configuration in my machine.  I may try to reinstall the 2 80 Gig drives again as slaves and see if they will work in that set-up.  

Thanks to everyone who pitched in to help me work through this.  It has been a real learning experience.  I now know a lot more about Ubuntu and Linux than I did before.  I hope this thread may serve to help someone else with a similar problem.

---

### Post by oldfred on 2011-02-22
We have seen issues like yours with mixed IDE and SATA drives. BIOS do not seem to be consistent. IDE drives only boot from primary master. SATA drives are set on which to boot by BIOS, they have no jumpers.

With IDE chains, it can get confusing. You have primary & secondary with two ribbon cables. You can have master & slave on each ribbon connector. Newer system have new 80 conductor cables that can use cable select. Also some hard drives have master with slave jumpers.

You cannot use a 40 conductor cable in the cable select mode. You cannot have two masters on the same cable. Sometime the CD drive also is set with jumpers on only has the 40 conductor cable.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Hakunka-Matata on 2011-02-22
> **oldfred said:**
> I have not paid attention to some of the details. Are these IDE or SATA drives? Is sdb different somehow? BIOS determines boot order, but with IDE drives, jumpers or locations on cable may control primary master or boot drive. I do not know if physical id or bus info are telling us something or not.


Well done oldfred

---

