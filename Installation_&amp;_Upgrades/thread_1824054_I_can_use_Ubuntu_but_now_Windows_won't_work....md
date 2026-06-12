---
title: "I can use Ubuntu but now Windows won't work..."
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by CaseyFen2 on 2011-08-13
Hey everyone,

I'm sure that you see a thousand of these per day and I've read a number of them but none of them suit my situation just perfectly.  So here's what happened, I've got an internal HDD in my computer and I initially installed Ubuntu on it and created a partition.  Once my computer rebooted, however, I saw no option to boot Ubuntu.  It booted normally to Windows.  So, I installed it again on an external USB hard drive.  This time, it worked perfectly.  My computer booted up and I hit F12, then I chose the external HDD and Ubuntu came right up.  Then, I unhooked the external hard drive and tried to reboot my computer normally.  This time, it gets to a screen that looks like a DOS command prompt but you can't type anything in.  I have no idea what to do.  Here's the results of "sudo fdisk -l":

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003880c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36473   292967424   83  Linux
/dev/sda2           36474       37689     9764865    5  Extended
/dev/sda3           77550       77826     2218328    c  W95 FAT32 (LBA)
/dev/sda5           36474       37689     9764864   82  Linux swap / Solaris

Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a108

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      243202  1953511424    7  HPFS/NTFS

Help me please!

---

### Post by wojox on 2011-08-13
You need to keep the external usb plugged in since that where Grub2 resides.

---

### Post by YesWeCan on 2011-08-13
Sigh. You have been caught out by the Ubuntu installer which idiotically defaults to putting Grub on sda regardless of which disk you installed Ubuntu to. Lots of people fall foul of this.

Now your normal MBR boot code on your internal disk has been replaced by Grub that depends on files that are on your external disk.

A. You need to reinstall the standard MBR boot code on your internal disk.
either boot from you Windows install CD and choose repair and fixmbr (preferred)
or
boot ubuntu CD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

B. You need to install Grub to your external disk.
boot ubuntu CD
sudo fdisk -l 
see what the drive name is of the external disk, eg: sdb, and the partition name of the ubuntu root, eg: sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

---

### Post by YesWeCan on 2011-08-13
Let me check I haven't got my wires crossed. Which is your internal HDD the 2TB? You seem to have only Windows on the 2TB. But you say you installed Ubuntu to a partition on the internal but it wouldn't boot? So did you subsequently delete the Ubuntu partition on the internal?

I assume the 640GB is the external as it is the only one with Ubuntu on it. But the disk numbers are a little odd because sda is often the internal and sdd an external.

---

### Post by CaseyFen2 on 2011-08-13
YesWeCan,

The 2TB HDD is my external one and the 640GB is the internal one.  I didn't delete Ubuntu on the internal one.  In fact, once I installed it, it booted up like normal to Windows.  There was no difference so I assumed something had gone wrong and it had not installed it at all.  Should I still follow the instructions you gave and see what that does?

---

### Post by YesWeCan on 2011-08-13
Let's get a better view of what's what before I advise further. I usually give better advice when I don't make too many assumptions. ;)

Would you mind downloading this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and posting the output here inside code tags (highlight and press the # icon).

---

### Post by CaseyFen2 on 2011-08-13
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 2272b7f7-41b0-4ac0-86d2-1cc48c88e581 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   585,936,895   585,934,848  83 Linux
/dev/sda2         585,938,942   605,468,671    19,529,730   5 Extended
/dev/sda5         585,938,944   605,468,671    19,529,728  82 Linux swap / Solaris
/dev/sda3       1,245,825,024 1,250,261,679     4,436,656   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 249     1,983,743     1,983,495   6 FAT16


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048 3,907,024,895 3,907,022,848   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2272b7f7-41b0-4ac0-86d2-1cc48c88e581   ext4       
/dev/sda3        082D-1AF5                              vfat       DOS_TEST
/dev/sda5        7bf43d76-aa72-43a9-9465-6ca820ab1a26   swap       
/dev/sdc1        6131-6233                              vfat       
/dev/sdd1        DA1CE6D71CE6AE27                       ntfs       Elements

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/DOS_TEST          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1        /media/6131-6233         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 2272b7f7-41b0-4ac0-86d2-1cc48c88e581
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 2272b7f7-41b0-4ac0-86d2-1cc48c88e581
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2272b7f7-41b0-4ac0-86d2-1cc48c88e581
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=2272b7f7-41b0-4ac0-86d2-1cc48c88e581 ro  vga=771  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2272b7f7-41b0-4ac0-86d2-1cc48c88e581
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=2272b7f7-41b0-4ac0-86d2-1cc48c88e581 ro single  vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2272b7f7-41b0-4ac0-86d2-1cc48c88e581
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2272b7f7-41b0-4ac0-86d2-1cc48c88e581
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sda2       /mnt/windows    ntfs-3g defaults,umask=0 0      0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 136.151718140 = 146.191794176  boot/grub/grub.cfg                             1
   1.415039062 = 1.519386624    boot/initrd.img-2.6.38-10-generic-pae          2
  40.552188873 = 43.542581248   boot/vmlinuz-2.6.38-10-generic-pae             1
   1.415039062 = 1.519386624    initrd.img                                     2
  40.552188873 = 43.542581248   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by YesWeCan on 2011-08-13
According to bootinfoscript,

The internal 640GB drive has Ubuntu and W98 installed but is has no MBR boot code. No boot flag is set. That should mean that if you try to boot this drive it won't boot. Is that correct?

The external 2TB drive has an NTFS partition with an XP boot sector and it has Grub boot code in the MBR that is configured to find its files in the Ubuntu partition on the 640GB drive. That should mean if you try to boot this drive you will either get a Grub menu or Ubuntu will boot. Is this correct?

And what do you want to end up with?

---

### Post by CaseyFen2 on 2011-08-13
Yes!  That's exactly what happens.  If I try to boot with my external, Ubuntu comes right up.  If I try to boot with my internal, nothing happens at all.

---

### Post by raja.genupula on 2011-08-13
ok i have a solution for this , maintain same grub on both hard disk . try this 

boot from a live CD/USB 
**sudo fdisk -l** to see what the internal disk partition name is that contains your boot directory, eg: sda1
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-partition=/mnt /dev/sda1
```

Then repeat this for you external, using the external partition and drive name, eg: sdc1
```
sudo umount /mnt
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-partition=/mnt /dev/sdc1
```

---

### Post by YesWeCan on 2011-08-13
@raja.genupula: sdc is not the external drive. sdd is and it already has Grub in its MBR. Putting Grub on sda may be the right move, tho.

@CaseyFen2
I would boot off the external into Ubuntu. Confirm the internal disk is still named sda by running
[COLOR="Navy"]sudo fdisk -l[/COLOR]

Then run
[COLOR="Navy"]sudo update-grub[/COLOR]
while it runs see confirm it lists your W98 OS
Then do this to put a boot flag on your W98 partition
[COLOR="Navy"]sudo sfdisk -A3 /dev/sda[/COLOR]

Then reboot off the external again. This time you should get a Grub menu that shows Ubuntu and W98 and memtest. Select W98 and confirm it boots.

Finally, reboot the external again into Ubuntu and run
[COLOR="Navy"]sudo grub-install /dev/sda[/COLOR]
Then try rebooting off the internal with the external disconnected.
Check you can boot both Ubuntu and W98.

---

### Post by CaseyFen2 on 2011-08-13
When I run 'sudo update-grub', this is what I get:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-10-generic-pae
Found memtest86+ image: /boot/memtest86+.bin

I don't see the Windows OS.  What do you think?  Should I continue with what you said?

---

### Post by YesWeCan on 2011-08-13
I was worried about that. I don't know but it may be that Grub isn't able to detect W98. Or it may be another problem.

So if you install Grub to the internal you still won't be able to boot W98.

It may be that a standard MBR code will boot W98. But then Ubuntu won't boot unless you use the external drive. So you need to decide what you want.

If you want to install a standard MBR the best way is to boot your W98 install disk if you have one and see if is will do a repair. Otherwise, you need to boot into Ubuntu and install lilo and run it:
sudo apt-get install lilo (ignore warnings)
sudo lilo -M /dev/sda mbr

If you just want Grub on the internal then boot Ubuntu and run
sudo grub-install /dev/sda

---

### Post by YesWeCan on 2011-08-13
I admit I am a little perplexed at how you booted W98 in the first place. It had no boot flag and no MBR boot code. It is W98 that you ran before, right?

---

### Post by YesWeCan on 2011-08-13
Oh, if you want to try to boot W98 you need to do the sfdisk -A3 /dev/sda first.

---

### Post by CaseyFen2 on 2011-08-14
Yea, I was running Windows Vista.

---

### Post by CaseyFen2 on 2011-08-14
Ok, I installed and ran lilo.  Now when I try to boot up, it says "No Partition selected" or something along those lines.  Any ideas?

---

### Post by CaseyFen2 on 2011-08-14
Ok, here is the result of 'sudo parted /dev/sda print':

```
Model: ATA WDC WD6400AAKS-2 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  300GB  300GB   primary   ext4            boot
 2      300GB   310GB  9999MB  extended
 5      300GB   310GB  9999MB  logical   linux-swap(v1)
 3      638GB   640GB  2272MB  primary   fat32           lba


```

When I first installed Ubuntu, I told it to create a 10 GB partition.  And I made Windows the rest of it.  From what I can tell, that is not the case now.  Does it look like I'm just going to have to completely reinstall Windows?

---

### Post by YesWeCan on 2011-08-14
notice that the boot flag is set to partition 1. it needs to be set to 3 where your Windows partition is. The command to do this is
sudo sfdisk -A3 /dev/sda

I'm wondering why bootinfoscript reports Windows 98 in partition 3 but you were using Vista?

---

### Post by CaseyFen2 on 2011-08-14
When I set it to boot from sda3, it said that it was pulling up Windows 98.  Then it did some sort of Memory check and it said it would be done in a minute but I left it on and it eventually restarted and came back on and did it again.  The thing I'm wondering is, I can only find around 300 GB of my 680 GB harddrive.  Am I reading it wrong or does it say sda1 have 300 GB, sda5 have 10 GB and sda3 have 2GB?  Where's the other 300GB?

---

### Post by YesWeCan on 2011-08-14
parted seems to be lying.
try sudo sfdisk -luM

Is W98 working yet? Was it doing a chdisk? Thats fine, just let it do it however much it wants.

---

### Post by CaseyFen2 on 2011-08-14
Ok, I'll let it run and see what happens.  Here is the results of sudo sfdisk -luM:

```
Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     1  286101  286101  292967424   83  Linux
/dev/sda2     286102+ 295638   9537-   9764865    5  Extended
/dev/sda3     608313  610479-  2167-   2218328    c  W95 FAT32 (LBA)
/dev/sda4         0      -      0          0    0  Empty
/dev/sda5     286103  295638   9536    9764864   82  Linux swap / Solaris

Disk /dev/sdb: 243201 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdb1   *     1  1907726  1907726  1953511424    7  HPFS/NTFS
/dev/sdb2         0      -      0          0    0  Empty
/dev/sdb3         0      -      0          0    0  Empty
/dev/sdb4         0      -      0          0    0  Empty
```

---

### Post by YesWeCan on 2011-08-14
look your boot flag is back on sda1. I wonder if W98 has done that, expecting to be installed in the first partition? Perhaps you should give up on this in case it messes with Ubuntu.
You mentioned you were using Vista...on what disk was it installed?

---

### Post by CaseyFen2 on 2011-08-14
Vista was installed on the C drive.  It was my internal.  Do you have any idea where my missing GB went?

---

