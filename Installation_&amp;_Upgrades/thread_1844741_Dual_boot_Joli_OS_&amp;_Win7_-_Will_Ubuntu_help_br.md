---
title: "Dual boot Joli OS &amp; Win7 - Will Ubuntu help bring GRUBback"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by Gregor11 on 2011-09-15
I have added a Jolicloud installation (Joli OS 1.2 from iso file flashed to a pen drive) this morning to work along with Windows 7 Starter as a dual boot. (Actually, doing so I have overwritten a Natty installation hoping for a better support of Intel GMA500 on my netbook). Here comes my headache:

The system always boots straight to Joli OS. No GRUB in sight. Natty was booting fine with GRUB and Win7. I guess after Joli OS GRUB has appeared once at the very first start and then never again.

The general problem seems Grub is given no time to make the OS selection. I came across quite a number of very similar cases with Win XP users. They were able to recover their dual boot by patching boot.ini. But Win 7 has no boot.ini. 

What I've been thinking so far is

Can I do anything to Grub's config (sudo gedit /etc/default/grub) ?

GRUB_TIMEOUT=10 is already set ..
GRUB_HIDDEN_TIMEOUT=0 0r =10 doesn't change anything.

Would another installation of Ubuntu (replacing Joli OS or alongside it) bring back GRUB?

Should I give a try with Super Grub Disk? Have never used this tool before.

Here is the disk partition:
/dev/sda1 Win recovery
/dev/sda2 ntfs, Windows 7 Starter
/dev/sda3 ntfs, empty
/dev/sda4 extended with:
      /dev/sda5 linux-swap
      /dev/sda6 ext4 with Joli OS
8 gig of empty space for another distro.


Any of your ideas will be so much appreciated!

---

### Post by drs305 on 2011-09-15
Installing Ubuntu would definitely bring back Grub 2. 

What does Jolicloud use? Since you mention Grub 2 files, does it also use it? If so, it's possible you just need to run "sudo update-grub" to make sure it finds Windows. If Grub 2 isn't aware of another OS, it will boot without showing the menu. You can try to bring up the menu during boot by holding down the SHIFT key.

It might be best to run the Boot Info Script and post the contents of RESULTS.txt. You can get to the page from the "BIS" link in my signature.

---

### Post by Gregor11 on 2011-09-15
> **drs305 said:**
> Installing Ubuntu would definitely bring back Grub 2. 

What does Jolicloud use? Since you mention Grub 2 files, does it also use it? If so, it's possible you just need to run "sudo update-grub" to make sure it finds Windows. If Grub 2 isn't aware of another OS, it will boot without showing the menu. You can try to bring up the menu during boot by holding down the SHIFT key.


Is it possible for Jolicloud to start without Grub? (I have to admit to being a novice..)
"sudo update-grub" result in
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35.10-1-jolicloud-atom
Found initrd image: /boot/initrd.img-2.6.35.10-1-jolicloud-atom
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

Obviously, it notices the Windows loader but doesn't lead to any changes (it's the second time I run "sudo update-grub").

Holding the shift key just puts the boot on hold.


> **drs305 said:**
> 
It might be best to run the Boot Info Script and post the contents of RESULTS.txt. You can get to the page from the "BIS" link in my signature.

Here it is in its entire length..
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Joli OS 1.2
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    16,386,047    16,384,000   7 NTFS / exFAT / HPFS
/dev/sda2          16,386,048   123,863,547   107,477,500   7 NTFS / exFAT / HPFS
/dev/sda3         123,865,088   199,942,143    76,077,056   7 NTFS / exFAT / HPFS
/dev/sda4         199,944,190   220,123,135    20,178,946   5 Extended
/dev/sda5         199,944,192   204,498,943     4,554,752  82 Linux swap / Solaris
/dev/sda6         204,500,992   220,123,135    15,622,144  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6EC653FBC653C24F                       ntfs       System
/dev/sda2        0682575582574877                       ntfs       Local Disk
/dev/sda3        5F44CA1335EF5FD1                       ntfs       Data
/dev/sda5        25ba27dd-52a7-425c-a2d4-468a47577f5d   swap       
/dev/sda6        35688b08-ce85-4851-97c6-847082942a9f   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 35688b08-ce85-4851-97c6-847082942a9f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 35688b08-ce85-4851-97c6-847082942a9f
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
menuentry 'Joli OS, with Linux 2.6.35.10-1-jolicloud-atom' --class joli os --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 35688b08-ce85-4851-97c6-847082942a9f
    echo    'Loading Linux 2.6.35.10-1-jolicloud-atom ...'
    linux    /boot/vmlinuz-2.6.35.10-1-jolicloud-atom root=UUID=35688b08-ce85-4851-97c6-847082942a9f ro acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=800x600-24,mtrr=3,scroll=ywrap pci=nocrs  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35.10-1-jolicloud-atom
}
menuentry 'Joli OS, with Linux 2.6.35.10-1-jolicloud-atom (recovery mode)' --class joli os --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 35688b08-ce85-4851-97c6-847082942a9f
    echo    'Loading Linux 2.6.35.10-1-jolicloud-atom ...'
    linux    /boot/vmlinuz-2.6.35.10-1-jolicloud-atom root=UUID=35688b08-ce85-4851-97c6-847082942a9f ro single acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=800x600-24,mtrr=3,scroll=ywrap pci=nocrs
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35.10-1-jolicloud-atom
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 35688b08-ce85-4851-97c6-847082942a9f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 35688b08-ce85-4851-97c6-847082942a9f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6ec653fbc653c24f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0682575582574877
    chainloader +1
}
if [ ${timeout} != -1 ]; then
  if sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=35688b08-ce85-4851-97c6-847082942a9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=25ba27dd-52a7-425c-a2d4-468a47577f5d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.326076508 = 107.724304384  boot/grub/core.img                             1
 101.105594635 = 108.561305600  boot/grub/grub.cfg                             1
  98.443359375 = 105.702752256  boot/initrd.img-2.6.35.10-1-jolicloud-atom     2
 101.143264771 = 108.601753600  boot/vmlinuz-2.6.35.10-1-jolicloud-atom        1
  98.443359375 = 105.702752256  initrd.img                                     2
 101.143264771 = 108.601753600  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 45 00 00 fe  |............E...|
000001d0  ff ff 05 fe ff ff 02 80  45 00 00 68 ee 00 00 00  |........E..h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2011-09-15
I can't see anything wrong with your Grub configuration. There is no keystatus check, so holding SHIFT during boot to display the menu won't work; however, pressing the ESC key repeatedly early in the boot process might.

One thing you could try would be to set the GRUB_TIMEOUT in /etc/default/grub from **10** to **-1**. You will have to edit the file as root. 

If things were working correctly that would display the menu until you make a selection. Run "*sudo update-grub*" after saving the file.

---

### Post by Gregor11 on 2011-09-16
> **drs305 said:**
> One thing you could try would be to set the GRUB_TIMEOUT in /etc/default/grub from **10** to **-1**. You will have to edit the file as root. 

If things were working correctly that would display the menu until you make a selection. Run "*sudo update-grub*" after saving the file.

This was it. Can't say enough how upset I was with such an elementary flaw in Jolicloud's setup routine and how happy I am now. Thank you so much, drs305.

---

### Post by drs305 on 2011-09-16
I'm glad you have it working now. Of course, it should have worked with the 10 second timeout, but if you are content with manually selecting an entry I'd leave it. (We get more requests to *bypass* the menu, so I guess things even out ;-) ).

If you don't have any other questions or issues with the boot, you can mark the thread SOLVED via the 'Thread Tools' link at the top right of the original post.

Happy computing !

---

