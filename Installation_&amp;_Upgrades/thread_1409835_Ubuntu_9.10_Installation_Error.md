---
title: "Ubuntu 9.10 Installation Error"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by Corneliuss on 2010-02-18
I have 2 Hard drive originally
my first harddrive was a 500 GB had 3 operating systems on it
Vista (This i installed in my 2nd partition at the very start)
Windows 7 ( This i installed in my 1st partition once it came out)
Ubuntu Linux (This I always had in my 3 partition as a removable windows program)

My 2nd harddrive
1.5 TB (I had recently got and decided i'd move start fresh on this harddrive and use the other as my backup and have ubuntu as my main OS)

So, I delete my vista and formatted the partition
after that I restarted my computer and had a boot error and not having any of my windows disks detecting my harddrives so i could fix the damn thing i gave up and grabbed my 1.5 TB and put Ubuntu Linux on it to partition it in half because i wanted to run both windows 7 off one harddrive and linux ubuntu // other linuxes off the other.

When i try to boot with just my Windows hard drive it says
"No Operating System Found"

When i try to boot with just my Ubuntu hard drive it says
Error: out of disk
Failed to boot default entries
Press any key to continue... (Just keeps repeating that)

Edit: I'm currently running it from the CD not the installation.
Desktop 64-Bit I believe (Maybe 32)

---

### Post by r_s on 2010-02-18
check using testdisk , you can run it from a live cd

---

### Post by Corneliuss on 2010-02-18
I'm currently on my system because of the live cd
I can't get it to work otherwise

---

### Post by r_s on 2010-02-18
just install testdisk and you can check all your partitions and even recover them if you haven't written on them

---

### Post by presence1960 on 2010-02-18
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

### Post by Corneliuss on 2010-02-18
> The only reason that i'm about to get on an OS is because it's running from "try ubuntu without any changes to your computer"

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5013dcd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,894,431,049 2,894,430,987  83 Linux
/dev/sda2       2,894,431,050 2,930,272,064    35,841,015   5 Extended
/dev/sda5       2,894,431,113 2,930,272,064    35,840,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1   ext4                                     
/dev/sda5        9ad2fd9c-7ba9-48db-bf9e-4feaffd6fadf   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1 ext4       (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1
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
    search --no-floppy --fs-uuid --set 5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1 ro single 
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5e5e64e6-b3e1-4b47-ad87-dd6f5ccacef1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9ad2fd9c-7ba9-48db-bf9e-4feaffd6fadf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 107.5GB: boot/grub/core.img
 107.5GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: initrd.img
    .1GB: vmlinuz

---

### Post by presence1960 on 2010-02-18
where is the disk with windows on it? The 1.5 TB only has linux. I need you to run the script with the disk that has windows on it plugged in. How else are you going to boot windows?

---

### Post by Corneliuss on 2010-02-18
Oh I got rid of the windows
I'm only running ubuntu and i get that error when i try too run it

I have a problem with my other harddrive that has windows 7 on it and it has to go back for warranty

I just want to be able to run Ubuntu 9.10 without that error that i'm getting

Edit:
Like right now i have to run it with the cd in it and no changes to the computer because it keeps giving me that error

> When i try to boot with just my Ubuntu hard drive it says
Error: out of disk
Failed to boot default entries
Press any key to continue... (Just keeps repeating that)

That is what I meant to say.

---

### Post by oldfred on 2010-02-18
Have you tried to boot using the liveCD but the selection that says use hard drive? (bypassing grub in the MBR which maybe all you have to reinstall).

Is there a problem with your windows drive or is the problem just that you cannot boot? When you deleted Vista you also deleted parts of the Win7 boot that was in the Vista partition. If you run the win7 repairs it should boot again.

---

### Post by Corneliuss on 2010-02-19
> **oldfred said:**
> Is there a problem with your windows drive or is the problem just that you cannot boot? When you deleted Vista you also deleted parts of the Win7 boot that was in the Vista partition. If you run the win7 repairs it should boot again.

Have you tried to boot using the liveCD but the selection that says use hard drive? (bypassing grub in the MBR which maybe all you have to reinstall).

Explain How lol
Sorry other then using Ubuntu for a couse last year I don't understand anything or remember anything accept the important terminal commands.
I understand boot using liveCD then the very last option i'm thinking is what your talking about where it says boot with harddrive. Done that thats the error I get from it that i reported.

Something is wrong with my Boot Sequence but how to fix...

---

### Post by oldfred on 2010-02-19
First lets try reinstalling grub, follow the directions for 9.10 with grub2:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2010-02-19
I'd try this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by kansasnoob on 2010-02-19
BTW if the Temporary Solution in that how-to gets you booted you could install the current Lucid packages of grub-pc and grub-common as they seem to have fixed that problem.

Once booted into your installed Karmic first run this command to see if you have 32bit or 64bit installed:

```
uname -m
```

(64 bit = x86_64, and 32 bit = i686)

Then just:

```
sudo apt-get remove grub-pc grub-common
```

Then download the proper versions of grub-common and grub-pc:

[http://packages.ubuntu.com/lucid/grub-common](http://packages.ubuntu.com/lucid/grub-common)

[http://packages.ubuntu.com/lucid/admin/grub-pc](http://packages.ubuntu.com/lucid/admin/grub-pc)

Just save them to the Desktop (or Downloads folder, wherever you wish) then just double-click the package and gdebi will install it. **(Note: grub-common must be installed first and grub-pc second)**

Then just run:

```
sudo update-grub
```

And to be on the safe side:

```
sudo grub-install /dev/sda
```

If the temp solution doesn't get you booted we can still try that through a chroot using wget and dpkg but I'd need to see the output of:

```
uname -m
```

So I use the proper packages in the commands.

---

### Post by Corneliuss on 2010-02-20
I sorta got it working can't get it to not fail boot.

If I were to torrent a new copy and (burn CD) install that would this problem be fixed?

Seeing how it seems you have packages out to fix this error.

I'm going to try these solutions i'll see if they work

---

