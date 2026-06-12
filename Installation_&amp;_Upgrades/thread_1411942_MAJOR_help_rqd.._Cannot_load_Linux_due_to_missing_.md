---
title: "MAJOR help rqd.. Cannot load Linux due to missing windows!"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by bazza825 on 2010-02-20
I've been trying to sort this out all day with numerous versions of linux with no success!!  It's driving me insane so bear with me cause there may be some clues to follow....

I wanted to try a dedicated linux media centre. I already had Windows 7, so got a copy of Knoppmyth and installed it. All seemed to go well until i removed the disc and restarted, then the windows boot manager tried to find windows 7 (which i obviously didn't want and had been overwritten) and then bombed out because it couldn't find the files..  i tried all sorts of MBR fixes and then resorted to install XP which removed the boot manager. Next i downloaded MythBunto and installation again went fine, but now upon restarting the pc's now giving errors about the xp files being missing...

How to i get the bloody thing to boot the linux installation....!!??????

Why is my hair slowly jumping off my head...

i'm sooo frustrated at this..

cheers
bazza

---

### Post by MooPi on 2010-02-20
If you didn't install grub at the end of the install process, on the master boot record, it won't find Ubuntu. Did you ?

---

### Post by presence1960 on 2010-02-20
We need way more info than you have provided. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

### Post by bazza825 on 2010-02-20
> **MooPi said:**
> If you didn't install grub at the end of the install process, on the master boot record, it won't find Ubuntu. Did you ?

No i didn't

As per other post, i will do this now  and report back . thanks guys...

---

### Post by bazza825 on 2010-02-20
.

---

### Post by presence1960 on 2010-02-20
> **bazza825 said:**
> Tried this, but getting the response:
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory



really doing me head in now.. nothings going right today :(

download the boot info script from the link in my signature

move the downloaded file to the desktop.

Now run the command from terminal

---

### Post by bazza825 on 2010-02-20
> **bazza825 said:**
> Tried this, but getting the response:
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory



really doing me head in now.. nothings going right today :(


Sorry, it's late for me and i've had a few lol

I've run the script as per your post and here's the result... hope it makes sense.. please excuse my obvious dimness... i'm so used to windows & mac 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5936904c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,511,889   300,511,827  83 Linux
/dev/sda2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sda5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x614540e2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbe26b10

Partition  Boot         Start           End          Size  Id System

/dev/sdc2    *         16,065   976,768,064   976,752,000   5 Extended
/dev/sdc5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ecdc8229-e8e3-4176-a80b-e2588520dd2e   ext4                                     
/dev/sda5        f17a53d9-37cb-4769-842f-affe78249b04   swap                                     
/dev/sdb1        00B81968B8195D8A                       ntfs       Large Store                   
/dev/sdc5        5837EAA3ECD08120                       ntfs       Large Store2                  

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set ecdc8229-e8e3-4176-a80b-e2588520dd2e
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ecdc8229-e8e3-4176-a80b-e2588520dd2e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ecdc8229-e8e3-4176-a80b-e2588520dd2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ecdc8229-e8e3-4176-a80b-e2588520dd2e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ecdc8229-e8e3-4176-a80b-e2588520dd2e ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 00b81968b8195d8a
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ecdc8229-e8e3-4176-a80b-e2588520dd2e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f17a53d9-37cb-4769-842f-affe78249b04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   9.2GB: boot/grub/core.img
   9.2GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .4GB: initrd.img
    .6GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(2)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by bazza825 on 2010-02-21
any ideas?

---

### Post by presence1960 on 2010-02-21
Your windows will never boot because you have a mix of windows 7 & XP boot files on your XP partition. It is looking for windows 7 to boot. XP is on sdb (500 GB) disk. To repair the boot function you will need the XP install CD. Go into BIOS and set the disk with XP (sdb) as first to boot in the hard disk boot order. This is critical as windows always writes to the first disk to boot. Save changes to CMOS and boot off the XP install CD. Follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for XP. When completed boot without the CD and make sure XP boots.

If XP boots go into BIOS and set sda (160 GB) disk as first to boot in the hard disk boot order. Save changes to CMOS & continue booting into ubuntu. sda has GRUB2 on it's MBR and it looks ok. You must have this disk boot first so GRUB can take over. Once the desktop loads open a terminal and run ```
sudo update-grub
```This will refresh your grub menu and add XP to it. You should now be good to go.

---

### Post by bazza825 on 2010-02-21
Many thanks for that. I've give that a try..

I suspected one of the other drives as i've just disconnected them in the bios and then the single drive booted into MythBunto...

I now have other problems as described in my other post...

So i'll get Mythbunto working with my tv cards (if it ever happens) and then once that's sorted will do as you said..

cheers
bazza

---

