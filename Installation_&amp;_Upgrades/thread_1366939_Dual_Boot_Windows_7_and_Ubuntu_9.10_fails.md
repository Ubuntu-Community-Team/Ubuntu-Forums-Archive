---
title: "Dual Boot Windows 7 and Ubuntu 9.10 fails"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by kalmos on 2009-12-29
In short, I've been at it for hours, and I cannot make it work. In the past, I have dual-booted (and triple-booted) several times successfully with no surprises, so I'm losing my patience here. :confused:

Details:
Windows 7 64-bit Professional
Ubuntu 9.10 64-bit Karmic Koala

I have a 32GB Corsair SSD. Originally, I used the whole drive for Ubuntu and some other drive for Win7, and it worked fine. (I would stick with ubuntu-only, but I need something faster than wine for the occasional video-game development.)

So, I booted to the Win7 disc, deleted everything on the SSD, and then told the installer to use roughly half of the drive as a ntfs partition (plus 100MB partition of "system restore" or some such). Windows installs flawlessly, and so far I'm happy.

Next, I boot to the Ubuntu disc and start a live session so I can surf on Firefox while Ubuntu installs. I click the "install" link, and point it at the second half of the SSD and make a ext4 partition: no surprises, it installs fine.

Now I restart, and there is no GRUB menu :(. It boots straight to windows. I don't know what to do. Earlier, I tried installing Ubuntu first and Windows second, but this caused a "Missing Operating System" message when I booted, so I couldn't boot into windows or ubuntu.

I found a few threads with general questions about dual booting, but nothing related to my problem. If you found a thread that could help me, please link to it.

Thanks in advance. I'd like to be able to use both OS's on the SSD, but I guess I'll have to settle for one or the other if I cannot fix this issue.

---

### Post by oldfred on 2009-12-29
The new install of win7 puts in a win7 boot partition of about 100mb. Part of windows boot is in the 100mb partition.

It sounds like grub did not install to the MBR of the drive. Do you have another drive installed?

To see what is where:

Boot Info Script 0.42 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by kalmos on 2009-12-29
Ok,  I'm running on the live cd right now and I executed the script you suggested.

Indeed, the 100MB partition seems to be the problem, but I don't know how to fix this. I don't mind reinstalling everything from scratch, because I've already done it a few times now.

Thanks for helping, I appreciate it.

RESULTS.txt:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000585af

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    33,998,847    33,792,000   7 HPFS/NTFS
/dev/sda3          34,009,605    62,524,979    28,515,375  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8AA226B5A226A623" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="52BE6DFCBE6DD8CD" TYPE="ntfs" 
/dev/sda3: UUID="0dac5624-8f6e-4e00-acd5-c9be6ef4e941" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd2,3)
search --no-floppy --fs-uuid --set 0dac5624-8f6e-4e00-acd5-c9be6ef4e941
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
    set root=(hd2,3)
    search --no-floppy --fs-uuid --set 0dac5624-8f6e-4e00-acd5-c9be6ef4e941
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0dac5624-8f6e-4e00-acd5-c9be6ef4e941 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,3)
    search --no-floppy --fs-uuid --set 0dac5624-8f6e-4e00-acd5-c9be6ef4e941
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0dac5624-8f6e-4e00-acd5-c9be6ef4e941 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 8aa226b5a226a623
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc3 during installation
UUID=0dac5624-8f6e-4e00-acd5-c9be6ef4e941 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/grub.cfg
  17.4GB: boot/initrd.img-2.6.31-14-generic
  17.4GB: boot/vmlinuz-2.6.31-14-generic
  17.4GB: initrd.img
  17.4GB: vmlinuz
```

---

### Post by oldfred on 2009-12-29
Your windows configuration looks normal. Part of the boot files are in the 100mb partition and the rest is in the main partition.

You are just missing the grub2 in the MBR. You still have windows. Follow the instructions for installing grub2 for Karmic 9.10. (upgrades to Karmic may still have grub legacy)

several versions all basically the same:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

After you install grub2 to the MBR run this to get the grub menu to find windows:
sudo update-grub

I just notices that you have a windows entry but it says 
/dev/sdc1
Did you have another drive installed and booting first? That is where it probably installed grub.

---

### Post by kalmos on 2009-12-29
Thank you very much, my problem is solved.

I followed these instructions:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

