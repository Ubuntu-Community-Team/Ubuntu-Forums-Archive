---
title: "Can't boot Windows 7 after Grub update"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by Rhodophyta on 2010-07-21
I have been phenomenally unlucky with Ubuntu as seen my my post history and decided to dual boot. 

I set it all up with a clean install, when I tried to load Windows from Grub the computer restarted. After much headache I managed to set it up correctly (when it wouldn't load from Grub I booted from the Windows CD and clicked on "Repair computer" and it finally worked).

Now I am having the same problem as before--I think my installed all the updates from Update Manager and it included a grub one. Now I can't load Windows from the grub menu: It goes to the Starting Windows screen and then reboots my computer. If I do it again it gives me an error message and an option to perform "Startup repair". When I try to do Startup Repair, the computer reboots after a few loading screens.

So I tried what worked before and put in my Windows 7 CD, and clicked on Repair Computer. BUT NOW it gives me an error message somewhere along the lines of system restore is not compatible with my installation of Windows, and to insert a compatible recovery CD. This is the ONLY Windows CD I have (legitimate copy).

Over the course of this migration experiment I have installed and reinstalled both operating systems 7-10 times total.  I'd rather not do it again. My poor laptop is probably wondering what the heck.

I can't stick with Ubuntu alone because my wireless doesn't work with it, my grad school files are not completely compatible with open source software, and I can't play the games I'd like to. So I must have the option to at least dual boot into Windows.:( 

Please, if anyone can help me troubleshoot I would greatly appreciate it.

Edit: When selecting Windows it restarts the computer entirely to the Compaq screen, not just to the Grub menu, if that matters.

---

### Post by wilee-nilee on 2010-07-21
Post the bootscript in my signature in code tags as described. At this point you must know what the mbr is and where it's at; is this correct?

---

### Post by Rhodophyta on 2010-07-21
Thanks so much for your quick reply! I know that the MBR is Window's booter, essentially, and it doesn't play well with others :) When I did clean install, I deleted ALL partitions from the Ubuntu CD, created a brand new one for Windows to have all to itself, installed Windows onto that partition, created a storage partition, then installed Ubuntu onto the remaining space using the "use side by side" install option. I thought it would be the most foolproof way, and it was (after repairing Windows with it's CD) until just today.

Here is the output
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00044831

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,513,148   123,513,086   7 HPFS/NTFS
/dev/sda2         252,879,165   488,392,064   235,512,900   5 Extended
/dev/sda5         252,879,228   478,736,999   225,857,772  83 Linux
/dev/sda6         478,737,063   488,392,064     9,655,002  82 Linux swap / Solaris
/dev/sda3         127,042,020   252,879,164   125,837,145   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        785E263D33679FD3                       ntfs       Windows 7                     
/dev/sda3        6A3448321BF1408B                       ntfs       Storage                       
/dev/sda5        fda81d8d-b393-4d85-a401-1461d86942c5   ext4       Ubuntu                        
/dev/sda6        83336a67-ed0f-4a77-811f-bd1bf0ed3a59   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/Storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set fda81d8d-b393-4d85-a401-1461d86942c5
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fda81d8d-b393-4d85-a401-1461d86942c5
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=fda81d8d-b393-4d85-a401-1461d86942c5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fda81d8d-b393-4d85-a401-1461d86942c5
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=fda81d8d-b393-4d85-a401-1461d86942c5 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fda81d8d-b393-4d85-a401-1461d86942c5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fda81d8d-b393-4d85-a401-1461d86942c5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set fda81d8d-b393-4d85-a401-1461d86942c5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fda81d8d-b393-4d85-a401-1461d86942c5 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 785e263d33679fd3
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=fda81d8d-b393-4d85-a401-1461d86942c5 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=83336a67-ed0f-4a77-811f-bd1bf0ed3a59 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 132.5GB: boot/grub/core.img
 144.6GB: boot/grub/grub.cfg
 130.0GB: boot/initrd.img-2.6.31-14-generic
 130.4GB: boot/initrd.img-2.6.31-22-generic
 130.0GB: boot/vmlinuz-2.6.31-14-generic
 129.8GB: boot/vmlinuz-2.6.31-22-generic
 130.4GB: initrd.img
 130.0GB: initrd.img.old
 129.8GB: vmlinuz
 130.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by wilee-nilee on 2010-07-21
The script looks okay, have you run a sudo update-grub in Ubuntu?

You mention a windows cd but you must have a W7 ISO of some sort on a dvd or a thumb. It seems the problem is with windows, hard to tell really, but grub looks correct as far as I can tell.

---

### Post by Rhodophyta on 2010-07-21
Holy moly! I ran sudo update-grub and restarted my computer. I figured I'd have to let Windows do "Startup repair" first so I did, and it was on the "attempting repairs" screen for ages. I got fed up, turned off my computer and booted it back up. This time I ignored the Windows message and chose "Start Windows normally".

And it worked! I guess it was just a matter of running sudo update-grub.

My husband says I'll be back when I encounter yet another problem, but I think everything is okay for now ;) Thanks for that tip!

---

### Post by Rhodophyta on 2010-07-21
I'm sorry to reopen my thread.

The problem has not been solved permanently. I just woke up this morning to boot into Windows and the SAME thing happens. I don't know if I need to restart my computer 5-6 times in a row to get it working or what caused it to work last night, but I still don't have a solution.

I would love more help troubleshooting, please. Thanks so much!

---

### Post by oldfred on 2010-07-21
If it was running chkdsk or other repairs shutting it down while in the middle is not a good idea.

Try running chkdsk on the NTFS partition from the Windows CD.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by RJARRRPCGP on 2010-07-21
> **Rhodophyta said:**
> : It goes to the Starting Windows screen and then reboots my computer. 

The rebooting is because Windows is P-ed off about something!

---

### Post by NFblaze on 2010-07-21
> **RJARRRPCGP said:**
> The rebooting is because Windows is P-ed off about something!

I actually had this problem also. I dont know what caused it and never did find out. Though, later on with a different program that modifies the MBR I saw something similar. I narrowed it down to how some computers particularly HP/Compaq CQ series and Pavilions have the Recovery Partition for Windows bootable via the Fkey. Never got to investigate further though on my Linux computer. Though, on the computer with that issue and the program we used it was best to wipe the MBR.

---

### Post by Rhodophyta on 2010-07-21
I don't understand how to run chkdsk if I can't get into Windows in the first place, even with the CD?

I ran Startup repair because I just had to try one more time, and I noticed something significant! It rebooted my computer after two "Windows is loading files" and the splash screen. It just clicked that I was looking at the Vista splash screen, NOT Windows 7, before it rebooted. This is the only time I ever see that screen (but I recognize it from my work computer).

My machine came with Vista, but my husband promptly removed it and put Windows 7 on. So I guess it has something to do with the that? Which would also explain why the repair option on my Windows 7 CD won't work (although the installed OS listed in the CD repair screen is 7, not Vista). Like my computer "remembers" that it's supposed to have Vista and it's freaking out now? And all this was brought on by messing with the MBR?

The Vista CD more likely than not is in another country. I bought the computer over a year ago.

I'm excited to finally shed light on something! Is there something I can do to fix this? How do I wipe all traces of Vista?

---

### Post by NFblaze on 2010-07-21
Unfortunately, if this is indeed the case (and it probrably might be). 

It is a huge headache trying to un-screw the stupidity that is involved when Windows bootloaders conflict with another bootloader. It's probably not feasibly simple to explain it over the internet. Especially with so many variables. You'd prolly be better off starting from scratch.

---

### Post by oldfred on 2010-07-21
Did you end up in the recovery partition sda3?  Sometimes the recover partitions were still labeled Vista whether XP, Vista or 7 was the actual operating system installed when they were offering different systems.

The recovery partition may also let you run chkdsk or other repairs. It seems to be and issue wit the BCD which holds you boot choices. BCDedit is to update it. I do not know anything about easyBCD but it is a third party tool to also fix or edit BCD file. Some here that use windows have suggested it.

---

### Post by Rhodophyta on 2010-07-22
I could be okay with starting over one more time. But the last time I thought I did everything clean and from scratch. I used gparted from the Ubuntu Live CD and deleted every single partition listed so it was entirely unallocated space. Then I created a brand new partition for the Windows 7 installation, and installed Ubuntu second using the "side by side" option.

If that wasn't sufficient to wipe Vista completely, what is? How do I redo it? Can I keep my storage partition or do I need to back up everything on it as well?

And if I do have to reinstall both OSs I think I'll try Mint this time. It shouldn't be a problem, right?

Edit: Fred, I'm so sorry for sounding like an idiot, but I don't know what partition I ended up in. sda3 appears to be my storage partition from the results of the bootinfo script. sda1 is where Windows 7 should be, sda 2 is an extended one that includes sda5 (linux), sda6 (swap). Come to think of it, there's no sda4 to be found. Maybe that's the recovery one?

---

### Post by oldfred on 2010-07-22
No, I guess I was thinking sda3 might be a recovery partition but it has not boot files at all, so it must just be data. If you deleted all partitions and then started over there is no sda4.

Can you boot windows now? Does Ubuntu boot? What error messages?

---

### Post by Rhodophyta on 2010-07-22
Ubuntu boots just fine, but Windows won't boot at all. When I first turn on the computer and try to boot Windows, I see the Windows 7 splash screen and then the computer reboots to the Compaq screen.  If I try to boot Windows again, it gives me an option to launch Startup recovery. If I do, the following happens:
I see two screens that say "loading Windows files"
Then I see the **VISTA** splash screen, not Windows 7
Then the computer reboots itself.

When I put in the Windows 7 CD to launch Repair, I go to the screen that says "select your operating system to repair". Windows 7 is listed, and the partition is the correct size. But when I hit ok, I get an error message that this startup disc is not compatible with this version and to insert the correct recovery CD (paraphrasing here).

I have not tried to reinstall Windows onto that partition as I am afraid to do so yet again without knowing what's wrong in the first place. Apparently the Vista bootloader is there somewhere and I don't know how to do a COMPLETELY clean install. I already tried deleting all partitions with the Ubuntu live CD and starting over as per my post above.

I'm definitely willing to give it another shot, but I need to know how to do a clean install and kill Vista remnents entirely, if I need to delete my storage partition, and any other steps I can take so this install works.

---

### Post by oldfred on 2010-07-22
If you are going to reinstall windows I would not touch the partitions, just reinstall to the existing NTFS partition. That way you will not have to resize it. Also clean installs of 7 put an extra 100MB boot/recovery partition as a primary partition using one of your 4 primary partitions. Installs to existing partitions do not add the extra boot partition.

---

### Post by YnotStrebor on 2010-07-22
Rhodophyta, you said you have a gap between sda1,2,3 and sda5,6

Might be related to a problem I had when I was dual-booting WinXP & Ubuntu 9.10. WinXP was on the primary partition, with temporary files, programs, documents on separate partitions. Then I added Ubuntu. For some nutty reason I decided to put the Ubuntu & swap partitions towards the end of the disk, with a great big empty, unformatted, unused partition in between the Ubuntu and Windows partitions. Installation was fine... however...

This resulted in GRUB refusing to work properly (no menu options). Couldn't boot Ubuntu or Windows. I could boot either Linux or Windows, but only if I used a floppy disk bootloader other than GRUB.

Realised that GRUB wasn't seeing the Ubuntu partition - it could see up to the unformatted gap then no more. The problem was resolved by placing the Ubuntu Partition directly after the Windows partition, no gaps, no other partitions in between.

As a backup operating system to browse the net to find a solution to the problem I used Puppy Linux. The advantage with this is that it runs off a CD and seems to be able to detect enough hardware & graphics cards.

---

### Post by Rhodophyta on 2010-07-22
I do have a gap between the Windows partition and the Linux partition! I did it on purpose to give a little wiggle room if I needed to give Windows more space.

What I think I will do now is use gparted from the live cd to move my partitions so it goes Windows-->Linux--->Storage with no gaps in between, then reinstall Windows onto the NFTS partition. I'm a little nervous because I hear it's hard to install Windows AFTER Linux.

But where exactly is the Vista stuff hiding? I feel like if I don't figure that out and delete it all to heck all this will happen again.

Edit: Does anyone know if the recovery partition that comes with HP computers is somehow hidden from view from gparted?

---

### Post by oldfred on 2010-07-23
Gparted will see all the partitions.

I do not think a gap is a problem. Partitions often have little gaps normally. 

Was your win7 install an upgrade from Vista? It may have left something. If it was an upgrade your win7 CD has to see that to update to win7, It will not do a new install.

The only difficulty installing windows after Ubuntu is that windows does not give an option on installing boot loaders and will automatically install the windows boot loader to the MBR. You then have to reinstall grub2 to get Ubuntu working. After installing grub a couple of times you will find it is not a big difficulty. So its not hard at all, just one extra step.

---

### Post by Rhodophyta on 2010-07-23
OK, I reinstalled Windows 7 onto sda 1, deleted Ubuntu, and reinstalled a  different distro onto the largest free space. Don't ask me why I did  this...but during the install I unchecked "install bootloader". I  figured, given the problems I've been having, I should do everything  manually. And I held off on a storage partition for now until I get this figured out.

I used the SuperGrub disk to boot into Linux and typed```
 sudo  apt-get install grub 
sudo update-grub
```The command ```
sudo grub 
find /boot/grub/stage 1
``` returns Error 15: File not found

Attempting to Fix Linux Boot from the supergrub CD also returns Error:  15 File not found, SGD was NOT successful

Here's the output of fdisk -l:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044831

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7689    61761861    7  HPFS/NTFS
/dev/sda2            7690       30402   182435841    5  Extended
/dev/sda5            7690       29745   177159168   83  Linux
/dev/sda6           29745       30402     5275648   82  Linux swap /  Solaris
```And the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

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

/dev/sda1    *             63   123,523,784   123,523,722   7 HPFS/NTFS
/dev/sda2         123,525,118   488,396,799   364,871,682   5 Extended
/dev/sda5         123,525,120   477,843,455   354,318,336  83 Linux
/dev/sda6         477,845,504   488,396,799    10,551,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        708681247CF2B9DB                       ntfs       Windows 7                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d83f968b-60a7-4b87-b0bc-95dc7473e562   ext4       Linux                         
/dev/sda6        618be07e-f2de-4cbb-8f33-ae53a0a6bc8d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d83f968b-60a7-4b87-b0bc-95dc7473e562 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d83f968b-60a7-4b87-b0bc-95dc7473e562

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Linux Mint 9 Isadora, kernel 2.6.32-21-generic
uuid        d83f968b-60a7-4b87-b0bc-95dc7473e562
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=d83f968b-60a7-4b87-b0bc-95dc7473e562 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic

title        Linux Mint 9 Isadora, kernel 2.6.32-21-generic (recovery mode)
uuid        d83f968b-60a7-4b87-b0bc-95dc7473e562
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=d83f968b-60a7-4b87-b0bc-95dc7473e562 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Linux Mint 9 Isadora, memtest86+
uuid        d83f968b-60a7-4b87-b0bc-95dc7473e562
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d83f968b-60a7-4b87-b0bc-95dc7473e562 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=618be07e-f2de-4cbb-8f33-ae53a0a6bc8d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 185.8GB: boot/grub/menu.lst
 185.8GB: boot/initrd.img-2.6.32-21-generic
  63.3GB: boot/vmlinuz-2.6.32-21-generic
 185.8GB: initrd.img
  63.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```Please help restore my grub without screwing up Windows too badly? I've looked everywhere and the instructions from various googled sites always result in the error messages above. Again, I CAN boot into Linux from the SuperGrub disc but not fix my linux boot. Without any CD loaded it goes straight to my newly installed Windows 7.

---

### Post by Rhodophyta on 2010-07-23
This is unbelieveable.

I managed to fix grub with the disc to boot Linux. But then Linux booted automatically with no Windows option.

I loaded the grub disc again and chose "Fix Windows Boot". Of course, it wiped out grub and let me boot Windows. But there was no menu to boot to Linux.

I loaded the grub disc again and chose "Fix Linux boot". But then Linux booted automatically with no Windows option.

Going in circles here.

Is it really impossible for my computer to dual boot? I'm starting to think I have to pick one and just use the SuperGrub disc to change the default (it allows me to boot into either OS). I really don't want to do that.

---

### Post by oldfred on 2010-07-23
By installing old grub you may have more issues finding windows. It seemed old grub often had to have us manually give users a stanza to post as it cannot find windows. Grub2 almost always finds windows even copies that will not boot.


Paste this stanza into your menu.lst. Do not put it into the automagic area as that gets updated with every kernel update.

so after this:
## END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7 (loader) on sda1
rootnoverify    (hd0,0)
savedefault
chainloader    +1

---

### Post by corona79 on 2010-07-23
> **Rhodophyta said:**
> 

Is it really impossible for my computer to dual boot? I'm starting to think I have to pick one and just use the SuperGrub disc to change the default (it allows me to boot into either OS). I really don't want to do that.

It's really unbelievable, given how long people have wanted to add Linux to a Windows PC, that creating a dual-boot system is so complicated and dangerous.

---

### Post by Rhodophyta on 2010-07-23
Hello, yes! I pasted that into my menu.lst and it seemed to do the trick! Posting this from crappy old IE right now!
 
Thanks so much! Hopefully this fix will stick, this time. I'll post again if there are any further problems.

---

