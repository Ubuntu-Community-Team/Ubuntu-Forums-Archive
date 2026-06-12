---
title: "Problems with GRUB on new Ubuntu install"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by brickhead248 on 2010-01-13
Hey!

I installed Ubuntu on an already existent Vista install, but now neither will boot.

Previously, Vista was installed on the single NTFS partition on my 250GB hard drive. I used the Ubuntu partition resizer to resize this partition which left about 25GB free space, on which I created an EXT4 partition mounted to / and a swap space. (that IS how you install ubuntu right?)

When i rebooted however, this is what i got from GRUB:

[B]GRUB loading.
error: no such partition
grub rescue>_[/B]

I've tried reinstalling Ubuntu on the same EXT4 partition, same thing.
I've tried using the vista 64 recovery disk, which was COMPLETELY useless as it didn't even give you the option to try and restore the Vista boot loader.

I've also just noticed that my hard drive has many bad sectors, could be causing some kind of problem.
[B]
Whats wrong with GRUB and how do i fix it?[/B]
cheers

---

### Post by garvinrick4 on 2010-01-13
Where did you put /boot

---

### Post by brickhead248 on 2010-01-13
hmmmm i didnt specify a partition for /boot, was i meant to?

i just assumed that it would be written into the / partition.

does that mean i should reinstall and specify a /boot partition?

---

### Post by garvinrick4 on 2010-01-13
Yes you must give Linux Grub2 a place to reside.
It will be your grub2 now taking over for bcd in Vista. Vista will chainload
to grub2. Here I will just give you some Links to read, that would be better for you.
Google Vista and Ubuntu dual boot for more info.


[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by brickhead248 on 2010-01-13
> **garvinrick4 said:**
> Yes you must give Linux Grub2 a place to reside.
It will be your grub2 now taking over for bcd in Vista. Vista will chainload
to grub2. Here I will just give you some Links to read, that would be better for you.
Google Vista and Ubuntu dual boot for more info.


[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
Thanks for the links. I followed the second link and reinstalled grub.
I got the exact same error in grub when I rebooted. - so we can rule out GRUB as a source of the error. 
Also, the boot configuration data file is not the problem in this case: Grub doesnt even give windows a chance to screw up anything because it doesnt even load the boot menu!

this sounds like a problem with the way that GRUB is detecting my hard drives.

this is what happened when i tried to load the normal module in grub rescue:

grub rescue>ls
(hd0) (hd0,1) (hd1) (fd0)
error: no such disk                                        **--WHAT THE HELL?**
grub rescue> insmod (hd0,1)/boot/grub/normal.mod
error: unknown filesystem                     **         --???**

whats going on??????????

---

### Post by brickhead248 on 2010-01-13
> **brickhead248 said:**
> Thanks for the links. I followed the second link and reinstalled grub.
I got the exact same error in grub when I rebooted. - so we can rule out GRUB as a source of the error. 
Also, the boot configuration data file is not the problem in this case: Grub doesnt even give windows a chance to screw up anything because it doesnt even load the boot menu!

this sounds like a problem with the way that GRUB is detecting my hard drives.

this is what happened when i tried to load the normal module in grub rescue:

grub rescue>ls
(hd0) (hd0,1) (hd1) (fd0)
error: no such disk                                        **--WHAT THE HELL?**
grub rescue> insmod (hd0,1)/boot/grub/normal.mod
error: unknown filesystem                     **         --???**

whats going on??????????
This is strange: **sudo gedit /boot/grub/menu.ls** and **sudo gedit /boot/grub/menu.lst** don't work on any of my ubuntu machines... i have 9.10, is this normal?

---

### Post by kansasnoob on 2010-01-13
We need to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Karmic's grub2 no longer uses a menu.lst!

---

### Post by kansasnoob on 2010-01-13
> **brickhead248 said:**
> hmmmm i didnt specify a partition for /boot, was i meant to?

i just assumed that it would be written into the / partition.

does that mean i should reinstall and specify a /boot partition?

No! There is very seldom a need to create a separate /boot partition! In fact it can cause problems.

---

### Post by brickhead248 on 2010-01-13
> **kansasnoob said:**
> We need to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Karmic's grub2 no longer uses a menu.lst!
Thanks Kansas,

unfortunately, im running ubuntu off the live CD, and its giving me this when i try and run the script, even though i've checked the file name.
[B]
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script*.sh
bash: /home/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script048.sh
bash: /home/ubuntu/downloads/boot_info_script048.sh: No such file or directory
ubuntu@ubuntu:~$ [/B]

any ideas?

---

### Post by brickhead248 on 2010-01-13
> **brickhead248 said:**
> Thanks Kansas,

unfortunately, im running ubuntu off the live CD, and its giving me this when i try and run the script, even though i've checked the file name.
[B]
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script*.sh
bash: /home/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script048.sh
bash: /home/ubuntu/downloads/boot_info_script048.sh: No such file or directory
ubuntu@ubuntu:~$ [/B]

any ideas?
AAAAAH, no capital D - silly me!

---

### Post by brickhead248 on 2010-01-13
> **brickhead248 said:**
> AAAAAH, no capital D - silly me!
here are the results:

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x025f025f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   449,145,269   449,143,222   7 HPFS/NTFS
/dev/sda2         449,145,270   488,392,064    39,246,795   5 Extended
/dev/sda5         449,145,333   486,657,044    37,511,712  83 Linux
/dev/sda6         486,657,108   488,392,064     1,734,957  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a52ea

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="629845729845462F" TYPE="ntfs" 
/dev/sda5: UUID="0a774894-a75e-4378-a450-194bdc1f8da9" TYPE="ext4" 
/dev/sda6: UUID="c0ce2412-0c97-410a-b14f-3ee202874df2" TYPE="swap" 
/dev/sdb1: UUID="0A6452B26452A06D" LABEL="1TB backup" TYPE="ntfs" 
/dev/sdc1: LABEL="THE BOX" UUID="C0AB-072D" TYPE="vfat" 

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
/dev/sdc1 on /media/THE BOX type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1 on /media/629845729845462F type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/0a774894-a75e-4378-a450-194bdc1f8da9 type ext4 (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 0a774894-a75e-4378-a450-194bdc1f8da9
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
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0a774894-a75e-4378-a450-194bdc1f8da9
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=0a774894-a75e-4378-a450-194bdc1f8da9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0a774894-a75e-4378-a450-194bdc1f8da9
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=0a774894-a75e-4378-a450-194bdc1f8da9 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 629845729845462f
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
UUID=0a774894-a75e-4378-a450-194bdc1f8da9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c0ce2412-0c97-410a-b14f-3ee202874df2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 229.9GB: boot/grub/core.img
 229.9GB: boot/grub/grub.cfg
 229.9GB: boot/initrd.img-2.6.31-17-generic-pae
 229.9GB: boot/vmlinuz-2.6.31-17-generic-pae
 229.9GB: initrd.img
 229.9GB: vmlinuz

---

### Post by Leppie on 2010-01-13
remember that linux is case sensitive:
```
sudo bash ~/**_D_**ownloads/boot_info_script*.sh
```

Also, when resizing ntfs partitions I'd say windows is best. Even though ntfs support has become excellent in linux, windows puts the files in a very random and strange way onto filesystem. Resizing ntfs partitions should be done from within windows environments.

---

### Post by brickhead248 on 2010-01-13
> **Leppie said:**
> remember that linux is case sensitive:
```
sudo bash ~/**_D_**ownloads/boot_info_script*.sh
```

Also, when resizing ntfs partitions I'd say windows is best. Even though ntfs support has become excellent in linux, windows puts the files in a very random and strange way onto filesystem. Resizing ntfs partitions should be done from within windows environments.
Yeah, the problem is that windows could only resize such that it would leave only 5gb for Ubuntu, even though i had much more free space than that.

maybe it was my impatience in using the ubuntu resizer that caused this mess.

is this why grub ***** itself when it tries to even contemplate booting?

---

### Post by kansasnoob on 2010-01-13
First observation: using gparted to resize Windows hosed some of the boot files.

Typical: /bootmgr /Boot/BCD /Windows/System32/winload.exe /ntldr /NTDETECT.COM 

Yours: /bootmgr /Boot/BCD /Windows/System32/winload.exe

So Windows is missing it's ntldr and NTDETECT.COM I think. I'll admit I'm not at all proficient with that, but this may help:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Note: I've found that sometimes I've had to run the Vista repair 3 or even 4 times sometimes before it's fixed. I was once told that's because it only fixes one thing at a time, so if you're missing 2 boot files it must be run twice.

Now I'll look at the rest of that and see if I can come up with an idea for grub2.

---

### Post by darkod on 2010-01-13
> **Leppie said:**
> remember that linux is case sensitive:
```
sudo bash ~/**_D_**ownloads/boot_info_script*.sh
```Also, when resizing ntfs partitions I'd say windows is best. Even though ntfs support has become excellent in linux, windows puts the files in a very random and strange way onto filesystem. Resizing ntfs partitions should be done from within windows environments.

I would generally agree that it's better to use windows disk management for resizing windows partitions, but in my case it also happened that vista would offer to shrink much less than available (and needed). Gparted did the job great. Only don't forget to reboot vista after that to do its checks.

Also, about the windows boot files. I'm just jumping into this thread but as far as I noticed the OP doesn't have XP, only Vista. ntldr and ntdetect.com are XP boot files. Not sure if we should be worried if they aren't there. bootmgr and boot/bcd are the main boot files for vista and 7.

---

### Post by kansasnoob on 2010-01-13
You might find this useful:

> Booting from the Rescue Mode
At the grub rescue> prompt, accomplish the following actions to attempt to boot to the latest kernel:

    * ls This will display the known devices and partitions. From this information, the user must determine the device and partition on which the system is installed.
    * set Check the current settings. Note the prefix listing. If it is not pointing to the correct location:
          o set prefix=(hdX,Y)/boot/grub Examples: sda1 is (hd0,1), sdb5 is (hd1,5)
    * set root=/dev/sdXY X is the device/drive, starting with 0. Y is the partition, starting with 1. (Example: (hd0,1) is sda1. (hd3,5) is sdc5.
          o For Wubi installs, use: set root=(loop0)
    * ls /boot Inspect the contents. The user should see varioius kernels, initrd images and the grub folder. If not, use the ls command to inspect the device and attempt to find these files and folders. If necessary, set another device as root.
    * insmod /boot/grub/_linux.mod Load the linux module. Without this module loaded, the user will receive an "Unknown command linux" message when trying to load the kernel.
    * linux /vmlinuz root=/dev/sdXY ro Load the linux kernel, substituting the correct designations for "X" and "Y" (example: sda1). The user will see a message showing the kernel has been loaded. (See graphic above)
          o Note: For Wubi installs within Windows, use this code: linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
    * initrd /initrd.img Load the initrd image. When pressing enter, the user may or may not see a message in the terminal. (See highlighted graphic above)
    * boot

More command line recovery options are available in the "Command Line & Rescue Mode" section of the Ubuntu Grub 2 community doc.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Now, if I'm fiddling with my own computer I don't care how long something like this takes to figure out. I'm multi-booting 5 Linux OS's (2 of which have grub2, the others have legacy grub) and Win XP, and I can quickly and easily hand boot off from one OS to another so if I grow tired of fiddling I'll do just that until I have the time and patience to go back and fiddle around some more.

That said it's a whole different story if I'm working on someone elses machine. They're usually impatient and I don't want them coming back a day or two later because the same problem recurred so, regarding grub2, I generally just do two things:

#1. I mount and chroot the Ubuntu OS using a Live CD and give grub2 another chance at configuring itself properly like this (please double-click to highlight, right click to copy, and then paste these commands):

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
sudo update-grub
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot and see if that changed anything. 

If that should make Ubuntu bootable be sure to run "sudo update-grub" after the initial boot and grub2 should find Windows.

If still unable to boot even Ubuntu I generally move on to:

#2. Just reverting to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

You know your Ubuntu is on sda5 and Windows is on sda1. I think that HowTo is pretty much self explanatory.

Of course you'll have to add Windows to the menu.lst:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

And edit the Timeout and Hidden Menu lines:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		**[COLOR="Red"]10[/COLOR]**

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]**hiddenmenu
```

After you fix the Vista boot files :)

---

### Post by kansasnoob on 2010-01-13
> Also, about the windows boot files. I'm just jumping into this thread but as far as I noticed the OP doesn't have XP, only Vista. ntldr and ntdetect.com are XP boot files. Not sure if we should be worried if they aren't there. bootmgr and boot/bcd are the main boot files for vista and 7.


Thanks Darko. That's why I said I'm less than proficient regarding Windows.

---

### Post by Leppie on 2010-01-13
Try downloading the [Ultimate Boot C]("http://www.ubcd4win.com/downloads.htm")D to recover vista.

---

