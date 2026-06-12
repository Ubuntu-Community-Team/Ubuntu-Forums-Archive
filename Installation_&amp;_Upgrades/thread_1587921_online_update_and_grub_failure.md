---
title: "online update and grub failure"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Warlok22 on 2010-10-04
Hello All,

My name is Andrei, i'm from Romania and im No.1 Begginer in linux,This is my problem...and hope to post well here.
a few months ago i found on pendrivelinux kubuntu 9.10 usb live...instaled and played with it on an memory stick of 2 gb, las week i got my 3rd hdd of 80 gb just to play with linux, i've disconected the first 2 hdd with windows instaled on one of them and instaled from that live stick on the 3rd hdd the permanent version of kubuntu 9.10, booting between  linux hdd3 and windows hdd1  was done using bios hdd select. last night i saw an update icon on linux to update to ubuntu 10.04 lts online... so i did but unfortunately i forgot to disconnect de first 2 hdd :(, it tooked me 1 hour to download and instal...at the end it asket for reboot .
Resoults :

1. after first reboot with all3 hdd conected it crashed asking for rescue/live cd and with the command GNU_GRUB_ 
i've restarted the pc and now i have 5 or 6 choices. i went for the higher number of ubuntu  with (rescue) at the end and he downloaded the bad files and installed them corectly.
2. the last choice is boot with windows xp ...if i select that ... i get an black screen .


I need you're help with this one ... from what i've read on this forum ...i understand that this is an MBR problem.... what and how do i proceed from here. the ubuntu is fully functional...but windos isn't.

thanks in advance !

---

### Post by Warlok22 on 2010-10-04
Resoults :

1. after first reboot with all3 hdd conected it crashed asking for rescue/live cd and with the command GRUB_ RESCUE_

This appears only when i try to boot directly from the hdd 1 or 0 where i have  windows installed

thanks in advance ![/QUOTE]

---

### Post by andrewthomas on 2010-10-04
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

just fix the windows mbr and then use the disk that ubuntu if on to boot off of.

make sure that you update-grub after fixing your windows

---

### Post by Warlok22 on 2010-10-04
> **andrewthomas said:**
> [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

just fix the windows mbr and then use the disk that ubuntu if on to boot off of.

make sure that you update-grub after fixing your windows

I tryd for some time now but it doesn't work, i have read all the post here regarding grub failure, mbr and dual boot...i've tryd on mi own risk som command but they dont work...

1.if i disconnect the hdd with ubuntu 10.04 lts remaining only windows hdd  and set boot from cd-rom to repair windows it say's :

```
verifying DMI pool Data ........................
error: no such device: 3cff2312-0a4d-04783-0a683-6eb1f8fb2d48.
grub rescue>
```

why doesnt it boot from cd? 

2.with all hdd connected it doesnt boot from cd...it goes directly to dual boot and say's:

```
ubuntu, with linux 2.6.32-25-generic
ubuntu, with linux 2.6.32-25-generic (recovery mode)
ubuntu, with linux 2.6.31-22-generic
ubuntu, with linux 2.6.31-22-generic ( recovery mode)
memory test (memtest86+)
memory test ( memtest86+, serial console 115200)
Microsoft windows xp proffesional (on /dev/sda1)

press E to edit comand before booting
press c for a  command-line - pressing c gives me  "   grub>   "
```

pressing E on windows selection replyes this :

```
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6c8857d788579f00
drivemap -s (hd0) ${root}
chain loader +1
```

pressing E on ubuntu linux 2.6.32-25-generic :

```
recordfail
insmod ext2
set root='(/dev/sdc,1)'
search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2\d48
linux /boot/vmlinuz-2.6.32-25-generic root=uuid=3cff2312-0a4d-4783-a\683-6eb1f8fb2d48 ro     quiet splash
initrd /boot/initrd.img-2.6.32-25-generic
```

history : 
i had kubuntu 9.04 usb live, instaled it on hdd 3 with hdd 1 and 2 disconnected
after a while it satyz new version.  i sayd yes and forgot to disconnect hdd 1 and 2 ...after update ...this is what happend.

i really need help with this one

---

### Post by andrewthomas on 2010-10-04
If you want to boot off the cd you need to change the boot order in BIOS.

---

### Post by Warlok22 on 2010-10-04
> **andrewthomas said:**
> If you want to boot off the cd you need to change the boot order in BIOS.

Thank you for the short timed answer. 
BUT : i've changed the, instead of booting from cd it goes directly to dual boot, i've managed to boot from that memorystick with kubuntu 9.04 live via USB ofcourse.

Can someone help ?

---

### Post by Warlok22 on 2010-10-06
Still need help ,

when i boot only with the hdd with windows it says that  

verifying DMI pool Data ........................ error: no such device: 3cff2312-0a4d-04783-0a683-6eb1f8fb2d48. grub rescue>

even if i try from bios to boot from cd and dissable hdd from bootl ist...stillgives me that !

HELP !

three days ago i was prehistoric with linux/kubuntu.... but now  using this forum i managed to install  assus xonar d2  audio device,,,  pulse audio...sett it right to work with youtube player..etc... still learning..but i really need mi windows stuff back !

---

### Post by Warlok22 on 2010-10-07
bunp!

---

### Post by Warlok22 on 2010-10-07
After running :

```
sudo bash /downloads/boot_info_script055.sh 
```

this are the results :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /media/sdc1/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 111298383.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   111,298,319   111,298,257   7 HPFS/NTFS
/dev/sda3         111,298,383   519,847,334   408,548,952   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   976,768,064   976,752,000   f W95 Ext d (LBA)
/dev/sdb5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdc2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdc5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6C8857D788579F00                       ntfs                                     
/dev/sda3        CE14701F14700CA9                       ntfs       Torr                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        A01426C614269F72                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3cff2312-0a4d-4783-a683-6eb1f8fb2d48   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        48b22117-abf9-4a93-abbf-817f67810f9b   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,1)'
search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
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
set root='(/dev/sdc,1)'
search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3cff2312-0a4d-4783-a683-6eb1f8fb2d48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3cff2312-0a4d-4783-a683-6eb1f8fb2d48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=3cff2312-0a4d-4783-a683-6eb1f8fb2d48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=3cff2312-0a4d-4783-a683-6eb1f8fb2d48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(/dev/sdc,1)'
    search --no-floppy --fs-uuid --set 3cff2312-0a4d-4783-a683-6eb1f8fb2d48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6c8857d788579f00
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3cff2312-0a4d-4783-a683-6eb1f8fb2d48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48b22117-abf9-4a93-abbf-817f67810f9b none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.31-22-generic
   1.6GB: boot/initrd.img-2.6.32-25-generic
    .9GB: boot/vmlinuz-2.6.31-22-generic
   1.5GB: boot/vmlinuz-2.6.32-25-generic
   1.6GB: initrd.img
   1.6GB: initrd.img.old
   1.5GB: vmlinuz
    .9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

what if donne so far.

found an post here on this forum with the instructions to install grub in the corect partition...and so far from what i seen i've instaled grub 2 ...second grub...to the corect hdd sdc1 ....mi windows is instaled in sda...i need it to boot.

---

### Post by drs305 on 2010-10-07
Welcome Warlok22 !

Disclaimer: I am not a Windows user.

Both Grub2 and Windows have files written to an MBR (Grub2 to sda, Windows to sdb) but neither is pointing to the correct files.

Restore the Windows MBR on sda so that Windows will boot if sdc is not installed. You can use a Windows repair disk to do this or from an Ubuntu LiveCD. Then we will make sure Grub is installed to sdc

```
sudo apt-get install lilo  # You don't want a full install in the bootloader so ignore the warnings
sudo lilo -M /dev/sda mbr
sudo mount /dev/sdc1 /mnt
sudo grub-install /dev/sdc

```

Set the BIOS to look for sdc first, then sda. If sdc is not connected, Windows should boot. If sdc is connected, the BIOS should find that drive first in BIOS and find the Grub sdc MBR instructions.

---

### Post by Warlok22 on 2010-10-07
hy and thx for sort timed answer... 

question.... : now im using the kubuntu 10.04...can i run this commands directly fom konsole?

```
sudo apt-get install lilo  # You don't want a full install in the bootloader so ignore the warnings sudo lilo -M /dev/sda mbr sudo mount /dev/sdc1 /mnt sudo grub-install /dev/sdc
```
to do this i leave the boot order from bios as is ...meaning first boot is hdd with windos, second is hdd storage,,, 3rd is sdc...linux dedicated hdd ?

or 

change the boot order from bios..and put sdc hdd 3 first boot ..and windows second?
i'm askyng this becouse... i would prefer to boot between windows andl inux not thru grub..but thru bios...meaning that ...the computer should boot directly to windows as it was dooing ti'll the kubuntu update... and just connect the hdd with linux  when i want to use it.

---

### Post by drs305 on 2010-10-07
Yes, you can use konsole. Any linux terminal will work. The lilo command just fixes the MBR on sda so Windows can use it.

The BIOS boot order would be sdc, sda, sdb.

It will try to boot sdc (your external Ubuntu). If it doesn't find that, it will boot sda and find your Windows install.

---

### Post by Warlok22 on 2010-10-07
i'm now typing from windows...

thank u verry much for the help given ! ... i succeded on solving this problem...

as a mather of now..i promise that i will try to learn linux ! 

last 4 days i've tryied ..every thing this forum says and worked!

comparisson 

for the moment... i'd say that linux gives 110 % potential on browsing internet..downloads and apps !

problem solved !!!\

---

