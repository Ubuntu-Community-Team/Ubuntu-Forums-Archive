---
title: "Dual Boot XP/Ubuntu 11.04 problem"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by kbagastro on 2011-06-14
I just installed ubuntu on my windows machine. After I installed, I noticed it never gave me an option to pick the partition.  I know I selected the dual boot option.  When I boot it automatically starts ubuntu.  My question is, did I accidentally choose single boot option and need to start over? Or did I miss something?  Is there a way to check to see if windows is still installed?  I'm very new to ubuntu, so go easy. Thanks in advance.
Chris

---

### Post by oldfred on 2011-06-14
Welcome to the forums.

First post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by kbagastro on 2011-07-12
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   247,802,624   247,802,562   7 NTFS / exFAT / HPFS
/dev/sda2         247,802,686   390,721,535   142,918,850   f W95 Extended (LBA)
/dev/sda5         247,802,688   258,036,029    10,233,342   e W95 FAT16 (LBA)
/dev/sda6    *    258,036,093   299,997,809    41,961,717   7 NTFS / exFAT / HPFS
/dev/sda7         299,999,232   388,757,503    88,758,272  83 Linux
/dev/sda8         388,759,552   390,721,535     1,961,984  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        AEB0F5A3B0F57267                       ntfs       
/dev/sda6        0004CF0E04CF059E                       ntfs       
/dev/sda7        37d88773-91ff-42b1-a35d-d2a47b7af660   ext4       
/dev/sda8        8a5d1115-4b71-4002-988f-f40ab87ce365   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 37d88773-91ff-42b1-a35d-d2a47b7af660
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 37d88773-91ff-42b1-a35d-d2a47b7af660
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 37d88773-91ff-42b1-a35d-d2a47b7af660
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=37d88773-91ff-42b1-a35d-d2a47b7af660 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 37d88773-91ff-42b1-a35d-d2a47b7af660
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=37d88773-91ff-42b1-a35d-d2a47b7af660 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 37d88773-91ff-42b1-a35d-d2a47b7af660
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 37d88773-91ff-42b1-a35d-d2a47b7af660
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root AEB0F5A3B0F57267
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
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=37d88773-91ff-42b1-a35d-d2a47b7af660 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=8a5d1115-4b71-4002-988f-f40ab87ce365 none            swap    sw              0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 171.245746613 = 183.873720320  boot/grub/core.img                             1
 149.782707214 = 160.827957248  boot/grub/grub.cfg                             1
 144.457031250 = 155.109556224  boot/initrd.img-2.6.38-8-generic               2
 171.244018555 = 183.871864832  boot/vmlinuz-2.6.38-8-generic                  1
 144.457031250 = 155.109556224  initrd.img                                     2
 171.244018555 = 183.871864832  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  70 d0 41 d1 bc 4c da e8  46 44 d5 28 e0 9f 10 96  |p.A..L..FD.(....|
00000010  b9 1b 13 b1 e2 17 f6 90  af a2 34 a3 f9 f2 3a 30  |..........4...:0|
00000020  ff bb d6 c2 17 f4 46 b5  50 ff 8f fd b2 d3 e3 ae  |......F.P.......|
00000030  b9 d0 b6 65 95 47 c9 c2  c3 06 82 15 4e ed 7d 72  |...e.G......N.}r|
00000040  6e ef 6f 96 30 5f e0 77  f8 a3 6a be 0f dd 79 88  |n.o.0_.w..j...y.|
00000050  de 7e d1 6a 2b 43 a1 ee  8a 57 a4 e9 b3 cc c4 37  |.~.j+C...W.....7|
00000060  09 1e b6 95 89 7e 72 72  f2 f2 b8 47 c6 63 ff 5d  |.....~rr...G.c.]|
00000070  4a 44 b4 df 4a 27 5f df  0c 73 3b 6f eb 99 76 f9  |JD..J'_..s;o..v.|
00000080  df 79 69 07 17 84 11 1c  55 e3 9f 5e 99 ca e6 c7  |.yi.....U..^....|
00000090  6d 12 10 ce 07 db 71 3b  1b f6 1e e9 45 f9 71 e9  |m.....q;....E.q.|
000000a0  cd 99 57 5e 76 5c 77 cf  29 8b f9 4e b0 f1 e4 e8  |..W^v\w.)..N....|
000000b0  d0 35 ce f6 4e 07 6a 9f  47 a0 75 f1 c8 c7 db eb  |.5..N.j.G.u.....|
000000c0  9c 2f d8 57 c5 18 13 91  4d 2a 8f c7 82 dd 26 f9  |./.W....M*....&.|
000000d0  d7 f3 d7 c4 a2 79 75 c2  da 6a 42 b4 bb 72 f2 c1  |.....yu..jB..r..|
000000e0  cf be 84 10 f8 fd c9 b1  b1 a3 01 ae a9 5b b2 b9  |.............[..|
000000f0  9d 4f 51 be fd 66 97 f8  53 a0 83 b1 7d dd d3 7b  |.OQ..f..S...}..{|
00000100  30 7f 17 aa 5e 59 1b c3  3d d8 ad a6 dc 0b fb 60  |0...^Y..=......`|
00000110  da 0a f0 4b b3 63 a2 57  59 ed f1 3a 9a 18 01 f5  |...K.c.WY..:....|
00000120  c9 a0 fd 46 55 36 e5 a1  ae 86 d3 2a 2d 7a 9b 50  |...FU6.....*-z.P|
00000130  3e 8d 29 fe 27 39 da 67  5b 45 69 e3 2c f0 4f 0b  |>.).'9.g[Ei.,.O.|
00000140  92 21 df 1d 16 61 13 69  f1 ec 8a 85 2d e2 3b 0c  |.!...a.i....-.;.|
00000150  0c 8c 44 f9 58 6f 6e 9f  bb b5 5d 80 f8 40 c3 73  |..D.Xon...]..@.s|
00000160  73 7c 4f eb 8f f3 a4 8c  2a 98 af b1 14 fa 9d 9b  |s|O.....*.......|
00000170  f0 35 16 37 8c 3b c5 31  77 6b 60 3f 50 60 36 d7  |.5.7.;.1wk`?P`6.|
00000180  fb 39 8d 07 29 34 0e 7e  09 02 bc 00 7e f9 82 9f  |.9..)4.~....~...|
00000190  dd 0b bf 4e ae 44 13 c5  5f 50 4f ef f2 65 f3 b7  |...N.D.._PO..e..|
000001a0  e8 f0 5f a5 a0 75 02 53  3c 19 ea 41 b9 5d 20 f5  |.._..u.S<..A.] .|
000001b0  ae 2b 3a 7c 24 1d 2b 9f  e3 af b6 eb f2 52 00 01  |.+:|$.+......R..|
000001c0  c1 ff 0e fe ff ff 02 00  00 00 fe 25 9c 00 00 fe  |...........%....|
000001d0  ff ff 05 fe ff ff 00 26  9c 00 34 49 80 02 00 00  |.......&..4I....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```Dang it I thought I subscribed to this thread so I just saw it.  Anyway, that what you needed?

---

### Post by Quackers on 2011-07-12
Have you run ```
sudo update-grub
``` in the terminal? Does it find the Windows Loader as grub.cfg is run?
If it does, reboot and you should get a grub menu giving you the choice of operating system.

---

### Post by ~!geek!~ on 2011-07-12
You have got windows and ubuntu on the same drive i.e. both ubuntu and windows now share the same drive i.e. C:/ of windows. 
I personally prefer to have ubuntu and windows on completely different  drives. (to avoid conflicts, if any). I never did this. So don't know to  remove it (I m guessing there will be some folder named ubuntu or  something in c:/ but I m not sure). 

If you could successfully remove ubuntu and leave windows alone on  c:/>, you may put ubuntu on separate drive by choosing 'something  else' option while installing ubuntu11.04 or by choosing 'advanced' or  'manual partition' in ubuntu 10.10 n before. This will be the last  option in the list in all cases, in general. 
After selecting this you will be shown the current partitions. Do take  care while partitioning there so that you don't hurt your data. Follow  some instructions if you find on forums or google to do this safely.

You may keep your installation the way you have right now if you don't have any problem with that.

About not able to have windows in grub listing, you may follow links in above post to update grub.

---

### Post by kbagastro on 2011-07-12
```

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done


```  that's what it gave me.

---

### Post by Quackers on 2011-07-12
That's good :-)
If you reboot now you should get a grub menu giving you the choice of which system to boot. Ubuntu will be the top (highlighted) option.

---

### Post by kbagastro on 2011-07-12
Rebooted...nothing. My 'compaq' boot screen comes up, monitor goes blank then ubuntu pops up. I have problems with my monitor if I suspend/hibernate. It won't come back on when pc does. Could that be a problem or is grub just not working you think?

---

### Post by Quackers on 2011-07-12
Do you know why the boot flag is set on sda6? I would expect it to be set on sda1, as that's where XP's boot files are, but that shouldn't stop grub showing its face.
There are a couple of anomalies with your partitions.
sda1 appears to be Windows XP, but you also have sda5 and sda6 as Windows type partitions. I presume sda5 is a recovery partition of some kind (as it's not being mounted), but I would expect this to be a primary partition, not logical.
Is sda6 a data partition of some kind?

---

### Post by kbagastro on 2011-07-12
Originally in windows before I installed Ubuntu I made my partitions.  I had about 20gigs for Windows, 5 for linux, and the rest was to be file storage.
  Sda6 was the partition I created for windows in windows. Sda5 is a partition also made in windows. It was going to be where I put Linux until I realised that's too small. There is nothing on it, it was just never deleted. Sda7 is the parition that linux created on it's own, at least I don't remember making it. I set the sda6 as bootable because initially sda1 didn't look like it had any info on it and it was where I thought XP was installed. I just switched them, tried rebooting and still nothing.   
Disk Utility says that neither drive is mounted.  I've mounted them before, but when I reboot it un-mounts them?

---

### Post by Quackers on 2011-07-12
So the boot flag is now set on sda1, yes?
I think we can purge and re-install grub to make sure that's ok first.
Go to the guide below and scroll down to the 
"Purge & Reinstall without Chroot" in red, and then use steps 2 to 5 in the following CHROOT section.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by kbagastro on 2011-07-12
Yea sda1 has boot flag. Followed 2 through 5. Restarted. Straight to Ubuntu she went.

---

### Post by Quackers on 2011-07-12
And the update-grub is finding the Windows Loader too.
It may be something to do with those partitions but I'm not sure at all.
I'll ask a couple of people to have a look at the thread and see what they think, though I don't think they are online at the moment.
Keep watching :-)

---

### Post by kbagastro on 2011-07-12
Will do! Thanks for all the help! I wish the world wasn't so freaking Windows dependent ha.  I'd just rid my self of it completely!

---

### Post by coffeecat on 2011-07-12
Hi, I'm one of the people Quackers contacted.

Tbh, I'm a bit mystified as to why your grub menu is not appearing. Os-prober is finding your Windows sda1 boot partition so the grub menu *ought to* appear.

I wonder....

> **kbagastro said:**
> Rebooted...nothing. My 'compaq' boot screen comes up, monitor goes blank then ubuntu pops up.

... if the monitor is blanking out during the 10 seconds that the grub menu is on screen. How long is the monitor blank for? You could try setting the grub menu timeout to be longer than the usual 10 seconds, but let's first see what is in your grub default file. Post the output of:

```
cat /etc/default/grub
```

---

### Post by kbagastro on 2011-07-12
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```there you go.  Also blank for about 10 seconds or so. give or take

---

### Post by coffeecat on 2011-07-12
That looks to be a standard /etc/default/grub which is what I expected, so...

I must admit I'm fishing in the dark here, so I really don't know whether this will help, but how about changing the timeout to 30 seconds? Edit /etc/default/grub with:

```
gksudo gedit /etc/default/grub
```

Change this line:

```
GRUB_TIMEOUT=10
```

To:

```
GRUB_TIMEOUT=30
```

Then run:

```
sudo update-grub
```

What happens then? Does the grub menu appear? If not, does the screen stay blank for the same length of time, or longer? Does bootup take longer?

---

### Post by oldfred on 2011-07-12
Coffeecat has some suggestions on seeing grub's menu.

But I do see two issues with your sda1 windows install. It says it was installed to sda3? And the boot script shows under operating system a blank. Mine shows Windows XP.
 Your boot.ini:

> [boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)[COLOR=Red]partition(3)[/COLOR]\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)[COLOR=Red]partition(3)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 


If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

> sda1: _________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    [COLOR=Red]Operating System:  [/COLOR]
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


From mine:
>     Operating System:  Windows XP


To fix how windows sees its install in sda1 you may need to run fixBoot from the windows XP CD. These are all the repairs, try just fixboot & chkdsk first.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

That the boot script could not mount sda5 says there is an issue. If you have no data in it I would delete it as that may be causing some of the problems.

---

### Post by kbagastro on 2011-07-12
Changing the grub_timeout just made boot up longer.  My monitor says there is no signal and goes to orange light and blank screen.  As far as editing boot.ini in windows. I don't have a boot disk or recover disk. I used a friends old xp disk awhile ago to do a fresh install, I may be able to get it again. Also according to disk utility I don't have a sda3. There is sda/1,2,5,6,7,8?

---

### Post by Quackers on 2011-07-12
That's the significance of the boot.ini that oldfred mentions. Windows is looking for files in a partition that doesn't exist, I suspect.

---

### Post by kbagastro on 2011-07-12
Can I change it if I don't have a disk?  Would I be able to do more if I used grub gfx?

---

### Post by oldfred on 2011-07-12
You can use gedit to modify it if you just change the 3 to 1 in both places. Do not add or delete lines. You do have a back up of it in your boot script and posted above in case it gets saved incorrectly. Still better to use nano editor from command line, but a bit more complex to create a mount for your cdrive, mount it & then edit boot.ini that is in your cdrive.

---

### Post by kbagastro on 2011-07-12
Ok.  This is getting complicated for my noob blood ha. Please excuse my denseness but can you give me a blow by blow?

---

### Post by oldfred on 2011-07-12
I do not know how Nautilus sees your c: drive. I mount mine so I can not use my example. Most see it as 233GB or 33GB entry or whatever size the windows partition is, on the left panel in Nautilus - file browser.

To be able to edit you will have to be at sudo (gksudo for gui apps)and in Nautilus. Do not do anything else while in this mode and be careful not to accidentally move any windows files. Linux shows all the hidden system files that windows protects you from. From terminal run this:
```

gksudo nautilus
```Then find windows on left panel, double click on it and in right panel should be all the windows files & folders at windows top level or root. double click on boot.ini, it may ask run or display, you want display. Then just change 3's to 1's and save, close nautilus and close terminal.

---

### Post by kbagastro on 2011-07-12
this is what popped up...

---

### Post by oldfred on 2011-07-12
You should see the sda1 partition as 97GB or 100GB on left panel. 

Since script had trouble mounting sda5, perhaps you are not able to mount any of the windows partitions?

If you have nothing in sda5, use a liveCD to boot and in gparted click on swap, right click and swapoff to fully unmount extended partition. Then you should be able to delete sda5. If gparted shows any error icons next to partitions post a screenshot of that. And right click on them to see what they say.

---

### Post by kbagastro on 2011-07-12
If i just click on my home, my windows partitions are mounted. It looks  like almost all of my windows files are on sda6, but some including my  boot.ini are in sda1. Can't I just move the 'leftovers' to sda6?

---

### Post by oldfred on 2011-07-12
Windows only boots from a primary partition. You should not move windows files. It becomes a major kludge to get XP to work in a logical partition and it is not then supported by Microsoft.

---

### Post by kbagastro on 2011-07-13
Ok. So should I still go into boot.ini and change 3's to 1's?

---

### Post by kbagastro on 2011-07-13
New problem...I was reading on a forum that if grub menu isn't coming up during boot to try and hit SHIFT. I did that and it gave me ERROR: unknown filesystem
then gives me place for command 'grub rescue>'. I didn't know what command to use so I tried rebooting and it just throws me back to that screen, it won't finish booting. What the hell did I do!?

---

### Post by oldfred on 2011-07-13
From grub rescue you should be able to manually boot or you can reinstall grub2's boot loader to the MBR.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kbagastro on 2011-07-13
I was looking into that solution and when I checked to see what the partition drive for ubuntu was I noticed the drive letter changed. It used to be 7 I believe. Now it's 6. The drive storages are all the same, but the names are different. Does that matter? 
 Also, if there was a way to just delete ubuntu, would windows come back online or would it still be messed up? I'm just thinking deleting and starting back from windows then reinstalling ubuntu from scratch would be easier?  I have no files on the ubuntu drive that I care about.  There isn't anything in my windows drive I care about either really.  I left it blank in case something happened.  I really don't want to reinstall windows, it's a pain in the *** and takes too long.  Ubuntu on the other hand takes 20 minutes if that.  Just trying to see what all my options are. Thanks again for all your help!!

---

### Post by oldfred on 2011-07-13
If you remove Ubuntu, it will not restore the winodws boot loader. You can use the XP install disk and run fixMBR to restore the windows boot loader. That will also test if windows is working.

You can install lilo's boot loader from the Ubuntu cd.
Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

You can just delete all the Ubuntu partitions and reinstall to the free space. Be careful not install to entire disk or entire partition.

I prefer to partition in advance so I have control over partition sizes.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by oldfred on 2011-07-13
@budde it would be better to have started your own thread. Boot problems are mostly unique and then it gets difficult to resolve who's issue is whos.

You are missing two of windows boot files, which with win7 are usually in a separate boot/recovery partition.
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You need to run BootRec.exe /FixBoot and repair/create the BCD from a win7 repair Cd.
oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

You also have one large drive with one large partition. You may want to read this.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by kbagastro on 2011-07-13
So if I reinstall ubuntu can I just overwrite the current partition it's on? Or would it not give me the option?  Or would it just be easier to restore grub 2 then work on previous windows problem again?  I don't want to take the easy way out, but at the same time I don't want to spend forever trying to fix something that can't be fixed. What would oldfred do? :)

---

### Post by oldfred on 2011-07-13
I would partition in advance and then install to those partitions. If you are satisfied with current partitions then you can reinstall to them

You have to use manual install (Something else in Natty) and choose a partition for / (root) and what format. It will find swap if you have it already created. The advantage of manual partitioning is you can also create /home in another partition. But if saving most of your data in a shared NTFS you do not absolutely need a separate /home.

---

### Post by kbagastro on 2011-07-16
Ok, I'm back online.  I just 'upgraded' from livecd and everything is as it was. So we are back to original problem. Windows is on machine but grub doesn't find it, or grub menu just doesn't pop up. Where to from here?

---

### Post by oldfred on 2011-07-16
As long as grub's os-prober does not find windows, it will not show the menu. You can hold shift from BIOS until menu appears to get menu.

Did you run the fixBoot command from XP? The original boot script showed XP missing in the NTFS boot sector.

---

