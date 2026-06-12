---
title: "Problem with GRUB"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by HP dv4 on 2009-12-28
This problem is my fault and I need help to fix it. When I installed Ubuntu on to my external hard drive I made a mistake during the installation somewhere. The GRUB needed to boot Ubuntu got installed on my laptop's internal drive. Now it will not boot the windows 7 that is installed on the internal drive with out the external drive being plugged in. And on the same note the external drive cannot be booted from on another computer because GRUB is not on it. Is there anyway to move GRUB, uninstall it from the internal drive, or anything without touching windows?

---

### Post by presence1960 on 2009-12-28
> **HP dv4 said:**
> This problem is my fault and I need help to fix it. When I installed Ubuntu on to my external hard drive I made a mistake during the installation somewhere. The GRUB needed to boot Ubuntu got installed on my laptop's internal drive. Now it will not boot the windows 7 that is installed on the internal drive with out the external drive being plugged in. And on the same note the external drive cannot be booted from on another computer because GRUB is not on it. Is there anyway to move GRUB, uninstall it from the internal drive, or anything without touching windows?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Hologide on 2009-12-28
I too have made the mistake of installing Ubuntu on an external hard drive, but ending up with GRUB on the internal hard drive.

Neither hard drive will boot, and if I try to get to Vista on the internal hard drive Grub goes straight into rescue mode and I can't do anything. 

All I want to do is boot vista right now, can anyone help?

---

### Post by presence1960 on 2009-12-28
> **Hologide said:**
> I too have made the mistake of installing Ubuntu on an external hard drive, but ending up with GRUB on the internal hard drive.

Neither hard drive will boot, and if I try to get to Vista on the internal hard drive Grub goes straight into rescue mode and I can't do anything. 

All I want to do is boot vista right now, can anyone help?

Boot your Vista install DVD (not recovery DVD). If you don't have one go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the iso for your Vista. Then burn the iso as an image to CD. This will allow you to boot that CD and access Vista Recovery only, you will not be able to use this CD to install Vista.

Boot that CD or the vista install DVD and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista. This will restore Vista's bootloader to MBR of the internal disk and allow you to boot into Vista again. When you are ready post back- it is a very simple procedure to install GRUB to your external disk.

If none of the above works I will need more detailed info. Do this: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by HP dv4 on 2009-12-28
mistake, had to erase

---

### Post by Hologide on 2009-12-28
Thanks Presence! I've managed to boot Vista again now, so thanks very much. I'll sleep easy now, and hopefully get GRUB on the right hard drive tomorrow!! I've received a nasty blue screen error, but probably more to do with the new ext. hard drive than the OS changes. Hopefully....

---

### Post by HP dv4 on 2009-12-28
I got it/ The results are long but here they are. I don't really know what you meant by the # on the toolbar though.
> ============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=6b3057d1-a964-460d-b45f-b2d6766a86fd)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x974097a6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   290,914,303   290,914,241   7 HPFS/NTFS
/dev/sda2         290,914,304   312,573,951    21,659,648   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f3587

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   360,723,509   360,723,447   c W95 FAT32 (LBA)
/dev/sdb2         360,723,510   488,392,064   127,668,555   5 Extended
/dev/sdb5         360,723,573   483,090,614   122,367,042  83 Linux
/dev/sdb6         483,090,678   488,392,064     5,301,387  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="BC200B32200AF2E6" TYPE="ntfs" 
/dev/sda2: UUID="0240F31E40F316DF" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sdb1: UUID="12F8-1D28" TYPE="vfat" 
/dev/sdb5: UUID="6b3057d1-a964-460d-b45f-b2d6766a86fd" TYPE="ext4" 
/dev/sdb6: UUID="8bebb6cd-4e08-416f-a63f-52cbe1d9c75e" TYPE="swap" 

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


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 6b3057d1-a964-460d-b45f-b2d6766a86fd
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
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6b3057d1-a964-460d-b45f-b2d6766a86fd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6b3057d1-a964-460d-b45f-b2d6766a86fd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6b3057d1-a964-460d-b45f-b2d6766a86fd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6b3057d1-a964-460d-b45f-b2d6766a86fd ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bc200b32200af2e6
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0240f31e40f316df
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=6b3057d1-a964-460d-b45f-b2d6766a86fd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=8bebb6cd-4e08-416f-a63f-52cbe1d9c75e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 184.6GB: boot/grub/grub.cfg
 184.6GB: boot/initrd.img-2.6.31-14-generic
 184.6GB: boot/vmlinuz-2.6.31-14-generic
 184.6GB: initrd.img
 184.6GB: vmlinuz

---

### Post by presence1960 on 2009-12-28
I assume since you are booting into Windows again that you ran the boot info script before fixing Windows? I say this because the script results show GRUB is on MBR of sda not Windows.

As long as you can boot into windows you can install GRUB to MBR of external. To do so boot the Ubuntu Live CD with your external plugged in. Choose 'try Ubuntu without any changes..." When the desktop loads open a terminal and run ```
sudo mount /dev/sdb5 /mnt
```
This will mount your Ubuntu root partition.

Next run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
This will put GRUB on MBR of sdb. Reboot and make sure you set USB/Removeable to boot before Hard Disk in BIOS. When your external is plugged in @ boot GRUB will take over, if the external is unplugged it will boot right to windows.

---

### Post by HP dv4 on 2009-12-28
OK that only fixed have of the problem. I can now take my external drive to another computer and boot from it, but when the drve is unplugged from my computer I can't load Windows. When it is unplugged the GRUB pops up and says no such disk (which I assume it's talking about the external drive) and then it says GRUB rescue. What do I do now?

---

### Post by presence1960 on 2009-12-28
> **HP dv4 said:**
> OK that only fixed have of the problem. I can now take my external drive to another computer and boot from it, but when the drve is unplugged from my computer I can't load Windows. When it is unplugged the GRUB pops up and says no such disk (which I assume it's talking about the external drive) and then it says GRUB rescue. What do I do now?

Unplug the external and do this:

Boot your Vista install DVD (not recovery DVD). If you don't have one go here and download the iso for your Vista. Then burn the iso as an image to CD. This will allow you to boot that CD and access Vista Recovery only, you will not be able to use this CD to install Vista.

Boot that CD or the vista install DVD and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista. This will restore Vista's bootloader to MBR of the internal disk and allow you to boot into Vista again.

---

### Post by HP dv4 on 2009-12-29
I will do that, but I need to know something first. Will this still work if I'm running Windows 7? I just upgraded to Windows 7 from Vista. Can I boot from the Windows 7 upgrade disk to do the same thing? This isn't going to mess with my files, reinstall Windows, or damage anything is it?

---

### Post by presence1960 on 2009-12-29
> **HP dv4 said:**
> I will do that, but I need to know something first. Will this still work if I'm running Windows 7? I just upgraded to Windows 7 from Vista. Can I boot from the Windows 7 upgrade disk to do the same thing? This isn't going to mess with my files, reinstall Windows, or damage anything is it?

Same process for Windows 7. If you need to download & burn that CD for Recovery make sure you download Windows 7. If you have a Windows 7 install DVD use that. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Windows 7.

---

### Post by HP dv4 on 2009-12-29
Thanks Presence 1960!
You fixed my problem with GRUB! I don't hace a clue what all of those command line entries were, but other than that it was quite a learning experience. Now I can boot form my external drive on another computer and I can boot windows on my computer without the external drive attached. THANK YOU!

---

### Post by presence1960 on 2009-12-29
> **HP dv4 said:**
> Thanks Presence 1960!
You fixed my problem with GRUB! I don't hace a clue what all of those command line entries were, but other than that it was quite a learning experience. Now I can boot form my external drive on another computer and I can boot windows on my computer without the external drive attached. THANK YOU!

You are welcome! Glad you got it working. Enjoy your dual boot setup.

---

