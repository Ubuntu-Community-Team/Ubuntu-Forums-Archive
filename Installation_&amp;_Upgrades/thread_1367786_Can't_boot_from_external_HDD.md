---
title: "Can't boot from external HDD"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by bryanlee1981 on 2009-12-29
I will start by saying that I am having trouble accessing an encrypted home folder on another drive. Now I'll give some details.

I have been running a dual boot of windows xp along with Suse 11.1 for quite a while.  I decided last week to install Ubuntu 9.1.  I installed it on an external hard drive that I had laying around with no problems at all.

After using it for a week or so I was very pleased and decided to go ahead and wipe out the internal HDD on my laptop and install Ubuntu all by it's lonesome.

I installed using the Ubuntu 9.1 Live cd and everything went along without a hitch until the reboot.  After rebooting I got the 

```
error no such device: xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

I was able to get past this by editing grub and removing a line.  This really isn't my issue but I'm just trying to be thorough.  

I was hoping to be able to just browse my external hard drive and copy over files from the home folder, but it appears that my home folder was encrypted although I was sure that i had not used this feature.

If I could somehow get the external to boot I would be able to just log in since I of course know the password, but I haven't been able to do that yet.

Is there a way to add the external hard drive to grub.cfg?  Would that even allow it to boot?  I don't know much about grub.

If I have left out any relevant info please let me know.

Thanks



........update.......

after doing some reading I found that i could run sudo update-grub to update grub and it's entries.  Here is the output from that.

```
bryan@laptop:~$ sudo update-grub
[sudo] password for bryan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
bryan@laptop:~$ 

```


..........update 2.........

i was able to add the external to the boot list by adding the line 
```
(hd1)	/dev/sdb
```
to /boot/grub/device.map

I am still unable to boot into the external drive.  My computer is set to boot to the usb drive first and I have tried to manually select USB as the boot drive.  When i try either of these i get a black screen with the blinking cursor in the upper left hand corner.

---

### Post by gosalia on 2009-12-29
I am really sorry if I am talking out of terms, but you seem to be having this problem, and I have got a solution for that...
 
I believe if you go into your BIOS (by clicking DEL (on normal computers) when your motherboard splash screen comes (before your grub)). Then select your EXTERNAL HARDDRIVE as your first booting priority. (I cannot help you with finding where it is, because every motherboard is different)
 
Then restart by clicking F10 and then clicking yes, or Y, then ENTER. This will restart your computer and you will be able to boot from your external harddrive, if that is what you want to do. 
 
Again, I cannot understand your problem, but with what I understand this may be your solution. If not, please don't yell, forgive me.

---

### Post by bryanlee1981 on 2009-12-29
Thanks for your reply but my issue isn't the boot order/precedence.  My computer has been set to boot from USB first (if present) since I installed Ubuntu last week.

---

### Post by presence1960 on 2009-12-29
I need more precise info than what you are giving. First if possible I need that long string of characters in the boot error- that is the UUID of the partition GRUB is looking to in trying to boot.

Then I need this: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with the external plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bryanlee1981 on 2009-12-29
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
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

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdd4ddd4d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   300,495,824   300,495,762  83 Linux
/dev/sda2         300,495,825   312,576,704    12,080,880   5 Extended
/dev/sda5         300,495,888   312,576,704    12,080,817  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,311,184   476,311,122  83 Linux
/dev/sdb2         476,311,185   488,392,064    12,080,880   5 Extended
Invalid MBR Signature found
/dev/sdb5     ?   476,311,185   476,311,184                   Unknown
/dev/sdb6     ?   476,311,185   476,311,184                   Unknown

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb5 ends after the last sector of /dev/sdb
the logical partition /dev/sdb5 is not contained in the extended partition /dev/sdb2
/dev/sdb6 ends after the last sector of /dev/sdb
the logical partition /dev/sdb6 is not contained in the extended partition /dev/sdb2

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9cb67f6c-8e57-408e-bd59-d031b0ecf9bb" TYPE="ext4" 
/dev/sda5: UUID="6f430b73-a87b-4d6d-a763-72bf0436a4b7" TYPE="swap" 

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
search --no-floppy --fs-uuid --set 9cb67f6c-8e57-408e-bd59-d031b0ecf9bb
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 9cb67f6c-8e57-408e-bd59-d031b0ecf9bb
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9cb67f6c-8e57-408e-bd59-d031b0ecf9bb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 9cb67f6c-8e57-408e-bd59-d031b0ecf9bb
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9cb67f6c-8e57-408e-bd59-d031b0ecf9bb ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 9cb67f6c-8e57-408e-bd59-d031b0ecf9bb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9cb67f6c-8e57-408e-bd59-d031b0ecf9bb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 9cb67f6c-8e57-408e-bd59-d031b0ecf9bb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9cb67f6c-8e57-408e-bd59-d031b0ecf9bb ro single 
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
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro single
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
UUID=9cb67f6c-8e57-408e-bd59-d031b0ecf9bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f430b73-a87b-4d6d-a763-72bf0436a4b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb5


Unknown BootLoader  on sdb6



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb6: No such file or directory
hexdump: /dev/sdb6: No such file or directory
```

---

### Post by presence1960 on 2009-12-29
You will never be able to boot from that external as there is no bootloader in the MBR of that disk. If it was Ubuntu 9.10 using GRUB2 on that external disk you can install GRUB2 to MBR of that disk. Boot into Ubuntu , open a terminal and run ```
sudo grub-install /dev/sdb
```

Then try rebooting from the external and see if you can log in.

P.S. I also just noticed you have a menu entry on your GRUB from the internal disk. You can try booting from that also. here are the entries that should appear on your GRUB menu. Note this is from grub.cfg on your internal disk:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 2709e1a4-da0d-43c0-86e0-ce1879c71487
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2709e1a4-da0d-43c0-86e0-ce1879c71487 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###
```

---

### Post by bryanlee1981 on 2009-12-29
I am able to boot from the internal HDD with no issue.  I followed your directions and installed GRUB onto the external drive.  When attempting to boot to the external I get...

```
error: you need to load the kernel first
```

I will keep reading and poking around to see what i come up with.  Thanks for you help.

---

### Post by presence1960 on 2009-12-29
> **bryanlee1981 said:**
> I am able to boot from the internal HDD with no issue.  I followed your directions and installed GRUB onto the external drive.  When attempting to boot to the external I get...

```
error: you need to load the kernel first
```

I will keep reading and poking around to see what i come up with.  Thanks for you help.

Did you try the bottom entries in your GRUB menu when you boot from internal as they are for the external disk.

You may have a problem because the external is encrypted and you may have wiped the bootloader for that when you formatted the internal disk. Hope you can get it working!

---

### Post by bryanlee1981 on 2009-12-29
I have tried all of the entries.  I was able to restore the original grub to the external HDD using [this post]("http://ubuntuforums.org/showthread.php?t=1014708"), but I am still unable to boot completely.  The grub loads as it should and displays the correct options, but when i try to boot it will load the ubuntu icon...then after a brief pause it goes to a black screen.  After a few more moments I am dumped to a prompt like this

```
initramfs:
```

---

### Post by presence1960 on 2009-12-30
> **bryanlee1981 said:**
> I have tried all of the entries.  I was able to restore the original grub to the external HDD using [this post]("http://ubuntuforums.org/showthread.php?t=1014708"), but I am still unable to boot completely.  The grub loads as it should and displays the correct options, but when i try to boot it will load the ubuntu icon...then after a brief pause it goes to a black screen.  After a few more moments I am dumped to a prompt like this

```
initramfs:
```

I wish I knew more about encryted disks but I do not. Hopefully someone will come along that knows.

I think it would be beneficial to you if you start a new thread with "encrypted file system" or "encrypted disk" in the title so as to attract attention to the problem when other users are reading the thread titles. You can then ask a moderator to merge your threads so all info is available to anyone else coming to help.

---

### Post by Herman on 2009-12-30
:-k If you can't remember encrypting it yourself then it's more than likely not encrypted, more likely it's just corrupted.

If it is encrypted, it looks like you're using some different kind of encryption to the kind I use. I have a USB drive plugged in at the moment, and for comparison's sake I ran 'sudo blkid', here's the output from mine, 
```
/dev/sda1: LABEL="OCZ-KARMIC" UUID="2ee1e3a3-f03a-4690-8310-7c3236786563" TYPE="ext4" 
/dev/sda5: UUID="f5cad0a5-ba50-4cbd-a8a3-d36c2509c1f7" TYPE="swap" 
/dev/sdb1: UUID="cec3489e-0be9-439d-8e44-b80a9b28f4e4" TYPE="**crypto_LUKS**" 
/dev/sdb5: UUID="63367bd4-23f5-4b40-b497-1946bb5d9035" TYPE="ext2" 
```If it's only encrypted it should be easy to mount and rescue your files from if you know the password.
First, install cryptsetup,
```
sudo apt-get install lvm2 cryptsetup
```next,
```
sudo modprobe dm-crypt
```Now you should easily be able to mount it just by clicking the icon for it in the 'Places' menu. A dialog box can be expected to pop up asking for your password, (for permission to mount it), and another for your encryption password. (I think, something like that anyway, I did it a little too quickly and didn't take enough notice).

Here's a link you might find useful, How To [Rescue An Encrypted LUKS Volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html"), UbuntuGeek.

Your partition table looks a bit corrupted to me, maybe TestDisk will fix it, or  maybe you should just try running a file system check?
I'm not sure which order I'd try those things in.

External hard disks are much very subject to damage from normal handling, I recommend flash memory for external drives instead, it's more robust. SSD drives are coming down in price, expensive, but not much as they were a year ago.

---

### Post by Herman on 2009-12-30
```
Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   476,311,184   476,311,122  83 Linux
/dev/sdb2         476,311,185   488,392,064    12,080,880   5 Extended
[COLOR=Red]Invalid MBR Signature found
/dev/sdb5     ?   476,311,185   476,311,184                   Unknown
/dev/sdb6     ?   476,311,185   476,311,184                   Unknown

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb5 ends after the last sector of /dev/sdb
the logical partition /dev/sdb5 is not contained in the extended partition /dev/sdb2
/dev/sdb6 ends after the last sector of /dev/sdb
the logical partition /dev/sdb6 is not contained in the extended partition /dev/sdb2[/COLOR] 
```Your partition table.

```
blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9cb67f6c-8e57-408e-bd59-d031b0ecf9bb" TYPE="ext4" 
/dev/sda5: UUID="6f430b73-a87b-4d6d-a763-72bf0436a4b7" TYPE="swap" 
```Your blkid output. It doesn't even show your USB drive.

I'd proceed with caution and seek the opinion of others first, especially if you have important information on this drive. 

I'd be inclined to start with TestDisk and try to fix the partition table first, (if it supposed to be a normal one). Test Disk is a program we can install in Ubuntu, [TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk").

---

