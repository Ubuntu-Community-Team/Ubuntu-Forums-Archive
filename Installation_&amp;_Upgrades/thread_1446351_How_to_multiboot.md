---
title: "How to multiboot?"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by nitstorm on 2010-04-03
i am desperately looking for a how to : multiboot. Checked bodhi.zazen's thread, but its totally with reference to GRUB Legacy. I have karmic installed and also vista. wondering if there is a step-wise guide to multiboot with reference to Grub2. 

I want to add a SUSE, Fedora and Lubuntu, but have no clue as to how. I messed up my comp earlier trying to multiboot so now I just dual-boot Windows Vista and Karmic Koala.

---

### Post by kblft on 2010-04-03
look here [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

and possibly here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by nitstorm on 2010-04-03
> **kblft said:**
> look here [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

and possibly here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But how does that help me multiboot??? i am looking for a step-wise procedure on how to multiboot.

---

### Post by kblft on 2010-04-03
> Quote:
Originally Posted by kblft  
look here [http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

and possibly here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
But how does that help me multiboot??? i am looking for a step-wise procedure on how to multiboot.

I don't know of a step-by-step procedure on how to multiboot with grub2

What you need to do though, is add the other OSs you wish to multiboot with to the grub menus.

There are sections in the wiki on how to add other OSs to the grub menus

---

### Post by nitstorm on 2010-04-03
So I just install the other OS's and put their entries in the grub and that's it????? But won't every OS that I install try to install their own Grub and what not?

---

### Post by kblft on 2010-04-03
You have two alternatives : 

1. I'm not sure how other distros handle this - but in ubuntu you can choose to not install a boot loader (e.g grub) - so things like this don't happen. I assume there is such a possibility with other distributions. Then once the other distros are installed - you can just add them to the grub menu

2. you can install everything - and just add ubuntu last. It will autodetect the rest of the OSs and will add them automatically to grub (overriding their installation of grub if installed).

EDIT
A warning though - if you choose to install several distros - you must remember to never accept grub updates from any of them except the one you chose to install grub with... otherwise it might cause some mess..

---

### Post by nitstorm on 2010-04-03
Ah! Nice.... I don't know how to do the first way, ill follow the second way and keep u posted... Thanks kblift :)

---

### Post by oldfred on 2010-04-04
Grub or grub2 is just the boot loader. You need to plan you partitions and which boot loader is in charge and how to boot the other systems. Grub2 is very good at finding other systems but if you have a lot the menu becomes very large and difficult to manage.

I always like chainbooting since each system has its boot loader in its partition and is updated with new kernels so you can easily boot the latest updates. Grub2 does not like to be installed in the PBR so it should not be used for chainbooting but can be. Other systems still using grub legacy can easily be chainbooted. Note separate data partiion.
Example with old grub booting 145 systems on 2 drives:
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

You also have to plan how you handle data. You should not share /boot nor /home as differences between versions can cause conflicts. If you share /home with different user names you have not shared any settings just the partition. But you can share all your data with just a little partition planning. I like having the same firefox, thunderbird and all data in each system.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by nitstorm on 2010-04-05
So how were you able to achieve the same firefox and thunderbird data across all ur OS's ?

---

### Post by oldfred on 2010-04-05
Continued to work with Firefox upgrades but I have not upgraded Thunderbird yet, and now have NTFS shared partition:

If you boot both windows and Ubuntu often you can have the same firefox and thunderbird data in a common partition.
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Firefox version 2 to 3 on both windows & ubuntu. 

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
More info:
    *  (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (SeaMonkey) ./seamonkey -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by ranch hand on 2010-04-06
There are several things to consider beefore you start your multi-boot installations.

Your drive is limited to 4 primary partitions.  You will need to add an "extended" partition.  This is a type of primary partition that you can install, in theory, and infinite number of "logical partitions".  Plan this on paper before you start.

I would make all your partitions before starting installation using gparted from your 9.10 Live CD.

Fedora and Suse will install nicely with MS but will try to take over any Linux partitions.  Make sure you check every partition in their installers to make sure only the partition(s) you want them installed on are marked for use and the others marked as "do not use".

Grub on your last (Ubuntu) installation should pick up your other OS'.  There may be way too many generated entries however.  You will probably need a custom menu for this to really work.  This is not hard to set up and requires little or no upkeep when finished.

See the link in my sig for a basic over view of Grub.  The second link that I give in that post is the very best in depth study of Grub you will find.

You need to know this stuff if you are going to multi boot.

It is a lot of FUN.  I am on a drive, right now with 12 installed and working OS' all booted from grub1.98 (from 10.04-testing).

---

### Post by nitstorm on 2010-04-08
gr8 info thanks guys, will try multibooting over the weekend and get back to y'all. also i can put in karmic and lucid in the multiboot list right?

---

### Post by ranch hand on 2010-04-08
> **nitstorm said:**
> gr8 info thanks guys, will try multibooting over the weekend and get back to y'all. also i can put in karmic and lucid in the multiboot list right?
I am not sure what you mean by that.  If you mean can you have more than on Ubuntu the answer is yes.

I have, right now, seven variations of 10.04 on this drive (test platform), one 8.04, one Mandriva2009-1 and 2 variations of 9.10.

As long as you are using an extended partition the only real limit is the size of your drive(s) and the amount of space you want each OS to have.

---

### Post by nitstorm on 2010-04-08
yeah my question was exactly that, if i could have more than one ubuntu on my machine :) great, will get down to it soon and post on how it went by tomorrow :) thanks guys :)

---

### Post by nitstorm on 2010-04-09
i put in open suse on the primary partition and then fedora on a logical, i got this error message 
no bootable device found - insert boot disk and press enter

i thought putting in ubuntu karmic and the grub2 will detect everything and sort the issue out , but even then i had the same error, so i put in lucid beta 2 and still the same error
now in a live cd session and tried running  *sudo update-grub,  *but this is the error i get
"[I]grub-probe: error: cannot find a device for /.  "

[/I]here is the output of my sudo fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe603e603

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20972826   83  Linux
/dev/sda2            2612       19456   135307432    5  Extended
/dev/sda5            2612        5222    20972826   83  Linux
/dev/sda6            5223        7833    20972826   83  Linux
/dev/sda7   *        7834       10444    20972826   83  Linux
/dev/sda8           10445       10705     2096451   82  Linux swap / Solaris
/dev/sda9           10706       10836     1052226   83  Linux
/dev/sda10          10837       19456    69240118+  83  Linux


```

sda1 - openSUSE
sda7 - fedora 12
sda6 - karmic
sda5 - lucid beta 2

this is the order i installed them in. 
Please help me boot !!!


P.S: there was a install bootloader option ticked by default during fedora installation and i just went ahead with it. is it the cause of this problem??? just wanted to let you know about it...

---

### Post by nitstorm on 2010-04-09
would this be solvable if i just remove fedora, i.e., delete its partition altogether????????

---

### Post by nitstorm on 2010-04-09
ok so i reinstalled fedora 12 on /dev/sda1 and so the bootloader is in a primary partition now but fedora 12 uses just grub by default, anyone want to help me update the grub in f12? anyone please????

i mean update to grub2????

---

### Post by nitstorm on 2010-04-09
Ok guys, I finally have understood multibooting, right now running two Lucids , one karmic and a fedora 12. didnt know how to upgrade from grub to grub2 on f12 so jus installed lucid there. 

Thanks everyone for ur help :D

---

### Post by ranch hand on 2010-04-09
I have been off line most of the day (problem with ISP server downtown).

There is no need to update grub in Fedora.  Fedora is just a bugger.  To boot to it you will probably need a custom menu entry for it.

I think there may be a working one in;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I have an install of Mandriva on here and os-prober now almost gets it right but not quite.  The custom entry does the job with no problem.  It is in the first post on the link in my sig.

---

### Post by oldfred on 2010-04-09
If you have grub2 as the standard in one of your partitions you just have to reinstall it like you would after a window boot loader overwrites it. Distributions with old grub can have grub installed to the partition and chainbooting will work but that becomes a custom entry.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by nitstorm on 2010-04-10
> 
I have been off line most of the day (problem with ISP server downtown).

No problem ranch hand , **** happens :P

> 
If you have grub2 as the standard in one of your partitions you just  have to reinstall it like you would after a window boot loader  overwrites it. Distributions with old grub can have grub installed to  the partition and chainbooting will work but that becomes a custom  entry.


earlier i had one primary partition with openSUSE on it and f12 jus shifted the bootloader to its partition a logical one, then i reinstalled f12 and then shifted the bootloader back to the primary partion, and then tried updating the grub legacy to grub2 and was unsuccessful thanks to all the hostile package mgmt tools of the rpm distros. (i have no clue about rpm packagin and all that, just started off with ubuntu roughly 3-4 months back, only been using ubuntu since then...)and i put in lucid beta2 on the primary partition to get me outta trouble.

here is my fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe603e603

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2549    20472656+  83  Linux
/dev/sda2            2612       19456   135307432    5  Extended
/dev/sda5            2612        5222    20972826   83  Linux
/dev/sda6            5223        7833    20972826   83  Linux
/dev/sda7            7834       10444    20972826   83  Linux
/dev/sda8           10445       10705     2096451   82  Linux swap / Solaris
/dev/sda9           10706       10836     1052226   83  Linux
/dev/sda10          10837       19456    69240118+  83  Linux

```
sda1 - Lucid Beta2
sda5 - Lucid Beta2
sda6 - Karmic
sda7 - F12
sda9 & sda10 - Storage

But I am not unhappy about all the failures coz I got to learn something :)
Thanks for all your help, especially  ranch hand and oldfred
THREAD SOLVED!

cheers guys :D

---

### Post by ranch hand on 2010-04-10
One handy tool that you need is here;

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It is handy for you to be able to run just to see what is up on your box.  When having a problem posting the entire results test file is a real help.

If you have everything working now I would run that script and save the results some where.  If you have trouble you can run it again (you can run it from the live CD if it is real bad) and compare the two and maybe pick up the problem yourself very easily.

A very cool script that you will see asked for in a lot of the boot problem threads.

The greatest gift to computing that the guy that came up with Debian gave was the .deb.  I really like Mandriva an PcLinuxOS (the gnome version) is pretty nice but the RPM package management is not really nice.  I don't really like Fedora or Suse as they have made the package management worse with the use of package kit.

Besides that, I am sure that you found you needed to really watch either of them to make sure they did not take over partitions used by your other Linux installs.

You should check out Debian and/or, I think better yet, PhatDebian (Lenny with the 2.6.30 kernel, it is ext3 but can see and read ext4).

---

### Post by nitstorm on 2010-04-10
Coool... Thanks for the info ranchhand will try out Debian and PhatDebia. Thanks a mil man :D

---

### Post by nitstorm on 2010-04-10
here is my bootinfoscript results if anyone was wondering and also give me some suggestions or advice for the next time.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 12 (Constantine) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe603e603

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,945,375    40,945,313  83 Linux
/dev/sda2          41,945,776   312,560,639   270,614,864   5 Extended
/dev/sda5          41,945,778    83,891,429    41,945,652  83 Linux
/dev/sda6          83,891,493   125,837,144    41,945,652  83 Linux
/dev/sda7         125,837,208   167,782,859    41,945,652  83 Linux
/dev/sda8         167,782,923   171,975,824     4,192,902  82 Linux swap / Solaris
/dev/sda9         171,975,888   174,080,339     2,104,452  83 Linux
/dev/sda10        174,080,403   312,560,639   138,480,237  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       343af808-9da1-4cb4-a39d-433bb9d8bbaa   ext4                                     
/dev/sda1        922e6f92-b6fa-4226-858c-ec94196021b6   ext4                                     
/dev/sda5        06e138a2-e42f-4207-aa23-b8a2f56e6401   ext4                                     
/dev/sda6        98959f16-78fc-45bd-980e-81490bed30c7   ext4                                     
/dev/sda7        a5d893f5-209e-462e-94ca-3195aacdeba8   ext4       Fedora-12-i686-L              
/dev/sda8        0dc51ee0-9432-44a6-9ca3-b9cacf5c9769   swap                                     
/dev/sda9        f61c5279-aae5-47b1-b7ee-24bc53a34036   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda10       /media/Storage           ext4       (rw)


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
search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
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
search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=922e6f92-b6fa-4226-858c-ec94196021b6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=922e6f92-b6fa-4226-858c-ec94196021b6 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 ro quiet splash
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 ro single
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a5d893f5-209e-462e-94ca-3195aacdeba8
    linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=a5d893f5-209e-462e-94ca-3195aacdeba8 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=922e6f92-b6fa-4226-858c-ec94196021b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0dc51ee0-9432-44a6-9ca3-b9cacf5c9769 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  17.5GB: boot/grub/grub.cfg
   2.2GB: boot/initrd.img-2.6.32-19-generic
   2.2GB: boot/vmlinuz-2.6.32-19-generic
   2.2GB: initrd.img
   2.2GB: vmlinuz

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,5)'
search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
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
set root='(/dev/sda,5)'
search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sda,5)'
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(/dev/sda,5)'
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(/dev/sda,5)'
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(/dev/sda,5)'
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "openSUSE 11.2 (on /dev/sda1)" {
    insmod ext2
    set root='(/dev/sda,1)'
    search --no-floppy --fs-uuid --set 45bb57d1-163f-452a-811f-cbe004259e43
    linux /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part1 resume=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part8 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.5-0.1-default
}
menuentry "Failsafe -- openSUSE 11.2 (on /dev/sda1)" {
    insmod ext2
    set root='(/dev/sda,1)'
    search --no-floppy --fs-uuid --set 45bb57d1-163f-452a-811f-cbe004259e43
    linux /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/disk/by-id/ata-ST3160215AS_5RA2WAB4-part1 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.5-0.1-default
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
    insmod ext2
    set root='(/dev/sda,6)'
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(/dev/sda,6)'
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/sda7)" {
    insmod ext2
    set root='(/dev/sda,7)'
    search --no-floppy --fs-uuid --set a5d893f5-209e-462e-94ca-3195aacdeba8
    linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=a5d893f5-209e-462e-94ca-3195aacdeba8 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0dc51ee0-9432-44a6-9ca3-b9cacf5c9769 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  23.7GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
  23.7GB: boot/initrd.img-2.6.32-19-generic
  23.7GB: boot/vmlinuz-2.6.32-19-generic
  23.7GB: initrd.img
  23.7GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 98959f16-78fc-45bd-980e-81490bed30c7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=98959f16-78fc-45bd-980e-81490bed30c7 ro single 
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=922e6f92-b6fa-4226-858c-ec94196021b6 ro quiet splash
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 922e6f92-b6fa-4226-858c-ec94196021b6
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=922e6f92-b6fa-4226-858c-ec94196021b6 ro single
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 ro quiet splash
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 06e138a2-e42f-4207-aa23-b8a2f56e6401
    linux /boot/vmlinuz-2.6.32-19-generic root=UUID=06e138a2-e42f-4207-aa23-b8a2f56e6401 ro single
    initrd /boot/initrd.img-2.6.32-19-generic
}
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a5d893f5-209e-462e-94ca-3195aacdeba8
    linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=a5d893f5-209e-462e-94ca-3195aacdeba8 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=98959f16-78fc-45bd-980e-81490bed30c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0dc51ee0-9432-44a6-9ca3-b9cacf5c9769 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sda10
UUID=343af808-9da1-4cb4-a39d-433bb9d8bbaa /media/Storage ext4 defaults 0 2


=================== sda6: Location of files loaded by Grub: ===================


  46.2GB: boot/grub/core.img
  46.2GB: boot/grub/grub.cfg
  44.6GB: boot/initrd.img-2.6.31-14-generic
  46.2GB: boot/initrd.img-2.6.31-20-generic
  44.5GB: boot/vmlinuz-2.6.31-14-generic
  45.0GB: boot/vmlinuz-2.6.31-20-generic
  46.2GB: initrd.img
  44.6GB: initrd.img.old
  45.0GB: vmlinuz
  44.5GB: vmlinuz.old

========================== sda7/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sda7
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,6)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.5-127.fc12.i686)
    root (hd0,6)
    kernel /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=a5d893f5-209e-462e-94ca-3195aacdeba8 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img

=============================== sda7/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Apr 10 05:28:23 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=a5d893f5-209e-462e-94ca-3195aacdeba8 /                       ext4    defaults        1 1
UUID=0dc51ee0-9432-44a6-9ca3-b9cacf5c9769 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


  66.5GB: boot/grub/grub.conf
  66.5GB: boot/grub/menu.lst
  65.6GB: boot/grub/stage2
  66.5GB: boot/initramfs-2.6.31.5-127.fc12.i686.img
  65.6GB: boot/vmlinuz-2.6.31.5-127.fc12.i686
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 81 00 00 e4 2d 00 00  72 f2 ca 4a 15 8f 47 4b  |.....-..r..J..GK|
00000010  72 f2 ca 4a 00 00 00 00  00 00 01 00 18 00 00 00  |r..J............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  03 00 00 00 f7 06 29 00  |..............).|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 a7 8e 9c c4  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 60 a4 60 5a  00 00 00 00 00 00 00 00  |....`.`Z........|
00000090  15 8f 47 4b 60 a4 60 5a  00 00 00 00 00 00 00 00  |..GK`.`Z........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 19 30 00 00  72 f2 ca 4a 15 8f 47 4b  |.....0..r..J..GK|
00000110  72 f2 ca 4a 00 00 00 00  00 00 01 00 20 00 00 00  |r..J........ ...|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  04 00 00 00 fa 06 29 00  |..............).|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 a8 8e 9c c4  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 bc 4a 73 5b  00 00 00 00 00 00 00 00  |.....Js[........|
00000190  15 8f 47 4b 60 a4 60 5a  00 00 00 00 00 00 00 00  |..GK`.`Z........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 34 0a 80 02 00 fe  |..........4.....|
000001d0  ff ff 05 fe ff ff 36 0a  80 02 73 0a 80 02 00 00  |......6...s.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by nitstorm on 2010-04-10
Now if I want to edit the names of the OS in the Grub, from where should i access it? /dev/sda1 or /dev/sda6 ( i am on sda6 right now)

---

### Post by ranch hand on 2010-04-10
You have the grub on sda6 doing the booting so that is where you need to be.

You will have to make a custom menu.  This is done usine the /etc/grub.d/40_custom as a template.

You make your entries and save the file as 06_custom (06,07,08 or 09).  The reason is that, if you look at your results test for the grub.cfg results, the scripts run in numeric order.  By putting the custom menu in as 06 puts it at the top of the screen menu.

An entry for debian based OS' looks like;
```

echo "Adding Daily on sda13" >&2 
cat << EOF
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet
        initrd /initrd.img
}
EOF

```
That is a symbolic entry that just calls for the most resent kernel on that partition.  I like them as they do not need updating.

If you want the same type entry as you are using now just copy/paste from your /boot/grub/grub.cfg file and ad the 2 top lines from mine and the EOF at the end.

You can edit the stuff between the "xxx" to anything you want.  The "echo" line is what you see in terminal when you run "update-grub".  The "menuentry" line is what you see on your screen menu.

There is some more info in the link in my sig and lots more at

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

As you know, it is easy in grub to change which installation is supplying the menu.  I change mine around to make sure they are working and to test different menu entries.  If you have the black background it is easy to forget where it is from.  I use the wallpaper from the OS supplying the menu as the menu background.

Just resize to 640x480 (format to .png), save to /usr/share/images/desktop-base, and edit the file name in 05_debian-theme.
```

else
  WALLPAPER="/usr/share/images/desktop-base/menu.png"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/black"
fi

```
The colors have been edited in my entry so that I can read the menu over my image.  Yes, I like a simple name on the image as I do not type that well.

---

### Post by oldfred on 2010-04-10
Besides the regular sites on grub2:

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)
ranch hand's custom grub2
[http://ubuntuforums.org/showthread.php?t=1284553](http://ubuntuforums.org/showthread.php?t=1284553)

---

### Post by nitstorm on 2010-04-26
Thanks for the help guys, thanks again ranchhand and oldfred , you guys are simply great :D 

Thread Solved! Cheers!

P.S: Sorry for the extremely late post.

---

