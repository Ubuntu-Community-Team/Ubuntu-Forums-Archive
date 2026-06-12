---
title: "Grub2 does not recognize Windows 7"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by freeflyerme on 2010-02-28
I've been using Ubuntu for the past few years, and I have finally came across something that requires community help.  Please see my plight and I thank you in advance for what help you may offer.

I have 2 hard drives, first drive (hd0) is for data, second drive (hd1) is for the OS's.  Windows 7 was installed on (hd1) a few months ago and wiped out GRUB.  But today, I decided to go back to Ubuntu.

I performed a fresh install of 9.10 x64 to (hd2), GRUB2 works and finds Ubuntu (both the newly installed x64, and the previous x86 versions), but it does not see Windows 7.  The only goal I have right now, is to make Windows 7 bootable, once again.

My "sudo fdisk -l" (typing manually, so skipping the Blocks)
Device Boot        Id   System
/dev/sdb1          83   Linux    -- where x64 9.10 is
/dev/sdb2           f   W95 Ext'd (LBA)
/dev/sdb5          83   Linux    -- where x86 9.04 is
/dev/sdb6          83   Linux    -- /home
/dev/sdb7          82   Linux Swap / Solaris
/dev/sdb8          87   HPFS/NTFS  -- Windows 7

Things I've tried so far:
1) Automagically finding Windows: sudo update-grub2
2) Reinstalling grub via Live CD (9.10): sudo grub-install --root-directory=/media/(where sdb1 - x64 Ubuntu is) /dev/sdb
3) Forgetting Ubuntu altogether and fixing boot using Windows 7 - bootrec.exe /fixmbr; bootrec.exe /rebuildbcd

Now, number 3 is interesting, I found out that where Windows is installed, /dev/sdb8, is a logical partition, and cannot be made active (bootable).  This led me to try number 4:

4) Updating /etc/grub.d with custom 40_Win7 file, and making it bootable (the GRUB makeactive, GRUB2 parttool command): 
echo "Adding Win 7 to Bootloader" >&2
cat << EOF
menuentry "Windows 7" {
   insmod ntfs
   set root=(hd1,8 )
   parttool (hd1,8 ) boot+
   chainloader +1
}
EOF

When I update grub.cfg after trying #4, it gives me the "not a primary partition" error.  So now I am confused.  Windows 7 was able to boot previously from this very partition, and I don't think installing 9.10 would change a partition type from primary to logical. So, why can't it boot?

More importantly, what can I do to boot Windows 7?  Tinkering is fun, but 8 hours of researching and trying and worn down my patience.  Please help if you are able.  Thank you.

---

### Post by meierfra. on 2010-02-28
Did you deleted or reformat any partitions  when you installed Ubutnu? You don't have any primary NTFS partition.  So I would  guess you are missing the  Window 7 boot files. But before we jump to conclusions  lets have a look at your setup. Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the Boot Info Script and post the RESULTS.txt.

---

### Post by honkeypatrolfbi on 2010-02-28
Boot up using your windows disc. Open up a command prompt and type this:
bootrec /FixMbr
Same thing as fdisk /mbrin older windows.
Read about it at [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record). That's how I fixed my Windows partition after removing a bad ubuntu partition. You may have to reinstall grub but that should get your partition working fine.

---

### Post by meierfra. on 2010-02-28
Deleted (did not contain any useful information)

---

### Post by Yz.MCR on 2010-02-28
Hi There,
I'm not that professional but I have my experience in grub2 stuff ..
I think editing the grub.cfg is a big mistake according to Ubuntu Wiki ..
First make sure that windows 7 boots normally and forget about ubuntu for a sec.
Then boot ur ubuntu 9.10 live CD and do exactly what this page says: 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

note: when u type the command "update-grub" for the first time it won't detect Windows 7
so reboot ur device, log in to ubuntu and type it again. Congrats !! ;)
sorry I wrote too much lol..
if u have any question u r welcome :)

---

### Post by meierfra. on 2010-02-28
Deleted (did not contain any useful information)

---

### Post by freeflyerme on 2010-02-28
Thanks Meierfra, I'll run the script in the morning and post the results.

And, I think you figured my problem perfectly.  I had XP's NTFS on the Primary Partition that is now occupied by 9.10 x64, so I probably lost the boot files when I installed Ubuntu over the XP partition.  To further support your premise, when I do try to boot the Win7 partition, it gives a NTLR missing error, so I'm more convinced by the minute that it's the missing boot files.  Since that's most likely what the problem is, what can I do to recover the Windows7 boot files? 

I'll still post the results.txt, just in case. 
---------------------------------------------------
Also, thanks for your input Yz.MCR.  I had already read up on GRUB2 documentation and knew to update "grub.cfg" via executable config files in "/etc/grub.d", and then running "sudo update-grub2", so no problems there :).

---

### Post by meierfra. on 2010-02-28
> The only goal I have right now, is to make Windows 7 bootable, once again.

Getting Win 7 to boot will be a little bit of work,but should be possible.
Are you currently able to  boot into Ubuntu?  If not I suggest to restore Grub first since some of the steps to fix  Windows 7 will be easiest in Ubuntu.

> I probably lost the boot files when I installed Ubuntu over the XP partition. 
I agree.

> Since that's most likely what the problem is, what can I do to recover the Windows7 boot files? 

Usually you just have to run "startup" repair from the Window 7 DVD, but since  you don't have a primary ntfs partition that will not work. 

But you can still use the Window7 DVD to recover the boot files. Just follow  this howto:

[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)

Step 3 is not always necessary, but RESULTS.txt will tell us if it is.

---

### Post by freeflyerme on 2010-02-28
Please see attached for my Results.txt.

I have followed your guide and completed Step 2 using the manual method.  Grub2 recognizes Windows 7, but when I try to boot, it goes to a black screen and nothing happens. 

I will now do step 3, sincerely hope that it works.

Again, thank you for your help.  If we were to meet in real life, I owe you a drink.
===================
I don't see the attachment, so I'll paste the resluts below.  Sorry it's two posts, because somehow there are "images" (?) in the file, and the forum only allow 8 images per post.

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 394264354 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcdfa46eb

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,851,124,463 1,851,124,401   7 HPFS/NTFS
/dev/sda2    *  1,851,137,820 1,953,520,064   102,382,245  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf749ee27

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   387,021,914   387,021,852  83 Linux
/dev/sdb2         387,021,915 1,250,258,624   863,236,710   f W95 Ext d (LBA)
/dev/sdb5         387,021,978   443,153,024    56,131,047  83 Linux
/dev/sdb6         443,153,088   525,180,914    82,027,827  83 Linux
/dev/sdb7         525,180,978   529,357,814     4,176,837  82 Linux swap / Solaris
/dev/sdb8         529,357,878 1,250,258,624   720,900,747   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        669C8FD09C8F98E7                       ntfs       Storage1                      
/dev/sda2        b3972c5e-bdd4-449b-acee-22c439ff216a   ext3       backup                        
/dev/sdb1        c5d71e17-cb29-4004-b98a-8849fc717a7d   ext4                                     
/dev/sdb5        243fdd72-e1f4-424f-b989-9198800a847b   ext3       ub32                          
/dev/sdb6        8c13df2d-6891-4a4b-b6a1-7cf14efc58da   ext3       ub32h                         
/dev/sdb7        cb8e115d-6231-4648-a555-15d73a1ee285   swap                                     
/dev/sdb8        229454249453F92D                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb6        /home                    ext3       (rw)


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c5d71e17-cb29-4004-b98a-8849fc717a7d

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		c5d71e17-cb29-4004-b98a-8849fc717a7d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		c5d71e17-cb29-4004-b98a-8849fc717a7d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		c5d71e17-cb29-4004-b98a-8849fc717a7d
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		c5d71e17-cb29-4004-b98a-8849fc717a7d
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set c5d71e17-cb29-4004-b98a-8849fc717a7d
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c5d71e17-cb29-4004-b98a-8849fc717a7d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set c5d71e17-cb29-4004-b98a-8849fc717a7d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d ro single 
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
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 243fdd72-e1f4-424f-b989-9198800a847b
	linux /boot/vmlinuz-2.6.28-13-generic root=/dev/sda5 ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 243fdd72-e1f4-424f-b989-9198800a847b
	linux /boot/vmlinuz-2.6.28-13-generic root=/dev/sda5 ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 243fdd72-e1f4-424f-b989-9198800a847b
	linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro quiet splash
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 243fdd72-e1f4-424f-b989-9198800a847b
	linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro single
	initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 243fdd72-e1f4-424f-b989-9198800a847b
	linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash
	initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Windows Vista (loader) (on /dev/sdb8)" {
	insmod ntfs
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 229454249453f92d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/39_Win7 ###
menuentry "Windows 7" {
	insmod ntfs
	set root=(hd1,8)
	parttool (hd1,8) boot+
	chainloader +1
}
### END /etc/grub.d/39_Win7 ###

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
UUID=c5d71e17-cb29-4004-b98a-8849fc717a7d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=8c13df2d-6891-4a4b-b6a1-7cf14efc58da /home           ext3    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=cb8e115d-6231-4648-a555-15d73a1ee285 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
    .7GB: boot/grub/grub.cfg
    .6GB: boot/grub/menu.lst
    .7GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: initrd.img
    .5GB: vmlinuz

---

### Post by freeflyerme on 2010-02-28
Sorry, here is the second part of the post - the menu.lst, etc. on my old 9.04 x32 partitions:
=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

#title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=/dev/sda5 ro  single
#initrd		/boot/initrd.img-2.6.27-11-generic
#
#title		Ubuntu 9.04, kernel 2.6.24-23-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=/dev/sda5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-23-generic
#quiet
#
#title		Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.24-23-generic root=/dev/sda5 ro  single
#initrd		/boot/initrd.img-2.6.24-23-generic
#
#title		Ubuntu 9.04, kernel 2.6.22-14-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.22-14-generic
#quiet
#
#title		Ubuntu 9.04, kernel 2.6.22-14-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro  single
#initrd		/boot/initrd.img-2.6.22-14-generic
#
#title		Ubuntu 9.04, kernel 2.6.20-16-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.20-16-generic
#quiet
#
#title		Ubuntu 9.04, kernel 2.6.20-16-generic (recovery mode)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/sda5 ro  single
#initrd		/boot/initrd.img-2.6.20-16-generic
#
#title		Ubuntu 9.04, memtest86+
#root		(hd0,5)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


========================== sdb5/boot/grub/grub.conf: ==========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu 7.10, kernel 2.6.17-11-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro quiet splash
#initrd		/boot/initrd.img-2.6.17-11-generic
#quiet
#
#title		Ubuntu 7.10, kernel 2.6.17-11-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro single
#initrd		/boot/initrd.img-2.6.17-11-generic
#
#title		Ubuntu 7.10, kernel 2.6.17-10-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-386
#quiet
#
#title		Ubuntu 7.10, kernel 2.6.17-10-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro single
#initrd		/boot/initrd.img-2.6.17-10-386
#
#title		Ubuntu 7.10, kernel 2.6.17-10-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#
#title		Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=243fdd72-e1f4-424f-b989-9198800a847b ro single
#initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
/dev/sda5 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda7
/dev/sda6 /home           ext3    defaults,relatime        0       2
# /dev/sda1
UUID=9E1C8AF01C8AC2AF /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
/dev/sdb1   /media/sdb1 ntfs defaults,locale=en_US,UTF-8 0 0
# /dev/sdb2
# /dev/sdb2   /media/sdb2 ext3 defaults 0 0
# /dev/sda5
#UUID=cb8e115d-6231-4648-a555-15d73a1ee285 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

=================== sdb5: Location of files loaded by Grub: ===================


 201.9GB: boot/grub/grub.conf
 201.8GB: boot/grub/menu.lst
 201.8GB: boot/grub/stage2
 202.5GB: boot/initrd.img-2.6.17-11-generic.bak
 201.1GB: boot/initrd.img-2.6.20-16-generic
 201.2GB: boot/initrd.img-2.6.20-16-generic.bak
 201.3GB: boot/initrd.img-2.6.22-14-generic
 204.0GB: boot/initrd.img-2.6.22-14-generic.bak
 201.4GB: boot/initrd.img-2.6.24-19-generic.bak2
 202.6GB: boot/initrd.img-2.6.24-23-generic
 202.1GB: boot/initrd.img-2.6.24-23-generic.bak
 205.2GB: boot/initrd.img-2.6.27-11-generic
 205.1GB: boot/initrd.img-2.6.28-11-generic
 202.2GB: boot/initrd.img-2.6.28-13-generic
 201.1GB: boot/vmlinuz-2.6.20-16-generic
 201.2GB: boot/vmlinuz-2.6.22-14-generic
 202.0GB: boot/vmlinuz-2.6.24-23-generic
 205.2GB: boot/vmlinuz-2.6.27-11-generic
 201.3GB: boot/vmlinuz-2.6.28-11-generic
 202.2GB: boot/vmlinuz-2.6.28-13-generic
 202.2GB: initrd.img
 205.1GB: initrd.img.old
 202.2GB: vmlinuz
 201.3GB: vmlinuz.old

---

### Post by meierfra. on 2010-02-28
Yes, you need to do Step 3.

---

### Post by freeflyerme on 2010-02-28
YOU ARE AWESOME.  Thank you! The steps I followed allowed me to boot Windows 7 (as well as all existing Ubuntu installs)!  

I would like to recap the issues and solutions, to help me and perhaps others understand what happened.  Could you please provide some comments if you see incorrect info, or if there are critical details to add?
=============================
Initial Setup on Hard Disk:
Primary Partition: 
 - Windows XP
Extended Partition (with logical Partitions)
 - 9.04 x84
 - Windows 7

Action leading to Issue:
Replaced Windows XP on Primary Partition with 9.10 x64.  This caused the boot information necessary for Windows to be removed in the Primary partition.

Symptoms:
GRUB2 does not recognize Windows during "update-grub2".  Manually forcing boot into the Windows partition (via /etc/grub.d/) gives NTLR boot error.

Steps to Resolution:
Followed meiefra's guide at : [http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)

This built the necessary boot information into the Windows logical partition, allowing GRUB2 to chainload the Windows boot.
=============================================
I will now mark this issue as Solved.  Thank you meierfra!

---

### Post by meierfra. on 2010-02-28
> The steps I followed allowed me to boot Windows 7 (as well as all existing Ubuntu installs)! 
Great. Have fun with Windows 7 and Ubuntu.

---

