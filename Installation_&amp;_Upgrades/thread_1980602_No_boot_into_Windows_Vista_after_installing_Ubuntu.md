---
title: "No boot into Windows Vista after installing Ubuntu"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by listentounderthegiven on 2012-05-15
Not sure exactly how to post this...

I installed Ubuntu 12.04 Precise alongside Windows Vista Home Premium.

I partitioned my 320gb hdd to allow 20gb to Ubuntu.

My computer will not let me load into vista now.  I'm not sure what I did, but I am able to see it is still there, or so I'm assuming, I have gparted installed, but Im not sure how to use it.  When I open gparted I can see all the drives and my primary hdd with windows vista and ubuntu on it.

How do I go about getting my Boot menu to allow me to choose between vista and ubuntu again?

---

### Post by wilee-nilee on 2012-05-15
In ubuntu run

```
sudo update-grub
```If windows does not show then run these commands and post the result.txt that will appear in your home in the thread.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by listentounderthegiven on 2012-05-15
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 590223592 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   354,289,663   354,289,601   7 NTFS / exFAT / HPFS
/dev/sda2         601,473,600   625,137,344    23,663,745   7 NTFS / exFAT / HPFS
/dev/sda3         560,580,606   601,473,023    40,892,418   5 Extended
/dev/sda5         560,580,608   595,447,807    34,867,200  83 Linux
/dev/sda6         595,449,856   601,473,023     6,023,168  82 Linux swap / Solaris
/dev/sda4         354,297,510   560,572,109   206,274,600  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F0360CD9360CA328                       ntfs       COMPAQ
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda4        4fc0b680-0235-4846-8766-689c5efbf13f   ext4       
/dev/sda5        ee6513db-9fd7-4590-b8a2-569fdc7b3c2f   ext4       
/dev/sda6        53d90de4-294d-461c-8e46-76d60050e808   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 12.04 LTS i386 iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="2"
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
  insmod video_bochs
  insmod video_cirrus
}

terminal_input console
terminal_output console
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ee6513db-9fd7-4590-b8a2-569fdc7b3c2f
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=ee6513db-9fd7-4590-b8a2-569fdc7b3c2f ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root ee6513db-9fd7-4590-b8a2-569fdc7b3c2f
	echo	'Loading Linux 3.2.0-24-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=ee6513db-9fd7-4590-b8a2-569fdc7b3c2f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root F0360CD9360CA328
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ee6513db-9fd7-4590-b8a2-569fdc7b3c2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=53d90de4-294d-461c-8e46-76d60050e808 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 281.440719604 = 302.194671616  boot/grub/core.img                             1
 271.691165924 = 291.726168064  boot/grub/grub.cfg                             1
 272.405277252 = 292.492939264  boot/initrd.img-3.2.0-24-generic-pae           2
 271.650180817 = 291.682160640  boot/vmlinuz-3.2.0-24-generic-pae              2
 272.405277252 = 292.492939264  initrd.img                                     2
 271.650180817 = 291.682160640  vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  9a 2e 08 c5 94 9d c0 c8  40 7d 86 e9 e7 49 87 78  |........@}...I.x|
00000010  15 aa f4 f2 af 0f 3d e9  15 01 8f 64 2a 98 81 da  |......=....d*...|
00000020  34 6e b3 d1 60 05 2f 7e  f2 a9 ed a0 a5 57 8a 6e  |4n..`./~.....W.n|
00000030  82 91 56 82 17 81 d1 7a  a8 25 1c 38 f3 9f 24 74  |..V....z.%.8..$t|
00000040  5c 3f 08 41 08 20 aa a5  c1 04 4a 83 f8 0a 40 3a  |\?.A. ....J...@:|
00000050  5e aa aa 5c 1d ab 09 36  13 bc 94 e6 36 ce b6 88  |^..\...6....6...|
00000060  d0 f8 b8 14 2a 95 28 05  0c d5 ef 37 a4 3e 50 4a  |....*.(....7.>PJ|
00000070  60 ef fc 6b bb 7f 04 51  e8 b0 e3 bb d3 bb 86 0f  |`..k...Q........|
00000080  7a b9 5c 83 3b 8e 9e f4  ef 76 55 b0 b6 7f d1 f2  |z.\.;....vU.....|
00000090  89 40 fb 60 58 56 68 f1  ea 95 2b 52 a7 79 55 4e  |.@.`XVh...+R.yUN|
000000a0  c8 3b 6c d0 b9 84 6e 38  b6 d4 d8 06 3f 8d 50 72  |.;l...n8....?.Pr|
000000b0  9f 38 02 70 bf be af 01  a8 49 d5 f9 5a 81 13 d7  |.8.p.....I..Z...|
000000c0  57 9a b8 82 b9 c7 13 d5  50 3b a3 a1 0d 91 45 ec  |W.......P;....E.|
000000d0  5d 01 11 70 28 e3 33 13  cf 94 0c 22 92 f5 c4 84  |]..p(.3...."....|
000000e0  7e 1f 8b 71 58 19 98 40  0c 85 f8 6f c0 3a d2 8d  |~..qX..@...o.:..|
000000f0  07 47 e7 69 70 f8 1d 70  86 80 7d 06 06 d1 61 59  |.G.ip..p..}...aY|
00000100  ce 0f 9b 07 50 3e 1a 13  5c 02 6e 1d 0f a8 8e aa  |....P>..\.n.....|
00000110  d0 27 5c ae 28 f0 1a 2e  50 5a 2e e6 1b 3c 9e 81  |.'\.(...PZ...<..|
00000120  60 b4 75 49 b5 bc 22 07  1d 0f bd df 01 fe af ff  |`.uI..".........|
00000130  e1 59 f0 7f 74 56 f0 39  ea cf c6 a3 a0 70 2e 0e  |.Y..tV.9.....p..|
00000140  32 17 e9 e2 eb ef c6 14  fc 0a 4d c4 d4 8d 97 fe  |2.........M.....|
00000150  77 7b 3d f6 4f 87 51 b0  9d 71 81 b7 a3 cd 9d 7a  |w{=.O.Q..q.....z|
00000160  71 1c 65 0c df 79 77 6c  60 85 bc 66 33 ee cc 6c  |q.e..ywl`..f3..l|
00000170  9e 51 fc ce 49 97 cd bc  d6 6e 9e 74 c9 7a 48 f1  |.Q..I....n.t.zH.|
00000180  df 87 be f2 bb 8a 74 b0  e8 ff ac 61 38 ad 8f 43  |......t....a8..C|
00000190  03 f0 77 93 d2 12 0f 75  a6 38 a1 37 79 05 8d 6f  |..w....u.8.7y..o|
000001a0  29 25 b0 f8 ff 38 05 f4  9f 96 f2 18 27 c1 c4 70  |)%...8......'..p|
000001b0  52 b4 22 61 6a 45 40 e4  be 26 56 5c af 27 00 fe  |R."ajE@..&V\.'..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 14 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 8b 0d  14 02 77 ea 5b 00 00 00  |..........w.[...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

  No volume groups found

---

### Post by wilee-nilee on 2012-05-15
Script looks good windows looks bootable, have you run this command in the ubuntu that is installed, not a live cd.

```
sudo update-grub
```If you have and do not see windows show in the terminal readout then install gparted.

```
sudo apt-get install gparted
```Open gparted and right click the sda1 partition then manage flags then click boot, this puts a bootflag on that partition and makes it active.

[ATTACH]218013[/ATTACH]

Then run the update grub command again. Basically grub should boot windows without the flag, but glitches do happen.

Running the update-grub command reloads the grub menu, in grub is a OS finder called os-prober this searches for other operating system to add to the boot menu.

It may be that the sda2 partition is the one that is supposed to be active, it is a recovery partition, I'm wary of having you start there, as it may trigger a recovery which probably can be stopped but you never know.

---

### Post by listentounderthegiven on 2012-05-15
after entering sudo update-grub into the terminal it looks like this...

drew@TheUbuntuBrain:~$ sudo update-grub
[sudo] password for drew: 
Generating grub.cfg ...
using custom appearance settings
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
  No volume groups found
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
drew@TheUbuntuBrain:~$ 

-------------------------

i am able to see windows in the readout... i took a screenshot of the terminal, but I'm not sure how to go about showing it to you on this...

i clicked to the advanced settings and clicked the attachments icon to see if i could allow you to see it. I don't think it worked though

---

### Post by wilee-nilee on 2012-05-15
> **listentounderthegiven said:**
> after entering sudo update-grub into the terminal it looks like this...

drew@TheUbuntuBrain:~$ sudo update-grub
[sudo] password for drew: 
Generating grub.cfg ...
using custom appearance settings
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
  No volume groups found
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
drew@TheUbuntuBrain:~$ 

-------------------------

i am able to see windows in the readout... i took a screenshot of the terminal, but I'm not sure how to go about showing it to you on this...

i clicked to the advanced settings and clicked the attachments icon to see if i could allow you to see it. I don't think it worked though

Looks good you may see two windows choices in the grub menu now, one is the main OS to get to Vista and the other is to the recovery, so be careful if you see two that you choose the correct one. 

Reboot and boot to vista from the grub menu.

---

### Post by listentounderthegiven on 2012-05-15
alrighty, this is where the problem starts..

when it loads the Bios Screen in the beginning of the bootup it goes to where i can choose from the 4 options (as stated in my private msg. to you. when i choose either windows one, the screen goes black, then says:

error: no device connected.
error: no device connected.
error: no device connected.
error: no device connected.

Then, about 10 seconds later, underneath the 4 error msgs. it says something like,

No video mode activated

then, 20 seconds later it says:

A disk read error occurred
Press Ctrl+Alt+Del to restart, and repeats this process until I choose the Ubuntu choice or the other Ubuntu Recovery Choice.

---

### Post by wilee-nilee on 2012-05-15
> **listentounderthegiven said:**
> alrighty, this is where the problem starts..

when it loads the Bios Screen in the beginning of the bootup it goes to where i can choose from the 4 options (as stated in my private msg. to you. when i choose either windows one, the screen goes black, then says:

error: no device connected.
error: no device connected.
error: no device connected.
error: no device connected.

Then, about 10 seconds later, underneath the 4 error msgs. it says something like,

No video mode activated

then, 20 seconds later it says:

A disk read error occurred
Press Ctrl+Alt+Del to restart, and repeats this process until I choose the Ubuntu choice or the other Ubuntu Recovery Choice.

If you have not installed gparted, and put the boot flag on the sda1 partition, do this now, then run the update-grub again. Then reboot to check the boot.

Look to see as well by mounting the sda1 in gparted or from home then right click information on the sda1 partition in gparted. That partition may need a chkdsk /r run, by using a vista recovery or install disc and its recovery terminal. The information in gparted may give a clue as to any anomalies in the sda1 partition.

The vista's boot can also be rebuilt if needed from the recovery terminal as well.

Do you have a vista recovery or install disc to do any rebuilds, or just load the vista bootloader back so we can see if vista just boots straight in.

When people install Ubuntu and let it resize windows partitions or just do it with gparted this has been known to cause failures in windows. 

Did you resize the vista C called sda1 in Ubuntu, and or use another partitioner and check that vista still booted, and let the auto-chkdsk run as well, before the Ubuntu install?

---

### Post by listentounderthegiven on 2012-05-15
I have g-parted installed, and sda1 is flagged to boot, and i have ran the sudo update-grub in terminal.

In GParted, when i right click sda1's information, it says,

File System:  ntfs
Size:         168.94 GiB
Unused:       136.27 GiB (81%)
Flags:        boot

Path:         dev/sda1
Status:       Not Mounted
Label:        Compaq
UUID:         Not sure if I should put this...

First Sector: 63
Last Sector:  354289663
Total Sectors:354289601

I don't know how to have it say "Mounted" in the proper field but, when i right click /dev/sda1 and the mini-menu pops up unmounted is grey...

I don't have a Vista recovery CD or an Installation Disk.

I did resize/created the partition in Ubuntu.

I don't recall checking to see if Vista would still boot after the initial partitioning and installtion of Ubuntu. 

I do remember restarting or shutting my computer down, and being anxious to learn of Ubuntu and use it so I didnt think to check Vista at that time. Then tried going to Vista at a later time and not being able to...

Does this info help at all?

---

### Post by jawilljr on 2012-05-15
listentounderthegiven,

Please [read this,](http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html) and [espicially this](http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html#hlp)

[Windows 7, Vista repair discs.](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

The repair discs used to be free...of course [M$ changed that.](http://neosmart.net/blog/2011/windows-recovery-discs-updated-reinstated/) It know costs $9.75 per disc.

Hope you get your system back up.

Jerry

---

### Post by wilee-nilee on 2012-05-15
> **listentounderthegiven said:**
> I have g-parted installed, and sda1 is flagged to boot, and i have ran the sudo update-grub in terminal.

In GParted, when i right click sda1's information, it says,

File System:  ntfs
Size:         168.94 GiB
Unused:       136.27 GiB (81%)
Flags:        boot

Path:         dev/sda1
Status:       Not Mounted
Label:        Compaq
UUID:         Not sure if I should put this...

First Sector: 63
Last Sector:  354289663
Total Sectors:354289601

I don't know how to have it say "Mounted" in the proper field but, when i right click /dev/sda1 and the mini-menu pops up unmounted is grey...

I don't have a Vista recovery CD or an Installation Disk.

I did resize/created the partition in Ubuntu.

I don't recall checking to see if Vista would still boot after the initial partitioning and installtion of Ubuntu. 

I do remember restarting or shutting my computer down, and being anxious to learn of Ubuntu and use it so I didnt think to check Vista at that time. Then tried going to Vista at a later time and not being able to...

Does this info help at all?

So you ran a reboot though to check the boot on the vista after the bootflag was set correct. IF this was done the first time that is okay I just want a confirmation on this.

Yes the info does help.

---

### Post by wilee-nilee on 2012-05-15
Lets load a bootloader that will boot vista straight in. If it boots vista after a install of this loader in Ubuntu but wants a check disc let it run.

So go to the ubuntu software center top left corner hit edit then software sources then find the universe repo and make sure it is clicked on first tab second box that can be ticked.

Then run this command after closing the windows and the software center.

```
sudo apt-get update
```Then follow this.

                                  [FONT=Verdana, sans-serif][SIZE=1]```
sudo apt-get install lilo
``` [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT]```
[FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr[/SIZE][/FONT]
``` [FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR[/SIZE][/FONT]

[FONT=Verdana, sans-serif][SIZE=1]reboot to see if vista boots and let any disc checks happen, it will reboot itself to vista hopefully after this.[/SIZE][/FONT]


[FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT]

---

### Post by wilee-nilee on 2012-05-15
> **jawilljr said:**
> listentounderthegiven,

Please [read this,]("http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html") and [espicially this]("http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html#hlp")

[Windows 7, Vista repair discs.]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

The repair discs used to be free...of course [M$ changed that.]("http://neosmart.net/blog/2011/windows-recovery-discs-updated-reinstated/") It know costs $9.75 per disc.

Hope you get your system back up.

Jerry

Thanks but there is a bootloader that can be used, please be careful about just posting when it is obvious that work is getting done, and any additions may cloud the situation, please. :)

Testdisk at this point is not needed and if run  wrong can brick the OS before a backup can be done .

---

### Post by listentounderthegiven on 2012-05-15
thank you im reading this now! thanks again.

---

### Post by jawilljr on 2012-05-15
> **wilee-nilee said:**
> Thanks but there is a bootloader that can be used, please be careful about just posting when it is obvious that work is getting done, and any additions may cloud the situation, please. :)

Testdisk at this point is not needed and if run  wrong can brick the OS before a backup can be done .

*snip*

I was just trying to give the OP some more information... also sometimes you have to repair windows with the install cd after resizing with gparted.

Jerry

---

### Post by darkod on 2012-05-15
I agree with the idea of wilee about installing generic mbr using part of lilo. Since it acts like windows bootloader, vista might offer to run a chkdsk.

Also, don't forget that you can get windows advanced options with F8. If booting vista automatically still doesn't work after the installation of the generic mbr, try hitting F8 when it starts booting and the bios messages go away. That should open the advanced menu.

Try the Safe Mode first. If you are lucky it will load it, or at least give a message and offer chkdsk to be done.

---

### Post by wilee-nilee on 2012-05-15
> **darkod said:**
> I agree with the idea of wilee about installing generic mbr using part of lilo. Since it acts like windows bootloader, vista might offer to run a chkdsk.

Also, don't forget that you can get windows advanced options with F8. If booting vista automatically still doesn't work after the installation of the generic mbr, try hitting F8 when it starts booting and the bios messages go away. That should open the advanced menu.

Try the Safe Mode first. If you are lucky it will load it, or at least give a message and offer chkdsk to be done.

Thanks darkod, I always appreciate you stopping by.  :)

---

### Post by listentounderthegiven on 2012-05-15
yes, i restarted my computer and it goes to the loader and i can only choose ubuntu or the ubuntu recovery mode,  But i see these to choices with 2 windows vista options, when i try those it tries to load but stops with a ctrl+alt+delete to restart as my only option.

---

### Post by darkod on 2012-05-15
Did you install the lilo mbr with the commands in post #12?

If you did that, it can't show the grub menu any more, and it should try to boot vista directly.

---

### Post by listentounderthegiven on 2012-05-15
I just did what was said in post 12, I must have completely missed it, thanks for your patience.  I'm gonna restart now and see what happens.

---

### Post by listentounderthegiven on 2012-05-15
Awesome, It worked I'd like to thank you guys for the help. Thank you so much.

---

### Post by darkod on 2012-05-15
There still might be some errors which could be causing grub2 not to load it correctly. Otherwise, it should work in grub2 also, when you select the Vista (/dev/sda1) entry.

Now that you have windows running, open a command prompt as administrator and just to make sure there are no errors, try:
chkdsk c: /r /f

It might take a while to finish.

After that you can start considering reinstalling grub2 to the MBR of the disk.

---

