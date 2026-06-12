---
title: "Ubuntu 9.10 don't start! Missing modules? :("
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by maori on 2010-01-30
Hi at all.

First: forgive my poor english!

I'm Angelo from Italy, and this is my first post in this forum.

I have a big big problem.

Well: almost 2 months with Ubuntu, a week ago I restart one time on Win to take an old email message.

After that my Ubuntu have no longer worked.

Every time I restart my pc (100 times!!) seems like on stanby: I can see Grub, then choose Ubuntu, but after that never happen, just a black monitor.

After 5 minutes the monitor show this ( some words are incomplete cause the monitor was not in center, so i put "...."):

[I]missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/dba21c64-aa69-4bfd-952-a665d72409ba does not exist

.......pping to a shell

......usybox v.1:1.13.3(ubuntu 1:1.13.3-1 ubuntu7)

.......built-in shell (ash)

enter 'help' for a  list of built-in command

....initramfs:[/I]

Then the cursor flashing in *"initramfs:" *

I hope you understand my bad english, and someone can help a very  unskilled like me

Ciao!:)

---

### Post by kansasnoob on 2010-01-30
So we can get a better look at your installation please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by maori on 2010-01-30
> **kansasnoob said:**
> So we can get a better look at your installation please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thank you very much!

Unfortunately right in this days I'm changing home, so the cd live is in a box.

If I post what you ask  me in 2 days? I'm in time for a help?

---

### Post by kansasnoob on 2010-01-30
> **maori said:**
> Thank you very much!

Unfortunately right in this days I'm changing home, so the cd live is in a box.

If I post what you ask  me in 2 days? I'm in time for a help?

Yes! Bookmark this page and to get my attention just click on my Forum username and send me a brief PM pointing me back to this thread.

---

### Post by maori on 2010-02-04
Hi.

Below the results.

I hope it helps.


===================================

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hda: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,712,509   209,712,447   7 HPFS/NTFS
/dev/sda2         209,712,510   233,151,344    23,438,835  83 Linux
/dev/sda3         233,151,345   235,143,404     1,992,060  82 Linux swap / Solaris
/dev/sda4    *    235,143,405   312,576,704    77,433,300   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda                                                iso9660    Ubuntu 7.04 i386              
/dev/sda1                                               ntfs                                     
/dev/sda2        dba21c64-aa69-4bfd-9252-a665d724c9ba   ext3                                     
/dev/sda3        aab35b0b-cc0c-4951-8ccd-ed08694fcdbd   swap                                     
/dev/sda4        711F-ADAD                              vfat                                     
/dev/sdb1                                               ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)
/dev/sda4        /media/disk              vfat       (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

================================ sda1/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set dba21c64-aa69-4bfd-9252-a665d724c9ba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 44fc53e7fc53d232
	drivemap -s (hd0) ${root}
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
UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba /               ext3    errors=remount-ro 0       1
# /mnt/data was on /dev/sda4 during installation
UUID=711F-ADAD  /mnt/data       vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda3 during installation
UUID=aab35b0b-cc0c-4951-8ccd-ed08694fcdbd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 108.7GB: boot/grub/core.img
 108.7GB: boot/grub/grub.cfg
 108.7GB: boot/initrd.img-2.6.31-14-generic
 108.7GB: boot/initrd.img-2.6.31-15-generic
 108.7GB: boot/initrd.img-2.6.31-16-generic
 108.7GB: boot/initrd.img-2.6.31-17-generic
 108.8GB: boot/vmlinuz-2.6.31-14-generic
 108.8GB: boot/vmlinuz-2.6.31-15-generic
 108.7GB: boot/vmlinuz-2.6.31-16-generic
 108.7GB: boot/vmlinuz-2.6.31-17-generic
 108.7GB: initrd.img
 108.7GB: initrd.img.old
 108.7GB: vmlinuz
 108.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hdb sdc sdd sde sdf sdg sdh sdi sdj

---

### Post by kansasnoob on 2010-02-04
Well I don't actually see anything wrong there, but I didn't really expect to. One thing I'll point out, in your original post you said:

> ALERT! /dev/disk/by-uuid/dba21c64-aa69-4bfd-952-a665d72409ba does not exist

Below I'm showing that UUID above the actual UUID shown in blkid, fstab, & grub:

```
dba21c64-aa69-4bfd-952-a665d72409ba
dba21c64-aa69-4bfd-9252-a665d724c9ba
```

I'd bet however that's just a typo. That's a lot of stuff to write down and then type.

Anyway lots of things can cause that type of error, most commonly something just goes wrong during a kernel update. So the first thing I'd try is simply booting into an older kernel, I see you have:

```
2.6.31-17-generic
2.6.31-16-generic
2.6.31-15-generic
2.6.31-14-generic
```

So you're probably trying to boot *-17. Try *-16 or older instead. If you can boot into one of the older kernels post the output of:

```
ls -l /boot
```

Note: those are lower case L's.

If not I'll have to put my thinking cap on :)

---

### Post by maori on 2010-02-04
Thanks for your reply.

I'm working to understand what you wrote!!!!:-k

And about the results, the only "strange" thing I can see is 

> UUID=dba21c64-aa69-4bfd-9252-a665d724c9ba / ext3 errors=remount-ro 0 1


So, please, suggest me wich kind of kernel have to start.

Thanks :-)

---

### Post by maori on 2010-02-04
Ok, try to boot in every kernel possible, everytime in "recovery mode" too.

The reply is the same; after 2 minutes in black monitor, shown the error in 1st post, and said that 
[I]
ALERT! /dev/disk/by-uuid/dba21c64-aa69-4bfd-952-a665d72409ba does not exist[/I]

In recovery mode too, after something like a hard drive scan, said the same thing.

If I send "help", there's a list of command that I don't know what's they are for.....I'm too stupid!

---

### Post by kansasnoob on 2010-02-04
You're not stupid! Give me a little time.

---

### Post by maori on 2010-02-05
> **kansasnoob said:**
> You're not stupid! Give me a little time.

Many thanks!

My intention is try to save all I have in Ubuntu (mail, configuration, pics, etc etc)

That's why maybe ( I think ) in live cd I can format then reinstall Ubuntu, but In this way I lose everything, right?

There's a way to copy and save the important folder, reinstall Ubuntu and overwrite the folder saved with inside my files?

Ciao.

---

### Post by kansasnoob on 2010-02-05
> **maori said:**
> Many thanks!

My intention is try to save all I have in Ubuntu (mail, configuration, pics, etc etc)

That's why maybe ( I think ) in live cd I can format then reinstall Ubuntu, but In this way I lose everything, right?

There's a way to copy and save the important folder, reinstall Ubuntu and overwrite the folder saved with inside my files?

Ciao.

Sorry to take so long. In answer to this:

> in live cd I can format then reinstall Ubuntu, but In this way I lose everything, right?

Yes, you would have to start over, but lets not get ahead of ourselves.

**Please post the results of all terminal commands, and also a screenshot of Gparted in your next post. And whether or not you can boot Windows.**

If my math is any good it looks like the size of your partitions is about:

```
Windows = 105GB
Ubuntu  =  12GB
SWAP    =   1GB
DATA?   =  38GB
```

Is that close to right?

I usually cheat and use the command "sudo parted /dev/sda print" to get a more human readable picture of the drive/partition structure :)

Anyway if Ubuntu is only 12GB I wonder if it encountered a "space limitation" problem?

We could mount and chroot Ubuntu to take a look. Please take time to look at this old post of mine so I don't have to explain a lot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

So you would boot the Live CD and run:

```
sudo mount /dev/sda2 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

And these two commands would provide info about used/free space:

```
df -H
```

BTW that's intentionally a capital H!

```
du -sh /*
```

The output of "df -H" is pretty simple to read, for example:

```
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              8.8G   4.2G   4.3G  50% /
none                   1.1G   316k   1.1G   1% /dev
none                   1.1G   238k   1.1G   1% /dev/shm
none                   1.1G    99k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              17G   4.4G    13G  27% /home

```

Of course I have a separate /home but if you'd see that nearly 100% of /dev/sda2 is used then that could be a part of the problem. The command "du -sh /*" just provides more detail if needed.

Anyway if space is a problem you should be able to safely run:

```
apt-get autoclean
```

```
apt-get clean
```

```
apt-get autoremove
```

Then to see what you gained run this again:

```
df -H
```

When done working in the chroot be sure to exit and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Then it's possible that if you start in "Ubuntu, Linux 2.6.31-17-generic (**recovery mode**)" that it may sort things or give you some instructions as far as what to do next.

Something I didn't think to ask was if you can still boot Windows?

As far as accessing and backing things up it should be possible using the Live CD. Just go to Places > Computer and you should be able to identify the Ubuntu install by size I think. Inside /home you should see your <username> folder which contains everything.

Once you open that folder if you click on View > Show hidden files you'll see everything like mozilla, evolution, thunderbird, etc. If you right click the <username> folder and select copy you should actually be able to just paste the whole thing to it's destination.

But there will be some reconfiguring needed upon reinstalling. You'll have to reinstall any packages you installed after the first install, etc.

I don't think this is a grub2 problem but IMHO it would be well worth the time and trouble to burn a Super Grub Disk and see if you can use it just to boot Ubuntu. Their homepage:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You don't want the newest (grub2) version, look here:

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

> If you are a newbie please check for Cdrom, Usb or floppy download instead of SG2D Cdrom, SG2D Usb and SG2D floppy on mirror #0. This is the old Super Grub Disk which actually works better than the new Super Grub Disk based on Grub2. Sorry for any troubles that you run into.

Basically grub2 has caused a lot of problems :)

So be sure to **use version 0.9799**, and only use it to try and boot Ubuntu. It won't help with "recovering" grub2 but it will boot a grub2 system, I know because I've used it.

Download page:

[http://developer.berlios.de/project/showfiles.php?group_id=10921](http://developer.berlios.de/project/showfiles.php?group_id=10921)

Simple instructions:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk)

Then if you should happen to be able to boot Ubuntu using the SGD we know what to fix :)

---

### Post by maori on 2010-02-08
Sorry for delay in reply, I was busy.

Let me some days please; have 
to find someone who translate your post, and be sure to do the right thing.

Thanks a lot.

Ciao.

---

### Post by maori on 2010-02-08
Ok, try to do what you asked me.

The results are in the files in attachment

Upoloaded in 2 extension to be sure about.

That's why maybe too long for a post, and not so nice....I think

There's the screenshot too.

Almost in the end, when I try to do "autoclean" said "impossible to open the file".

Am I in a wrong directory (E), cause impossible to mount sda2 like said in first row?

P.S windows works.....unfortunately I'm using that OS...

Thanks, ciao.

---

### Post by kansasnoob on 2010-02-08
You're doing fine!

> Am I in a wrong directory (E), cause impossible to mount sda2 like said in first row?

No. I've double checked, both Gparted and the Boot Info Script show Ubuntu is on sda2.

Disc space does not appear to be a problem as Gparted shows 6.58 GB unused.

Considering both the boot problem and this:

> mount: you must specify the filesystem type

I suspect file-system damage so I'd boot the Live CD again and go to Gparted, then right click on sda2 and select "Check":

[ATTACH]146452[/ATTACH]

NOTE: I used my sda12 in the example!

That may find and fix some errors. If so try booting into "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" and see what happens.

If that doesn't work we probably need to devise a re-installation strategy.

Since you have Win XP and an ext3 Linux partition you should be able to use "fs-driver":

[http://www.fs-driver.org/](http://www.fs-driver.org/)

> Linux Ext3 volumes can also be accessed. To do that, please read the FAQ section. 

That should allow you to copy everything you want to keep from Ubuntu and reinstall it.

One thing! **[COLOR="Red"]Only if you decide to remove Ubuntu or want to be able to boot Windows only during the process[/COLOR]** you'll need to restore a Windows mbr to sda by booting an Ubuntu Live CD and running:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

I hope this helps :)

---

### Post by maori on 2010-02-09
> **kansasnoob said:**
> I suspect file-system damage so I'd boot the Live CD again and go to Gparted, then right click on sda2 and select "Check"

Done, and reboot in Recovery the 2.6.31.17, but the results are the same: after such a devices scan, the system show what I wrote in 1st post: missing modules etc etc.

Explane  me please, like talk to a little child, this:> **kansasnoob said:**
> 
One thing! Only if you decide to remove Ubuntu or want to be able to boot Windows only during the process you'll need to restore a Windows mbr to sda by booting an Ubuntu Live CD and running:

Code:
sudo apt-get install lilo

Code:
sudo lilo -M /dev/sda mbr


I hope this helps 

Thanks

**_EDIT: _**in previous post you talk about fs-driver. I checked, and seem to be a sw to manage in Windows the ext3 files, right?

So I can copy from Windows all the files in Ubuntu, and after installation overwrite that folders, correct?

But, I have a question: can I do the same thing from Live CD? Or not? In that environment I see the Ubuntu folder......

---

### Post by kansasnoob on 2010-02-10
> Explane me please, like talk to a little child, this:

Originally Posted by kansasnoob View Post
One thing! Only if you decide to remove Ubuntu or want to be able to boot Windows only during the process you'll need to restore a Windows mbr to sda by booting an Ubuntu Live CD and running:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```


I only included that in case you'd have trouble reinstalling Ubuntu. Since grub2 is now booting Windows (and trying to boot Ubuntu), if Ubuntu is removed not even Windows will boot.

Running those commands would make it possible for Windows to boot even if Ubuntu and/or grub2 is removed.

> I have a question: can I do the same thing from Live CD? Or not? In that environment I see the Ubuntu folder......

Yes, you can use a Live CD to copy files to an external drive, CDRW, DVDRW, etc. Sometimes it can be tricky copying files to a partition on the same drive because you don't have "administrative privileges" and I don't like modifying "privileges".

> So I can copy from Windows all the files in Ubuntu, and after installation overwrite that folders, correct?

That was only one way to backup your files/data from Ubuntu. Use whatever method you're comfortable with.

Then if you want to reinstall to the exact same partitions use "manual partitioning" option like this:

[http://members.iinet.net.au/%7Eherman546/p22/028.png](http://members.iinet.net.au/%7Eherman546/p22/028.png)

You see he's chosen "Specify partitions manually (advanced)", then this screen will open:

[http://members.iinet.net.au/%7Eherman546/p22/031.png](http://members.iinet.net.au/%7Eherman546/p22/031.png)

Just be sure to select sda2 as that's where your Ubuntu is. And choose to "use as" ext3 same as before, tick on "format", set "Mount point" as "/" because / = root.

You don't need to change anything about the SWAP.

---

### Post by maori on 2010-02-10
Ok, maybe I understand what to do.

So, you think that fs-driver is the best way to save the folders, right?

Last thing: wich folder I must save, to have all configuration I had?

I'd love to save: configuration, images, mail, configuration evolution.

Thank you very much.

---

### Post by kansasnoob on 2010-02-16
> So, you think that fs-driver is the best way to save the folders, right?

That is just one way. **Use whatever method you are most comfortable with.** You appear to have only 2GB to 3GB to save so you could use the Live CD and a USB stick, DVD, etc. Or feel free to try using the Live CD to save to your /media.

> Last thing: wich folder I must save, to have all configuration I had?

Just go to Places > Computer and you should be able to identify your Ubuntu install by size. Once you double click it you should see your user-name folder and a lost & found folder, click on the UP arrow and you should see something like this:

[ATTACH]147261[/ATTACH]

You see I've highlighted the home folder. That contains documents, pictures, evolution, firefox, etc. If you right click on it and select Properties you can see the "used" size, so make sure wherever you're saving it is large enough. 

If you right click on home and select Copy you should then be able to paste it wherever you wish. Just be sure to verify the contents using either Windows with the fs-drivers or the Live CD.

To verify using the Live CD just double click on the saved "home" folder and you should see the user-name folder so double click on it, then click on View > Show Hidden and, besides your documents and such, you should see .evolution, .mozilla, etc.

I don't think I can explain it much better than that.

---

### Post by maori on 2010-02-16
No way...I give up :(

Impossible: with the Cd Live I can't find all the pics I have (had?).........try to install F-Driver, then I can see the disk in Windows, but if I try to open, Win says: Disk not format: do you want to format?

WTF!!!!

Many thanks for your help, just a little sad cause for me impossible to use Ubuntu.....

Now have to convince myself that all my job in Ubuntu are lost forever.......

Ciao, grazie (thanks)
Angelo

---

### Post by dtobias on 2010-06-29
> **kansasnoob said:**
> 

Anyway if Ubuntu is only 12GB I wonder if it encountered a "space limitation" problem?



I have gone through the kernels in safe mode and all end with the same result as described in this thread.  I haven't been able to get a live CD working yet but that is my next step.  The last time I was logged in I had approxametely 10GB remaining of my 160GB HD....could this be a space issue?

Based on the information in [http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

I ran the 'cat /proc/modules' command in Busybox and as stated on that page and I found I had no ide, ata, sata modules...which if I read correctly means that I'm missing my initrd.img.  

any help would be great!!

---

