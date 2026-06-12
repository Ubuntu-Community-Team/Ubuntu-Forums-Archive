---
title: "Error After Install Restart (Ubuntu 9.10)"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by punk_newbie on 2009-12-23
Hi, I'm a brand new Linux user, but I have a bit of knowledge in programming so I'm hoping that will help as I brave the adventure that is Linux.

So onto the problem. I recently attempted to install Ubuntu 9.10 on to my desktop as a clean install on a recently added 500GB HD(Set as Master HD). First time through everything seemed to be fine with the install no errors, but once I did the after install restart I ran into a "No Such Device" error when trying to select Ubuntu from the Grub. Selected XP(on slave HD) and it ran fine and dandy. So I reinserted the install CD and checked it for defects and it had 1 file corrupted.

Second time attempting to install with a newly burned disc and I am having the same problem. I ran the check for defects before installing and it came out clean. When I installed I selected wipe the drive before installing. Then once I tried to select Ubuntu from the Grub and error. This time I wrote it down.

```
No Such Device : 8470e440-c5b3-4ddc-b955-5efdbc774040
```So the question is what is causing this error and what can I do to fix it and run Ubuntu? When I set the 500 GB HD as master and the existing 80GB HD as slave I did so with the pins on the back of the HD's, do I need to do it as well in the BIOS? Is my computer simply not meeting specs? All help is appreciated.


Computer Specs
Pentium 4    2.53 Ghz
256 MB of RAM
NVidia GeForce Ti 4200
80 GB SeaGate HD (Original HD with XP installed and set to Slave) Ubuntu tells me on the LiveUser  set up that this is a bad HD. 
500 GB WesternDigital HD (Master HD)

---

### Post by Macmania on 2009-12-23
I am very interested in the solution for this as I am having the exact same error message. I checked the disc for defects and it checked out ok. I ran memtest86 and that came out good too. The install went totally smooth, seemingly with no trouble at all. I had it use the entire drive to install because I have no plans of any kind for dual boot setup. It also boots the live cd option with no problem at all and is actually what I am using to post this. This computer originally had Win XP on it but the hard drive died so I installed a new one and decided to give Ubuntu another spin as it has been a few years since I last used it. My current setup consists of:

Compaq Presario 2100 laptop (2103US)
AMD Athlon XP 2800+ processor
512mb pc2700 DDR ram 
ATI Mobility Radeon 4x AGP graphics 
Western Digital 160gb 5400rpm hard drive

---

### Post by Macmania on 2009-12-23
Ideas anybody??

---

### Post by oakgrove on 2009-12-23
Try pulling all the drives out of the computer except for the one you want Ubuntu on.  Put the Ubuntu drive as the Master on the IDE0 channel and of course set the jumper on the drive.  Install Ubuntu and see if that solves the problem.  If you try switching around drive orders in the BIOS after installing Ubuntu, that can cause confusion for GRUB.

---

### Post by presence1960 on 2009-12-24
> **oakgrove said:**
> Try pulling all the drives out of the computer except for the one you want Ubuntu on.  Put the Ubuntu drive as the Master on the IDE0 channel and of course set the jumper on the drive.  Install Ubuntu and see if that solves the problem.  ***_If you try switching around drive orders in the BIOS after installing Ubuntu, that can cause confusion for GRUB_***.

Not true for GRUB2. Grub2 actually uses the disk order as reported by fdisk not the order in BIOS as Legacy GRUB does. Here is my setup:

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4c62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f07bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7833    62918541    5  Extended
/dev/sdb2           12693       60801   386435542+  83  Linux
/dev/sdb5               1         522     4192902   82  Linux swap / Solaris
/dev/sdb6             523        2872    18876343+  83  Linux
/dev/sdb7            2873        5483    20972826   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02020202

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sdc2            6528       14360    62918572+   7  HPFS/NTFS
raz@raz-desktop:~$ 

```
sda1 is data storage
sdb2 is backups and clonezilla images
sdb6 is Ubuntu 9.10
sdb7 is Sabayon 5.0
sdc1 is XP
sdc2 is data for windows

My boot order in BIOS is sdb,sda, sdc.

Now note my grub.cfg:
```

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
	[COLOR="Red"]set root=(hd1,6)[/COLOR]
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	[COLOR="Red"]set root=(hd1,6)[/COLOR]
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	[COLOR="Red"]set root=(hd1,6)[/COLOR]
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	[COLOR="Red"]set root=(hd1,6)[/COLOR]
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-16-generic
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
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sdb7)" {
	insmod ext2
	[COLOR="Red"]set root=(hd1,7)[/COLOR]
	search --no-floppy --fs-uuid --set b9e8a529-266d-4dd2-b892-914893cee3a2
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sdb5 real_resume=/dev/sdb5
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sdb7)" {
	insmod ext2
	[COLOR="Red"]set root=(hd1,7)[/COLOR]
	search --no-floppy --fs-uuid --set b9e8a529-266d-4dd2-b892-914893cee3a2
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sdb5 real_resume=/dev/sdb5 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 5b8a70bc5646ab94
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Note the entries in red for Ubuntu & Sabayon 5.0- they are (hd1,6) and (hd1,7). But that disk is first in my BIOS boot order. If I had GRUB Legacy then they would be (hd0,6) & (hd0,7). That is one of the improvements in GRUB2. It used to cause confusion in GRUB Legacy when fdisk would report disks in a certain order but then the x (device) designation in (hdx,y) would be determined by the hard disk boot order in BIOS rather than the disk order in fdisk.

---

### Post by presence1960 on 2009-12-24
> **punk_newbie said:**
> Hi, I'm a brand new Linux user, but I have a bit of knowledge in programming so I'm hoping that will help as I brave the adventure that is Linux.

So onto the problem. I recently attempted to install Ubuntu 9.10 on to my desktop as a clean install on a recently added 500GB HD(Set as Master HD). First time through everything seemed to be fine with the install no errors, but once I did the after install restart I ran into a "No Such Device" error when trying to select Ubuntu from the Grub. Selected XP(on slave HD) and it ran fine and dandy. So I reinserted the install CD and checked it for defects and it had 1 file corrupted.

Second time attempting to install with a newly burned disc and I am having the same problem. I ran the check for defects before installing and it came out clean. When I installed I selected wipe the drive before installing. Then once I tried to select Ubuntu from the Grub and error. This time I wrote it down.

```
No Such Device : 8470e440-c5b3-4ddc-b955-5efdbc774040
```So the question is what is causing this error and what can I do to fix it and run Ubuntu? When I set the 500 GB HD as master and the existing 80GB HD as slave I did so with the pins on the back of the HD's, do I need to do it as well in the BIOS? Is my computer simply not meeting specs? All help is appreciated.


Computer Specs
Pentium 4    2.53 Ghz
256 MB of RAM
NVidia GeForce Ti 4200
80 GB SeaGate HD (Original HD with XP installed and set to Slave) Ubuntu tells me on the LiveUser  set up that this is a bad HD. 
500 GB WesternDigital HD (Master HD)

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Macmania on 2009-12-24
Well, it seems that I found a workaround here [http://ubuntuforums.org/showthread.php?t=1337254]("http://ubuntuforums.org/showthread.php?t=1337254") that seems to be doing the job. The only problem I am having now is the keyboard doesn't work. Now when I get to the Grub screen to select how/what I want to boot, I can't select anything!! What can I do to get it to recognize my keyboard?
*Minor Update* I just hooked up an external keyboard to it and it works in bios but still not at the Grub screen.

---

### Post by punk_newbie on 2009-12-24
Here is the results of the scripts run.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
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

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aa5be

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   975,306,149   975,306,087  83 Linux
/dev/sda2         975,306,150   976,768,064     1,461,915   5 Extended
/dev/sda5         975,306,213   976,768,064     1,461,852  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004876800 bytes
64 heads, 63 sectors/track, 971 cylinders, total 3915775 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8470e440-c5b3-4ddc-b955-5efdbc774040" TYPE="ext4" 
/dev/sda5: UUID="3d021a2e-9657-4ffe-98c7-33b6d5ae43a6" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: LABEL="CRUZER" UUID="6EB9-0393" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr1 on /cdrom type iso9660 (rw)
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
/dev/sr2 on /media/U3 System type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1 on /media/CRUZER type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 8470e440-c5b3-4ddc-b955-5efdbc774040
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
    search --no-floppy --fs-uuid --set 8470e440-c5b3-4ddc-b955-5efdbc774040
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8470e440-c5b3-4ddc-b955-5efdbc774040 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8470e440-c5b3-4ddc-b955-5efdbc774040
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8470e440-c5b3-4ddc-b955-5efdbc774040 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 0800524400523940
    drivemap -s (hd0) ${root}
    chainloader +1
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
UUID=8470e440-c5b3-4ddc-b955-5efdbc774040 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3d021a2e-9657-4ffe-98c7-33b6d5ae43a6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

```


I removed the Seagate drive containing XP and am currently reinstalling Ubuntu 9.10 . Once the Seagate drive was removed the boot process became much slower. Bios loaded slow, Grub loaded slow(Boot once to the Grub to see if removing HD removed the error) and the boot from the LiveCD was slower.

---

### Post by presence1960 on 2009-12-24
Everything seems in order. I happened to google this and found a couple links with the same method of solving this problem. here is one: [http://fivejacksons.com/brian/?p=325](http://fivejacksons.com/brian/?p=325)

To do what he said you need to open a root file browser- run in terminal ```
gksu nautilus
```
Navigate to /boot/grub/grub.cfg
Right click on grub.cfg and choose properties.
Click on the permissions tab. Change the root owner from read only to read and write and the group root from read only to read and write. Close the window. 
Now open the grub.cfg file and comment out that line.
Click Save on top toolbar. 
Close file.
Reboot & see what happens.

---

### Post by punk_newbie on 2009-12-24
The Install failed and I still got those No such device found errors. Now when I put the LiveCD in and the desktop loaded almost immediately an application problem window popped up saying "jockey-gtk" closed unexpectedly. I don't know if this is unrelated or what.

Once I run the gksu command in the terminal it spits out a bunch of errors before opening the root browser. Inside  of /boot/grub/  I only have the file "grubenv" no grub.cfg .

Here is a clickable thumbnail of the error and and file " /boot/grub/ "  

[[IMG]http://i5.photobucket.com/albums/y193/ilovebree/linux/th_error.png[/IMG]]("http://s5.photobucket.com/albums/y193/ilovebree/linux/?action=view&current=error.png")

---

### Post by Macmania on 2009-12-24
> **Macmania said:**
> The only problem I am having now is the keyboard doesn't work. Now when I get to the Grub screen to select how/what I want to boot, I can't select anything!! What can I do to get my keyboard to work?
*Minor Update* I just hooked up an external keyboard to it and it works in bios but still not at the Grub screen.

The strange thing with this is that during the install and when I boot the live cd the keyboard works perfectly. It is very frustrating because I am so close now and yet so far. Any ideas would be greatly appreciated. If I can't get this to work soon I think I am just going to have to put XP back on there. I don't want to but may have no choice because my friend is waiting/needing to get his computer back and is bugging me every day about it.

---

### Post by punk_newbie on 2009-12-26
> **punk_newbie said:**
> The Install failed and I still got those No such device found errors. Now when I put the LiveCD in and the desktop loaded almost immediately an application problem window popped up saying "jockey-gtk" closed unexpectedly. I don't know if this is unrelated or what.

Once I run the gksu command in the terminal it spits out a bunch of errors before opening the root browser. Inside  of /boot/grub/  I only have the file "grubenv" no grub.cfg .

Here is a clickable thumbnail of the error and and file " /boot/grub/ "  

[[IMG]http://i5.photobucket.com/albums/y193/ilovebree/linux/th_error.png[/IMG]]("http://s5.photobucket.com/albums/y193/ilovebree/linux/?action=view&current=error.png")


Still struggling and I can't figure out why I don't have the grub.cfg file.

---

### Post by pantherdj on 2010-01-02
I had the same problem when booting from the Live CD, but found a way to fix it.  If you go under the Places menu on the top bar and select your hard drive it will mount it.  Once mounted, you will see it in Nautilus.  Unless you do this, you will be looking at the CD files, not the hard drive.   Select the hard drive and go to /boot/grub/grub.cfg.  Right-click on grub.cfg and change permissions to "read-write" for group "Others".  Then select "open with gedit" on the same right-click menu.  I just commented the lines out with the # character instead of deleting anything and saved the file.  Reboot the system and it will work.  I am strictly a Newbie, so I hope this works for you.

---

### Post by punk_newbie on 2010-01-02
Alright using that method I was able to find and open the grub.cfg file. However I get an error saying that "You are not the owner and can not change permissions", and the line of code that the earlier posted guide says to comment out is not in the grub.cfg file. There are other 
```
search [COLOR=#339933]--[/COLOR]no[COLOR=#339933]-[/COLOR]floppy [COLOR=#339933]--[/COLOR]fs[COLOR=#339933]-[/COLOR]uuid [COLOR=#339933]--[/COLOR]set (numbers)
```
but not the exact one specified.

Does anyone have any ideas as to how I can set it so I can change permissions?

---

### Post by punk_newbie on 2010-01-14
Alright I believe I found the solution to my problem. So with my frustration with the 9.10 instillation I tried other distros (Fedora 12, 11, and finally Ubuntu 8.04). All failed, Fedora because I don't have enough RAM(or so the error message said). However Ubuntu 8.04 gave me a different error and after a successful install. On reboot it gave me an Error 18 when attempting to load the grub.

Some looking around and I found this thread.
[http://ubuntuforums.org/showthread.php?t=11764](http://ubuntuforums.org/showthread.php?t=11764)

On page 3 I found this post and it worked for me
[http://ubuntuforums.org/showpost.php?p=3447429&postcount=22](http://ubuntuforums.org/showpost.php?p=3447429&postcount=22)

Some further reading leads me to believe that my BIOS is not compatible with large capacity hard drives. The resulting problem when you try to boot the BIOS believes you are reading from a section of hard drive that does not exist.

---

