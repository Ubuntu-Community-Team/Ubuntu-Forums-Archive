---
title: "Another dual boot problem."
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by unisubzero on 2010-01-09
Hi guys !
 

 I hope some one can help me out with a “small” problem I have.
 

 I have quit simple setup: 2 x 500Gig HDD's (sda with Windows 7 64Bit and sdb with Ubuntu 9.10 32Bit, both fresh install with updates).
 From time to time right after GRUB menu it will hang and all I can see is Ubuntu sign om a black screen. It wont response to any key combination and only way to reboot is hardware button reset. I tried to enter recovery boot but it will also freeze in the next recovery menu. Once I saw a massage: Mountall cancelled. General error mounting file system. A maintenance shell now be started Ctrl+D will terminate this shell and re-try.
 

 Motherboard is Intell DX58SO with 2 SATA HDD (if that of any importance).
 

 The chance of booting or not booting is like 50/50. If I see HDD activities right after GRUB menu it will boot if not then it will hang there forever.
 

 What can it be or where should I look to solve this annoying problem ?
 

 Thanks in advance !


```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=e2367832-f04f-4189-b433-171015ade1cf)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f1d8de7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e209e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   957,168,764   957,168,702  83 Linux
/dev/sdb2         957,168,765   976,768,064    19,599,300   5 Extended
/dev/sdb5         957,168,828   976,768,064    19,599,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="02600A2D600A27CD" TYPE="ntfs" 
sda2: UUID="7E6C0DFF6C0DB2C7" TYPE="ntfs" 
sdb1: UUID="e2367832-f04f-4189-b433-171015ade1cf" TYPE="ext4" 
sdb5: UUID="13049692-d8d6-40ce-86e9-0013db38d6b9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrei/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrei)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set e2367832-f04f-4189-b433-171015ade1cf
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
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set e2367832-f04f-4189-b433-171015ade1cf
insmod tga
if background_image /boot/grub/Hortensia-1.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2367832-f04f-4189-b433-171015ade1cf
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=e2367832-f04f-4189-b433-171015ade1cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e2367832-f04f-4189-b433-171015ade1cf
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=e2367832-f04f-4189-b433-171015ade1cf ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02600a2d600a27cd
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=e2367832-f04f-4189-b433-171015ade1cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=13049692-d8d6-40ce-86e9-0013db38d6b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-17-generic-pae
    .0GB: boot/vmlinuz-2.6.31-17-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz

```

---

### Post by darkod on 2010-01-09
Did you try switching the drives in the boot order in BIOS? Because both drives are 500GB you can't know which is which, so just go into BIOS and make the drive currently second in boot order to be first.
Then check out if it helps.
You have grub2 on both drives so you should be able to boot but if you are using the grub2 from the windows drive sometimes it taken longer to jump to the ubuntu drive. Occasionally this may be a reason for the delay.

---

### Post by unisubzero on 2010-01-09
Still the same. Twice booted OK and once hanged (waited 20 min).
 

 Had the same problem when those two OS's where on the same HDD.  
 

 Maybe swapping places (Ubuntu on sda and win 7 on sdb) will work out … ?
Or Ubuntu 64Bit ?

---

### Post by oldfred on 2010-01-09
There seem to be a few similar errors:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/488462](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/488462)

Some of the older bug reports say it was fixed?

I might try the 64 bit if you have not done a lot of upgrades to your system. It will automatically run with all your memory without the PAE server add in. I have had no issues with the 64 bit version on two computers, desktop and portable.

Installing on opposite drives will not make any difference. Do you have an encrypted drive? There seem to be more issues with encryption.

---

### Post by tn812 on 2010-01-09
I experience the same problem.  Computer hangs 50/50 of the time at bootup.  I've tried to search for solutions but not much luck.  I first try with Ubuntu went well, never crashed (installed xp then ubuntu with side by side option).  Now I'm trying to install ubuntu on a second pc.  First used Gpart to set up desired partitions.  But this method runs into bootup problems.  It's frustrating because I'm new to Linux, and I like it much better than all versions of Windows.

 Now I'm trying to find out if the hang up has anything with resizing the HD partitions before/after ubuntu installation.  It seems like bootup or grub got lost at startup, doesn't know where the Ubuntu drive is.  HD just keeps spinning at logo.

I hope someone can help before I give up and just stay with Windows.

---

### Post by unisubzero on 2010-01-09
OK. The problem seems to be gone … (at least I hope so)
 

 What I did is: I removed old sda drive and put another one instead (also 500Gig). Installed Win 7 64Bit on sdb drive and Ubuntu 9.10 64Bit on sda.  
 

 Booted around 10 times and so far so good.


                                   It could be some hardware and software incompatibility … I don't know. Sins not that much people having this problem.


                                  Anyway, thanks for the input guys and here is the code from the script from the new install.  
 


```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4742c7f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             208,845   976,768,064   976,559,220   5 Extended
/dev/sda5             208,908   940,943,114   940,734,207  83 Linux
/dev/sda6         940,943,178   976,768,064    35,824,887  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e209e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="2036DBCD36DBA1D8" LABEL="System Reserved" TYPE="ntfs" 
sda5: UUID="8280aa20-7969-4283-ba43-6234548382d1" TYPE="ext4" 
sda6: UUID="1562b04e-0159-4f60-90ff-c0feafe8bd37" TYPE="swap" 
sdb1: UUID="DAB4D4B5B4D4957B" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrei/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrei)


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
search --no-floppy --fs-uuid --set 8280aa20-7969-4283-ba43-6234548382d1
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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 8280aa20-7969-4283-ba43-6234548382d1
insmod tga
if background_image /boot/grub/Hortensia-1.tga ; then
  set color_normal=black/black
  set color_highlight=blue/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 8280aa20-7969-4283-ba43-6234548382d1
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8280aa20-7969-4283-ba43-6234548382d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 8280aa20-7969-4283-ba43-6234548382d1
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=8280aa20-7969-4283-ba43-6234548382d1 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2036dbcd36dba1d8
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8280aa20-7969-4283-ba43-6234548382d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1562b04e-0159-4f60-90ff-c0feafe8bd37 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.31-17-generic
    .1GB: boot/vmlinuz-2.6.31-17-generic
    .1GB: initrd.img
    .1GB: vmlinuz
```

---

### Post by XxX_VLAD_XxX on 2010-04-18
Maybe you should try a BIOS update to the motherboard, because it seems to be a lot of problems at boot up with this motherboard. I'm going to update BIOS, see how that goes....

---

