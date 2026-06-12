---
title: "Completely new to ubuntu, need help with error: out of disk grub rescue issue"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by RogueGrendel on 2011-01-10
I have just attempted to install Ubuntu 10.10 onto an old Sony Vaio laptop, (sorry I do not know the model off hand).
I followed this process:
Downloaded ubuntu iso and burned to dvd as per ubuntu website instructions
Booted laptop from optical drive and followed instructions to install just ubuntu on whole of hard drive, followed prompts all the way to restart computer. 
Ejected dvd with iso image on and restarted the laptop
I am not familiar with how ubuntu should start up, so not sure whether the raindrop screen is a loading screen or startup screen or whatever.
Anyway, after the animation faded to an all black screen, the computer seemed to get stuck, their was no prompt or button or login, etc.
So I turned off laptop and tried again.
This time the computer displayed a stream of error things (white text on black background)
before displaying this prompt

error: out of disk
grub rescue>

I have absolutely no idea what to do now, I have tried searching the forums and google but to be honest the terminology is baffling.

Please can someone explain in the simplest terms what to do next?
(Also please tell me how to open "terminals" or command lines etc if this is necessary, as I really have no clue how to use ubuntu yet.)

Thanks in advance to everyone. I'm looking forward to playing with Linux but the learning curve is a bit steep for me. :)

---

### Post by psusi on 2011-01-10
Boot up the live cd again and choose the terminal from the menu.  Paste this into it:

```

wget http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh

sudo bash boot_info_script055.sh
gedit RESULTS.txt

```

Highlight all of the text in the file that opens, copy, and paste it here inside [code] tags.

---

### Post by RogueGrendel on 2011-01-10
Thank you for the help.

I tried what you suggested, it boots from live CD, but the laptop is not connected to the internet so it gave a convoluted error message when I entered the code into the terminal.

Please excuse me not posting it here, but I am having to run back and forth with a usb stick to copy and paste stuff from laptop to desktop and vice versa. I can get the details if you need it.

I googled my Vaio for specs and found this page if it helps resolve issues re RAM size etc.

[http://www.zdnet.co.uk/reviews/laptops-mainstream/2002/11/20/sony-vaio-pcg-grx516sp-10002270/](http://www.zdnet.co.uk/reviews/laptops-mainstream/2002/11/20/sony-vaio-pcg-grx516sp-10002270/)

Thanks again, Pete

I think I understand what you are looking for, is it this script that i need to download and paste into terminal to get results info?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by presence1960 on 2011-01-10
Symptoms

Booting a Linux Operating System fails with error message "error: biosdisk write error, failed to boot default entries." or with "error: out of disk"

Cause:

The menuentry for your operating system in grub.cfg contains the lines

       ```
recordfail=1
       if [ -n \${have_grubenv} ]; then save_env recordfail; fi
```

This instructs Grub, to write "recordfail=1" to the file "/boot/grub/grubenv". In same rare cases the file "grubenv" exists but always has length 0. In this case Grub cannot write to the file and booting fails.

This problem should by fixed in Ubuntu 10.04 and higher. 

Reference: [1]
Temporary Solution

At the Grub menu at boot up (you may have hold down the "shift" key during boot up or press "esc" during the count down to bring up the Grub menu):

Select the Linux OS you are trying to boot and press "e".

At the new screen, delete the line

  ```
 if  [ -n \${have_grubenv} ]; then save_env recordfail; fi
```

Press "Ctr+x".

If this does not boot you into your Linux OS, this How-To probably does not apply to you.

Solution

Boot into the OS controlling Grub (use the Temporary Solution if necessary), open a terminal and then open the file "10_linux" via

  ```
 gksudo gedit /etc/grub.d/10_linux

```

Look for

   ```
  menuentry "$1" {
     recordfail=1
     if  [ -n \${have_grubenv} ]; then save_env recordfail; fi
```
   

(should be around line 60) and add a "#" in front of "if"

   ```
 menuentry "$1" {
    recordfail=1
  [COLOR="Red"]#[/COLOR] if [ -n \${have_grubenv} ]; then save_env recordfail; fi

```

Save the file. Then back in the terminal:

   ```
 sudo update-grub
```

Since you say you can't get online I posted a page which refers to your problem with a possible fix.

P.S. I see you can get online. here is the [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write") for a better read of those instructions.

---

### Post by RogueGrendel on 2011-01-10
Thank you, will try what you suggested and report back!

---

### Post by RogueGrendel on 2011-01-10
I have run out of time and patience at the moment, but I really appreciate you all trying to help me out with this problem.

I will have another go tomorrow afternoon and post the results as soon as i get them.

Cheers guys, catch you in a bit.

PS: I am loving the ubuntu interface so far, despite only using a few menus and opening a couple of apps/programs. Much quicker than my previous xp installation :)

---

### Post by psusi on 2011-01-10
Prescence: he already said he is running 10.10 so that doesn't apply.

Rogue: yes, that is the script I would like you to run on the laptop, and post the RESULTS.txt file it generates.  The wget part of the commands I posted was to download the file.  If you can copy it over with a usb stick that will work too.

---

### Post by RogueGrendel on 2011-01-11
Prescence: Thanks for your help, unfortunately that fix is a bit beyond my ability at the moment.
Psusi: Thanks for your patience and help.

I have managed to get the RESULTS.txt file from the laptop, hope it sheds some light on the problem.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sda2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
5 heads, 32 sectors/track, 97894 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,064    15,663,103    15,655,040   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        24f0e02c-c8ac-424b-bf9f-db8b62eb1b80   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1b09325a-9586-4e25-ba9e-bb552f6aacf6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        C055-F15E                              vfat       PATRIOT                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PATRIOT           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1        /media/24f0e02c-c8ac-424b-bf9f-db8b62eb1b80 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 24f0e02c-c8ac-424b-bf9f-db8b62eb1b80
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 24f0e02c-c8ac-424b-bf9f-db8b62eb1b80
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24f0e02c-c8ac-424b-bf9f-db8b62eb1b80
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=24f0e02c-c8ac-424b-bf9f-db8b62eb1b80 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24f0e02c-c8ac-424b-bf9f-db8b62eb1b80
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=24f0e02c-c8ac-424b-bf9f-db8b62eb1b80 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24f0e02c-c8ac-424b-bf9f-db8b62eb1b80
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24f0e02c-c8ac-424b-bf9f-db8b62eb1b80
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=24f0e02c-c8ac-424b-bf9f-db8b62eb1b80 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1b09325a-9586-4e25-ba9e-bb552f6aacf6 none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
  94.6GB: boot/grub/grub.cfg
 150.6GB: boot/initrd.img-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-22-generic
 150.6GB: initrd.img
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  98 80 00 00 67 b4 b2 af  b8 de 22 c8 46 a3 25 08  |....g.....".F.%.|
00000010  04 8d af 99 0c f1 c5 a1  9b 96 ef 7d 05 43 80 31  |...........}.C.1|
00000020  40 23 8b 0c 05 0f 14 82  2e 53 0f 68 9a 94 dd a2  |@#.......S.h....|
00000030  03 57 13 20 b1 9f c3 e5  33 6d 49 d9 1d 91 8a ec  |.W. ....3mI.....|
00000040  2c cb 42 b1 8d 7f 56 16  2b 31 59 48 ce 1c 42 96  |,.B...V.+1YH..B.|
00000050  57 88 4a d5 14 3a 8b bd  62 43 a3 48 a7 4a 6c 31  |W.J..:..bC.H.Jl1|
00000060  98 b2 2e 88 86 63 e4 72  4e 9f ff fe 40 eb 73 01  |.....c.rN...@.s.|
00000070  f8 88 f9 2a 60 80 99 55  00 00 00 30 82 00 c9 f6  |...*`..U...0....|
00000080  25 31 60 c4 99 67 a8 fe  87 eb 5d 7f 43 6c 0e 76  |%1`..g....].Cl.v|
00000090  d4 bb 09 04 84 8a c7 14  10 63 a6 b4 ee df 65 fb  |.........c....e.|
000000a0  43 44 67 f0 e8 10 31 91  a5 d6 35 7f b7 88 da bf  |CDg...1...5.....|
000000b0  ef 46 14 9a 5a 56 ed 9f  06 0e 41 a6 90 8a a9 d4  |.F..ZV....A.....|
000000c0  ac 50 92 32 14 44 aa ca  20 99 73 ef 14 23 48 36  |.P.2.D.. .s..#H6|
000000d0  a1 4e 40 d8 4a 81 f4 4c  11 a8 38 28 c4 51 32 db  |.N@.J..L..8(.Q2.|
000000e0  4b a1 44 c8 6d 74 cb 1c  83 79 8d c0 b2 48 02 8d  |K.D.mt...y...H..|
000000f0  3a 28 20 8d e5 04 1b 0d  93 2d 31 35 a3 ba c3 4a  |:( ......-15...J|
00000100  2c 60 37 8b 26 1f 44 81  e8 db a1 01 23 e9 8d a9  |,`7.&.D.....#...|
00000110  ac 83 c9 44 ca 56 2e 9c  dd 18 02 60 00 09 20 89  |...D.V.....`.. .|
00000120  78 95 c1 2b b8 e9 d4 3a  5a 5c ad 44 7c 11 06 cf  |x..+...:Z\.D|...|
00000130  c3 83 95 c5 5d 9c 52 42  3f 52 95 b8 5d 7d 94 09  |....].RB?R..]}..|
00000140  58 54 5e bb 3c 64 2c 7f  fe 4c 9d ca 50 ff ff a8  |XT^.<d,..L..P...|
00000150  db fe 07 b0 f7 35 06 b0  eb ce a2 6b 13 57 d7 ff  |.....5.....k.W..|
00000160  c3 ae 50 fe 4c aa af f8  f1 20 67 be 04 c2 8c 60  |..P.L.... g....`|
00000170  8f 24 10 5d 50 eb 78 ca  ad e9 a7 f3 65 38 51 f3  |.$.]P.x.....e8Q.|
00000180  64 8f cb 87 e4 df fd 3b  65 ac 8b 23 50 4c 79 0d  |d......;e..#PLy.|
00000190  92 80 b7 e1 78 17 ec 2c  03 4f b4 dd 63 31 eb 72  |....x..,.O..c1.r|
000001a0  99 55 b9 ed 4d d2 c7 aa  54 ec b4 a1 2b ca d6 5d  |.U..M...T...+..]|
000001b0  3a 08 a3 8f 71 44 f4 a4  68 c8 48 7c b7 b6 00 fe  |:...qD..h.H|....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

Please let me know what my next step should be. Cheers, Pete.

---

### Post by RogueGrendel on 2011-01-11
Okay, I have managed to sort it through blind luck.

I noticed xp was still showing in the RESULTS.txt document so I decided to run my xp disc to get to the format and partition options.

I then deleted the existing partitions and created a new one, to maximum size.

For some reason XP could not recognise my hard drive to start with so I took it out and replaced it then tried again.

After setting up the Partition I exited without installing XP, put in my Ubuntu Live Disc, and installed as normal.

Luckily this time everything appears to be working fine.

It boots from hard drive and everything is ok.

Thank you for all your help with this matter. It is great to see that their is such a great support network for new adopters of Linux, it gives me great confidence to explore this OS and see what it can do.

Cheers, Pete :)

---

### Post by psusi on 2011-01-11
Your disk might be starting to have issues.  Fire up the disk utility from the menu and look at the SMART stats of the drive.  Make sure the following values are zero:

Offline_Uncorrectable
Current_Pending_Sector
Reallocated_Sector_Ct

You might also want to run the long self test and then check the values again.

You may have just had an unexplained 'hicup' but it doesn't hurt to check the health of the drive.

---

### Post by florian107 on 2011-01-26
> **psusi said:**
> Boot up the live cd again and choose the terminal from the menu.  Paste this into it:

```

wget http://downloads.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh

sudo bash boot_info_script055.sh
gedit RESULTS.txt

```

Highlight all of the text in the file that opens, copy, and paste it here inside ```
 tags.


Hi,

Ever since I created two 10GB partitions on my 500GB drive (but never installed anything on them), using a GParted Live CD, I got messages such as 

error: hd0, msdos1 out of disk
error: no suitable mode found
error: couldn't read file
Failed to boot both default and fallback entries

or

error: couldn't read file
error: you need to load the kernel first

Then, after a couple of reboots, it seemed all fine again and Maverick booted normally. After 30 minutes or so it all went terrible slow, even the reboot took ages. Then same story as above.

I did as you suggested above. I post the RESULTS.txt below. Any ideas?

Thanks a lot

Florian

------
Linux 10.10
2GB RAM, Intel Core2Quad  CPU Q3800@2.5GHz


                [CODE]Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     20,754,432   943,265,791   922,511,360  83 Linux
/dev/sda2         964,487,166   976,771,071    12,283,906   5 Extended
/dev/sda5         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris
/dev/sda3         943,265,792   964,485,119    21,219,328   7 HPFS/NTFS
/dev/sda4               2,048    20,754,431    20,752,384  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8015 MB, 8015314944 bytes
111 heads, 16 sectors/track, 8814 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             16    15,654,910    15,654,895   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        832a3077-821f-4a2c-be35-d140e3842df9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        66EB8FB5448F11DF                       ntfs                                     
/dev/sda4        dbb92fb8-58c6-4e88-985e-471da2294592   ext2                                     
/dev/sda5        5256d371-b608-4620-9bc7-65b6d9d853e4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0123-4567                              vfat       NO NAMEFORR                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/NO NAMEFORR       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=832a3077-821f-4a2c-be35-d140e3842df9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5256d371-b608-4620-9bc7-65b6d9d853e4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 221.2GB: boot/grub/core.img
 139.8GB: boot/grub/grub.cfg
  11.7GB: boot/initrd.img-2.6.35-22-generic
  11.3GB: boot/initrd.img-2.6.35-23-generic
 474.3GB: boot/initrd.img-2.6.35-24-generic
 221.3GB: boot/vmlinuz-2.6.35-22-generic
 221.3GB: boot/vmlinuz-2.6.35-23-generic
 221.3GB: boot/vmlinuz-2.6.35-24-generic
 474.3GB: initrd.img
  11.3GB: initrd.img.old
 221.3GB: vmlinuz
 221.3GB: vmlinuz.old
```

---

### Post by ethode on 2011-03-17
> **florian107 said:**
> Hi,

Ever since I created two 10GB partitions on my 500GB drive (but never installed anything on them), using a GParted Live CD, I got messages such as 

error: hd0, msdos1 out of disk
error: no suitable mode found
error: couldn't read file
Failed to boot both default and fallback entries

or

error: couldn't read file
error: you need to load the kernel first

Then, after a couple of reboots, it seemed all fine again and Maverick booted normally. After 30 minutes or so it all went terrible slow, even the reboot took ages. Then same story as above.

I did as you suggested above. I post the RESULTS.txt below. Any ideas?

Thanks a lot

Florian

------
Linux 10.10
2GB RAM, Intel Core2Quad  CPU Q3800@2.5GHz


                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     20,754,432   943,265,791   922,511,360  83 Linux
/dev/sda2         964,487,166   976,771,071    12,283,906   5 Extended
/dev/sda5         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris
/dev/sda3         943,265,792   964,485,119    21,219,328   7 HPFS/NTFS
/dev/sda4               2,048    20,754,431    20,752,384  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8015 MB, 8015314944 bytes
111 heads, 16 sectors/track, 8814 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             16    15,654,910    15,654,895   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        832a3077-821f-4a2c-be35-d140e3842df9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        66EB8FB5448F11DF                       ntfs                                     
/dev/sda4        dbb92fb8-58c6-4e88-985e-471da2294592   ext2                                     
/dev/sda5        5256d371-b608-4620-9bc7-65b6d9d853e4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0123-4567                              vfat       NO NAMEFORR                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/NO NAMEFORR       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=832a3077-821f-4a2c-be35-d140e3842df9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 832a3077-821f-4a2c-be35-d140e3842df9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=832a3077-821f-4a2c-be35-d140e3842df9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5256d371-b608-4620-9bc7-65b6d9d853e4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 221.2GB: boot/grub/core.img
 139.8GB: boot/grub/grub.cfg
  11.7GB: boot/initrd.img-2.6.35-22-generic
  11.3GB: boot/initrd.img-2.6.35-23-generic
 474.3GB: boot/initrd.img-2.6.35-24-generic
 221.3GB: boot/vmlinuz-2.6.35-22-generic
 221.3GB: boot/vmlinuz-2.6.35-23-generic
 221.3GB: boot/vmlinuz-2.6.35-24-generic
 474.3GB: initrd.img
  11.3GB: initrd.img.old
 221.3GB: vmlinuz
 221.3GB: vmlinuz.old
```

I'm having the identical problem.  I haven't done anything to Ubuntu other than get the latest updates and it's been fine, then today apps just started freezing and POOF, had to restart... When the PC rebooted I had a message

error: hd0, msdos1 out of disk

Neither of my 500GB seagate drives are out of space, or even half full for that matter.  However, this same problem cropped up a couple weeks ago.. I never fixed it.. Just rebooted my PC after a couple days and POOF, all was good again.

Now this afternoon same crap again..


EDIT:
Yesterday afternoon I rebooted the machine again, and now it's working.. I know it's just a matter of time before the time bomb hits again.

---

