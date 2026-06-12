---
title: "Help, odd boot problems after installing 10.04.1"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2010-09-19
I finally got around to installing 10.04.1 on a partition (clean install, not an upgrade), and it's caused some odd boot problems. Here's what my typical power up sequence is:

- Power on, cursor in top left corner for 10-12 sec, never see grub menu, boots to 10.04.1 with never an option to select other OS's.

then,
- Reboot, grub menu appears, and I select 9.10, and it hangs (black screen).

then,
- Power cycle, grub menu appears, and I select 9.10, and it boots but noticeably slower than before the clean install of 10.04.1.

The above is typical, but not completely repeatable. It does some combination of the above steps sometimes, but not all of them.

A bit frustrating to say the least.

Help please!!!!

FYI, I have Windows XP, Windows Media, 9.10, and 10.04.1 in separate partitions to boot. 10.04.1 is currently in the default (1st) position in grub. (Plus I have a partition set up just for my files.)

(PS, I searched around, but couldn't find this particular set of problems.)

---

### Post by andrewthomas on 2010-09-20
post the output of 
```
cat /etc/default/grub
```

---

### Post by Rubi1200 on 2010-09-20
Also, what graphics card do you have installed?

---

### Post by aeronutt on 2010-09-20
> **Rubi1200 said:**
> Also, what graphics card do you have installed?

Thanks for the quick responses folks.
This problem is on a Dell laptop, which is at home, so I'll do this this evening.

What command do I need to run to provide the needed info on the graphics card?

---

### Post by Rubi1200 on 2010-09-20
If you can boot into Ubuntu; from the terminal ```
lspci | grep VGA
``` otherwise from the LiveCD same thing.

---

### Post by aeronutt on 2010-09-20
Here are the results. To be complete, I ran both commands after booting into both 9.10 and 10.4.  The cat /etc/default/grub results are different between 9.10 and 10.04.  The lspci results are exactly the same.

9.10 "cat /etc/default/grub results":

[INDENT]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="2"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"[/INDENT]

10.04 "cat /etc/default/grub results":

[INDENT]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"[/INDENT]

9.10 and 10.04 "lspci | grep VGA results":

[INDENT]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/INDENT]

---

### Post by Rubi1200 on 2010-09-21
Ok, the graphics card should not be an issue as far as I know.

However, the discrepancies between the grub files may be the cause of the problems.

If I understood your post correctly, you installed 10.04 after 9.10 right?

What does the output of ```
sudo fdisk -l
``` show

I think you may need to run either ```
sudo update-grub
``` or edit the file to the settings you had in 9.10.

Hope this helps.

---

### Post by aeronutt on 2010-09-21
Correct, I installed 10.04.1 on a partition a few days ago. 9.10 has been loaded since its release.

"sudo fdisk -l" shows:

[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f9c0a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        2687    21503002+   7  HPFS/NTFS
/dev/sda3            4512       19457   120053683    f  W95 Ext'd (LBA)
/dev/sda4            2688        4511    14651280   83  Linux
/dev/sda5            5234        7145    15358140   83  Linux
/dev/sda6           19131       19457     2626596   dd  Unknown
/dev/sda7            4512        5233     5799402   82  Linux swap / Solaris
/dev/sda8            7146       19130    96269481   83  Linux

Partition table entries are not in disk order
[/INDENT]

I assume I should run update-grub while running 10.04.1 ? (Also, I assume because I loaded 10.04 after 9.10, that the grub files located in 9.10 won't be used anymore, even when booting to 9.10, correct?) 

So FYI, running update-grup while in 10.04.1 didn't change /etc/default/grub, it's the same as posted above.

---

### Post by Rubi1200 on 2010-09-21
Hi,
the /etc/default/grub file from 9.10 indicates that you made changes to it.

Have you tried applying the same changes to the file in 10.04 and running the update-grub command?

In the worst case scenario, we can reinstall GRUB so don't be concerned about that.

Also, did you create any custom entries for GRUB on the 9.10 install?

If you can, it would also help if you post the results of the bootscript linked to at the bottom of my post.

---

### Post by aeronutt on 2010-09-22
In 9.10, I changed the grub menu delay time from 10 secs to 2 secs, and used the GUI (can't remember the name of it right now, startupmanager?) to make that change. Otherwise, nothing else. No, I haven't tried to make those changes in 10.04.1.

I'll run the boot-script this evening and post results.

Rookie question, is there any security concern with posting UUID's ?

---

### Post by Rubi1200 on 2010-09-22
> **aeronutt said:**
> In 9.10, I changed the grub menu delay time from 10 secs to 2 secs, and used the GUI (can't remember the name of it right now, startupmanager?) to make that change. Otherwise, nothing else. No, I haven't tried to make those changes in 10.04.1.

I'll run the boot-script this evening and post results.

Rookie question, is there any security concern with posting UUID's ?
> Rookie question, is there any security concern with posting UUID's ?
None that I am aware of.

---

### Post by bait28 on 2010-09-22
I am having grub boot problems with my 10.10 beta install.  I get the error grub error no such device.  I ran your Boot Info program and have results but need some help determining what to do next.  Can you help.

---

### Post by aeronutt on 2010-09-22
Here are my results from the boot script. Note, being paranoid, I did a global replace of each of the UUIDs with something else in the form of nnnnnnUUIDnnnnn. Thanks for the help so far!!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650    43,166,654    43,006,005   7 HPFS/NTFS
/dev/sda3          72,469,339   312,576,704   240,107,366   f W95 Ext d (LBA)
/dev/sda5          84,068,145   114,784,424    30,716,280  83 Linux
/dev/sda6         307,323,513   312,576,704     5,253,192  dd Dell Media Direct
/dev/sda7          72,469,341    84,068,144    11,598,804  82 Linux swap / Solaris
/dev/sda8         114,784,488   307,323,449   192,538,962  83 Linux
/dev/sda4          43,166,655    72,469,214    29,302,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        111UUID11                              vfat       DellUtility                   
/dev/sda2        2222222UUID22222                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        333333333333UUID33333333333333333333   ext4                                     
/dev/sda5        44444444444UUID444444444444444444444   ext4                                     
/dev/sda6        111UUID11                              vfat       MEDIADIRECT                   
/dev/sda7        555555555555UUID55555555555555555555   swap                                     
/dev/sda8        6666666666666UUID6666666666666666666   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
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
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=44444444444UUID444444444444444444444 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=44444444444UUID444444444444444444444 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=44444444444UUID444444444444444444444 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=44444444444UUID444444444444444444444 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-21-generic
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2222222UUID22222
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=333333333333UUID33333333333333333333 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=333333333333UUID33333333333333333333 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda6)" {
    insmod fat
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 111UUID11
    drivemap -s (hd0) ${root}
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
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda5 during installation
UUID=44444444444UUID444444444444444444444  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda7 during installation
UUID=555555555555UUID55555555555555555555  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sda8                                  /media/sda8    ext3         errors=remount-ro      0  0  

=================== sda5: Location of files loaded by Grub: ===================


  47.1GB: boot/grub/core.img
  50.1GB: boot/grub/grub.cfg
  53.7GB: boot/initrd.img-2.6.31-21-generic
  53.5GB: boot/initrd.img-2.6.31-22-generic
  50.8GB: boot/vmlinuz-2.6.31-21-generic
  52.3GB: boot/vmlinuz-2.6.31-22-generic
  53.5GB: initrd.img
  53.7GB: initrd.img.old
  52.3GB: vmlinuz
  50.8GB: vmlinuz.old

================================ sda6/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=333333333333UUID33333333333333333333 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=333333333333UUID33333333333333333333 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 333333333333UUID33333333333333333333
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2222222UUID22222
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=44444444444UUID444444444444444444444 ro vga=769 quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=44444444444UUID444444444444444444444 ro single vga=769
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=44444444444UUID444444444444444444444 ro vga=769 quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44444444444UUID444444444444444444444
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=44444444444UUID444444444444444444444 ro single vga=769
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda6)" {
    insmod fat
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 111UUID11
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=333333333333UUID33333333333333333333 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=555555555555UUID55555555555555555555 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  24.7GB: boot/grub/core.img
  24.7GB: boot/grub/grub.cfg
  24.8GB: boot/initrd.img-2.6.32-24-generic
  24.6GB: boot/vmlinuz-2.6.32-24-generic
  24.8GB: initrd.img
  24.6GB: vmlinuz

```

---

### Post by Rubi1200 on 2010-09-23
Well, I don't see any obvious errors in the bootscript.

Did you create any custom GRUB entries using the templates in /etc/grub.d?

If not, I would suggest a reinstall of GRUB and see if that fixes the problem.

The first method is the easiest, but if that does not work use Method 3: CHROOT:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

In your case, make sure to reinstall GRUB to the MBR of sda and to mount the 10.04 partition on sda4.

When finished, don't forget to reboot into Ubuntu and run ```
sudo update-grub
```

If you have any questions, feel free to ask.

---

### Post by Rubi1200 on 2010-09-23
> **bait28 said:**
> I am having grub boot problems with my 10.10 beta install.  I get the error grub error no such device.  I ran your Boot Info program and have results but need some help determining what to do next.  Can you help.
Hi, firstly you should really start a new thread since your issues are different.

Beta = bugs, especially at this stage so soon before the RC.

You need to copy and paste the results of the bootscript into a new post and wrap it with code tags as aeronutt did.

Thanks.

---

### Post by aeronutt on 2010-09-23
> **Rubi1200 said:**
> Well, I don't see any obvious errors in the bootscript.

Did you create any custom GRUB entries using the templates in /etc/grub.d?

If not, I would suggest a reinstall of GRUB and see if that fixes the problem.

The first method is the easiest, but if that does not work use Method 3: CHROOT:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

In your case, make sure to reinstall GRUB to the MBR of sda and to mount the 10.04 partition on sda4.

When finished, don't forget to reboot into Ubuntu and run ```
sudo update-grub
```

If you have any questions, feel free to ask.

Nope, no custom grub entries using templates.
I'll reinstall grub and see if that fixes things. I'm sure I'll have a few questions. :)
Thanks!!

---

### Post by aeronutt on 2010-09-23
Ok, reloading of grub2 using the 1st method seems to have gone cleanly. I tested by rebooting into each of my loaded OS's, and all is good so far. We'll see if any of the intermittent problems pop up over the next few days.
Thanks!!

---

### Post by aeronutt on 2010-09-28
All seems ok now, so again, thanks for the help. Marking this as solved.

---

### Post by Rubi1200 on 2010-09-28
You are more than welcome :)

Glad things worked out for you; enjoy!

---

