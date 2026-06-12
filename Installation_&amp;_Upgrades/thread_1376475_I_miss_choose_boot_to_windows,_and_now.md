---
title: "I miss choose boot to windows, and now?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by clapton on 2010-01-09
Hello!
On Ubuntu installation I didn't choose dualboot with windows.7
I don't remember if needs or if exists any option.
Grub goes direct to ubuntu.
How can I fix this?

This is my RESULTS.txt

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00077140

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   362,371,071   362,164,224   7 HPFS/NTFS
/dev/sda3         362,371,072   862,642,304   500,271,233   7 HPFS/NTFS
/dev/sda4         862,642,305   976,768,064   114,125,760   5 Extended
/dev/sda5         862,642,368   968,558,849   105,916,482  83 Linux
/dev/sda6         968,558,913   976,768,064     8,209,152  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="EA980E4A980E15AB" TYPE="ntfs" 
sda2: UUID="A44C64F24C64C122" TYPE="ntfs" 
sda3: UUID="6218FF3818FF0A35" LABEL="lixo" TYPE="ntfs" 
sda5: UUID="c90a8f99-1fed-4142-9ca2-9bea79bb102f" TYPE="ext4" 
sda6: UUID="06c37e30-b43c-4b96-8d6d-d3d85204f5db" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
none on /proc type proc (rw)
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
gvfs-fuse-daemon on /home/marco/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marco)
/dev/sda2 on /media/A44C64F24C64C122 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/EA980E4A980E15AB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/lixo type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================
```

---

### Post by darkod on 2010-01-09
You mean there is no grub menu at all showing?
That can happen only if ubuntu is the only OS on the computer. You are sure you still have your windows right?
You can try this: Boot into ubuntu and in terminal execute:
sudo update-grub

That should update the grub menu with windows.

---

### Post by clapton on 2010-01-09
> **darkod said:**
> You mean there is no grub menu at all showing?
That can happen only if ubuntu is the only OS on the computer. You are sure you still have your windows right?
You can try this: Boot into ubuntu and in terminal execute:
sudo update-grub

That should update the grub menu with windows.

Yes, I've got windows as you can see at RESULTS.txt

Something happens at installation :S

---

### Post by darkod on 2010-01-09
Did you try running update-grub? I can't see the content of your grub.cfg file, you didn't copy the full content of the results.txt file.

Also, at the top of the results file you can see at sda5 it says OS Ubuntu Karmic (development branch). I've never seen that before. Are you running some development version or the standard desktop ubuntu?

---

### Post by clapton on 2010-01-09
```
marco@marco-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

I need boot Windows7 :shock:

---

### Post by clapton on 2010-01-09
RESULTS.txt

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00077140

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   362,371,071   362,164,224   7 HPFS/NTFS
/dev/sda3         362,371,072   862,642,304   500,271,233   7 HPFS/NTFS
/dev/sda4         862,642,305   976,768,064   114,125,760   5 Extended
/dev/sda5         862,642,368   968,558,849   105,916,482  83 Linux
/dev/sda6         968,558,913   976,768,064     8,209,152  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="EA980E4A980E15AB" TYPE="ntfs" 
sda2: UUID="A44C64F24C64C122" TYPE="ntfs" 
sda3: UUID="6218FF3818FF0A35" LABEL="lixo" TYPE="ntfs" 
sda5: UUID="c90a8f99-1fed-4142-9ca2-9bea79bb102f" TYPE="ext4" 
sda6: UUID="06c37e30-b43c-4b96-8d6d-d3d85204f5db" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
none on /proc type proc (rw)
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
gvfs-fuse-daemon on /home/marco/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marco)
/dev/sda2 on /media/A44C64F24C64C122 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/EA980E4A980E15AB type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/lixo type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set c90a8f99-1fed-4142-9ca2-9bea79bb102f
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
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c90a8f99-1fed-4142-9ca2-9bea79bb102f
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=c90a8f99-1fed-4142-9ca2-9bea79bb102f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c90a8f99-1fed-4142-9ca2-9bea79bb102f
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=c90a8f99-1fed-4142-9ca2-9bea79bb102f ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
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
UUID=c90a8f99-1fed-4142-9ca2-9bea79bb102f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=06c37e30-b43c-4b96-8d6d-d3d85204f5db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 441.6GB: boot/grub/core.img
 441.6GB: boot/grub/grub.cfg
 441.6GB: boot/initrd.img-2.6.31-11-generic
 441.6GB: boot/vmlinuz-2.6.31-11-generic
 441.6GB: initrd.img
 441.6GB: vmlinuz
```

---

### Post by clapton on 2010-01-09
I think this problem is similar to this one

[http://http://ubuntuforums.org/showthread.php?p=86250147]("http://ubuntuforums.org/showthread.php?p=86250147")
I don't know how to config my particular case.

---

### Post by darkod on 2010-01-09
ls: cannot access /var/lib/os-prober/mount/boot

Out of whatever reason the os-prober seems unable to search for other OSs. Try adding the entry manually to 40_custom. Open the file by executing:
sudo gedit /etc/grub.d/40_custom

At the end add the following:

menuentry "Windows 7 custom" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set EA980E4A980E15AB
chainloader +1
}

Save and close the file. Then run again update-grub, reboot and see if it worked.

---

### Post by clapton on 2010-01-09
Didn't work.

Grub menu didn't appears

---

### Post by darkod on 2010-01-09
Hmmm, not sure why it didn't work. I'm out of ideas sorry. Unless you are willing to reinstall grub2 but not sure if it would help with the os-prober.

---

