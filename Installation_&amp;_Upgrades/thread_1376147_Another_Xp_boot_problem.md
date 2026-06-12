---
title: "Another Xp boot problem"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by sungman on 2010-01-08
I've tried to read all the other forum...and I got nothing out of it. I am completely new to this have no knowledge of ubuntu. I just install ubuntu on my computer by a second partition and ubuntu boots fine but xp will not anymore, all I get is the black splash screen.

---

### Post by louieb on 2010-01-08
Follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

Welcome to Ubuntu and Ubuntu forums.

---

### Post by sungman on 2010-01-08
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4bec4beb

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   302,166,584   302,166,522   7 HPFS/NTFS
/dev/sda2    *    469,914,480   488,391,119    18,476,640   c W95 FAT32 (LBA)
/dev/sda3         302,166,585   469,901,249   167,734,665   5 Extended
/dev/sda5         302,166,648   462,993,299   160,826,652  83 Linux
/dev/sda6         462,993,363   469,901,249     6,907,887  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="8C1838DD1838C7CA" LABEL="HP_PAVILION" TYPE="ntfs" 
sda2: LABEL="HP_RECOVERY" UUID="4A03-7C99" TYPE="vfat" 
sda5: UUID="ea6da282-2847-4e17-a49b-c2b7642d226d" TYPE="ext4" 
sda6: UUID="43dd821e-79a7-453b-9a34-466d1628a8c2" TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

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
search --no-floppy --fs-uuid --set ea6da282-2847-4e17-a49b-c2b7642d226d
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ea6da282-2847-4e17-a49b-c2b7642d226d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ea6da282-2847-4e17-a49b-c2b7642d226d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ea6da282-2847-4e17-a49b-c2b7642d226d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ea6da282-2847-4e17-a49b-c2b7642d226d ro single 
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
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8c1838dd1838c7ca
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 4a03-7c99
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ea6da282-2847-4e17-a49b-c2b7642d226d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=43dd821e-79a7-453b-9a34-466d1628a8c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/core.img
 154.7GB: boot/grub/grub.cfg
 154.7GB: boot/initrd.img-2.6.31-14-generic
 154.7GB: boot/vmlinuz-2.6.31-14-generic
 154.7GB: initrd.img
 154.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by louieb on 2010-01-08
Don't see anything wrong at 1st glance.  

Did you try the entry that reads **Windows NT/2000/XP (on /dev/sda2**) ?

You should get the windows boot menu and can chose XP from there.

---

### Post by sungman on 2010-01-08
I've tried to access the command prompt using the recovery disk that I have but it would not load the command prompt. Is there another way of accessing the Window boot menu or obtaining another disk?

---

### Post by louieb on 2010-01-08
Do you get the same thing when you try both windows options in the GRUB menu? 

If not what is the difference? 

I've never used it but I've see it recommended quite a few times. [UBCD for Windows]("http://www.ubcd4win.com/")

---

### Post by presence1960 on 2010-01-08
The only thing I can see which may or may not make a difference is the boot flag is on the Recovery Partition (sda2) instead of on XP's partition (sda1).

Boot from the Live CD and choose "try ubuntu without any changes...", when the desktop loads open a terminal and run ```
gksu gparted
```

Right click on the sda2 partition and choose "Manage Flag". Untick the boot flag. Now right click on sda1 and choose "Manage Flag". Tick the boot flag. Now click the Apply (green check mark) on the top toolbar. When done reboot and see if you can boot to windows.

---

### Post by sungman on 2010-01-08
Before I try the live cd suggestion I will say that when I try to load Window media center, the first option, I get the black screen with the splash, but when I load the second optionI get an error message about Disk I/ O error , No system disk.

Not sure if that'll help, I'll try that terminal trick next

---

### Post by presence1960 on 2010-01-08
> **sungman said:**
> Before I try the live cd suggestion I will say that when I try to load Window media center, the first option, I get the black screen with the splash, but when I load the second optionI get an error message about Disk I/ O error , No system disk.

Not sure if that'll help, I'll try that terminal trick next

it is not a terminal trick. You can also start gparted by going System > Administration > Gparted. I like to get people used to using terminal for simple stuff so they are not loathe when they really need to use it. Either the terminal command or what I just posted will open gparted for you. That is the beauty of linux- there are usually multiple ways to accomplish each task.

There is no trick you are just using gparted to change the boot flag from sda2 to sda1.

To boot a Recovery Partition (sda2) on an HP you usually need to press a certain key which your HP documentation will explain. You may even see a message very quickly when you begin booting the machine telling you which key to press for Recovery.

---

### Post by sungman on 2010-01-08
Changing the flag hasn't changed anything. Grub still loads and window still won't work, and the system recovery menu will not load(not that it has before)

---

### Post by presence1960 on 2010-01-08
> **sungman said:**
> Changing the flag hasn't changed anything. Grub still loads and window still won't work, and the system recovery menu will not load(not that it has before)

Let's try to get windows booting first, then reinstall GRUB. Boot from the Ubuntu Live CD. Choose "try ubuntu without any changes...", when the desktop loads open a terminal and run ```
sudo apt-get install lilo
```

Once lilo is installed run in terminal ```
sudo lilo -M /dev/sda mbr
```

This will put windows back on the MBR. Reboot without the Live CD and see if you boot right to windows. If you do boot again from the Live CD to restore GRUB. Choose "try ubuntu without any changes..." again, when the desktop loads open a terminal and mount your / partition by running ```
sudo mount /dev/sda5 /mnt
```

Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
which will put GRUB back on MBR. Reboot without the Live CD and boot into Ubuntu. Open a terminal and run ```
sudo update-grub
```
Now reboot & see if you can boot windows from GRUB.

---

### Post by louieb on 2010-01-09
> **presence1960 said:**
> sudo apt-get install lilo

Hello presence1960. I've seen lilo suggested as a way to restore the Windows XP boot loader to the MBR before. Do you know if it works for Vista/Win7 too?

---

### Post by presence1960 on 2010-01-09
> **louieb said:**
> Hello presence1960. I've seen lilo suggested as a way to restore the Windows XP boot loader to the MBR before. Do you know if it works for Vista/Win7 too?

As far as I know it does, but I have never done it with Vista/7. The person I can think of who will know is meierfra, maybe he will see this and respond.

---

### Post by meierfra. on 2010-01-10
> I've seen lilo suggested as a way to restore the Windows XP boot loader to the MBR before. Do you know if it works for Vista/Win7 too?

Yes, it does.   The XP, Vista/7 and Lilo MBRsall do the same thing:  Load the code in the boot sector of the partition with the boot flag. 

Disclaimer:  Although they do the same thing, they do it in slightly different ways. So I'm sure there are some cases (strange bios, etc) where the Lilo MBR  will fail to boot XP (Vista, Window 7).  But personally I have never encountered such a case.

---

