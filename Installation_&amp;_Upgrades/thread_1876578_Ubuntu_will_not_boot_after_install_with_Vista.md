---
title: "Ubuntu will not boot after install with Vista"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by gwatts on 2011-11-06
Ubuntu will not boot after installing with Windows Vista. Vista starts.

Installed Ubuntu 11 10 to dual-boot with Vista and using Easy BCD.

View Settings >:

Vista > C:\boot loader path: \Windows\system32\winload.exe

Linux > C:\boot loader path: \NST\AutoNeoGrub0.mbr

Is this correct?  I can boot Windows Vista but not Ubuntu.

---

### Post by darkod on 2011-11-06
And why don't you just use grub bootloader? It can boot both ubuntu and windows, just what you need.

---

### Post by gwatts on 2011-11-06
darkod

Thank you. Can you  tell me more as to how?  I have  made at least 6 installation and used almost every combination of selections in BCD and each time I have to repair Windows to boot anything.

---

### Post by darkod on 2011-11-06
1. Don't use BCD. I am not sure if you can simply remove it and whether that will return your original windows bootloader configuration. Don'y worry if the computer boots vista directly and doesn't show option for ubuntu, that is easy to fix.

First remove BCD and all entries it has made.

2. When you have achieved that vista boots directly, reboot the computer with the ubuntu cd in live mode (try ubuntu mode), open terminal and execute:

sudo fdisk -l (that's small L, not 1)

That will show you the partitions on the disk. You will have two linux partitions, the root and swap (unless you manually created more). Most probably root is /dev/sda5, it's the bigger partition. If it's not sda5 change the number as needed. To install grub to the MBR of your disk, execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That should install grub to your disk /dev/sda and it will offer option to boot both ubuntu and windows.

If you have any questions just ask.

---

### Post by gwatts on 2011-11-06
darkod
I really appreciate your prompt response.

I selected sda2 (I could not tell which partition is which) but after the first command it said to specify the filesystem type. ??

So I redid the commands selecting sda5 and multiple errors occurred. I had to  power down with pages of errors and Vista came up with no boot selections.

I have 2 Vista partition  plus 1 16Gb plus 1 or more 4GB swaps (seemed like it created another 
swap on 1-2 Ubuntu installs of Ubuntu).

Next?
 Next?

---

### Post by darkod on 2011-11-06
Looks like it's the 16GB partition. You can also post the results of:

sudo fdisk -l

here and it should show more info.

---

### Post by gwatts on 2011-11-06
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000694ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    87891614    43945776    7  HPFS/NTFS/exFAT
/dev/sda2        87891966   128680649    20394342    f  W95 Ext'd (LBA)
/dev/sda3       128680653   234441646    52880497    7  HPFS/NTFS/exFAT
/dev/sda5        87891968   120291327    16199680    7  HPFS/NTFS/exFAT
/dev/sda6       120294783   128680649     4192933+  82  Linux swap / Solaris

---

### Post by darkod on 2011-11-06
As you can see yourself you have no Linux partition on the disk. Just a swap partition. The rest are all ntfs partitions.

Is it possible that the root partition was deleted while installing vista?
Did you have a dual boot before that or just ubuntu?

---

### Post by gwatts on 2011-11-06
Yes re /.

I have tried  at times to create ext3 and 4.

Always Vista, tried off and on over several years to install Ub but never could get it to boot.

Used several partition managers over the years.

---

### Post by darkod on 2011-11-06
I can't see why it wouldn't work. Here is a suggestion:

1. Move all the data from partition sda5 to the other partitions or an external disk. You can then use tat partition as /.
2. Boot with ubuntu cd and select Install.
3. In the partitioning step select Manual (Custom) to set your own partitions (they already exist).
4. When the list of partitions on the disk appears, click once to select sda5. Under the list click on the button Change...
5. In the windows that opens, change the field "do not use" to "ext4".
6. Set the mount point as /
7. Tick the Format box to tell the installer to format it.
8. Close that window. You do not need to do anything about the swap partition (sda6), ubuntu can see it and will use it as swap.
9. Leave the bootloader option to be installed on /dev/sda.
10. Continue with the install process and you should be enjoying your vista/ubuntu dual boot.

---

### Post by gwatts on 2011-11-06
Thank you, I will respond tomorrow.

g

---

### Post by gwatts on 2011-11-07
darkod

Thank you. Installation proceeded exactly as you said until on reboot it stalled after a blackish purple screen > a long scroll and all was okay except “starting automatic crash report generation” .
The last entry was checking battery state OK.

After control, alt, delete, another scroll ended in “Pulseaudio configured for per user sessions saned disabled; edit  /etc/defaults/saned.”  which was marked with a yellow star.

 I then tried the recovery Linux selection which stopped at the recovery menu and of

 Of the four options, none of them had worked in the past.

I selected Resume normal boot which > the  purplish black screen and a blinking cursor in the upper left corner.  Again c-a-d  > the usual  choices and I went into Windows without difficulty.

This is really about how I started before, unable to get into the Ubuntu install.

I ran the Easy BCD view setting which revealed:

“There is one entry in the Windows bootload.”  

“The default Windows Vista Ultimate recovered Timeout 10 seconds 
EasyBCD boot device C:\.”

Entry # 1
name: Windows Vista ultimate (recovered)
BCD ID : “Current.”.
Drive C:\.
Bootloader path \Windows\system32\winload.exe

There was no other entry.

---

### Post by darkod on 2011-11-07
That sounds like it has problem with part of your hardware, probably the audio. Did you try googling the specific error? Usually you can find some specific instructions from people that have already solved it.

If from the recovry menu you select Root only )or root session, don't remember exactly), it should boot a text only system. But this is not something you can work with. Maybe only to install some driver or solution for the problem.

PS. Did you ever try booting with the cd in live mode? If the live mode works, the installation should too. If live mode doesn't work it means it has some issue and the installation will have the same. So it is not advised to install until you figure out what the problem is.

---

### Post by gwatts on 2011-11-08
darkod

How would you estimate the chances of this working?  

Wipe the entire hard drive, install an image of Vista and petition the disc with a petition manager and then install Ubuntu in the usual manner.  I would presume that everything is erased with a total hard drive wipe.

What would I do if the hardware such as a sound card is the problem? The laptop is at least four years old.

When you say “ booting with the cd in live mode.”  Isn't that what I've been doing when I  run the computer off the CD?

I did the root thing and tried the commands that you gave me but nothing worked.

Check these links, they are close but in some ways much different from my problem and I don't understand them. Sorry I don't know how to link them.

[http://superuser.com/questions/277515/newly-upgraded-ubuntu-11-04-vm-not-booting](http://superuser.com/questions/277515/newly-upgraded-ubuntu-11-04-vm-not-booting)

[http://askubuntu.com/questions/67430/my-fresh-installation-doesnt-load-pulseaudio-problem](http://askubuntu.com/questions/67430/my-fresh-installation-doesnt-load-pulseaudio-problem)

Thank you.

---

### Post by gwatts on 2011-11-09
Recap since yesterday:

I am trying to dual boot Vista with Ubuntu 11 10. I have done many things and arrived at the point where it will boot only to a grub> prompt where it stalls. I am able to run the Ubuntu live CD  but I cannot enter Vista (as I could until I used the RescueCD) after a repair from the installation Vista disk. That is to say Windows repair does not work.

While I have never been able to dual-boot as I should on this  laptop, I was able to boot into Windows Vista while I was playing around with Easy  BCD and almost every other command I could find. The most recent and immediate thing that I did  was to use a SystemRescueCD

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

that was supposed to solve all my problems.  I ran each of the various options without benefit.

I read  that wiping the entire hard drive and reinstalling Windows may not affect the boot loader.  Is it correct that there boot codes somewhere on hardware affecting the boot process that I cannot change by wiping, format,  repartitioning and installing Windows?

Any advice or suggestions will be appreciated.

---

### Post by darkod on 2011-11-09
Reinstalling vista should work. The install process will write the windows bootloader to the MBR of the disk (the first sector) overwriting the earlier bootloader.

Don't forget, if you still plan to dual boot, when installing vista create the vista partition as big as you need it, and leave the other part of the hdd unallocated (not belonging to a partition). Later you will have unallocated space to install ubuntu.

---

### Post by critin on 2011-11-09
**To darkod: ** For my education please.   :confused:  This seems to show the OP* may not be* waiting for the os to load completely.   Using the restart method too quick and too often?   It's used two or three (++?) times in this instance.  In Windows, C-A-D is an easy way to get out of sticky situations, but doesn't do the same in linux if used indiscriminately.   A Bad Windows habit used when we have no patience to wait.   I mean sometimes I get the long scroll with an error here and there with other things marked OK.  I let it go and it loads up and works fine.  
His audio wasn't disabled until after he'd hit C.A.D.  which would be normal on a restart.  

Most errors must be fixed automatically because I don't do it.   Thanks, I'm still learning and my patience has improved considerably.


>    [gwatts]("http://ubuntuforums.org/member.php?u=247615") Thank you. Installation proceeded exactly as you said until on reboot it  stalled after a blackish purple screen > a long scroll and all was  okay except &#8220;starting automatic crash report generation&#8221; .
The last entry was checking battery state OK.

After control, alt, delete, another scroll ended in &#8220;Pulseaudio  configured for per user sessions saned disabled; edit   /etc/defaults/saned.&#8221;  which was marked with a yellow star.

---

### Post by gwatts on 2011-11-09
Following your directions I had successfully installed and rebooted several times both Windows Vista as well as UBUNTU and then I brought over an image of C: to replace the fresh install and I lost Ubuntu. 
 I then reinstalled Ubuntu just as you directed and exactly as I did the first time and now I can boot Windows but not Ubuntu.  The scroll stalls as before with the "pulse audio configured===== etc." that I sent you earlier as well as "automatic crash report generation" and a new fail "light DEM display manager" which is a red fail followed by an okay which is below the red fail of "Light DEM display manager". There is nothing on the left in the scroll list online with the okay.  I don't know how to interpret that. I guess it does not matter.h
I will start over tomorrow.  Thank you.

---

### Post by darkod on 2011-11-09
> **gwatts said:**
> Following your directions I had successfully installed and rebooted several times both Windows Vista as well as UBUNTU and then I brought over an image of C: to replace the fresh install and I lost Ubuntu. 
 I then reinstalled Ubuntu just as you directed and exactly as I did the first time and now I can boot Windows but not Ubuntu.  The scroll stalls as before with the "pulse audio configured===== etc." that I sent you earlier as well as "automatic crash report generation" and a new fail "light DEM display manager" which is a red fail followed by an okay which is below the red fail of "Light DEM display manager". There is nothing on the left in the scroll list online with the okay.  I don't know how to interpret that. I guess it does not matter.h
I will start over tomorrow.  Thank you.

You never said you want to apply an image of C:. We have no idea what it does to the ubuntu partition, and to the whole computer.

I think it's better to stop right now, and take a small break. Vista works now after the applied backup, but not ubuntu. Don't reinstall anything right now.
Follow the link in my signature from ubuntu live mode, download and run the bootinfoscript. Post the content of the results.txt file here, included in code tags as explained on that link.
Lets see what is the current status and figure out why ubuntu can't boot.
In theory, it all depends how applying the vista backup changed the computer. If it only deleted the bootloader from the MBR it's easy to simply put it back there from ubuntu live mode, no need to reinstall whole of ubuntu.
One thing though: If you planned to apply image of C: why did you start with clean vista reinstall? Why not apply the image, and then continue from there by installing ubuntu? If you are shrinking the vista partition for this purpose don't forget to do it with vista disk management, reboot vista few times to do its checks, and only then install ubuntu.
But now that's done, run the script first and report the results. It should have more information about the boot process.

---

### Post by mikaelcrocker on 2011-11-09
I have used GRUB as a boot loader, and it seems that GRUB is better at changing and managing windows files when Linux is already installed.  Always worked better for me.

---

### Post by gwatts on 2011-11-10
thank you.

 Didn't know  how to apply image  without OS.               


Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    87,891,614    87,891,552   7 NTFS / exFAT / HPFS
/dev/sda2          87,891,968   120,291,327    32,399,360  83 Linux
/dev/sda3         120,294,781   128,680,649     8,385,869   f W95 Extended (LBA)
/dev/sda5         120,294,783   128,680,649     8,385,867  82 Linux swap / Solaris
/dev/sda4         128,680,653   234,441,646   105,760,994   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        04F47061F4705740                       ntfs       
/dev/sda2        bd305c6f-8a4f-4b04-8c40-fa29fb21cb81   ext4       
/dev/sda4        06C6BF7AC6BF6897                       ntfs       
/dev/sda5        d7b347d3-a627-438b-9592-558218114867   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/06C6BF7AC6BF6897  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
	linux	/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=bd305c6f-8a4f-4b04-8c40-fa29fb21cb81 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
	echo	'Loading Linux 3.0.0-12-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=bd305c6f-8a4f-4b04-8c40-fa29fb21cb81 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=bd305c6f-8a4f-4b04-8c40-fa29fb21cb81 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=bd305c6f-8a4f-4b04-8c40-fa29fb21cb81 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root bd305c6f-8a4f-4b04-8c40-fa29fb21cb81
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 04F47061F4705740
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=bd305c6f-8a4f-4b04-8c40-fa29fb21cb81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d7b347d3-a627-438b-9592-558218114867 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-12-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              2
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  b6 75 c2 e9 ca 14 f4 8c  c0 aa ff f3 42 c4 f5 18  |.u..........B...|
00000010  40 ea a0 01 99 78 00 8a  9b 43 95 6a da e5 82 ae  |@....x...C.j....|
00000020  5a b5 e9 98 b3 75 20 2c  a3 cc 10 31 e7 84 c8 59  |Z....u ,...1...Y|
00000030  57 21 0e 03 3d 63 49 28  ed 97 5f c7 0a fa 1c 9f  |W!..=cI(.._.....|
00000040  ff f4 fc 62 02 fe 8c 80  0e a8 89 a2 00 93 38 da  |...b..........8.|
00000050  a6 d9 e9 db 96 5d a9 53  bb 3b 52 e4 9e 7c 5c ca  |.....].S.;R..|\.|
00000060  a5 88 57 2e 8a 4e 5b 63  a9 a2 34 d3 78 e3 eb a4  |..W..N[c..4.x...|
00000070  c2 0c 55 ff f3 40 c4 f0  19 40 f2 a4 0b 99 60 00  |..U..@...@....`.|
00000080  68 43 27 50 4f 8c 48 2e  50 42 28 44 48 dd 65 46  |hC'PO.H.PB(DH.eF|
00000090  93 0f 82 65 50 e2 aa 25  4d d8 04 e9 dd 01 61 43  |...eP..%M.....aC|
000000a0  4f d0 6e e7 ff dc cd dd  51 5a 37 97 21 0c d1 fc  |O.n.....QZ7.!...|
000000b0  50 c3 10 03 68 95 4c c9  9c 58 c0 10 24 fb a2 9c  |P...h.L..X..$...|
000000c0  76 2b 41 72 c1 5b 4c 09  66 40 c0 ca 14 45 c8 df  |v+Ar.[L.f@...E..|
000000d0  3c 3e f5 d5 82 0c df a6  75 71 0d ff f3 42 c4 e6  |<>......uq...B..|
000000e0  16 e8 e2 a0 01 99 78 00  85 96 ad 3f 7e 90 cd 9c  |......x....?~...|
000000f0  bd 2f f6 bf 4d f7 1d 8e  1d d9 98 0e 9f 0d 86 4b  |./..M..........K|
00000100  e8 22 86 0a 80 4a 2c 8a  03 49 17 e6 ad 7f fd fb  |."...J,..I......|
00000110  ff dc fd 5a 2a 74 44 a0  56 e1 2b 40 82 84 32 34  |...Z*tD.V.+@..24|
00000120  c3 12 1a 6d 6e 82 ce 12  0f 70 db 23 c1 be 75 65  |...mn....p.#..ue|
00000130  4f bb 48 2c bf 2a d4 31  29 f5 2c 0f b8 d2 de 97  |O.H,.*.1).,.....|
00000140  cd 20 3f 8b ff f3 40 c4  e6 16 20 de a4 0b 98 48  |. ?...@... ....H|
00000150  00 15 d4 36 df 36 f5 1d  f2 32 d0 ec dd 07 56 b7  |...6.6...2....V.|
00000160  b6 a9 ed 6b 56 3c 37 90  de cd 67 08 8f e0 56 9a  |...kV<7...g...V.|
00000170  f9 df df ef d8 18 ab 3e  71 9d 36 b7 28 a2 d7 35  |.......>q.6.(..5|
00000180  67 7b 7f 5a 7c 89 cf ff  fb 4a 0b 6a c1 67 03 9f  |g{.Z|....J.j.g..|
00000190  fa 5c df f0 ea 6a 10 e9  44 98 1c a1 a8 17 10 be  |.\...j..D.......|
000001a0  2c 05 91 34 0d 15 08 03  29 99 af 3b ff f3 42 c4  |,..4....)..;..B.|
000001b0  e8 17 51 3a 9c 01 99 60  00 9e 16 1e 90 47 00 fe  |..Q:...`.....G..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 4b f5 7f 00 00 00  |..........K.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by darkod on 2011-11-10
Depending what program are you using for your windows recovery, most of them would allow you to create a boot cd which you use to boot the computer and apply the image from external HDD for example.
Even using the built in windows backup solution lets you create a boot cd.

There is nothing wrong I can see in the results, except that you seem to be using generic-pae kernel and not the standard generic. Where did you get this cd of ubuntu?

Ii looks like in the grub boot menu you should have submenu saying Previous versions, did you try booting ubuntu from there? There should also be one ubuntu there and that's the standard generic kernel.

Otherwise the first ubuntu option at the top is generic-pae.

---

### Post by gwatts on 2011-11-10
I  downloaded  from Ubuntu and made 2 CDs (because 1st didn't work).
First entry Ububtu-----------------  -pae does not boot.
Previous versions does indeed  reveal 2 entries: 
Ubuntu------------3.0.0.12-generic
Ububtu----------               same    with recovery mode
The  first entry boots. 
Should I leave it like this?  What's happening?
Other boot options failed.

---

### Post by darkod on 2011-11-10
I have seen -pae mentioned but I don't know what's it all about. The standard kernel is -generic and the -pae probably has some differences otherwise it wouldn't be called differently.

For the time being I would use it with the -generic, it works. If I got it right, you can now boot both vista and -generic, which means both OSs work.

Use it like this and later you can investigate what is the point with -pae if you feel like it.

---

### Post by mohamedtoma73 on 2011-11-10
i can figure a solution. install ubuntu inside windows vista using wubi.in the boot menu of wubi ubuntu installation you will see entry of the previosly installed ubuntu(installed before windows installation).if you do not see the entry boot into wubi installation and run sudo update-grub in a terminal and you are done.you will see the entry of ubuntu installation (the one before windows ) in the boot screen of wubi ubuntu installation

---

### Post by Mark Phelps on 2011-11-10
Cardinal rule ... if it isn't Broken, don't fix it!

Messing around with Wubi, and then with GRUB updates, is a sure-fire way to mess up something in your existing system.

My advice -- leave it alone.

---

### Post by darkod on 2011-11-10
> **Mark Phelps said:**
> Cardinal rule ... if it isn't Broken, don't fix it!

Messing around with Wubi, and then with GRUB updates, is a sure-fire way to mess up something in your existing system.

My advice -- leave it alone.

+1

Especially since the OP is already on dual boot. Wubi was meant as a previous step, to test how you like it, installing inside windows. When a dual boot already exists going the wubi way can only create problems.

---

### Post by gwatts on 2011-11-10
Great help. Thank you. Close question?

---

### Post by darkod on 2011-11-10
You are welcome. You can mark it Solved in Thread Tools above the first post on the page. Because it's your thread only you can mark it.

---

