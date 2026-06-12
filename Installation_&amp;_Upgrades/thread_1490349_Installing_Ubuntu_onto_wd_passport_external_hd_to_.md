---
title: "Installing Ubuntu onto wd passport external hd to replace non-functioning internal hd"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by welbek on 2010-05-22
Hi there, all:

I recently bought an Acer Extensa 5635Z and things were fine until I lent it to my godson for a weekend and got it back with the internal hard drive not functioning; he said it worked one night, and didn't the next morning; now, it's not recognised and an OS is not found during bootup. Whereas this was bad news for me in one way, on the other hand it was the perfect chance to switch to Ubuntu, something I've been wanting to do for years, and I've been really enjoying most aspects of it after using a live disk to be able to do my work over the last couple of days. Now, instead of buying another new laptop, I would like to use an external hard drive that I've just bought in the place of my broken internal hd, and have Ubuntu on it.

I've read tutorials on it and they basically say that all I have to do is:

* Run the live disk - done
* Uncheck these options -
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserte
* Use the install ubuntu process and supposedly use the entire disk?
* Restart and choose to boot from the external HDD

Is that it? Is there anything else I should do for this particular brand or situation (will the BIOS recognise the hard drive?) or any issues I should know about beforehand? How do I choose the HDD as primary boot? Should I insert the external HD before or after unchecking the options? Should I leave any of the 250 GB to '/dev/sda1'? There being no actual internal hard drive won't provoke trouble with the process?


P.S. My computer is 64-bit capable and I've been using a 64-bit Ubuntu  disc. I've had trouble viewing things in this interim period,  particularly videos, and incapable of installing codecs. Should I just  get a 32-bit Ubuntu disc? Or will the problems be resolved when I have a  rewritable disc on which to operate?


I'm sorry if that's a barrage of questions.

Thanks in advance

Welbek

---

### Post by darkod on 2010-05-22
I haven't heard about item #2 you specified, but if it says to do it, then do it.
Otherwise, there is really nothing special. Especially if your internal hdd is completely dead, the ext hdd will be only hdd as far as ubuntu is concerned.

You can use the Use Whole Disk option, or manual partitioning if you prefer. The bootloader should go on the same disk especially if it's the only one.

In your laptop BIOS you will need to set USB-HDD as boot device in first place. It should be able to boot from usb but some laptops can't (probably older ones), so watch out for that option.

If you use the whole disk guided option, I think the standard install is with /dev/sda1 as root and logical partition /dev/sda5 as swap.

Once you have it fully installed, you will be able to add all codecs you need. Some of them are really easy fix. I had the same problem with flash on 64bit. Tried with various players, even Adobe flash player from their website, and it turned out the best solution is just to download a library for 64bit flash from Adobe and put it in firefox plugins folder.

---

### Post by welbek on 2010-05-22
Thanks a lot for your help! I guess that I will have to set up BIOS after putting Ubuntu onto the external hdd? Where do you get such a library?

All the best,

Welbek

---

### Post by welbek on 2010-05-22
By the way, it is asking me the following:

The installer has detected that the following disks have mounted partitions, /dev/sda - do you want to try to unmount the partitions?

What does this mean? I'm supposing that I should unmount them, is that right?

All the best
Welbek

---

### Post by darkod on 2010-05-22
> **welbek said:**
> By the way, it is asking me the following:

The installer has detected that the following disks have mounted partitions, /dev/sda - do you want to try to unmount the partitions?

What does this mean? I'm supposing that I should unmount them, is that right?

All the best
Welbek

Yes, unmount all partitions so the installer can work with the disk.

I had to get the library for flash for 9.10 but as a matter of fact, when I recently installed 10.04 over it as clean install, not upgrade, I didn't have to. So it seems it's included in 10.04 64bit.

---

### Post by welbek on 2010-05-22
Hi there, unfortunately it didn't go too smoothly and I am back working off the live disc:

Here's what happened.

I had it install and unmounted and all, and it seemed like it was installing and then it came up with:

I/O Error Dev sr0 sector 466308
repeated dozens of times.

I restarted and changed the boot order, giving primacy to the external hard drive and putting the broken internal hard drive (which was making a horrific churning noise) last behind CD, and other stuff related to the external hard drive. it went onto a black screen with a single _. Then it said: Gave up waiting for root device. Common problems boot-arap missing modules

ALERT! /dev/disk/by-uuid/3e66bbd5-ed17-4bdf-8969-38a228455d8d does not exist, dropping to a shell. Then it came up with this busybox interface. And yet Ubuntu seems to be installed on the external harddrive. What can I do to rectify this?

Thanks in advance

All the best, Welbek

---

### Post by darkod on 2010-05-22
Run the boot info script from live mode as per the instructions and post the content of the results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

I also recommend taking the broken internal hdd out if you have easy access to it. Laptops usually have a cover you can remove to access the hdd.

---

### Post by welbek on 2010-05-22
Thanks! Here's what is says. I put it onto the desktop that appears when running the live disk. Unfortunately I don't have a small enough screwdriver with me to take out the internal hard drive at the minute.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 249.4 GB, 249356615680 bytes
255 heads, 63 sectors/track, 30315 cylinders, total 487024640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   475,391,999   475,389,952  83 Linux
/dev/sda2         475,394,046   487,022,591    11,628,546   5 Extended
/dev/sda5         475,394,048   487,022,591    11,628,544  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0e2e2a66-d81a-4e64-91fc-8bd9562445db   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        71a946cf-5cf3-4f07-a319-0f64ac3fe6a5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/0e2e2a66-d81a-4e64-91fc-8bd9562445db ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr1         /media/WD SmartWare      udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0e2e2a66-d81a-4e64-91fc-8bd9562445db
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0e2e2a66-d81a-4e64-91fc-8bd9562445db
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e2e2a66-d81a-4e64-91fc-8bd9562445db
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0e2e2a66-d81a-4e64-91fc-8bd9562445db ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e2e2a66-d81a-4e64-91fc-8bd9562445db
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0e2e2a66-d81a-4e64-91fc-8bd9562445db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e2e2a66-d81a-4e64-91fc-8bd9562445db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e2e2a66-d81a-4e64-91fc-8bd9562445db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0e2e2a66-d81a-4e64-91fc-8bd9562445db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=71a946cf-5cf3-4f07-a319-0f64ac3fe6a5 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 167.6GB: boot/grub/core.img
  34.4GB: boot/grub/grub.cfg
 167.6GB: boot/initrd.img-2.6.32-21-generic
 167.6GB: boot/vmlinuz-2.6.32-21-generic
 167.6GB: initrd.img
 167.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  63 4a 4a 76 df 5e 92 ac  92 3d 94 b3 cb b5 f3 4f  |cJJv.^...=.....O|
*
000001b0  63 4a 4a 76 df 5e 92 ac  92 3d 94 b3 cb b5 00 fe  |cJJv.^...=......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 70 b1 00 00 00  |...........p....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by darkod on 2010-05-22
It looks good. Not sure why is it confused and why does it look for UUID 3e66bb... 

Also not sure if that I/O error is caused by the internal disk malfunction, and ubuntu tries to spin it. That's why the suggestion to get rid of it, to take it out of the equation.

Restart, make sure the usb-hdd is first option in BIOS (ok, it can be second, after cd-rom, the main part is to be before hdd).

If that UUID disk error is still there, boot into live mode again and reinstall grub2 to the MBR of the ext hdd with:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

See if that helps. Otherwise the results file looks perfectly normal.

---

### Post by efflandt on 2010-05-22
If your internal hard drive is broken, why don't you just remove it, or at least deactivate it in BIOS and/or remove it from boot order?

I don't know what those * items are for in your original post.  All you should have to do in BIOS is make sure that USB boots before hard drive if you did not remove or deactivate internal hard drive.

To install to WD Passport, I simply booted the install iso from CD or USB flash into live system.  If the Passport is connected after that, unmount its partition(s), then run the install.  Partition it how you want (swap partition >= RAM if you want to hibernate).  And pay attention to the **Advanced** button in the summary screen (step 7 or 8) to make sure that grub goes to mbr of external drive (especially if your internal drive is still there).

It sounds like your CD is corrupt or your drive is having trouble reading it (I/O Error Dev sr0 sector 466308).

Booting USB hard drives can be temperamental with some computers.  For example Dell laptops seem to do a fast boot before the drive spins up, and often do not even show the USB drive as a boot option unless I change something in BIOS and reboot, or boot something else, and then reboot with the drive already connected.

One thing I have not figured out is why my desktop PC cannot boot 10.04 from a 500 GB Passport. At first it could not even boot 10.04 from a 160 GB Passport (grub rescue "error: file not found") until I repartitioned and installed 10.04 using partman/alignment=cylinder parameter. That parameter also worked installing 10.04 on 200 GB internal drive.  But grub rescue for the 500 GB Passport says "error: unknown filesystem" (it is ext3 and the drive boots fine on 2 laptops).  Linux itself has no trouble reading reading or mounting the 500 GB drive partitions, but even grub 1.98 from my main hard drive cannot.

So I do not know what causes my issues with just that one PC (HP a530n w/Asus mobo from 2004) at some size bigger than 200 GB, but less than 500 GB.

---

### Post by robvas on 2010-05-22
There are videos on how to open the case of the external HD, you can just put the drive directly in your computer, replacing the broken one that's in there now.

---

### Post by welbek on 2010-05-22
hello everyone – thanks for your suggestions. I'm rather confused too. I went into Bios and set the usb-hdd in primary position, as I had done before, but with the same outcome. I've entered the code that you gave me, Darko, into the terminal, and it says 'installation finished: no error reported' but there are still problems. It isn't allowing me to put anything onto the external HDD – would you all suggest that it be reformatted (and try to install it again with another disk perhaps?) The CD may be corrupted but I've been using it to work on for days without any big problems yet. I would have already taken out the HD, but I need tools to get to it and I won't have them at hand until Monday.


All the best


Welbek

---

### Post by dino99 on 2010-05-22
your sda2 is corrupted (look and read the info script at the end), so your formatting is not good. No need to go further till you make a correct formating:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

about your "dead" hdd, check it with partedmagic (link above) or cgsecurity tools ([http://www.cgsecurity.org/](http://www.cgsecurity.org/))

---

