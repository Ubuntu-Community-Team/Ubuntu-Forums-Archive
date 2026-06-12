---
title: "Fix the process after choosing windows boot in grub2"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by christiaanb on 2010-06-09
I need help Please!

I have a dell Inspiron 5150. I had perfect windows XP home installation, and decided to dual boot with Ubunutu 10.04.

I copied the whole C:/ to external drive, installed ubuntu, installed windows, repaired Grub2, but now, Grub2 looks something like this.

Linux   ...
Linus (recovery)   ...
Memtest ...
XP - Work (/dev/sda3)

I can go to ubuntu fine, but as soon as I select the windows installation, I only get a blinking cursor at the left top corner.

I need XP to work...

I have google'd all day yesterday, and tried loads of processes, no success.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x138a1389

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              18       10949    87809025    5  Extended
/dev/sda3   *       10950       30401   156248190    7  HPFS/NTFS
/dev/sda5              18         309     2343750   82  Linux swap / Solaris
/dev/sda6             310        2741    19529728   83  Linux
/dev/sda7            2741       10949    65934336   83  Linux
```


What else can I post here?

the boot.ini on windows looks like this:


```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP - Work" /noexecute=optin /fastdetect 1
```


Another question, ubuntu sees the windows partition as /dev/sda3, but the partition in boot.ini is partition 1. Is that even related?

Help will be grately appreciated!

Thanks!
Christiaan

---

### Post by bcbc on 2010-06-09
Not sure what happened to your /dev/sda1 !? But anyway, I imagine that windows will see /dev/sda3 as the second partition and since it's a zero based index, partition 1 is correct.

Ideally you should install XP first, then Ubuntu.

Why don't you post the results of the [bootinfoscript]("bootinfoscript.sourceforge.net/"). That might help.

---

### Post by christiaanb on 2010-06-09
Hi bcbc,

Thanks for the quick reply.

Here are the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2             276,478   175,894,527   175,618,050   5 Extended
/dev/sda5             276,480     4,963,979     4,687,500  82 Linux swap / Solaris
/dev/sda6           4,964,352    44,023,807    39,059,456  83 Linux
/dev/sda7          44,025,856   175,894,527   131,868,672  83 Linux
/dev/sda3    *    175,895,685   488,392,064   312,496,380   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda3        1F44129B41115450                       ntfs       Work                          
/dev/sda5        52a4f117-13b4-4a93-8a9e-68ecf07bc540   swap                                     
/dev/sda6        998c03f3-d367-4f08-9225-4bf8e27d59bf   ext4                                     
/dev/sda7        df9b29b7-4ada-4f24-9714-b50a7cdbe1e1   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sda3        /media/Work              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 998c03f3-d367-4f08-9225-4bf8e27d59bf
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
search --no-floppy --fs-uuid --set 998c03f3-d367-4f08-9225-4bf8e27d59bf
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 998c03f3-d367-4f08-9225-4bf8e27d59bf
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=998c03f3-d367-4f08-9225-4bf8e27d59bf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 998c03f3-d367-4f08-9225-4bf8e27d59bf
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=998c03f3-d367-4f08-9225-4bf8e27d59bf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 998c03f3-d367-4f08-9225-4bf8e27d59bf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 998c03f3-d367-4f08-9225-4bf8e27d59bf
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "XP - Work (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 1f44129b41115450
	drivemap -s (hd0) ${root}
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
# / was on /dev/sda6 during installation
UUID=998c03f3-d367-4f08-9225-4bf8e27d59bf /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=df9b29b7-4ada-4f24-9714-b50a7cdbe1e1 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=52a4f117-13b4-4a93-8a9e-68ecf07bc540 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  19.9GB: boot/grub/core.img
   4.9GB: boot/grub/grub.cfg
  20.0GB: boot/initrd.img-2.6.32-21-generic
  20.0GB: boot/vmlinuz-2.6.32-21-generic
  20.0GB: initrd.img
  20.0GB: vmlinuz

================================ sda3/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP - Work" /noexecute=optin /fastdetect 1
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b5 fc ac fc 9e fc 78 fc  4e fc 1f fc 02 fc f6 fb  |......x.N.......|
00000010  fc fb 14 fc 3d fc 74 fc  b5 fc 05 fd 60 fd c1 fd  |....=.t.....`...|
00000020  14 fe 62 fe 9d fe cb fe  f0 fe 16 ff 3d ff 6b ff  |..b.........=.k.|
00000030  ac ff fd ff 65 00 e8 00  69 01 01 02 af 02 53 03  |....e...i.....S.|
00000040  05 04 bf 04 85 05 4e 06  1f 07 10 08 0e 09 36 0a  |......N.......6.|
00000050  7f 0b f0 0c 81 0e 39 10  13 12 05 14 0d 16 24 18  |......9.......$.|
00000060  44 1a 65 1c 74 1e 69 20  33 22 d7 23 4d 25 81 26  |D.e.t.i 3".#M%.&|
00000070  70 27 0d 28 61 28 65 28  11 28 70 27 97 26 91 25  |p'.(a(e(.(p'.&.%|
00000080  87 24 8e 23 a9 22 ea 21  63 21 2a 21 43 21 b7 21  |.$.#.".!c!*!C!.!|
00000090  93 22 dd 23 c3 25 2d 28  1c 2b ab 2e c2 32 5e 37  |.".#.%-(.+...2^7|
000000a0  49 3c 7d 41 da 46 26 4c  00 51 e4 54 bd 57 38 59  |I<}A.F&L.Q.T.W8Y|
000000b0  43 59 aa 57 3d 54 c2 4e  01 47 a9 3c df 2f 95 20  |CY.W=T.N.G.<./. |
000000c0  89 0f 38 fd 17 eb 02 da  66 ca c5 bc f6 b0 68 a7  |..8.....f.....h.|
000000d0  fc 9f ab 9a 60 97 f0 95  0f 96 68 97 b5 99 cb 9c  |....`.....h.....|
000000e0  68 a0 69 a4 9d a8 d3 ac  20 b1 53 b5 82 b9 94 bd  |h.i..... .S.....|
000000f0  89 c1 6c c5 2c c9 de cc  60 d0 c2 d3 f5 d6 09 da  |..l.,...`.......|
00000100  06 dd cf df 79 e2 ed e4  38 e7 44 e9 1d eb cc ec  |....y...8.D.....|
00000110  5c ee de ef 53 f1 ca f2  2d f4 7b f5 c5 f6 f1 f7  |\...S...-.{.....|
00000120  09 f9 04 fa e6 fa ab fb  54 fc ec fc 62 fd c5 fd  |........T...b...|
00000130  0e fe 36 fe 50 fe 58 fe  56 fe 4c fe 41 fe 32 fe  |..6.P.X.V.L.A.2.|
00000140  23 fe 14 fe 16 fe 14 fe  12 fe f9 fd d8 fd af fd  |#...............|
00000150  79 fd 40 fd ff fc bc fc  7b fc 39 fc 00 fc d8 fb  |y.@.....{.9.....|
00000160  bd fb bc fb ca fb ee fb  28 fc 6c fc b2 fc ff fc  |........(.l.....|
00000170  4d fd 9b fd e0 fd 26 fe  6b fe b7 fe 0e ff 6c ff  |M.....&.k.....l.|
00000180  d4 ff 45 00 dc 00 6b 01  04 02 aa 02 59 03 11 04  |..E...k.....Y...|
00000190  ca 04 75 05 27 06 db 06  9e 07 68 08 46 09 40 0a  |..u.'.....h.F.@.|
000001a0  5a 0b 9b 0c 00 0e 88 0f  3a 11 09 13 f7 14 f0 16  |Z.......:.......|
000001b0  f9 18 02 1b 06 1d f8 1e  ca 20 7b 22 f3 23 00 35  |......... {".#.5|
000001c0  25 11 82 fd 55 34 02 00  00 00 8c 86 47 00 00 00  |%...U4......G...|
000001d0  41 35 05 fe ff ff f7 86  47 00 0b 01 54 02 00 00  |A5......G...T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```






Hope this means anything to you!


Oh yea, about the /dev/sda1, When I installed Ubuntu, i followed a guide that suggested to create a boot partition, so I did, but it didn't work, so i deleted it... sorry if i shouldn't have. But my ubuntu installation is working fine... just can't get to XP.

---

### Post by John Bean on 2010-06-09
You have a very odd set of partitions there, but crucially they're all extended not primary. XP will not boot from anything but a primary partition.

I'm at a loss to understand why you did this, since simply adding Ubuntu to the existing XP installation would have done the job without breaking anything. I'm even more puzzled how you installed XP in an extended partition anyway since the XP installer only offers primary partitions.

---

### Post by christiaanb on 2010-06-09
Okay, i'm sorry. I think all that was done just through a lack of understanding...

I installed ubuntu following a thread that explained how to create all the separate partitions, then i just copied the XP installation back to the free space, sudo grub update, and wham... problem...

I did not want to reinstall windows, since i use it for work, and don't want to re-register all the applications...

Is there a way to do that? I still have the whole c:/ of my windows installation on an external hard drive. Is there a way to just wipe it and redo it?

Also, i struggled all day yesterday to get the ubuntu 10.04 to connect to the wireless connection, and don't want to do that again either...

Yelp me please... what can/should i do? What is your suggestion?

---

### Post by bcbc on 2010-06-09
I can't see anything wrong with the windows, e.g. the boot files look good and the bootsector looks normal. But I can't understand why your partition table starts with partition2. What happened to the first 275000 sectors?

Looking at this ...> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "XP - Work (on /dev/sda3)" {
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 1f44129b41115450
drivemap -s (hd0) ${root}
chainloader +1
} ... I wonder whether grub is seeing /dev/sda3 as (hd0,3) or as (hd0,2).

You could try booting, select the windows entry and hit 'e' to edit, then change it to (hd0,2) and press CTRL-X to boot.

You could hit 'c' instead and type ls (lower case LS) at the grub prompt ```
grub> ls 
``` and see whether you get (hd0,1) in which case it probably does need to be (hd0,2).

You could also install the windows bootloader, and see if it can boot windows - it just looks for the partition with the boot flag set. If that doesn't work, then grub isn't going to do a better job.

PS go back and edit your post with the bootinfoscript (click edit, click "go advanced", highlight the full result and click the '#' button above to enclose the text in [[SIZE="1"] [/SIZE]CODE][/CODE] tags (it makes it more readable).

---

### Post by christiaanb on 2010-06-09
Thanks for the advice about CODE tags, i didn't know how to do that... newbie here...

```
grub> ls
(hd0 (hd0,7) (hd0,6) (hd0,5) (hd0,3)
```

and changing the (hd0,3) to (hd0,2) did not do anything...

I have a question, is there a way I can start from scratch, install XP, install Ubuntu, and then in ubuntu, not to have to reinstall stuff like the ndiswrapper, and wireless drivers? I need to work, and I work on XP...

---

### Post by bcbc on 2010-06-09
Hold on, did you ever boot windows successfully after installing? I suppose you could also try editing the boot.ini file and set the partition to 2 (i.e. the 3rd)... but odds are you are going to have ongoing problems.

By the way, it looks to me like /dev/sda3 is in fact a primary partition. I still want to know what happened to /dev/sda1 though :)

Anyway - it's late here. Good luck. I recommend redoing it all - it's the figuring out of how to get something working (the wireless) that takes time - then you make notes, and the next time it's painless. (That's what I do anyway)

---

### Post by bcbc on 2010-06-09
> **christiaanb said:**
> Thanks for the advice about CODE tags, i didn't know how to do that... newbie here...

```
grub> ls
(hd0 (hd0,7) (hd0,6) (hd0,5) (hd0,3)
```

and changing the (hd0,3) to (hd0,2) did not do anything...

I have a question, is there a way I can start from scratch, install XP, install Ubuntu, and then in ubuntu, not to have to reinstall stuff like the ndiswrapper, and wireless drivers? I need to work, and I work on XP...

Why don't you try editing the boot.ini (from ubuntu). I don't recommend this sort of thing, but hey if you can get it booting at least you can work tomorrow while you figure out your recovery options.

Regarding ndiswrapper - that all depends on the wireless card you have. I need ndiswrapper for one of my computers, but not the other. It works fine so it doesn't bother me. Go to the networking section of the forum - they have some good threads there on getting wireless to work (and the right people to help).

Edit: If you start from scratch, first setup your partitions, then install/copy your xp and make sure it works. Then install ubuntu and then grub2 should be able to boot both OS's without any extra work.

---

### Post by christiaanb on 2010-06-09
bcbc, thanks for your help! I appreciate it!

About the first partition, I followed a thread that said i had to make a boot partition. I did, and when i went back into disk utility, it showed it as a black partition, so i deleted it, and it didn't seem to make any difference on my system... that's what happened.

Okay, I think I'll redo the whole thing. thanks for all your help!
Sleep well!

---

### Post by christiaanb on 2010-06-09
Okay, after a looong day, and reinstallation of Windows XP, then installing Ubuntu 10.04 to the default location, and rebooting as the promt requested, i get to:

```
grub rescue>
```

There is no option to boot any OS... what now?

---

### Post by darkod on 2010-06-09
I'm starting to think that during reinstall of ubuntu not always grub2 on the MBR is reinstalled too. So if this is correct, the message means you have the old grub2 looking for its now not existing files any more. :)

From live mode can you run again:

sudo fdisk -l (small L)

to see the partitions, and we'll try reinstalling grub2 to the MBR.

---

### Post by christiaanb on 2010-06-09
ok thanks for your message. Out of pure frustration I booted into xp recovery mode, and used

fixboot
fixmbr
fixboot

and now I'm back in my XP. I really wanted to use the Grub2 because of the modifications one can use.

Is there a way to add the existing ubuntu installation to the boot.ini of XP?

Thank you!

---

### Post by darkod on 2010-06-09
There is, but it's more complicated than letting grub2 be the main bootloader. Plus for XP not even sure it can work, I know it can from Vista onwards.

Frustration doesn't lead you anywhere. Post the output of fdisk and lets try to reinstall grub2 to the MBR. You can always restore windows bootloader back as you already did.

---

### Post by christiaanb on 2010-06-09
I know... I'm sorry... I'm booted back into the live CD, and here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa77ba77b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18115   145502981+   7  HPFS/NTFS
/dev/sda2           18115       30402    98695169    5  Extended
/dev/sda5           18115       30028    95689728   83  Linux
/dev/sda6           30028       30402     3004416   82  Linux swap / Solaris
```

---

### Post by darkod on 2010-06-09
OK, from live mode in terminal do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and you should see grub2. The windows entry might not work the first time, boot into ubuntu and run in terminal:

sudo update-grub

because you reinstalled XP, to figure it out.

---

### Post by christiaanb on 2010-06-09
Hi there, sorry, just went for dinner...

Tried it, still no luck. Just gets to the

```
error: no such partition.
grub rescue>
```

---

### Post by darkod on 2010-06-09
Download and run the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of the results file as explained. Lets see more details of what you've got.

---

### Post by christiaanb on 2010-06-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   291,006,025   291,005,963   7 HPFS/NTFS
/dev/sda2         291,006,462   488,396,799   197,390,338   5 Extended
/dev/sda5         291,006,464   482,385,919   191,379,456  83 Linux
/dev/sda6         482,387,968   488,396,799     6,008,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1820F70620F6EA20                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c6b00636-c1fa-489f-bb05-0897adf6c2cd   ext4                                     
/dev/sda6        aa8257c2-d09a-4ebf-a8f5-bfd2c6c89d7e   swap                                     
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

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c6b00636-c1fa-489f-bb05-0897adf6c2cd
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c6b00636-c1fa-489f-bb05-0897adf6c2cd
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c6b00636-c1fa-489f-bb05-0897adf6c2cd
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c6b00636-c1fa-489f-bb05-0897adf6c2cd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c6b00636-c1fa-489f-bb05-0897adf6c2cd
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c6b00636-c1fa-489f-bb05-0897adf6c2cd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c6b00636-c1fa-489f-bb05-0897adf6c2cd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c6b00636-c1fa-489f-bb05-0897adf6c2cd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 1820f70620f6ea20
	drivemap -s (hd0) ${root}
	chainloader +1
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
UUID=c6b00636-c1fa-489f-bb05-0897adf6c2cd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aa8257c2-d09a-4ebf-a8f5-bfd2c6c89d7e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 244.0GB: boot/grub/core.img
 153.6GB: boot/grub/grub.cfg
 149.8GB: boot/initrd.img-2.6.32-21-generic
 244.3GB: boot/vmlinuz-2.6.32-21-generic
 149.8GB: initrd.img
 244.3GB: vmlinuz
```

---

### Post by darkod on 2010-06-09
Hmmm... it looks fine.

You can't boot anything or you can't boot XP when you try? Does it show the grub menu at all or immediately just the rescue prompt?

---

### Post by christiaanb on 2010-06-09
It just goes straight to the grub rescue>   it doesn't show any grub menu whatsoever...

---

### Post by bcbc on 2010-06-09
Try the following from the grub prompt:

```
configfile (hd0,5)/boot/grub/grub.cfg
```

If not, hopefully you'll see some error information.

---

### Post by christiaanb on 2010-06-09
Sorry man,

ls prevails (hd0) (hd0,1)

when i tried :  configfile (hd0,1) /boot/grub/grub.cfg

unknown command 'configfile'

---

### Post by christiaanb on 2010-06-09
I tell you what, I'm going to restore my windows installation, and get my apps running for work. Thanks for your time, but it is taking too long right now.

Will try it another day.

Thanks again!

---

### Post by darkod on 2010-06-09
> **christiaanb said:**
> Sorry man,

ls prevails (hd0) (hd0,1)

when i tried :  configfile (hd0,1) /boot/grub/grub.cfg

unknown command 'configfile'

It can't see the other two partitions on the disk. That's why the error message, can't find the config files. I have no idea why it doesn't see the partitions though. The results file looks fine as far as I can see. I suspect the partition table is corrupted.

From one of your earlier posts:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, [COLOR=Red]30401[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa77ba77b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18115   145502981+   7  HPFS/NTFS
/dev/sda2           18115       [COLOR=Red]30402[/COLOR]    98695169    5  Extended
/dev/sda5           18115       30028    95689728   83  Linux
/dev/sda6           30028       [COLOR=Red]30402[/COLOR]     3004416   82  Linux swap / Solaris
```

The disk has 30401 cylinders but the extended partition seems to finish at 30402.

---

### Post by christiaanb on 2010-06-09
Okay, i just fixboot'ed and fix MBR again, and now i'm back in windows again.

Thank you for your help.

Is there a way to fix the partition table, and then add ubuntu to the boot.ini of windows xp??

---

### Post by darkod on 2010-06-09
> **christiaanb said:**
> Okay, i just fixboot'ed and fix MBR again, and now i'm back in windows again.

Thank you for your help.

Is there a way to fix the partition table, and then add ubuntu to the boot.ini of windows xp??

I don't really know what to recommend. Since the ubuntu install is new, and you still don't have any important data in it, I would boot up in live mode, open Gparted and delete /dev/sda6, /dev/sda5 and /dev/sda2.
Then I would boot up with the cd again and started the installer process and tell it to use Use Largest Available Free space option. Hopefully this time the partitions will be created correctly.

However, having said that, you just reinstalled ubuntu and I can't explain why the extended partition seems created wrongly, ending one cylinder beyond the possible number.

---

