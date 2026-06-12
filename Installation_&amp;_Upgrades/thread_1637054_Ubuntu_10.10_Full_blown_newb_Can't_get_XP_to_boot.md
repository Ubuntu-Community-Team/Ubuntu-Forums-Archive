---
title: "Ubuntu 10.10 Full blown newb Can't get XP to boot"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Tron22 on 2010-12-03
Alright guys, 

I've searched through tons of posts but I can't find anything that will work and is specific for me.

I have recently jumped into the world of Ubuntu.  I am a complete noob and know nothing.  

I have set up a dual boot xp/ubuntu.  Love ubuntu and am learning the new system.   I installed it using an iso file to Live DVD.  Everything in ubuntu seems to work perfect.

 I restart my computer and it gets to the boot screen where i can select a 4 ubuntu boots(2 being safe modes), 2 memory boots, or the xp boot.  Ubuntu boots fine.  I select XP and I get a blank screen with the cursor blinking in the upper left corner.. the only thing I can do is control+alt+delete to restart and get back to the main boot screen.  

Did Ubuntu kill windows in good taste? kidding.. But seriously if anyone can help me figure out how to get my windows working again... I would make them feel good by telling them how much I love them and how much they have helped me.  Let me know what you need to know/see and don't leave out pathways and how to do everything!  

Hopefully your out there hero....My hero.  

Love you Linuxers,

Tron22 (supernewb)

---

### Post by oldfred on 2010-12-04
Welcome to the forum.

We need to see if something is missing or installed in the wrong place. Normally grub's osprober does not even add a windows entry if it is too messed up. Or it could just be windows issues.

Lets run this script to see what is installed where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Tron22 on 2010-12-04
Alright think i got this.. Here is the info you asked for ... iiii think.



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   632,260,169   632,260,107   7 HPFS/NTFS
/dev/sda2         632,260,606   976,771,071   344,510,466   5 Extended
/dev/sda5         632,260,608   964,485,119   332,224,512  83 Linux
/dev/sda6         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        12E83321E8330291                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2dc6d6c5-1621-4b9f-9a37-0c536d974b9d   ext4                                     
/dev/sda6        c2ca94af-f6f8-484b-bba9-58e9e90f5fd7   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=2dc6d6c5-1621-4b9f-9a37-0c536d974b9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=2dc6d6c5-1621-4b9f-9a37-0c536d974b9d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc6d6c5-1621-4b9f-9a37-0c536d974b9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2dc6d6c5-1621-4b9f-9a37-0c536d974b9d ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 2dc6d6c5-1621-4b9f-9a37-0c536d974b9d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 12e83321e8330291
    drivemap -s (hd0) ${root}
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
UUID=2dc6d6c5-1621-4b9f-9a37-0c536d974b9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c2ca94af-f6f8-484b-bba9-58e9e90f5fd7 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 426.9GB: boot/grub/core.img
 401.2GB: boot/grub/grub.cfg
 324.6GB: boot/initrd.img-2.6.35-22-generic
 323.9GB: boot/initrd.img-2.6.35-23-generic
 426.9GB: boot/vmlinuz-2.6.35-22-generic
 426.9GB: boot/vmlinuz-2.6.35-23-generic
 323.9GB: initrd.img
 324.6GB: initrd.img.old
 426.9GB: vmlinuz
 426.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  03 6a a4 da 92 f4 e0 59  6b 55 61 19 34 bd 0d a6  |.j.....YkUa.4...|
00000010  55 49 b1 3f 83 5c 82 3e  ec 63 51 34 fe 1b 0c 07  |UI.?.\.>.cQ4....|
00000020  6d 24 cd 87 ce 8e 2c b5  ea e2 94 f9 06 d2 43 7a  |m$....,.......Cz|
00000030  c8 47 10 a2 a8 c1 d8 ad  26 f4 9a d5 3e 00 64 81  |.G......&...>.d.|
00000040  0b 77 8f d9 1e 40 e1 dc  18 c0 3f 09 ff 59 74 68  |.w...@....?..Yth|
00000050  66 8a 8b 51 61 6a 00 3f  40 80 95 57 49 55 53 52  |f..Qaj.?@..WIUSR|
00000060  f9 f3 e7 b5 df 3e 7c fd  2b e7 b0 dd 3e ad 87 61  |.....>|.+...>..a|
00000070  bd af 0a 1a 97 d0 9d 56  75 49 2b b8 36 df aa 73  |.......VuI+.6..s|
00000080  59 f4 37 b5 d7 ba a5 72  0c 3a fa 21 42 ad 4e 94  |Y.7....r.:.!B.N.|
00000090  27 d4 d2 ad af 59 4c 39  d0 9f 42 55 db 65 55 ab  |'....YL9..BU.eU.|
000000a0  a9 86 f9 32 a4 d5 92 d3  42 9a ae fa 6a 9f 56 74  |...2....B...j.Vt|
000000b0  fd 52 a5 6d 9e dc ae ba  be ba f0 d4 d6 a7 0a 75  |.R.m...........u|
000000c0  2a 4f d2 be 7e 95 f3 da  ef 95 f9 00 8b ea 69 63  |*O..~.........ic|
000000d0  c2 7c 75 5d 27 4f 9c bb  83 71 39 24 2f 5f a6 83  |.|u]'O...q9$/_..|
000000e0  6e 15 35 50 a1 5d 55 5d  f3 e7 b0 ab bf 4c e5 f3  |n.5P.]U].....L..|
000000f0  e7 d4 9d 2e 7c f9 f5 27  de c9 55 5d 4c 28 0e 2b  |....|..'..U]L(.+|
00000100  bd a6 ba 72 a8 4f 9f 43  29 0a e2 64 aa 6d bd 87  |...r.O.C)..d.m..|
00000110  49 f5 2d 5a ee 2e a4 e9  cd 77 d3 9c d6 ae fd 2d  |I.-Z.....w.....-|
00000120  67 cf 9f 26 7c f9 f7 b2  55 43 53 09 fd 1a ef a9  |g..&|...UCS.....|
00000130  42 9c ba 1a 65 4f 96 c2  b6 e9 52 58 54 ab d2 85  |B...eO....RXT...|
00000140  60 aa 9e 2d 5f b9 86 a6  32 a7 cf 9f a4 90 96 13  |`..-_...2.......|
00000150  9a ef d0 aa 87 ff ce b9  6f 4c 20 40 81 02 04 09  |........oL @....|
00000160  00 e2 3d ad 45 9c 1b be  76 d7 e5 09 24 fc 5d 14  |..=.E...v...$.].|
00000170  10 53 6d e3 ef 04 d0 56  30 b8 f4 48 50 0f 5e 08  |.Sm....V0..HP.^.|
00000180  3a 02 f7 9e fa 7d 01 a3  de 75 c9 26 80 a2 7c 40  |:....}...u.&..|@|
00000190  f4 50 02 0f c0 8b e2 da  fb e0 23 1f b5 ba 69 61  |.P........#...ia|
000001a0  3d a7 f8 f7 37 35 2d d1  f1 e9 71 2a 39 f9 ae 08  |=...75-...q*9...|
000001b0  48 05 29 ac ad f3 31 c5  8d e6 0e e0 20 88 00 fe  |H.)...1..... ...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 58 cd 13 00 fe  |...........X....|
000001d0  ff ff 05 fe ff ff 02 58  cd 13 00 78 bb 00 00 00  |.......X...x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Parlek on 2010-12-04
posted in error

---

### Post by wilee-nilee on 2010-12-04
@Tron22, was a chkdsk run after the Ubuntu install, generally XP will want one, ant MS really.?

Did you use the install partitioner to install side by side?

Has XP ever booted after the install?

Do you have a XP CD, to initiate a chkdsk?

Have you tried the f8 prompt to get to a safe mode?

---

### Post by Tron22 on 2010-12-04
mmm no chkdsk was run, no cd

believe partitioned side by side.

will try F8

---

### Post by Tron22 on 2010-12-04
Nope F8 did not work
and no I have not seen XP since installing ubuntu... not the best first exp.

---

### Post by wilee-nilee on 2010-12-04
> **Tron22 said:**
> Nope F8 did not work
and no I have not seen XP since installing ubuntu... not the best first exp.

Well just so happens I have a XP link.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Follow these directions to get to the repair command line and run chkdsk /r
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

This is a instruction to the command line for another problem the bootloader but we want the chkdsk run instead.

Also make sure you run in the Ubuntu install, in a terminal this command it may be all you need to begin with but it should be run all through the process whenever you in the Ubuntu install. If you never had a chkdsk that is probably the culprit here.
```
sudo update-grub
```

---

### Post by Tron22 on 2010-12-04
does it matter if I have xp pro?

---

### Post by Tron22 on 2010-12-04
> Follow these directions to get to the repair command line and run chkdsk /r
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

This is a instruction to the command line for another problem the bootloader but we want the chkdsk run instead.

Also make sure you run in the Ubuntu install, in a terminal this command  it may be all you need to begin with but it should be run all through  the process whenever you in the Ubuntu install. If you never had a  chkdsk that is probably the culprit here.

Also.... IIIIII don't get it. I'm not running the fixmbr right?

---

### Post by wilee-nilee on 2010-12-04
> **Tron22 said:**
> does it matter if I have xp pro?

No your just starting a chkdsk, it will probably say disc mounted can't run , do you want one at next start say yes and hopefully it will happen. This is not just a shot in the dark this is standard procedure, just so you know.;)

Windows has unmovable files in its partition when you let them get moved with another partitioner a chkdsk is run automatically. Really any windows resizing should be done then checked to be a still working system before install another.

---

### Post by wilee-nilee on 2010-12-04
> **Tron22 said:**
> Also.... IIIIII don't get it. I'm not running the fixmbr right?

No, no fixmbr, you just need to at that command screen type chkdsk /r

The link was to show you how to get to that terminal screen to run the chkdsk.

---

### Post by Tron22 on 2010-12-04
Okay, I think i Got it.

Just get to where i would do the mbr fix but instead run chkdsk.  1 moment.

---

### Post by Tron22 on 2010-12-04
FML, can't figure out my admin password.

---

### Post by wilee-nilee on 2010-12-04
> **Tron22 said:**
> FML, can't figure out my admin password.

[COLOR="Sienna"]I think you don't need one if it is running in the hidden admin. Try to just hit enter when the password is asked for.[/COLOR]

All windows setups have a hidden admin that you don't ever see in logins without a key prompt or in safe mode or looking at the users.

This one has no password unless you even knew about it, you would have to make one, this hidden admin is not in the guest area either.

Could be the admin password for the regular account as well, do you not remember it.

---

### Post by Tron22 on 2010-12-04
no idea... going to try and reset it.

---

### Post by Tron22 on 2010-12-04
I did it! 4 hours later and I ran chkdsk!!

moment of truth... I think at least?  XP is supposed to work now? No idea if that's the step we're at... but i'll try.. moment of truth for me!! muhahaha

---

### Post by Tron22 on 2010-12-04
Faiiiil.. XP still fails to boot.. Black screen.. blinking cursor.

What can I do now?

---

### Post by wilee-nilee on 2010-12-04
> **Tron22 said:**
> Faiiiil.. XP still fails to boot.. Black screen.. blinking cursor.

What can I do now?

You have run the 
sudo-update-grub command in Ubuntu correct.

You could also from that disc you dowloaded and put the MS bootloader back in the mbr and see if XP boots from that. Reloading the grub bootloader is easy.


To reload the mbr just follow that link and run the /fixmbr command this will put the ms booloader in.
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If that doesn't work getting into XP then you can reload grub just follow this links instructions. Notice that there are only three commands needed and run from the Ubuntu cd booted in a live mode. The first command is just to identify the partitions so you can run the other two to reload grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

It also wouldn't hurt to post tyhe script again the chkdsk may have changed something it would help to know.

I have op crash soon but during the day US time more people with help might be available.

---

### Post by Tron22 on 2010-12-04
Alright.... Fixmbr ran.  Computer now freezes if and doesn't even get to the boot up screen.  Just shows a club an L, a bracket, and a music symbol spaced out diagonally across the screen.  The only way to access my computer now is the ubuntu live cd or the xp cd to get into the windows c...... Am I f$;?Ed?

---

### Post by Tron22 on 2010-12-04
All I want is my xp back.  I'll merge all my partitions.  And start over

---

### Post by oldfred on 2010-12-04
Did chkdsk report any errors? If so you have to rerun it until you have no errors as it does not fix everything on one pass.

The fixMBR puts the windows boot loader into the MBR to directly boot windows. If it does not boot that is a windows issue.

From the windows CD you can refresh all the XP boot files.
FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by Tron22 on 2010-12-04
Yes I can still get into ubuntu.

I ran fix Mbr and also fixboot

The cd drive ones couldn't be found. But I don't know if I'm entering them right either.  How do I mount windows?  All I want is windows then I'll start over.

---

### Post by Tron22 on 2010-12-04
>  If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild

yah.. no idea how to do this.

---

### Post by Tron22 on 2010-12-04
okay i'm not sure how to tell if windows is "mounted".. but i've found ntldr and ntdetect.com how do i copy them to root?

---

### Post by oldfred on 2010-12-04
The bootcfg /rebuild is another windows command to rebuild boot.ini incase it is corrupted.

You can copy the ntldr and ntdetect.com from your windows cd  with windows from the repair line or using your Ubuntu liveCD from the service pack saved  files to your c:\.

Everything in XP can be repaired from the XP disk and everything but chkdsk can be fixed from a Ubuntu liveCD (but obviously using different commands)

Same info presented differently:
How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by Tron22 on 2010-12-04
Okay... this isn't working

i've tried chkdsk, fixmbr, fixboot, bootcfg /rebuild and put in my windows xp professional and fastdetect

I have no idea what you mean when you say i can copy nltdr and ntdetect.com? why am i copying it?  where am i copying it too.  Remember.. supernewb here

In the windows cd i put in 

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:

and neither were found.

so after installing linux, trying chkdsk, fixmbr, fixboot, bootcfg /rebuild for it to work as a dual boot... i'm left with a computer that has the capabilty of flashing some really colorful characters over a black screen when i try and boot anything. :( so frustrated.

I'm afraid i've lost my xp.  I need specific directions how to get windows to boot. 

> You can copy the ntldr and ntdetect.com from your windows cd  with  windows from the repair line or using your Ubuntu liveCD from the  service pack saved  files to your c:\.

Everything in XP can be repaired from the XP disk and everything but  chkdsk can be fixed from a Ubuntu liveCD (but obviously using different  commands)Looks like I have a couple options here but I don't know how to copy ntldr and ntdetect.com from my windows cd repair line.  or how to use the service pack through ubuntu.  

So lost with a computer that doesn't work :( what next?

---

### Post by oldfred on 2010-12-04
In this command the windows repair requires you to use for [CDDRIVE] what ever the path is to your cd drive, not just those letters.
COPY [CDDRIVE]:\I386\NTLDR  C:\ 

Sometimes ntldr and ntdetect.com get corrupted so they need to be replaces. Often it is boot.ini that is wrong and it needs to be rebuilt.

All those files have to be in the c:\ or the root of your windows installs. If viewing from Ubuntu it is easy to see, not sure about from windows anymore. 

Did you look at the links on repairing windows?
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by Tron22 on 2010-12-05
Alright my cd drive is just drive d.  I tried it and got "access is denied". Copy d:\i386\ntldr

---

### Post by oldfred on 2010-12-06
Did you leave off:

d:\i386\ntldr [COLOR=Red]c:\[/COLOR]

---

### Post by sp-1070 on 2010-12-06
just throw out XP run it from a virtual box way easyer that way you wont even have to reboot evrytime you want to go into xp

---

