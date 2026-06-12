---
title: "Dualboot - Windows 7/Ubuntu 9.10 - Windows 7 won't boot"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by KillerKellerjr on 2010-01-11
Fresh install of Windows 7 (installed 1st) then a fresh install of Ubuntu 9.10 with the GRUB2 as the bootloader & EXT4, they are both installed on the same drive, different partitions of course. I am unable to boot Windows 7 when I select it from the menu, PC just reboots a second after selecting Windows 7 to boot. Any help here is much appreciated!  

I need Windows for work purposes when I am on Emergency Support for programs that only run under Windows.  Otherwise I choose Ubuntu as my OS of choice!

---

### Post by studmf on 2010-01-11
[FONT=Arial][SIZE=2][COLOR=red]**Be sure to take note of YOUR Ubuntu Partition and /boot Partition prior to beginning**[/COLOR][/SIZE][/FONT]

[FONT=Arial][SIZE=2]Try using the tools in your windows 7 disc to check for errors and fix the MBR/bootloader, after that restore grub2 by Using Ubuntu 9.10 livecd[/SIZE][/FONT]
[SIZE=2][FONT=Arial]Here assuming the Ubuntu partition is *sda7 *and /boot partition is *sda6* (if you have a separate /boot partition).[/FONT][/SIZE]

[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Boot up ubuntu from the livecd,open terminal and run:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]sudo -i[/SIZE][/FONT]
[FONT=Arial][SIZE=2]mount [/SIZE][/FONT][FONT=Arial][SIZE=2]/dev/sda7 /mnt[/SIZE][/FONT]
[FONT=Arial][SIZE=2]mount /dev/sda6 /mnt/boot #skip this one if not have a separate /boot partition[/SIZE][/FONT]
[FONT=Arial][SIZE=2]grub-install --root-directory=/mnt/ /dev/sda[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]If you are missing &#8220;grub.cfg&#8221; file,use following to recreate:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]mount --bind /proc /mnt/proc[/SIZE][/FONT]
[FONT=Arial][SIZE=2]mount --bind /dev /mnt/dev[/SIZE][/FONT]
[FONT=Arial][SIZE=2]mount --bind /sys /mnt/sys[/SIZE][/FONT]
[FONT=Arial][SIZE=2]chroot /mnt update-grub[/SIZE][/FONT]
[FONT=Arial][SIZE=2]umount /mnt/sys[/SIZE][/FONT]
[FONT=Arial][SIZE=2]umount /mnt/dev[/SIZE][/FONT]
[FONT=Arial][SIZE=2]umount /mnt/procexit[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]After the boot command, you&#8217;ll go into grub2 menu.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Select to boot up ubuntu,and run this command to restore grub:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]sudo grub-install /dev/sda[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Note- Found on Ubuntuguide.net[/SIZE][/FONT]

---

### Post by oldfred on 2010-01-11
You will need to boot with your Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd
How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I am sorry I have copied so much off the forums I do not know who to credit.

---

### Post by presence1960 on 2010-01-11
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I would do this to see exactly your setup & boot process before making any changes.

---

### Post by KillerKellerjr on 2010-01-11
Just a note that I have tried a few things before posting. One being to use that os-prober and then redoing Grub2 but that did not work so I am posting here.  Thanks for any and all help!



```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x358a3589

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    43,471,889    43,471,827   7 HPFS/NTFS
/dev/sda2          77,352,975   156,296,384    78,943,410   5 Extended
/dev/sda5          77,353,038   152,970,929    75,617,892  83 Linux
/dev/sda6         152,970,993   156,296,384     3,325,392  82 Linux swap / Solaris
/dev/sda3          43,471,890    77,352,974    33,881,085   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1037 MB, 1037828096 bytes
32 heads, 62 sectors/track, 1021 cylinders, total 2027008 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00038f5d

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             62     2,025,663     2,025,602   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="BEF0A0BAF0A07A73" TYPE="ntfs" 
sda5: UUID="632b95ad-d816-45e6-beaf-0d27d9fc2da5" TYPE="ext4" 
sda6: UUID="cc17feaa-1f8c-4a03-a1be-a3af48596cbb" TYPE="swap" 
sda3: UUID="108FF83071B8515E" LABEL="HD_Shared" TYPE="ntfs" 
sdf1: LABEL="" UUID="E3B7-D9CB" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdf1 on /cdrom type vfat (rw)
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
search --no-floppy --fs-uuid --set 632b95ad-d816-45e6-beaf-0d27d9fc2da5
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 632b95ad-d816-45e6-beaf-0d27d9fc2da5
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=632b95ad-d816-45e6-beaf-0d27d9fc2da5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 632b95ad-d816-45e6-beaf-0d27d9fc2da5
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=632b95ad-d816-45e6-beaf-0d27d9fc2da5 ro single 
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 632b95ad-d816-45e6-beaf-0d27d9fc2da5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=632b95ad-d816-45e6-beaf-0d27d9fc2da5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 632b95ad-d816-45e6-beaf-0d27d9fc2da5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=632b95ad-d816-45e6-beaf-0d27d9fc2da5 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set bef0a0baf0a07a73
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
UUID=632b95ad-d816-45e6-beaf-0d27d9fc2da5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cc17feaa-1f8c-4a03-a1be-a3af48596cbb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  39.6GB: boot/grub/core.img
  39.6GB: boot/grub/grub.cfg
  39.6GB: boot/initrd.img-2.6.31-14-generic
  39.6GB: boot/initrd.img-2.6.31-18-generic
  39.6GB: boot/vmlinuz-2.6.31-14-generic
  39.6GB: boot/vmlinuz-2.6.31-18-generic
  39.6GB: initrd.img
  39.6GB: initrd.img.old
  39.6GB: vmlinuz
  39.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by presence1960 on 2010-01-11
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM[/COLOR]

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
```
You did not mention that you removed windows XP from an XP/Windows 7 dual boot setup. See the red above. It would seem that when you installed windows 7 (clean install) you still had XP on the machine and it combined 7's bootloader with XP's.

You are going to have to try fixing 7's bootloader with the install DVD, See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and follow instructions for windows 7.

Reboot & check that you boot right to windows.
If so you mow need to restore GRUB to MBR. Boot the Ubuntu 9.10 Live Cd. Choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```
This will mount your ubuntu / partition. Then run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB back on MBR. reboot without Live CD and boot into Ubuntu, open a terminal and run ```
sudo update-grub
```
to refresh grub.cfg

Here is a link for that how to FYI: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Reboot & try booting windows 7 from GRUB.

---

### Post by tad1073 on 2010-01-12
What if you accidentally deleted bootmgr, mbr, etc.?

I have a storage partition and that was where they were located, I was doing some cleaning and accidentally deleted them.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   


```

---

### Post by KillerKellerjr on 2010-01-12
[SIZE="3"][COLOR="Red"]Hey tad1073 please start your own thread and don't hijack mine...Thanks [-X [/COLOR][/SIZE]

presence1960
tried your suggestion but no luck after installing Grub2 again Windows 7 wouldn't boot.  I ended up fixing the MBR again to the Windows 7 loader and installed...brace yourself...EasyBCD and poof I was able to dualboot into Windows 7 and Ubuntu so I am happy with that result.  Wish the Grub2 would work but oh well it works so I think I will leave it at that.  Thanks for your help in at least getting me to my result. :-P

---

### Post by tad1073 on 2010-01-12
Sorry, but I didn't want to start a new thread about a similar problem.:neutral:

---

### Post by presence1960 on 2010-01-12
> **tad1073 said:**
> What if you accidentally deleted bootmgr, mbr, etc.?

I have a storage partition and that was where they were located, I was doing some cleaning and accidentally deleted them.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   


```

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   [COLOR="Red"]/bootmgr /boot/bcd /Boot/BCD 
                       /Windows/System32/winload.exe[/COLOR]
You didn't delete bootmgr see red above. You can't delete MBR in the way that you can delete files from a file browser.

---

### Post by tad1073 on 2010-01-12
thanks, I got it fixed, but I wound up having to reinstall ubuntu.

---

