---
title: "messed up bootloader"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by slpixe on 2010-05-20
Hey all,

Installed Ubuntu 10.04 on my 2nd harddrive (took loads of retry's to try and get boot onto that hard drive)
anyway finally installed it and left it working on my 2nd drive.
But I had to load it from my first hard drives boot menu (that ubuntu had generated).

I have now installed 7 on my primary drive, and thus when I tell my mobo(bios/cmos w/e) to load my 2nd drive, it just gets to a fairly blank prompt.

How can I create the loader to go on my 2nd drive? (tell my mobo to load 2nd drive, and it goes stright to ubunto)

(basicly I don't want the 2 systems on 1 bootloader)

---

### Post by wilee-nilee on 2010-05-21
Your better off with one bootloader, grub that will let you choose or default the operating system. The way your going about it makes it much more difficult and leaves you where your at.

The MS bootloader can be reloaded with 2 commands from a install dvd and the grub bootloader can be restored with 2 commands run from a live cd, it is quite easy once you know how.

I don't know the size of your hard drives but if it was me I would have W7 and Ubuntu on one and the other used as 1 backup partition and a 2nd partition to share a ntfs partition for both operating systems.

---

### Post by darkod on 2010-05-21
> **wilee-nilee said:**
> Your better off with one bootloader, grub that will let you choose or default the operating system. The way your going about it makes it much more difficult and leaves you where your at.

The MS bootloader can be reloaded with 2 commands from a install dvd and the grub bootloader can be restored with 2 commands run from a live cd, it is quite easy once you know how.

I don't know the size of your hard drives but if it was me I would have W7 and Ubuntu on one and the other used as 1 backup partition and a 2nd partition to share a ntfs partition for both operating systems.

This is much better option.

If you can use some kind of Quick Boot menu, I could somehow understand wanting to select a disk, and not an OS in grub2. But if you actually have to go into BIOS, change settings, save them and exit, that is like starting your PC twice every time. You noticed exiting from BIOS restarts it, right?

However, if you still want to have it your way, boot ubuntu in live mode from the cd, in terminal run:

sudo fdisk -l (small L)

and we'll give you the commands needed to execute in order to put grub2 on your ubuntu disk.

---

### Post by linuxmart on 2010-05-21
> **slpixe said:**
> Hey all,

Installed Ubuntu 10.04 on my 2nd harddrive (took loads of retry's to try and get boot onto that hard drive)
anyway finally installed it and left it working on my 2nd drive.
But I had to load it from my first hard drives boot menu (that ubuntu had generated).

I have now installed 7 on my primary drive, and thus when I tell my mobo(bios/cmos w/e) to load my 2nd drive, it just gets to a fairly blank prompt.

How can I create the loader to go on my 2nd drive? (tell my mobo to load 2nd drive, and it goes stright to ubunto)

(basicly I don't want the 2 systems on 1 bootloader)

If I understand you correctly, you don't want Grub to be installed in two places, or don't want it on the Windows drive.
To fix the Windows boot, create a Rescue (startup) CD in Windows 7, boot from the CD and select **repair>cmd prompt**, and in command line run
**BootRec.exe /fixmbr**
**BootRec.exe /fixboot**

That should fix your Windows boot, but as I stated in this thread, I find that after a kernel update, Grub rewrites the Windows mbr.

[http://ubuntuforums.org/showthread.php?t=1489190]("http://ubuntuforums.org/showthread.php?t=1489190")

---

### Post by linuxmart on 2010-05-21
I think this would solve your "Grub being updated in two places" problem. I just ran the command suggested here:

[http://ubuntuforums.org/showpost.php?p=9336445&postcount=9]("http://ubuntuforums.org/showpost.php?p=9336445&postcount=9")

---

### Post by slpixe on 2010-05-21
> If you can use some kind of Quick Boot menu, I could somehow understand wanting to select a disk, and not an OS in grub2. But if you actually have to go into BIOS, change settings, save them and exit, that is like starting your PC twice every time. You noticed exiting from BIOS restarts it, right?

bingo, im using a quick boot menu on my mobo, I keep putting in and pulling out hard drives, hence I wont want to have the grub menu on a drive that I may reformat or remove, I want it on the drive that has ubuntu on.

I installed win7 after ubuntu, so it has scrapped the grub thing (so i cant get into ubuntu)

As far as im understanding, Im going to load the cd in live mode, and use
```
sudo dpkg-reconfigure grub-pc
```
to deselect my win7 drive,
then
```
sudo fdisk -l (small L)
``` to rebuild the grub loader on only the selected drives (ubuntu drive from the previous step)

Is this all correct?

Thanks for the help

---

### Post by darkod on 2010-05-21
> **slpixe said:**
> bingo, im using a quick boot menu on my mobo, I keep putting in and pulling out hard drives, hence I wont want to have the grub menu on a drive that I may reformat or remove, I want it on the drive that has ubuntu on.

I installed win7 after ubuntu, so it has scrapped the grub thing (so i cant get into ubuntu)

As far as im understanding, Im going to load the cd in live mode, and use
```
sudo dpkg-reconfigure grub-pc
```to deselect my win7 drive,
then
```
sudo fdisk -l (small L)
``` to rebuild the grub loader on only the selected drives (ubuntu drive from the previous step)

Is this all correct?

Thanks for the help

NO.

I asked for fdisk because I don't want to issue commands blind. We need:
- the name of your ubuntu partition
- the name of the disk

First show is the fdisk output from live mode, lets reinstall grub2 to the ubuntu disk, and only after you can boot the hdd ubuntu you need to do the dpkg command, it doesn't work from live mode.

PS. fdisk will only show your partitions list, it is not used to reinstall grub2.

---

### Post by slpixe on 2010-05-21
Alright fdisk here we go!

Ubuntu drive
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1534

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24043   193118208   83  Linux
/dev/sda2           24043       24793     6027265    5  Extended
/dev/sda5           24043       24793     6027264   82  Linux swap / Solaris
```

Thinks this be my win7 drive
```
Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b323b31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9000    72292468+   7  HPFS/NTFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22e80000

Disk /dev/sdc doesn't contain a valid partition table
```

I got a fair few more drives in, but im guessing when putting up grub, it wont touch them

---

### Post by darkod on 2010-05-21
You see, I would have assumed your ubuntu disk is /dev/sdb, that's why it's better not to type blind. :)

OK. To install grub2 from live mode you have to mount the root partition first, and then install grub2 telling it which parameter to use for root partition:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install it on /dev/sda (the MBR) using the /mnt as root directory, and we already mounted root there. :)

Reboot, set the 200GB disk as first option in BIOS, and you should see your grub menu. Boot ubuntu, and run that dpkg-reconfigure command as suggested earlier, to deselect /dev/sdb from grub2 updates, and to select /dev/sda if not selected.

That should sort you out.

---

### Post by slpixe on 2010-05-21
alright just done the first step
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
error: cannot seek `/dev/sdd'.
error: cannot seek `/dev/sde'.
error: cannot seek `/dev/sdd'.
error: cannot seek `/dev/sde'.
error: cannot seek `/dev/sdd'.
error: cannot seek `/dev/sde'.
Installation finished. No error reported.

```going to restart and try to boot from ubuntu drive (and remove other drives from updates)

will post success or failure

---

### Post by slpixe on 2010-05-21
alright i got booted into ubuntu

loaded the dp config in terminal
no idea how to use it though,
its asking for a package to reconfigure, (is there no gui for this)?

I will only want the ubuntu drive on this im guessing, 

(during boot it showed:
ubuntu
ubuntu down 1 version
ubuntu recov
ubuntu down 1 version recov
windows xp (which is now win7)
)

im guessing after this reconfigure, it wont ask and will just boot  stright into ubuntu, or just show the ubuntu boot's

---

### Post by darkod on 2010-05-21
If you used the command in full, it shouldn't ask which package to reconfigure because the package name was there:

sudo dpkg-reconfigure grub-pc

As for booting straight into ubuntu, it can find windows on the other disk, so it presents a menu to select OS rather than booting ubuntu automatically. If you are sure you don't want the menu, disable the os-prober with:

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

After that it shouldn't detect windows any more and it will try to load ubuntu right away.

---

### Post by slpixe on 2010-05-21
All works perfectly!

Thanks a lot everyone

---

### Post by slpixe on 2010-05-21
Problems:
ahh running into a problem now.

restarted pc, and tried loading into win7, it displayed the grub loader (which ofc only shows ubuntu).
so i figured, only grub installed itself first time updated grub, surely just have to reinstall the win7 loader, so loaded the win7 disk. went to cmd
used
```
BootRec.exe /fixmbr
BootRec.exe /fixboot
```
fixmbr worked, but fixboot said incorrect element,

tried restarting, and still only grub loader with ubuntu,

ran win7 disks repair tool for startup problems, said sucsessful,
still only grub loader - ubuntu.

idea's?
(img of only ubuntu drive selected for grub updates)
[http://img714.imageshack.us/img714/8413/grub.png](http://img714.imageshack.us/img714/8413/grub.png)

---

### Post by slpixe on 2010-05-21
where im at:

I performed a recboot.exe /scanos, and it found no installs of win7.
So i think whats happening is win7 cant read my 2 drives as my raid win7 drive.

so im currently getting the raid drivers, and will load the drivers  and perform the fixmbr and fixboot again, hopefully it will work this time.

if that dont work, I will try win7's fix boot issues thing.
if that dont work Im stuck out of idea's again

---

### Post by slpixe on 2010-05-21
I've tried with a million and on (around 30) raid drivers, some of which I know should work (cause i installed win7 the other day using them). I got a few times where it would say, "Ohh found 1 instillation at E:/ ... so i was like, ah ok. fix mbr, fix boot "ERROR element not found", ok.. try the fix startup issues,.

dont work either...
so I could really do with some help, or idea's

---

### Post by darkod on 2010-05-21
I wasn't aware you are running raid for windows, but that shouldn't change things.

Don't push too hard with the windows dvd, you see it's useless. :)

Can you run the boot info script like explained here and post the content of the results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

In case there is a boot flag correctly on your raid array, you only need standard MBR on the windows disk, we can do that with ubuntu tools too.

---

### Post by slpixe on 2010-05-26
alright I've done the boot info script (late reply due to work overload, etc).

and wow my bootup looks messed up,
I got 2 sata drives in raid with win7 on them, 2 sata drives for storage, and 1 IDE drive with ubuntu on, hope this helps.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf
 => Grub 2 is installed in the MBR of /dev/mapper/sil_agagcededfff and looks 
    on the same drive in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd1 has 
                       488394751 sectors, but according to the info from 
                       fdisk, it has 488397104 sectors.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sde1 has 
                       1953523056 sectors, but according to the info from 
                       fdisk, it has 1953525104 sectors.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sil_agagcededfff1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   386,238,463   386,236,416  83 Linux
/dev/sda2         386,240,510   398,295,039    12,054,530   5 Extended
/dev/sda5         386,240,512   398,295,039    12,054,528  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   144,584,999   144,584,937   7 HPFS/NTFS

/dev/sdb1 ends after the last sector of /dev/sdb

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,397,167   488,397,105  42 SFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63 1,953,525,167 1,953,525,105  42 SFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *            128     4,030,463     4,030,336   b W95 FAT32


Drive: sil_agagcededfff ___________________ _____________________________________________________

Disk /dev/mapper/sil_agagcededfff: 74.0 GB, 74037002240 bytes
255 heads, 63 sectors/track, 9001 cylinders, total 144603520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/sil_agagcededfff1   *             63   144,584,999   144,584,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/sil_agagcededfff1 ACE05A9BE05A6B98                       ntfs       20k raptor 70                 
/dev/mapper/sil_agagcededfff: PTTYPE="dos" 
/dev/sda1        c09f4313-b132-4c21-85f3-26c710076248   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        eabe636a-1917-4734-a6a8-1a2bd313b160   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                silicon_medley_raid_member                               
/dev/sdc                                                silicon_medley_raid_member                               
/dev/sdd1        240428100427E390                       ntfs       WD 250                        
/dev/sdd: PTTYPE="dos" 
/dev/sde1        A08014578014366E                       ntfs       Tera                          
/dev/sde: PTTYPE="dos" 
/dev/sdf1        8E74-D94E                              vfat                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
sil_agagcededfff
sil_agagcededfff1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/CD_ROM            iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdf1        /media/8E74-D94E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sde1        /media/Tera              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
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
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c09f4313-b132-4c21-85f3-26c710076248 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c09f4313-b132-4c21-85f3-26c710076248 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c09f4313-b132-4c21-85f3-26c710076248 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c09f4313-b132-4c21-85f3-26c710076248 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set c09f4313-b132-4c21-85f3-26c710076248
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/sil_agagcededfff1)" {
    insmod ntfs
    set root='(hd6,1)'
    search --no-floppy --fs-uuid --set ace05a9be05a6b98
    chainloader +1
}
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
# / was on /dev/sdc1 during installation
UUID=c09f4313-b132-4c21-85f3-26c710076248 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=eabe636a-1917-4734-a6a8-1a2bd313b160 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  90.3GB: boot/grub/core.img
  90.3GB: boot/grub/grub.cfg
  90.3GB: boot/initrd.img-2.6.32-21-generic
  90.4GB: boot/initrd.img-2.6.32-22-generic
  90.3GB: boot/vmlinuz-2.6.32-21-generic
    .4GB: boot/vmlinuz-2.6.32-22-generic
  90.4GB: initrd.img
  90.3GB: initrd.img.old
    .4GB: vmlinuz
  90.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  93 4e 28 49 07 69 e9 33  34 28 5f 09 0d 99 b9 a6  |.N(I.i.34(_.....|
00000010  7b 96 43 ee b6 14 9d 6b  1a 26 05 50 1e 1e 68 0e  |{.C....k.&.P..h.|
00000020  10 4a 4b 81 78 1e 14 e5  56 c5 3d 75 d6 36 df b5  |.JK.x...V.=u.6..|
00000030  f1 4b 6b 1d ed ff d4 41  28 80 80 01 11 0c 91 55  |.Kk....A(......U|
00000040  58 10 d6 5d 9a c2 3c b3  6f 3c dc d3 8a 9a 04 35  |X..]..<.o<.....5|
00000050  82 6a 78 17 14 59 fe fc  78 a3 d1 8b 93 f1 5e c8  |.jx..Y..x.....^.|
00000060  ba 20 62 cf 18 d5 38 9f  39 dc 4d 18 68 a4 43 48  |. b...8.9.M.h.CH|
00000070  28 8d 23 c7 68 86 ce 68  16 32 79 87 c3 21 1e 87  |(.#.h..h.2y..!..|
00000080  3a 47 29 54 4a a6 c2 a0  09 4c 07 05 23 64 23 f0  |:G)TJ....L..#d#.|
00000090  e8 09 0f 21 29 64 b8 7a  74 7a b5 73 42 7d ea cb  |...!)d.ztz.sB}..|
000000a0  08 d4 08 de b5 71 58 b2  a0 95 4a aa 5c 5a 73 54  |.....qX...J.\ZsT|
000000b0  ab 72 02 99 64 bc 4e 8b  a3 39 a2 f3 88 3e ae 19  |.r..d.N..9...>..|
000000c0  2f 72 1a f1 55 95 a8 52  f7 d5 27 bd 0d b4 c9 ea  |/r..U..R..'.....|
000000d0  ae 5a f3 2a 1c ed e8 df  ff 55 9d 34 db f3 3c c3  |.Z.*.....U.4..<.|
000000e0  57 e4 9f 76 6b 6f 6a 73  df 9a 6d 5d b2 e7 da 7e  |W..vkojs..m]...~|
000000f0  2a 1d 42 73 46 6a ca 26  2e e6 3f ab ce 5d a6 79  |*.BsFj.&..?..].y|
00000100  e9 ab 30 34 ea 96 ec b2  a7 ed 96 4f ff fb a2 64  |..04.......O...d|
00000110  e7 07 75 0c 6e da c1 8c  43 72 57 65 5b 05 09 a9  |..u.n...CrWe[...|
00000120  4c 1a 69 d7 66 ac 3d 8d  c1 9e 14 ec 00 64 99 30  |L.i.f.=......d.0|
00000130  4c 44 f0 a7 e2 5a df 53  d8 da 53 06 c2 4a 52 54  |LD...Z.S..S..JRT|
00000140  d6 36 94 f2 31 28 59 80  b4 1d ca 4d 85 41 d0 1a  |.6..1(Y....M.A..|
00000150  0a af 3c ff e7 10 5e 92  90 21 d2 39 87 1e 2c d4  |..<...^..!.9..,.|
00000160  e6 09 65 49 e8 87 c5 cd  19 28 d2 e4 80 a9 7b 85  |..eI.....(....{.|
00000170  87 24 78 2c 25 64 cb da  c5 5e d5 ac 71 20 f5 36  |.$x,%d...^..q .6|
00000180  b8 5a 53 a5 d4 b5 fd 9b  9e b0 88 73 72 d4 4a 1b  |.ZS........sr.J.|
00000190  58 38 1f 07 f0 85 21 00  00 02 7f cc 78 55 45 2b  |X8....!.....xUE+|
000001a0  1a c5 0c b6 dc 87 0a 0a  1a 29 55 79 59 24 00 60  |.........)UyY$.`|
000001b0  5c f4 8a 4c cf a9 b2 d2  8d 2e 14 42 65 18 00 fe  |\..L.......Be...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 b7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory

```

---

### Post by darkod on 2010-05-26
# / was on /dev/sdc1 during installation

The ubuntu disk was sdc during install but somehow now it's sda. sdb and sdc are the win7 raid disks.

Boot into ubuntu, and first I would recreate a new device.map with:

sudo grub-mkdevicemap

Then recreate a new grub.cfg with:

sudo update-grub

Hopefully that will sort out few things.

The next question would be whether grub2 can successfully load the win7 from the menu because it's on a raid. I see an entry for win7, but I have never had this situation to try.

You also have grub2 installed on the raid mbr which I would remove and leave those disks with windows (or generic) mbr.

---

