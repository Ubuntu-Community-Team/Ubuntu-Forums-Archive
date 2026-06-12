---
title: "After installing Lucid, grub does not work correctly"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by Mikrolimano on 2011-04-18
Edit:

The problem:

After installing Ubuntu 10.04 on an external HDD (via Live-CD), [COLOR="Red"]grub never shows a menu, it only goes to command line.[/COLOR]
Every time I want to boot, I have to enter these commands:

[COLOR="Blue"]set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot[/COLOR]

That only works if I have no other disk connected to the computer.

If I have other drives (internally) connected, despite the above commands, the boot will end with Kernel Panic.

Any ideas, please?

For the original post, containing all the long and boring information, please scroll below.

===========================================================================================

Hello,

After installing Ubuntu 10.04 on an external hard drive (using the Live-CD on a computer with all internal hard drives removed), grub is not starting automatically. The cursor is blinking for several seconds, and then it goes to command line. Pressing <shift> does not help. In the end I get the following:

GNU GRUB version 1.98-1ubuntu10

Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device or file completions.

if I enter "boot", I get...

error: no loaded kernel.

when I enter "ls" it first gives me...
error: unknown filesystem

...but if I re-enter ls after 2 seconds, I properly get...
(hd0) (hd0,1)

grub is installed in (hd0,1)/boot/grub

It seems to me that somehow grub is not retaining any changes.

So, each time, I manually have to enter the following commands:

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

and after that, ubuntu loads correctly (or so it seems, I haven't checked any possible logs).

This is a fresh install from Live-CD, without any after-tweaking (changes in files etc) that I can remember of. The disk is a Seagate 2.5" 500GB ext4, with also a second tiny partition created by the installation procedure. No other partitions or operating systems exist on the disk. During the installation I chose to erase the disk and use all of it for Ubuntu. The disk is connected via USB2.

During my previous, failed attempts, I found that no tweaking could possibly make grub start. I even tried Rescatux, to no avail. I can't exactly remember what I did, but roughly I tried to re-install grub, fix the MBR so that it starts Ubuntu, among other things. Nothing worked. At least, I am now at a state where I can somehow get the OS to start. Thankfully, Ubuntu retains all settings, program installations etc from previous sessions. This just leaves me with the very annoying and tedious task of having to enter the aforementioned commands each time I plug the external drive into the computer, to work with Ubuntu.

Additional info:
-When connected to the same computer with 2 more disks (one of them booting windows 7 professional 64 bit), the cursor will blink again for several seconds, but in the end no grub command line comes up, and instead windows 7 load. The only way to get grub cli to appear is by pressing F8 for a boot menu, where I can pick from which device I can boot.

Please pardon my ignorance, but this is the first time I touch Ubuntu (and Linux, in general) in my life. I would appreciate any insight as to why this annoyance might occur, and how it could be rectified, so that I don't have to enter these commands every time I boot.

If you need the output from any commands, or the content of any configuration files or any logs, please let me know, so that I can provide them.

Thanks in advance!

---

### Post by Dutch70 on 2011-04-18
Hi and welcome to UF

Lets *(and when I say "let's" I mean someone other than me)* have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
This step must not be skipped due to formatting.

---

### Post by Mikrolimano on 2011-04-18
Hi Dutch70,

A small correction, and some additional notes: When connected to the computer with Windows disks also connected, the reason I needed to press F8 for boot menu was that I accidentally had not set the external disk as first in the boot list.

The same disk, connected to a Vaio laptop, does not boot. The laptop simply waits (literally!) forever for an OS to load (and it doesn't).

In the meantime, my last 3 attempts at re-booting the first computer with Ubuntu from the external disk fail miserably, with a "divide by zero" Kernel Panic... (at line 230, if it helps).

Boot info coming up right next...

---

### Post by Mikrolimano on 2011-04-18
Hi again,

Here are the contents of the results of the boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   957,114,367   957,112,320  83 Linux
/dev/sdd2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sdd5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        589A38B79A38940A                       ntfs       System                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4CF62449F624359C                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        e9585c24-1c59-4c78-be7a-272ac652170a   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        92f0794e-a661-4cb3-b1d8-b840e5ceb071   swap                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/e9585c24-1c59-4c78-be7a-272ac652170a ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
    linux    /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=e9585c24-1c59-4c78-be7a-272ac652170a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
    echo    'Loading Linux 2.6.32-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=e9585c24-1c59-4c78-be7a-272ac652170a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e9585c24-1c59-4c78-be7a-272ac652170a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92f0794e-a661-4cb3-b1d8-b840e5ceb071 none            swap    sw              0       0

=================== sdd1: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img
 290.0GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.32-30-generic-pae
  51.7GB: boot/vmlinuz-2.6.32-30-generic-pae
  51.8GB: initrd.img
  51.7GB: vmlinuz
```

What I find strange is that grub sees my external Ubuntu disk as hd0,1 (sda1?). Could this be causing the kernel panics, when I enter sda1 instead? With a single disk inserted sda1 seemed to work when I entered the commands...

:confused:

I'll appreciate any ideas on what I might be doing wrong.

Thanks again.

---

### Post by Mikrolimano on 2011-04-18
Hello once more,

Here are the results of the Boot Info Script, this time with only the external hard disk plugged in (all other internal disks disconnected).

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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

/dev/sda1    *          2,048   957,114,367   957,112,320  83 Linux
/dev/sda2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sda5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e9585c24-1c59-4c78-be7a-272ac652170a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        92f0794e-a661-4cb3-b1d8-b840e5ceb071   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=e9585c24-1c59-4c78-be7a-272ac652170a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	echo	'Loading Linux 2.6.32-30-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=e9585c24-1c59-4c78-be7a-272ac652170a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e9585c24-1c59-4c78-be7a-272ac652170a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92f0794e-a661-4cb3-b1d8-b840e5ceb071 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img
 290.0GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.32-30-generic-pae
  51.7GB: boot/vmlinuz-2.6.32-30-generic-pae
  51.8GB: initrd.img
  51.7GB: vmlinuz
```

This time, no Kernel Panic!

I am wondering whether I should be entering sda2 instead of sda1 in the following command:

[COLOR="Blue"]*linux /vmlinuz root=/dev/**sda1***[/COLOR]

I read somewhere that grub sees (hd0,0) as sda1, and (hd0,1) as sda2, correct? That article claimed that grub starts counting from zero for both X and Y in the (hdX,Y) format... Can somebody please verify this?

---

### Post by Dutch70 on 2011-04-18
Well, I'm no pro with boot script, but I can't find anything wrong with it. 

Also, I think grub starts counting at (hd0,0) and grub2 starts at (hd0,1). 

 One problem here is your post is very long and confusing. I can tell you put a lot of time & thought into it, which is nice, but as for me. By the time I get to the bottom of your post with all the details, I've already forgotten what your problem is. :-k

---

### Post by Dutch70 on 2011-04-18
Wait, I just noticed something strange. 
In your 1st boot script, you have this...
```

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        **/media/e9585c24-1c59-4c78-be7a-272ac652170a ext4       (rw,nosuid,nodev,uhelper=udisks)**
```

That doesn't look right. The mount point should be "/" for starters.

Edit: Notice your 2nd boot script has this...(of course it changed to sda, disregard that)
```
============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)

```

---

### Post by Mikrolimano on 2011-04-18
You're right, Dutch70, I wasn't sure how much information I should give, it ended up being long, confusing and boring. So I've edited the problem description, and put the interesting stuff on top!

Thanks again for your help!

---

### Post by Dutch70 on 2011-04-19
Great, looks much better. 

A friend looked at this thread & suggested that maybe reinstalling grub2 would help. This link will give more info than I can.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1581099[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1581099")

There is also this one if you need it.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")

---

### Post by Mikrolimano on 2011-04-19
Thanks, I'll check it out, and post the results...

---

### Post by Mikrolimano on 2011-04-19
Hi again,

I just finished re-installing grub. All commands were entered in "normal" mode (that is, not from Live-CD or chroot mode).

I entered the following commands:

sudo apt-get update
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-common grub-pc
(when asked, in the following menu, I picked "sda1")
==========================================
Configuring grub-pc
GRUB install devices:

[ ] /dev/sda (500107 MB, Portable)
[*] - /dev/sda1 (490041 MB, /)

<Ok>
==========================================
sudo update-grub

After that, same behaviour. At boot I only see grub command line, and unless I enter the commands I described in the very beginning of this thread, I can't boot Ubuntu.

For reference, here are the latest results of boot info script after the last reboot. It mentions a problem with a "missing" core.img - any ideas what this means? :confused:

Once more I feel stuck. I'll appreciate any directions on how to solve this...

```
[SIZE="2"][COLOR="Blue"][FONT="Lucida Console"]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 101018776 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

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

/dev/sda1    *          2,048   957,114,367   957,112,320  83 Linux
/dev/sda2         957,116,414   976,773,119    19,656,706   5 Extended
/dev/sda5         957,116,416   976,773,119    19,656,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e9585c24-1c59-4c78-be7a-272ac652170a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        92f0794e-a661-4cb3-b1d8-b840e5ceb071   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=e9585c24-1c59-4c78-be7a-272ac652170a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	echo	'Loading Linux 2.6.32-30-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=e9585c24-1c59-4c78-be7a-272ac652170a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e9585c24-1c59-4c78-be7a-272ac652170a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e9585c24-1c59-4c78-be7a-272ac652170a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92f0794e-a661-4cb3-b1d8-b840e5ceb071 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img
 406.0GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.32-30-generic-pae
  51.7GB: boot/vmlinuz-2.6.32-30-generic-pae
  51.8GB: initrd.img
  51.7GB: vmlinuz[/FONT][/COLOR][/SIZE]
```

---

### Post by Pitboss on 2011-04-19
Hey, the same thing happened to me. The solution was booting from Live CD and reinstalling grub. 

I think a potential problem in what you are doing is that you are installing the grub in sda1 whereas it should be installed in sda. Why don't you try this.

---

### Post by Mikrolimano on 2011-04-19
Thanks for the hint, Pitboss!

As for what to do next, I'm confused.
If Ubuntu loads (even after typing commands manually, as in my case), isn't it preferred to re-install grub from normal boot (as opposed to Live-CD), exactly the way I did?

Additionally, since I'm a total beginner in Linux, I am not quite sure about the difference between sda and sda1. sda appears as 500GB, sda1 appears as 490GB (in the menu where I choose where to install grub). Should I install grub on sda instead? What will happen if I install it on both sda and sda1? Will there be a conflict? Can somebody please enlighten me?

---

### Post by Mikrolimano on 2011-04-24
Hi again... I have to admit that even though I haven't given up the effort on solving this problem, I have given it the last priority...

I think I'll study the workings of grub a bit more, and come back when I have more specific questions.

Thanks once more to all the people who helped!

---

