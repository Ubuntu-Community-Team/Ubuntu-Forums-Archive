---
title: "Something stole my Grub!"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by minerbog on 2010-01-07
Hi All,

I am after some advice on Grub please.

In my system I have two hard drives (hda0) (hda1).

My first drive is always install with ubuntu as this is my OS of choice, but I install different Os's on the second drive to try.

I have recently installed openSuse on my second drive and I think it stole Grub!!

The main drive is all still intact with grub and everything, but the second drive has also installed grub and now the second drive seems to have become my main boot drive!!

What I want to do is have hda0 as my main drive and grub settings but openSuse or whatever on drive two. How do I get hda0 back as my boot drive and how do I merge the grub settings so I can boot either to ubuntu or openSuse??

Many Thanks for any help.

---

### Post by tachuela on 2010-01-07
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by minerbog on 2010-01-07
Good info on Grub2 I agree but it doesn't really help.

Suse updated itself which now makes in impossible for me to boot into Suse. As the Suse disk has somehow taken over the MBR I cannot boot into my Ubuntu partition either.

Any further help on this would be greatly appreciated.

---

### Post by kansasnoob on 2010-01-07
Boot an Ubuntu Live CD and then post the output of the Boot Info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by minerbog on 2010-01-07
Nice script :)

Anyway in the end I reinstalled Karmic to reinstate the MBR.

What I'm trying to do now is get grub to recognize Suse and add an entry.

But here is the results.txt file. It would be great if you could maybe explain some of this??

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
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
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0ace0ac

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   389,238,884   389,238,822  83 Linux
/dev/sda2         389,238,885   398,283,479     9,044,595   5 Extended
/dev/sda5         389,238,948   398,283,479     9,044,532  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43044303

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,436,544   234,436,482  83 Linux


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="491c9ea0-1117-408d-bd1d-b0536cc8260b" TYPE="ext4" 
sda5: UUID="aca92743-10de-4143-b3a0-227001f7cb54" TYPE="swap" 
sdb1: UUID="ae6ac825-b3bf-4836-aeb0-77ba46a06835" TYPE="ext4" 

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
gvfs-fuse-daemon on /home/gavin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gavin)
/dev/sdb1 on /media/ae6ac825-b3bf-4836-aeb0-77ba46a06835 type ext4 (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 491c9ea0-1117-408d-bd1d-b0536cc8260b
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 491c9ea0-1117-408d-bd1d-b0536cc8260b
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=491c9ea0-1117-408d-bd1d-b0536cc8260b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 491c9ea0-1117-408d-bd1d-b0536cc8260b
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=491c9ea0-1117-408d-bd1d-b0536cc8260b ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 491c9ea0-1117-408d-bd1d-b0536cc8260b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=491c9ea0-1117-408d-bd1d-b0536cc8260b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 491c9ea0-1117-408d-bd1d-b0536cc8260b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=491c9ea0-1117-408d-bd1d-b0536cc8260b ro single 
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
menuentry "openSUSE 11.2 (i586) (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set ae6ac825-b3bf-4836-aeb0-77ba46a06835
	linux /boot/vmlinuz-2.6.31.8-0.1-default root=/dev/sdb1
	initrd /boot/initrd-2.6.31.8-0.1-default
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
UUID=491c9ea0-1117-408d-bd1d-b0536cc8260b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aca92743-10de-4143-b3a0-227001f7cb54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=============================== sdb1/etc/fstab: ===============================

/dev/disk/by-id/ata-ST3120022A_5JS0L9G9-part1 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-Maxtor_6Y200P0_Y6448ZEE-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST3120022A_5JS0L9G9-part2 /home                ext4       acl,user_xattr        1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/initrd
    .0GB: boot/initrd-2.6.31.8-0.1-default
    .0GB: boot/vmlinuz
    .0GB: boot/vmlinuz-2.6.31.8-0.1-default
=============================== StdErr Messages: ===============================

boot_info_script045.sh: line 1421: type: lvscan: not found
boot_info_script045.sh: line 1451: type: mdadm: not found

---

### Post by darkod on 2010-01-07
You probably already figured it out, but lets say it for other people reading this:
If you already have one version of linux running on the computer and you want to install another version of linux, there is NO NEED to install the bootloader of the second linux, in most cases.
Especially with the new grub2 in ubuntu 9.10, you can just run update-grub and it would find the newly installed linux and add it to the grub menu.
IMHO, especially with single drive setup, it's best keeping the original grub and not install grub with any subsequent linux install. Of course, there are exceptions.

---

### Post by kansasnoob on 2010-01-07
> Anyway in the end I reinstalled Karmic to reinstate the MBR.

First of all I want you to understand how to restore Ubuntu's grub2 so that's not necessary again. There are many ways, certainly nothing wrong with the **How to restore the Ubuntu grub bootloader (9.10 and beyond)** section here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I do things differently *(because I'm special)*, not really but I use my mount & chroot procedure and the "grub-install /dev/**[COLOR="Red"]sda[/COLOR]**" command (note I put sda in red because you must select the right location for you - yours is sda):

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then while chroot in the Ubuntu OS root partition I can deal with other errors as they arise. (**Note: your Ubuntu is on sda1 whereas I used sda3 in that chroot HowTo!**)

And please copy-n-paste commands! Just double click, then select copy, etc! Pretty please.

Anyway the first thing I'd try to add opensuse to Ubuntu's grub2 is (while booted into Ubuntu, not the Live CD):

```
sudo apt-get install --reinstall libdebian-installer4
```

```
sudo os-prober
```

```
sudo update-grub
```

Be sure and wait until it says "done". If it found it you'll see it in the list. Example (mine's different because I have no opensuse):

```
lance@lance-desktop:~$ sudo apt-get install --reinstall libdebian-installer4
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 33.0kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/main libdebian-installer4 0.63ubuntu2 [33.0kB]
Fetched 33.0kB in 0s (40.2kB/s)           
(Reading database ... 162155 files and directories currently installed.)
Preparing to replace libdebian-installer4 0.63ubuntu2 (using .../libdebian-installer4_0.63ubuntu2_i386.deb) ...
Unpacking replacement libdebian-installer4 ...
Setting up libdebian-installer4 (0.63ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
lance@lance-desktop:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
/dev/sda13:Ubuntu 8.04.3 LTS (8.04):Ubuntu:linux
/dev/sda3:Ubuntu lucid (development branch) (10.04):Ubuntu1:linux
/dev/sda5:Ubuntu 9.04 (9.04):Ubuntu2:linux
/dev/sda7:Linux Mint 7 Gloria - Main Edition (7):LinuxMint:linux
lance@lance-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda13
Found Ubuntu lucid (development branch) (10.04) on /dev/sda3
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7
done
lance@lance-desktop:~$ 

```

If it found it fine, we're done! If not we move on. The Boot Info Script shows:

> => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #1 for /boot/grub.
=> Windows is installed in the MBR of /dev/sdb

Well having that Win MBR on sdb might be a problem so it would be nice to have Suse's legacy grub on sdb, **[COLOR="Red"]not on sda[/COLOR] and please take note here that I am not proficient with opensuse's grub!** But then just boot your Ubuntu Live CD and once at the live desktop go to terminal and run:

```
sudo grub
```

Continue only if you get a grub prompt like this:

```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 

```

**If you see anything other than a grub shell STOP, reboot, and we'll try something else!**

If you get the grub shell do this:

```
find /boot/grub/stage1
```

I'd expect it to return **(hd1,0)**, **if not STOP**, if so then run:

```
root (hd1,0)
```

And:

```
setup (hd1)
```

And:

```
quit
```

Then just to be sure we didn't hose grub2 run:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

And:

```
sudo reboot
```

Once booted into Ubuntu again try the previous steps:

sudo apt-get install &#8211;reinstall libdebian-installer4
sudo os-prober
sudo  update-grub

If that doesn't work I'll have to try and build a custom menu entry for suse.

---

### Post by minerbog on 2010-01-07
> **darkod said:**
> You probably already figured it out, but lets say it for other people reading this:
If you already have one version of linux running on the computer and you want to install another version of linux, there is NO NEED to install the bootloader of the second linux

Yep worked that one out!!! DOH!

Thanks for all your help guys. Both systems are now up and running fine. Although I re-installed ubuntu I now have the knowledge to fix it, if it happens again (or should I say, if I break it again!!)

Many Thanks All

---

### Post by llawwehttam on 2010-01-07
Hmm sounds like a job for *superman tune* SUPERGRUB!!!!! [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by kansasnoob on 2010-01-07
> **minerbog said:**
> Yep worked that one out!!! DOH!

Thanks for all your help guys. Both systems are now up and running fine. Although I re-installed ubuntu I now have the knowledge to fix it, if it happens again (or should I say, if I break it again!!)

Many Thanks All

Exactly what worked?

It would be helpful to know for future use :)

---

### Post by minerbog on 2010-01-08
The solution for me was nothing technical at all.

I reinstalled ubuntu and that resorted the MBR and Grub.

Then when installing Suse I made sure that it didn't install a bootloader (which I didn't do the first time!!).

Then booted in ubuntu and run the following from a terminal.

```

sudo update-grub

```

Then reboot and all works fine.

As I said, nothing very technical!!

---

