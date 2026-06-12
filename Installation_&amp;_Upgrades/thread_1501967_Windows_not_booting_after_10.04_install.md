---
title: "Windows not booting after 10.04 install"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Ericj1186 on 2010-06-04
I have seen a few threads on this, but my situation is a bit different.  

I installed Ubuntu 10.04 on my GF's laptop and netbook, per her request.  She now wants to use Windows because Ubuntu isn't loading Youtube, Pogo, or any other videos she needs for class.  K, that is fine.

She boots into Windows on the Laptop, and it just restarts the computer.  Every time.  She has tried to go to the recovery screen, but it just skips her key strokes and goes to the Grub screen.  Any clue on that one?

The Netbook is weird.  It boots up Windows as a recovery for a bad install, but when we do the recovery, nothing happens.  Any ideas what to do?

---

### Post by wojox on 2010-06-04
Oops double post

---

### Post by wojox on 2010-06-04
Have you tried installing the Medibuntu repo's?

[http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

That should load up all the codecs and what not's.

---

### Post by wilee-nilee on 2010-06-05
Besides wojox instructions to get Ubuntu to play videos to get windows back in order you will have to post this script in code tags to itemize the problems and fix it.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by darkod on 2010-06-05
> **Ericj1186 said:**
>  She now wants to use Windows because Ubuntu isn't loading Youtube, Pogo, or any other videos she needs for class.  

Sometimes this is related only to the flash plugin in firefox. I have noticed on 64bit ubuntu it can be problematic, I had some issues making it work on Karmic too. After that I found a library file (flash plugin) from Adobe that you simply save in your /Home/.mozilla/firefox/plugins folder and it worked straight away.

Maybe this is all you need? If you want to give it a shot, tell me and I'll try to dig out the link.

> 
She boots into Windows on the Laptop, and it just restarts the computer.  Every time.  

Was windows booting fine after installing ubuntu? If you used the ubuntu installer to shrink the windows partition (using the guided side-by-side method) it might have corrupted some windows files. You might not notice it until you try to run windows next time.

> The Netbook is weird.  It boots up Windows as a recovery for a bad install, but when we do the recovery, nothing happens.  Any ideas what to do?

You mean the restore process looks like finishing successfully but there is no restore done? Try contacting the netbook support for that, or the manual.

You can also run the boot info script as suggested, and there might be few things to try to make windows on the laptop work.

---

### Post by Ericj1186 on 2010-06-05
Can you please post that link, darkod?

I'll reply once we try the other suggestions.  Thanks for the help.

---

### Post by kansasnoob on 2010-06-05
> **Ericj1186 said:**
> Can you please post that link, darkod?

I'll reply once we try the other suggestions.  Thanks for the help.

It's in post #4:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by darkod on 2010-06-05
> **kansasnoob said:**
> It's in post #4:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

We are actually talking about the link for a 64bit flash plugin for firefox. At least I was.

@Eric

Remove all flash players/plugins you might have installed, like flashplugin-nonfree or what ever the packages were called.

What I used is in post #3 here:
[http://ubuntuforums.org/showthread.php?t=1306113](http://ubuntuforums.org/showthread.php?t=1306113)

Just download it, unpack it, and save the .so file in the plugins folder. If it doesn't exist, just create it.

---

### Post by Ericj1186 on 2010-06-05
Some updates:

- @wojox, after using your stuff, she can view Youtube without issue.  She cannot use Pogo still (the games load up, but stops before allowing her to play) and she cannot view her class videos.  When she tries to, she gets this message saying to save a folder called nutcracker-plug.rpm.  She also gets the screenshot attached.  It's asking her for some plugins that she doesn't have.

- @wilee-nilee, here is the boot info script result.

```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

/dev/sda1    *             63   241,798,350   241,798,288   7 HPFS/NTFS
/dev/sda2         429,096,150   488,392,064    59,295,915   7 HPFS/NTFS
/dev/sda3         241,799,166   429,094,911   187,295,746   5 Extended
/dev/sda5         241,799,168   421,386,239   179,587,072  83 Linux
/dev/sda6         421,388,288   429,094,911     7,706,624  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5A9042C89042AA79                       ntfs                                     
/dev/sda2        1A4C2FDA4C2FAF85                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6c0ecf1f-0364-489b-a54a-9be0a75e9cc8   ext4                                     
/dev/sda6        24d890ea-eaa5-4db1-b302-8c0da4f52d4a   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
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
search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6c0ecf1f-0364-489b-a54a-9be0a75e9cc8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6c0ecf1f-0364-489b-a54a-9be0a75e9cc8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6c0ecf1f-0364-489b-a54a-9be0a75e9cc8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6c0ecf1f-0364-489b-a54a-9be0a75e9cc8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6c0ecf1f-0364-489b-a54a-9be0a75e9cc8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5a9042c89042aa79
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a4c2fda4c2faf85
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
UUID=6c0ecf1f-0364-489b-a54a-9be0a75e9cc8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=24d890ea-eaa5-4db1-b302-8c0da4f52d4a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 192.6GB: boot/grub/core.img
 134.7GB: boot/grub/grub.cfg
 192.7GB: boot/initrd.img-2.6.32-21-generic
 193.2GB: boot/initrd.img-2.6.32-22-generic
 192.6GB: boot/vmlinuz-2.6.32-21-generic
 141.5GB: boot/vmlinuz-2.6.32-22-generic
 193.2GB: initrd.img
 192.7GB: initrd.img.old
 141.5GB: vmlinuz
 192.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  02 00 00 00 01 00 00 00  49 6d 61 67 65 50 61 74  |........ImagePat|
00000010  68 00 00 00 00 00 00 00  70 ff ff ff 25 00 53 00  |h.......p...%.S.|
00000020  79 00 73 00 74 00 65 00  6d 00 52 00 6f 00 6f 00  |y.s.t.e.m.R.o.o.|
00000030  74 00 25 00 5c 00 53 00  79 00 73 00 74 00 65 00  |t.%.\.S.y.s.t.e.|
00000040  6d 00 33 00 32 00 5c 00  73 00 76 00 63 00 68 00  |m.3.2.\.s.v.c.h.|
00000050  6f 00 73 00 74 00 2e 00  65 00 78 00 65 00 20 00  |o.s.t...e.x.e. .|
00000060  2d 00 6b 00 20 00 4c 00  6f 00 63 00 61 00 6c 00  |-.k. .L.o.c.a.l.|
00000070  53 00 65 00 72 00 76 00  69 00 63 00 65 00 4e 00  |S.e.r.v.i.c.e.N.|
00000080  65 00 74 00 77 00 6f 00  72 00 6b 00 52 00 65 00  |e.t.w.o.r.k.R.e.|
00000090  73 00 74 00 72 00 69 00  63 00 74 00 65 00 64 00  |s.t.r.i.c.t.e.d.|
000000a0  00 00 00 00 00 00 00 00  d8 ff ff ff 76 6b 0b 00  |............vk..|
000000b0  52 00 00 00 d0 2e 9d 00  01 00 00 00 01 00 00 00  |R...............|
000000c0  44 65 73 63 72 69 70 74  69 6f 6e 00 00 00 00 00  |Description.....|
000000d0  a8 ff ff ff 40 00 25 00  53 00 79 00 73 00 74 00  |....@.%.S.y.s.t.|
000000e0  65 00 6d 00 52 00 6f 00  6f 00 74 00 25 00 5c 00  |e.m.R.o.o.t.%.\.|
000000f0  53 00 79 00 73 00 74 00  65 00 6d 00 33 00 32 00  |S.y.s.t.e.m.3.2.|
00000100  5c 00 61 00 75 00 64 00  69 00 6f 00 73 00 72 00  |\.a.u.d.i.o.s.r.|
00000110  76 00 2e 00 64 00 6c 00  6c 00 2c 00 2d 00 32 00  |v...d.l.l.,.-.2.|
00000120  30 00 31 00 00 00 00 00  f0 ff ff ff a0 3c 9d 00  |0.1..........<..|
00000130  00 3f 9d 00 48 3b 9d 00  08 00 00 00 40 2f 9d 00  |.?..H;......@/..|
00000140  d8 ff ff ff 76 6b 0a 00  34 00 00 00 68 2f 9d 00  |....vk..4...h/..|
00000150  01 00 00 00 01 00 00 00  4f 62 6a 65 63 74 4e 61  |........ObjectNa|
00000160  6d 65 00 00 00 00 00 00  c8 ff ff ff 4e 00 54 00  |me..........N.T.|
00000170  20 00 41 00 55 00 54 00  48 00 4f 00 52 00 49 00  | .A.U.T.H.O.R.I.|
00000180  54 00 59 00 5c 00 4c 00  6f 00 63 00 61 00 6c 00  |T.Y.\.L.o.c.a.l.|
00000190  53 00 65 00 72 00 76 00  69 00 63 00 65 00 00 00  |S.e.r.v.i.c.e...|
000001a0  d8 ff ff ff 76 6b 0c 00  04 00 00 80 01 00 00 00  |....vk..........|
000001b0  04 00 00 00 01 00 00 00  45 72 72 6f 72 43 00 fe  |........ErrorC..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 b4 0a 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff 02 48  b4 0a 00 a0 75 00 00 00  |.......H....u...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

Thanks for any help.

---

### Post by darkod on 2010-06-05
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    [COLOR=Red]Boot files/dirs:   /bootmgr /boot/bcd[/COLOR]

You are missing one of the vista boot files. There should also be /windows/system32/winload.exe. If you don't have vista install dvd, you can get a rescue cd image here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

There are instructions how to manually repair the boot process here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I would recommend running the /fixboot command only first, because you don't actually need /fixmbr, you need grub2 to stay on the mbr.

But if that doesn't work, run both commands and also try the automatic repair method, not just the command prompts approach.

If the script reports winload.exe being there, most probably vista will start loading fine.

---

### Post by Ericj1186 on 2010-06-06
Okay, she has the Vista fix in the process.  Any idea why she can't  watch videos for her class on Linux or access Pogo?  I used Wojox's method for installing Sun Java, and it loads a Pogo screen for a game, then stops.  See the screen shot for what happens with her school videos.

Thanks a bunch, guys.

Edit: Sorry, I can't seem to attach.  Here is the screen shot:

[IMG]http://img576.imageshack.us/img576/3064/screenshotsi.jpg[/IMG]

---

### Post by darkod on 2010-06-06
The message about not having the plugin is clear enough. Maybe they use specific type of video files.

Have in mind that even if sometimes an automatic method to install video player/plugin is offered, the procedure might not end fully or successfully. You would have to add it manually.
But at least you have the exact name of the player plugin to search for.

---

### Post by wilee-nilee on 2010-06-06
> **darkod said:**
> The message about not having the plugin is clear enough. Maybe they use specific type of video files.

Have in mind that even if sometimes an automatic method to install video player/plugin is offered, the procedure might not end fully or successfully. You would have to add it manually.
But at least you have the exact name of the player plugin to search for.

Good advice.
With a quick look at vbrick on the web it seems to be basically a MS device setup, although I did find supposed methods of getting it to run in Linux, but nothing I would attempt, since I have both MS and Linux setups.

You might be able to setup a virtual in linux with XP if you have a license, and get it to run from there so that it can be accessed without rebooting into MS.

Just a idea, but I would follow darkod's advice always.

---

### Post by Ericj1186 on 2010-06-07
Noted.

Any suggests on getting Pogo to work?

I know Java is the core to that issue, but I have no idea what to do to solve it.  I installed both Sun Java and the Icetea plugin with no help.

Thanks for the suggestions and help.

---

### Post by Ericj1186 on 2010-06-14
Any suggestions on the Pogo problem?

Also, I used the Windows recovery link, and all was good until it said "click next on the regional screen."

We never got the option to click next.  Any clue?

---

