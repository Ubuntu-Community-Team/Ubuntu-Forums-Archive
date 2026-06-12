---
title: "Dual Boot Windows 7 and Ubuntu 10.10"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by knightmt on 2010-10-19
Hi
Apologise for my ignorance I have no experience with Linux.
I have an installation of Windows 7 professional 64bit in RAID 1(mirrored) and I put an extra HD in ages ago to install a Linux Based OS. 

 I have only recently upgraded to Windows 7 a couple of months ago. So a couple of days ago I tried to install Ubuntu 10.10 desktop version onto the extra drive, as I read some of the documentation and hoped that the boot loader would be able to recognise Windows 7 and be able to put Ubuntu onto a separate drive(no partitioning necessary on my part). 

 I went through the installation process with a CD with the iso file on it. I opted to go for an install alongside another OS(I do not know if this was a mistake as I am using separate drives) I did not use the manual installation option as I am not an advanced user.  When I tried to start up, the BIOS loaded up then it said my RAID was healthy, then there might be an error message, then nothing just a black screen with a dash in the top left hand corner. 
I thought there may be an error in the installation so I overwrote the third disk(by reinstall once) but nothing changed.

Now I am using the temporary version or Live CD (if that is what using the OS straight of the CD is called)
I did see an error message this time when I put the CD in, though I had very little time to write it down I only got the beginning. 
(process 448) GLib warning  unknown user  (0)
unable to open SDB/DEV

I was looking at another query as I have no previous knowledge of Dual Boot and someone suggested some diagnostic or at least that is what it appears to me to be.
using sudo fdisk -l in the terminal?


Here were the results

  ubuntu@ubuntu:~$ sudo fdisk -l

  Disk /dev/sda: 250.1 GB, 250059350016 bytes
  255 heads, 63 sectors/track, 30401 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x38523cca

     Device Boot      Start         End      Blocks   Id  System

  Disk /dev/sdb: 250.1 GB, 250059350016 bytes
  255 heads, 63 sectors/track, 30401 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x38523cca

     Device Boot      Start         End      Blocks   Id  System

  Disk /dev/sdc: 250.1 GB, 250059350016 bytes
  255 heads, 63 sectors/track, 30401 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x0003f2fe

     Device Boot      Start         End      Blocks   Id  System
  /dev/sdc1               1       29165   234259456   83  Linux
  /dev/sdc2           29165       30402     9936897    5  Extended
  /dev/sdc5           29165       30402     9936896   82  Linux swap / Solaris

  Disk /dev/dm-0: 250.1 GB, 250059348992 bytes
  255 heads, 63 sectors/track, 30401 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x38523cca

       Device Boot      Start         End      Blocks   Id  System

I hope this makes sense to someone as I have no clue what is going on, I imagine if I went medieval I could disconnect one of the RAID disks and use the windows DVD to fix that boot, but I have mobility issues so I not particularly like opening my desktop.

---

### Post by oldfred on 2010-10-19
Welcome to the Forum.

I do not know RAID, but to help post this so we can see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by kansasnoob on 2010-10-19
> I opted to go for an install alongside another OS(I do not know if this was a mistake as I am using separate drives)

Yes, that was a mistake :(

The output of fdisk -l is showing no sign of Windows. Did you perhaps click on "use entire partition" or "use entire disc" when you got to this screen:

[ATTACH]172856[/ATTACH]

I filed a bug report during iso-testing but got shot down:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Please tell me you backed up your data before installing. If not, and if you need to try and recover any data, do not attempt to boot the newly installed Ubuntu anymore, just use the Live CD.

So, using the live CD let's get a closer look. Post the output of the following commands:

```
sudo parted /dev/sda print
```

```
sudo parted /dev/sdb print
```

```
sudo parted /dev/sdc print
```

And also post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You may be able to use PhotoRec to recover data if necessary.

---

### Post by knightmt on 2010-10-19
results.txt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_cgdbcbbi

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   468,520,959   468,518,912  83 Linux
/dev/sdc2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdc5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: nvidia_cgdbcbbi ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_cgdbcbbi: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_cgdbcbbi: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        820ce3a9-d284-456d-bd4b-0c53c9676d34   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        5eb6bc95-099a-4e8d-8b16-1346c0d78b01   swap                                     
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_cgdbcbbi

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=820ce3a9-d284-456d-bd4b-0c53c9676d34 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=820ce3a9-d284-456d-bd4b-0c53c9676d34 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=820ce3a9-d284-456d-bd4b-0c53c9676d34 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=5eb6bc95-099a-4e8d-8b16-1346c0d78b01 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
 202.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic-pae
  13.0GB: boot/vmlinuz-2.6.35-22-generic-pae
    .5GB: initrd.img
  13.0GB: vmlinuz

---

### Post by knightmt on 2010-10-19
sudo parted /dev/sda print


Model: ATA Hitachi HDT72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

---

### Post by knightmt on 2010-10-19
ubuntu@ubuntu:~$ sudo parted /dev/sdb print
Model: ATA Hitachi HDT72502 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

---

### Post by knightmt on 2010-10-19
[FONT=monospace]ubuntu@ubuntu:~$ sudo parted /dev/sdc print
Model: ATA Hitachi HDP72502 (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  240GB  240GB   primary   ext4
 2      240GB   250GB  10.2GB  extended
 5      240GB   250GB  10.2GB  logical   linux-swap(v1)

[/FONT]

---

### Post by knightmt on 2010-10-19
@kansasnoob 
I did choose to install to the entire disc but it was not the disks that Windows was on?
There were two options the mirrored drives or SC3 and I only installed to the SC3.

---

### Post by kansasnoob on 2010-10-19
> **knightmt said:**
> @kansasnoob 
I did choose to install to the entire disc but it was not the disks that Windows was on?
There were two options the mirrored drives or SC3 and I only installed to the SC3.

Well, I'm sorry but I think these two bugs (both of which I filed) hosed you:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

It's so upsetting to me I filed an Ayatana request today with a cc to SABDFL. I've seen no response yet.

IMHO you now need to figure out a strategy to recover your Win data. With RAID maybe it's only unreadable by Linux, I'm not sure.

---

### Post by oldfred on 2010-10-19
What does this show:

```
sudo dmraid -l
```

---

### Post by knightmt on 2010-10-20
ubuntu@ubuntu:~$ sudo dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

---

### Post by knightmt on 2010-10-20
@kansasnoob Whatever has happened is pretty much my fault as I did not know what I was doing and even though I do not know anyone who uses Ubuntu currently, I could have done some preparation.

To be honest I do not really understand what these bugs are, something about the option to insall alongside not being mutually exclusive with a partitions. 

A couple of things that do not make sense to me. Firstly I do have 3 drives physically, not just in name A:,  B: or whatever
so when I chose to use the whole disk, how did it affect the other disks. Does the graphic that represents the installation refer to more than one physical disk. 
Secondly if I am using RAID 1 how was this affected by Ubuntu install as I would guess that you would need to use the proprietry drivers to install in a RAID format. And if I had changed the disks wouldn't the array be unhealthy as they would be desynchronised.
Also if I install a 32bit version of Ubuntu can this detect a 64bit version of Windows?

p.s. it is not the data loss that concerns me as I have pretty much got everything in duplicate, it is the time that it takes to install all the drivers and programs, I have quite a lot of devices and large programs that are a hassle to install.

I am still hoping at least that one of my RAID drives has my windows installation on it, but why is nothing starting up including Ubuntu.

---

### Post by kansasnoob on 2010-10-20
Sorry to take so long but I'll try to explain as best I can.

> when I chose to use the whole disk, how did it affect the other disks. Does the graphic that represents the installation refer to more than one physical disk. 

The first thing to understand is Linux device designations. Your three drives are recognized as '/dev/sda', /dev/sdb, and '/dev/sdc'. The last character (a,b.c) indicates the actual drive designation.

You'll notice that the output '/dev/sdc' shows three partitions: '/dev/sdc1', '/dev/sdc2', and '/dev/sdc5'. You'll notice that many Ubuntu tutorials will refer to designations in a manner similar to '/dev/sdXY', then explaining that the 'X' indicates the drive designation and the 'Y' indicates the partition designation.

Clear as mud :confused:

And Linux/Ubuntu very well may not recognize your drives in the same order as Windows, so the first step should always be finding out how Ubuntu recognizes all of your drives and partitions. Probably the simplest way to do that is using Gparted which is on all Ubuntu Live CD's in System > Administration.

Here's a somewhat representative graphic:

[http://members.iinet.net.au/%7Eherman546/p22/009.png](http://members.iinet.net.au/%7Eherman546/p22/009.png)

You'll notice in the upper right hand corner you can toggle between drives.

So, ultimately I need to answer your question with a question :(

How do you know which drive you selected?

As far as the installer goes you should have seen three options:

1: Install alongside other operating systems
2: Erase and use entire disc
3: Specify partitions manually (advanced)

Having chosen "Install alongside other operating systems" the installer (aka: ubiquity) would have assumed that you wanted to resize Windows and install alongside it on the same drive. If you look at that screenshot in post #3 you'll see at the very top it indicates the device designation (in that case SCSI2 (0.0.0) (**sdb**)-80.0GB etc).

I don't believe you'd even have been able to "toggle" to the empty drive using that option because the empty drive would have had no partition(s) to "install alongside" of, and IMO being offered to “Use entire partition” or “Use entire disc” is horribly confusing :(

Had you chosen "Erase and use entire disc" you should have been able to "toggle" between all three drives but **you needed to be darn sure which drive you wanted to use!** That's why it's so important to know how Ubuntu recognizes your drives and partitions.

Actually I much prefer the "Specify partitions manually (advanced)" option if I'm attempting to save an existing OS or any existing data partitions. Even though the new ubiquity UI is quite different this general method still applies:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

You'll see there that they actually create the new partitions in advance using Gparted, then simply jot down the new device designations, and then be certain to install to those new partitions.

You'll find that most people like to create a primary partition at the beginning of the drive for "/" (aka: root) about 8 to 10 GB, then use the rest of the available space to create an extended partition, then at the far right end of the extended partition create an appropriate sized logical SWAP, and use the remainder of the space to create a logical "/home" kind of like this:

[ATTACH]172936[/ATTACH]

Also if Gparted does not for some reason properly recognize your existing partitions this is the time to know it, then you can figure out what's up before proceeding any further.

> why is nothing starting up including Ubuntu

I'm not sure, we might be able to overcome that but I didn't even want to try and boot Ubuntu until we figured out if Windows could be saved. I also don't know diddly about RAID.

If you have your Win 7 disc I'd begin by booting that and see if it finds an OS to repair. If so I'd try recovering the Windows bootloader first:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Should you get lucky and find a bootable or repairable Windows we could then try getting Ubuntu booting.

---

### Post by oldfred on 2010-10-20
the boot script and the parted do not show sda or sdb the RAID drives. It looks like Ubuntu installed to sdc.

This command supposed remounts the raid from man dmraid
"dmraid -ay" activates all software RAID sets discovered.

sudo dmraid -ay 

Then rerun the boot script and see if it shows sda & sdb correctly??

---

### Post by knightmt on 2010-10-20
@oldfred

ubuntu@ubuntu:~$ sudo dmraid -ay 
RAID set "nvidia_cgdbcbbi" already active

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_cgdbcbbi

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   468,520,959   468,518,912  83 Linux
/dev/sdc2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdc5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: nvidia_cgdbcbbi ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_cgdbcbbi: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_cgdbcbbi: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        820ce3a9-d284-456d-bd4b-0c53c9676d34   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        5eb6bc95-099a-4e8d-8b16-1346c0d78b01   swap                                     
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_cgdbcbbi

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=820ce3a9-d284-456d-bd4b-0c53c9676d34 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=820ce3a9-d284-456d-bd4b-0c53c9676d34 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 820ce3a9-d284-456d-bd4b-0c53c9676d34
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=820ce3a9-d284-456d-bd4b-0c53c9676d34 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=5eb6bc95-099a-4e8d-8b16-1346c0d78b01 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
 202.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic-pae
  13.0GB: boot/vmlinuz-2.6.35-22-generic-pae
    .5GB: initrd.img
  13.0GB: vmlinuz

---

### Post by knightmt on 2010-10-20
@kansasnoob
It may take me a couple of reads to digest your reply.

I guess the bit that describes what is happening is the UUID
Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_cgdbcbbi: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        820ce3a9-d284-456d-bd4b-0c53c9676d34   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        5eb6bc95-099a-4e8d-8b16-1346c0d78b01   swap                                     
/dev/sdc: PTTYPE="dos" 

But doesn't the boot script point out that the partitions are all on the third disc which is not the raid disks.
If I had written to the first two disk then the sections would be prefaced 
sda1, sda2 and sda5
or sdb1, sdb2 and sdb5

Is partitioned the same as formatted, in which case I may have previously formatted the third disk.
Isn't the main problem that there is no boot loader?

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_cgdbcbbi

---

### Post by knightmt on 2010-10-20
@oldFred Sorry I did realise after I posted it that it was identical to the first.

---

### Post by knightmt on 2010-10-20
@kansasnoob
How do I know which drive I selected?
It gave me two options which I found reassuring as that meant that the Mirrored drives were identified as one.
The nomenclature was something like
nvidia_cgdbcbbi/sda
and
sdc
and because I knew that the motherboard implements RAID and my motherboard is nvidia, the drives that were directly controlled by the motherboard would have the prefix nvidia. Plus it may have said RAID within the name of the drive.

I have a feeling that if I unbuild the RAID my windows disk will identify two operating systems(Win 7), but this requires me to do a bit of reading to check that I do not wipe those drives unbuilding one. I will have to check with my Windows guy what he thinks and check the motherboard manual, I can only get hold of him directly tomorrow night.

p.s. I understand your point that linux can identify the drives in a different order, but I am pretty sure that the mirrored drives were installed first and thus in the lower SATA positions and the third drive was later after I had to have the first two replaced due to one failing under RAID0.

My question still stands about the 32bit Ubuntu recognising my 64bit Windows 7 professional.

---

### Post by kansasnoob on 2010-10-21
> **knightmt said:**
> @kansasnoob
How do I know which drive I selected?
It gave me two options which I found reassuring as that meant that the Mirrored drives were identified as one.
The nomenclature was something like
nvidia_cgdbcbbi/sda
and
sdc
and because I knew that the motherboard implements RAID and my motherboard is nvidia, the drives that were directly controlled by the motherboard would have the prefix nvidia. Plus it may have said RAID within the name of the drive.

I have a feeling that if I unbuild the RAID my windows disk will identify two operating systems(Win 7), but this requires me to do a bit of reading to check that I do not wipe those drives unbuilding one. I will have to check with my Windows guy what he thinks and check the motherboard manual, I can only get hold of him directly tomorrow night.

p.s. I understand your point that linux can identify the drives in a different order, but I am pretty sure that the mirrored drives were installed first and thus in the lower SATA positions and the third drive was later after I had to have the first two replaced due to one failing under RAID0.

My question still stands about the 32bit Ubuntu recognising my 64bit Windows 7 professional.

Did you skip over what I said at the end:

> If you have your Win 7 disc I'd begin by booting that and see if it finds an OS to repair. If so I'd try recovering the Windows bootloader first:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Should you get lucky and find a bootable or repairable Windows we could then try getting Ubuntu booting.

I'd noticed in the boot script results that no bootloader is installed to any drives mbr:

> => No boot loader is installed in the MBR of /dev/sda
=> No boot loader is installed in the MBR of /dev/sdc
=> No boot loader is installed in the MBR of /dev/mapper/nvidia_cgdbcbbi


If you have a Win7 install disc you can follow these instructions to restore the Windows mbr if a Win OS is identified:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you have no disc you can get a "repair disc" here:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I'd try that before trying to get Ubuntu to boot. You may well find that Windows and your RAID are fine.

If so then we could try installing Ubuntu's grub to /dev/sdc, changing the boot order in BIOS, and see if it boots OK. If so simply run "sudo update-grub" and see if Windows is found.

Then we can work from there, although you'll need help from someone other than me to deal with getting a RAID array to boot with grub2.

My first concern is getting Windows to boot, we need to get that far first :)

If grub2 fails to cooperate with your RAID array you could install Ubuntus grub to /dev/sdc1 and then use Easy-BCD 2.0.2 to manage boot:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by kansasnoob on 2010-10-21
> My question still stands about the 32bit Ubuntu recognising my 64bit Windows 7 professional.

Yes, that should be no problem.

---

### Post by knightmt on 2010-10-21
@kansasnoob
Sorry if I sounding a bit desperate, it is more laziness than anything. I did read your whole message, but I think I was a bit overwhelmed with what you said earlier. They say that when you go to the doctor you only remember about one third of what they say, I would say that might be a little optimistic in my case.

Initially the first thing I did was try to boot with the Windows disk or at least repair, but windows did not recognise anything, which supports your analysis, but the funny thing is that it would not accept my raid drivers which are essential to install the OS when using the mirrored drives. Believe me I screwed this up with my first install with windows, if you try to install windows on a RAID disk without the drivers it is very messy. This lead me to hope that it was only looking at the unRAIDed disk. 

So basically I have get rid of the Array and try the windows repair. If this does not work then I can go for an install and see if it finds the previous data which is an option on the install, but as I said it would not recover the register which is what bothers me the most.

To be honest I regret using RAID as it is really for performance gains, where as I used it for redundancy, and even there I am worried that I failed.

---

### Post by ronparent on 2010-10-21
It does appear as if you have hosed your raid partition tables. I don't know if this would work on a raid. If not perhaps on one disk of a raid 1 set. In the General forum I saw it advised to use 'testdisk' (from synaptics) to recover a damaged ntfs partition table (submitted by Quakers). This: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
to guide you through the process.

---

### Post by knightmt on 2010-10-21
@ronparent
Thanks, though I think I am falling further down the rabbit's hole.
This could take a while.

---

### Post by ronparent on 2010-10-22
How right you are. The Ubuntu installation/live cd is supposed to make it safe for anyone to boot to or do a trial install safely. Until 10.10 There were serious inadequacies which didn't allow anyone without some linux background to install to a raid system. As you unfortunately discovered it is still too easy to inadvertently hose a raid and find yourself in a 'rabbit hole'. All your choices now are painful. Once you know what you want to do to recover post here if you need advice to proceed. Good luck.

---

