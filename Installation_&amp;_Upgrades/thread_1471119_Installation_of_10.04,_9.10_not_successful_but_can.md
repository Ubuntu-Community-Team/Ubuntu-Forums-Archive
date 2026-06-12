---
title: "Installation of 10.04, 9.10 not successful but can install 9.04 without any problem"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by slee328 on 2010-05-03
Hi:

I have been using Ubuntu for a while but I am not a super admin type of person.  I have an old AMD Athlon 32-bit PC with 2GB of RAM and a Maxtor 8GB and WD 60GB HDD, I have no problem with using and installing of ubuntu till 9.10.  The latest ubuntu version that I can install on this desktop was 9.04.  When 9.10 released, I tried to upgrade from 9.04 or fresh install of the 9.10 on this desktop without any success.  It usually hangs right after the BIOS message in the startup sequence.  I cannot even get to the flash screen of ubuntu 9.10.  Then when 10.04 released in the past few days, I tried to the do the same upgrade or re-installation of ubuntu 9.10 to this desktop without success.  It will shows the blank dark screen after the BIOS booting sequence with the LED lit up on the 1.44 FDD constantly.  Even if I changed the boot sequence to have the HDD boot ahead of the 1.44 FDD, I still get the blank screen without after the BIOS boot sequence.

Am I having too old of HW for ubuntu?  I do not know the issue but spent many hours in installing 9.10 and 10.04 without success.  Any help that anyone can offer will be very helpful and I would like to keep up in using the latest offering from ubuntu.  Thanks in advance.

Regards,
Stephen Lee

---

### Post by oldfred on 2010-05-03
Welcome to the forums.

Since you mentioned floppy, I have seen one or two comments where they turned off the floppy in BIOS and got it to work. I had no issues at all with Karmic on both my desktop and laptop, but with Lucid I have had to add nomodeset to get it to work.

---

### Post by quadproc on 2010-05-03
> **slee328 said:**
> Hi:

I have been using Ubuntu for a while but I am not a super admin type of person.  I have an old AMD Athlon 32-bit PC with 2GB of RAM and a Maxtor 8GB and WD 60GB HDD, I have no problem with using and installing of ubuntu till 9.10.  The latest ubuntu version that I can install on this desktop was 9.04.  When 9.10 released, I tried to upgrade from 9.04 or fresh install of the 9.10 on this desktop without any success.  It usually hangs right after the BIOS message in the startup sequence.  I cannot even get to the flash screen of ubuntu 9.10.
You might be having an issue with your graphics hardware and/or its driver.  It would be helpful to know what versions of graphics hardware and software that you are running.

quadproc

---

### Post by slee328 on 2010-05-04
Hi:  The graphics card that I have is an ATI one which is identified as AIW 8500DV 64MB DDR and its Product number is: 10284801210 69995.  I think the board was made in 2002.

---

### Post by slee328 on 2010-05-11
I installed 10.04 again and there was no luck.  10.04 is not coming up either.  I boot from the Live-CD and try to edit the /etc/default/grub file and run the update-grub utility.  However, since I was not booted from the local HD, I got an error from update-grub.

I tried to remove the 'quiet' and add 'nomodeset' boot options from the boot sequence.  I suspect that 10.04 does not like my old ATI AIW graphics card and hang from booting.

Anyone can offer any help here on this thread?

---

### Post by darkod on 2010-05-11
> **slee328 said:**
> I installed 10.04 again and there was no luck.  10.04 is not coming up either.  I boot from the Live-CD and try to edit the /etc/default/grub file and run the update-grub utility.  However, since I was not booted from the local HD, I got an error from update-grub.

I tried to remove the 'quiet' and add 'nomodeset' boot options from the boot sequence.  I suspect that 10.04 does not like my old ATI AIW graphics card and hang from booting.

Anyone can offer any help here on this thread?

The first test you can do is when the grub2 menu shows up (or keep hitiing Shift to make it show up if ubuntu is only OS it won't show up by default), highlight the ubuntu normal mode entry but don't press Enter. Hit 'e' and that will show you the boot lines.

There you can remove quiet and add nomodeset.

Hit Ctrl + X to try to boot. If that works and you can boot that way, it seems you know where to add them for permanently (/etc/default/grub).

PS. If the live mode boots OK from the cd, doesn't sound like hardware problems. It shouldn't work neither.

---

### Post by slee328 on 2010-05-11
I tried the following:

Power cycled the computer, when it boots up, after the BIOS screen, I keep hitting the 'Shift' key.  However, the most I can get is a single line screen output of 'GRUB Loading.'.  Then the computer hung again.  I repeated this method a dozen times already but was not able to get the GRUB menu loaded.

My machine is an old Compaq Media Desktop with the first generation of AMD Athlon 32-bit CPU.  I have used it to try the LiveCD and it runs flawlessly and I also confirmed that the first HD that I have is set to the bootable from the Partition Manager of the LiveCD.

What other thing that I can try?  I really want to fix this issue.  So I can restore it back to a working state for my 10 year son who uses it for his school work.  Any help is much appreciate!!

---

### Post by darkod on 2010-05-11
Did you try disconnecting the FDD as oldfred said?

If that also fails, the last idea I have is the Alternate CD, not the standard Desktop LiveCD.

Download the image of the alternate install cd and boot with it and try to install fresh. You still end up with the same system but the installer is text based, not graphical.

However it seems to work better especially on older machines. I'm not sure how comfortable you are with text based installers, but it's rather straight forward.

There is still the option that it will install OK but not be able to boot later, but I have no other ideas right now.

---

### Post by slee328 on 2010-05-11
Hi:  I have disabled or removed the FDD from the BIOS setting.  However, I did not disconnect the FDD controller cable or its power cable to the FDD unit.  I will try the alternate CD installation as well.  Although I am not a Linux guru but I start using it since Slackware distro days.  For those who do not know Slackware, it is a very old distribution of Linux software in the infancy days of Linux.  Thank you for your help and I will report back with my trying and results.  You folks are great in providing me with the support.  Thanks again!!

---

### Post by darkod on 2010-05-11
Well, we weren't much of a help. :)

A really last idea would be to use 9.04 until you manage to figure this out. It will still have support until October since standard releases (not LTS) have 18mths support. And 9.04 was released April 2009.

---

### Post by oldfred on 2010-05-11
Depending on the video card this has other settings:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by slee328 on 2010-05-11
Hi:  I just did a reinstallation of 10.04 using the Alternative Installation CD but it behaved in a similar way.  The computer will hang and did not even boot to GRUB even, I have tried about 4 times in rebooting and trying to press the <Shift> key.  In this round, I even unhook the power and controller cable to the FDD.  I think, I am stuck and cannot move forward to  install 10.04 properly.  The latest version that I can run on this machine is 9.04.  This is an old Compaq Presario 7110US with 1333MHz CPU with 2GB of RAM and 2 HDDs 8GB (Master) 60GB(Slave).  If anyone can help on this situation, please help.  I can run the 10.04 LiveCD but cannot successfully install the OS on the computer.  It always cannot completely shutdown successfully after either using the LiveCD and Alternative CD for installation.  I have to manually power down the computer and restart it.  Afterward and after the loading of the BIOS screen, the computer will freeze up and there is no HDD activities.  The keyboard is non responsive either.

---

### Post by slee328 on 2010-05-11
oldfred:  Thanks for the link and will let you know how it goes.  I have a question regarding the changes suggested in the link to grub.  How can you edit changes to the grub config if I cannot even boot from the installed computer.  I can boot from the LiveCD.  However, after the edit to the grub file, I need to run update-grub but if I run from the kernel of the LiveCD and run update-grub, the computer will return error.  Any suggestion to overcome this issue?  Thanks!

---

### Post by oldfred on 2010-05-12
For a single boot (edits not saved but good for trying alternatives as it usually comes back )
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot

From the liveCD you can just find the /etc/default/grub and edit the line there.  But you would have to chroot into your system to run the update-grub. But the single boot edits should get you into your system.

---

### Post by slee328 on 2010-05-12
Hi oldfred:  Thanks for you help on this issue.  I tried about 8 times this AM to hold on to the 'e' key on the keyboard to try to get to the GRUB bootloader when my computer reboots but with no success to get to the GRUB bootloader.  I am sure that I have check the box of installing of GRUB when I installed 10.04 and this is my habiit of doing any way when I install an OS.  Hmmm....Seems I am stucked!!! Any other idea?

---

### Post by oldfred on 2010-05-12
If you are configured not to get a menu, with grub legacy it was the escape key and with grub2 it is the shift key to see the menu. You usually have to hold it down from BIOS boot until it appears.

The e is once you see the menu to edit the boot stanza lines.

---

### Post by slee328 on 2010-05-12
oldfred:  I have tried multiple time and holding the 'Shift', or 'Esc' or 'e' keys on the keyboard while the computer was booting.  Unfortunately, none will help me to get to the GRUB or GRUB 2 menue.  Since the latestest install is using 10.04 and I format all the partitions and asked to add the bootloader to the installation.  I assume, GRUB2 is being installed by the 10.04 installation.  Very frustrated and no progress yet with the 10.04 installation.

---

### Post by oldfred on 2010-05-12
lets see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by slee328 on 2010-05-12
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8399 MB, 8399978496 bytes
34 heads, 36 sectors/track, 13403 cylinders, total 16406208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    16,404,479    16,402,432  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046    39,063,551    39,061,506   5 Extended
/dev/sdb5               2,048    39,063,551    39,061,504  83 Linux
/dev/sdb2          39,063,552   107,423,743    68,360,192  83 Linux
/dev/sdb3         107,423,744   117,229,567     9,805,824  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9c7b2554-2493-4303-aff8-82f2167aa0d3   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        155b62e3-c754-48cb-ad38-28061b67a88f   ext4                                     
/dev/sdb3        cb672263-baf8-4f86-8a75-e5df00b5d2ec   swap                                     
/dev/sdb5        a6d70496-0ee7-4eae-9caf-a995cfae3c8f   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        ABD1-F70A                              vfat       USB DISK                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/USB DISK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set a6d70496-0ee7-4eae-9caf-a995cfae3c8f
if loadfont /share/grub/unicode.pf2 ; then
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9c7b2554-2493-4303-aff8-82f2167aa0d3
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9c7b2554-2493-4303-aff8-82f2167aa0d3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9c7b2554-2493-4303-aff8-82f2167aa0d3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9c7b2554-2493-4303-aff8-82f2167aa0d3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9c7b2554-2493-4303-aff8-82f2167aa0d3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9c7b2554-2493-4303-aff8-82f2167aa0d3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9c7b2554-2493-4303-aff8-82f2167aa0d3
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9c7b2554-2493-4303-aff8-82f2167aa0d3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=155b62e3-c754-48cb-ad38-28061b67a88f /home           ext4    defaults        0       2
# /usr was on /dev/sdb5 during installation
UUID=a6d70496-0ee7-4eae-9caf-a995cfae3c8f /usr            ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=cb672263-baf8-4f86-8a75-e5df00b5d2ec none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
   4.8GB: boot/initrd.img-2.6.32-21-generic
   4.7GB: boot/vmlinuz-2.6.32-21-generic
   4.8GB: initrd.img
   4.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  79 74 68 6f 6e 2d 72 64  66 6c 69 62 20 32 2e 34  |ython-rdflib 2.4|
00000010  2e 30 2d 35 0a 32 30 30  38 2d 31 30 2d 32 39 20  |.0-5.2008-10-29 |
00000020  32 33 3a 30 38 3a 34 33  20 63 6f 6e 66 69 67 75  |23:08:43 configu|
00000030  72 65 20 75 6e 61 74 74  65 6e 64 65 64 2d 75 70  |re unattended-up|
00000040  67 72 61 64 65 73 20 30  2e 33 32 75 62 75 6e 74  |grades 0.32ubunt|
00000050  75 32 20 30 2e 33 32 75  62 75 6e 74 75 32 0a 32  |u2 0.32ubuntu2.2|
00000060  30 30 38 2d 31 30 2d 32  39 20 32 33 3a 30 38 3a  |008-10-29 23:08:|
00000070  34 33 20 73 74 61 74 75  73 20 75 6e 70 61 63 6b  |43 status unpack|
00000080  65 64 20 75 6e 61 74 74  65 6e 64 65 64 2d 75 70  |ed unattended-up|
00000090  67 72 61 64 65 73 20 30  2e 33 32 75 62 75 6e 74  |grades 0.32ubunt|
000000a0  75 32 0a 32 30 30 38 2d  31 30 2d 32 39 20 32 33  |u2.2008-10-29 23|
000000b0  3a 30 38 3a 34 33 20 73  74 61 74 75 73 20 75 6e  |:08:43 status un|
000000c0  70 61 63 6b 65 64 20 75  6e 61 74 74 65 6e 64 65  |packed unattende|
000000d0  64 2d 75 70 67 72 61 64  65 73 20 30 2e 33 32 75  |d-upgrades 0.32u|
000000e0  62 75 6e 74 75 32 0a 32  30 30 38 2d 31 30 2d 32  |buntu2.2008-10-2|
000000f0  39 20 32 33 3a 30 38 3a  34 33 20 73 74 61 74 75  |9 23:08:43 statu|
00000100  73 20 75 6e 70 61 63 6b  65 64 20 75 6e 61 74 74  |s unpacked unatt|
00000110  65 6e 64 65 64 2d 75 70  67 72 61 64 65 73 20 30  |ended-upgrades 0|
00000120  2e 33 32 75 62 75 6e 74  75 32 0a 32 30 30 38 2d  |.32ubuntu2.2008-|
00000130  31 30 2d 32 39 20 32 33  3a 30 38 3a 34 34 20 73  |10-29 23:08:44 s|
00000140  74 61 74 75 73 20 68 61  6c 66 2d 63 6f 6e 66 69  |tatus half-confi|
00000150  67 75 72 65 64 20 75 6e  61 74 74 65 6e 64 65 64  |gured unattended|
00000160  2d 75 70 67 72 61 64 65  73 20 30 2e 33 32 75 62  |-upgrades 0.32ub|
00000170  75 6e 74 75 32 0a 32 30  30 38 2d 31 30 2d 32 39  |untu2.2008-10-29|
00000180  20 32 33 3a 30 38 3a 34  34 20 73 74 61 74 75 73  | 23:08:44 status|
00000190  20 69 6e 73 74 61 6c 6c  65 64 20 75 6e 61 74 74  | installed unatt|
000001a0  65 6e 64 65 64 2d 75 70  67 72 61 64 65 73 20 30  |ended-upgrades 0|
000001b0  2e 33 32 75 62 75 6e 74  75 32 0a 32 30 30 00 20  |.32ubuntu2.200. |
000001c0  21 00 83 fe ff ff 02 00  00 00 00 08 54 02 00 00  |!...........T...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by darkod on 2010-05-12
Is this a netbook? /dev/sda is only 8GB. In that case, is /dev/sdc a 4GB memory card?

Get it out of there, I've seen cases when it blocks installing ubuntu and maybe it's bothering your grub2 in this case.

If it works without it, maybe insert it after booting, or possibly another solution will come up when you know what the issue is.

---

### Post by slee328 on 2010-05-12
No this is a old Compaq Presario 7110US with 1333MHz CPU with 2GB of RAM and 2 HDDs 8GB (Master, /dev/sda) 60GB(Slave, /dev/sdb).  /dev/sdc is a USB flash memory.  I can remove the USD stick to reboot and see if it helps.  I doubt it because when I first log this issue, my USB stick is not even there.  I use the USB stick to move the .sh file from another computer to the one that I am installing ubuntu.  I will report back with the boot result after I remove the USB memory stick.

---

### Post by slee328 on 2010-05-13
I tried more rebooting and try to get to the GRUB menu by pressing the 'e', 'Shift', or 'Esc' key on the keyboard of the computer while booting up but I have no success in getting to the GRUB menu.  The computer frozen after the BIOS screen.  The screen was all dark and the keyboard was not responsive.  However, I was still able to boot from the LiveCD and used the "Try Out" of 10.04 without installation.  The graphic displayed properly while using the LiveCD.  Any help there for my installation?

---

### Post by darkod on 2010-05-13
I really have no ideas... :(

If you want to try adding 'nomodeset' or similar, the way to edit your grub on the hdd from live mode is:

sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys

After this by using chroot you are entering your root partition:

To open /etc/default/grub to add 'nomodeset' and delete 'quiet':

sudo chroot /mnt gedit /etc/default/grub

To update grub.cfg after that:

sudo chroot /mnt update-grub

After you're done, unmount with:

sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

This is if you want to try. I have no new clues otherwise.

---

### Post by slee328 on 2010-05-13
I will give it a shot and love to get this installation hurdle of 10.04 behind my current computer and start to use it instead.  When all things fail, I will reinstall the 9.04 and use it them.  This is the last known version that did not give me any installation problem.  Maybe I will try to install 8.04 and patch it up with all the latest patches and try to upgrade it to 10.04 as well to see whether this will get me to 10.04.  However, the preferred way of my ubuntu upgrade is to always reinstall the OS from scratch and mount the existing /home filesystem from a separate partition.  I have hope that someone will be able to help from this forum.  Anyway, thanks for all your pointers and ideas.  They are all logical and help for me to get over this issue.  I appreciate your help very much!!  I will report back of my progress.

---

### Post by oldfred on 2010-05-13
You mention computer is old. Is it old enough to have the BIOS limits that your new hard drive exceeds and you need a /boot at the front of the drive? More info:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

---

### Post by slee328 on 2010-05-13
Hmmm...this may make sense.  I know that GRUB2 is using the first segment of the disk for its code.  I can create a small partition right after that to place the file system /boot there and try out.  How much of disk capacity that I need to provide for the /boot filesystem?  I think it probably will not be big any way.  I will try it out and report back.  However, as I said before, I can have 9.04 installed from the LiveCD without any problem at all.  I also tried 8.10 as well and it worked too.  Just a thought to see if moving /boot to the front of the boot disk will help?  Thanks for the suggestion.

---

### Post by darkod on 2010-05-13
> **slee328 said:**
> Hmmm...this may make sense.  I know that GRUB2 is using the first segment of the disk for its code.  I can create a small partition right after that to place the file system /boot there and try out.  How much of disk capacity that I need to provide for the /boot filesystem?  I think it probably will not be big any way.  I will try it out and report back.  However, as I said before, I can have 9.04 installed from the LiveCD without any problem at all.  I also tried 8.10 as well and it worked too.  Just a thought to see if moving /boot to the front of the boot disk will help?  Thanks for the suggestion.

I think if that is the problem, then 9.04 would be affected too.

Otherwise, 200MB for /boot is plenty. It will have enough space for a decent number of future kernels.

---

### Post by Tholley on 2010-05-13
Not sure this will help, but I noticed you have installed in the ext4 file system.
 
I had similar problems with 9.10, but when re-installed under ext3, all worked great again.

---

### Post by recluce on 2010-05-13
Also not sure if this will help: since this problem is present both in Karmic and Lucid, but Jaunty works fine - and he cannot even get the GRUB2 boot screen, it seems that GRUB2 has severe issues on the OP's machine. Wouldn't it make sense to try to go back to Legacy GRUB?

---

### Post by robert shearer on 2010-05-13
Assuming you have **no other o/s** and can use any drive......(ie **happy to erase all data ?**) then..

Try removing the old 8Gb hard drive from the box.
Jumper the 60 Gb hard drive as master and connect to the first ide cable as master.

Jumper the cd drive as master and connect to the second ide cable as master.

Try to install with that configuration and I think you may have a result.

(I had the same trouble with an old compaq desktop, two hard drives and Grub2. Installing with one hard drive fixed it.
Grub2 doesn't seem to play nice with multiple hard drives of older ide type.)

---

### Post by slee328 on 2010-05-13
Thanks for all of your pointers.  I did more digging and find the following from the link:  [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

<=======================================================================>

  Installing Ubuntu

Warning: Ubuntu Desktop edition installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which allows very little customization). DO NOT USE the Lucid Lynx Desktop edition if you use a boot partition, use multiple OS (more than 2), or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it manually. This is a serious flaw in both Karmic Koala and Lucid Lynx. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).

GRUB2 has caused major problems in installation -- be sure to research the issue before upgrading to Lucid Lynx.

<=======================================================================>

I wonder whether my issue is related to this posting in the link.  If this is the case, shall I use the server ISO instead but I think the server installation ISO is for 64-bit CPUs and I only have the 32-bit version of the Athlon CPU.  Or can someone point me to steps to install the old GRUB and then install 10.04?  If this is possible, which 10.04 ISO image that I should use?  I appreciate for your pointers and comments.

---

### Post by slee328 on 2010-05-13
> **Tholley said:**
> Not sure this will help, but I noticed you have installed in the ext4 file system.
 
I had similar problems with 9.10, but when re-installed under ext3, all worked great again.

I have tried installed 10.04 with EXT3 and EXT4 file system but they worked the same that my computer was hung after the installation.  Thanks for sharing of your experience.

---

### Post by darkod on 2010-05-13
> **slee328 said:**
> Thanks for all of your pointers.  I did more digging and find the following from the link:  [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)


Ignore that link, it's rubbish. Another person pointed to it and I was shocked to read the amount of wrong information there. One of all, grub2 is more than able to boot 3 or more OSs...

ubuntuguide.org has nothing officially to do with Ubuntu I think.

But trying grub1 might be worth a shot.

Let me think about it and gather the necessary commands. In theory, you install Lucid without a bootloader and then add grub1. But let me see what's the easiest way.

PS. You mentioned 9.04 installs OK which means you have a 9.04 cd right? That makes things easier because it has grub1 on it.

---

### Post by slee328 on 2010-05-13
> **darkod said:**
> Ignore that link, it's rubbish. Another person pointed to it and I was shocked to read the amount of wrong information there. One of all, grub2 is more than able to boot 3 or more OSs...

ubuntuguide.org has nothing officially to do with Ubuntu I think.

But trying grub1 might be worth a shot.

Let me think about it and gather the necessary commands. In theory, you install Lucid without a bootloader and then add grub1. But let me see what's the easiest way.

PS. You mentioned 9.04 installs OK which means you have a 9.04 cd right? That makes things easier because it has grub1 on it.

Thanks and I really do not want to yank out the 9GB HDD either.  Although this machine is old, it is just right for my kids to do their research for homework.  I hope to keep up with the latest version of ubuntu on this machine.  I am now 2 versions behind.

---

### Post by darkod on 2010-05-13
I never needed to do this, so I'm not sure I will get it right. If someone else knows how to add grub1 to a system where it was never installed and doesn't have the files existing, please jump in.

1. Start the Lucid installation but on the last screen click Advanced and uncheck the bootloader installation. When that is done you won't be able to boot ubuntu because there is no bootloader.

2. Boot in live mode with the 9.04 cd. If your Lucid root is again /dev/sda1, use the block of 4 commands as earlier to prepare to chroot:

sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys

3. Install the grub1 package (and this is the step I'm not 100% will work):

chroot /mnt apt-get install grub

In theory, if other packages are needed it should install them too.

4. Depending whether installing the 'grub' package will ask you where you want to install grub (you should select the MBR, /dev/sda), execute it yourself if it didn't ask:

chroot /mnt update-grub
chroot /mnt grub-install /dev/sda

PS. 4a. Unmount with:

sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

5. Restart and see where we stand. :)

PPS. UPDATE: Step 4 has changed, I have edited it after finding some more info.

---

### Post by slee328 on 2010-05-14
Darko and the rest of you folks who have been helping out.  We did it and I got GRUB v1 to install and it boots 10.04 without any problem.  As a matter of fact, I am using the newly installed and updated 10.04 Desktop to log in to this forum and type this message.

The only part that I trouble with was step #3:

chroot /mnt apt-get install grub

It did not work.  Instead, I did the following:

chroot /mnt /bin/bash
sudo su -
apt-get install grub
update-grub
grub-install /dev/sda

Then I follow 4a and the rest of the steps and reboot.  Now I can read the GRUB menu by holding the 'Esc' key and later successfully booting into 10.04 repeatedly.  Like I mentioned before, I also updated all the newer packages except for GRUB2 update.

I wonder whether the root cause of this is because of GRUB2 defect or my hardware is too old and can only work with GRUB v1.  If this is a bug, how can I report it and hope the GRUB development team can fix this issue in future releases of GRUB.

Again, I appreciate for all of the help that I receive from all of you out there even for a total stranger that we never meet.  Just with this kind of support efforts received and sharing, it makes using Linux a well worth while experience.  You folks are good people and thank you.

---

### Post by recluce on 2010-05-14
> **slee328 said:**
> 
I wonder whether the root cause of this is because of GRUB2 defect or my hardware is too old and can only work with GRUB v1.  If this is a bug, how can I report it and hope the GRUB development team can fix this issue in future releases of GRUB.

Again, I appreciate for all of the help that I receive from all of you out there even for a total stranger that we never meet.  Just with this kind of support efforts received and sharing, it makes using Linux a well worth while experience.  You folks are good people and thank you.

Glad that you got it working! Please change the tag of your thread to [SOLVED] now.

As to why it did not work? I have no idea, it is only certain that GRUB2 did not like your particular combination of hardware/BIOS components. GRUB2 is great when it works, but being more complex than GRUB1, it has a greater potential for things to go wrong.

Just one reminder: if you used an older Live CD than Jaunty to setup GRUB1, you will not have EXT4 boot support.

---

### Post by slee328 on 2010-05-14
Thanks for the tip on the limitation of file system support for GRUB1.  I think I will hold on to ext4 for the time being because I think in some situation like package installation, it is twice as slow when comparing to ext3.  I cannot think of any good reason to use it yet.  I will change this thread to solved.  Again, thanks to all of you out there in help me.

---

### Post by darkod on 2010-05-14
Glad you got it sorted out. Enjoy it now, you deserved it!!!. :)

---

### Post by Tholley on 2010-05-14
I know this is considered SOLVED, but I have a couple of questions.
 
>  
Then I follow 4a and the rest of the steps and reboot. Now I can read the GRUB menu by holding the 'Esc' key and later successfully booting into 10.04 repeatedly. Like I mentioned before, I also updated all the newer packages except for GRUB2 update.


 
Do you have to hold the Esc key down eveytime you boot in order to access GRUB, or can you just power up and GRUB1 menu appears with your dual boot options?
 
Also, your are saying that when Update Manager runs, you will have to weed thru the updates and un-select GRUB2 everytime?

---

### Post by darkod on 2010-05-14
> **Tholley said:**
> I know this is considered SOLVED, but I have a couple of questions.
 

 
Do you have to hold the Esc key down eveytime you boot in order to access GRUB, or can you just power up and GRUB1 menu appears with your dual boot options?
 
Also, your are saying that when Update Manager runs, you will have to weed thru the updates and un-select GRUB2 everytime?

If I remembered correctly, the OP is not trying to dual boot. Only ubuntu is on the computer. That's why no boot menu is shown and he just wanted to point out that by hitting Esc he can make the menu show (for grub2 it's Shift). If you have only ubuntu the menu doesn't show, ubuntu boots right away which makes sense.

I guess you have to skip the grub2 update every time if you don't want it installed. I never needed to disable some particular package update permanently but maybe there is way to do that.

---

### Post by Tholley on 2010-05-14
Ok... makes sense.
 
I was thinking he had Windows on one of his hardrives, but then remembered the Windows I saw was on his /dev/sdc, which turned out to be a flash drive.

---

### Post by darkod on 2010-05-14
> **Tholley said:**
> Ok... makes sense.
 
I was thinking he had Windows on one of his hardrives, but then remembered the Windows I saw was on his /dev/sdc, which turned out to be a flash drive.

Yes, and that was only "Windows MBR is installed on /dev/sdc", just the fact that the stick has windows type mbr. Of course he didn't have windows installation on the stick.

---

### Post by slee328 on 2010-05-14
Yes, the /dev/sdc is just a flash stick that I used to copy the boot message  checking script to the computer.  It is mostly used among Windows systems.  I did not need to hold on to the 'Esc' key to get to the GRUB boot menu because ubuntu is the only OS on this machine.  So if I do not hold on to the 'Esc' key, the system will boot directly to 10.04.  Regarding the Update Manager, I have to just need to uncheck the GRUB2 update to avoid any unexpected damages to the current GRUB boot loader.

FYI, after I used the newly installed 10.04 on the same machine that it used to run 9.04, I like the new gnome stuff of the UI but overall usage feeling is that it is a little bit sluggish when comparing with 9.04 on the same machine.  My graphics feature setting is only set at normal without the extended graphics features on this machine.

Again, thank you to all of your support.  Open systems work well among a very wide variety of machines.  Even for the weird issue of GRUB2 that I encountered with my older HW, there is a solution to allow me to enjoy the new features of 10.04.  I am grateful for all the technical pointers that I received on this thread by all of you.  Linux rocks!!!

---

### Post by recluce on 2010-05-14
If you remove GRUB2 (using synaptic or apt-get), then the Update manager will not try to update it, obviously....

---

