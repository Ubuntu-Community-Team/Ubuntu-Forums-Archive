---
title: "Grub2 and Windows 7 - Thoroughly confused."
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by ed-koala on 2010-04-13
Ok, here's my situation.  I've done a lot of searching through the forums and everything I've found has left me too confused to know what to do.

I installed Windows 7 to my first hard drive.
I then installed Ubuntu 9.10 via alt-install CD to second hard drive.

I boot 1st HD, 2nd HD in Bios ... I know I may need to change that.

Windows 7 can't be found by Grub2.  Here is a copy of bootinfo (run from my current install of Ubuntu, not from LiveCD)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=903f98b5-112a-403e-a8f9-75b7893c2aba)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbe8c40

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dbaf8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   937,167,839   937,167,777  83 Linux
/dev/sdb2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sdb5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A2A092A134EA339                       ntfs       Windows                       
/dev/sda                                                nvidia_raid_member                               
/dev/sdb1        903f98b5-112a-403e-a8f9-75b7893c2aba   ext4                                     
/dev/sdb5        89536d05-f423-4796-b1d4-1b63e41757b3   swap                                     
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        610B70B04DE9F32D                       ntfs       My Book                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro nodmraid  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro single nodmraid
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro nodmraid  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 903f98b5-112a-403e-a8f9-75b7893c2aba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=903f98b5-112a-403e-a8f9-75b7893c2aba ro single nodmraid
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=903f98b5-112a-403e-a8f9-75b7893c2aba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=89536d05-f423-4796-b1d4-1b63e41757b3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
   3.3GB: boot/initrd.img-2.6.31-14-generic
   3.6GB: boot/initrd.img-2.6.31-20-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   3.4GB: boot/vmlinuz-2.6.31-20-generic
   3.6GB: initrd.img
   3.3GB: initrd.img.old
   3.4GB: vmlinuz
   2.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

Can anyone give simple, step by step instructions on how to get my Grub list to appear, and have Windows 7 in it?

---

### Post by Objekt on 2010-04-13
Did you already try running:

```
sudo update-grub
```

?

That should make GRUB2 search all hard drives for installed operating systems, & put them in the list of choices.

---

### Post by ed-koala on 2010-04-13
Yes, I tried that. It does not "see" windows 7.  I'm left with booting straight into Ubuntu.

I would try reinstalling the Windows MBR and then Grub2, but I'm assuming that would just get me right back where I am now, since Grub2 isn't noticing Windows 7.

I've read many posts, but there are so many different things, and most don't seem to work.  I'm lost from all the commands.

These are fresh installs.  Other than some simple software I haven't made changes, so in theory this should be simple.

---

### Post by Objekt on 2010-04-13
Yes, sometimes GRUB2 does not correctly detect what's installed.  I once had a Kubuntu 9.04 install I had erased, but it was still showing up in the GRUB2 list.  Even after running "update-grub."  Can't remember how I fixed it.

I don't know what to tell you.  I am having a similar problem, except in my case I can't boot Windows XP from the Windows 7 loader.  I think it must be GRUB2-related, because I can boot XP from the Win 7 bootloader by itself, but not if I run the Win 7 bootloader by going through GRUB2.  More details in my thread here:
[http://ubuntuforums.org/showthread.php?t=1453080]("http://ubuntuforums.org/showthread.php?t=1453080")

Like you, I have the different OSs all on separate hard drives.  That should make things easier, but it doesn't quite work.

---

### Post by ed-koala on 2010-04-13
I found a solution on the web, though it needed a bit of tweaking to work.

[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/")

Ok, now the tweaks ...

If Windows is NOT on your first partition, you will have to change (hd0,1) to whichever partition number it is on.  Chance the second number usually.

Grub will return an error if there is a space between "Windows" and "7". I made mine read Windows_7 and it worked fine.

Next, I edited /etc/default/grub (as root, use the sudo nano line from the link above and change the filename) and I put a # in front of GRUB_HIDDEN_TIMEOUT=0 so it reads # GRUB_HIDDEN_TIMEOUT=0.  That makes Grub show up.

Windows 7 now boots fine from the list.

---

### Post by oldfred on 2010-04-14
Your windows partition starts at 63 when new installs will start at 2048. Did you install over an XP install as XP started at 63? If the partition originally started at 2048 and now is at 63 you will have to repair it before the grub os-prober will find it.

I also like to have each drive with a different operating system and that operating systems boot loader in the MBR of that drive. Then if ever a drive issue you can still boot the other one. If you want you then could install grub to sdb. I would try booting from sdb (f12 or whatever key to single boot) to make sure it works first. Then you can install windows to the sda MBR and repair it. Then when in BIOS you set sdb as the first boot drive and sudo update-grub will find the windows and add it to your grub.cfg.

reinstall from working system - first find Ununtu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

---

### Post by Objekt on 2010-04-14
I used the procedure above to restore the Vista/7 bootloader to the MBR of my first HDD (sda).  

What's driving me nuts is that Windows XP can only start when the Vista/7 bootloader starts by itself.  If I load the Vista/7 bootloader from GRUB, trying to boot XP only restarts the machine.  It isn't how it worked before, and doesn't make any sense.

I also like to have one OS per drive & keep the OS's native bootloader on that drive's MBR (mostly, Windows 7 is actually installed on a different .  Before I learned how to deal with GRUB, I used to multi-boot by means of removable hard drive trays.  I would simply disconnect the drive with the OS I did not intend to use.  GRUB is a more elegant solution, but by keeping various OS's on their own drives with their own bootloaders, I can still boot *something* when I inevitably muck up GRUB.

---

### Post by oldfred on 2010-04-14
If you have multiple windows installs:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

While it is much easier to set up a new install, there may be ways to fix older installs but not easy if the second install is in a logical partition.

---

### Post by Objekt on 2010-04-15
> **oldfred said:**
> If you have multiple windows installs:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

While it is much easier to set up a new install, there may be ways to fix older installs but not easy if the second install is in a logical partition.

Thanks for the links.  I'm in the "trying to fix existing installs" category.  I don't see any reason I would need to reinstall Windows XP.  There is no issue of logical vs. primary partitions, as the disk XP is on (sda) has only two (primary) partitions total.  

The real problem is with the Windows 7 bootloader not behaving correctly.  I still have no idea what's going on there.  Since I just reinstalled the Win 7 bootloader, I don't know what else I can do to make the 7 loader boot XP properly.

---

### Post by oldfred on 2010-04-15
The boot info script showed this:
nvidia_raid_member

Are you running raid? these setting on drives have cause problems if they are not really raid.

---

### Post by Objekt on 2010-04-15
That isn't my bootinfo results above.  Mine's posted in this other thread here: [http://ubuntuforums.org/showthread.php?t=1453080]("http://ubuntuforums.org/showthread.php?t=1453080")

---

### Post by noletolucas on 2010-10-30
For me what worked was: install **grub-pc** package.

This will remove the default one that shipped with Ubuntu 10.04 -- that didnt seem to work at all.

---

### Post by v1ad on 2010-10-30
this worked for me:
```

sudo apt-get --purge remove dmraid
sudo update-grub
sudo update-grub2

```

i put in the first grub just in case you have it too. the second grub update will update grub2.

---

