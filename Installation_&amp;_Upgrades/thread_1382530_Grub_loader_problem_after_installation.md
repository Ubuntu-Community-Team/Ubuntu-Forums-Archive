---
title: "Grub loader problem after installation"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by mellice on 2010-01-16
Hi there,

I have a amd pc with windows 7 installed on it, I installed ubuntu 9.10 and the installation went well, but when the computer restarts after finish, the grub loader didn't show up and it log into windows 7
how can I fix this??
I want the grub loader to show up with the 2 operating systems with windows 7 is the default.

any help?
thanks.

---

### Post by kansasnoob on 2010-01-16
Did you do an actual dual-boot something like this:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

**Note: ignore what it says there about grub, 9.10 uses grub2 so you won't have a menu.lst.**

Or was it a Wubi install like this:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

If it was an actual dual-boot like in the first example boot your Live CD choosing to Try without changes ...... and go to Terminal and run this command:

```
sudo fdisk -l
```

BTW that's a lower case L.

Please post those results here.

---

### Post by Sylslay on 2010-01-16
press SHIFT , while booting (before, in grub1 was ESC). than 
You should get Grub menu with list OS installed on disk.
And than boot manual with some parametrs, like  gfxpayload=1034x768

ps. just found 

[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html) 
very well someone wrote about it on His blog, thx Harrison

ps. check my old post, meaby there is more info.

Old parametes I used the vga=792 variable instead of gfxpayload. It's deprecated but it works. On 1024x768 with intel i845 graphic card

---

### Post by mellice on 2010-01-16
actually this didn't solve the problem,
well I need to mention that I have two hard disks
the windows 7 is installed on one hard disk, and the ubuntu is installed on the second hard disk

---

### Post by mellice on 2010-01-16
I also want to mention that the new hard disk with ubuntu is 2 volumes, I set one as root "/" and the other home "/home"

---

### Post by Leppie on 2010-01-16
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by mellice on 2010-01-16
well, this is quite long :),
to help u out, I have 2 hard disks each 500 GB, Disk 0 contains 4 partitions, 1 swap, 2 ext4 for ubuntu one with mount / and the other /home.
The last volume in this Disk0 is netfs

the second hard disk in Disk1 with 2 ntfs volumes, one of them has windows 7 installed.
Thanks

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xefe8f36b

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   567,166,975   567,164,928   7 HPFS/NTFS
/dev/sda2    *    567,166,976   774,260,735   207,093,760  83 Linux
/dev/sda3         774,262,783   778,360,831     4,098,049   f W95 Ext d (LBA)
/dev/sda5         774,262,784   778,360,831     4,098,048  82 Linux swap / Solaris
/dev/sda4         778,360,832   976,764,927   198,404,096  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cd81cd8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620   976,751,999   771,955,380   f W95 Ext d (LBA)
/dev/sdb5         204,796,683   976,751,999   771,955,317   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.1 GB, 16131293184 bytes
25 heads, 25 sectors/track, 50410 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    31,506,431    31,504,384   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F69C78AF9C786BCD" LABEL="Stuff" TYPE="ntfs" 
/dev/sda2: UUID="33a89ec8-bc97-450f-a26d-8d550d06a40e" TYPE="ext4" 
/dev/sda4: UUID="313e22d4-28c4-402c-9e12-efc554d1e278" TYPE="ext4" 
/dev/sda5: UUID="f789c1a9-24f9-44dc-9d06-e6e99f9a2a81" TYPE="swap" 
/dev/sdb1: UUID="E234E33934E30EFB" TYPE="ntfs" 
/dev/sdb5: UUID="58E85C4BE85C2A10" LABEL="Data" TYPE="ntfs" 
/dev/sdc1: UUID="2E2288172287E1E7" LABEL="MELLICE" TYPE="ntfs" 

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
/dev/sdc1 on /media/MELLICE type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 33a89ec8-bc97-450f-a26d-8d550d06a40e
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
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 33a89ec8-bc97-450f-a26d-8d550d06a40e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=33a89ec8-bc97-450f-a26d-8d550d06a40e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 33a89ec8-bc97-450f-a26d-8d550d06a40e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=33a89ec8-bc97-450f-a26d-8d550d06a40e ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set e234e33934e30efb
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=33a89ec8-bc97-450f-a26d-8d550d06a40e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=313e22d4-28c4-402c-9e12-efc554d1e278 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f789c1a9-24f9-44dc-9d06-e6e99f9a2a81 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 290.3GB: boot/grub/core.img
 290.3GB: boot/grub/grub.cfg
 290.3GB: boot/initrd.img-2.6.31-14-generic
 290.3GB: boot/vmlinuz-2.6.31-14-generic
 290.3GB: initrd.img
 290.3GB: vmlinuz

---

### Post by Leppie on 2010-01-16
booting off the livecd, could you try the following:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda2 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
apt-get purge grub grub-pc grub-common
apt-get install grub-pc grub-common
exit
```
then reboot

---

### Post by mellice on 2010-01-17
this didn't help either, I even try to install the ubuntu again, but this time in the last step (the summery step) I clicked advanced and instruct it to install the boot into the windows 7 volume.
Well that's cause a problem, when I finished, and restarting a word Grub is show up but the computer hang there & I was forced to restart it again and again with no step forward :(
any help please:(

---

### Post by kansasnoob on 2010-01-17
> **mellice said:**
> this didn't help either, I even try to install the ubuntu again, but this time in the last step (the summery step) I clicked advanced and instruct it to install the boot into the windows 7 volume.
Well that's cause a problem, when I finished, and restarting a word Grub is show up but the computer hang there & I was forced to restart it again and again with no step forward :(
any help please:(

Well, since you reinstalled and changed things, we need to have you run the Boot Info Script again and post the new results. 

I hope when you said:

> I clicked advanced and instruct it to install the boot into the windows 7 volume

That you mean you installed grub2 to the mbr of sdb and not the Windows partition sdb1. That will certainly make things more complicated :(

Also please give a physical description of your drives, both SATA? both IDE? one of each? I assume sdc is a Live USB?

BTW you'd be doing me a favor if you'd post the RESULTS.txt as an attachment. Just right click on it and choose "compress", then use the little paper clip thingy at the top of this forums reply box to attach it. Or, if it's confusing, just do it the way you did before.

---

### Post by mellice on 2010-01-17
> That you mean you installed grub2 to the mbr of sdb and not the Windows partition sdb1. That will certainly make things more complicated 

Actually this is what happened:(
and I even can't fix my windows boot :(

---

### Post by kansasnoob on 2010-01-17
Well if you want to fix it we're going to have to see the results of a new Boot Info Script test.

---

### Post by Leppie on 2010-01-17
> **mellice said:**
> Actually this is what happened:(
and I even can't fix my windows boot :(
so you installed grub2 into the windows partition? or the mbr of sdb?

---

### Post by drs305 on 2010-01-17
To get at least one system booting, take a look at this howto:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by mellice on 2010-01-18
Well this is it, I tried to fix the windows boot loader using the windows 7 dvd by all ways and didn't work :(
so I installed windows and ubuntu again but this time on single hard disk :(
this is tooooooo bad

---

### Post by mellice on 2010-01-21
Well, what happen happened, but I thought I should post this as a solution for other people.
You have a hard disk with windows os installed on it and you want to install ubuntu on other hard disk, so you should do the following:

**NOTE: this solution is not tested, do it on your own!!**

1-Install ubuntu on the new hard disk, when you came to the summery step click advanced and instruct Grub to be installed on the MBR of the old hard disk.
2-After installation, go into bios settings and make the new hard disk is the default.

That's it.
please any one use this solution post a comment telling us the result.

---

### Post by Leppie on 2010-01-21
> **mellice said:**
> **NOTE: this solution is not tested, do it on your own!!**

1-Install ubuntu on the new hard disk, when you came to the summery step click advanced and instruct Grub to be installed on the MBR of the old hard disk.
2-After installation, go into bios settings and make the new hard disk is the default.
i think this is how you got into this trouble.
when using 2 drives, each dedicated to a system, do not go and place grub in the mbr of the windows drive. this is would be a good way to complicate things.
there are actually tons of threads on this issue and i'm sure there's also howto's and guides on this. using the forum's search function really isn't that hard...

---

