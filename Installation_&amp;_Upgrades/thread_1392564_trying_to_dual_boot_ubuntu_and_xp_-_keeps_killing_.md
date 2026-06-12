---
title: "trying to dual boot ubuntu and xp - keeps killing my xp install..."
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Jonasan Cope on 2010-01-28
hey folks, a little help please.....
 
have been trying to setup a dual boot system with ubuntu and XP running side by side on my Thinkpad T41.
 
tried it a few times and always causes the same problem.
 
i have 40 gig HDD, on which i create a 13 gig NTFS partition and leave the rest as free space. then install XP on the NTFS partition. no problems.
 
then i boot from the ubuntu disk (9.10 Karmic) and install using the "use free space" option at the partition section. ubuntu installs ok, and boots fine from GRUB 2.0. 
 
BUT when i select the XP option from GRUB's list, it starts to boot XP, i get the standard XP loading screen for three seconds and then it crashes to a blue screen critical problem, and restarts the system.
 
when i then boot from the xp cd and go into recovery mode CHKDSK will not recognise the disk, and DISKPART shows one HDD at 35 gig which it cannot access.
 
this means i cant run FIXBOOT and get my xp install running again.
 
every time i do this process it produces the same problem. tried at first with xp installed on whole HDD, and reducing the xp partition size. killed XP. then tried ubuntu first and xp second - but this caused the same inaccessible disk problem - xp would not recognise the partitions and would not install. so i slipstreamed my XP install disk to SP2 hoping this would make it recognise the partitions, but no luck there. so had to format all and repartition the 13 gig NTFS for xp. installed xp again without difficulty but ubuntu install killed my xp in the same way.
 
stuck now... any suggestions?? any help would be much appreciated. cheers

---

### Post by Brett.Townsend on 2010-01-28
I would recommend running a dft on your hard drive that would be a good starting place and then go from there.

---

### Post by Jonasan Cope on 2010-01-28
alright will try a fukitsu one now... cheers

---

### Post by Jonasan Cope on 2010-01-28
ok downloading bootable cd with dft on (no A drive). while im waiting, sorted out the boot_info_script (thanks darko). here is the output of the results.txt file.
 
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       26626256 sectors, but according to the info from 
                       fdisk, it has 40692581 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
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
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    40,692,644    40,692,582   7 HPFS/NTFS
/dev/sda2          40,692,645    78,140,159    37,447,515   5 Extended
/dev/sda5          40,692,708    76,485,464    35,792,757  83 Linux
/dev/sda6          76,485,528    78,140,159     1,654,632  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        D82447CF2447AF76                       ntfs                                     
/dev/sda5        748f6c7b-f601-49e5-9a7a-1c4a500a1441   ext4                                     
/dev/sda6        edf245c9-9647-404c-a76b-0b8a275192e9   swap                                     
============================ "mount | grep ^/  output: ===========================
Device           Mount Point      Type       Options
/dev/sda5        /                ext4       (rw,errors=remount-ro)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
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
search --no-floppy --fs-uuid --set 748f6c7b-f601-49e5-9a7a-1c4a500a1441
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd0,5)
 search --no-floppy --fs-uuid --set 748f6c7b-f601-49e5-9a7a-1c4a500a1441
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=748f6c7b-f601-49e5-9a7a-1c4a500a1441 ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd0,5)
 search --no-floppy --fs-uuid --set 748f6c7b-f601-49e5-9a7a-1c4a500a1441
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=748f6c7b-f601-49e5-9a7a-1c4a500a1441 ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
 insmod ntfs
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set d82447cf2447af76
 drivemap -s (hd0) ${root}
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=748f6c7b-f601-49e5-9a7a-1c4a500a1441 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=edf245c9-9647-404c-a76b-0b8a275192e9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sda5: Location of files loaded by Grub: ===================

  20.8GB: boot/grub/core.img
  20.8GB: boot/grub/grub.cfg
  20.8GB: boot/initrd.img-2.6.31-14-generic
  20.8GB: boot/vmlinuz-2.6.31-14-generic
  20.8GB: initrd.img
  20.8GB: vmlinuz

 
---------
 
dont know if that will help anyone understand my issue.
 
will report on the results of the DFT. cheers

---

### Post by darkod on 2010-01-28
Not sure if this can be the problem but look what it says under sda1:
File system:       ntfs
    Boot sector type:  Windows XP
    [COLOR=Red]Boot sector info:  According to the info in the boot sector, sda1 has 
                       26626256 sectors, but according to the info from 
                       fdisk, it has 40692581 sectors.[/COLOR]
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Two different sizes of the partition are reported by different programs. I wonder if Gparted could sort out something like this. I guess it would be better not to use the ubuntu install, instead boot with ubuntu cd, Try Ubuntu option. Open Gparted and you might notice symbol like triangle next to /dev/sda1. If you right-click on /dev/sda1 there will be Check option in the menu.
Run the check and see what it says. Not sure if it will detect any problem or if it can repair it if detected.
If you can't boot XP even in Safe Mode, I'm not sure how to run a repair process with windows tools.

---

### Post by Jonasan Cope on 2010-01-28
cheers darko, running comprehensive disk fitness test now, should be another 15 minutes.
 
i spotted that problem in the results file myself, aprreciate the input. will try what you suggest after the dft is done. seems remincent of the xp install program not recognising the partitions and just giving the total capacity. we'll see what dft and gparted have to say... will post results

---

### Post by Jonasan Cope on 2010-01-28
ok so the comprehensive disk fitness test was a success - no errors found at all. this was a fujitsu test, which is correct for my HDD so i'm pretty confident that the HDD is in good nick.
 
gparted.... no triangle symbol, checked each partition (which are all detailed correctly) with out any errors. tried to reboot the system once more but still getting same issue on xp boot.
 
going to try googling the BSOD error message (0x0000007b) and see if i can come up with a solution that way. open to suggestions though.... thanks

---

### Post by Jonasan Cope on 2010-01-28
well BSOD 0x0000007b searching lead me to try and repair the windows install using the xp boot disk. which shows up "setup cannot access this disk", and then crashes to another BSOD. also found suggestion to manually repair system registry. but repair mode from th xp boot disk wont give me access to the disk at all in the same way.
 
dosent leave me with much. as the disk is completely inaccessible to windows right now i dont see any other option but formating and beginning again...? but if i do that and then try to install ubuntu in the same way i fear the same problem once again...?
 
any bright ideas before i take the plunge and reinstall..? cheers

---

### Post by Jonasan Cope on 2010-01-28
well i managed it. you see i am using a Thinkpad which had a preinstalled recovery partition. when i decided to dual boot with ubuntu i wiped the HDD including the recovery partition, so i could use the whole 40 gig. 
 
and now i know...... the reason for the XP not booting is confusion in my partition tables caused by a BIOS setting which was protecting an area of my HDD that no longer contained the recovery partition. 
 
my bios was setup to "hide the IBM predesktop area from the OS" - that is, dont let anything access the recovery partition on the HDD. when i installed ubuntu it appears that the computer got confused by this partition geometry because of the BIOS setting reserving the Hidden Partition Area. 
 
when i found this i figured i'd have to disable the BIOS setting so the area could be reclaimed and reinstall everything. happy to do that if it works. but it turns out that the area had been wiped and reinstalled to properly, just turning the BIOS setting off allowed proper access to that area of my HDD, and now everything works! just a flick of a BIOS switch.
 
figured this out from some reading about recovery partitions causing problems on linux installs, and then this from think wiki.org -->
 
If the Hidden Partition Area is enabled in the BIOS (mode set to "Normal"), Linux may get confused about the correct partition geometry. The exact reason is not clear, but apparently a [[COLOR=blue][COLOR=blue !important][FONT=sans-serif][COLOR=blue !important][FONT=sans-serif]Linux [/FONT][/FONT][/COLOR][FONT=sans-serif][COLOR=blue !important][FONT=sans-serif]installation[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://ubuntuforums.org/#") may overwrite/damage the HPA, which then causes problems during boot. The problem may also be caused by changing the BIOS mode of the HPA after the installation of Linux. 

Reported symptoms are: 
[LIST]
[*]Linux fails to boot: On boot, Grub displays *Error 17*; Lilo shows *L 99 99 99 99 ...*
[*][[COLOR=blue][COLOR=blue !important][FONT=sans-serif][COLOR=blue !important][FONT=sans-serif]Windows [/FONT][/FONT][/COLOR][FONT=sans-serif][COLOR=blue !important][FONT=sans-serif]XP[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://ubuntuforums.org/#") bluescreens during booting, with the message *STOP [....] UNMOUNTABLE_BOOT_VOLUME*
[/LIST]See for example this bug report from Ubuntu: [Bug #25451: Thinkpad BIOS can't hide the Predesktop area]("https://bugs.launchpad.net/ubuntu/+bug/25451") 
This problem can apparently be fixed by setting the HPA mode to "Disable" in the BIOS setup. 
 
----
 
I'm so glad, was starting to contemplate the thought of choosing one OS over the other. now i have a multifunctional system - ubuntu for almost everything, and XP for gaming.
 
Thanks to everyone on here for their help. Maybe this fix will help someone else out, seems to be a pretty common thing to problems getting a dual boot up and running.
 
be well

---

### Post by Brett.Townsend on 2010-01-28
Congrats on getting it working. Those hidden partitions can sometimes be a pain.

---

