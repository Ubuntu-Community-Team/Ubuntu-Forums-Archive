---
title: "help ..."
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by fishstick41 on 2010-10-06
Hi everyone i finely got myself a usb 320 gb HD. ubuntu installed it self on to the HD but every time  i try to get on ubuntu i get a grub error ... is it because im using a usb HD ?



update: 

this is what it is saying

GRUB LOADING...
ERROR: UNKNOWN FILE SYSTEM
GRUB RESCUE>_ 


please help me with this if you have any questions please ask...

---

### Post by Rubi1200 on 2010-10-07
Hi and welcome to the forums :)

I assume the USB drive is an external device?

What is on your internal drive?

From an Ubuntu CD in live mode please post the results of the boot-script linked at the bottom of my post.

I suspect there might be an issue with the Ubuntu bootloader; the results of the script should confirm this and then we can advise you further.

Thanks.

---

### Post by fishstick41 on 2010-10-07
hey thanks for the reply I'm still new Ubuntu and i don't know how to get the boot-script sorry for my noobish ways :(. my internal HD is 250, and yes the usb is a external drive it is 320. 





thanks 


~Fishy~

---

### Post by Rubi1200 on 2010-10-07
> **fishstick41 said:**
> hey thanks for the reply I'm still new Ubuntu and i don't know how to get the boot-script sorry for my noobish ways :(. my internal HD is 250, and yes the usb is a external drive it is 320. 





thanks 


~Fishy~

If you have an Ubuntu CD or USB, boot the computer and choose to try Ubuntu in live mode, not install it.

Then, assuming you are connected to the Internet, click on the link I mentioned and follow the instructions.

Best thing to do is download to the Desktop and run the command given in the link.

Post the results back here from the LiveCD (otherwise you will lose the script when you reboot).

We can then take a look and help you sort this out.

One other thing; have you tried changing the boot order in BIOS to make the external drive the first thing to boot?

---

### Post by fishstick41 on 2010-10-07
im sooo lost ... sorry what was the site you talked about?

---

### Post by Warlok22 on 2010-10-07
here you go just click it 

__________________
				Bootscript courtesy of meierfra.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

download it to you're live linux desktop... the you have to run it

after download use this 

 pres Alt + F2  ..then type Konsole and press enter

then folloow this :

 sudo bash [path/to/the/download_folder]/boot_info_script*.sh  For example if you downloaded the file to the desktop, use          sudo bash ~/Desktop/boot_info_script*.sh where ~ equals more or less user name/home/desktop

after run  it creats an TXT file...open, copy everything in there ..and paste it here using  # for code

---

### Post by fishstick41 on 2010-10-07
ummm i think i got it sorry about that. here is what i got. thanks for the help yall =]

---

### Post by Warlok22 on 2010-10-07
with any luck someone will tell you what to do 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd712d712

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31800fde

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   334,071,674   334,071,612   7 HPFS/NTFS
/dev/sdb2         334,071,675   625,137,344   291,065,670   5 Extended
/dev/sdb5         334,071,738   613,233,179   279,161,442  83 Linux
/dev/sdb6         613,233,243   625,137,344    11,904,102  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BC70951A7094DD08                       ntfs                                     
/dev/sdb1        6CB4C18CB4C158EA                       ntfs                                     
/dev/sdb5        cc0e738d-47ae-4513-8c3a-ac2602ab61ba   ext4                                     
/dev/sdb6        a8b36643-e0cd-4e47-8b25-f3d7c29ce401   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb5        /media/cc0e738d-47ae-4513-8c3a-ac2602ab61ba ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1        /media/BC70951A7094DD08  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer
C:\wubildr.mbr = "Ubuntu"

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set cc0e738d-47ae-4513-8c3a-ac2602ab61ba
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
    search --no-floppy --fs-uuid --set cc0e738d-47ae-4513-8c3a-ac2602ab61ba
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cc0e738d-47ae-4513-8c3a-ac2602ab61ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set cc0e738d-47ae-4513-8c3a-ac2602ab61ba
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cc0e738d-47ae-4513-8c3a-ac2602ab61ba ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=cc0e738d-47ae-4513-8c3a-ac2602ab61ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a8b36643-e0cd-4e47-8b25-f3d7c29ce401 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 176.7GB: boot/grub/core.img
 176.6GB: boot/grub/grub.cfg
 171.4GB: boot/initrd.img-2.6.31-14-generic
 171.3GB: boot/vmlinuz-2.6.31-14-generic
 171.4GB: initrd.img
 171.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by Rubi1200 on 2010-10-07
Thanks go to Warlok22 for the additional help and posting the results the way we need to see it.

Ok, so you seem to have a bit of a muddle here.

You have Wubi installed both on sda and sdb as well as what looks like a regular install of Ubuntu 9.10

This is not a good way to go about things.

So, you need to decide where and how to install Ubuntu. Wubi is not really intended for anything but to give Ubuntu a try.

I suggest you install Ubuntu to the drive and dual-boot with Windows.

Tell us what _you_ want and then we can proceed.

By the way, I assume you can boot into Windows normally?

---

### Post by fishstick41 on 2010-10-07
hey thanks for the reply. i don't really want to dual boot on my main HD because its not my.. but i do have a 40 GB IDE HD ..





EDIT: sorry about that and yes i do boot normally into windows.

---

### Post by Warlok22 on 2010-10-07
my personal advice :

go to pendrivelinux... or where you've downloaded your ubuntu/kubuntu...etc... mount the image and :

1 create first partition ...let's say  30gb and leave the rest in secont partition
2 the external hdd is used as an memory stick so you can step 3
3 create an live version of the linux you want to try/use/see
4 when finished you will be asked  what you want to  start from 

    a. run ubuntu non-persistant
    b. run ubuntu persistant
    c. install ubuntu
    d. memtest
    e. boot first hdd
this is where that first partition comes in becouse you will use allways  version B with persistamt settings. Still live one not installed but it will remember all you're settings and apps installled  and ALSO you'll benefit from the rest of the portable hdd for windows files /mp3/movies/software...etc.... Since Windows doesn't recognize linux partitions.

Hope that my advice is the correct one... so don't do anything until an senior user of this forum will give his OK !  on mi advice or refrase to make it simple !

GL an HF !

---

### Post by fishstick41 on 2010-10-07
now that may be idea =\ the only really reason i want to install ubuntu is to scan or recover my main HD when it got a vises or it crashes ..

---

### Post by Warlok22 on 2010-10-08
Then if iti s oky with you please use the forum function called " thread tools" and mark  the post as Solved !

GoodLuck !

---

### Post by Rubi1200 on 2010-10-08
> **fishstick41 said:**
> now that may be idea =\ the only really reason i want to install ubuntu is to scan or recover my main HD when it got a vises or it crashes ..
To be quite honest, if this is your idea then your reasoning is flawed. It is a waste of time to install an operating system for the reasons you mention.

What **should** you do?

Have an Ubuntu CD handy; download and burn to disc one of the many system rescue CDs; have a backup plan; try not to get viruses in the first place!

[http://www.livecdlist.com/purpose/rescue](http://www.livecdlist.com/purpose/rescue)

[www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/]("http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/")

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by fishstick41 on 2010-10-08
i don't install virus to this computer its my family=\ anyways I'm just trying to play around on the computer soo if i needed to do i know how to do it =\

---

