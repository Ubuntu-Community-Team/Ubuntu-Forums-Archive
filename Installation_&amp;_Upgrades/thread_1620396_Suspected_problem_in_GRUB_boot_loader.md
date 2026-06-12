---
title: "Suspected problem in GRUB boot loader"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by Talruk6 on 2010-11-13
I suspect that the problem here is the GRUB boot loader, but I should start at the beginning of how I got to that conclusion because I'm somewhat new at this.

I decided to dual boot from a computer with Windows 7, using Ubuntu 10.04, 64-bit.  

I had to alter the BIOS to make the computer boot first from the CD, and hard-drive after.  I then partitioned the hard-drive easily using the GUI installer, and the whole installation went off without a hitch.

After that I restarted and went into Windows 7 and it wanted to scan my disk for errors, which I allowed.  I think it's possible that the scan messed with the GRUB boot loader.

After Windows 7 scanned for errors, I logged in normally.  After I rebooted after that, however, I got the following error message:

> no module name found.
Aborted.  Press any key to exit.

No boot device available
Strike the F1 key to reboot, F2 to run the setup utility

SATA1:  Installed
SATA2:  Installed
SATA3:  None
SATA4:  None
SATA5:  None

Whenever I reboot with the CD tray empty, I get the above error message.

When I rebooted with the linux install CD I was able to use the Live mode to access firefox and post this.

To compound this whole mess, I noticed after the error message that the original install CD was somewhat scratched, and I wonder if that may have played a part in this whole mess.

What I think I need to do is get a fresh disc and reinstall the GRUB boot loader using the Live mode.  I don't know enough about the command line to know how exactly what to type to do that though.

Thanks in advance for the help, and for bothering to read this very long post.

---

### Post by Rubi1200 on 2010-11-13
Resizing Windows 7 partitions MUST be done with the built-in Disk Management tools in Windows 7. You should then reboot a few times and run chkdsk if necessary to make sure Windows is "happy."

Right now, I suggest you follow the instructions in the link at the bottom of my post.

Post back here with the results and we will try and help you find a solution.

Thanks.

---

### Post by Talruk6 on 2010-11-14
> Resizing Windows 7 partitions MUST be done with the built-in Disk Management tools in Windows 7. You should then reboot a few times and run chkdsk if necessary to make sure Windows is "happy."


Wow, I'm shocked the book I was using didn't tell me that.  I was reading "Beginning Ubuntu Linux", 5th edition.  The 4th edition had amazing reviews, so I thought I was safe there.  It said I should just let the installer do it.

Anyway, I ran the script, and here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    22,286,335    22,204,416   7 HPFS/NTFS
/dev/sda3          22,286,336 1,048,335,687 1,026,049,352   7 HPFS/NTFS
/dev/sda4       1,048,336,382 1,953,523,711   905,187,330   5 Extended
/dev/sda5       1,048,336,384 1,916,811,263   868,474,880  83 Linux
/dev/sda6       1,916,813,312 1,953,523,711    36,710,400  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        D8980FEC980FC848                       ntfs       RECOVERY                      
/dev/sda3        CAFA1286FA126EC7                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9   ext4                                     
/dev/sda6        6de6243a-94c3-498c-b13b-50524d44a516   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d8980fec980fc848
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fc32cfc0-8ea6-4be7-9f4e-22a0b89acab9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6de6243a-94c3-498c-b13b-50524d44a516 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 953.5GB: boot/grub/core.img
 962.0GB: boot/grub/grub.cfg
 953.5GB: boot/initrd.img-2.6.32-24-generic
 953.6GB: boot/initrd.img-2.6.32-25-generic
 953.5GB: boot/vmlinuz-2.6.32-24-generic
 953.6GB: boot/vmlinuz-2.6.32-25-generic
 953.6GB: initrd.img
 953.5GB: initrd.img.old
 953.6GB: vmlinuz
 953.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```


To make sure I copied the results properly, I also attached the actual file that was generated.

---

### Post by Rubi1200 on 2010-11-14
Hi Talruk6,
I based my statement about resizing Windows 7 partitions on the views of quite a few of the more experienced members on this forum. From what I understand, Windows XP is a different story (not sure about Vista).

However, the results of the boot-script look quite normal and I would like to know what the current situation is: can you boot into either Windows and/or Ubuntu?

---

### Post by Talruk6 on 2010-11-14
I can only access the Live CD version of Ubuntu.  When I boot up with the disc in, I initially get the error:

> no module name found.
press any key to exit

After pressing a key, I get the Ubuntu installation screen, which I can use to get the "try Ubuntu" option.

I've also found that when turning my computer off, I have to manually hold the button, because the Live CD doesn't turn it all the way off.

I do think that the Live CD must be accessing the actual installed Linux partition, because it allowed me to save the diagnostic script I needed to run.

---

### Post by drs305 on 2010-11-14
Have you ever had Ubuntu on this drive before? Is the motherboard/BIOS a bit old? 

It doesn't appear that anything can be read from the MBR. All your Ubuntu Grub files are way deep on the drive (900GB+). If you have previously had Ubuntu on the drive in a similar location this is obviously not the problem. But if you haven't, it could be.

Check your BIOS settings to see if you can enable the "large drive" feature. You can also see how large a drive your BIOS thinks you have. Many computers still have a BIOS that can only see the first 137GB. 

It's not a problem after booting, as the newer OS's can read the larger disks. But older BIOS's have to access boot files within the first part of the disk.

If you don't see an option for larger disks and/or it reports a drive size of 137GB, see if there is a BIOS update available from the motherboard/BIOS manufacturer.

---

### Post by Rubi1200 on 2010-11-14
Hi,
also some other new information that might be relevant here:
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

It seems that the Dell DataSafe partition can also cause problems, so you may want to investigate this further especially since what I linked to mentions modules not found errors.

This information was provided courtesy of forum member wilee-nilee; big thanks to him!

EDIT: are you able to enter the Windows recovery mode? If so, you might want to try a chkdsk /r first to see if that helps.

---

### Post by Talruk6 on 2010-11-15
>  Have you ever had Ubuntu on this drive before? Is the motherboard/BIOS a bit old?

It doesn't appear that anything can be read from the MBR. All your Ubuntu Grub files are way deep on the drive (900GB+). If you have previously had Ubuntu on the drive in a similar location this is obviously not the problem. But if you haven't, it could be.

Check your BIOS settings to see if you can enable the "large drive" feature. You can also see how large a drive your BIOS thinks you have. Many computers still have a BIOS that can only see the first 137GB.

It's not a problem after booting, as the newer OS's can read the larger disks. But older BIOS's have to access boot files within the first part of the disk.

If you don't see an option for larger disks and/or it reports a drive size of 137GB, see if there is a BIOS update available from the motherboard/BIOS manufacturer. 

The computer is almost brand new since I bought it in early July.  This is the first time I've ever attempted to install Ubuntu on it.  What exactly does the "large drive" feature do?  I'm a little scared to poke around in the BIOS without knowing exactly what I'm doing first.  I guessing my BIOS can see more than 137 GB because the whole drive showed up during the installation when I had to partition it.

>  Hi,
also some other new information that might be relevant here:
[http://ubuntuforums.org/showpost.php...49&postcount=9](http://ubuntuforums.org/showpost.php...49&postcount=9)

It seems that the Dell DataSafe partition can also cause problems, so you may want to investigate this further especially since what I linked to mentions modules not found errors.

This information was provided courtesy of forum member wilee-nilee; big thanks to him!

EDIT: are you able to enter the Windows recovery mode? If so, you might want to try a chkdsk /r first to see if that helps. 

I can't get into the Windows recovery mode, but the link looks very promising.  I'm using a dell Studio XPS Desktop 7100.  I do remember it having some sort of data backup software when I could still boot from Windows, and the link seems to be complaining of this very same software.

The two things I don't understand in the procedure are the parts of the linked procedure.  Could anyone explain how this part works before I use it?

> For Windows Vista/7, make sure your Windows installation is NOT SELECTED in the repair process before clicking Next to get to the command prompt. Then type:

BOOTREC /FIXBOOT

BOOTREC /FIXMBR

EXIT

The next part that I don't understand is the details on reinstalling Grub, but that part I can find details on in any number of references on my own before I carry this whole thing out.


Thanks for the help everyone!

edit:  I forgot to mention, the Live CD isn't accessing the installed Linux partition because the script that I saved disappeared after I rebooted.  It must have been saved in the RAM.

---

### Post by drs305 on 2010-11-15
> **Talruk6 said:**
> The computer is almost brand new since I bought it in early July.  This is the first time I've ever attempted to install Ubuntu on it.  What exactly does the "large drive" feature do?

If your computer is new, this isn't the issue. On older computers, the BIOS may have been updated to allow the BIOS to adapt to the new larger drives.

>    I guessing my BIOS can see more than 137 GB because the whole drive showed up during the installation when I had to partition it.

Actually that can be the part that is deceiving. Once the system boots, the OS can see the entire drive. That would be true during installation as well. So the first time this situation might appear would be the first time the system boots *after* an installation and the BIOS has to try to find the new boot files.

But that doesn't appear to be your problem. 

I'm not a Windows guy, but looking for Dell Data Safe, HP Protect Tools, etc is a good avenue to explore.

---

### Post by Talruk6 on 2010-12-12
> **Rubi1200 said:**
> Hi,
also some other new information that might be relevant here:
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

It seems that the Dell DataSafe partition can also cause problems, so you may want to investigate this further especially since what I linked to mentions modules not found errors.

This information was provided courtesy of forum member wilee-nilee; big thanks to him!

EDIT: are you able to enter the Windows recovery mode? If so, you might want to try a chkdsk /r first to see if that helps.

It took me 3 weeks to read up on the Linux side of this suggestion, and acquire the Windows 7 operating system "Reinstallation DVD" which should have originally been provided by Dell.  

The result was disappointing because the second I booted up with the Reinstallation DVD, I got a familiar twist of the same old message:

> 
Press any key to boot from CD or DVD.....no module name found

Aborted.  Press any key to exit.

No boot device available
Strike the F1 key to reboot, F2 to run the setup utility

SATA1: Installed
SATA2: Installed
SATA3: None
SATA4: None
SATA5: None 


The new difference is "Press any key to boot from CD or DVD.....".  I also just noticed the "A" in "Aborted" is slightly cut off because it's too far left on the screen, implying some sort of graphics problem which I assume is because of a lack of OS for graphics driver.

Does anyone have any new ideas on what's going on here?  

I'm also considering trying to install Ubuntu by itself as a last resort, even though I'd be losing some windows only programs.  Any theories on how well that would work?

---

### Post by Quackers on 2010-12-12
Just as an idea (it has worked before) just try going into your bios and resetting everything to default. Then reboot and see if anything boots. Sometimes bioses can trip over themselves after a setting has been changed.

---

### Post by Talruk6 on 2010-12-28
Sorry for taking so long to respond to this.  My job has been taking away from my time to tinker with my currently broken computer.

I realized the problem I've talked about here is already being addressed in another thread, so I'm linking these threads to each other to make things simpler on everyone.

[http://ubuntuforums.org/showthread.php?p=10286654#post10286654](http://ubuntuforums.org/showthread.php?p=10286654#post10286654)

Edit:  I finally fixed the problem, at the expense of my old data.  I did a clean install of Ubuntu by itself.  Since the issue was probably the master boot record, the installer automatically fixed that in the process.

---

