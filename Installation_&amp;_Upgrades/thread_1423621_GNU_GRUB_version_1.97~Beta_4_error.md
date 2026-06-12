---
title: "GNU GRUB version 1.97~Beta 4 error"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by sdeannas on 2010-03-06
I think the pc updated, or at least that is the only thing I can figure.  Anyhow, pc froze so I reboot system.  I have dual setup, after choosing Ubuntu, I receive GNU GRUB version 1.97~Beta 4 error.  I am also told to press TAB for further commands, but none of the commands seem to do anything.

---

### Post by paulemony on 2010-03-08
Same deal, update manager prompted install updates & reboot but now Ubuntu doesn't boot (so have to use Windows to post this message....)

---

### Post by bcbc on 2010-03-08
If you're using wubi (installed under windows), see [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by presence1960 on 2010-03-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by natpic1 on 2010-06-30
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

This link worked for me. 
When I booted up Xubuntu, it would give me a command prompt but I couldn't do a boot command. 
I went to this link (provided my bcbc) and then I could boot normally.

-This only worked because I had installed Xubuntu in Windows.

---

### Post by Dr Strangelove on 2010-07-20
I have had a ubuntu box standing at my dads place, suddenly it stopped working and now I get the same GNU GRUB shell thingy when I boot.

I have downloaded the boot script and here is the result

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   159,573,644   159,573,582  8e Linux LVM
/dev/sdc2         159,573,645   160,071,659       498,015   5 Extended
/dev/sdc5         159,573,708   160,071,659       497,952  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8edecaf8-4069-759e-a61a-3d3ade111a5b   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8edecaf8-4069-759e-a61a-3d3ade111a5b   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        jO42qa-YJ7P-Q9BT-o01c-dz8U-iHLV-590KEJ LVM2_member                               
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        f90cb27d-6a9f-4aa1-ac32-48b7821c381b   ext2                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc5        /media/f90cb27d-6a9f-4aa1-ac32-48b7821c381b ext2       (rw,nosuid,nodev,uhelper=udisks)


============================= sdc5/grub/grub.cfg: =============================

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
menuentry "Ubuntu, Linux 2.6.31-22-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/vmlinuz-2.6.31-22-server root=/dev/mapper/pufferfish-root ro   quiet splash
	initrd	/initrd.img-2.6.31-22-server
}
menuentry "Ubuntu, Linux 2.6.31-22-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/vmlinuz-2.6.31-22-server root=/dev/mapper/pufferfish-root ro single 
	initrd	/initrd.img-2.6.31-22-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/vmlinuz-2.6.31-20-server root=/dev/mapper/pufferfish-root ro   quiet splash
	initrd	/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-20-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/vmlinuz-2.6.31-20-server root=/dev/mapper/pufferfish-root ro single 
	initrd	/initrd.img-2.6.31-20-server
}
menuentry "Ubuntu, Linux 2.6.31-19-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/vmlinuz-2.6.31-19-server root=/dev/mapper/pufferfish-root ro   quiet splash
	initrd	/initrd.img-2.6.31-19-server
}
menuentry "Ubuntu, Linux 2.6.31-19-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/vmlinuz-2.6.31-19-server root=/dev/mapper/pufferfish-root ro single 
	initrd	/initrd.img-2.6.31-19-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/vmlinuz-2.6.31-14-server root=/dev/mapper/pufferfish-root ro   quiet splash
	initrd	/initrd.img-2.6.31-14-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/vmlinuz-2.6.31-14-server root=/dev/mapper/pufferfish-root ro single 
	initrd	/initrd.img-2.6.31-14-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sdc5: Location of files loaded by Grub: ===================


  81.9GB: grub/core.img
  81.9GB: grub/grub.cfg
  81.7GB: initrd.img-2.6.31-14-server
  81.7GB: initrd.img-2.6.31-19-server
  81.7GB: initrd.img-2.6.31-20-server
  81.7GB: initrd.img-2.6.31-22-server
  81.7GB: vmlinuz-2.6.31-14-server
  81.7GB: vmlinuz-2.6.31-19-server
  81.7GB: vmlinuz-2.6.31-20-server
  81.7GB: vmlinuz-2.6.31-22-server
```

I really hope you can help me get the computer to boot.... as you can see I have two rather large disks in a raid (mirrored) if it is not possible to "save" the linux installation is there a way I can at least recover the data on the raid? 

Thanks
Jacob

Edit> Checked the SMART status on the boot drive, there seems to be two errors. "Reallocated sector count" and "Current pending sector count" could these errors be the reason I now have boot issues? can it be fixed?
thanks

---

