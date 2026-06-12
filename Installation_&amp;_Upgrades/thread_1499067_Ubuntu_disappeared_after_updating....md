---
title: "Ubuntu disappeared after updating..."
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by arcelivez on 2010-06-01
Hello,

well my problem is as follows:

on ubuntu lucid I ran:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Then I restarted the computer (oh one more thing, right after this update, before restarting, the nvidia display became a question mark).
Well after the restarting it failed to boot, by saying something like : init failed to respawn, or something like that, and later complained about graphic driver running in low graphic mode. But xserver didn't boot up at all...

Well I went to the recovery console in the grub menu and from there I ran:

```

sudo apt-get dist-upgrade

```

And then I restarted after it finished the procedures and then no ubuntu in the grub menu...

So what should I do? I was thinking of reinstalling from ubuntu lucid cd, but I'm affraid it might mess up things and I might loose some of my previous settings or information, which I can't afford to loose... :/

OK, I've learnt my lesson and won't update ubuntu anymore, since it's the second time i'm encountering serious problems after updating it. But please if somebody can, please help me fix this now. I need my os with all my settings back as it was... :/

P.S. I've seen that my /home partition is fine, and the root partition has less files/folders than the live cd root partition has, so I believe that only some important system files went missing up to now...

---

### Post by darkod on 2010-06-01
First of all, UPDATE and UPGRADE are not the same. Updates are usually the updates for the installed packages/software. Upgrade is to go to the newer version release.

Since Lucid IS the LATEST version of ubuntu, why were you doing dist-upgrade? To which version do you think it will upgrade you?

Read these instructions and run the boot info script which hopefully will show more details about the system:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by arcelivez on 2010-06-01
OK, sorry, I thought it also did upgrades like the linux core? I'm pretty sure the dist-upgrade did that? I might be wrong though, since I'm a noob. here's what I got from the script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/disks/root.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   225,023,991   204,050,424   7 HPFS/NTFS
/dev/sda3         225,026,046   499,322,879   274,296,834   f W95 Ext d (LBA)
/dev/sda5         225,026,048   323,151,871    98,125,824   7 HPFS/NTFS
/dev/sda6         323,153,920   405,182,463    82,028,544  83 Linux
/dev/sda7         405,184,512   411,432,959     6,248,448  82 Linux swap / Solaris
/dev/sda8         411,435,008   499,322,879    87,887,872  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       56661f11-a9bd-44e4-b0c6-b72a3863c6ec   ext4                                     
/dev/sda1        362AA65B2AA6183F                       ntfs       RECOVERY                      
/dev/sda2        08DAA81BDAA80752                       ntfs       System                        
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2E8234EF8234BCE1                       ntfs       Extra                         
/dev/sda6        1eb0dbec-b864-439f-9fb6-fe3b01e7060f   ext3                                     
/dev/sda7        bbaf8654-15f7-4186-a510-b78cefa12e53   swap                                     
/dev/sda8        8c741b94-bfa5-49dc-8fbd-f3c98d7fab58   xfs                                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1eb0dbec-b864-439f-9fb6-fe3b01e7060f ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda8        /media/8c741b94-bfa5-49dc-8fbd-f3c98d7fab58 xfs        (rw,nosuid,nodev,uhelper=udisks)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set f432855b328523a8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set f432855b328523a8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set f432855b328523a8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set f432855b328523a8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 362aa65b2aa6183f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 08daa81bdaa80752
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


    .1GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.31-14-generic
   5.6GB: boot/initrd.img-2.6.31-20-generic
   2.6GB: boot/vmlinuz-2.6.31-14-generic
   4.6GB: boot/vmlinuz-2.6.31-20-generic
   5.6GB: initrd.img
    .9GB: initrd.img.old
   4.6GB: vmlinuz
   2.6GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1eb0dbec-b864-439f-9fb6-fe3b01e7060f
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1eb0dbec-b864-439f-9fb6-fe3b01e7060f
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 1eb0dbec-b864-439f-9fb6-fe3b01e7060f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 1eb0dbec-b864-439f-9fb6-fe3b01e7060f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 362aa65b2aa6183f
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 08daa81bdaa80752
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=8c741b94-bfa5-49dc-8fbd-f3c98d7fab58 /home           xfs     defaults        0       2
# swap was on /dev/sda7 during installation
UUID=bbaf8654-15f7-4186-a510-b78cefa12e53 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 184.9GB: boot/grub/core.img
 184.9GB: boot/grub/grub.cfg

```

---

### Post by darkod on 2010-06-01
You don't have any kernels on /dev/sda6.

But I don't know how to add them with chroot exactly, kansasnoob is the expert for that.
You around kansas? :)

---

### Post by kansasnoob on 2010-06-01
> the nvidia display became a question mark

A kernel upgrade likely killed your nVidia drivers!

You'll need to reinstall the nVidia drivers. This may be helpful:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

> Incompatibility with nVidia upstream driver installer

Ubuntu 10.04 LTS includes improved integration for nVidia binary driver packages. Unfortunately, this comes at the expense of compatibility with the installer provided upstream on the nVidia website. Users who wish to use the nVidia binary video drivers with 10.04 LTS should install them using the Ubuntu packages, as made available under System -> Administration -> Hardware Drivers. 

You may need to restart in Recovery Mode and then select "failsafeX" to get to a desktop so you can pull that off.

---

### Post by kansasnoob on 2010-06-01
> **darkod said:**
> You don't have any kernels on /dev/sda6.

But I don't know how to add them with chroot exactly, kansasnoob is the expert for that.
You around kansas? :)

Oh crap, I didn't see that :(

I'll have to do some more studying.

---

### Post by arcelivez on 2010-06-01
> **kansasnoob said:**
> A kernel upgrade likely killed your nVidia drivers!

You'll need to reinstall the nVidia drivers. This may be helpful:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)



You may need to restart in Recovery Mode and then select "failsafeX" to get to a desktop so you can pull that off.

Well my drivers in lucid were previously installed with  System -> Administration -> Hardware Drivers.
No upstream drivers form nVidia website have been used.

About the recovery mode, I don't have it anymore, it diseappeared together with the ubuntu normal mode. What's left ar the windows boots and memory tests which were created by linux.

So any ideas what I should do? Or how do I enter that Recovery Mode? Or should I do that from this live cd somehow?

---

### Post by kansasnoob on 2010-06-01
> **arcelivez said:**
> Well my drivers in lucid were previously installed with  System -> Administration -> Hardware Drivers.
No upstream drivers form nVidia website have been used.

About the recovery mode, I don't have it anymore, it diseappeared together with the ubuntu normal mode. What's left ar the windows boots and memory tests which were created by linux.

So any ideas what I should do? Or how do I enter that Recovery Mode? Or should I do that from this live cd somehow?

Yeah forget that. Darkod found the problem, hold on :)

---

### Post by kansasnoob on 2010-06-01
First look here just to get an idea how my chroot process works:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then copy-n-paste the following commands:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now things get tricky! It's impossible for me to know what's going on without seeing the full terminal output pasted back here in a reply!

You can feel free to repeat any of the commands from here to where we exit the chroot and unmount repeatedly!

I'd begin with:

```
apt-get clean
```

```
apt-get update
```

```
dpkg --configure -a
```

```
apt-get -f install
```

```
apt-get dist-upgrade
```

```
update-grub
```

NOW, that "update-grub" command can tell you a lot! Does it show something like:

> Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.34-5-generic
Found initrd image: /boot/initrd.img-2.6.34-5-generic
Found linux image: /boot/vmlinuz-2.6.34-4-generic
Found initrd image: /boot/initrd.img-2.6.34-4-generic


:confused:

Your kernel numbers will be different, but if so it probably found the new kernel and it may be good to give a reboot a try after exiting the chroot.

If not any errors displayed during that process can be very helpful in determining what to do next.

In some situations I've even resorted to (if you have Ubuntu and not a derivative):

```
apt-get install --reinstall ubuntu-minimal
```

```
apt-get install --reinstall ubuntu-standard
```

```
apt-get install --reinstall ubuntu-desktop
```

Or one that's saved my bacon a few times:

```
dpkg-reconfigure -phigh -a
```

But that can take a long, long time! Like an hour and a half!

When you're done in the chroot just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

I hope that helps or at least yields some clues.

---

### Post by kansasnoob on 2010-06-01
BTW I've got to step out for a while so please be patient :)

---

### Post by arcelivez on 2010-06-01
OK, so I finally did it the second time and I will post my terminal output now, which i've put in together in a file, however the forum didn't let me upload 35 kb, so I'll try to post it here:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get clean
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get update
Hit http://deb.opera.com stable Release.gpg
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Get:1 http://ftp.de.debian.org etch Release.gpg [1,033B]                       
Ign http://ftp.de.debian.org/debian/ etch/main Translation-en_US               
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net/reacocard-awn/ubuntu/ gutsy/main Translation-en_US
Hit http://deb.opera.com stable Release                                        
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ karmic/main Translation-en_US
Get:3 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/compiz/ubuntu/ lucid/main Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ lucid/main Translation-en_US
Get:4 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Get:5 http://dl.google.com stable Release [2,544B]                             
Get:6 http://ftp.de.debian.org etch Release [67.8kB]                           
Hit http://archive.ubuntu.com lucid Release                                   
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ lucid/main Translation-en_US
Ign http://ftp.de.debian.org etch Release                                      
Ign http://deb.opera.com stable/non-free Packages                              
Get:7 http://dl.google.com stable/main Packages [1,051B]                       
Hit http://ftp.de.debian.org etch/main Packages                                
Hit http://archive.ubuntu.com lucid/universe Packages                          
Get:8 http://ppa.launchpad.net gutsy Release [27.6kB]                          
Hit http://ppa.launchpad.net karmic Release                          
Ign http://deb.opera.com stable/non-free Packages                    
Get:9 http://ppa.launchpad.net lucid Release [57.3kB]                          
Hit http://ppa.launchpad.net lucid Release                                    
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://archive.ubuntu.com lucid/main Packages                              
Hit http://archive.ubuntu.com lucid/restricted Packages              
Hit http://archive.ubuntu.com lucid/multiverse Packages              
Hit http://archive.ubuntu.com lucid/universe Sources                 
Get:10 http://ppa.launchpad.net lucid Release [57.3kB]               
Hit http://ppa.launchpad.net lucid Release                           
Ign http://ppa.launchpad.net lucid Release                           
Ign http://ppa.launchpad.net lucid Release                              
Hit http://archive.ubuntu.com lucid/main Sources                        
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Ign http://ppa.launchpad.net gutsy/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net gutsy/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net gutsy/main Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Fetched 5,435B in 1s (4,512B/s)
W: GPG error: http://ftp.de.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY B5D0C804ADB11277
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# dpkg --configure -a
root@ubuntu:/# 
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez libpolkit-qt-1-0 libmono0
  libqt4-opengl-dev libpthread-stubs0 remuco-base libsox-fmt-base
  libqtscript4-network libgsasl7 libtaglib2.0-cil
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgl1-mesa-dev libgmime-2.0-2a libqtscript4-gui
  libcrypt-ssleay-perl libboost-program-options1.40.0 libxcb-xv0
  libsox-fmt-alsa libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 libexiv2-6
  mysql-server-core-5.1 libqtscript4-sql x11proto-kb-dev libdvbpsi5 grub-pc
  libqtscript4-xml mesa-common-dev libqt4-dbg xtrans-dev libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libbabl-0.0-0 libqt4-dev
  libcrypt-simple-perl libsoprano4 akonadi-server libvlc2 gettext python-qt4
  x11proto-input-dev libclucene0ldbl libxml-simple-perl
  shared-desktop-ontologies python-sip linux-headers-2.6.32-21 vlc-nox
  openshot-doc cvs amarok-utils virtuoso-nepomuk libmikmod2 libqimageblitz4
  libglu1-mesa-dev libdrm-dev libupnp3 mysql-client-core-5.1
  libmono-zeroconf1.0-cil ttf-symbol-replacement libmailutils2 qt4-qmake
  kdepimlibs-data libmatroska0 python-gtkmozembed libxcb-keysyms1
  libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1 libxine1-console
  libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1 soprano-daemon
  wine1.2-gecko libservlet2.5-java cabextract libntlm0 libxau-dev os-prober
  packagekit exim4-config libkephal4 libgdata1.4-cil libgtk2-sexy-perl
  automake libgimp2.0 ksysguardd libc6-dbg libpackagekit-glib2-12 libattica0
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  libx11-dev kdelibs5-data libqtscript4-uitools libtar winbind grub-common
  libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a libmlt-data
  libxcb1-dev libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java pingus-data x11proto-core-dev keyutils
  libxdmcp-dev libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer
  nvidia-settings libstreamanalyzer0 libfaac0 mono-gmcs
  libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  apparmor-utils aptdaemon apturl at avant-window-navigator-data-trunk
  avant-window-navigator-trunk awn-applets-c-core-trunk
  awn-applets-c-extras-trunk awn-applets-python-core-trunk
  awn-applets-python-extras-trunk awn-settings-trunk computer-janitor-gtk
  consolekit cron empathy firefox-gnome-support friendly-recovery ftp
  gconf-editor gdebi gksu gnome-codec-install gnome-keyring irqbalance
  jockey-common jockey-gtk language-selector libgl1-mesa-dev libglu1-mesa-dev
  libgnome-vfs2.0-cil libgnome2-vfs-perl libgnomekbd4 libgnomevfs2-0
  libgnomevfs2-extra libpolkit-gtk-1-0 libqt4-dev libqt4-opengl-dev
  librpc-xml-perl libwww-perl libx11-dev libxau-dev libxcb1-dev libxklavier16
  libxml-parser-perl libxvmc1 logrotate mesa-common-dev ntpdate
  nvidia-settings packagekit plymouth-theme-ubuntu-text policykit-1
  policykit-1-gnome ppp pppconfig pppoeconf python-aptdaemon
  python-aptdaemon-gtk rsyslog screen-resolution-extra software-center
  software-properties-gtk telnet ubufox ubuntu-minimal ubuntu-standard
  ubuntu-system-service ufw update-manager ureadahead x11-xkb-utils xtrans-dev
0 upgraded, 0 newly installed, 72 to remove and 0 not upgraded.
After this operation, 94.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176059 files and directories currently installed.)
Removing apparmor-utils ...
Removing software-center ...
Removing aptdaemon ...
Removing ubufox ...
Removing apturl ...
Removing ubuntu-standard ...
Removing at ...
Removing awn-settings-trunk ...
Removing awn-applets-c-core-trunk ...
Removing awn-applets-c-extras-trunk ...
Removing awn-applets-python-core-trunk ...
Removing awn-applets-python-extras-trunk ...
Removing computer-janitor-gtk ...
Removing jockey-gtk ...
Removing jockey-common ...
Removing ubuntu-system-service ...
Removing nvidia-settings ...
Removing screen-resolution-extra ...
Removing python-aptdaemon-gtk ...
Removing python-aptdaemon ...
Removing libpolkit-gtk-1-0 ...
Removing gconf-editor ...
Removing policykit-1-gnome ...
Removing policykit-1 ...
Removing consolekit ...
Removing logrotate ...
Removing cron ...
Removing empathy ...
Removing firefox-gnome-support ...
Removing friendly-recovery ...
Removing ftp ...
Removing gdebi ...
Removing update-manager ...
Removing software-properties-gtk ...
Removing language-selector ...
Removing gnome-codec-install ...
Removing gksu ...
Removing gnome-keyring ...
Removing irqbalance ...
Removing libqt4-opengl-dev ...
Removing libglu1-mesa-dev ...
Removing libgl1-mesa-dev ...
Removing libgnome-vfs2.0-cil ...
Removing libgnome-vfs2.0-cil from Mono
Removing libgnome2-vfs-perl ...
Removing libgnomekbd4 ...
Removing libgnomevfs2-extra ...
Removing libgnomevfs2-0 ...
Removing libqt4-dev ...
Removing librpc-xml-perl ...
Removing libxml-parser-perl ...
Removing libwww-perl ...
Removing mesa-common-dev ...
Removing libx11-dev ...
Removing libxcb1-dev ...
Removing libxau-dev ...
Removing libxklavier16 ...
Removing libxvmc1 ...
Removing ubuntu-minimal ...
Removing ntpdate ...
Removing packagekit ...
Removing plymouth-theme-ubuntu-text ...
update-alternatives: warning: alternative /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth (part of link group text.plymouth) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/text.plymouth is dangling, it will be updated with best choice.
rmdir: failed to remove `/lib/plymouth/themes': Directory not empty
rmdir: failed to remove `/lib/plymouth': Directory not empty
update-initramfs: deferring update (trigger activated)
Removing pppoeconf ...
Removing pppconfig ...
Removing ppp ...
Stopping all PPP connections...done.
Removing rsyslog ...
Removing telnet ...
Removing ufw ...
Removing ureadahead ...
Removing x11-xkb-utils ...
dpkg: warning: while removing x11-xkb-utils, directory '/var/lib/xkb' not empty so not removed.
Removing xtrans-dev ...
Removing avant-window-navigator-trunk ...
Removing avant-window-navigator-data-trunk ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/Anglonas.desktop: ParsingError in file '/usr/share/applications/Anglonas.desktop', [Desktop Entry]-Header missing
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for initramfs-tools ...
Processing triggers for python-support ...
Processing triggers for python-central ...
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 

root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Flashiukas: No such file or directory  // Flashiukas is my USB stick...
ls: cannot access /media/Flashiukas: No such file or directory
ls: cannot access /media/Flashiukas: No such file or directory
ls: cannot access /media/Flashiukas: No such file or directory
ls: cannot access /media/Flashiukas: No such file or directory
ls: cannot access /media/Flashiukas: No such file or directory
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get install --reinstall ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libqtscript4-gui
  libcrypt-ssleay-perl libboost-program-options1.40.0 libxcb-xv0
  libsox-fmt-alsa libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libbabl-0.0-0 libcrypt-simple-perl
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg apparmor libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata winbind grub-common
  libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a libmlt-data
  libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cron logrotate ntpdate rsyslog ureadahead
Suggested packages:
  exim4 postfix mail-transport-agent anacron checksecurity mailx rsyslog-mysql
  rsyslog-pgsql rsyslog-doc rsyslog-gnutls rsyslog-gssapi rsyslog-relp
The following NEW packages will be installed:
  cron logrotate ntpdate rsyslog ubuntu-minimal ureadahead
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 558kB of archives.
After this operation, 1,769kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/main cron 3.0pl1-106ubuntu5 [89.7kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid/main logrotate 3.7.8-4ubuntu2 [45.5kB]
Get:3 http://archive.ubuntu.com/ubuntu/ lucid/main ntpdate 1:4.2.4p8+dfsg-1ubuntu2 [72.1kB]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid/main rsyslog 4.2.0-2ubuntu8 [295kB]
Get:5 http://archive.ubuntu.com/ubuntu/ lucid/main ureadahead 0.100.0-4.1 [24.8kB]
Get:6 http://archive.ubuntu.com/ubuntu/ lucid/main ubuntu-minimal 1.197 [30.7kB]
Fetched 558kB in 2s (207kB/s)      
Selecting previously deselected package cron.
(Reading database ... 169449 files and directories currently installed.)
Unpacking cron (from .../cron_3.0pl1-106ubuntu5_amd64.deb) ...
Selecting previously deselected package logrotate.
Unpacking logrotate (from .../logrotate_3.7.8-4ubuntu2_amd64.deb) ...
Selecting previously deselected package ntpdate.
Unpacking ntpdate (from .../ntpdate_1%3a4.2.4p8+dfsg-1ubuntu2_amd64.deb) ...
Selecting previously deselected package rsyslog.
Unpacking rsyslog (from .../rsyslog_4.2.0-2ubuntu8_amd64.deb) ...
Selecting previously deselected package ureadahead.
Unpacking ureadahead (from .../ureadahead_0.100.0-4.1_amd64.deb) ...
Selecting previously deselected package ubuntu-minimal.
Unpacking ubuntu-minimal (from .../ubuntu-minimal_1.197_amd64.deb) ...
Processing triggers for man-db ...
Setting up cron (3.0pl1-106ubuntu5) ...

Setting up logrotate (3.7.8-4ubuntu2) ...
Setting up ntpdate (1:4.2.4p8+dfsg-1ubuntu2) ...
Setting up rsyslog (4.2.0-2ubuntu8) ...

Setting up ureadahead (0.100.0-4.1) ...

Setting up ubuntu-minimal (1.197) ...
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get install --reinstall ubuntu-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libqtscript4-gui
  libcrypt-ssleay-perl libboost-program-options1.40.0 libxcb-xv0
  libsox-fmt-alsa libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libbabl-0.0-0 libcrypt-simple-perl
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata winbind grub-common
  libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a libmlt-data
  libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apparmor-utils at friendly-recovery ftp irqbalance librpc-xml-perl
  libwww-perl libxml-parser-perl plymouth-theme-ubuntu-text ppp pppconfig
  pppoeconf telnet ufw
Suggested packages:
  apparmor-docs libterm-readline-gnu-perl default-mta mail-transport-agent
  libapache2-mod-perl2 xdialog
The following NEW packages will be installed:
  apparmor-utils at friendly-recovery ftp irqbalance librpc-xml-perl
  libwww-perl libxml-parser-perl plymouth-theme-ubuntu-text ppp pppconfig
  pppoeconf telnet ubuntu-standard ufw
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,897kB of archives.
After this operation, 8,720kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/main libwww-perl 5.834-1 [401kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid/main libxml-parser-perl 2.36-1.1build3 [324kB]
Get:3 http://archive.ubuntu.com/ubuntu/ lucid/main librpc-xml-perl 0.72-1 [235kB]
Get:4 http://archive.ubuntu.com/ubuntu/ lucid/main apparmor-utils 2.5-0ubuntu3 [105kB]
Get:5 http://archive.ubuntu.com/ubuntu/ lucid/main at 3.1.11-1ubuntu5 [50.5kB] 
Get:6 http://archive.ubuntu.com/ubuntu/ lucid/main friendly-recovery 0.2.10 [4,994B]
Get:7 http://archive.ubuntu.com/ubuntu/ lucid/main ftp 0.17-19build1 [58.5kB]  
Get:8 http://archive.ubuntu.com/ubuntu/ lucid/main irqbalance 0.55+20091017-3ubuntu2 [20.6kB]
Get:9 http://archive.ubuntu.com/ubuntu/ lucid/main plymouth-theme-ubuntu-text 0.8.2-2ubuntu2 [21.0kB]
Get:10 http://archive.ubuntu.com/ubuntu/ lucid/main ppp 2.4.5~git20081126t100229-0ubuntu3 [376kB]
Get:11 http://archive.ubuntu.com/ubuntu/ lucid/main pppconfig 2.3.18ubuntu2 [44.7kB]
Get:12 http://archive.ubuntu.com/ubuntu/ lucid/main pppoeconf 1.19ubuntu1 [23.3kB]
Get:13 http://archive.ubuntu.com/ubuntu/ lucid/main telnet 0.17-36build1 [72.2kB]
Get:14 http://archive.ubuntu.com/ubuntu/ lucid/main ubuntu-standard 1.197 [30.8kB]
Get:15 http://archive.ubuntu.com/ubuntu/ lucid/main ufw 0.30pre1-0ubuntu2 [129kB]
Fetched 1,897kB in 10s (186kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package libwww-perl.
(Reading database ... 169527 files and directories currently installed.)
Unpacking libwww-perl (from .../libwww-perl_5.834-1_all.deb) ...
Selecting previously deselected package libxml-parser-perl.
Unpacking libxml-parser-perl (from .../libxml-parser-perl_2.36-1.1build3_amd64.deb) ...
Selecting previously deselected package librpc-xml-perl.
Unpacking librpc-xml-perl (from .../librpc-xml-perl_0.72-1_all.deb) ...
Selecting previously deselected package apparmor-utils.
Unpacking apparmor-utils (from .../apparmor-utils_2.5-0ubuntu3_amd64.deb) ...
Selecting previously deselected package at.
Unpacking at (from .../at_3.1.11-1ubuntu5_amd64.deb) ...
Selecting previously deselected package friendly-recovery.
Unpacking friendly-recovery (from .../friendly-recovery_0.2.10_all.deb) ...
Selecting previously deselected package ftp.
Unpacking ftp (from .../ftp_0.17-19build1_amd64.deb) ...
Selecting previously deselected package irqbalance.
Unpacking irqbalance (from .../irqbalance_0.55+20091017-3ubuntu2_amd64.deb) ...
Selecting previously deselected package plymouth-theme-ubuntu-text.
Unpacking plymouth-theme-ubuntu-text (from .../plymouth-theme-ubuntu-text_0.8.2-2ubuntu2_amd64.deb) ...
Selecting previously deselected package ppp.
Unpacking ppp (from .../ppp_2.4.5~git20081126t100229-0ubuntu3_amd64.deb) ...
Selecting previously deselected package pppconfig.
Unpacking pppconfig (from .../pppconfig_2.3.18ubuntu2_all.deb) ...
Selecting previously deselected package pppoeconf.
Unpacking pppoeconf (from .../pppoeconf_1.19ubuntu1_all.deb) ...
Selecting previously deselected package telnet.
Unpacking telnet (from .../telnet_0.17-36build1_amd64.deb) ...
Selecting previously deselected package ubuntu-standard.
Unpacking ubuntu-standard (from .../ubuntu-standard_1.197_amd64.deb) ...
Selecting previously deselected package ufw.
Unpacking ufw (from .../ufw_0.30pre1-0ubuntu2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/Anglonas.desktop: ParsingError in file '/usr/share/applications/Anglonas.desktop', [Desktop Entry]-Header missing
Processing triggers for python-support ...
Setting up libwww-perl (5.834-1) ...
Setting up libxml-parser-perl (2.36-1.1build3) ...
Setting up librpc-xml-perl (0.72-1) ...
Setting up apparmor-utils (2.5-0ubuntu3) ...
Setting up at (3.1.11-1ubuntu5) ...

Setting up friendly-recovery (0.2.10) ...
Setting up ftp (0.17-19build1) ...
update-alternatives: using /usr/bin/netkit-ftp to provide /usr/bin/ftp (ftp) in auto mode.

Setting up irqbalance (0.55+20091017-3ubuntu2) ...

Setting up plymouth-theme-ubuntu-text (0.8.2-2ubuntu2) ...
update-alternatives: using /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth to provide /lib/plymouth/themes/text.plymouth (text.plymouth) in auto mode.
update-initramfs: deferring update (trigger activated)

Setting up ppp (2.4.5~git20081126t100229-0ubuntu3) ...

Setting up pppconfig (2.3.18ubuntu2) ...

Setting up pppoeconf (1.19ubuntu1) ...

Setting up telnet (0.17-36build1) ...
update-alternatives: using /usr/bin/telnet.netkit to provide /usr/bin/telnet (telnet) in auto mode.

Setting up ubuntu-standard (1.197) ...
Setting up ufw (0.30pre1-0ubuntu2) ...

Processing triggers for initramfs-tools ...
Processing triggers for python-central ...
root@ubuntu:/# 

root@ubuntu:/# 
root@ubuntu:/# apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: indicator-applet-session but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
                  Recommends: firefox-gnome-support but it is not going to be installed
E: Broken packages
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# dpkg-reconfigure -phigh -a
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "force-reload" failed.
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

 * Starting AppArmor profiles                                                    * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "start" failed.
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "reload" failed.
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support                umount: /proc/sys/fs/binfmt_misc: not mounted
update-binfmts: warning: Couldn't unmount the binfmt_misc filesystem from
/proc/sys/fs/binfmt_misc. 
                                                                         [ OK ]
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.
root@ubuntu:/# 

root@ubuntu:/# 
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

```

I'll try to restart again, but last time I tried, nothing seemed to have changed in the grub and overall boot. So I'm counting for you to check this. :)

---

### Post by kansasnoob on 2010-06-01
I don't know how or why but your software sources are a total mess:

> Get:1 [http://ftp.de.debian.org](http://ftp.de.debian.org) etch Release.gpg [1,033B]                       
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) etch/main Translation-en_US               

> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy/main Translation-en_US

> Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net/](http://ppa.launchpad.net/)**tualatrix**/ppa/ubuntu/ karmic/main Translation-en_US

I could go on but you have all kinds of crap wrong with your software sources!

If you replaced the entire sources.list using nano in a chroot I'd give it maybe a 10% chance of success.

---

### Post by arcelivez on 2010-06-01
Uhm, so I didn't really understand what you suggest me do. Hmm, should I try to replace my /etc/apt/sources.list with those lines in your quotes or what??? :confused: I'm kinda confused and yeah I get those software source problems often lately, no idea, why they keep coming while I am even on live cd?

---

### Post by kansasnoob on 2010-06-02
My point was that your sources.list must be a total mess. You have all kinds of improper repos in there: Debian etch, Gutsy, loads of PPA's, etc.

And gedit doesn't work properly in a chroot so you'd have to use nano to replace the sources.list, and IMO the odds of that being successful are maybe 10%.

If I were you I'd backup everything important and do a clean install. Here's a Lucid i386 sources.list though if you want to try it:

```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

Then in a chroot as described previously first replace your sources.list with that one using:

```
nano /etc/apt/sources.list
```

Followed by:

```
apt-get clean
```

```
apt-get update
```

```
apt-get dist-upgrade
```

And see what happens. You may have to try some of those other commands to clear errors.

---

### Post by arcelivez on 2010-06-02
OK, so I tried changing the contents of sources.list with your given ones, But I believe this still doesn't install the kernel again. :/ 
Here's the terminal
```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# ls
apps  boot   dev  home    lib32  lost+found  mnt    proc  sbin     srv  tmp  var
bin   cdrom  etc  lib    lib64  media       opt    root  selinux  sys  usr
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# cd /
root@ubuntu:/# ls
apps  boot   dev  home    lib32  lost+found  mnt    proc  sbin     srv  tmp  var
bin   cdrom  etc  lib    lib64  media       opt    root  selinux  sys  usr
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# more sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid mai
n restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted unive
rse multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted u
niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get clean
root@ubuntu:/etc/apt# apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:2 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Get:3 http://dl.google.com stable Release [2,544B]                             
Hit http://deb.opera.com stable Release                                        
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid Release                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release 
Get:4 http://ppa.launchpad.net lucid Release [57.3kB]                
Hit http://ppa.launchpad.net lucid Release                                    
Ign http://ppa.launchpad.net lucid Release     
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:5 http://dl.google.com stable/main Packages [1,051B]                       
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 4,092B in 0s (4,782B/s)
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# dpkg --configure -a
Processing triggers for python-central ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  cups-bsd cups-client cups-common kdebase-runtime-data libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libgtkmm-2.4-1c2a
  libsnmp-base libsnmp15 simple-scan skype
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.0MB of archives.
After this operation, 521kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner skype 2.1.0.81-1ubuntu5 [20.2MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcups2 1.4.3-1ubuntu1 [223kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main cups-common 1.4.3-1ubuntu1 [1,463kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main cups-bsd 1.4.3-1ubuntu1 [44.8kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsimage2 1.4.3-1ubuntu1 [53.1kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main cups-client 1.4.3-1ubuntu1 [141kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdebase-runtime-data 4:4.4.2-0ubuntu4.1 [4,014kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupscgi1 1.4.3-1ubuntu1 [31.5kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsdriver1 1.4.3-1ubuntu1 [22.1kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsmime1 1.4.3-1ubuntu1 [15.4kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsppdc1 1.4.3-1ubuntu1 [60.0kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtkmm-2.4-1c2a 1:2.20.3-0ubuntu1 [1,190kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsnmp-base 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 [1,335kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsnmp15 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 [2,178kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main simple-scan 1.0.3-0ubuntu1 [95.0kB]
Fetched 31.0MB in 2min 21s (219kB/s)                                           
Preconfiguring packages ...
(Reading database ... 170128 files and directories currently installed.)
Preparing to replace libcups2 1.4.3-1 (using .../libcups2_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace cups-common 1.4.3-1 (using .../cups-common_1.4.3-1ubuntu1_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.4.3-1 (using .../cups-bsd_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace libcupsimage2 1.4.3-1 (using .../libcupsimage2_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace cups-client 1.4.3-1 (using .../cups-client_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace kdebase-runtime-data 4:4.4.2-0ubuntu4 (using .../kdebase-runtime-data_4%3a4.4.2-0ubuntu4.1_all.deb) ...
Unpacking replacement kdebase-runtime-data ...
Preparing to replace libcupscgi1 1.4.3-1 (using .../libcupscgi1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libcupsdriver1 1.4.3-1 (using .../libcupsdriver1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace libcupsmime1 1.4.3-1 (using .../libcupsmime1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupsppdc1 1.4.3-1 (using .../libcupsppdc1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace libgtkmm-2.4-1c2a 1:2.20.2-1 (using .../libgtkmm-2.4-1c2a_1%3a2.20.3-0ubuntu1_amd64.deb) ...
Unpacking replacement libgtkmm-2.4-1c2a ...
Preparing to replace libsnmp-base 5.4.2.1~dfsg0ubuntu1-0ubuntu2 (using .../libsnmp-base_5.4.2.1~dfsg0ubuntu1-0ubuntu2.1_all.deb) ...
Unpacking replacement libsnmp-base ...
Preparing to replace libsnmp15 5.4.2.1~dfsg0ubuntu1-0ubuntu2 (using .../libsnmp15_5.4.2.1~dfsg0ubuntu1-0ubuntu2.1_amd64.deb) ...
Unpacking replacement libsnmp15 ...
Preparing to replace simple-scan 1.0.2-0ubuntu1 (using .../simple-scan_1.0.3-0ubuntu1_amd64.deb) ...
Unpacking replacement simple-scan ...
Preparing to replace skype 2.1.0.81-1 (using .../skype_2.1.0.81-1ubuntu5_amd64.deb) ...
Unpacking replacement skype ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/Anglonas.desktop: ParsingError in file '/usr/share/applications/Anglonas.desktop', [Desktop Entry]-Header missing
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-support ...
Setting up libcups2 (1.4.3-1ubuntu1) ...

Setting up cups-common (1.4.3-1ubuntu1) ...
Setting up libcupsimage2 (1.4.3-1ubuntu1) ...

Setting up cups-client (1.4.3-1ubuntu1) ...

Setting up cups-bsd (1.4.3-1ubuntu1) ...

Setting up kdebase-runtime-data (4:4.4.2-0ubuntu4.1) ...

Setting up libcupscgi1 (1.4.3-1ubuntu1) ...

Setting up libcupsdriver1 (1.4.3-1ubuntu1) ...

Setting up libcupsmime1 (1.4.3-1ubuntu1) ...

Setting up libcupsppdc1 (1.4.3-1ubuntu1) ...

Setting up libgtkmm-2.4-1c2a (1:2.20.3-0ubuntu1) ...

Setting up libsnmp-base (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1) ...
Setting up libsnmp15 (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1) ...

Setting up simple-scan (1.0.3-0ubuntu1) ...

Setting up skype (2.1.0.81-1ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get install --reinstall ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 30.7kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main ubuntu-minimal 1.197 [30.7kB]
Fetched 30.7kB in 0s (91.8kB/s)   
(Reading database ... 170130 files and directories currently installed.)
Preparing to replace ubuntu-minimal 1.197 (using .../ubuntu-minimal_1.197_amd64.deb) ...
Unpacking replacement ubuntu-minimal ...
Setting up ubuntu-minimal (1.197) ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get install --reinstall ubuntu-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 30.8kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main ubuntu-standard 1.197 [30.8kB]
Fetched 30.8kB in 0s (83.2kB/s)    
(Reading database ... 170130 files and directories currently installed.)
Preparing to replace ubuntu-standard 1.197 (using .../ubuntu-standard_1.197_amd64.deb) ...
Unpacking replacement ubuntu-standard ...
Setting up ubuntu-standard (1.197) ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acpi-support acpid alsa-base alsa-utils anacron apport apport-gtk aptdaemon
  apturl at-spi avahi-daemon bluez bluez-cups brasero brltty brltty-x11
  checkbox checkbox-gtk computer-janitor-gtk consolekit couchdb-bin cups
  cups-driver-gutenprint desktopcouch empathy erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins f-spot foo2zjs
  foomatic-db foomatic-db-engine gbrainy gconf-editor gdebi gdm
  gdm-guest-session ghostscript-cups gksu gnome-about gnome-applets
  gnome-bluetooth gnome-codec-install gnome-control-center gnome-disk-utility
  gnome-keyring gnome-mag gnome-media gnome-orca gnome-panel
  gnome-power-manager gnome-screensaver gnome-session gnome-session-bin
  gnome-settings-daemon gnome-system-tools gnome-user-share gnome-utils
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hplip indicator-applet indicator-applet-session indicator-me
  indicator-session indicator-sound jockey-common jockey-gtk language-selector
  lftp libasound2-plugins libbonoboui2-0 libgail-gnome-module libgdu0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 libgnome2-perl
  libgnome2-vfs-perl libgnome2.24-cil libgnomekbd4 libgnomepanel2.24-cil
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-extra liblpint-bonobo0
  libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0
  libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  libsdl1.2debian libsdl1.2debian-pulseaudio libxklavier16 libxml-twig-perl
  libxml-xpath-perl libxss1 libxtst6 libxvmc1 libxxf86dga1 linux-sound-base
  media-player-info mousetweaks nautilus nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  onboard openoffice.org-base-core openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-writer openprinting-ppds pcmciautils
  plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 pm-utils
  pm-utils-powersave-policy policykit-1 policykit-1-gnome powermgmt-base
  pptp-linux pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python-aptdaemon python-aptdaemon-gtk python-desktopcouch
  python-desktopcouch-records python-gnome2 python-gnomeapplet python-pyatspi
  python-speechd python-uno python-virtkey rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screen-resolution-extra software-center
  software-properties-gtk speech-dispatcher splix system-config-printer-gnome
  system-tools-backends telepathy-salut tomboy totem totem-mozilla
  totem-plugins tsclient ubufox ubuntu-system-service udisks update-manager
  update-notifier upower usb-creator-common usb-creator-gtk vinagre vino
  x-ttcidfont-conf x11-apps x11-session-utils x11-utils x11-xfs-utils
  x11-xkb-utils x11-xserver-utils xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-encodings xfonts-scalable xfonts-utils xinit xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
Suggested packages:
  apmd alsa-oss oss-compat default-mta mail-transport-agent
  gstreamer0.10-fluendo-mp3 cdrdao dvdauthor vcdimager libdvdcss2
  brltty-speechd couchdb cups-ppdc xpdf-korean xpdf-japanese
  xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf gutenprint-doc
  gutenprint-locales erlang-tools erlang erlang-manpages erlang-doc-html
  bug-buddy evolution-dbg evolution-plugins-experimental gnome-pilot-conduits
  evolution-exchange-dbg psutils hannah-foo2zjs tix hplip-cups m2300w
  openprinting-ppds-extra cjet foomatic-db-hpijs foomatic-db-gutenprint
  foomatic-gui uswsusp gok gnome-netstatus-applet deskbar-applet cpufrequtils
  geoclue epiphany-browser menu-xdg hal xscreensaver-data-extra
  xscreensaver-gl-extra rss-glx desktop-base ntp apache2.2-bin
  libapache2-mod-dnssd gwibber-themes kdeprint gtklp xpp hplip-gui hplip-doc
  monodoc-gtk2.0-manual libgnomevfs2-bin libunicode-map8-perl
  libunicode-string-perl xml-twig-tools gnome-app-install samba
  openoffice.org-base openoffice.org-evolution openoffice.org-java-common
  openoffice.org-gcj openoffice.org-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre sun-java5-jre sun-java6-jre java5-runtime jre
  pavumeter paman paprefs python-gnome2-doc python-coherence
  rhythmbox-plugin-coherence speech-dispatcher-festival
  speech-dispatcher-doc-cs speech-dispatcher-flite tasque gromit vnc-viewer
  xnest reiserfsprogs mdadm cryptsetup mesa-utils nickle cairo-5c xfs xserver
  xorg-docs gpointing-device-settings touchfreeze firmware-linux
Recommended packages:
  firefox-gnome-support
The following NEW packages will be installed:
  acpi-support acpid alsa-base alsa-utils anacron apport apport-gtk aptdaemon
  apturl at-spi avahi-daemon bluez bluez-cups brasero brltty brltty-x11
  checkbox checkbox-gtk computer-janitor-gtk consolekit couchdb-bin cups
  cups-driver-gutenprint desktopcouch empathy erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins f-spot foo2zjs
  foomatic-db foomatic-db-engine gbrainy gconf-editor gdebi gdm
  gdm-guest-session ghostscript-cups gksu gnome-about gnome-applets
  gnome-bluetooth gnome-codec-install gnome-control-center gnome-disk-utility
  gnome-keyring gnome-mag gnome-media gnome-orca gnome-panel
  gnome-power-manager gnome-screensaver gnome-session gnome-session-bin
  gnome-settings-daemon gnome-system-tools gnome-user-share gnome-utils
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hplip indicator-applet indicator-applet-session indicator-me
  indicator-session indicator-sound jockey-common jockey-gtk language-selector
  lftp libasound2-plugins libbonoboui2-0 libgail-gnome-module libgdu0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 libgnome2-perl
  libgnome2-vfs-perl libgnome2.24-cil libgnomekbd4 libgnomepanel2.24-cil
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-extra liblpint-bonobo0
  libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0
  libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  libsdl1.2debian libsdl1.2debian-pulseaudio libxklavier16 libxml-twig-perl
  libxml-xpath-perl libxss1 libxtst6 libxvmc1 libxxf86dga1 linux-sound-base
  media-player-info mousetweaks nautilus nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  onboard openoffice.org-base-core openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-writer openprinting-ppds pcmciautils
  plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 pm-utils
  pm-utils-powersave-policy policykit-1 policykit-1-gnome powermgmt-base
  pptp-linux pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python-aptdaemon python-aptdaemon-gtk python-desktopcouch
  python-desktopcouch-records python-gnome2 python-gnomeapplet python-pyatspi
  python-speechd python-uno python-virtkey rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screen-resolution-extra software-center
  software-properties-gtk speech-dispatcher splix system-config-printer-gnome
  system-tools-backends telepathy-salut tomboy totem totem-mozilla
  totem-plugins tsclient ubufox ubuntu-desktop ubuntu-system-service udisks
  update-manager update-notifier upower usb-creator-common usb-creator-gtk
  vinagre vino x-ttcidfont-conf x11-apps x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xinit xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 251 newly installed, 0 to remove and 0 not upgraded.
Need to get 131MB of archives.
After this operation, 577MB of additional disk space will be used.
Do you want to continue [Y/n]? y


///////////////// somewhere after reinstall ubuntu-desktop i think

Selecting previously deselected package rhythmbox-ubuntuone-music-store.
Unpacking rhythmbox-ubuntuone-music-store (from .../rhythmbox-ubuntuone-music-store_0.0.9-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/Anglonas.desktop: ParsingError in file '/usr/share/applications/Anglonas.desktop', [Desktop Entry]-Header missing
Processing triggers for install-info ...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for fontconfig ...
Processing triggers for python-support ...
Processing triggers for python-central ...
Setting up cups (1.4.3-1ubuntu1) ...
 * Starting Common Unix Printing System: cupsd                                  FATAL: Could not load /lib/modules/2.6.32-21-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.32-21-generic/modules.dep: No such file or directory
                                                                         [ OK ]

Setting up libgnomevfs2-0 (1:2.24.2-1ubuntu2) ...

Setting up udisks (1.0.1-1build1) ...

(udisks:9104): udisks-WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Setting up libgdu0 (2.30.1-1) ...

Setting up consolekit (0.4.1-3ubuntu1) ...
Setting up policykit-1 (0.96-2) ...

Setting up policykit-1-gnome (0.96-2ubuntu2) ...
Setting up gvfs (1.6.1-0ubuntu1build1) ...
Setting up libgnome2-0 (2.30.0-0ubuntu1) ...

Setting up libbonoboui2-0 (2.24.3-0ubuntu1) ...

Setting up libpanel-applet2-0 (1:2.30.0-0ubuntu1) ...

Setting up x11-xkb-utils (7.5+1) ...
Setting up libxklavier16 (5.0-0ubuntu1) ...

Setting up libgnomekbd4 (2.30.0-0ubuntu2) ...

Setting up libxss1 (1:1.2.0-2) ...

Setting up libpulse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...

Setting up libpulse-mainloop-glib0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...

Setting up gnome-settings-daemon (2.30.1-0ubuntu1) ...

Setting up ubuntu-system-service (0.1.20) ...

Setting up libgnomeui-0 (2.24.3-1) ...

Setting up python-gnome2 (2.28.0-1ubuntu1) ...

Setting up gnome-about (1:2.30.0-0ubuntu1) ...
Setting up hplip (3.10.2-2ubuntu2) ...
Creating/updating hplip user account...

Setting up openoffice.org-emailmerge (1:3.2.0-7ubuntu4) ...
stat: cannot read file system information for `/home/ubuntu': No such file or directory
Copying: mailmerge.py
Enabling: mailmerge.py

unopkg done.

Setting up x11-apps (7.5+1ubuntu2) ...

Setting up x11-session-utils (7.5+1) ...
Setting up libxxf86dga1 (2:1.1.1-2) ...

Setting up x11-utils (7.5+3) ...

Setting up x11-xfs-utils (7.4+1build2) ...
Setting up x11-xserver-utils (7.5+1ubuntu2) ...

Setting up powermgmt-base (1.31) ...

Setting up acpid (1.0.10-5ubuntu2.1) ...

Setting up pm-utils (1.3.0-1ubuntu2) ...
Setting up acpi-support (0.136) ...
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

Setting up linux-sound-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-utils (1.0.22-0ubuntu5) ...

Setting up anacron (2.3-13.1ubuntu11) ...

Setting up apport (1.13.3-0ubuntu2) ...

Setting up gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) ...

Setting up gksu (2.0.2-2ubuntu2) ...

Setting up software-properties-gtk (0.75.10) ...

Setting up at-spi (1.30.0-0ubuntu2) ...

Setting up avahi-daemon (0.6.25-1ubuntu6) ...

Setting up bluez (4.60-0ubuntu8) ...

Setting up bluez-cups (4.60-0ubuntu8) ...
Setting up brasero (2.30.0-0ubuntu1) ...

Setting up checkbox (0.9.1) ...

Setting up computer-janitor-gtk (1.14.1-0ubuntu2) ...
Setting up erlang-base (1:13.b.3-dfsg-2ubuntu2) ...
Searching for services which depend on erlang and should be started...none found.

Setting up erlang-crypto (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-mnesia (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-runtime-tools (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-public-key (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-ssl (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-inets (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-xmerl (1:13.b.3-dfsg-2ubuntu2) ...
Setting up couchdb-bin (0.10.0-1ubuntu2) ...

Setting up ghostscript-cups (8.71.dfsg.1-0ubuntu5.1) ...

Setting up cups-driver-gutenprint (5.2.5-0ubuntu1) ...
Did not update any PPD files
 * Reloading Common Unix Printing System: cupsd                          [ OK ] 
Backend smb used by printer HP-Deskjet-3840 is current.
Backend smb used by printer HP-Officejet-g85 is current.
Backend smb used by printer HP-On-Linux is current.
Backend usb used by printer OfficeJet-G85 is current.

Setting up empathy (2.30.1-0ubuntu1) ...

Setting up erlang-syntax-tools (1:13.b.3-dfsg-2ubuntu2) ...
Setting up libgnome-pilot2 (2.0.17-0ubuntu5) ...

Setting up liblpint-bonobo0 (0.1.35) ...

Setting up evolution (2.28.3-0ubuntu9) ...

Setting up evolution-exchange (2.28.3-0ubuntu1) ...

Setting up evolution-plugins (2.28.3-0ubuntu9) ...
Setting up libgnome-vfs2.0-cil (2.24.1-6ubuntu1) ...
* Installing 6 assemblies from libgnome-vfs2.0-cil into Mono

Setting up libgnome2.24-cil (2.24.1-6ubuntu1) ...
* Installing 2 assemblies from libgnome2.24-cil into Mono

Setting up gvfs-bin (1.6.1-0ubuntu1build1) ...
Setting up f-spot (0.6.1.5-2ubuntu6) ...

Setting up foo2zjs (20100210-0ubuntu4) ...

Setting up gbrainy (1.41-1ubuntu1) ...

Setting up gconf-editor (2.30.0-0ubuntu1) ...

Setting up gdebi (0.6.0ubuntu1) ...

Setting up gnome-session-bin (2.30.0-0ubuntu1) ...

Setting up gdm (2.30.0-0ubuntu5) ...

Setting up gdm-guest-session (0.15) ...
Setting up gnome-bluetooth (2.30.0-0ubuntu3) ...

Setting up gnome-codec-install (0.4.2ubuntu2) ...
update-alternatives: using /usr/bin/gnome-codec-install to provide /usr/bin/gstreamer-codec-install (gstreamer-codec-install) in auto mode.

Setting up gnome-disk-utility (2.30.1-1) ...
Setting up python-gnomeapplet (2.30.0-0ubuntu1) ...

Setting up gnome-mag (1:0.16.1-0ubuntu1) ...
Setting up gstreamer0.10-pulseaudio (0.10.21-1ubuntu2) ...
Setting up gnome-media (2.30.0-0ubuntu1) ...

Setting up speech-dispatcher (0.6.8~unofficial~rc2-0ubuntu3) ...
 * Speech-dispatcher configured for user sessions

Setting up python-speechd (0.6.8~unofficial~rc2-0ubuntu3) ...

Setting up python-pyatspi (1.30.0-0ubuntu2) ...

Setting up upower (0.9.1-1) ...

(upower:10997): libupower-glib-WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Setting up gnome-power-manager (2.30.0-0ubuntu1) ...

Setting up gnome-screensaver (2.30.0-0ubuntu2) ...

Setting up nautilus (1:2.30.1-0ubuntu1) ...

Setting up gnome-user-share (2.30.0-0ubuntu2) ...

Setting up gnome-utils (2.30.0-0ubuntu1) ...

Setting up gvfs-backends (1.6.1-0ubuntu1build1) ...

Setting up gvfs-fuse (1.6.1-0ubuntu1build1) ...
Setting up indicator-session (0.2.8-0ubuntu2) ...

Setting up jockey-common (0.5.8-0ubuntu8.1) ...

Setting up language-selector (0.5.7) ...

Setting up lftp (4.0.2-1) ...

Setting up libasound2-plugins (1.0.22-0ubuntu6) ...
Setting up libgail-gnome-module (1.20.1-2) ...
Setting up libgnome2-vfs-perl (1.081-1build1) ...
Setting up libgnome2-perl (1.042-2build1) ...
Setting up libgnomepanel2.24-cil (2.26.0-2ubuntu1) ...
* Installing 1 assembly from libgnomepanel2.24-cil into Mono

Setting up libgnomevfs2-extra (1:2.24.2-1ubuntu2) ...
Setting up libxml-twig-perl (1:3.32-3ubuntu1) ...
Setting up libnet-dbus-perl (0.33.6-1build3) ...
Setting up libnss-mdns (0.10-3ubuntu4) ...

Setting up system-tools-backends (2.9.4-0ubuntu1) ...
Setting up liboobs-1-4 (2.30.0-0ubuntu1) ...

Setting up libpolkit-gtk-1-0 (0.96-2ubuntu2) ...

Setting up libpulse-browse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...

Setting up libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1) ...

Setting up libsdl1.2debian (1.2.14-4ubuntu1) ...
Setting up libxml-xpath-perl (1.13-7) ...
Setting up libxvmc1 (2:1.0.5-1ubuntu1) ...

Setting up media-player-info (6-1) ...
Setting up mousetweaks (2.30.0-0ubuntu1) ...

Setting up nautilus-share (0.7.2-12build1) ...
Setting up network-manager (0.8-0ubuntu3) ...

Setting up network-manager-gnome (0.8-0ubuntu3) ...

Setting up pptp-linux (1.7.2-4) ...
Setting up network-manager-pptp (0.8-0ubuntu3) ...

Setting up network-manager-pptp-gnome (0.8-0ubuntu3) ...

Setting up python-virtkey (0.50ubuntu3) ...

Setting up openoffice.org-base-core (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-calc (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-draw (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-gtk (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-gnome (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-writer (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-help-en-us (1:3.2.0-7ubuntu1) ...

Setting up openoffice.org-impress (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-math (1:3.2.0-7ubuntu4) ...

Setting up openprinting-ppds (20100216-0ubuntu3) ...

Setting up pcmciautils (014-4ubuntu4) ...

Setting up plymouth-label (0.8.2-2ubuntu2) ...
Setting up plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2) ...
update-alternatives: using /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth to provide /lib/plymouth/themes/default.plymouth (default.plymouth) in auto mode.
update-initramfs: deferring update (trigger activated)

Setting up plymouth-x11 (0.8.2-2ubuntu2) ...
Setting up pm-utils-powersave-policy (0.3) ...
Setting up pulseaudio-utils (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pulseaudio (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
 * PulseAudio configured for per-user sessions

Setting up pulseaudio-esound-compat (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pulseaudio-module-gconf (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pulseaudio-module-x11 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pxljr (1.1-0ubuntu7) ...

Setting up rhythmbox (0.12.8-0ubuntu5) ...

Setting up rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu5) ...
Setting up rhythmbox-plugins (0.12.8-0ubuntu5) ...

Setting up screen-resolution-extra (0.13) ...

Setting up python-aptdaemon (0.11+bzr345-0ubuntu4) ...

Setting up splix (2.0.0-2ubuntu3) ...

Setting up system-config-printer-gnome (1.2.0+20100408-0ubuntu5.2) ...

Setting up telepathy-salut (0.3.11-1) ...
Setting up tomboy (1.2.1-0ubuntu1) ...

Setting up totem (2.30.2-0ubuntu1) ...

Setting up totem-mozilla (2.30.2-0ubuntu1) ...
Setting up totem-plugins (2.30.2-0ubuntu1) ...

Setting up tsclient (0.150-3ubuntu1) ...

Setting up gnome-system-tools (2.30.0-0ubuntu2) ...

Setting up update-manager (1:0.134.8) ...

Setting up xfonts-encodings (1:1.0.3-1) ...
Setting up xfonts-utils (1:7.5+2) ...

Setting up x-ttcidfont-conf (32) ...
Updating font configuration of x-ttcidfont-conf...
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Updating category truetype..
Updating category cid..
Updating category cmap..

Setting up xserver-common (2:1.7.6-2ubuntu7) ...
Setting up xfonts-base (1:1.0.1) ...

Setting up xfonts-100dpi (1:1.0.1) ...

Setting up xfonts-75dpi (1:1.0.1) ...

Setting up xinit (1.2.0-1) ...
Setting up usb-creator-common (0.2.22) ...

Setting up vinagre (2.30.1-0ubuntu1) ...

Setting up vino (2.28.2-0ubuntu2) ...

Setting up xfonts-scalable (1:1.0.1-1) ...

Setting up brltty (4.1-2ubuntu6) ...
update-initramfs: deferring update (trigger activated)

Setting up brltty-x11 (4.1-2ubuntu6) ...
Setting up evolution-indicator (0.2.8-0ubuntu1) ...

Setting up indicator-sound (0.2.3-0ubuntu1) ...

Setting up pulseaudio-module-bluetooth (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Processing triggers for python-central ...
Setting up gnome-control-center (1:2.30.1-0ubuntu1) ...

Setting up gnome-panel (1:2.30.0-0ubuntu1) ...

Setting up gnome-applets (2.30.0-0ubuntu2) ...

Setting up apport-gtk (1.13.3-0ubuntu2) ...
Setting up apturl (0.4.1ubuntu4) ...

Setting up checkbox-gtk (0.9.1) ...

Setting up gnome-orca (2.30.0-0ubuntu3) ...

Setting up gnome-session (2.30.0-0ubuntu1) ...
update-alternatives: using /usr/bin/gnome-session to provide /usr/bin/x-session-manager (x-session-manager) in auto mode.

Setting up indicator-applet (0.3.7-0ubuntu1) ...
Setting up indicator-applet-session (0.3.7-0ubuntu1) ...
Setting up indicator-me (0.2.6-0ubuntu1) ...
Setting up jockey-gtk (0.5.8-0ubuntu8.1) ...
Setting up onboard (0.93.0-0ubuntu4) ...

Setting up python-aptdaemon-gtk (0.11+bzr345-0ubuntu4) ...

Setting up aptdaemon (0.11+bzr345-0ubuntu4) ...
Setting up update-notifier (0.99.3) ...

Setting up usb-creator-gtk (0.2.22) ...

Processing triggers for python-central ...
Setting up software-center (2.0.4) ...
WARNING:root:Failed to setup dbus (ignoring)

Setting up ubufox (0.9~rc2-0ubuntu2) ...

Setting up rhythmbox-ubuntuone-music-store (0.0.9-0ubuntu1) ...

Processing triggers for python-central ...
Setting up xserver-xorg-core (2:1.7.6-2ubuntu7) ...

Setting up foomatic-db-engine (4.0.4-0ubuntu1) ...

Setting up foomatic-db (20100216-0ubuntu3) ...

Setting up desktopcouch (0.6.4-0ubuntu3) ...
Setting up python-desktopcouch (0.6.4-0ubuntu3) ...

Setting up evolution-couchdb (0.4.5-0ubuntu1) ...
Setting up xserver-xorg-video-apm (1:1.2.2-1) ...
Setting up xserver-xorg-video-ark (1:0.7.2-1) ...
Setting up xserver-xorg-video-r128 (6.8.1-2ubuntu1) ...
Setting up xserver-xorg-video-mach64 (6.8.2-2) ...
Setting up xserver-xorg-video-radeon (1:6.13.0-1ubuntu5) ...

Setting up xserver-xorg-video-ati (1:6.13.0-1ubuntu5) ...
Setting up xserver-xorg-video-chips (1:1.2.2-1) ...
Setting up xserver-xorg-video-cirrus (1:1.3.2-1ubuntu1) ...
Setting up xserver-xorg-video-fbdev (1:0.4.1-1ubuntu1) ...
Setting up xserver-xorg-video-i128 (1:1.3.3-1) ...
Setting up xserver-xorg-video-intel (2:2.9.1-3ubuntu5) ...

Setting up xserver-xorg-video-mga (1:1.4.11.dfsg-2ubuntu1) ...
Setting up xserver-xorg-video-neomagic (1:1.2.4-2) ...
Setting up xserver-xorg-video-nouveau (1:0.0.15+git20100219+9b4118d-0ubuntu5) ...
Setting up xserver-xorg-video-nv (1:2.1.15-1ubuntu3) ...
Setting up xserver-xorg-video-rendition (1:4.2.3-1) ...
Setting up xserver-xorg-video-s3 (1:0.6.3-1) ...
Setting up xserver-xorg-video-s3virge (1:1.10.4-1) ...
Setting up xserver-xorg-video-savage (1:2.3.1-1ubuntu1) ...
Setting up xserver-xorg-video-siliconmotion (1:1.7.3-1) ...
Setting up xserver-xorg-video-sis (1:0.10.2-2) ...
Setting up xserver-xorg-video-sisusb (1:0.9.3-1) ...
Setting up xserver-xorg-video-tdfx (1:1.4.3-1) ...
Setting up xserver-xorg-video-trident (1:1.3.3-1) ...
Setting up xserver-xorg-video-tseng (1:1.2.3-1) ...
Setting up xserver-xorg-video-vesa (1:2.3.0-1ubuntu1) ...
Setting up xserver-xorg-video-openchrome (1:0.2.904+svn827-1) ...

Setting up xserver-xorg-video-voodoo (1:1.2.3-1) ...
Setting up xserver-xorg-video-v4l (1:0.2.0-4) ...
Setting up xserver-xorg-video-vmware (1:10.16.9-1) ...
Setting up xserver-xorg-video-all (1:7.5+5ubuntu1) ...
Setting up xserver-xorg-input-evdev (1:2.3.2-5ubuntu1) ...
Setting up xserver-xorg-input-synaptics (1.2.2-1ubuntu4) ...

Setting up xserver-xorg-input-mouse (1:1.5.0-1) ...
Setting up xserver-xorg-input-vmmouse (1:12.6.5-4ubuntu2) ...

Setting up xserver-xorg-input-wacom (1:0.10.5-0ubuntu4) ...

Setting up xserver-xorg-input-all (1:7.5+5ubuntu1) ...
Setting up xserver-xorg (1:7.5+5ubuntu1) ...

Setting up xorg (1:7.5+5ubuntu1) ...
Setting up ubuntu-desktop (1.197) ...
Processing triggers for python-central ...
Setting up python-desktopcouch-records (0.6.4-0ubuntu3) ...

Processing triggers for python-central ...
Setting up gwibber-service (2.31.1~bzr743-0ubuntu1~daily1) ...

Processing triggers for python-central ...
Setting up gwibber (2.31.1~bzr743-0ubuntu1~daily1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
Processing triggers for python-central ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "force-reload" failed.
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

 * Starting AppArmor profiles                                                    * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "start" failed.
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "reload" failed.
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support                umount: /proc/sys/fs/binfmt_misc: not mounted
update-binfmts: warning: Couldn't unmount the binfmt_misc filesystem from
/proc/sys/fs/binfmt_misc. 
                                                                         [ OK ]
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


```

So what if I run ubuntu install from the live cd? If i choose my old root partition will it delete it's contents? So basically what I'm planning to do is:
1) I'll create a new partition and move the files from my current inactive root partition to that partition?
2) I'll install lucid again to that old root partition. Now the question is will it remove my old files in root or not? And if it will, should everything work well again, with old settings and apps installed?

I assume I don't need to backup my /home since it's on another partition? So a new installation shouldn't touch it, should it?

Are my plans OK, can I try that? Please suggest me something better if you have any ideas.

And thank you very much for helping me :)

---

### Post by gazmend on 2012-03-25
> **arcelivez said:**
> OK, so I tried changing the contents of sources.list with your given ones, But I believe this still doesn't install the kernel again. :/ 
Here's the terminal
```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# ls
apps  boot   dev  home    lib32  lost+found  mnt    proc  sbin     srv  tmp  var
bin   cdrom  etc  lib    lib64  media       opt    root  selinux  sys  usr
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# cd /
root@ubuntu:/# ls
apps  boot   dev  home    lib32  lost+found  mnt    proc  sbin     srv  tmp  var
bin   cdrom  etc  lib    lib64  media       opt    root  selinux  sys  usr
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# more sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid mai
n restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted unive
rse multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted u
niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get clean
root@ubuntu:/etc/apt# apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/awn-testing/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:2 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Get:3 http://dl.google.com stable Release [2,544B]                             
Hit http://deb.opera.com stable Release                                        
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid Release                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release 
Get:4 http://ppa.launchpad.net lucid Release [57.3kB]                
Hit http://ppa.launchpad.net lucid Release                                    
Ign http://ppa.launchpad.net lucid Release     
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:5 http://dl.google.com stable/main Packages [1,051B]                       
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 4,092B in 0s (4,782B/s)
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# dpkg --configure -a
Processing triggers for python-central ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  cups-bsd cups-client cups-common kdebase-runtime-data libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libgtkmm-2.4-1c2a
  libsnmp-base libsnmp15 simple-scan skype
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.0MB of archives.
After this operation, 521kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner skype 2.1.0.81-1ubuntu5 [20.2MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcups2 1.4.3-1ubuntu1 [223kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main cups-common 1.4.3-1ubuntu1 [1,463kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main cups-bsd 1.4.3-1ubuntu1 [44.8kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsimage2 1.4.3-1ubuntu1 [53.1kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main cups-client 1.4.3-1ubuntu1 [141kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdebase-runtime-data 4:4.4.2-0ubuntu4.1 [4,014kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupscgi1 1.4.3-1ubuntu1 [31.5kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsdriver1 1.4.3-1ubuntu1 [22.1kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsmime1 1.4.3-1ubuntu1 [15.4kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsppdc1 1.4.3-1ubuntu1 [60.0kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtkmm-2.4-1c2a 1:2.20.3-0ubuntu1 [1,190kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsnmp-base 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 [1,335kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libsnmp15 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 [2,178kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main simple-scan 1.0.3-0ubuntu1 [95.0kB]
Fetched 31.0MB in 2min 21s (219kB/s)                                           
Preconfiguring packages ...
(Reading database ... 170128 files and directories currently installed.)
Preparing to replace libcups2 1.4.3-1 (using .../libcups2_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcups2 ...
Preparing to replace cups-common 1.4.3-1 (using .../cups-common_1.4.3-1ubuntu1_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.4.3-1 (using .../cups-bsd_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace libcupsimage2 1.4.3-1 (using .../libcupsimage2_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace cups-client 1.4.3-1 (using .../cups-client_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace kdebase-runtime-data 4:4.4.2-0ubuntu4 (using .../kdebase-runtime-data_4%3a4.4.2-0ubuntu4.1_all.deb) ...
Unpacking replacement kdebase-runtime-data ...
Preparing to replace libcupscgi1 1.4.3-1 (using .../libcupscgi1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libcupsdriver1 1.4.3-1 (using .../libcupsdriver1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace libcupsmime1 1.4.3-1 (using .../libcupsmime1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupsppdc1 1.4.3-1 (using .../libcupsppdc1_1.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace libgtkmm-2.4-1c2a 1:2.20.2-1 (using .../libgtkmm-2.4-1c2a_1%3a2.20.3-0ubuntu1_amd64.deb) ...
Unpacking replacement libgtkmm-2.4-1c2a ...
Preparing to replace libsnmp-base 5.4.2.1~dfsg0ubuntu1-0ubuntu2 (using .../libsnmp-base_5.4.2.1~dfsg0ubuntu1-0ubuntu2.1_all.deb) ...
Unpacking replacement libsnmp-base ...
Preparing to replace libsnmp15 5.4.2.1~dfsg0ubuntu1-0ubuntu2 (using .../libsnmp15_5.4.2.1~dfsg0ubuntu1-0ubuntu2.1_amd64.deb) ...
Unpacking replacement libsnmp15 ...
Preparing to replace simple-scan 1.0.2-0ubuntu1 (using .../simple-scan_1.0.3-0ubuntu1_amd64.deb) ...
Unpacking replacement simple-scan ...
Preparing to replace skype 2.1.0.81-1 (using .../skype_2.1.0.81-1ubuntu5_amd64.deb) ...
Unpacking replacement skype ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/Anglonas.desktop: ParsingError in file '/usr/share/applications/Anglonas.desktop', [Desktop Entry]-Header missing
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for python-support ...
Setting up libcups2 (1.4.3-1ubuntu1) ...

Setting up cups-common (1.4.3-1ubuntu1) ...
Setting up libcupsimage2 (1.4.3-1ubuntu1) ...

Setting up cups-client (1.4.3-1ubuntu1) ...

Setting up cups-bsd (1.4.3-1ubuntu1) ...

Setting up kdebase-runtime-data (4:4.4.2-0ubuntu4.1) ...

Setting up libcupscgi1 (1.4.3-1ubuntu1) ...

Setting up libcupsdriver1 (1.4.3-1ubuntu1) ...

Setting up libcupsmime1 (1.4.3-1ubuntu1) ...

Setting up libcupsppdc1 (1.4.3-1ubuntu1) ...

Setting up libgtkmm-2.4-1c2a (1:2.20.3-0ubuntu1) ...

Setting up libsnmp-base (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1) ...
Setting up libsnmp15 (5.4.2.1~dfsg0ubuntu1-0ubuntu2.1) ...

Setting up simple-scan (1.0.3-0ubuntu1) ...

Setting up skype (2.1.0.81-1ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get install --reinstall ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 30.7kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main ubuntu-minimal 1.197 [30.7kB]
Fetched 30.7kB in 0s (91.8kB/s)   
(Reading database ... 170130 files and directories currently installed.)
Preparing to replace ubuntu-minimal 1.197 (using .../ubuntu-minimal_1.197_amd64.deb) ...
Unpacking replacement ubuntu-minimal ...
Setting up ubuntu-minimal (1.197) ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get install --reinstall ubuntu-standard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 30.8kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main ubuntu-standard 1.197 [30.8kB]
Fetched 30.8kB in 0s (83.2kB/s)    
(Reading database ... 170130 files and directories currently installed.)
Preparing to replace ubuntu-standard 1.197 (using .../ubuntu-standard_1.197_amd64.deb) ...
Unpacking replacement ubuntu-standard ...
Setting up ubuntu-standard (1.197) ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2 python-packagekit libpackagekit-qt-12 python-evolution
  libemail-mime-encodings-perl libqca2 python-bluez python-gnomedesktop
  bzrtools libpolkit-qt-1-0 libmono0 python-awn-extras-trunk libpthread-stubs0
  remuco-base libsox-fmt-base libqtscript4-network libgsasl7 python-awn-trunk
  libtaglib2.0-cil libdesktop-agnostic-fdo-glib
  libplasma-geolocation-interface4 libboost-signals1.40.0 libquicktime1
  openoffice.org-l10n-en-gb libgmime-2.0-2a libcrypt-ssleay-perl
  libqtscript4-gui libboost-program-options1.40.0 libxcb-xv0 libsox-fmt-alsa
  libavahi1.0-cil banshee-extensions-common libavfilter0
  linux-headers-2.6.32-21-generic oxygen-icon-theme m4 autoconf libchm1
  libiso9660-7 libhsqldb-java podsleuth libcddb2 java-wrappers
  libcommons-cli-java libavdevice52 libtag-extras1 fortune-mod libexiv2-6
  mysql-server-core-5.1 libdesktop-agnostic-vfs-gio libqtscript4-sql
  x11proto-kb-dev libdvbpsi5 grub-pc libdesktop-agnostic0
  libdesktop-agnostic-cfg-gconf libqtscript4-xml libqt4-dbg libakonadiprivate1
  libsolidcontrolifaces4 libsexy2 libcrypt-simple-perl libbabl-0.0-0
  libsoprano4 python-paramiko librecode0 akonadi-server libvlc2 gettext
  libawn1-trunk python-qt4 x11proto-input-dev python-desktop-agnostic
  libclucene0ldbl libxml-simple-perl shared-desktop-ontologies python-sip
  linux-headers-2.6.32-21 diff vlc-nox openshot-doc bzr cvs amarok-utils
  virtuoso-nepomuk libmikmod2 libqimageblitz4 libdrm-dev libupnp3
  mysql-client-core-5.1 libmono-zeroconf1.0-cil ttf-symbol-replacement
  libmailutils2 qt4-qmake kdepimlibs-data libmatroska0 python-gtkmozembed
  libxcb-keysyms1 libnotify0.4-cil libwebkit1.1-cil amarok-common libuser1
  libxine1-console libswt-cairo-gtk-3.5-jni libdevmapper-event1.02.1
  python-chardet python-rsvg soprano-daemon wine1.2-gecko libservlet2.5-java
  cabextract libntlm0 python-utidylib python-configobj os-prober exim4-config
  libkephal4 libgdata1.4-cil libgtk2-sexy-perl automake libgimp2.0 ksysguardd
  libc6-dbg libpackagekit-glib2-12 libattica0 fortunes-min
  libcrypt-blowfish-perl libstreams0 libcommons-lang-java vlc-data exiv2
  kdelibs5-data libqtscript4-uitools libtar python-gdata mktemp winbind
  grub-common libboo2.0.9-cil liblastfm0 python-libuser autotools-dev libsox1a
  libmlt-data libsexymm2 libxcb-shape0 libgmime2.2a-cil libssh-4 gimp-data
  libqtscript4-core libxcb-shm0 libvlccore2 kdebase-runtime-data libvcdinfo0
  libebml0 libiodbc2 liblog4j1.2-java python-feedparser pingus-data
  python-dateutil x11proto-core-dev keyutils libxdmcp-dev libtidy-0.99-0
  libpthread-stubs0-dev libgtk2-trayicon-perl qt4-designer libstreamanalyzer0
  libfaac0 mono-gmcs libswt-mozilla-gtk-3.5-jni packagekit-backend-apt
  python-gweather
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acpi-support acpid alsa-base alsa-utils anacron apport apport-gtk aptdaemon
  apturl at-spi avahi-daemon bluez bluez-cups brasero brltty brltty-x11
  checkbox checkbox-gtk computer-janitor-gtk consolekit couchdb-bin cups
  cups-driver-gutenprint desktopcouch empathy erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins f-spot foo2zjs
  foomatic-db foomatic-db-engine gbrainy gconf-editor gdebi gdm
  gdm-guest-session ghostscript-cups gksu gnome-about gnome-applets
  gnome-bluetooth gnome-codec-install gnome-control-center gnome-disk-utility
  gnome-keyring gnome-mag gnome-media gnome-orca gnome-panel
  gnome-power-manager gnome-screensaver gnome-session gnome-session-bin
  gnome-settings-daemon gnome-system-tools gnome-user-share gnome-utils
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hplip indicator-applet indicator-applet-session indicator-me
  indicator-session indicator-sound jockey-common jockey-gtk language-selector
  lftp libasound2-plugins libbonoboui2-0 libgail-gnome-module libgdu0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 libgnome2-perl
  libgnome2-vfs-perl libgnome2.24-cil libgnomekbd4 libgnomepanel2.24-cil
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-extra liblpint-bonobo0
  libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0
  libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  libsdl1.2debian libsdl1.2debian-pulseaudio libxklavier16 libxml-twig-perl
  libxml-xpath-perl libxss1 libxtst6 libxvmc1 libxxf86dga1 linux-sound-base
  media-player-info mousetweaks nautilus nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  onboard openoffice.org-base-core openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-writer openprinting-ppds pcmciautils
  plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 pm-utils
  pm-utils-powersave-policy policykit-1 policykit-1-gnome powermgmt-base
  pptp-linux pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python-aptdaemon python-aptdaemon-gtk python-desktopcouch
  python-desktopcouch-records python-gnome2 python-gnomeapplet python-pyatspi
  python-speechd python-uno python-virtkey rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screen-resolution-extra software-center
  software-properties-gtk speech-dispatcher splix system-config-printer-gnome
  system-tools-backends telepathy-salut tomboy totem totem-mozilla
  totem-plugins tsclient ubufox ubuntu-system-service udisks update-manager
  update-notifier upower usb-creator-common usb-creator-gtk vinagre vino
  x-ttcidfont-conf x11-apps x11-session-utils x11-utils x11-xfs-utils
  x11-xkb-utils x11-xserver-utils xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-encodings xfonts-scalable xfonts-utils xinit xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
Suggested packages:
  apmd alsa-oss oss-compat default-mta mail-transport-agent
  gstreamer0.10-fluendo-mp3 cdrdao dvdauthor vcdimager libdvdcss2
  brltty-speechd couchdb cups-ppdc xpdf-korean xpdf-japanese
  xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf gutenprint-doc
  gutenprint-locales erlang-tools erlang erlang-manpages erlang-doc-html
  bug-buddy evolution-dbg evolution-plugins-experimental gnome-pilot-conduits
  evolution-exchange-dbg psutils hannah-foo2zjs tix hplip-cups m2300w
  openprinting-ppds-extra cjet foomatic-db-hpijs foomatic-db-gutenprint
  foomatic-gui uswsusp gok gnome-netstatus-applet deskbar-applet cpufrequtils
  geoclue epiphany-browser menu-xdg hal xscreensaver-data-extra
  xscreensaver-gl-extra rss-glx desktop-base ntp apache2.2-bin
  libapache2-mod-dnssd gwibber-themes kdeprint gtklp xpp hplip-gui hplip-doc
  monodoc-gtk2.0-manual libgnomevfs2-bin libunicode-map8-perl
  libunicode-string-perl xml-twig-tools gnome-app-install samba
  openoffice.org-base openoffice.org-evolution openoffice.org-java-common
  openoffice.org-gcj openoffice.org-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre sun-java5-jre sun-java6-jre java5-runtime jre
  pavumeter paman paprefs python-gnome2-doc python-coherence
  rhythmbox-plugin-coherence speech-dispatcher-festival
  speech-dispatcher-doc-cs speech-dispatcher-flite tasque gromit vnc-viewer
  xnest reiserfsprogs mdadm cryptsetup mesa-utils nickle cairo-5c xfs xserver
  xorg-docs gpointing-device-settings touchfreeze firmware-linux
Recommended packages:
  firefox-gnome-support
The following NEW packages will be installed:
  acpi-support acpid alsa-base alsa-utils anacron apport apport-gtk aptdaemon
  apturl at-spi avahi-daemon bluez bluez-cups brasero brltty brltty-x11
  checkbox checkbox-gtk computer-janitor-gtk consolekit couchdb-bin cups
  cups-driver-gutenprint desktopcouch empathy erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins f-spot foo2zjs
  foomatic-db foomatic-db-engine gbrainy gconf-editor gdebi gdm
  gdm-guest-session ghostscript-cups gksu gnome-about gnome-applets
  gnome-bluetooth gnome-codec-install gnome-control-center gnome-disk-utility
  gnome-keyring gnome-mag gnome-media gnome-orca gnome-panel
  gnome-power-manager gnome-screensaver gnome-session gnome-session-bin
  gnome-settings-daemon gnome-system-tools gnome-user-share gnome-utils
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hplip indicator-applet indicator-applet-session indicator-me
  indicator-session indicator-sound jockey-common jockey-gtk language-selector
  lftp libasound2-plugins libbonoboui2-0 libgail-gnome-module libgdu0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome2-0 libgnome2-perl
  libgnome2-vfs-perl libgnome2.24-cil libgnomekbd4 libgnomepanel2.24-cil
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-extra liblpint-bonobo0
  libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0
  libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  libsdl1.2debian libsdl1.2debian-pulseaudio libxklavier16 libxml-twig-perl
  libxml-xpath-perl libxss1 libxtst6 libxvmc1 libxxf86dga1 linux-sound-base
  media-player-info mousetweaks nautilus nautilus-share network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  onboard openoffice.org-base-core openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-math openoffice.org-writer openprinting-ppds pcmciautils
  plymouth-label plymouth-theme-ubuntu-logo plymouth-x11 pm-utils
  pm-utils-powersave-policy policykit-1 policykit-1-gnome powermgmt-base
  pptp-linux pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
  python-aptdaemon python-aptdaemon-gtk python-desktopcouch
  python-desktopcouch-records python-gnome2 python-gnomeapplet python-pyatspi
  python-speechd python-uno python-virtkey rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screen-resolution-extra software-center
  software-properties-gtk speech-dispatcher splix system-config-printer-gnome
  system-tools-backends telepathy-salut tomboy totem totem-mozilla
  totem-plugins tsclient ubufox ubuntu-desktop ubuntu-system-service udisks
  update-manager update-notifier upower usb-creator-common usb-creator-gtk
  vinagre vino x-ttcidfont-conf x11-apps x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xinit xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 251 newly installed, 0 to remove and 0 not upgraded.
Need to get 131MB of archives.
After this operation, 577MB of additional disk space will be used.
Do you want to continue [Y/n]? y


///////////////// somewhere after reinstall ubuntu-desktop i think

Selecting previously deselected package rhythmbox-ubuntuone-music-store.
Unpacking rhythmbox-ubuntuone-music-store (from .../rhythmbox-ubuntuone-music-store_0.0.9-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/Anglonas.desktop: ParsingError in file '/usr/share/applications/Anglonas.desktop', [Desktop Entry]-Header missing
Processing triggers for install-info ...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for fontconfig ...
Processing triggers for python-support ...
Processing triggers for python-central ...
Setting up cups (1.4.3-1ubuntu1) ...
 * Starting Common Unix Printing System: cupsd                                  FATAL: Could not load /lib/modules/2.6.32-21-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.32-21-generic/modules.dep: No such file or directory
                                                                         [ OK ]

Setting up libgnomevfs2-0 (1:2.24.2-1ubuntu2) ...

Setting up udisks (1.0.1-1build1) ...

(udisks:9104): udisks-WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Setting up libgdu0 (2.30.1-1) ...

Setting up consolekit (0.4.1-3ubuntu1) ...
Setting up policykit-1 (0.96-2) ...

Setting up policykit-1-gnome (0.96-2ubuntu2) ...
Setting up gvfs (1.6.1-0ubuntu1build1) ...
Setting up libgnome2-0 (2.30.0-0ubuntu1) ...

Setting up libbonoboui2-0 (2.24.3-0ubuntu1) ...

Setting up libpanel-applet2-0 (1:2.30.0-0ubuntu1) ...

Setting up x11-xkb-utils (7.5+1) ...
Setting up libxklavier16 (5.0-0ubuntu1) ...

Setting up libgnomekbd4 (2.30.0-0ubuntu2) ...

Setting up libxss1 (1:1.2.0-2) ...

Setting up libpulse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...

Setting up libpulse-mainloop-glib0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...

Setting up gnome-settings-daemon (2.30.1-0ubuntu1) ...

Setting up ubuntu-system-service (0.1.20) ...

Setting up libgnomeui-0 (2.24.3-1) ...

Setting up python-gnome2 (2.28.0-1ubuntu1) ...

Setting up gnome-about (1:2.30.0-0ubuntu1) ...
Setting up hplip (3.10.2-2ubuntu2) ...
Creating/updating hplip user account...

Setting up openoffice.org-emailmerge (1:3.2.0-7ubuntu4) ...
stat: cannot read file system information for `/home/ubuntu': No such file or directory
Copying: mailmerge.py
Enabling: mailmerge.py

unopkg done.

Setting up x11-apps (7.5+1ubuntu2) ...

Setting up x11-session-utils (7.5+1) ...
Setting up libxxf86dga1 (2:1.1.1-2) ...

Setting up x11-utils (7.5+3) ...

Setting up x11-xfs-utils (7.4+1build2) ...
Setting up x11-xserver-utils (7.5+1ubuntu2) ...

Setting up powermgmt-base (1.31) ...

Setting up acpid (1.0.10-5ubuntu2.1) ...

Setting up pm-utils (1.3.0-1ubuntu2) ...
Setting up acpi-support (0.136) ...
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

Setting up linux-sound-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-utils (1.0.22-0ubuntu5) ...

Setting up anacron (2.3-13.1ubuntu11) ...

Setting up apport (1.13.3-0ubuntu2) ...

Setting up gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) ...

Setting up gksu (2.0.2-2ubuntu2) ...

Setting up software-properties-gtk (0.75.10) ...

Setting up at-spi (1.30.0-0ubuntu2) ...

Setting up avahi-daemon (0.6.25-1ubuntu6) ...

Setting up bluez (4.60-0ubuntu8) ...

Setting up bluez-cups (4.60-0ubuntu8) ...
Setting up brasero (2.30.0-0ubuntu1) ...

Setting up checkbox (0.9.1) ...

Setting up computer-janitor-gtk (1.14.1-0ubuntu2) ...
Setting up erlang-base (1:13.b.3-dfsg-2ubuntu2) ...
Searching for services which depend on erlang and should be started...none found.

Setting up erlang-crypto (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-mnesia (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-runtime-tools (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-public-key (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-ssl (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-inets (1:13.b.3-dfsg-2ubuntu2) ...
Setting up erlang-xmerl (1:13.b.3-dfsg-2ubuntu2) ...
Setting up couchdb-bin (0.10.0-1ubuntu2) ...

Setting up ghostscript-cups (8.71.dfsg.1-0ubuntu5.1) ...

Setting up cups-driver-gutenprint (5.2.5-0ubuntu1) ...
Did not update any PPD files
 * Reloading Common Unix Printing System: cupsd                          [ OK ] 
Backend smb used by printer HP-Deskjet-3840 is current.
Backend smb used by printer HP-Officejet-g85 is current.
Backend smb used by printer HP-On-Linux is current.
Backend usb used by printer OfficeJet-G85 is current.

Setting up empathy (2.30.1-0ubuntu1) ...

Setting up erlang-syntax-tools (1:13.b.3-dfsg-2ubuntu2) ...
Setting up libgnome-pilot2 (2.0.17-0ubuntu5) ...

Setting up liblpint-bonobo0 (0.1.35) ...

Setting up evolution (2.28.3-0ubuntu9) ...

Setting up evolution-exchange (2.28.3-0ubuntu1) ...

Setting up evolution-plugins (2.28.3-0ubuntu9) ...
Setting up libgnome-vfs2.0-cil (2.24.1-6ubuntu1) ...
* Installing 6 assemblies from libgnome-vfs2.0-cil into Mono

Setting up libgnome2.24-cil (2.24.1-6ubuntu1) ...
* Installing 2 assemblies from libgnome2.24-cil into Mono

Setting up gvfs-bin (1.6.1-0ubuntu1build1) ...
Setting up f-spot (0.6.1.5-2ubuntu6) ...

Setting up foo2zjs (20100210-0ubuntu4) ...

Setting up gbrainy (1.41-1ubuntu1) ...

Setting up gconf-editor (2.30.0-0ubuntu1) ...

Setting up gdebi (0.6.0ubuntu1) ...

Setting up gnome-session-bin (2.30.0-0ubuntu1) ...

Setting up gdm (2.30.0-0ubuntu5) ...

Setting up gdm-guest-session (0.15) ...
Setting up gnome-bluetooth (2.30.0-0ubuntu3) ...

Setting up gnome-codec-install (0.4.2ubuntu2) ...
update-alternatives: using /usr/bin/gnome-codec-install to provide /usr/bin/gstreamer-codec-install (gstreamer-codec-install) in auto mode.

Setting up gnome-disk-utility (2.30.1-1) ...
Setting up python-gnomeapplet (2.30.0-0ubuntu1) ...

Setting up gnome-mag (1:0.16.1-0ubuntu1) ...
Setting up gstreamer0.10-pulseaudio (0.10.21-1ubuntu2) ...
Setting up gnome-media (2.30.0-0ubuntu1) ...

Setting up speech-dispatcher (0.6.8~unofficial~rc2-0ubuntu3) ...
 * Speech-dispatcher configured for user sessions

Setting up python-speechd (0.6.8~unofficial~rc2-0ubuntu3) ...

Setting up python-pyatspi (1.30.0-0ubuntu2) ...

Setting up upower (0.9.1-1) ...

(upower:10997): libupower-glib-WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Setting up gnome-power-manager (2.30.0-0ubuntu1) ...

Setting up gnome-screensaver (2.30.0-0ubuntu2) ...

Setting up nautilus (1:2.30.1-0ubuntu1) ...

Setting up gnome-user-share (2.30.0-0ubuntu2) ...

Setting up gnome-utils (2.30.0-0ubuntu1) ...

Setting up gvfs-backends (1.6.1-0ubuntu1build1) ...

Setting up gvfs-fuse (1.6.1-0ubuntu1build1) ...
Setting up indicator-session (0.2.8-0ubuntu2) ...

Setting up jockey-common (0.5.8-0ubuntu8.1) ...

Setting up language-selector (0.5.7) ...

Setting up lftp (4.0.2-1) ...

Setting up libasound2-plugins (1.0.22-0ubuntu6) ...
Setting up libgail-gnome-module (1.20.1-2) ...
Setting up libgnome2-vfs-perl (1.081-1build1) ...
Setting up libgnome2-perl (1.042-2build1) ...
Setting up libgnomepanel2.24-cil (2.26.0-2ubuntu1) ...
* Installing 1 assembly from libgnomepanel2.24-cil into Mono

Setting up libgnomevfs2-extra (1:2.24.2-1ubuntu2) ...
Setting up libxml-twig-perl (1:3.32-3ubuntu1) ...
Setting up libnet-dbus-perl (0.33.6-1build3) ...
Setting up libnss-mdns (0.10-3ubuntu4) ...

Setting up system-tools-backends (2.9.4-0ubuntu1) ...
Setting up liboobs-1-4 (2.30.0-0ubuntu1) ...

Setting up libpolkit-gtk-1-0 (0.96-2ubuntu2) ...

Setting up libpulse-browse0 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...

Setting up libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1) ...

Setting up libsdl1.2debian (1.2.14-4ubuntu1) ...
Setting up libxml-xpath-perl (1.13-7) ...
Setting up libxvmc1 (2:1.0.5-1ubuntu1) ...

Setting up media-player-info (6-1) ...
Setting up mousetweaks (2.30.0-0ubuntu1) ...

Setting up nautilus-share (0.7.2-12build1) ...
Setting up network-manager (0.8-0ubuntu3) ...

Setting up network-manager-gnome (0.8-0ubuntu3) ...

Setting up pptp-linux (1.7.2-4) ...
Setting up network-manager-pptp (0.8-0ubuntu3) ...

Setting up network-manager-pptp-gnome (0.8-0ubuntu3) ...

Setting up python-virtkey (0.50ubuntu3) ...

Setting up openoffice.org-base-core (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-calc (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-draw (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-gtk (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-gnome (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-writer (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-help-en-us (1:3.2.0-7ubuntu1) ...

Setting up openoffice.org-impress (1:3.2.0-7ubuntu4) ...

Setting up openoffice.org-math (1:3.2.0-7ubuntu4) ...

Setting up openprinting-ppds (20100216-0ubuntu3) ...

Setting up pcmciautils (014-4ubuntu4) ...

Setting up plymouth-label (0.8.2-2ubuntu2) ...
Setting up plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2) ...
update-alternatives: using /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth to provide /lib/plymouth/themes/default.plymouth (default.plymouth) in auto mode.
update-initramfs: deferring update (trigger activated)

Setting up plymouth-x11 (0.8.2-2ubuntu2) ...
Setting up pm-utils-powersave-policy (0.3) ...
Setting up pulseaudio-utils (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pulseaudio (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
 * PulseAudio configured for per-user sessions

Setting up pulseaudio-esound-compat (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pulseaudio-module-gconf (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pulseaudio-module-x11 (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Setting up pxljr (1.1-0ubuntu7) ...

Setting up rhythmbox (0.12.8-0ubuntu5) ...

Setting up rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu5) ...
Setting up rhythmbox-plugins (0.12.8-0ubuntu5) ...

Setting up screen-resolution-extra (0.13) ...

Setting up python-aptdaemon (0.11+bzr345-0ubuntu4) ...

Setting up splix (2.0.0-2ubuntu3) ...

Setting up system-config-printer-gnome (1.2.0+20100408-0ubuntu5.2) ...

Setting up telepathy-salut (0.3.11-1) ...
Setting up tomboy (1.2.1-0ubuntu1) ...

Setting up totem (2.30.2-0ubuntu1) ...

Setting up totem-mozilla (2.30.2-0ubuntu1) ...
Setting up totem-plugins (2.30.2-0ubuntu1) ...

Setting up tsclient (0.150-3ubuntu1) ...

Setting up gnome-system-tools (2.30.0-0ubuntu2) ...

Setting up update-manager (1:0.134.8) ...

Setting up xfonts-encodings (1:1.0.3-1) ...
Setting up xfonts-utils (1:7.5+2) ...

Setting up x-ttcidfont-conf (32) ...
Updating font configuration of x-ttcidfont-conf...
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Updating category truetype..
Updating category cid..
Updating category cmap..

Setting up xserver-common (2:1.7.6-2ubuntu7) ...
Setting up xfonts-base (1:1.0.1) ...

Setting up xfonts-100dpi (1:1.0.1) ...

Setting up xfonts-75dpi (1:1.0.1) ...

Setting up xinit (1.2.0-1) ...
Setting up usb-creator-common (0.2.22) ...

Setting up vinagre (2.30.1-0ubuntu1) ...

Setting up vino (2.28.2-0ubuntu2) ...

Setting up xfonts-scalable (1:1.0.1-1) ...

Setting up brltty (4.1-2ubuntu6) ...
update-initramfs: deferring update (trigger activated)

Setting up brltty-x11 (4.1-2ubuntu6) ...
Setting up evolution-indicator (0.2.8-0ubuntu1) ...

Setting up indicator-sound (0.2.3-0ubuntu1) ...

Setting up pulseaudio-module-bluetooth (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) ...
Processing triggers for python-central ...
Setting up gnome-control-center (1:2.30.1-0ubuntu1) ...

Setting up gnome-panel (1:2.30.0-0ubuntu1) ...

Setting up gnome-applets (2.30.0-0ubuntu2) ...

Setting up apport-gtk (1.13.3-0ubuntu2) ...
Setting up apturl (0.4.1ubuntu4) ...

Setting up checkbox-gtk (0.9.1) ...

Setting up gnome-orca (2.30.0-0ubuntu3) ...

Setting up gnome-session (2.30.0-0ubuntu1) ...
update-alternatives: using /usr/bin/gnome-session to provide /usr/bin/x-session-manager (x-session-manager) in auto mode.

Setting up indicator-applet (0.3.7-0ubuntu1) ...
Setting up indicator-applet-session (0.3.7-0ubuntu1) ...
Setting up indicator-me (0.2.6-0ubuntu1) ...
Setting up jockey-gtk (0.5.8-0ubuntu8.1) ...
Setting up onboard (0.93.0-0ubuntu4) ...

Setting up python-aptdaemon-gtk (0.11+bzr345-0ubuntu4) ...

Setting up aptdaemon (0.11+bzr345-0ubuntu4) ...
Setting up update-notifier (0.99.3) ...

Setting up usb-creator-gtk (0.2.22) ...

Processing triggers for python-central ...
Setting up software-center (2.0.4) ...
WARNING:root:Failed to setup dbus (ignoring)

Setting up ubufox (0.9~rc2-0ubuntu2) ...

Setting up rhythmbox-ubuntuone-music-store (0.0.9-0ubuntu1) ...

Processing triggers for python-central ...
Setting up xserver-xorg-core (2:1.7.6-2ubuntu7) ...

Setting up foomatic-db-engine (4.0.4-0ubuntu1) ...

Setting up foomatic-db (20100216-0ubuntu3) ...

Setting up desktopcouch (0.6.4-0ubuntu3) ...
Setting up python-desktopcouch (0.6.4-0ubuntu3) ...

Setting up evolution-couchdb (0.4.5-0ubuntu1) ...
Setting up xserver-xorg-video-apm (1:1.2.2-1) ...
Setting up xserver-xorg-video-ark (1:0.7.2-1) ...
Setting up xserver-xorg-video-r128 (6.8.1-2ubuntu1) ...
Setting up xserver-xorg-video-mach64 (6.8.2-2) ...
Setting up xserver-xorg-video-radeon (1:6.13.0-1ubuntu5) ...

Setting up xserver-xorg-video-ati (1:6.13.0-1ubuntu5) ...
Setting up xserver-xorg-video-chips (1:1.2.2-1) ...
Setting up xserver-xorg-video-cirrus (1:1.3.2-1ubuntu1) ...
Setting up xserver-xorg-video-fbdev (1:0.4.1-1ubuntu1) ...
Setting up xserver-xorg-video-i128 (1:1.3.3-1) ...
Setting up xserver-xorg-video-intel (2:2.9.1-3ubuntu5) ...

Setting up xserver-xorg-video-mga (1:1.4.11.dfsg-2ubuntu1) ...
Setting up xserver-xorg-video-neomagic (1:1.2.4-2) ...
Setting up xserver-xorg-video-nouveau (1:0.0.15+git20100219+9b4118d-0ubuntu5) ...
Setting up xserver-xorg-video-nv (1:2.1.15-1ubuntu3) ...
Setting up xserver-xorg-video-rendition (1:4.2.3-1) ...
Setting up xserver-xorg-video-s3 (1:0.6.3-1) ...
Setting up xserver-xorg-video-s3virge (1:1.10.4-1) ...
Setting up xserver-xorg-video-savage (1:2.3.1-1ubuntu1) ...
Setting up xserver-xorg-video-siliconmotion (1:1.7.3-1) ...
Setting up xserver-xorg-video-sis (1:0.10.2-2) ...
Setting up xserver-xorg-video-sisusb (1:0.9.3-1) ...
Setting up xserver-xorg-video-tdfx (1:1.4.3-1) ...
Setting up xserver-xorg-video-trident (1:1.3.3-1) ...
Setting up xserver-xorg-video-tseng (1:1.2.3-1) ...
Setting up xserver-xorg-video-vesa (1:2.3.0-1ubuntu1) ...
Setting up xserver-xorg-video-openchrome (1:0.2.904+svn827-1) ...

Setting up xserver-xorg-video-voodoo (1:1.2.3-1) ...
Setting up xserver-xorg-video-v4l (1:0.2.0-4) ...
Setting up xserver-xorg-video-vmware (1:10.16.9-1) ...
Setting up xserver-xorg-video-all (1:7.5+5ubuntu1) ...
Setting up xserver-xorg-input-evdev (1:2.3.2-5ubuntu1) ...
Setting up xserver-xorg-input-synaptics (1.2.2-1ubuntu4) ...

Setting up xserver-xorg-input-mouse (1:1.5.0-1) ...
Setting up xserver-xorg-input-vmmouse (1:12.6.5-4ubuntu2) ...

Setting up xserver-xorg-input-wacom (1:0.10.5-0ubuntu4) ...

Setting up xserver-xorg-input-all (1:7.5+5ubuntu1) ...
Setting up xserver-xorg (1:7.5+5ubuntu1) ...

Setting up xorg (1:7.5+5ubuntu1) ...
Setting up ubuntu-desktop (1.197) ...
Processing triggers for python-central ...
Setting up python-desktopcouch-records (0.6.4-0ubuntu3) ...

Processing triggers for python-central ...
Setting up gwibber-service (2.31.1~bzr743-0ubuntu1~daily1) ...

Processing triggers for python-central ...
Setting up gwibber (2.31.1~bzr743-0ubuntu1~daily1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for initramfs-tools ...
Processing triggers for python-central ...
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "force-reload" failed.
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

 * Starting AppArmor profiles                                                    * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "start" failed.
 * Reloading AppArmor profiles                                                   * AppArmor not available as kernel LSM.
                                                                         [fail]
invoke-rc.d: initscript apparmor, action "reload" failed.
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support                umount: /proc/sys/fs/binfmt_misc: not mounted
update-binfmts: warning: Couldn't unmount the binfmt_misc filesystem from
/proc/sys/fs/binfmt_misc. 
                                                                         [ OK ]
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.
root@ubuntu:/etc/apt# 
root@ubuntu:/etc/apt# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


```So what if I run ubuntu install from the live cd? If i choose my old root partition will it delete it's contents? So basically what I'm planning to do is:
1) I'll create a new partition and move the files from my current inactive root partition to that partition?
2) I'll install lucid again to that old root partition. Now the question is will it remove my old files in root or not? And if it will, should everything work well again, with old settings and apps installed?

I assume I don't need to backup my /home since it's on another partition? So a new installation shouldn't touch it, should it?

Are my plans OK, can I try that? Please suggest me something better if you have any ideas.

And thank you very much for helping me :)

root@bt:~# sudo rm /etc/X11/xorg.conf
root@bt:~# reboot

---

### Post by howefield on 2012-03-25
Old thread closed.

---

