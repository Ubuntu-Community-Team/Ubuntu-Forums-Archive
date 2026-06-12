---
title: "Sticks at &quot;Grub...&quot; when booting"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by RonMorris on 2010-02-18
I am new to Ubuntu, having only installed it on vitrual machines, and my own machine on a spare hard drive. Now I would like to offer refurbished/new builds to customers who want something other than... you know what. 
 
On a rather boring old Asus P4B motherboard, which I have sitting around, Ubuntu 9.10 installs fine, but when booting hangs at a blank screen with "Grub" displayed. The BIOS is configured to try the optical drive first, then the hard drive. If I boot while leaving the Ubuntu Live CD in the drive and choose "Boot from main hard drive" or boot while leaving a Windows XP install CD in the drive and DO NOT "Hit any key to boot from CD," Ubuntu boots fine. This ought to be a generic install with Ubuntu as the only operating system and the only hard drive partitioned entirely for it, so I am puzzled by the bootloader's problem!
 
Others have had similar problems, but the solutions either seem to not help, or the settings involved are already set correctly. I have already tried the most mundane options, reinstalling, substituting another hard drive, using a different IDE channel, and so forth, with the same results. I can't seem to find reliable information about the Grub bootloader and how to configure it either!

---

### Post by johnson.d on 2010-02-19
You can probably try updating the grub using the following steps:

1) Boot into the Ubuntu OS using the "boot from the Harddisk" option.

2) After booting open terminal and use the following command,

```
$ sudo update-grub2
```

3) Reboot and boot directly from the Harddisk.

Note: you should be cautious about using the above command as it affects the boot loader.

---

### Post by darkod on 2010-02-19
To have more detailed info about the boot process, use these instructions and post the content of your results.txt file here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by RonMorris on 2010-02-19
> **johnson.d said:**
> You can probably try updating the grub using the following steps:
 
1) Boot into the Ubuntu OS using the "boot from the Harddisk" option.
 
2) After booting open terminal and use the following command,
 
```
$ sudo update-grub2
```
 
3) Reboot and boot directly from the Harddisk.
 
Note: you should be cautious about using the above command as it affects the boot loader.
 
Well, this command completed and reconfigured the config file, but the problem is still the same. When I get time I will research further, using your kind help and the results of searching these forums for "update-grub2," which provided a couple of day's worth of study material. Thanks for the lead. I am sure the answer is close by.

---

### Post by kansasnoob on 2010-02-19
It would be very helpful to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by RonMorris on 2010-02-19
> **darkod said:**
> To have more detailed info about the boot process, use these instructions and post the content of your results.txt file here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)
 
 OK! Here is the contents of RESULTS.TXT:
 
```
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #1 for /boot/grub.
sda1: _________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda2: _________________________________________________________________________
File system: Extended Partition
Boot sector type: -
Boot sector info: 
sda5: _________________________________________________________________________
File system: swap
Boot sector type: -
Boot sector info: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001d925
Partition Boot Start End Size Id System
/dev/sda1 * 63 157,083,569 157,083,507 83 Linux
/dev/sda2 157,083,570 160,071,659 2,988,090 5 Extended
/dev/sda5 157,083,633 160,071,659 2,988,027 82 Linux swap / Solaris
&#12288;
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/sda1 9d5035ba-0ea1-4882-b0ce-748e2e1e2c41 ext4 
/dev/sda5 6946c7a5-27f1-4cff-9431-ad7e3a9d5d1d swap 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
/dev/sda1 / ext4 (rw,errors=remount-ro)
/dev/sr0 /media/cdrom0 iso9660 (ro,nosuid,nodev,utf8,user=default)
&#12288;
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
search --no-floppy --fs-uuid --set 9d5035ba-0ea1-4882-b0ce-748e2e1e2c41
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
search --no-floppy --fs-uuid --set 9d5035ba-0ea1-4882-b0ce-748e2e1e2c41
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=9d5035ba-0ea1-4882-b0ce-748e2e1e2c41 ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 9d5035ba-0ea1-4882-b0ce-748e2e1e2c41
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=9d5035ba-0ea1-4882-b0ce-748e2e1e2c41 ro single 
initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=9d5035ba-0ea1-4882-b0ce-748e2e1e2c41 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=6946c7a5-27f1-4cff-9431-ad7e3a9d5d1d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
=================== sda1: Location of files loaded by Grub: ===================
&#12288;
3.2GB: boot/grub/core.img
.5GB: boot/grub/grub.cfg
.5GB: boot/initrd.img-2.6.31-14-generic
.5GB: boot/vmlinuz-2.6.31-14-generic
.5GB: initrd.img
.5GB: vmlinuz
 

```

---

### Post by RonMorris on 2010-02-19
See my two new posts. Sorry for the out-of-thread reply, I just found the cryptic "Reply" button!

---

### Post by kansasnoob on 2010-02-19
Well that all looks good. I suspect this is similar to a legacy grub error 18:

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

NOTE: That applies to legacy grub but I can't find anything for grub2 yet regarding this.

Basically the deal is this, that's an old MoBo, I see it still uses PC100/PC133 RAM, so I think this basically applies:

> dates back to the old days when new computers were just beginning to use hard disks that exceeded the 8.45 GB limit.

> Now, technology has also passed the 33.8 and 137 GB hard drive limits too

> You can check the date of your computer's BIOS by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: Getting Product Information.

Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented.
2.11 GB or 4095 cylinder limit
3.26 GB or 6322 cylinder limit
4.22 GB or 8192 cylinder limit _______________________________(around 1997 or earlier)
8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)

You could check at your motherboard manufacturer's website, (find it with google), to see if there is a newer update for your machine's BIOS available. If so, you can download it and try 'flashing the BIOS'.  That has been reported to have solved this problem many times. 

[http://members.iinet.net/~herman546/p1.html#Getting_Product_Information](http://members.iinet.net/~herman546/p1.html#Getting_Product_Information)

[http://www.asus.com/999/html/events/mb/socket478/p4b-e/overview.htm](http://www.asus.com/999/html/events/mb/socket478/p4b-e/overview.htm)

So it would be interesting to know which limit is possibly being exceeded. Since this is a fresh install anyway I'd begin by using Gparted from the Live CD and shrinking sda1 to just below the limit if you can figure out what the limit is, I'd guess 33.8 or 8.45 GB.

If that seems to get you booting then you might want to reinstall choosing to create a separate /boot partition.

Clear as mud?????????

---

### Post by meierfra. on 2010-02-20
Grub2 also is affected by the Bios hard disk limits. But I don't think that is the issue at hand".  The "boot from the first hard disk" option  would also  be affected by the  Bios hard disk limits. Also:

```
3.2GB: boot/grub/core.img
.5GB: boot/grub/grub.cfg
.5GB: boot/initrd.img-2.6.31-14-generic
.5GB: boot/vmlinuz-2.6.31-14-generic
.5GB: initrd.img
.5GB: vmlinuz
```

all of the boot files are within the first 3.2 GB of the hard drives. So I don't think a smaller partition will help.  At least you would have to create a separate boot partition (200-500MB).

Before trying a separate boot partition try reinstalling grub with the "ata" module (Using that module, grub relies less on the bios)

```
sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --disk-module=ata --root-directory=/mnt /dev/sda
```

---

### Post by RonMorris on 2010-02-20
If the BIOS could not detect the hard drive properly, it would not report the correct size. This is what happened in the old days when the problems you refer to were common. You could still use a larger hard drive, but it would have only the maximum capacity the BIOS allowed. This is not what I see here. The BIOS is the newest available for this board. I verified that the SAME PROBLEM happens when I install Ubuntu on an old spider encrusted 1GB hard drive. So I don't think this is it. The BIOS correctly reports the size of the largest drive I have to plug into it, 320GB.

---

### Post by RonMorris on 2010-02-20
> **meierfra. said:**
> Grub2 also is affected by the Bios hard disk limits. But I don't think that is the issue at hand".  The "boot from the first hard disk" option  would also  be affected by the  Bios hard disk limits. Also:

```
3.2GB: boot/grub/core.img
.5GB: boot/grub/grub.cfg
.5GB: boot/initrd.img-2.6.31-14-generic
.5GB: boot/vmlinuz-2.6.31-14-generic
.5GB: initrd.img
.5GB: vmlinuz
```

all of the boot files are within the first 3.2 GB of the hard drives. So I don't think a smaller partition will help.  At least you would have to create a separate boot partition (200-500MB).

Before trying a separate boot partition try reinstalling grub with the "ata" module (Using that module, grub relies less on the bios)

```
sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --disk-module=ata --root-directory=/mnt /dev/sda
```
This does not work either. The problem is still the same. Thanks for trying to help.

---

### Post by meierfra. on 2010-02-20
> This does not work either.
I'm not surprised, it was just something easy to try. 

Other things you might try
[LIST=1]

[*] Separate Boot partition at the beginning of the hard drive.

[*] Upgrade to Lucid's Grub 2

[*] Downgrade to Legacy Grub.

[*] Install Grub 2 or Legacy Grub to  /dev/sda1 and install [GAG]("http://gag.sourceforge.net/") to the MBR

[*] Check whether where is a update for your Bios.

[/LIST]

I have heard of similar cases with Legacy grub  where  Suggestion #4  (using GAG in the MBR) was successful. 
All the other suggestions are pure speculation and I have no idea whether they would work.

Herman has a page on Gag: [http://members.iinet.net.au/~herman546/p12.html](http://members.iinet.net.au/~herman546/p12.html)

To install Grub 2 to /dev/sda1, boot into Ubuntu. Then

```

sudo grub-install --recheck  --force /dev/sda1
```

---

### Post by RonMorris on 2010-02-20
PROBLEM SOLVED:
 
I found it by diddling with BIOS options.
 
The fact that Ubuntu booted correctly when even a Windows bootable install CD was in the drive suggested that perhaps nothing basic was really wrong. This was correct.
 
This motherboard (Asus P4B) has a strange and annoying, but cute, voice POST readout feature. Turning this off solved the problem. 
 
There was some strange timing thing going on making Grub hang while the asthmatic robot woman droned on saying "Power on self-test complete.... Computer now booting from operating system." I assume a CD in the drive merely delayed Grub starting until she stopped yacking. Quieter is better anyway. I can't imagine why I had the nasty thing on anyway. One simple beep is much nicer. The engineers at Asus usually aren't so silly!! ;)
 
Thanks for the help.

---

### Post by meierfra. on 2010-02-20
> PROBLEM SOLVED:

I found it by diddling with BIOS options.

Great.   That's a new item for my list of  Grub problems.

---

### Post by RonMorris on 2010-02-22
Thanks for the help. This bothered me for days. 
 
Now onto the next problem.............

---

