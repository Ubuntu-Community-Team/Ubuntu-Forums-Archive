---
title: "Problems with Dual Boot - Help Please"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by mikeody on 2010-12-26
I have just finished installing the Netbook Remix as a dual boot with Windows7 starter.
PC is Toshiba Netbook, 1.6 Atom, plenty of Hard Drive space.
The install appeared to go well - via bootable USB flash drive.
I accepted the suggested partition 'split'and made no changes to anything during the install.

Upon restart the GRUB menu item "Ubuntu Generic" gives me :
"Gave up waiting for root device.
Missing modules (cat /proc/modules ; 1s /dev)
ALERT /dev/disk/by-uuid/dbe1dd84-00e2-427a-bbc5-29ad6e3d6237 does not exist"

The other GRUB options vis 
"Windows 7 (loader) (ondev/sdb1)" boots Windows 7 OK.
"Windows 7 (loader) (on dev/sdb2)" also boots Windows 7 OK.

Can anyone help me please ? Thanks.

---

### Post by Quackers on 2010-12-26
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mikeody on 2010-12-26
Thanks Quackers,
Wow that was fun - I dont have ANY experience of that new swish desktop !


```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4089 MB, 4089446400 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7987200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,984,304     7,984,242   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sdb2           3,074,048   258,369,257   255,295,210   7 HPFS/NTFS
/dev/sdb3         472,444,928   488,396,799    15,951,872  17 Hidden HPFS/NTFS
/dev/sdb4         258,369,534   472,444,927   214,075,394   5 Extended
/dev/sdb5         258,369,536   466,302,975   207,933,440  83 Linux
/dev/sdb6         466,305,024   472,444,927     6,139,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C72-4A42                              vfat       NEW VOLUME                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3C2C05012C04B7C2                       ntfs       System                        
/dev/sdb2        BED02A95D02A5445                       ntfs       NETBOOK                       
/dev/sdb3        7CBE502FBE4FE06E                       ntfs       HDDRECOVERY                   
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        dbe1dd84-00e2-427a-bbc5-29ad6e3d6237   ext4                                     
/dev/sdb6        ad05a681-680c-46dd-a63d-2e04dca8b91c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dbe1dd84-00e2-427a-bbc5-29ad6e3d6237 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dbe1dd84-00e2-427a-bbc5-29ad6e3d6237 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 3c2c05012c04b7c2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set bed02a95d02a5445
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 7cbe502fbe4fe06e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=dbe1dd84-00e2-427a-bbc5-29ad6e3d6237 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ad05a681-680c-46dd-a63d-2e04dca8b91c none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 156.1GB: boot/grub/core.img
 158.3GB: boot/grub/grub.cfg
 154.0GB: boot/initrd.img-2.6.35-22-generic
 156.1GB: boot/vmlinuz-2.6.35-22-generic
 154.0GB: initrd.img
 156.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  fe ff ff 50 51 8b 8d 58  fe ff ff 51 ff 92 64 01  |...PQ..X...Q..d.|
00000010  00 00 8b 95 54 fe ff ff  83 c4 20 8b 8d 54 fe ff  |....T..... ..T..|
00000020  ff 8b bd 6c fe ff ff 8b  42 0c 8b 95 74 fe ff ff  |...l....B...t...|
00000030  29 d0 d9 bd 66 fe ff ff  50 66 8b 85 66 fe ff ff  |)...f...Pf..f...|
00000040  db 04 24 d8 0d e0 3e 63  62 b4 0c 66 89 85 64 fe  |..$...>cb..f..d.|
00000050  ff ff 83 ec 04 d9 ad 64  fe ff ff db 9d 60 fe ff  |.......d.....`..|
00000060  ff d9 ad 66 fe ff ff 8b  41 04 8b 95 60 fe ff ff  |...f....A...`...|
00000070  01 c2 8b 41 08 8b 8d 5c  fe ff ff 29 f8 83 e8 10  |...A...\...)....|
00000080  f6 45 18 04 8b 59 08 8b  7b f8 75 20 b9 01 00 00  |.E...Y..{.u ....|
00000090  00 51 6a 00 6a 00 52 50  57 53 6a 00 6a 00 56 e8  |.Qj.j.RPWSj.j.V.|
000000a0  bc bb 03 00 83 c4 30 e9  f4 fc ff ff b9 21 00 00  |......0......!..|
000000b0  00 f6 45 18 01 74 da eb  d3 83 ec 0c 51 e8 1e 9f  |..E..t......Q...|
000000c0  0c 00 83 c4 10 e9 01 fd  ff ff 8d 4d 88 6a 01 6a  |...........M.j.j|
000000d0  02 51 53 e8 a8 ab 0c 00  e9 e8 f8 ff ff c7 45 ac  |.QS...........E.|
000000e0  00 00 00 00 50 c6 45 b0  00 6a ff c7 45 a8 78 c2  |....P.E..j..E.x.|
000000f0  66 62 57 53 e8 77 80 fd  ff 8b 45 ac 83 c4 10 39  |fbWS.w....E....9|
00000100  45 8c 74 0f 8d 4d 88 50  50 53 51 e8 a0 5f 07 00  |E.t..M.PPSQ.._..|
00000110  83 c4 10 83 ec 0c 53 e8  64 75 fd ff 83 c4 10 e9  |......S.du......|
00000120  5e fa ff ff 8d b6 00 00  00 00 8d bf 00 00 00 00  |^...............|
00000130  55 89 e5 56 53 89 c6 83  ec 10 81 fa ff ff 00 00  |U..VS...........|
00000140  0f 94 c3 83 f8 01 0f 94  c0 20 d8 88 45 f7 75 14  |......... ..E.u.|
00000150  85 f6 0f 94 c0 20 c3 0f  85 9b 00 00 00 8d 65 f8  |..... ........e.|
00000160  5b 5e 5d c3 83 ec 0c a1  24 d9 69 62 c7 05 a8 b1  |[^].....$.ib....|
00000170  69 62 e4 3e 63 62 c7 05  ac b1 69 62 08 00 00 00  |ib.>cb....ib....|
00000180  c7 05 b0 b1 69 62 f0 63  4e 62 c7 05 b4 b1 69 62  |....ib.cNb....ib|
00000190  7c 10 6a 62 c7 05 b8 b1  69 62 00 00 00 00 a3 bc  ||.jb....ib......|
000001a0  b1 69 62 c7 05 24 d9 69  62 a8 b1 69 62 68 a8 b1  |.ib..$.ib..ibh..|
000001b0  69 62 e8 39 5d 07 00 83  c4 10 80 7d f7 00 00 fe  |ib.9]......}....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 64 0c 00 fe  |............d...|
000001d0  ff ff 05 fe ff ff 02 d0  64 0c 00 b8 5d 00 00 00  |........d...]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Your efforts are REALLY appreciated.

---

### Post by Quackers on 2010-12-26
Ok, thanks for that.
It's saying that the specified partition (the one with all the numbers) does not exist, whereas it is listed properly in your etc/fstab file. So it is there, but it can't find it for some reason.
Could you try something please?
Take out the flash drive and then reboot. When the grub menu appears and making sure that the Ubuntu......Generic line is highlighted, press the "e" key and a new screen will appear.
From that screen press ctrl + X and see if it then boots ok

---

### Post by mikeody on 2010-12-26
Hi again Quakers,
No, it hung with flashing cursor.
After a fair while I hit enter and got the same message as I got via the GRUB menu.

---

### Post by Quackers on 2010-12-26
I don't see anything wrong I'm afraid.
I could suggest that you re-install grub, but I don't know if that will fix it.
It could be that the file system needs checking on the Ubuntu system, but again, I'm not sure.
I would suggest leaving the thread open for others more experienced than me to offer advice.
Hang in there :-)

---

### Post by mikeody on 2010-12-26
Thanks Quackers for all your efforts - lets hope someone else can pick this one up ! 
I am a bit surprised at the problem though given I am not doing anything unexpected - just following the bouncing ball.
A question.
If it was an installation issue - how easy is it to wipe out the (broken) Ubuntu OS and try to do it all over again ?

---

### Post by Quackers on 2010-12-26
As I say, I really don't see anything wrong.
A re-install may fix it by virtue of the fact that the Ubuntu partition will be formatted and therefore get a new UUID number.
To re-install you would just boot from the live cd/usb and choose to install Ubuntu. Then, at the partitioning stage you would need to choose "specify manually" and then in the display of available partitions double-click on sdb5 (which may change to sda5, depending on what your flash drive is listed as).
You would then get a new box opening up and you would select ext4 as the format type (from the drop down menu), check the format box, select / as the mount point, leave the size the same and click on OK, then continue with the installation.

---

### Post by Herman on 2010-12-26
:D My suggestion is to try booting manually from the GNU/GRUB command line instead of just from your GRUB Menu, and then get updates.
Here's a link about how to boot manually from CLI Mode GRUB,  [GRUB How To Boot From CLI Mode.]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html")

Another way would be to chroot , [COLOR=#333333][How to chroot]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#chroot") - [/COLOR]use a Live CD or another Ubuntu installed in a hard disk or USB to fix  your GRUB, and get operating system updates, (sudo apt-get update, and sudo apt-get upgrade).
EDIT: Just apt-get update and apt-get upgrade because we don't need 'sudo' in chroot, I just remembered, sorry for my mistake.

I think operating system updates might fix it, I'm not sure, but your computer's symptoms remind me of something that happened to me once and that's what worked that time, so I'm just hoping the same will work again. 

Regards, Herman :)

---

### Post by Quackers on 2010-12-26
Aha! A timely visit Herman :-)
I must say I've not seen this type of error before.
I hope the OP gets to see your post before he re-installs.

---

### Post by mikeody on 2010-12-26
Have just reinstalled with EXACTLY the same message when booting 'generic' so will pursue Hermans idea [thanks Herman] - will report back.

---

### Post by coffeecat on 2010-12-26
I could be wrong - I often am :( - but I think I may have found the problem. When you boot from the live USB, it assigns itself the device descriptor sda and the internal drive sdb - as you can see from your bootscript. But when you try to boot from the hard drive without the USB, the HD becomes sda. Normally, a UUID (which is correct in your case) would get round this, but for this one little detail (from grub.cfg):

> **mikeody said:**
> ```

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='[COLOR=Red](hd1,msdos5)[/COLOR]'
    search --no-floppy --fs-uuid --set dbe1dd84-00e2-427a-bbc5-29ad6e3d6237
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dbe1dd84-00e2-427a-bbc5-29ad6e3d6237 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
```

(hd1,msdos5) is grubspeak for sdb5, but it needs to be sda5 = (hd0,msdos5). I know the UUID will be different now because you have reinstalled, but since you are getting the same problem, my guess is that you have the same hd1 instead of hd0 here. 

The answer would be to boot up with the live CD and edit grub.cfg where I've highlighted in red. This should enable you to boot from the HD. It's not normally considered OK to edit grub.cfg directly, but this is one of those rare occasions where it would be justifiable. If that gets you booting OK, all you then have to do is to run 'sudo update-grub' from the installed desktop and the problem will sort itself out.

Post back if you need help editing grub.cfg, because there are one or two little wrinkles you need to know about.

---

### Post by Quackers on 2010-12-26
That's well spotted sir! :-)

---

### Post by mikeody on 2010-12-27
Well folks, Netbook Remix [on a Toshiba Netbook] is a dirty word around here !
I tried my best to follow your last instructions but ended up totally confused !! Must be old age.
All I can tell you is that when I tried to boot using the GRUB console I ended up with virtually the same 'message' as before.
I began then to doubt the ISO on the flash drive, so I installed Netbook Remix on a spare hard drive on a desktop [using same flash drive]. It installed perfectly and interestingly without that 'new fangled' destop !
So back to the netbook.
I deleted Windows7 and set out [optimistically] to install Netbook Remix taking the whole of the 250GB - after all as I knew the ISO was good I thought I would have no problem without the complications of dual boot.
Wrong again ! Installation went all OK but as soon as I booted the generic kernel - guess what - the same message ! Toshiba doesnt like Ubuntu ?
So I will tinker a bit more but if I cannot get my Remix to boot I think I will put XP on the laptop - pity.
Thanks again.

---

### Post by mikeody on 2010-12-27
Have only just spotted coffecat post.
Will follow up and post.

---

### Post by mikeody on 2010-12-28
An update.
Remix is still not booting. Have tried to follow everyones kind advice but have had no joy as yet - a combination I think of genuine 'the fix wont work for me' and my general lack of command line knowledge.
Its ironic that the Remix installs perfectly [and quickly] on a desktop [from same flash drive], and 10.04 desktop installs perfectly [but slowly] on the Netbook [also from a flash drive] !
I was thinking I might keep the desktop version on the netbook but boot was taking [without exaggeration] 8 minutes !!
I tried some recommended boot speed-up fixes [involving a profile] but after that it wouldnt boot at all ! Not my day.
Am currently downloading Netbook Remix 9.10 to see if I can get that to work. If it does I will download updates and settle for that.
Will post again.

---

