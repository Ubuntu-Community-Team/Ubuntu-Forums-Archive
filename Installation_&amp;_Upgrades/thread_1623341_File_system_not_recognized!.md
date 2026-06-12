---
title: "File system not recognized?!"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by smeelkin on 2010-11-16
Story:

So, a month ago I finally switched to Linux from Windows XP, something that I had been wanting to do for a long time. I decided to go with a dual-boot since I already had payed for the Windows with my Netbook. I installed ubuntu 10.10 on a new partition of the harddisk. Then I decided yesterday to install the netbook remix of ubuntu on one more partition with the minimum of 2.5 gigs. I did this from a live USB. The installer crashed inside the copying of files, and so did every other program I tried to use (I was in the tryout mode). This was probably the USB that was unreliable. I turned off the computer, and started Ubuntu desktop. Then I deleted the partition that was supposed to have the netbook remix on it, leaving a 2.5 gb free space on the drive. Everything worked fine until today.

**[SIZE="4"]PROBLEM:[/SIZE]**

When I start up my computer, this message is displayed:

> error: unknown filesystem.
grub rescue> 

When typing "ls", I'm shown this:

(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

I think this is the different partitions (the netbook came with a lot of crappy partitions for recovery and so).

How should I fix this?

---

### Post by drs305 on 2010-11-16
smeelkin,

Welcome to the Ubuntu forums.

Try this from the grub prompt. I'm guessing your Ubuntu installation is on sda5. If you know it's not, change the (hd0,5) values.

```
ls (hd0,5)/boot/grub
ls (hd0,5)/
```

After the first command, do you see dozens of *.mod files?
In the second, can you find a "vmlinuz" and "initrd.img" listing?

If yes to both, we can boot you from the grub prompt. 

If no, please boot a LiveCD, download and run the boot info script from the following link, and post the contents of the RESULTS.txt file the script generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by smeelkin on 2010-11-16
> **drs305 said:**
> smeelkin,

Welcome to the Ubuntu forums.

Try this from the grub prompt. I'm guessing your Ubuntu installation is on sda5. If you know it's not, change the (hd0,5) values.

```
ls (hd0,5)/boot/grub
ls (hd0,5)/
```

After the first command, do you see dozens of *.mod files?
In the second, can you find a "vmlinuz" and "initrd.img" listing?

If yes to both, we can boot you from the grub prompt. 

If no, please boot a LiveCD, download and run the boot info script from the following link, and post the contents of the RESULTS.txt file the script generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

I got just those results when typing :D 
I'm a newbie in this area. How do I boot then?

---

### Post by drs305 on 2010-11-16
Your system may still be intact, so type these commands at the grub prompt:

Corrected:
```
set prefix=(hd0,5)/boot/grub
**[COLOR="DarkRed"]set[/COLOR]** root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

Note it's *vmlinuz* with a "z".

If you successfully boot, run "sudo update-grub" to try to reset things.

---

### Post by smeelkin on 2010-11-16
it doesn't recognize the two commands, linux and initrd. what should i do then?

---

### Post by drs305 on 2010-11-16
> **smeelkin said:**
> it doesn't recognize the two commands, linux and initrd. what should i do then?

Run the earlier commands, then:

linux (hd0,5)/boot/vmlinuz

at that point press the TAB key and see if it completes. It may autocomplete the remainder of the kernel name (such as vmlinuz-2.6.32.25). If it does, or displays more options, continue to type until the complete vmlinuz name is entered, then add the "root=/dev/sda5 ro"  and then

initrd (hd0,5)/boot/initrd.img
and again press TAB to fill in the remainder of the name.

If they both complete, finally type "boot".

If this doesn't work, it's time to boot the LiveCD and run the boot info script.

---

### Post by drs305 on 2010-11-16
My apologies, I omitted a word in the first of the commands post:
```
set prefix=(hd0,5)/boot/grub
**set** root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

---

### Post by smeelkin on 2010-11-16
still the same,

command 'linux' not found

btw, if this doesn't work, i'm probably just gonna use a live usb to backup my files, and then reinstall ubuntu overwriting everything. using a live cd seems like too much effort for a system with so much junk on it

---

### Post by smeelkin on 2010-11-16
ok, now i got it to boot! YAY! i used insmod to load linux and ext2 and then i could use the commands initrd and linux
then i ran the sudo update-grub and it found the linux and initrd images, plus a memtest and the windows os. then i guess i should just reboot to test, right?

---

### Post by drs305 on 2010-11-16
> **smeelkin said:**
> ok, now i got it to boot! YAY! i used insmod to load linux and ext2 and then i could use the commands initrd and linux
then i ran the sudo update-grub and it found the linux and initrd images, plus a memtest and the windows os. then i guess i should just reboot to test, right?

Yes. You know how to get back to the desktop if it doesn't work. If you have to repeat the procedure report back and we'll take the next steps to restoring Grub.

Added: The extra commands were:
> insmod linux
insmod ext2

---

### Post by smeelkin on 2010-11-16
great. it didnt work. im gonna try repeating the procedure then...

---

### Post by smeelkin on 2010-11-16
i tried the whole procedure again, but this time it stops in the middle of booting, saying that the folder /dev/sda5/ro does not exist

what now?!

---

### Post by drs305 on 2010-11-16
> **smeelkin said:**
> great. it didnt work. im gonna try repeating the procedure then...

I realize it was a few posts back, but did you run "sudo update-grub" after you successfully booted?

If not, run it once you get to the Desktop. 

If you did, run this command:

```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

If that doesn't work, we may have to purge & reinstall Grub2.

---

### Post by smeelkin on 2010-11-16
yes, i did run that "successfully"
right now, the problem is the /ro folder that doesnt seem to exist. gonna have to go to sleep now though. night, and thanks so for :D

---

### Post by drs305 on 2010-11-16
Ok, good night then. But you will have to explain the "/ro" folder remark...

---

### Post by smeelkin on 2010-11-17
the /ro thing was just a typing error
so now i can manually boot this, but it comes up with the same screen, even after using the grub-update...
what to do?

---

### Post by drs305 on 2010-11-17
> **smeelkin said:**
> the /ro thing was just a typing error
so now i can manually boot this, but it comes up with the same screen, even after using the grub-update...
what to do?

Boot into your system via the command line as you have been doing. Then either:

1, Purge and reinstall Grub2. Make sure you have an Internet connection before running the commands. The first command will remove grub-pc and grub-common, the second will reinstall them. You don't have to use both names in both commands.
```
sudo apt-get purge grub-common
sudo apt-get install grub-pc
sudo update-grub
```

As you remove them, you will get a warning about losing your bootloader. Tab to OK and press ENTER.

As you install, it will ask if you want to add anything to the "linux" kernel line. Normally nothing is needed, so tab to OK and press ENTER.

You will also have to tell the install where to put Grub2. Normally it will be your sda drive. Highlight it and press the space bar to put an asterisk next to it. That is the only one you need (if Ubuntu in on one of the sda partitions). Do NOT select a partition (sda1, sda5, etc).

You are accomplishing steps 2-5 of this link:  [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

2. Run the boot info script from the following link. Paste the contents of the RESULTS.txt file here. It will tell us how your boot system is set up. Once we see it, we can recommend a fix (possibly #1).
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

We are almost done.  ;-)

---

### Post by smeelkin on 2010-11-17
so i did that and now i have this long info file. should i post all of it?

---

### Post by drs305 on 2010-11-17
> **smeelkin said:**
> so i did that and now i have this long info file. should i post all of it?

Yes, please. Copy the contents of RESULTS.txt. Open a new post, then press the # icon. It will generate  code /code tags. Paste the contents between them.

---

### Post by smeelkin on 2010-11-17
ok, here it is
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    23,069,339    23,069,277  12 Compaq diagnostics
/dev/sda2    *     23,070,720    97,702,920    74,632,201   7 HPFS/NTFS
/dev/sda3          97,703,934   312,580,095   214,876,162   5 Extended
/dev/sda5          97,703,936   301,203,454   203,499,519  83 Linux
/dev/sda6         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris
/dev/sda7         306,087,936   306,440,191       352,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6C2401142400E2C6                       ntfs       PQSERVICE                     
/dev/sda2        9CB0818DB0816F18                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3de65621-9a0e-4cf5-ac2b-cea4de5317af   ext4                                     
/dev/sda6        a2a0f6a6-f1c4-4ef0-a358-98e2c88a51a1   swap                                     
/dev/sda7        34d9b85f-98a1-41ab-b59c-0c1d04c5f843   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 3de65621-9a0e-4cf5-ac2b-cea4de5317af
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3de65621-9a0e-4cf5-ac2b-cea4de5317af
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3de65621-9a0e-4cf5-ac2b-cea4de5317af
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3de65621-9a0e-4cf5-ac2b-cea4de5317af ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3de65621-9a0e-4cf5-ac2b-cea4de5317af
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3de65621-9a0e-4cf5-ac2b-cea4de5317af ro single 
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
    search --no-floppy --fs-uuid --set 3de65621-9a0e-4cf5-ac2b-cea4de5317af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3de65621-9a0e-4cf5-ac2b-cea4de5317af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 6c2401142400e2c6
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9cb0818db0816f18
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
# / was on /dev/sdb5 during installation
UUID=3de65621-9a0e-4cf5-ac2b-cea4de5317af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a2a0f6a6-f1c4-4ef0-a358-98e2c88a51a1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 131.7GB: boot/grub/core.img
  61.0GB: boot/grub/grub.cfg
  50.8GB: boot/initrd.img-2.6.35-22-generic
 131.7GB: boot/vmlinuz-2.6.35-22-generic
  50.8GB: initrd.img
 131.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  87 9f 14 4f 29 75 7d 21  ae c9 b1 7a 4e fe 50 f8  |...O)u}!...zN.P.|
00000010  50 7b 17 5c 17 a0 5a da  33 e8 53 45 5c a9 c0 2a  |P{.\..Z.3.SE\..*|
00000020  77 e3 a6 28 3e 29 b4 6f  f5 cb 86 18 e8 2f 1d 68  |w..(>).o...../.h|
00000030  aa 92 84 fd 12 ee 68 3c  89 fe 51 bf eb bc 2b 73  |......h<..Q...+s|
00000040  c1 3b 24 bb 25 be 49 96  ad c5 ce df 04 e0 29 22  |.;$.%.I.......)"|
00000050  a9 12 cf 10 39 11 eb da  1d 1b 10 8e d9 14 dc 6b  |....9..........k|
00000060  06 70 99 0f e2 0d 56 4f  aa e5 f5 1f 86 55 3e dd  |.p....VO.....U>.|
00000070  c5 16 be 4f 72 6b 4e f7  c9 2f 7a e5 e8 58 08 f9  |...OrkN../z..X..|
00000080  03 6e d0 f2 01 62 d3 fa  8b a5 8f 99 95 ae 1d b0  |.n...b..........|
00000090  2f d8 39 6d 43 cb 4b 04  6e f1 4a 91 df 4c fb a9  |/.9mC.K.n.J..L..|
000000a0  58 10 ab cb f4 0c f7 70  3f 6f 79 41 a8 42 b7 42  |X......p?oyA.B.B|
000000b0  dd c6 f3 7b 18 2f 45 37  ef 2c 5b 13 6d 94 f0 e4  |...{./E7.,[.m...|
000000c0  51 b9 91 d6 3a c3 51 ff  d3 34 cb ae 88 ee 13 d8  |Q...:.Q..4......|
000000d0  9b c9 20 f5 02 8c 2b de  de b2 5f 3b ba e9 ca 2b  |.. ...+..._;...+|
000000e0  d3 50 fb 9d 5e 76 98 86  9b d7 f4 af 3b c8 b6 f4  |.P..^v......;...|
000000f0  c2 fc 18 27 9e cc 4f b8  1e a4 07 60 89 67 7b 71  |...'..O....`.g{q|
00000100  fd 22 ba d2 15 32 9d 64  d8 46 3e c2 ca 0a dc 4b  |."...2.d.F>....K|
00000110  78 e2 6b 4d 5c 3f 1f 49  ae 5b ed 47 42 1d c8 26  |x.kM\?.I.[.GB..&|
00000120  f8 29 94 d2 b0 5d 18 6e  5a 7a 1d ff 05 fa 45 22  |.)...].nZz....E"|
00000130  0a 9b 2f 09 62 7a f7 e5  0d f4 2b 49 dd 98 99 5d  |../.bz....+I...]|
00000140  c5 64 61 66 f5 47 78 ca  e1 d7 eb 69 0e 9a d0 37  |.daf.Gx....i...7|
00000150  ec 31 bc 17 a2 52 48 f2  27 76 86 6f cc ed 91 31  |.1...RH.'v.o...1|
00000160  d7 f9 89 70 8c f3 83 79  db e0 92 3f 62 94 fd 68  |...p...y...?b..h|
00000170  bb 32 bc b2 7f f9 b8 a0  16 05 c3 30 39 7e 1c 2d  |.2.........09~.-|
00000180  d4 07 a1 fb 05 cb d2 6d  90 6a 9b ea 13 db 93 f4  |.......m.j......|
00000190  4b ea 13 d6 14 77 96 72  99 88 9e 84 2f 2d 3f 58  |K....w.r..../-?X|
000001a0  d5 c4 65 c2 8c 4c f0 39  ab 4b 5c 7b d7 7d 79 80  |..e..L.9.K\{.}y.|
000001b0  8f 0e c6 0e ea 24 06 9a  90 f8 70 a2 74 aa 00 fe  |.....$....p.t...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 ff 27 21 0c 00 fe  |...........'!...|
000001d0  ff ff 05 fe ff ff 02 10  71 0c 00 b0 5d 00 00 00  |........q...]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by drs305 on 2010-11-17
I do not see any problems with your RESULTS.txt

Since it's still not booting normally, from a boot to your Ubuntu system (not the LiveCD) run the commands in Post #17. Make sure you have no external/removable drives plugged in, and test your Internet connection before purging grub.

---

### Post by smeelkin on 2010-11-17
hey, now it works after i did that reinstall thingy!
thanks alot!!!! :D

---

