---
title: "Issues with last upgrades"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Arpayon on 2010-12-28
Hi everyone, 
I've got Ubuntu 10.04 and I just tried to upgrade to last kernel (I think it's .37, cannot check now). 
I had an error when upgrade finished (cannot complete because in use by another process), then I tried to check for new upgrades and it said that it was up to date.
When I reboot the new kernel doesn't appear in grub and I can only boot the one I was using before (.36). Then this message shows up

Screen is running in the lowest resolution.
(EE) NVIDIA(0): Failed to load NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

At this point I cannot do anything, even click on the ok button cause the cursos doesn't move. I tried the recovery boot but it stops at a point.

Actually i'm trying to recover some files via windows, I tried these 3 solutions [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows) but when I try to open the linux partition with all of them nothing happens. 
Now i'm trying to make a complete backup of the partition with DiskInternals Linux Reader, but the image will be .dsk and I'm not sure I will be able to open it. In fact, if I would be able to recover the files, I could even format the partition and reinstall Ubuntu.
Edit: I think that the problem related with those programs is that i have ext4 on my linux partition, I'm searching on google how to read that.

---

### Post by dino99 on 2010-12-28
boot on recovery mode and delete xorg.conf (not needed and cause that low resolution)

run this command:

sudo rm /etc/X11/xorg.conf

(enter)

reboot and remove/purge this latest kernel (.37) from synaptic

if you want the latest kernel/packages, add this ppa to your sources.list (system admin synaptic third-party tab)

---

### Post by kansasnoob on 2010-12-28
Just checked my 10.04 and the newest kernel is 2.6.32-27, but regardless, I think it's worthwhile to try and rescue your 10.04 install.

When you say, "I tried the recovery boot but it stops at a point." do you mean that you never even reach the screen offering these options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

If you get that far I'd try the "xfix" option because it sounds rather like your nvidia driver is failing for some reason.

OTOH this "I had an error when upgrade finished (cannot complete because in use by another process)" makes it sound like choosing the option "dpkg" might make sense, followed by "grub".

Of course if you don't get to the screen offering those options we'd have to take a different approach, maybe using a chroot to try and fix things.

So, if you can get to that screen in recovery mode we should know that. If not please use any Ubuntu Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dino99 on 2010-12-28
i think he only had the command line (prompt) instead of a gui

---

### Post by Arpayon on 2010-12-28
Ok, let me explain something cause I'm fairly new to Ubuntu and can't speak properly, sorry guys.

First of all, I cannot reach that screen offering those options and i can't even write commands in the recovery mode.
I think that the problem is related to a minor issue i've been experiencing since I installed Ubuntu for the first time (like 3 months ago)

I already had windows with 2 partition, let's say C: (with windows) and D: (for datas). I said to Linux to format D: into 2 new partitions: D: (fat32) and F: (ext4) cause i wanted to continue using D: for windows. Problem is that, I had to reformat this D: from fat32 to ntfs and everytime i launch Ubuntu it says that it cannot find that partition he made the first time, so I have to press S to skip the mounting. Anyway, when Ubuntu is running he does see both C: (ntfs) and D: (ntfs since the reformatting).

Actually, i've been able to recover the files I needed so i could even reinstall Ubuntu now if things are going to become too tough for a noob like me.

---

### Post by dino99 on 2010-12-28
follow this mini howto to make a standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Arpayon on 2010-12-28
@kansasnoob:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 251277312.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   251,275,263   230,793,216   7 HPFS/NTFS
/dev/sda3         251,277,310   482,103,295   230,825,986   5 Extended
/dev/sda5         251,277,312   368,461,823   117,184,512   7 HPFS/NTFS
/dev/sda6         368,463,872   482,103,295   113,639,424  83 Linux
/dev/sda4         482,103,296   488,394,751     6,291,456  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123264 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441647 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,903,794     3,903,732  1b Hidden W95 FAT32
/dev/sdb2    *      3,903,795   142,384,094   138,480,300   7 HPFS/NTFS
/dev/sdb3         142,384,095   234,436,544    92,052,450   f W95 Ext d (LBA)
/dev/sdb5         142,384,158   234,436,544    92,052,387   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        3A240EDB240E99D1                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        28EE0191EE015908                       ntfs                                     
/dev/sda5        4C72B49B72B48B6A                       ntfs                                     
/dev/sda6        622beb39-bd3d-44d8-8007-2766157b74c6   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9877-489A                              vfat       RECOVERY                      
/dev/sdb2        00522A88522A8310                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        7E7C8EE87C8E9B13                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/00522A88522A8310  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/7E7C8EE87C8E9B13  fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 622beb39-bd3d-44d8-8007-2766157b74c6
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 622beb39-bd3d-44d8-8007-2766157b74c6
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 622beb39-bd3d-44d8-8007-2766157b74c6
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=622beb39-bd3d-44d8-8007-2766157b74c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 622beb39-bd3d-44d8-8007-2766157b74c6
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=622beb39-bd3d-44d8-8007-2766157b74c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 622beb39-bd3d-44d8-8007-2766157b74c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 622beb39-bd3d-44d8-8007-2766157b74c6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set eaee-eb49
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3a240edb240e99d1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 28ee0191ee015908
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=622beb39-bd3d-44d8-8007-2766157b74c6 /               ext4    errors=remount-ro 0       1
# /win-data was on /dev/sda5 during installation
UUID=CF2E-8E7D  /win-data       vfat    utf8,umask=007,gid=46 0       1

=================== sda6: Location of files loaded by Grub: ===================


 214.5GB: boot/grub/core.img
 214.6GB: boot/grub/grub.cfg
 191.9GB: boot/initrd.img-2.6.32-26-generic
 214.7GB: boot/vmlinuz-2.6.32-26-generic
 214.7GB: boot/vmlinuz-2.6.32-27-generic
 191.9GB: initrd.img
 214.7GB: vmlinuz

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768
```

@dino99:
If I understood properly, if I burn partedmagic on a cd and boot it at startup I will be able to manage my partitions and remove ubuntu to reinstall it in the way you suggest me, am I right?

P.s. I hate this american keyboard layout on the Live CD lol

---

### Post by dino99 on 2010-12-28
> **Arpayon said:**
> @kansasnoob:
[CODE]   

@dino99:
Are those programs you use to manage partitions for Windows or for Linux? Cause if they are for Linux I do not know how to use them atm

P.s. I hate this american keyboard layout on the Live CD lol

keyboard: at the beginning, select your language :)

Windows ? whats that ?

---

### Post by Arpayon on 2010-12-28
Sorry I edited my last reply, it sounds like a boot from cd now :)

Lol @ Language fail xD

---

### Post by dino99 on 2010-12-28
@dino99:
If I understood properly, if I burn partedmagic on a cd and boot it at startup I will be able to manage my partitions and remove ubuntu to reinstall it in the way you suggest me, am I right?

yes

---

### Post by Arpayon on 2010-12-28
Ok, let me burn it and try to use it, i'll be back if i find other problems :)

---

### Post by kansasnoob on 2010-12-28
> **dino99 said:**
> follow this mini howto to make a standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Why in the world do you post things like that? The OP already has a standard installation, and when you throw out bad suggestions that's worse than no suggestion at all!

How bad could it get if the OP decides to download 10.10? Really disastrous:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

So, if you're not sure just say so. We don't want to make things worse!

It appears that the kernel didn't fully update properly:

> 214.5GB: boot/grub/core.img
 214.6GB: boot/grub/grub.cfg
 191.9GB: boot/initrd.img-2.6.32-26-generic
 214.7GB: boot/vmlinuz-2.6.32-26-generic
 214.7GB: boot/vmlinuz-boot/initrd.img
 191.9GB: initrd.img
 214.7GB: vmlinuz

Notice how there is no "boot/initrd.img" for 2.6.32-27-generic?

That's indicative of a broken kernel update!

---

### Post by Arpayon on 2010-12-28
Here I am.
I used partedmagic to analyze and format my hd. This is a screenshot I took after formatting a partition [IMG]http://i54.tinypic.com/2whlc02.png[/IMG]

It seems that I have 2 useless partitions (sda1/sda4), don't I? I think it's Acer problem.
Btw, at this point I couldn't launch Windows cause grub didn't work, so I reinstalled 10.04 in the sda3, I'm updating it right now.
Though I have few questions:
1) I couldn't split up sda3 cause the program said I can have only 4 main partitions. I was thinking to format the whole computer with just 2 partitions (linux and windows) and make things work. Is there a guide to do this somewhere? Like what to install first and so on.
2) I was thinking about Windows not booting cause grub not working. If i have to do it, how can I fully remove Linux and making Windows boot? I mean, how do I tell to my computer not to use grub anymore and just boot the partition tagged with "boot"?
3) What to do if, like what happened to me, the kernel upgrade brokes?

---

### Post by kansasnoob on 2010-12-28
> **Arpayon said:**
> Ok, let me burn it and try to use it, i'll be back if i find other problems :)

IMHO you need a PartedMagic CD like you need a new hole in your head!

Now, I may be away from the desk off and on, I can't help that but I think I see the problem.

The new problem is that I don't know what you've done in between posting the output of the Boot Info Script and now :confused:

I don't want to just assume what you've done between then and now.

So, what have you done?

And please, using the Live CD, post the output of:

```
sudo parted -l
```

Hopefully I'll be at the desk for a few hours.

I will post some general info so others who are knowledgeable can see where I was headed :D

---

### Post by kansasnoob on 2010-12-28
> **Arpayon said:**
> Here I am.
I used partedmagic to analyze and format my hd. This is a screenshot I took after formatting a partition [IMG]http://i54.tinypic.com/2whlc02.png[/IMG]

It seems that I have 2 useless partitions (sda1/sda4), don't I? I think it's Acer problem.
Btw, at this point I couldn't launch Windows cause grub didn't work, so I reinstalled 10.04 in the sda3, I'm updating it right now.
Though I have few questions:
1) I couldn't split up sda3 cause the program said I can have only 4 main partitions. I was thinking to format the whole computer with just 2 partitions (linux and windows) and make things work. Is there a guide to do this somewhere? Like what to install first and so on.
2) I was thinking about Windows not booting cause grub not working. If i have to do it, how can I fully remove Linux and making Windows boot? I mean, how do I tell to my computer not to use grub anymore and just boot the partition tagged with "boot"?
3) What to do if, like what happened to me, the kernel upgrade brokes?

Cool, my lunch break begins soon so I should be able to hang tight! Give me a few moments.

---

### Post by kansasnoob on 2010-12-28
Arrgh! I shouldn't have said, "COOL" until I'd looked closer!

You formatted (aka: erased) everything in Ubuntu!

Are you aware of that?

Did you have things backed up from Ubuntu?

---

### Post by Arpayon on 2010-12-28
As I wrote under the screenshot, I reinstalled Ubuntu in the sda3 and now everything works.
I'm aware I lost everything, but i backed up it earlier with a tool for Win :). Actually I don't need much space for Linux, that's why I asked the first of the 3 questions, I just have to find a Windows Vista and I'd like to have about 180Gb for it and 40 for Linux. 
The other 2 questions where just for personal interest ^^'.

---

### Post by kansasnoob on 2010-12-28
> **Arpayon said:**
> As I wrote under the screenshot, I reinstalled Ubuntu in the sda3 and now everything works.
I'm aware I lost everything, but i backed up it earlier with a tool for Win :). Actually I don't need much space for Linux, that's why I asked the first of the 3 questions, I just have to find a Windows Vista and I'd like to have about 180Gb for it and 40 for Linux. 
The other 2 questions where just for personal interest ^^'.

You said:

> Actually i'm trying to recover some files via windows

Which led me to believe that you wanted to do something other than reinstall.

Regardless I'm done with this thread.

---

### Post by Arpayon on 2010-12-28
Can't u help me with questions 2 and 3? I think those are Linux issues and I'd like to know some more :)

---

