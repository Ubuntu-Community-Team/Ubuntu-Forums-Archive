---
title: "Win7 can not reboot after install Ubuntu 9.10"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by hoody4032 on 2009-11-26
Dear all,

I installed Win7 first on my laptop and it worked great. Then I installed Ubuntu 9.10 in another partition and it worked. When I boot up my machine, I can see both Ubuntu and Win7 in my Grub menu list. But I can only boot Ubuntu. I can not boot Win7 any more. 

Then error message is "[I]NTLDR is missing". 

I searched on google but could not find a good solution. It appears now Ubuntu is using Grub2, which I am not familiar with.

Any suggestions?

Many thanks.
[/I]

---

### Post by presence1960 on 2009-11-26
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldfred on 2009-11-26
+1 on the script. It tells all on the boot process.

Did you by any chance delete an old XP install?

Vista/Win7 copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by hoody4032 on 2009-11-27
Thank you guys.

This installation is a fresh install. I installed a brand new 400G hard drive on my laptop. Then I installed Win7, it worked. Then I installed Ubuntu 9.10. It worked, but Win7 can not boot any more.


```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
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
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f3261

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,448,624    61,448,562   7 HPFS/NTFS
/dev/sda2          61,448,625   519,831,269   458,382,645   7 HPFS/NTFS
/dev/sda3         519,831,270   666,311,939   146,480,670  83 Linux
/dev/sda4         666,311,940   976,768,064   310,456,125   5 Extended
/dev/sda5         666,312,003   812,792,609   146,480,607  83 Linux
/dev/sda6         812,792,673   820,600,199     7,807,527  82 Linux swap / Solaris
/dev/sda7         820,600,263   976,768,064   156,167,802  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="01CA5A0ECB47C200" LABEL="Sys" TYPE="ntfs" 
/dev/sda2: UUID="01CA5A0ECB47C200" LABEL="Data" TYPE="ntfs" 
/dev/sda3: UUID="b9982138-dec6-42ba-97b2-fcbd5fb71708" TYPE="ext4" 
/dev/sda5: UUID="ebbefd66-7335-45be-9eba-9e155ffbac0c" TYPE="ext4" 
/dev/sda6: UUID="9f655164-f988-42f7-a526-91ea922a166e" TYPE="swap" 
/dev/sda7: UUID="8f6a23c3-74fd-405e-9086-43b4a9ed49cc" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda3 on /home type ext4 (rw)
/dev/sda5 on /opt type ext4 (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jmeng/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jmeng)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 8f6a23c3-74fd-405e-9086-43b4a9ed49cc
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
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 8f6a23c3-74fd-405e-9086-43b4a9ed49cc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8f6a23c3-74fd-405e-9086-43b4a9ed49cc ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 8f6a23c3-74fd-405e-9086-43b4a9ed49cc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8f6a23c3-74fd-405e-9086-43b4a9ed49cc ro single 
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
    search --no-floppy --fs-uuid --set 01ca5a0ecb47c200
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=8f6a23c3-74fd-405e-9086-43b4a9ed49cc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=b9982138-dec6-42ba-97b2-fcbd5fb71708 /home           ext4    defaults        0       2
# /opt was on /dev/sda5 during installation
UUID=ebbefd66-7335-45be-9eba-9e155ffbac0c /opt            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=9f655164-f988-42f7-a526-91ea922a166e none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 420.1GB: boot/grub/grub.cfg
 420.1GB: boot/initrd.img-2.6.31-14-generic
 420.1GB: boot/vmlinuz-2.6.31-14-generic
 420.1GB: initrd.img
 420.1GB: vmlinuz

```

---

### Post by darkod on 2009-11-27
I can see you are already getting help from more experienced than me, but just to add.
If win7 was a clean install and ubuntu 9.10 also, what has ntldr got to do with it? Win7 uses bootmgr instead, not sure if grub2 or the windows boot process is reporting the ntldr missing error, but none of them should be asking for that file.

---

### Post by oldfred on 2009-11-27
This is the problem:
[FONT=monospace]
/dev/sda1: UUID="01CA5A0ECB47C200" LABEL="Sys" TYPE="ntfs" 
/dev/sda2: UUID="01CA5A0ECB47C200" LABEL="Data" TYPE="ntfs" 

You cannot have two UUID's the same. I did not think this was possible unless you copied a partition. My quick search shows NTFS does not support UUID's so the usual linux tools may not fix it.

I would copy this entry to 40_custom and edit out the line with the UUID reference and see if that works. Someone else may know how to change the UUID, possibly gparted?

menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    [COLOR=DarkRed]search --no-floppy --fs-uuid --set 01ca5a0ecb47c200  <delete[/COLOR]
    chainloader +1
}

and then run update-grub to refresh grub.cfg.
[/FONT]

---

### Post by hoody4032 on 2009-11-27
Hi oldfred,

Thank you. You solved the problem. I used gparted delete the data partition and then Win7 can boot properly. Then I use Win7 to re-format this partition.

Now everything work fine.

Thanks again.

---

### Post by hoody4032 on 2009-11-27
How can I change the thread from [ubuntu] to [solved]?

---

### Post by hoody4032 on 2009-11-27
OK. I got it. Use the thread tool.

---

### Post by Xenzaka on 2009-11-27
> **hoody4032 said:**
> Dear all,

I installed Win7 first on my laptop and it worked great. Then I installed Ubuntu 9.10 in another partition and it worked. When I boot up my machine, I can see both Ubuntu and Win7 in my Grub menu list. But I can only boot Ubuntu. I can not boot Win7 any more. 

Then error message is "[I]NTLDR is missing". 

I searched on google but could not find a good solution. It appears now Ubuntu is using Grub2, which I am not familiar with.

Any suggestions?

Many thanks.
[/I]

Okay, I'm still learning myself, but I would like to help you as much as I can. I've been through a similar problem before. 

First thing is first, try to find a copy of the Windows instalment you have. If you cannot find an installation disk, you're not in trouble, yet. Try to find a "copy", or at least make a "copy" (abiding by federal and state law of course on copyright) and place the CD in before post / boot up with your machine. 

Secondly, it should load Windows files wherein it should give you a list of available options. Select repair, or system restore if you've recently made a restore point. 

Last but not least, Google might help you. Type in: "[I]NTLDR is missing" windows 7

[/I]Hopefully you can find help from google above anything else.

---

