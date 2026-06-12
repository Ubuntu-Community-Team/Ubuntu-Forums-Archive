---
title: "Grub2 mania"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by neelsonwheels on 2010-10-31
The short back story: I've got a new HP dv6. It's got Win7 on the internal hard drive (like 3 partitions for all the HP bloatware). I've got a 1TB external HD that I want to install Linux on. I attempted Kubuntu 10.10 no dice. I'm currently wrestling with Mint 9 KDE, and no dice as well.

Yada, yada, yada... I've narrowed it down to grub2 issues. [This post]("http://ubuntuforums.org/showthread.php?t=1581099") has been the most helpful thus far. After I follow the Chroot steps, when I reboot I get a device not found error with grub rescue prompt.  Now the weird thing is when I power down, and power back up the Grub menu is there with all my OSs including Win7 and I can boot to all of them. This happens for both Kubuntu and Mint. WTF! 

My issues seem to be related to these bugs [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435") and [here]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996"), however my symptoms just don't make sense. What could be that different b/w restarting and powering down. 

Can anyone provide insight? I'm stumped.

---

### Post by oldfred on 2010-10-31
I have heard of the opposite problem where warm boot working and cold boot does not. Which may be power related.

Yours sounds like a drive order issue, which I have had with USB flash drive boots where the drives were numbered above the hard drives, the set root was the wrong drive and the grub search by UUID stopped working as the flash drive was located above blank drive letters.

Run this just to confirm drives and locations of grub.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by neelsonwheels on 2010-10-31
Here it is. Any fresh ideas would be greatly appreciated! 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 453411200 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   581,984,255   581,574,656   7 HPFS/NTFS
/dev/sda3         581,984,256   624,928,767    42,944,512   7 HPFS/NTFS
/dev/sda4         624,928,768   625,140,399       211,632   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000194399744 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953504687 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   509,560,562   509,558,515  83 Linux
/dev/sdb2       1,024,015,230 1,953,503,999   929,488,770   7 HPFS/NTFS
/dev/sdb3         509,560,830   530,157,567    20,596,738   5 Extended
/dev/sdb5         509,560,832   530,157,567    20,596,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        540C73820C735DC4                       ntfs       SYSTEM                        
/dev/sda2        D44E8D0E4E8CEB16                       ntfs                                     
/dev/sda3        00CA055ECA0550F8                       ntfs       RECOVERY                      
/dev/sda4        C809-BF46                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ac0df2d9-29f6-4182-bdf0-ab43575e5215   ext4                                     
/dev/sdb2        64B219703A114706                       ntfs       Windows                       
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        d053f573-8816-467f-b49c-50c05176a046   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
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

### BEGIN /etc/grub.d/07_mintkde_theme ###
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
insmod jpeg
if background_image /boot/grub/isadorablue.jpeg ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/07_mintkde_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-23-generic (/dev/sdb1)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=ac0df2d9-29f6-4182-bdf0-ab43575e5215 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry "Linux Mint 9, 2.6.32-23-generic (/dev/sdb1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=ac0df2d9-29f6-4182-bdf0-ab43575e5215 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb1)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ac0df2d9-29f6-4182-bdf0-ab43575e5215 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ac0df2d9-29f6-4182-bdf0-ab43575e5215 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ac0df2d9-29f6-4182-bdf0-ab43575e5215
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set d44e8d0e4e8ceb16
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 00ca055eca0550f8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ac0df2d9-29f6-4182-bdf0-ab43575e5215 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d053f573-8816-467f-b49c-50c05176a046 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 232.0GB: boot/grub/core.img
 240.6GB: boot/grub/grub.cfg
 232.1GB: boot/initrd.img-2.6.32-21-generic
 232.0GB: boot/initrd.img-2.6.32-23-generic
 232.0GB: boot/vmlinuz-2.6.32-21-generic
 232.0GB: boot/vmlinuz-2.6.32-23-generic
 232.1GB: initrd.img
 232.1GB: initrd.img.old
 232.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by oldfred on 2010-10-31
You do have grub2 installed in each drive but the one in sda points to the windows recovery partition which also has parts of grub installed. That must be the one that is not working.

It looks like the grub2 in sdb, the 1TB drive should boot the install in sdb1, Mint.

This looks like the windows recovery or your system recovery partition:

sda1: ________________
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector [/COLOR]of sda1 and 
                       looks at sector 453411200 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]

There are two issues. You have grub in the boot sector and all windows NTFS partitions have to have a windows boot sector. You also have /boot grub folder, but windows has a /Boot/BCD. 

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

If you boot from BIOS the 1TB drive grub should give you a choice to boot windows or Ubuntu. If you have windows boot loader in sda then you can boot sda from BIOS in an emergency.
You probably have to run this in Mint, after the windows fixes.
```
sudo update-grub
```

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by neelsonwheels on 2010-11-01
So the first time I followed your instructions they worked. However my system was booting directly into Windows (maybe that was the intention, but not what I wanted).

Then I tried a whole bunch of different things very unsystematically. As you might imagine nothing worked.

Now I must stop for tonight. I'm going to think on it for a coupla days, but I might just wipe Windows all together. I never really use it, and the only reason I was wanting to keep it was to prove I could make dual booting work on an external HD.

Machine won for now, but I think I'll be back...

---

### Post by oldfred on 2010-11-01
If in BIOS you boot the 320GB, you should boot directly into windows.

If you have grub in the 1TB drive's MBR, it should boot grub and give you a choice of Ubuntu or windows.

If you have modified things you may want to rerun the boot info script, so we can give specific instructions.

---

### Post by neelsonwheels on 2010-11-02
Well after a new day, I'm thinking back to your original comment... > I have heard of the opposite problem where warm boot working and cold boot does not. Which may be power related.I think my new CPU has power issues.  About a month ago (before I attempted to put *ubuntu on), my RJ-45 jack quit working. Called HP (which surprisingly was helpful), and ultimately had me flash an updated BIOS and all was well. Said there was static on the motherboard (don't really know how they know unless other CPUs are having the same problem). 

So fast forward to last night, and my internet jack started flaking out again (and potentially my DVD drive along with the original warm/cold boot symptoms reemerging).

I think I might reimage my internal HD and start over. I'm afraid I'm having hardware issues (unrelated to *ubuntu), but I don't know how well HP will respond to me messing with things like that.

Thoughts?

---

### Post by oldfred on 2010-11-02
Is your USB drive powered separately or from the USB port?

I have heard that portables do not have much power output on the USB ports and that can cause issues for USB devices that use a lot of power (but still within official USB specs.)

---

### Post by neelsonwheels on 2010-11-02
The TB drive has it's own power supply.

---

