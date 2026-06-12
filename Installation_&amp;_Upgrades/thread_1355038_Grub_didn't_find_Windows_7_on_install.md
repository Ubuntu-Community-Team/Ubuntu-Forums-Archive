---
title: "Grub didn't find Windows 7 on install"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by PendragonUK on 2009-12-14
I have just installed Ubuntu 9.10 (32bit), Grub appears not to know about the Windows instillation. I'm not familiar with Grub2 and can't fix. Can someone please point me in the right direction, it would be nice to get back into Windows when I need to...

I have tried ```
update-grub
```

> 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-16-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done


Not sure why Windows is hiding from Ubuntu, in the past they have happily lived together. Mind you it's Windows 7 not XP, that has changed.

---

### Post by darkod on 2009-12-14
What does the command:
sudo fdisk -l

show for the partitions?

---

### Post by PendragonUK on 2009-12-14
```

pen@pen-desktop:~$ sudo fdisk -l
[sudo] password for pen: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64648d65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fbd5c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2              13       30385   243960832    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders

```

---

### Post by darkod on 2009-12-14
It looks normal except that it's not showing any partitions on /dev/sdb.
To get more detailed info you can download the script in my signature, move it on desktop for example and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of detailed info about your boot process. Look inside, you might find something interesting. If you want to, post the content of the file here and please wrap it with CODE tags also for easier reading (it's long).

---

### Post by PendragonUK on 2009-12-14
Here is the result:

The 500Gb drive was the only drive in the PC around a month ago when I had Ubuntu and XP installed. It's now just used as storage with the 120 with ubuntu and the 250 with W7 64bit

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64648d65

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8969a6e5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,502,783   976,500,736   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbd5c0a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   488,128,511   487,921,664   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 33 MB, 33030144 bytes
2 heads, 32 sectors/track, 1008 cylinders, total 64512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b0e9b0e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32        64,447        64,416   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="becdfa3d-5b55-41af-bfe9-72e7e1023baf" TYPE="ext4" 
/dev/sda5: UUID="f4885287-dd08-4202-b67e-53e47f860dd1" TYPE="swap" 
/dev/sdc1: UUID="027A66D47A66C3CF" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc2: UUID="583E7BE63E7BBB96" LABEL="WIN-SYS" TYPE="ntfs" 
/dev/sdb1: UUID="ACA6C8BCA6C88872" LABEL="DATA-NTFS" TYPE="ntfs" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="32MB_STICK" UUID="5CE1-2B89" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/pen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pen)
/dev/sdd1 on /media/32MB_STICK type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f4885287-dd08-4202-b67e-53e47f860dd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic-pae
    .0GB: boot/vmlinuz-2.6.31-16-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by darkod on 2009-12-14
No specific problem as far as I can see.
I guess it's time to try manual entry. Open 40_custom file with:
sudo gedit /etc/grub.d/40_custom

And at the end add:

echo "Adding Windows 7 on /dev/sdc1" >&2
menuentry "Windows 7 on /dev/sdc1" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 027A66D47A66C3CF
chainloader +1
}

/dev/sdc should be your hd2 drive, that's why I used that in root=(hd2,1). Save and close the file. Do update-grub to generate the changes to grub.cfg, reboot and try it.

---

### Post by PendragonUK on 2009-12-14
Still no luck...

Output from update-grub

```
pen@pen-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-16-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by darkod on 2009-12-14
OK, I left the echo command on purpose. It should have said Adding Windows 7 too in those lines, even if the entry in grub menu doesn't work later. Something is fishy.
You noticed in the results file you have grub2 on sda, grub2 on sdb and grub1 on sdc. The grub2 on sdb seems to be poiting to a partition no longer there (#5 on the same disk, which doesn't exist any more).
I'm not sure if this is a big confusion between so many grubs. :)
Just to confirm, you have your /dev/sda, the 120GB disk as first option in boot order in BIOS right?

---

### Post by PendragonUK on 2009-12-14
yea 120Gb is plugged in the first SATA socket and first in the boot order. In the last few days I have been distro hopping a little with ATI driver issues. This may have lead to some interesting issues. At some time or other all of these drives would have been bootable win an OS or two. I realy must discover how to wipe the MBR when changing partition for a new setup.

---

### Post by darkod on 2009-12-14
I wonder if something is missing and that's why it can't find it. I'm talking about MBR of /dev/sdc. Lets try restoring the windows MBR there, no need to have grub1 there anyway.
IMPORTANT: Make /dev/sdc disk first in boot order. Windows requires that its disk is first in boot order when fixing MBR. Boot with win7 dvd and you have instructions here how to restore windows mbr with commands:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That should put windows mbr on /dev/sdc, your win7 disk.

Switch back /dev/sda first in boot order. Boot ubuntu. Try update-grub again.

---

### Post by PendragonUK on 2009-12-14
That's done, W7 has it's self sorted, put things back and did the update-grub with this result...


```
pen@pen-desktop:~$ sudo update-grub
[sudo] password for pen: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-16-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by darkod on 2009-12-14
Honestly, I'm running out of ideas. :( Everything is looking fine, and yet... You could try running the script again although I'm not expecting a lot new in the results. Just the mbr of /dev/sdc.

---

### Post by PendragonUK on 2009-12-14
I did get one odd thing. I changed the boot order in the bios for doing the MBR thing for W7. I got a GRUB error because I missed the "key to boot CD" message.  
So at the time, before W7 was fixed there was a Grub on the 250Gb drive...

---

### Post by darkod on 2009-12-14
I noticed that in the results file, there was some grub1 on /dev/sdc. But it shouldn't have made a difference, and now it's definitely not there after windows mbr restore.

---

### Post by PendragonUK on 2009-12-14
Yea just to check I swapped the boot order in the BIOS and have successfully booted into W7.

---

### Post by darkod on 2009-12-14
Lets try to reinstall grub2 on /dev/sda too, just in case. Boot with ubuntu 9.10 cd, Try Ubuntu option, in terminal execute:

sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
sudo update-grub

Take the cd out and reboot. See if it makes a change.

---

### Post by PendragonUK on 2009-12-14
I'm typing this from the Boot CD...

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ 


```

as you can see it was all going so well till the last instruction...

---

### Post by darkod on 2009-12-14
Sorry, my mistake. You can't update it because you're on the LiveCD. Just reboot without the cd, and I think win7 will not show up yet, boot ubuntu from the hdd and then do update-grub.

---

### Post by PendragonUK on 2009-12-14
```
pen@pen-desktop:~$ sudo update-grub
[sudo] password for pen: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-16-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
pen@pen-desktop:~$
```

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64648d65

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8969a6e5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,502,783   976,500,736   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbd5c0a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   488,128,511   487,921,664   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 33 MB, 33030144 bytes
2 heads, 32 sectors/track, 1008 cylinders, total 64512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b0e9b0e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32        64,447        64,416   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="becdfa3d-5b55-41af-bfe9-72e7e1023baf" TYPE="ext4" 
/dev/sda5: UUID="f4885287-dd08-4202-b67e-53e47f860dd1" TYPE="swap" 
/dev/sdc1: UUID="027A66D47A66C3CF" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc2: UUID="583E7BE63E7BBB96" LABEL="WIN-SYS" TYPE="ntfs" 
/dev/sdb1: UUID="ACA6C8BCA6C88872" LABEL="DATA-NTFS" TYPE="ntfs" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="32MB_STICK" UUID="5CE1-2B89" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/pen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pen)
/dev/sdd1 on /media/32MB_STICK type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
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

"Adding Windows 7 on /dev/sdc1" >&2
menuentry "Windows 7 on /dev/sdc1" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 027A66D47A66C3CF
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f4885287-dd08-4202-b67e-53e47f860dd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic-pae
    .0GB: boot/vmlinuz-2.6.31-16-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by darkod on 2009-12-14
This line you put in 40_custom:
[COLOR=Red] "Adding Windows 7 on /dev/sdc1" >&2[/COLOR]

needs to be

echo "Adding...

Although I can't see it interfering.

---

### Post by PendragonUK on 2009-12-14
Put that right still no luck. This is a bugger... I can swap by changing the boot order but that is going to ware thin quick enough...

no option to swap back to old style grub, or lilo for that matter

---

### Post by darkod on 2009-12-14
This is very strange. I'm out of ideas, sorry. :(

It's not whether it's new or old grub, it's just not finding win7. :(

---

### Post by darkod on 2009-12-14
I found something which might help. Insert this line also in the entry in 40_custom:

echo "Adding Windows 7 on /dev/sdc1" >&2
menuentry "Windows 7 on /dev/sdc1" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 027A66D47A66C3CF
[COLOR=Red]drivemap -s (hd0) ${root}[/COLOR]
chainloader +1
}

Of course, update-grub follows as always. And reboot to check if it's working. Is it displaying Adding Windows 7 now when you do the update command?

---

### Post by PendragonUK on 2009-12-14
No luck, do you need any more info?

---

### Post by PendragonUK on 2009-12-14
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64648d65

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8969a6e5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,502,783   976,500,736   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbd5c0a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   488,128,511   487,921,664   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 33 MB, 33030144 bytes
2 heads, 32 sectors/track, 1008 cylinders, total 64512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b0e9b0e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32        64,447        64,416   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="becdfa3d-5b55-41af-bfe9-72e7e1023baf" TYPE="ext4" 
/dev/sda5: UUID="f4885287-dd08-4202-b67e-53e47f860dd1" TYPE="swap" 
/dev/sdc1: UUID="027A66D47A66C3CF" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc2: UUID="583E7BE63E7BBB96" LABEL="WIN-SYS" TYPE="ntfs" 
/dev/sdb1: UUID="ACA6C8BCA6C88872" LABEL="DATA-NTFS" TYPE="ntfs" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="32MB_STICK" UUID="5CE1-2B89" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/pen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pen)
/dev/sdd1 on /media/32MB_STICK type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
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

echo "Adding Windows 7 on /dev/sdc1" >&2
menuentry "Windows 7 on /dev/sdc1" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 027A66D47A66C3CF
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f4885287-dd08-4202-b67e-53e47f860dd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic-pae
    .0GB: boot/vmlinuz-2.6.31-16-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz
```

I'm sure some of the issues are related to the extra little partition W7 makes on install. silly 100Mb partition for no damn reason...

---

### Post by darkod on 2009-12-14
The custom win7 entry is not even showing in grub menu???

---

### Post by PendragonUK on 2009-12-14
I have not seen a menu at start up LOL

---

### Post by PendragonUK on 2009-12-14
Just rebooted to check...

Just after the POST ends and a second before the Ubuntu logo appears for half a second on the left hand side of the screen the messages "Grub loading" or "loading Grub" one of the two, maybe on screen for less than flash, quarter of a second.

---

### Post by darkod on 2009-12-14
Yeah, not seeing win7 ubuntu is acting like it's the only OS, in that case it doesn't show the menu. Just for information, holding the SHIFT key makes grub show the menu even if it's only OS.
Sorry, but I have no solution for your problem. Maybe someone with more experience will jump in. :)

---

### Post by PendragonUK on 2009-12-14
I have just read something while reading about boot managers. 

> 10.21.2009.
v3.6 can boot Windows7. Windows7 automatically creates a 100MB, NTFS type boot partition, that partition should be selected during MasterBooter installation.

Should we be pointing Grub to the first small partition even though it's not flagged as bootable?

---

### Post by PendragonUK on 2009-12-14
Got that the wrong way around now working.

---

### Post by PendragonUK on 2009-12-14
Any way of forcing the Grub menu to appear? might be too fast for my LCD monitor to respond to the change in screen before the information is removed? Just might be set to something silly like 1 or zero??

I think we may have this licked...

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdd1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64648d65

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8969a6e5

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,502,783   976,500,736   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0fbd5c0a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   488,128,511   487,921,664   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 33 MB, 33030144 bytes
2 heads, 32 sectors/track, 1008 cylinders, total 64512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b0e9b0e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32        64,447        64,416   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="becdfa3d-5b55-41af-bfe9-72e7e1023baf" TYPE="ext4" 
/dev/sda5: UUID="f4885287-dd08-4202-b67e-53e47f860dd1" TYPE="swap" 
/dev/sdc1: UUID="027A66D47A66C3CF" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc2: UUID="583E7BE63E7BBB96" LABEL="WIN-SYS" TYPE="ntfs" 
/dev/sdb1: UUID="ACA6C8BCA6C88872" LABEL="DATA-NTFS" TYPE="ntfs" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="32MB_STICK" UUID="5CE1-2B89" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/pen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pen)
/dev/sdd1 on /media/32MB_STICK type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set becdfa3d-5b55-41af-bfe9-72e7e1023baf
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
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

echo "Adding Windows 7 on /dev/sdc2" >&2
menuentry "Windows 7 on /dev/sdc2" {
insmod ntfs
set root=(hd2,1)
search --no-floppy --fs-uuid --set 027A66D47A66C3CF
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=becdfa3d-5b55-41af-bfe9-72e7e1023baf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f4885287-dd08-4202-b67e-53e47f860dd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic-pae
    .0GB: boot/vmlinuz-2.6.31-16-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

