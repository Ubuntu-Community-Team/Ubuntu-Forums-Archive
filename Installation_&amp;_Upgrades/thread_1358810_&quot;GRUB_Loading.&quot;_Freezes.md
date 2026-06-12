---
title: "&quot;GRUB Loading.&quot; Freezes"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by psyboy55 on 2009-12-18
I recently installed Ubuntu 9.10 but when i try to boot it says "booting from local disk" then "GRUB Loading." and it just freezes. what do i do?

---

### Post by shredder12 on 2009-12-19
so, are you not even able to reach the grub-menu..?
try reinstalling grub2 using a live CD and see if it works..

---

### Post by LonelyLion on 2009-12-19
Me, too!  I have a dual partitioned drive.  The first partition is Vista, the second was U8.04 32-bit, which I wanted to overwrite with U9.10 64-bit.  I got the CD from the Ubuntu User magazine.  The installation seemed to go okay, but then GRUB locked up.  I went back to the troubleshooting section of the magazine and did pretty much what they said to do, and now GRUB starts up normally...except the GRUB menu shows U8.04 still installed.  I'm hesitant to try that, but as you can see, I can still access my computer via Vista.  Sorry, I don't mean to hijack the thread, but maybe our problems are related.

---

### Post by psyboy55 on 2009-12-19
This is getting very strange. Just yesterday i fixed it and got to my computer fine. now today it will only boot if i have 265mb or less of ram. im going to try it again soon but this is just very wierd.

---

### Post by darkod on 2009-12-19
> **LonelyLion said:**
> Me, too!  I have a dual partitioned drive.  The first partition is Vista, the second was U8.04 32-bit, which I wanted to overwrite with U9.10 64-bit.  I got the CD from the Ubuntu User magazine.  The installation seemed to go okay, but then GRUB locked up.  I went back to the troubleshooting section of the magazine and did pretty much what they said to do, and now GRUB starts up normally...except the GRUB menu shows U8.04 still installed.  I'm hesitant to try that, but as you can see, I can still access my computer via Vista.  Sorry, I don't mean to hijack the thread, but maybe our problems are related.

Depending how you installed the 9.10 you might actually have 8.04 still installed. If you do not instruct it to overwrite the 8.04 it will not do it by itself. You might lose data that way.
It will only install over the 8.04 if you select manual partitioning and install it on the same 8.04 partition formatting it.

---

### Post by darkod on 2009-12-19
> **psyboy55 said:**
> I recently installed Ubuntu 9.10 but when i try to boot it says "booting from local disk" then "GRUB Loading." and it just freezes. what do i do?

Download the script from my signature, move it to desktop for example, and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by psyboy55 on 2009-12-19
This file is very long but here it is. Also i have another ubuntu 9.10 on my second hard drive that doesnt work. It was accidentally put there. ill try to repartition that. 
note: reseting cmos didnt help
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb

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

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   486,833,759   486,833,697  83 Linux
/dev/sda2         486,833,760   488,279,609     1,445,850   5 Extended
/dev/sda5         486,833,823   488,279,609     1,445,787  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3584eeaf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   975,322,214   975,322,152  83 Linux
/dev/sdb2         975,322,215   976,768,064     1,445,850   5 Extended
/dev/sdb5         975,322,278   976,768,064     1,445,787  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="738708a1-19d3-4908-81b5-cdf24c2979ed" TYPE="ext4" 
/dev/sda5: UUID="1d0723bf-e067-4c69-a0a2-c56a30d6a6c9" TYPE="swap" 
/dev/sdb1: UUID="58453288-b131-4849-a0fc-f067d4b9f0a7" TYPE="ext4" 
/dev/sdb5: UUID="74d895c1-cc35-4d53-b587-8d409cd112bc" TYPE="swap" 

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
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)


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
search --no-floppy --fs-uuid --set 738708a1-19d3-4908-81b5-cdf24c2979ed
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 738708a1-19d3-4908-81b5-cdf24c2979ed
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=738708a1-19d3-4908-81b5-cdf24c2979ed ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 738708a1-19d3-4908-81b5-cdf24c2979ed
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=738708a1-19d3-4908-81b5-cdf24c2979ed ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 58453288-b131-4849-a0fc-f067d4b9f0a7
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=58453288-b131-4849-a0fc-f067d4b9f0a7 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 58453288-b131-4849-a0fc-f067d4b9f0a7
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=58453288-b131-4849-a0fc-f067d4b9f0a7 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
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
UUID=738708a1-19d3-4908-81b5-cdf24c2979ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1d0723bf-e067-4c69-a0a2-c56a30d6a6c9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

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
search --no-floppy --fs-uuid --set 58453288-b131-4849-a0fc-f067d4b9f0a7
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 58453288-b131-4849-a0fc-f067d4b9f0a7
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=58453288-b131-4849-a0fc-f067d4b9f0a7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 58453288-b131-4849-a0fc-f067d4b9f0a7
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=58453288-b131-4849-a0fc-f067d4b9f0a7 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
UUID=58453288-b131-4849-a0fc-f067d4b9f0a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=74d895c1-cc35-4d53-b587-8d409cd112bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by darkod on 2009-12-19
Just to confirm, your "good" install is on /dev/sda, the 250GB disk, right? Because first and second drive doesn't mean much. :)
Also, do you have your 250GB drive as first option in boot order in BIOS? You might be booting the old LILO grub.

---

### Post by psyboy55 on 2009-12-19
I dont know which one is the 250? its just numbers. The 250gb is the good one.

---

### Post by darkod on 2009-12-19
> **psyboy55 said:**
> I dont know which one is the 250? its just numbers. The 250gb is the good one.

[COLOR=Red] Disk /dev/sda: 250.0 GB, 250000000000 bytes[/COLOR]

And that is the disk which is first in boot order in BIOS right?

---

### Post by psyboy55 on 2009-12-19
In my bios both harddrives are numbers that are very similar. But i belive that the 250 boots first becuase if i boot the other one first it just gives me random numbers.

---

### Post by darkod on 2009-12-19
OK. Lets reinstall grub2 on your 250GB drive just in case. While booted with the cd in terminal execute:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd and see how it goes.

---

### Post by psyboy55 on 2009-12-19
2 quick questions. 
First: my root directory is just my username right?
second: how to i boot to terminal? i have two disks one alternate and one normal. im trying to use rescue mode on the alternate cd. Am i doing it right?

---

### Post by darkod on 2009-12-19
You root directory is your root partition, in your case /dev/sda1 (or the first partition on /dev/sda disk).
Use the normal disc and select Try Ubuntu option. It will load full ubuntu from the cd and works from the cd. You should have internet access, etc. Then just go in Applications-Accessories and open Terminal.
Execute those commands there. Because when running from the cd like that you are actually not using your hdd install, you have to mount your root partition at /mnt:

sudo mount /dev/sda1 /mnt

Then tell grub2 to install on the /dev/sda disk by using that directory as root directory:

sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by psyboy55 on 2009-12-19
o wait. I ran rescue mode. then it mounted the sda1 file system for my and it ran a shell. i then typed in the second command exactly as u told me.

it said installation finished. then check if the installation was right 

(hd0) /dev/sda
(hd1) /dev/sda

now im gonna reboot

EDIT: ops sorry i did not see your second post. ill try that next.

---

### Post by psyboy55 on 2009-12-19
IT WORKED!thank you thank you thank you!

---

### Post by darkod on 2009-12-19
No problem. Glad you got it sorted.

---

### Post by darkod on 2009-12-19
Note that until you delete the install on the 500GB disk (format it for example), grub will probably see it and add it to the list. Because that is the same version it can get confusing at times which one is the "good" one. I recommend getting rid of the old install ASAP if you're not using it and if it's not working at all.

---

