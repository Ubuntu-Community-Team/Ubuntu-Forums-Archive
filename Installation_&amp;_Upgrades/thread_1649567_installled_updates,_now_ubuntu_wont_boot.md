---
title: "installled updates, now ubuntu wont boot"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by red40y on 2010-12-20
i installed updates for ubuntu 10.04 this morning, and on restart when i choose ubuntu (im dual booting on xp) i get a blank screen. the grub wont load.  any incite on this problem?

---

### Post by sikander3786 on 2010-12-20
You sure it is a Wubi install? If unsure, please post the output of bootinfoscript as per instructions here in order to let us figure that for you. You'll need to boot an Ubuntu Live CD/USB for that.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

If sure it is Wubi, can you boot Windows successfully? Depending on that query, either Problem # 1 or Problem # 2 will apply from this thread.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
courtesy of forum member *Rubi1200* and others.

And once fixed your Wubi Ubuntu, don't forget to apply the "Permanent Fix" from the same page to save you troubles later.

Good Luck!

---

### Post by red40y on 2010-12-20
it is a wubi dual boot with win xp pro sp3. windows loads no problem, but when i choose ubuntu it wont go to the grub to choose the ubuntu version.

---

### Post by karthick87 on 2010-12-20
Read this thread,and see which problem matches to you.And apply the fix..Probably Problem #2

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bikeman01 on 2010-12-20
Me too - it is very tiresome how ubuntu updates often break windows dual boots. Wubi included.

Do the developers do this on purpose to annoy windows users?

Is it really that difficult to test releases?

I like Ubuntu but its crap like this which will prevent Linux ever going mainstream.

---

### Post by red40y on 2010-12-20
ok, im running the live cd now, but im not sure how  to go about doing the repairs. (im hopeless i know, lol) i have nothing but time if someone out there was up to walking me through it. =)

---

### Post by Rubi1200 on 2010-12-20
> **bikeman01 said:**
> Me too - it is very tiresome how ubuntu updates often break windows dual boots. Wubi included.

Do the developers do this on purpose to annoy windows users?

Is it really that difficult to test releases?

I like Ubuntu but its crap like this which will prevent Linux ever going mainstream.
There are specific issues affecting Wubi installs at the moment. 

Are they annoying? Yes

Are they relatively easy to fix? Yes

> Do the developers do this on purpose to annoy windows users?
No!

We here on the forums do our utmost best to help users fix these types of issues, learning from them in the process, and trying to persuade the developers to make changes that will avoid these types of situations in the future.

---

### Post by sikander3786 on 2010-12-20
> Do the developers do this on purpose to annoy windows users?

I believe that Wubi installs need to be a bit more stable. But remember, Wubi was just intended for testing and not for production purposes. Did you read through what the Wubi creator said?

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

Updates with a proper Ubuntu install are far more stable.

And, I don't want to start a flame war here :-)

---

### Post by Rubi1200 on 2010-12-20
> **red40y said:**
> ok, im running the live cd now, but im not sure how  to go about doing the repairs. (im hopeless i know, lol) i have nothing but time if someone out there was up to walking me through it. =)
Hi,
first of all, I need to know if you can boot Windows normally?

Next, download and run the boot info script. It is linked at the bottom of my post. There are instructions how to run it.

Post the results back here and then we can move to the next step.

---

### Post by red40y on 2010-12-20
yes, i can boot win just fine, untill i poped in the live cd, i was posting using win.


(Quick question, do you want me to post the whole results.txt, or a section of it?)

---

### Post by Rubi1200 on 2010-12-20
Then please run the boot info script and post the results here.

Thanks.

---

### Post by red40y on 2010-12-20
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
43 heads, 41 sectors/track, 277026 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      2,041,856   488,394,751   486,352,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4d96f6f9-6d18-40d3-88f3-4d5bf391f253   ext4                                     
/dev/sda1        9EE8A555E8A52C89                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.6GB: boot/grub/grub.cfg
  11.8GB: boot/initrd.img-2.6.32-21-generic
  12.0GB: boot/initrd.img-2.6.32-26-generic
   2.8GB: boot/initrd.img-2.6.32-27-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
  11.8GB: boot/vmlinuz-2.6.32-26-generic
  12.1GB: boot/vmlinuz-2.6.32-27-generic
   2.8GB: initrd.img
  12.0GB: initrd.img.old
  12.1GB: vmlinuz
  11.8GB: vmlinuz.old

---

### Post by Rubi1200 on 2010-12-20
Okay, thanks for the results.

So, this is what we are going to do now.

Go back to the terminal and copy/paste the following commands there. Run them separately and hit Enter after each one:
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```
After running the last command to open the grub.cfg file, post back here and we will move forward.

If you run into any problems, also let me know.

---

### Post by babdare on 2010-12-20
I have the same problem. Winxp and Ubuntu 10.10(wubi-install update 10.04 to 10.10).
I have fixed the update problem 10.04 to 10.10 with the modified wubildr.
Today there was a kernel update  from 2.6.32 to .26.35 and after the restart i can boot only xp.
If i choose Ubuntu, there is a black screen and the computer restart.

Here is my log:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,560,639   240,878,610   f W95 Ext d (LBA)
/dev/sda5          71,682,093   312,560,639   240,878,547   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3b9cec62-504f-464b-be56-c4e87a606129   ext4                                     
/dev/sda1        64C4AEEEC4AEC222                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2E64A09964A064F5                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/2E64A09964A064F5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINXP
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINXP="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr="Ubuntu" 

```

---

### Post by red40y on 2010-12-20
her we go...

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9ee8a555e8a52c89
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Rubi1200 on 2010-12-20
Do you see this line?
> ### BEGIN /etc/grub.d/10_lupin ###
Delete everything in the file ABOVE that line. Do not delete the line itself or anything below it.

Close and save the file.

Reboot the computer, taking the CD out of course, and you should be back in both Windows and Ubuntu (try Ubuntu first just to make sure)

---

### Post by red40y on 2010-12-20
!Bam!
that did the trick, thank you for the walk through! you are a real life saver! =)

---

### Post by Rubi1200 on 2010-12-20
No problem, you are more than welcome :)

But, we are not finished yet ;)

In Ubuntu, go to System > Administration > Synaptic Package Manager

Use the search function to find the grub-pc and grub-common packages (they will be marked with a green checkmark).

Highlight each one and then from the menu choose Package > Lock Version

Do this for each one and that should prevent the problem from happening again.

There is also a more permanent fix on the thread, but we can save that for another day unless you want to try it yourself.

Please also mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by Rubi1200 on 2010-12-20
> **babdare said:**
> I have the same problem. Winxp and Ubuntu 10.10(wubi-install update 10.04 to 10.10).
I have fixed the update problem 10.04 to 10.10 with the modified wubildr.
Today there was a kernel update  from 2.6.32 to .26.35 and after the restart i can boot only xp.
If i choose Ubuntu, there is a black screen and the computer restart.

Here is my log:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,560,639   240,878,610   f W95 Ext d (LBA)
/dev/sda5          71,682,093   312,560,639   240,878,547   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3b9cec62-504f-464b-be56-c4e87a606129   ext4                                     
/dev/sda1        64C4AEEEC4AEC222                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2E64A09964A064F5                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/2E64A09964A064F5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINXP
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINXP="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr="Ubuntu" 

```
Hi and welcome to the forums :)

You have a different problem in some ways because of this:
> mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error

Please start a new thread posting all the information so we can deal with this separately.

Thanks.

---

