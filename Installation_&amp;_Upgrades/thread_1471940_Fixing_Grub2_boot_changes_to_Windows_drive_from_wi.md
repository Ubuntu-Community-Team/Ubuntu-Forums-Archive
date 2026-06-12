---
title: "Fixing Grub2 boot changes to Windows drive from within Ubuntu"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by walt11 on 2010-05-03
I just installed Ubuntu 10.04 LTS on an external hard drive (USB connected) and I can no longer boot my Windows XP(SP3) from my internal C Drive. Grub gives me the list of boot choices, but when I choose the C drive, I just get these error messages:

GEOM ERROR
For Realtek RTL8139(X)/8130/810X PCI fast ethernet controller v2.13 (020326)

Client MAC ADDR: 00 13 D3 07 FD F5 GUID: FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF

PXE-E53: No boot filename received
PXE-NOF: Exiting PXE ROM

(The version of Grub is  1.98-lubuntu5).

I don't have a Windows System CD to boot from, but is there something I can do from within Ubuntu itself?

Thanks much

---

### Post by bcbc on 2010-05-03
Do you get this problem when the usb is not connected? You may have installed grub to the internal drive and it is looking for the external drive.

Run the following [script]("bootinfoscript.sourceforge.net/") and post the output between code tags (# above).

---

### Post by walt11 on 2010-05-04
[SIZE=2]Thanks so much for responding so quickly. It is much appreciated!

The usb drive is always connected.

Here's the output from the script

[/SIZE]```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 405115038 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      8,819,685   390,716,864   381,897,180   7 HPFS/NTFS
/dev/sda2                  63     8,819,684     8,819,622   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   404,436,374   404,436,312   7 HPFS/NTFS
/dev/sdb2         404,436,375   625,137,344   220,700,970   5 Extended
/dev/sdb5         404,436,438   616,076,684   211,640,247  83 Linux
/dev/sdb6         616,076,748   625,137,344     9,060,597  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        96FCDA15FCD9EF8B                       ntfs                                     
/dev/sda2        423B-2BDF                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F6F84D79F84D395F                       ntfs       Iomega_HDD                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a2e1bfbd-43e9-4815-9977-0d6732326b79   ext4                                     
/dev/sdb6        2de0f1bb-2a0a-42d2-9a5d-9495b83210b6   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 96fcda15fcd9ef8b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=2de0f1bb-2a0a-42d2-9a5d-9495b83210b6 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdg        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 207.4GB: boot/grub/core.img
 207.4GB: boot/grub/grub.cfg
 207.3GB: boot/initrd.img-2.6.31-14-generic
 207.4GB: boot/initrd.img-2.6.32-21-generic
 207.2GB: boot/vmlinuz-2.6.31-14-generic
 207.3GB: boot/vmlinuz-2.6.32-21-generic
 207.4GB: initrd.img
 207.3GB: initrd.img.old
 207.3GB: vmlinuz
 207.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

Those last devices (or 4 of them, I think, at any rate) are slots for cards in a "multi-media" input panel in my PC. I disabled 4 of them in the device manager before doing the install (to get around a bug in wubi) and forgot to re-enable them! Also, it's not clear to me why the error message would have anything to do with the Ethernet controller??

Thanks again. I probably won't be looking for your response till the morning. (Two late nights stewing over this.)

---

### Post by bcbc on 2010-05-04
You've installed grub to your windows partition - this destroys the windows boot sector. You can fix it either with a windows repair disk or from within ubuntu using testdisk - see [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") for instructions.

You also have grub installed in the master boot records of both your internal and your external. That means that if you do unplug your external, you won't be able to boot windows. But you said that the external is always plugged in so that may not be an issue for you.

Finally, you said something about wubi, but you don't have wubi installed (i.e. ubuntu installed from within windows). All I see is a 'side by side' installation with ubuntu on your external. Just FYI.
I'm also puzzled by the 'ethernet' error. That is strange.

But at any rate, try and fix the boot sector on /dev/sda1 and see if it that resolves your problem.

Good luck

---

### Post by walt11 on 2010-05-04
[SIZE=2]Thank you again for your response!!  I'll try to follow the instructions on the SourceForge page, and get back to you with the results. I'll need to use the testdisk approach, since I don't have a windows repair disk, and may need to ask you some questions in the process.

You said that I also have grub installed in the master boot records of both the internal and external. Will the procedure on SourceForge also enable me to fix the one on the internal? If the external ever is unplugged, or fails, I'd be out of luck. (What are the implications of grub being installed in the mbr of the external? Is that required to be able to boot ubuntu, or is it only required in the partition in which ubuntu resides?)

[/SIZE]

---

### Post by bcbc on 2010-05-04
> **walt11 said:**
> [SIZE=2]Thank you again for your response!!  I'll try to follow the instructions on the SourceForge page, and get back to you with the results. I'll need to use the testdisk approach, since I don't have a windows repair disk, and may need to ask you some questions in the process.

You said that I also have grub installed in the master boot records of both the internal and external. Will the procedure on SourceForge also enable me to fix the one on the internal? If the external ever is unplugged, or fails, I'd be out of luck. (What are the implications of grub being installed in the mbr of the external? Is that required to be able to boot ubuntu, or is it only required in the partition in which ubuntu resides?)

[/SIZE]
What I do, is I have grub installed in the external drive, and I just select to boot from it using the BIOS boot options menu. When I don't have it, the default is to boot from the internal drive. 

If your BIOS supports this it this would work, but it may be a pain if you most often boot into ubuntu (because if you don't watch/override every boot, it will slip by into windows by default).

Another option is to boot from windows to ubuntu - I haven't done this but you can search on how to do this. 

You should get an xp repair cd anyway. You will need it if the 'testdisk option' doesn't work and it's a good idea to have as a backup.

---

### Post by walt11 on 2010-05-04
[SIZE=2]It worked! THANK YOU! It's responses like yours that make me glad to be part of the ubuntu community. I had planned to try ubuntu (and I'm discovering [/SIZE][SIZE=2]great [/SIZE][SIZE=2]new things every day) but I'm starting to think about making it my primary system. (After 2 days without Windows, I'm finding that the things I couldn't live without I can actually live without.)[/SIZE]
[SIZE=2]
Having Grub at the root of the internal drive [/SIZE][SIZE=2]actually [/SIZE][SIZE=2]seems quite convenient. Although my BIOS does support a boot menu, as you point out it would be a pain to enter that each time, particularly as I boot into ubuntu more and more frequently. Am I correct that if the external drive failed, I could still boot into Windows via the Grub menu on the internal?

Yes, I should get an xp repair cd. How does one go about getting it?
[/SIZE]

---

### Post by bcbc on 2010-05-04
> **walt11 said:**
> [SIZE=2]It worked! THANK YOU! It's responses like yours that make me glad to be part of the ubuntu community. I had planned to try ubuntu (and I'm discovering [/SIZE][SIZE=2]great [/SIZE][SIZE=2]new things every day) but I'm starting to think about making it my primary system. (After 2 days without Windows, I'm finding that the things I couldn't live without I can actually live without.)[/SIZE]
[SIZE=2]
Having Grub at the root of the internal drive [/SIZE][SIZE=2]actually [/SIZE][SIZE=2]seems quite convenient. Although my BIOS does support a boot menu, as you point out it would be a pain to enter that each time, particularly as I boot into ubuntu more and more frequently. Am I correct that if the external drive failed, I could still boot into Windows via the Grub menu on the internal?

Yes, I should get an xp repair cd. How does one go about getting it?
[/SIZE]

Great, you're welcome!

In answer to your questions, if your external fails then you will stuck as the grub in your MBR is actually loading the menu from your ubuntu install. 

Not sure how to go about creating an xp repair. I have my original install disk so haven't had to. I'd recommend searching on the net.

---

### Post by oldfred on 2010-05-04
You can install a basic window boot loader from linux.

per meierfra. mbr.bin may cause problems in some cases better to use lilo
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

sdX - Use sda for the internal drive.

---

### Post by walt11 on 2010-05-04
[SIZE=2]> **oldfred said:**
> You can install a basic window boot loader from linux.

per meierfra. mbr.bin may cause problems in some cases better to use lilo[/SIZE] [SIZE=2]
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

sdX - Use sda for the internal drive.[/SIZE] [SIZE=2]

bcbc: I was going to ask if there was a way to fix the MBR of the internal drive from Ubuntu, and it looks like oldfred has already given me the answer. (Thanks!).

Then do I just need to execute those 2 commands from a terminal window and the MBR will no longer reference grub on the external drive? Will the basic boot loader which is installed this way understand that it needs to boot sda1 and not sda2? (Both are bootable, but sda2 immediately starts to do a system recovery.)

Another question. If the internal drive fails (it's 5 years old now) will I just be able to put the external on another system and boot Ubuntu, i.e., is the external drive independent, or does it need something from the internal to be able to boot?

[/SIZE]

---

### Post by oldfred on 2010-05-04
The lilo boot loader in the MBR works like the windows boot loader in that it just looks for an active partition  or one with the boot flag. So it will try to boot the partition with the boot flag. It requires boot loader in the PBR partition boot record which windows has for its active partition. When grub chainboots to windows it does the same thing chains to the windows PBR.

After you install it just test it by booting without the external.

The external should boot on its own from any system. There may be drive numbering issues but since UUIDs are used for most things now it just works. I have heard that even different video card will at least boot, maybe not in best mode.

---

### Post by walt11 on 2010-05-06
> **bcbc said:**
> Great, you're welcome!

In answer to your questions, if your external fails then you will stuck as the grub in your MBR is actually loading the menu from your ubuntu install. 

Not sure how to go about creating an xp repair. I have my original install disk so haven't had to. I'd recommend searching on the net.

bcbc, can you say a bit more about your comment that the grub in my MBR (sda) is actually loading the menu from my ubuntu install? I'm confused by the following 2 statements at the beginning of The Boot Info Script, particularly the first one:

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

What is partition #5 on sda? sda only has 2 partitions. It would make more sense if it was talking about sdb, but it says "on the same drive"?? And, is that file, /boot/grub the one which references the ubuntu install?

Another, but related question: If sda fails (it's 5 years old now) would I still be able to boot ubuntu from sdb? If I chose sdb from the BIOS boot menu, would it just connect with the grub 2 menu on that drive?

Thanks again. I'll soon stop taking your time (both of you) with this, but feel I need to know more to make an appropriate decision about the MBR on sda.)

---

### Post by oldfred on 2010-05-06
I believe either the script or grub report the drive/partition incorrectly with grub 1.98. I have the same issue as my Lucid is in sdc7, grub 1.98 to boot Lucid is in sda and the script says it boots the same drive partition 7 and I only have 3 partitions in sda. But it boots ok.

You can test your grub in sdb. Either change BIOS or use the single boot choice (f12 on my desktop, f2 on portable) that your BIOS offers. It should boot your install on sdb5.

I typically recommend that you  boot the drive and have grub in the drive that has the Ubuntu install when you have more than one drive. Same with windows or other systems. Each drive then can boot on its own "just in case". 
Grub 1.97 had a minor bug that caused a 20 sec delay in booting if it was not on the same drive (it went off and did some searching). So it was always better to have it on the same drive as Ubuntu.

I have not tested this with Lucid but in Karmic this reset the default location for future updates to grub.
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc

Location of grub-pc/install_devices is in /var/cache/debconf/config.dat for karmic.

---

### Post by bcbc on 2010-05-07
> **walt11 said:**
> bcbc, can you say a bit more about your comment that the grub in my MBR (sda) is actually loading the menu from my ubuntu install? I'm confused by the following 2 statements at the beginning of The Boot Info Script, particularly the first one:

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

What is partition #5 on sda? sda only has 2 partitions. It would make more sense if it was talking about sdb, but it says "on the same drive"?? And, is that file, /boot/grub the one which references the ubuntu install?

Yes I agree with oldfred. The bootinfoscript hasn't been updated since february I guess, so I just assumed (based on the same observations as you) that it wasn't correctly identifying partition 5 as being on sdb - I should have mentioned this before.

> **walt11 said:**
> Another, but related question: If sda fails (it's 5 years old now) would I still be able to boot ubuntu from sdb? If I chose sdb from the BIOS boot menu, would it just connect with the grub 2 menu on that drive?
Yes, since you installed grub2 to both MBR's they both look in the same place for the menu. 

The only caveat is that the menu entries may not work if the external is not identified as the same hard drive number: if you look within the menu in /boot/grub/grub.cfg...
```
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set a2e1bfbd-43e9-4815-9977-0d6732326b79
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a2e1bfbd-43e9-4815-9977-0d6732326b79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
``` 
you see the line "set root='(hd1,5)'. It's possible that e.g. if that's the only drive, or you plug it into some other computer, that your external is no longer "hd1" i.e. the second hard drive. You can get around this by booting manually from the grub command line the first time, and then updating grub once you boot ubuntu. There are some good [guides]("http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") on how to boot from grub command line.

I don't think you should get hung up on whether your drives will fail. This could happen at any time regardless of age, so you should just choose the setup that works best for you (and of course backup your data). If you use Ubuntu more than windows and have a desktop, you may prefer to leave grub2 in your internal, using the grub menu from your external. 

Just keep a live CD around, then you can install lilo anytime you need to the internal and get windows booting again.

---

### Post by julio.010101 on 2010-05-08
> **bcbc said:**
> You've installed grub to your windows partition - this destroys the windows boot sector. You can fix it either with a windows repair disk or from within ubuntu using testdisk - see [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") for instructions.

You also have grub installed in the master boot records of both your internal and your external. That means that if you do unplug your external, you won't be able to boot windows. But you said that the external is always plugged in so that may not be an issue for you.

Finally, you said something about wubi, but you don't have wubi installed (i.e. ubuntu installed from within windows). All I see is a 'side by side' installation with ubuntu on your external. Just FYI.
I'm also puzzled by the 'ethernet' error. That is strange.

But at any rate, try and fix the boot sector on /dev/sda1 and see if it that resolves your problem.

Good luck

testdisk solved for me, thanks

---

### Post by walt11 on 2010-05-10
Thanks bcbc & oldfred, for those very helpful recent posts (#s 13 & 14).

bcbc, I agree with you that I shouldn't get hung up on possible drive failure, and for now I'm keeping grub on both the internal and external because it's convenient. Nevertheless, would you elaborate on a couple of things in your #14:

> It's possible that e.g. if that's the only drive, or you plug it into some other computer, that your external is no longer "hd1" i.e. the second hard drive. You can get around this by booting manually from the grub command line the first time, and then updating grub once you boot ubuntu.How do you update grub? Is it by sudo dpkg-reconfigure grub-pc as in oldfred's last post? Or is there some way to edit the grub.cfg file (which starts out by stating # DO NOT EDIT THIS FILE)?

> Just keep a live CD around, then you can install lilo anytime you need to the internal and get windows booting again.(I'm thinking you meant grub.) How do you do that install? Is it also by sudo dpkg-reconfigure grub-pc?

Finally, a relatively minor issue: The grub menu entries for my internal partitions are right next to each other:

```

menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 96fcda15fcd9ef8b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}

```I'm afraid that when booting, I, or someone else, may accidentally choose the second one, causing it to restore 5 year old software, wiping out my C: drive. Is there a way to eliminate that last entry?

Thanks once more.

---

### Post by oldfred on 2010-05-10
Copy you one windows that you want into 40_custom. If osprober is off then it will not find your windows entry and only show the one from 40_custom. If you every change or add systems you can turn the prober back on temporarily. 


Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

---

### Post by bcbc on 2010-05-10
> **walt11 said:**
> Thanks bcbc & oldfred, for those very helpful recent posts (#s 13 & 14).

bcbc, I agree with you that I shouldn't get hung up on possible drive failure, and for now I'm keeping grub on both the internal and external because it's convenient. Nevertheless, would you elaborate on a couple of things in your #14:

How do you update grub? Is it by sudo dpkg-reconfigure grub-pc as in oldfred's last post? Or is there some way to edit the grub.cfg file (which starts out by stating # DO NOT EDIT THIS FILE)?

(I'm thinking you meant grub.) How do you do that install? Is it also by sudo dpkg-reconfigure grub-pc?

Finally, a relatively minor issue: The grub menu entries for my internal partitions are right next to each other:

```

menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 96fcda15fcd9ef8b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}

```I'm afraid that when booting, I, or someone else, may accidentally choose the second one, causing it to restore 5 year old software, wiping out my C: drive. Is there a way to eliminate that last entry?

Thanks once more.

You can update grub with:```
sudo update-grub
``` ('update-grub' is an alias for 'grub-mkconfig -o /boot/grub/grub.cfg'). This is great when you're in ubuntu, but you might be stuck at the grub menu and when you try and boot it gives you some error. In that case, you can select the entry you want, press 'e', and make changes, then boot with CTRL+X. Once you're in ubuntu just run update-grub as above.

Yes, you shouldn't edit the grub.cfg directly, because it is automatically regenerated with certain updates.

I actually meant lilo. Grub is already installed and you shouldn't have to reinstall it under normal use. I was thinking *if you ever needed* to boot the internal i.e. windows, without the external plugged in, you could just install lilo to the internal MBR. 

Finally, I use the [custom menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu") oldfred mentioned. And drs305's method sounds like it will do the trick as well.

---

### Post by walt11 on 2010-05-11
Thanks to both of you again for much good information. I'm way over my depth here, and need to ask for more detail on a couple of things.

bcbc:

> Just keep a live CD around, then you can install lilo anytime you need  to the internal and get windows booting again.
 
> I actually meant lilo. Grub is already installed and you shouldn't have  to reinstall it under normal use. I was thinking *if you ever needed*  to boot the internal i.e. windows, without the external plugged in, you  could just install lilo to the internal MBR. 


I have to ask for a step-by-step explanation here. I do have a good 9.10 live CD which I've booted from before, and installed a temporary system from it.

Once I've done that, what are the steps to install (and configure?) lilo to the MBR on my internal drive?
Then, if I just reboot, will I see a menu (from lilo) which allows me to choose the internal?

One other area:

> ... you might be stuck at the grub  menu and when you try and boot it gives you some error. In that case,  you can select the entry you want, press 'e', and make changes, then  boot with CTRL+X. Once you're in ubuntu just run update-grub as above.

 What changes would I need to make after entering 'e'?

---

### Post by oldfred on 2010-05-11
The windows boot loader just looks for an active partition (boot flag in Ubuntu) on a primary partition. the lilo boot loader in the MBR will do the same thing.

You need to have universe enabled:
Restore basic windows boot loader 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

And with a liveCd you can reinstall grub or do many other repairs. Some emergency/rescue CDs are set up just for that.

---

### Post by walt11 on 2010-05-11
> The windows boot loader just looks for an active partition (boot flag in  Ubuntu) on a primary partition. the lilo boot loader in the MBR will do  the same thing.

You need to have universe enabled:
Restore basic windows boot loader 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

And with a liveCd you can reinstall grub or do many other repairs. Some  emergency/rescue CDs are set up just for that.

Thanks oldfred! (After sending my last post, I came across your #9, which I had forgotten. Sorry.)

How do I enable universe?

---

### Post by bcbc on 2010-05-12
> **walt11 said:**
> 
 What changes would I need to make after entering 'e'?

I'm probably guilty of providing 'too much information'. Along with that other link about booting from the grub CLI, you could adjust grub entries on the fly... but really, if you ever have problems posting here on the forums will probably get you the help you need without resorting to this.

However, just for an example, instead of hitting enter when you boot next time, hit 'e'. You can see what grub commands are required to boot. Once you're done looking, you can either ESC back to the menu, or CTRL+X to boot directly if you made changes. One of the most common things would be to delete 'quiet splash', especially if you have problems booting and you want to see diagnosis information where the boot fails.

You could instead hit 'c' and go to the grub command line, and just boot manually. That link I provided earlier has info on the basic stuff you need to boot in this way.

---

### Post by walt11 on 2010-05-24
[SIZE=2]bcbc & oldfred: I just wanted to thank you both again for your consistent and unfailing support. I haven't responded to your last posts, because I'm spending less of my time worrying about disaster (as bcbc suggested) and more of it just leaning about the amazing things in Ubuntu, and customizing it to my needs. You have provided me with more than enough info in the event of a problem. And, as you said, I can always come back here for help.[/SIZE]

---

### Post by oldfred on 2010-05-24
Glad we could help. Enjoy Ubuntu.

---

