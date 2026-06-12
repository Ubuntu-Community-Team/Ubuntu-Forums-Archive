---
title: "After Fedora FAIL, success with Ubuntu - BUT..."
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by Leo Rivers on 2011-03-11
I bought a magazine with an ubuntu 10 DVD and it installed flawlessly on my laptop which had both Windows and Linux on it.

Unlike FEDORA it didn't lock me out! (when upgrading Fedora it accepted my name and password and then installed forgetting my password).

I was even able to install ubuntu so it seized the Fedora partition. It sees my Windows partition and the partition configured to be shared by Windows and Linux for data.

The only screw up was mine. I left the 2 FAT partitions alone thinking they were Windows but I believe I installed the SWAP space on the DOS-Window Boot partition.

OOOPS.

I have Windows presented as a selection in GRUB, (or whatever it is), but it fails to boot claiming a missing Boot item.

Can anyone suggest a remedy possible for an ignorant person like me?


By the way, ubuntu is amazing. Updates on installation, finding new packages is a breeze, found my network (efn/Quest) connection and even recognized my Mac airport.

It was painless. Even installed a driver to take advantage of my graphics card.

Leo

---

### Post by Quackers on 2011-03-11
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Leo Rivers on 2011-03-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 260943858.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda7: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   146,800,703   146,800,641  83 Linux
/dev/sda2         300,903,120   312,575,759    11,672,640  12 Compaq diagnostics
/dev/sda3         146,800,765   300,897,449   154,096,685   5 Extended
/dev/sda5         260,943,858   300,897,449    39,953,592   c W95 FAT32 (LBA)
/dev/sda6    *    146,800,767   147,210,366       409,600  83 Linux
/dev/sda7         147,210,368   246,728,830    99,518,463  8e Linux LVM
/dev/sda8         246,730,752   260,941,823    14,211,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d265d1ad-512a-4f0a-8f47-d13517036a52   ext4                                     
/dev/sda2        8850-CD70                              vfat       SERVICEV001                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        475E-BE3C                              vfat                                     
/dev/sda6        f6c4e336-be37-46bd-ab9a-e746d231ebb2   ext4                                     
/dev/sda7        lxaw0O-WYPj-b6bn-GbLd-0AYm-u3rE-GAZFGy LVM2_member                               
/dev/sda8        89bb3e07-c339-4203-b472-598d8e3bd945   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set d265d1ad-512a-4f0a-8f47-d13517036a52
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d265d1ad-512a-4f0a-8f47-d13517036a52
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
    search --no-floppy --fs-uuid --set d265d1ad-512a-4f0a-8f47-d13517036a52
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d265d1ad-512a-4f0a-8f47-d13517036a52 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d265d1ad-512a-4f0a-8f47-d13517036a52
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d265d1ad-512a-4f0a-8f47-d13517036a52 ro single 
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
    search --no-floppy --fs-uuid --set d265d1ad-512a-4f0a-8f47-d13517036a52
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d265d1ad-512a-4f0a-8f47-d13517036a52
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8850-cd70
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
# swap was on /dev/sda8 during installation
UUID=89bb3e07-c339-4203-b472-598d8e3bd945 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  53.8GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-22-generic
   6.5GB: boot/vmlinuz-2.6.35-22-generic
   1.1GB: initrd.img
   6.5GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\ 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\ = "PC-DOS" 

============================= sda6/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,5)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,5)
    kernel /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/VolGroup-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img
title Fedora (2.6.32.26-175.fc12.i686)
    root (hd0,5)
    kernel /vmlinuz-2.6.32.26-175.fc12.i686 ro root=/dev/mapper/VolGroup-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.32.26-175.fc12.i686.img
title Fedora (2.6.32.21-168.fc12.i686)
    root (hd0,5)
    kernel /vmlinuz-2.6.32.21-168.fc12.i686 ro root=/dev/mapper/VolGroup-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.32.21-168.fc12.i686.img
title Fedora (2.6.32.19-163.fc12.i686)
    root (hd0,5)
    kernel /vmlinuz-2.6.32.19-163.fc12.i686 ro root=/dev/mapper/VolGroup-lv_root noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.32.19-163.fc12.i686.img
title Other
    rootnoverify (hd0,0)
    chainloader +1

=================== sda6: Location of files loaded by Grub: ===================


  75.1GB: grub/grub.conf
  75.1GB: grub/menu.lst
  75.1GB: grub/stage2
  75.1GB: initramfs-2.6.32.19-163.fc12.i686.img
  75.2GB: initramfs-2.6.32.21-168.fc12.i686.img
  75.2GB: initramfs-2.6.32.26-175.fc12.i686.img
  75.2GB: initramfs-2.6.35.6-45.fc14.i686.img
  75.2GB: initrd-plymouth.img
  75.1GB: vmlinuz-2.6.32.19-163.fc12.i686
  75.2GB: vmlinuz-2.6.32.21-168.fc12.i686
  75.2GB: vmlinuz-2.6.32.26-175.fc12.i686
  75.2GB: vmlinuz-2.6.35.6-45.fc14.i686
```

---

### Post by Quackers on 2011-03-12
It appears that the only thing remaining of XP is on sda2, which is a partition labelled as Compaq diagnostics. The operating system field is empty.
I am wondering if your XP installation was on sda1, but has now been over-written by Ubuntu 10.10
Did you select the "install alongside" option in the installer?
The 10.10 installer has a nasty habit of over-writing existing installations. That may have happened here.

---

### Post by Hedgehog1 on 2011-03-12
I was waiting for Quackers to post first (*Quackers is a very smart person, even if his avatar is a bad tempered duck*), but I agree that Windows is not really on the disk as a viable OS anymore.

Both: **sda2** & **sda5** can be deleted.

I also believe **sda7** is an abandoned partition.

Leo, if you still have your windows install disks, you can install Virtual Box and run Windows as an application in Ubuntu.

***The Hedge***

:KS

---

### Post by Leo Rivers on 2011-03-12
Sigh...

I thought I was okay avoiding the 2 FAT partitions.

Well... if U 10 installed in Windows partition why does Windows show up as a choice when I hit ESCAPE during opening window and see grub?

And if ubuntu Linux is now in the Windows partition why isn't the old Fedora Linux a choice?

I am like that old man in Moonstruck "confused".
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Quackers on 2011-03-12
> **Leo Rivers said:**
> Sigh...

I thought I was okay avoiding the 2 FAT partitions.

Well... if U 10 installed in Windows partition why does Windows show up as a choice when I hit ESCAPE during opening window and see grub?

And if ubuntu Linux is now in the Windows partition why isn't the old Fedora Linux a choice?

I am like that old man in Moonstruck "confused".
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

You see the Windows entry in grub because XP-like boot files exist in the sda2 directory (maybe to boot a recovery system???)

The only operating system registered on your hard drive is Ubuntu 10.10, in sda1, as far as I can see. That would explain why Fedora doesn't have an entry in the grub menu. (unless there is an unclean file system involved).

From the Ubuntu desktop, have you run ```
sudo update-grub
``` since you installed?

---

### Post by Leo Rivers on 2011-03-12
No.

I will do so and repeat above instructions and post accordingly.

---

### Post by Leo Rivers on 2011-03-12
```
harald@harald-ThinkPad-T61:~$ sudo update-grub
[sudo] password for harald: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP on /dev/sda2
done
harald@harald-ThinkPad-T61:~$ 
```

---

### Post by Quackers on 2011-03-12
No other OS found in that output.
You seem to have copied the actual boot-info-script, rather than running it and quoting the output file, but it will be the same as earlier anyway.

---

### Post by Leo Rivers on 2011-03-12
Alright.

I guess I need to

#1  remove false entries (What do I need to keep ubuntu and swap and 20 Gig shared data partition?)

#2 Make a partition of free space for Windoze

#3 Install Windows into that space AND NOT F**K up and ruin Linux?


Some advice might be nice.

Virtualizing a Windows install like Parallels on a Mac would be GREAT, but how do I then rescue lost partition space?


Thanks for you excellent newbie assistance.

---

### Post by Hakunka-Matata on 2011-03-12
> **Leo Rivers said:**
> Alright.

I guess I need to

#1  remove false entries (What do I need to keep ubuntu and swap and 20 Gig shared data partition?)

#2 Make a partition of free space for Windoze

#3 Install Windows into that space AND NOT F**K up and ruin Linux?



Look at your disk using GParted "System > Administration > GParted", (not installed by default).  You can easily use that tool to accomplish #1 & #2 above if you choose.  You'd have to boot into the LiveCD to work on your hard disk, if you decide to do it that way.

---

### Post by Leo Rivers on 2011-03-12
I made that /dev/sda7 of 51 GB into a 32 Fat partition 

now it is mounted at  /media/129F-1FC2

so how can I trick a Windows installer to see and install into it AND LEAVE EVERYTHING ELSE ALONE!

And I guess grub will spot it, or do I need to edit that? and how?


Already all seems manageable.

Thanks again

---

### Post by Hakunka-Matata on 2011-03-12
Post a screenshot "Applications > Accessories > Take Screenshot" of a GParted gui of your disk partitioning first please.  Upload it with the paperclip icon.

---

### Post by Leo Rivers on 2011-03-12
As asked. (I really appreciate the effort folks)

PS: the sda5 20 GB is my shared Data drive. It's a keeper.


Leo

---

### Post by Hakunka-Matata on 2011-03-12
OK, and you want to install windows on sda7?

---

### Post by Leo Rivers on 2011-03-12
Yes,/dev/sda7/    /media/129F-1fc2    47.45 GB

I have no idea what /dev/sda2 of 5.57 GB is

my SHARED data partition is /dev/sda5 , Open Office in both Linux and Windows can share the same files.

---

### Post by Hakunka-Matata on 2011-03-12
[LIST]
[*]sda7 is a logical partition, that will not work for windows install.
[*]sda5, your shared partition, it's FAT32, NTFS would be better
[/LIST]

it can all be fixed with GParted,

You need to make a NTFS primary partition for the windows install, that's 
probably the first thing to do.

Thumbnail is of a XP_UB1010 dual boot drive, simple, as example only

---

### Post by srs5694 on 2011-03-12
Hakunka-Matata is correct that Windows must install to a primary partition, and that this fact makes /dev/sda7 a poor choice and /dev/sda2 a better choice. OTOH, /dev/sda7 is a bigger partition than /dev/sda2, and I'd be reluctant to recommend wiping it out if you don't know its purpose. (My suspicion is that it's a leftover partition from an earlier OEM install of Windows, and so it should be safe to remove it, but I'm not positive of that.) One possible way out of this dilemma is to use my new [FixParts](http://www.rodsbooks.com/fixparts/) program, which can convert primary partitions into logical partitions and vice-versa, within certain constraints. It's apparent from your layout that you could convert /dev/sda2 into a logical partition and then convert /dev/sda6 and /dev/sda7 into primary partitions. Such a conversion would be quicker and safer than resizing and moving partitions with GParted, which is the other option if you need ~45 GiB for Windows.

One caveat with this approach is that many of your important partition identifiers will change. This could render Linux unbootable until you adjust the /etc/fstab file and/or your GRUB configuration. OTOH, in theory it could still all work, since Ubuntu normally uses UUIDs for these features rather than partition numbers. Another caveat is that FixParts is new; it's conceivable you'll run into a bug that will cause further problems.

A Windows caveat is that the Windows installer, under certain circumstances, can delete partitions it's not asked to delete or convert logical partitions into primaries in a way that's illegal. Thus, I recommend setting up your partitions *before* launching the Windows installer, so that you can just click the target partition and tell Windows to install there, rather than add, delete, or otherwise manipulate partitions in the installer.

I don't see any way of making that disk suitable for Windows installation that doesn't involve some type of risk. Therefore, I strongly recommend that you back up your important data before you proceed. If this is impossible or inconvenient, then you need better backup hardware. Buy it and use it.

It's also unclear to me what purpose /dev/sda6 serves. It's only 200 MiB in size, which isn't big enough for much. It's big enough for a Linux /boot partition, but according to GParted, it's mounted at a mount point in /media named after its UUID value. That suggests it's not being used as a /boot partition, but I can't be 100% certain of that. It's could be it's a leftover /boot partition from a previous installation. If so, you could safely delete it. This wouldn't significantly alter any of your options, but if you convert partition types with FixParts, deleting this partition would free up one primary partition slot, which might be useful in the future.

Windows will ultimately want an NTFS partition, but IIRC, if you feed it  a disk with a FAT partition, it will enable you to install to the FAT  partition; it will just convert from FAT to NTFS by itself. Thus, you  should be able to leave it as FAT or convert it to NTFS using GParted,  with more-or-less identical results.

One more observation: Your /dev/sda7 partition currently has an "LVM flag" set. That's GParted's way of saying that it has a partition type code of 0x8E, which identifies Linux Logical Volume Manager (LVM) partitions. Having a FAT filesystem on such a partition is incorrect, and there's a good chance that the Windows installer will not detect it as-is, even if you convert it into a primary partition. You can correct the matter in several ways, such as by using fdisk to change the type code, using GParted to create a new filesystem on the partition, or using FixParts to change the type code while you juggle primary/logical partition assignments.

---

### Post by Leo Rivers on 2011-03-12
> Linux operating systems can be installed into (and run from) **logical** partitions, whereas Windows operating systems are restricted to primary partitions. *wiki*

Does the above quote from a wiki mean I have to _nuke_ my laptop into two partitions, both NTFS, install *Windows* into **the primary, (first) partition**

THEN BOOT  my *ubuntu  linux* disk to force a take over of the second and **extended** partition
'
and let _Grub_ run the show?

right? Wrong? Gory details?

---

### Post by Hakunka-Matata on 2011-03-12
No, you're fine.  You can rearrange/configure your drive to provide all the partitions necessary.

Figure out the plan first, then execute slowly, once.  No problem.  

srs5694 does make a good point about your sda5 Data partition.  Looks like you have about a Gig of data, would be smart to get that backed up somehow first.

---

### Post by Leo Rivers on 2011-03-12
Re-Partitioning went well, at least as far as I can tell.

BUT Windows installer still "can find no hard drive"


:lolflag:

---

### Post by Hakunka-Matata on 2011-03-12
There's no boot flag set on your windows partition, sda4, ntfs.  GParted, highlite sda4, then right button mouse, manage flags,  set boot flag.  That is what windows installer needs to see to find it's home

---

### Post by Leo Rivers on 2011-03-13
You would think that would work, but it didn't.

"No hard drive could be found..."

I am getting quite the education though.

Priceless.

---

### Post by Hakunka-Matata on 2011-03-13
> **Leo Rivers said:**
> You would think that would work, but it didn't.

"No hard drive could be found..."

I am getting quite the education though.

Priceless.

Yes, isn't it fun when so much gets demystified, I just love how Linux enables one to examine EVERYTHING.    A few more subtle things to consider now.  i.e. consider what other FMs **Quackers; Hedgehog1; srs5694;** who are good at this have pointed out.[LIST]
[*]it appears your swap is not turned on, (no key icon showing), GParted, highlight swap partition, right button, swapon
[*]Partition UUIDs have changed, post output of CODE: cat /etc/fstab
[*]post output of CODE: sudo blkid
[*]The windows partition is at the end of the disc, physically last I think, usually it's first, or near first. Is there a BIOS read limit of 137.5GB glitch? Rerun 'bootinfoscript' & post output
[*] #'bootinfoscript' showed sda7 FileSystem as "Linux LVM", want to see if there is any evidence now of LVM on disc
[*]post output of CODE: df-h 
[*]perform fsck on each partition that isn't mounted: GParted > highlight each partiton, Right Mouse button, select "CHECK" execute, repeat...
[/LIST]```
cat /etc/fstab
sudo blkid
sudo bash ~/Desktop/boot_info_script*.sh
df -h
```

There, that should keep you busy for a while, thanks for being easy to work with....

---

### Post by Hakunka-Matata on 2011-03-13
After doing everything so far lined out, if Windows installer still can't see it's partition, and If we understand the disc layout correctly, and you have your Data backed up to a USB stick or something, you could clean it up considerably from here.


[LIST]
[*]what's sda6 being used for?  I'm guessing nothing, that was a FEDORA partition, junk it
[*]sda5 is your Data partition, right?
[/LIST]

[LIST=1]
[*]delete sda6, sda7, sda4:
[*]make room immediately after sda1 for a primary ntfs windows partition
[*]make new logical swap partition in unallocated extended space: size = your Physical RAM
[*]then fix (again) /etc/fstab with all the new UUIDs
[*]Install Windows
[*]take a shower, go on vacation
[/LIST]

---

### Post by Leo Rivers on 2011-03-13
Ah,... the goal is in sight.

All 4 operations suggested are competed.
> ```
cat /etc/fstab
sudo blkid
sudo bash ~/Desktop/boot_info_script*.sh
df -h
```


These ought to provide the tools to re-compase fstab so everybody sees every body, even Windose Installers.

I will pursue [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and get back to you.

This has been fun. Fun and aspirin.

---

### Post by Hakunka-Matata on 2011-03-13
Hey, the partitioning looks nice.  OOPS, Swap should be in a logical partition, (within an Extended partition) Look at your Thumbnail in Post#24   You can just delete the swap, create the Extended, create swap within unallocated of Extended.

This paragraph now redundant after all the edits:  How much RAM does that machine have?  Adjust swap file size to equal RAM.  Highlight, right button, turn SWAPOFF, do the resize, SWAPON

are you going to post the output from the four commands?

---

### Post by srs5694 on 2011-03-13
There's no requirement that swap space be in a logical partition. The Ubuntu installer puts it in one by default, but that's just the default for the Ubuntu installer. That said, a disk with four primary partitions gives no room for expansion in the number of partitions on the disk, should that become desirable in the future. In fact, I'd argue that it's desirable now, in order to provide a data exchange partition between the two OSes. (It's unwise to give Linux write access to a Windows boot partition, so exchanging or sharing data is best accomplished via a separate non-boot NTFS partition.)

The heart of the current issue, though, is this:

[quote=Leo Rivers]BUT Windows installer still "can find no hard drive"[/quote]

This is a Windows issue at this point, so you might want to post about it on a Windows forum. Whether you pursue it here or elsewhere, though, it's critical that you understand and communicate clearly whether Windows can't find the *hard drive* or the *Windows partition*. If your motherboard is newer than the version of Windows you're installing, then Windows may lack drivers for your disk controller circuitry. This would result in Windows being unable to access your hard drive(s). The installer would show no partitions available at all, and it might complain that it could find no hard disks. (I don't know precisely what Windows reports in such situations.) If, OTOH, you've got suitable drivers, then Windows *should* show you your available partitions, even if they're Linux partitions. You might be unable to move beyond the partitioning screen because of various problems, but you should at least be able to see the hard disk.

It's unclear from your description which of these things is happening, although it sounds more like the former than the latter. Perhaps posting a screen shot or two would help. (Try using a digital camera to photograph the screen.)

---

### Post by Animal X on 2011-03-13
> **Leo Rivers said:**
> Alright.

I guess I need to


#3 Install Windows into that space AND NOT F**K up and ruin Linux?

Some advice might be nice.

Thanks for you excellent newbie assistance.



just a side-note: when you get your windoze installed successfully and booted into it, look up "EasyBCD", it will make it easier to get back to linux. in other words, if you install linux then windows, microsux will overwite the MBR, EasyBCD gies you acces to editing that from windows if repairing it from linux seems daunting.

---

### Post by Leo Rivers on 2011-03-14
I look forward to the time I need help with   EasyBCD :D

---

### Post by Leo Rivers on 2011-03-14
6.5GB: boot/grub/core.img
  54.0GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/initrd.img-2.6.35-27-generic
   6.5GB: boot/vmlinuz-2.6.35-22-generic
   6.5GB: boot/vmlinuz-2.6.35-27-generic
   1.4GB: initrd.img
   1.4GB: initrd.img.old
   6.5GB: vmlinuz
   6.5GB: vmlinuz.old

---

### Post by Hakunka-Matata on 2011-03-15
thanks for all the pictures-

Let's clear the slate, Where do you stand now?,

[LIST]
You are running on Ubuntu10.10, now, right?
[*]There is no Windows installation on the drive, right?
[*]You want to re-install Windows, right?
[*]If that's all true, 
[*]Can we have a new Thumbnail from GParted now?
[/LIST]


Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

> 
Partition Boot Start End Size Id System

/dev/sda1 63 146,800,703 146,800,641 83 Linux
/dev/sda2 257,105,920 312,580,095 55,474,176 b W95 FAT32
/dev/sda3 * 146,802,688 244,830,207 98,027,520 7 HPFS/NTFS
/dev/sda4 244,830,600 257,104,259 12,273,660 82 Linux swap / Solaris


             [ATTACH]186139[/ATTACH]

sda1, system 
what's with sda2 FAT32?, what's it for?
sda3 would be where you want to install Windows, right?
sda4 is a massive swap, sda4 partition should be deleted (and recreated) or resized.  I don't know how to tell if it's a Primary partition, or a logical in an extended?

---

### Post by Leo Rivers on 2011-03-15
> sda1, system 
what's with sda2 FAT32?, what's it for?

It is my 20+ Gig shared DATA hard drive. The idea is that Bothe Windows and Linux can see it and use the same files.

> sda3 would be where you want to install Windows, right?yes

> sda4 is a massive swap, sda4 partition should be deleted (and recreated)  or resized.  I don't know how to tell if it's a Primary partition, or a  logical in an extended?How big should SWAP be?  I think it is a primary partition

PS:

Was I correct about re-writing* fstab*?

---

### Post by Hakunka-Matata on 2011-03-15
I'm not certain at this point whether you have to rewrite /etc/fstab, or whether a sudo update-grub will rewrite it for you?  anyway, if it's got a problem, it'll be apparent.  I wouldn't worry about it at this point.  
Although sda4 should normally be deleted and an Extended partition created in it's place, there is so little room left on this drive (because of huge (**oops, MY MISTAKE, only 1GB)** sda2 Data) I guess it really doesn't make much difference now.  Swap needs to be equal size to your RAM size if you Hibernate the machine, but otherwise it can be smaller.  4GB RAM, 2GB swap, for example.

What's next?, are you going to install WindowsXP? 7?

PS, I just looked quickly at etc/fstab, I think it's ok

You could/should turn on swap, in your GParted Thumbnail, it does not have the key-icon showing, right button on the partition, and select 'SWAP ON'

---

### Post by Leo Rivers on 2011-03-15
Why doesn't Windows NT install disc SEE sda3?

It says> I can't find a hard drive, press F3 to shut downEven if it didn't want to install into the ntfs primary partition at sda3, shouldn't it offer to nuke the hard drive at least?

I am completely happy with ubuntu and am thinking seriously of asking help with a choice of emulators and how to go about that.

The trouble is I need TibetDoc an word proceesing program designed for Tibetan Type an and Text lay out and am ignorant of how ubuntu will handle the special fonts.:o



[IMG]http://www.tibet.dk/tcc/images/tibwin2.gif[/IMG]

[http://www.tibet.dk/tcc/tdoca.htm](http://www.tibet.dk/tcc/tdoca.htm)

> Overview 
   TibetDoc is a word-processor for Windows.  It is one of a pair of the first programs written from the ground up for Windows that support Tibetan script.  The other program is [TibetD]("http://www.tibet.dk/tcc/tibetda.htm").  TibetDoc is derived from TibetD and hence has features very similar to it.  However, some things have been modified or added to make it more suited to word-processing.      TibetDoc creates word-processing documents in its own file format which was made specially for the purpose.  However, TibetDoc files can also be saved in a variety of other formats including RTF, HTML, and WordPerfect (DOS and Windows).  Especially though, TibetDoc like TibetD can save files in a special protected format that was designed for archiving and disseminating important materials like Tibetan Buddhist texts. 
     TibetDoc was built for Tibetan language purposes.  It has the highest level of support for Tibetan of any software available.  It has excellent support for many other languages, including English, all European languages, and and others.  It also has a complete system for working with Sanskrit diacriticals (fonts included, too). 


---

### Post by Hakunka-Matata on 2011-03-15
say again, what windows version are you trying to install?  

And excuse me, I've asked for so many pictures already, but please send a thumbnail of drive partitioning from GParted again, now.  OK

thanks

---

### Post by Hakunka-Matata on 2011-03-15
Easy to understand your wanting to get to work, and be finished with all these changes and time you've put in to date on your machine/disc.  But stick with it just a little longer and you'll be up and running.  It's highly likely that you'll find applications for Ubuntu that can do everything you want to do with your Tibetan work.  You have gotten your disc partitioned and cleaned up, I'll be requesting some other forum members to jump in here and help get windows installer to recognize the drive very soon if we don't succeed in the very near future.  I did not want to do that until you got your hard drive partitioning fixed up though, because it's valuable experience and VERY useful for the future.  You've done that now, so..........

---

### Post by Hakunka-Matata on 2011-03-15
[https://collab.itc.virginia.edu/access/wiki/site/26a34146-33a6-48ce-001e-f16ce7908a6a/using%20tibetan%20in%20linux.html]("https://collab.itc.virginia.edu/access/wiki/site/26a34146-33a6-48ce-001e-f16ce7908a6a/using%20tibetan%20in%20linux.html")

For starters..........

---

### Post by oldfred on 2011-03-15
Windows normally installs to a NTFS partition with the boot flag. Users have installed XP and others that way. Your sda3 looks correct and I would expect a windows installer to see it. But windows does not see Linux partitions, so it may be confused.

Perhaps that the boot sector is Vista/7 it is too advanced for an older system? Perhaps a repair from your windows system to sda3 then the installer may see it? Not sure.

---

### Post by srs5694 on 2011-03-15
> **Leo Rivers said:**
> Why doesn't Windows NT install disc SEE sda3?

It says

> I can't find a hard drive, press F3 to shut down

Even if it didn't want to install into the ntfs primary partition at sda3, shouldn't it offer to nuke the hard drive at least?

Yes. Please review [my last post.](http://ubuntuforums.org/showpost.php?p=10555841&postcount=29) Although it's conceivable that Windows is confused by something about the partitions, I think that's unlikely. I think it's much more likely that Windows needs *drivers* for your hard disk controller. Try checking with your computer or motherboard manufacturer.

Also, you mentioned *Windows NT*. If you're really trying to install something so ancient, it's possible it doesn't have drivers for modern hardware. If that's the case, you may need to upgrade to a more modern version of Windows or run it in a virtual machine.

My advice: Don't bother posting more screen shots or diagnostic scripts; instead, post details of your hardware (motherboard model, or any add-in disk controller card you're using) and Windows version. You're better off posting this to a Windows forum, as well.

---

### Post by oldfred on 2011-03-15
I think srs5694 is correct and/or BIOS settings.

I installed a new motherboard and Ubuntu worked just fine, as did window. I then enabled AHCI in BIOS since it was a new setting & supposedly a little better. Ubuntu still booted but XP would not boot at all. I never have gone back to install hte drivers as I am now using XP so little and hope to have it gone soon.

---

### Post by Hakunka-Matata on 2011-03-15
Yes, I don't know how OPs BIOS is set 'AHCI'

The  current HPFS/NTFS-sda3 was formatted Linux & Linux LVM previously.  If there is residual code there, could that be influencing the picture?
I don't think the OP has run fsck on the partition or any other 'cleaning' tools.  yet.  


> Drive: sda ___________________ **ORIGINAL Post #3**_____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   146,800,703   146,800,641  83 Linux
/dev/sda2         300,903,120   312,575,759    11,672,640  12 Compaq diagnostics
/dev/sda3         146,800,765   300,897,449   154,096,685   5 Extended
/dev/sda5         260,943,858   300,897,449    39,953,592   c W95 FAT32 (LBA)
[COLOR="Magenta"]/dev/sda6    *    146,800,767   147,210,366       409,600  83 Linux
/dev/sda7         147,210,368   246,728,830    99,518,463  8e Linux LVM[/COLOR]
/dev/sda8         246,730,752   260,941,823    14,211,072  82 Linux swap / 
Solaris



> Drive: sda ___________________ **Current from Post #32 **__________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 63 146,800,703 146,800,641 83 Linux
/dev/sda2 257,105,920 312,580,095 55,474,176 b W95 FAT32
[COLOR="Magenta"]/dev/sda3 * 146,802,688 244,830,207[/COLOR] 98,027,520 7 HPFS/NTFS
/dev/sda4 244,830,600 257,104,259 12,273,660 82 Linux swap / Solaris



---

### Post by Leo Rivers on 2011-03-15
I mis-spoke. I am trying to install [COLOR="DarkRed"]Windows xp[/COLOR] [COLOR="Red"]Professional[/COLOR].

I thank everyone for teaching me the Introductory course.

Even though my problem is still a boil on my **** I going to purchase a 30 lb tome on Ubuntu and try to reason with chaos.):P



I apologize.

---

### Post by Hakunka-Matata on 2011-03-15
Is your hard drive SATA or PATA/IDE?
Look in BIOS for what options are available for the drive controller, AHCI, Large, etc. try different ones.
With GParted, run a CHECK on the drive, select partition, right button, check, maybe add lba flag

oldfred and srs5694 are very good help.

---

### Post by srs5694 on 2011-03-15
> **oldfred said:**
> I think srs5694 is correct and/or BIOS settings.

I installed a new motherboard and Ubuntu worked just fine, as did window. I then enabled AHCI in BIOS since it was a new setting & supposedly a little better. Ubuntu still booted but XP would not boot at all.

I'd forgotten about BIOS settings, but you're right: They are another possibility. My understanding is that Windows is usually fine with either AHCI or non-AHCI settings, but once you install it one way you shouldn't muck with the settings. Still, I seem to recall hearing of cases where Windows is OK with one setting but not with another. Thus, it's worth checking that detail, as well as look for new drivers.

[quote=Leo Rivers]I mis-spoke. I am trying to install [COLOR=DarkRed]Windows xp[/COLOR] [COLOR=Red]Professional[/COLOR].[/quote]

According to Wikipedia, Windows XP was released in October of 2001, almost ten years ago. No doubt there have been updated installation CDs/DVDs over the years, but I don't know details about that. Nonetheless, unless the computer is truly ancient, it's entirely probable that the installation CD/DVD lacks drivers for the motherboard's ATA controller, particularly if it's an original 2001-era disc. In that case, switching the AHCI mode or downloading drivers (if available) from the motherboard or chipset manufacturer's Web site makes sense. There's a prompt at some point to enable you to install such drivers, but they'll need to be on a floppy disk or some other type of media that Windows can read at that point. I'm not sure if the XP installer could read a USB flash drive. If nothing else, you could try a CD-R.

Unless you need to give Windows direct hardware access (say, to handle a scanner or to run games that use graphics card acceleration features), it might make sense to run it under VirtualBox. VirtualBox emulates hardware that's old enough that Windows XP has no problems installing in it. That'll also eliminate a lot of areas that can be problems in a dual-boot configuration.

---

### Post by Leo Rivers on 2011-03-15
This is all starting to make a scary kind of sense. My computer really is about five years old. So is of course the DVD that went with it.

**It was a great learning experience though**

I may just have to buy a new copy of XP somewhere. Sigh. 

Believe me if it wasn't for two programs, (TibetDoc and iTunes for iPhone linkage),  I would easily be happy with Ubuntu Linux, because I've already lived in the Mozilla Thunderbird and Firefox and OpenOffice, (Neo office), in both Windows and Apple Macintosh as well as Linux In one form or another for the last 10 years.

It was when Ellen Hitchcock quit Apple and their operating system 8, Copeland, collapsed that I started looking for Linux on the PowerPC, and yellow dog Linux. In those days we didn't even have ppp. But I was trying to get ready because like hell was I ever going to be a slave of Redmond. But the truth is, even now with the iPhone which I love and can do voice to text dictation on, Cupertino is starting to feel a lot Redemond.:lolflag:

---

### Post by Hakunka-Matata on 2011-03-15
I have 1 year old ASUS motherboards with AMD Phenom CPUs that install WindowsXP Professional fine, with no extra drivers, so I hope your machine would be able to do that too.  Are you going to try to clean sda3 somehow, with "dmraid -r -E /dev/sda3" tool or write zeros with dd command?  This computer has WindowsXP Prof on it, and I just tried what oldfred did with AHCI, with SATA controller set to AHCI, windows boots - gets to the start-up screen, with the blue bars running left to right maybe 2.5 times before it blinks and reboots the machine.  Setting the BIOS back to SATA, it works fine.

---

### Post by Leo Rivers on 2011-03-16
I am going to break down everything you have said and learn about each part and then decide what to do.

I am doing that with all the responses in this thread. I figure in a week I will have an idea of my next move. 

It's turning into fun now I've let go of emergency mode.:popcorn:



> **Hakunka-Matata said:**
> I have 1 year old ASUS motherboards with AMD Phenom CPUs that install WindowsXP Professional fine, with no extra drivers, so I hope your machine would be able to do that too.  Are you going to try to clean sda3 somehow, with "dmraid -r -E /dev/sda3" tool or write zeros with dd command?  This computer has WindowsXP Prof on it, and I just tried what oldfred did with AHCI, with SATA controller set to AHCI, windows boots - gets to the start-up screen, with the blue bars running left to right maybe 2.5 times before it blinks and reboots the machine.  Setting the BIOS back to SATA, it works fine.

---

### Post by kagerato on 2011-03-16
What oldfred said is quite important. Stock XP (whether the installer or the installed system) will typically not run correctly for systems running hard disks in AHCI mode.  It almost never has the correct driver for this.  XP even lacks the storage controller drivers to properly detect the disks in some SATA systems (mine is one of them).

The only "easy" solution is to configure the BIOS to use 'basic' SATA mode.  Then, if that doesn't work, PATA emulation mode.  Personally, I find running a modern system in archaic Parallel ATA mode to be unacceptable.

Vista and 7 don't have this issue, if you can stomach their extreme bloat compared to XP.

---

### Post by jerome1232 on 2011-03-16
> **kagerato said:**
> What oldfred said is quite important. Stock XP (whether the installer or the installed system) will typically not run correctly for systems running hard disks in AHCI mode.  It almost never has the correct driver for this.  XP even lacks the storage controller drivers to properly detect the disks in some SATA systems (mine is one of them).

The only "easy" solution is to configure the BIOS to use 'basic' SATA mode.  Then, if that doesn't work, PATA emulation mode.  Personally, I find running a modern system in archaic Parallel ATA mode to be unacceptable.

Vista and 7 don't have this issue, if you can stomach their extreme bloat compared to XP.

I wanted to re emphasize this post, when XP came out SATA was new, and drivers weren't all there yet. I've had a few problems in the past with XP and SATA drives, if your bios doesn't allow you to switch the mode of the disk to pata emulation, then the only solution I found then was to obtain the drivers online and put them on a floppy disk and insert it when XP asks if you have additional drivers, or use a program called nlite (if I recall correctly) to create your own XP installation disk with the drivers included.

---

### Post by Hakunka-Matata on 2011-03-16
> It's turning into fun now I've let go of emergency mode.

Letting go of emergency mode is invaluable, good stuff.

Leo, Thanks for apprising of your plan, and I applaud your attitude towards getting your installation all sorted.  Unix - Linux - Ubuntu, and this forum are & have been a real joy for me over the last several years.  Working with people with your attitude are part of the joy, having fun is a big part also.  I'm confident you will find a way through to success and enjoy hassle free computing for years to come.

---

### Post by Hakunka-Matata on 2011-03-16
> 
post #61 [http://ubuntuforums.org/showthread.php?t=1689533]("http://ubuntuforums.org/showthread.php?t=1689533")
We have had a lot of users who for whatever reason have RAID metadata on their drive which then causes the liveCd to not work as it does not include the RAID drivers. The alternate installer often then works since it has the extra drivers.

IF you have the liveCD working, you need to do a full standared install from that, then if you have problems post a new copy of the boot info script as that gives us many clues about why things are not working.

The other issue many are having including me, is video issues. If only one system it may seem like a boot issue, but it has booted and then found video issue and stopped. I have to add a nomodeset parameter to get it to boot. LiveCD works (now) older versions need parameter even for liveCD. But first boot needs special settings.
__________________
Let us know what works and to mark your thread as [SOLVED], use Thread Tools on forum page.
Howto: [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads](https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads)

Leo:  Although the quoted post does not directly relate to your WindowsXP-Prof installer's inability to recognize the ntfs partition you've prepared for it, it does deal with that type of issue.  It lends further credence to me at least that there may be something written in those sectors of your drive that is upsetting the windows installer, and is not revealed via the few tools you've used (to date) to examine the problem.  When a problem such as this presents, the more difficult the problem to solve, the more important it becomes to solve it, because of the potential knowledge to be gained.  I hope you pursue resolution of this problem, using some of the available tools that have not yet been employed.

---

### Post by glene77is on 2011-05-21
*(:  Ubuntu_forums_110521.txt

[http://ubuntuforums.org/newreply.php?do=newreply&p=10566156](http://ubuntuforums.org/newreply.php?do=newreply&p=10566156)

> **Hakunka-Matata said:**
> Leo:  Although the quoted post does not directly relate to your WindowsXP-Prof installer's inability to recognize the ntfs partition you've prepared for it, it does deal with that type of issue.  It lends further credence to me at least that there may be something written in those sectors of your drive that is upsetting the windows installer, and is not revealed via the few tools you've used (to date) to examine the problem.  When a problem such as this presents, the more difficult the problem to solve, the more important it becomes to solve it, because of the potential knowledge to be gained.  I hope you pursue resolution of this problem, using some of the available tools that have not yet been employed.

[COLOR=Red]Leo ![/COLOR]  Where did you go ? 
quote/    It's turning into fun now I've let go of emergency mode.:popcorn:   /quote
[COLOR=Red]Leo ?  Hope you read this, and simply do what I did.  
 "START OVER".   
 Don't give up on Linux !  
 Ubuntu is the best thing since Jason invented sliced bread. 
[/COLOR] 

[COLOR=Red]
Hakunka, [/COLOR]
I checked into this thread late, about two months late !
[COLOR=RoyalBlue]You better run XP Installer FIRST, and the reasons are below. [/COLOR]

[COLOR=SeaGreen]Always, 
I welcome the technical and intelligent  ( sometimes too terse ) replies 
from members of this forum.   
[/COLOR] 
For my part, 
(1) I do have a "sand-box" computer (Dell, 512 MB RAM, 320 GB HD Pata).   
There have been as many as 12 different OS installed, all being directed  by Grub4Dos, using a dedicated sda1 primary partition.   
(2) I do have a HP-1G RAM-40GB HD, along-side of Parted-Magic and Ubuntu 10.04, (upgraded to 10.10).    There are XP & Ubuntu & Parted-Magic installed on the HP, and it is used for business.
(3) There are several 250+ GB USB external HD for backup. 
(4) I share the USB external HD via a multi-switcher, and use a KVM  switcher for I/O switching. 

That said,  (follow along with me, please) 
(1) there is no good reason that I would **accidently** allow ** uBootMgr** (with syslinux)  
to boot  off a USB flash drive  and then try to use the syslinux menu on my business HD.  
(2) But, ** I did,**  
and it promptly[COLOR=SeaGreen]** wiped out the partition address section of the MBR**[/COLOR],  leaving the Grub2 intact.   :(

Now, 
The Live-CD for Parted-Magic provided some interesting (wierd) info  about GRUB2 still being there, and the squirrely addresses, which were  obviously garbage, since they were on top and overlapping each other.  :(

So, the [COLOR=Red]**GOOD NEWS **[/COLOR]
for Leo, and perhaps the rest of the guys who were so helpful follows:  :D

[SIZE=2][COLOR=RoyalBlue]I have re-installed XP Pro five times on my HP, alongside Ubuntu and Parted-Magic[/COLOR].[/SIZE]    
In my careless tinkering, I have 
(1) wiped out the MBR totally, 
(2) wiped out the Grub2, 
(3) wiped out the partition table (last 32 bytes of MBR space) which made the whole HD vanish.  
(4) become thankful for back-up files. 

I want to relate to you guys just exactly what the [COLOR=Red][SIZE=3]XP installer[/SIZE] [/COLOR]put on my screen 
FOUR times during each of the FIVE re-installs I have done.   
I am making no mistaking is issue, and you should check it out, telling me if I am mistaken.
[COLOR=Red][SIZE=3]The XP installer clearly warned me that : 
(1) it requires the _entire_ Hard Drive, 
(2) it will wipe out _all_ Partition Info, 
(3)_ clearing_ the ENTIRE hard drive.   [/SIZE]
[COLOR=Black]
[SIZE=2]I checked after the XP install,  booting the[/SIZE][SIZE=2][COLOR=RoyalBlue]Parted-Magic Live-CD to RAM,[/COLOR][/SIZE] [SIZE=2]
and [/SIZE][SIZE=2][COLOR=RoyalBlue]it clearly showed an XP-PRO install that used the ENTIRE hard drive[/COLOR][/SIZE][SIZE=2]. 
[/SIZE][/COLOR] [/COLOR]
For my own needs, I promtly used Parted-Magic Live-CD to :
(1) shrink the XP sda1 primary partition down to 10GB, 
(2) create an Extended partition, for two more logical partitions for:  (a) Ubuntu Sys  (b) Data. 
(3) create a primary partition of  < 1 GB for the small Swap.  

[SIZE=2][COLOR=SeaGreen]That means that 
IF any of your fixes worked, 
THEN the XP installer would WIPE OUT all the clean-up work you all did. 

[/COLOR][/SIZE]
**********************************************************************************************************************
This has been a great thread, and while I was anticipating Leo's use of the XP installer in due time, 
I was being pulled along ([COLOR=SeaGreen]just like in a mystery novel[/COLOR])  with great apprehension 
because I have seen the XP installer 'clear out' disks prior to use. 
I was very disappointed when Leo did not respond again.  The little novelette did not play out well.  

This was really educational to me.  
I also read that M$ requires  sda1  as a  primary partition  for any M$ OS install. 
I suppose that M$  believes in itself, and only itself.  
I think that Linux has been written with the capability of installing "BESIDE" any other OS. 
With Ubuntu's (paid) engineering staff pushing a great "desk-top" OS, 
Linux has a virtual foot-in-the-door of every corporation in the world !

My many Grub2 installs pick up every OS [COLOR=SeaGreen]except[/COLOR] :
(1)[COLOR=SeaGreen] Puppy Linux[/COLOR], with the SQFS (Squash File System) 
   (a)  SQF methods are like a "zip" file, and the vmlinux and initrd are not exposed to grub. 
   (b)  SQF technology is really interesting and hack-proof.  
(2)[COLOR=SeaGreen] Parted-Magic[/COLOR],  
   (a) which is copied from the Live-CD into C:\pmagic  subdir, 
   (b) then hand-coded into grub.cfg.   

On my "sand-box" computer,  an 'aside' thought, 
I installed Grub4Dos, in a dedicated sda1 primary partition, 
and make use of  the regular   menu.lst   method.   Has controlled 12 OS on one HD. 

Again, 
I welcome the technical and intelligent  ( sometimes too terse ) replies 
from members of this forum.   

[COLOR=Red]Leo ?  Hope you read this, and simply do what I did.  
"START OVER".   
Don't give up on Linux !  
Ubuntu is the best thing since Jason invented sliced bread. 
[/COLOR] 
Buena suerta,    ---{^,^}---  glene77is, Memphis, TN, USA.

---

### Post by Leo Rivers on 2011-05-21
Greetings;

What I ended up doing was

Part A

1.    Booted Ubuntu Live DVD

2.    Reformatted my laptop with a Windows partition in the first position

3.    Made a subsequent Swap partition and then

4.    Made a LOGICAL partition for a Linux partition to nest in

5.    and lastly a Data partition for files (I use Open Office and Mozilla and Gimp on both OS "sides")

Part B

1.    I installed Windows in 1st partition at front of cylinder

2.    I booted from Live DVD and installed Linux in the LOGICAL partition 

Part C

3.    - this REMADE GRUB so at boot I can choose between Ubuntu or Windows xp

EASY ):P

It was pointed out my attempts to help were very unhelpful. My medicine is another's poison.

---

### Post by glene77is on 2011-05-21
> **Leo Rivers said:**
> Greetings;
What I ended up doing was
Part A
1.    Booted Ubuntu Live DVD
2.    Reformatted my laptop with a Windows partition in the first position
3.    Made a subsequent Swap partition and then
4.    Made a LOGICAL partition for a Linux partition to nest in
5.    and lastly a Data partition for files (I use Open Office and Mozilla and Gimp on both OS "sides")
Part B
1.    I installed Windows in 1st partition at front of cylinder
2.    I booted from Live DVD and installed Linux in the LOGICAL partition 
Part C
3.    - this REMADE GRUB so at boot I can choose between Ubuntu or Windows xp
EASY ):P
It was pointed out my attempts to help were very unhelpful. My medicine is another's poison.

Leo,

Great news, and a good way to end a little mystery novelette ! :)
I use Libre(Open)Office, FireFox, GIMP,  Audacity as main applications.
Flipping between computers is much simpler that way.   :)

At the Univ. of TN, Memphis, TN, we did research into designing analog IC circuits, computer interfacing, with the application being a population of 956 cerebral palsy/MS/AS clients.  
In 1980 I used a AIM-65, from Rockwell, 6502 micro, 4 KB RAM, built-in assembler ROM, and cassette drives. I wrote a variant of the Word Star word processing program, in 6502 assembler code, to use on this special "industrial controller computer".  
Then, at the University, we used an Altair 8000, using 8080 micro, and dual 8" floppy drives.  ( 5 MB HD was $1200). 
Then,  we progressed to  half-dozen Apple II, with the 6502 micro, and 64 MB RAM, two 5 1/4" floppies. 
I remember using the CP/M OS on a Z-80 card, plugged into my Apple II, with 64 KB Ram, 6502 microprocesser.   For work I used old Word Star and dBASE.  Wrote in 6502, 6803, 8080 machine (hex) and assemblers.  
Now, I use Libre, FireFox, GIMP, Audacity applications., 

[COLOR=Red]Ubuntu[/COLOR] is simply the best desk-top OS around.  [COLOR=SeaGreen]Excellent support, leading edge[/COLOR]. 
It is a RAM hog, and requires more OS HD space, but it does everything. 

[COLOR=Red]Puppy[/COLOR] is simply the best Live-CD OS around.    I combine it with XP and Ubuntu, and neither one knows that Puppy ever runs in the midst.  Can run in 128 MegBytes of RAM.  
Can download huge applications (such as the ones we use) 
and leave Squash files on the HD,   [COLOR=SeaGreen]never touching the XP or Ubuntu OS ![/COLOR] 

What you wrote fits into my model.  Glad it works.  
Hope it proves productive.  

[SIZE=3][COLOR=Red]So, WELCOME to the forums,   check in again,  anytime ![/COLOR][/SIZE]

(always check in and list the final results, 
(1) as a "Thank you"
(2) and so this thread can be marked "Solved".

---

### Post by srs5694 on 2011-05-22
> **glene77is said:**
> I am making no mistaking is issue, and you should check it out, telling me if I am mistaken.
[COLOR=Red][SIZE=3]The XP installer clearly warned me that : 
(1) it requires the _entire_ Hard Drive, 
(2) it will wipe out _all_ Partition Info, 
(3)_ clearing_ the ENTIRE hard drive.[/SIZE][COLOR=Black][SIZE=2]

I'm not sure what the case was with XP, but some OEM versions of the Windows Vista and 7 installers behave this way. OTOH, my retail (upgrade) copy of XP does *not* have *any* of those restrictions. I've re-installed it several times, and it's never insisted on taking over the entire hard disk. There may have been an *option* to do so (I don't remember that detail), but I'm quite certain I've installed it alongside other OSes without running into problems.

That said, what every Microsoft install I've ever made on a BIOS-based computer has done is to wipe the boot loader code from the MBR. This can be an annoyance if you had GRUB or some other multi-OS boot loader set up there, since it renders your non-Microsoft OSes unbootable until you re-install your original boot loader. It doesn't destroy those installations, though.

[/SIZE][/COLOR][/COLOR][SIZE=2][COLOR=SeaGreen][/COLOR][/SIZE]> I also read that M$ requires  sda1  as a  primary partition  for any M$ OS install.

I've read this many times, too. I must be doing something wrong, since I've installed Windows on other partitions many times. ;) In fact, I've installed different versions of Windows side-by-side on the same computer and disk (although I don't happen to have such an installation right this moment).

What Windows *does* require (on an MBR disk) is a primary partition. Normally this will be the main OS installation partition, but it's possible to install most of Windows in a logical partition and use a primary just for a few critical files. I've never tried to set it up this way, though, and I don't recall what sort of hoops you've got to jump through to do it.

---

### Post by glene77is on 2011-05-22
> **srs5694 said:**
> 
I'm not sure what the case was with XP, but some OEM versions of the Windows Vista and 7 installers behave this way. OTOH, my retail (upgrade) copy of XP does *not* have *any* of those restrictions. I've re-installed it several times, and it's never insisted on taking over the entire hard disk. There may have been an *option* to do so (I don't remember that detail), but I'm quite certain I've installed it alongside other OSes without running into problems.

That said, what every Microsoft install I've ever made on a BIOS-based computer has done is to wipe the boot loader code from the MBR. This can be an annoyance if you had GRUB or some other multi-OS boot loader set up there, since it renders your non-Microsoft OSes unbootable until you re-install your original boot loader. It doesn't destroy those installations, though.

[/SIZE][/COLOR][/COLOR]

I've read this many times, too. I must be doing something wrong, since I've installed Windows on other partitions many times. ;) In fact, I've installed different versions of Windows side-by-side on the same computer and disk (although I don't happen to have such an installation right this moment).

What Windows *does* require (on an MBR disk) is a primary partition. Normally this will be the main OS installation partition, but it's possible to install most of Windows in a logical partition and use a primary just for a few critical files. I've never tried to set it up this way, though, and I don't recall what sort of hoops you've got to jump through to do it.


[SIZE=2][COLOR=Red]SRS,[/COLOR][/SIZE]

Always,  thanks for responding.   :P
I basically agree on each point of your re-post. 
 It is a big world, and I learn something from every re-post. 

[COLOR=Red]**Really happy to see that Leo has his system up-and-running.  **[/COLOR]

I will be reading your narrative again, 
and adding it to the every widening scope of my studies. 


glene77is

---

### Post by glene77is on 2011-05-22
> **Hakunka-Matata said:**
> Leo:  Although the quoted post does not directly relate to your WindowsXP-Prof installer's inability to recognize the ntfs partition you've prepared for it, it does deal with that type of issue.  It lends further credence to me at least that there may be something written in those sectors of your drive that is upsetting the windows installer, and is not revealed via the few tools you've used (to date) to examine the problem.  When a problem such as this presents, the more difficult the problem to solve, the more important it becomes to solve it, because of the potential knowledge to be gained.  I hope you pursue resolution of this problem, using some of the available tools that have not yet been employed.

Hakunka,
Thanks for responding to Leo.   :)
Your posts were good, intelligent reading. 

glene77is

---

### Post by Leo Rivers on 2011-06-15
Ever one to take a hint as a command...

... I now have a thumbdrive case on a chain around my neck. It has pockets for 2 thumb drives.

_In one I have my Core DATA_[IMG]http://i36.photobucket.com/albums/e33/UncleRando/WashingtonDC/th_NationalArchives1.jpg[/IMG]

in the other I have** Lucent Puppy!**[IMG]http://puppylinux.com/puppylogo96.png[/IMG]


I am a nomad now. Got all I need to go.:popcorn:

---

