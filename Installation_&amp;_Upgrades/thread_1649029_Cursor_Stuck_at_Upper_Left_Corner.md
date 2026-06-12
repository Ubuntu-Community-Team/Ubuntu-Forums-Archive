---
title: "Cursor Stuck at Upper Left Corner"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by Experimenter on 2010-12-19
This issue was solved On June 9th.  Root cause was Kore 2 controller device being misinterpreted as a pointing device.  I hope to eventually use the Kore as a straight-up MIDI controller in Ubuntu Studio, but that's a long way off.  For now I will unplug it whenever I boot Ubuntu Studio.

XINPUT LIST gave me the hint I needed to figure this out.

Original post and problem resolution thread follows:


====================================

Hi, I'm a total Linux newbie, but well versed in Windows.
 
Just installed Ubuntu Studio 10.10.  This was a clean install, not an upgrade..  Installation went fine, but when I boot into it, I get the cursor stuck at the upper left corner of the screen.  When I move the mouse, the cursor will move, but it immediately jumps back to the upper left corner.  I can't select anything except to open the main menu.  Then I must use keyboard cursor control to navigate.  
 
The mouse pointer problem happens with a USB trackball and a USB wireless mouse.
 
I searched here but could not find this problem in 10.10.
 
Here are my system specs:
 
Intel Q6600 quad core processor
8 GB OCZ DDR 200 RAM
PreSonus Project Studio Firewire audio and MIDI interface
ATI 5750 graphic card running two monitors, DVI and HDMI
Western Digital 750 GB SATA hard drive
PS2 keyboard
Logitec USB mouse and keyboard
Logitec USB trackball
Wacom tablet
A number of USB MIDI controllers plugged in
 
When I installed Ubuntu Studio, I selected to install everything.
 
My searches here uncovered some possible problems with the Wacom tablet and mouse cursors in prior versions of Ubuntu Studio, so I disconnected the Wacom.  Problem still happens, even after a reboot.
 
I have also brought in about 200 MB of updates with the ... what is it called... updater?  Package manager?  It nagged me, so I applied everything in the hopes that I would gain control of my mouse pointer.  The installs took a long time but were successful.  
 
However, the mouse problem still happens, even after a reboot.
 
It's unusable at this point.  Any suggestions would be appreciated.  Thanks in advance!

---

### Post by Quackers on 2010-12-19
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Experimenter on 2010-12-20
Hi Quackers, and thanks for your reply.
 
Not sure my Ubuntu Studio ISO contained a live CD or USB option.  When I boot from the DVD, there seems to be no "live" option.  There is a "Rescue a Broken System" option, but when I select that it appears to load the installer, possibly with the intent to reinstall components or the entire OS.  So I did not proceed with this.
 
Now, I can get (make) myself a live CD, but I'm figuring it will take another download.  Unless there is a "build live CD" option somehow available after I boot the OS?  Not sure how to get to it with a non-working mouse but I can try.
 
If I need to download one after all, can it be "any" Ubuntu version?
 
Thanks!

---

### Post by Quackers on 2010-12-20
I'm afraid I'm not familiar with the studio. Maybe somebody with more experience could help.

---

### Post by Quackers on 2010-12-20
Cetainly any Live cd would do for the purpose of running the boot script. That would, however, mean another download. 
During the installation, did you get any option to install a bootloader, or Grub?

---

### Post by Experimenter on 2010-12-20
Yes, I did get an option to install a bootloader or grub.  I remember thinking that it was an odd option since I had no other OS on that disk and I had always been under the impression that Grub was a bootloader.  I figured that I couldn't go wrong by taking the default, so I just hit enter to do that.  
 
I'm sorry, I can't remember my actual selection.
 
Aaaah, it just dawned on me as I was typing this, maybe doing the "install" and aiming it at my DVD burner will create a live CD/DVD?

---

### Post by Experimenter on 2010-12-20
Got it done. Sheesh, it sucks working without a mouse!
 
```

                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
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
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *          2,048 1,415,999,487 1,415,997,440  83 Linux
/dev/sda2       1,416,001,534 1,465,147,391    49,145,858   5 Extended
/dev/sda5       1,416,001,536 1,465,147,391    49,145,856  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda1        24635ab3-de22-4567-81de-b9282d5ebd7f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        06d49a31-634a-4f7f-926a-6c9f2e5c4faa   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)

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
search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
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
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
 linux /boot/vmlinuz-2.6.35-23-generic root=UUID=24635ab3-de22-4567-81de-b9282d5ebd7f ro   quiet splash
 initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
 echo 'Loading Linux 2.6.35-23-generic ...'
 linux /boot/vmlinuz-2.6.35-23-generic root=UUID=24635ab3-de22-4567-81de-b9282d5ebd7f ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=24635ab3-de22-4567-81de-b9282d5ebd7f ro   quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=24635ab3-de22-4567-81de-b9282d5ebd7f ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 24635ab3-de22-4567-81de-b9282d5ebd7f
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=24635ab3-de22-4567-81de-b9282d5ebd7f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=06d49a31-634a-4f7f-926a-6c9f2e5c4faa none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=================== sda1: Location of files loaded by Grub: ===================

 176.2GB: boot/grub/core.img
 652.9GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
   1.2GB: boot/initrd.img-2.6.35-23-generic
 176.2GB: boot/vmlinuz-2.6.35-22-generic
 176.2GB: boot/vmlinuz-2.6.35-23-generic
   1.2GB: initrd.img
   1.0GB: initrd.img.old
 176.2GB: vmlinuz
 176.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda2
00000000  90 fd 07 48 ff 04 e2 1f  40 fc 1b 88 ff 02 f1 2f  [EMAIL="|...H....@....../"]|...H....@....../[/EMAIL]|
00000010  20 66 31 65 39 83 6e 1e  07 50 3d 3b 10 73 02 31  | f1e9.n..P=;.s.1|
00000020  1b 50 9e 15 28 86 8c bf  02 f5 7d 01 e2 cf 40 fc  |.P..(.....}...@.|
00000030  0d 88 bf 03 f1 1a 20 5e  0b c4 a7 ff 30 fb 9c 04  |...... ^....0...|
00000040  e2 53 40 7c 06 88 cf 02  f1 b9 3f cc 67 84 81 fa  [EMAIL="|.S@|......?.g"]|.S@|......?.g[/EMAIL]...|
00000050  f0 61 11 a0 5d 42 40 2c  08 c4 a2 40 2c 06 c4 fc  |.a..]B@,...@,...|
00000060  40 cc 03 c4 dc 40 cc 07  c4 02 40 cc 0b c4 e2 40  |@....@....@....@|
00000070  37 81 f4 20 63 79 3c 58  1a a8 47 0a 88 25 81 58  |7.. cy<X..G..%.X|
00000080  02 88 15 80 58 11 88 65  81 58 0e 88 65 80 e6 c1  |....X..e.X..e...|
00000090  f4 5b 02 b1 36 01 ac 07  d4 a3 03 c4 5a 40 ac 09  |.[..6.......Z@..|
000000a0  c4 ba 40 ac 0e c4 2a 40  ac 0c c4 6a 40 ac 01 c4  [EMAIL="|..@...*@...j"]|..@...*@...j[/EMAIL]@...|
000000b0  aa 40 ac 0f 34 1b dd 3c  90 1d 84 b0 0d 50 af 01  [EMAIL="|.@..4..<.....P"]|.@..4..<.....P[/EMAIL]..|
000000c0  10 2b 01 b1 39 10 9b 01  b1 05 10 9b 02 b1 35 10  |.+..9.........5.|
000000d0  5b 01 b1 31 10 1b 01 b1  21 10 9b 00 ed 01 e9 83  |[..1....!.......|
000000e0  61 3b 20 76 05 8a bb 00  b1 13 10 3b 03 b1 1b 10  |a; v.......;....|
000000f0  3b 02 b1 03 10 db 03 b1  2d 50 0f 48 1d 3e ec 05  |;.......-P.H.>..|
00000100  54 e7 09 c4 de 40 ec 01  54 ef 0e 14 43 c6 d1 40  [EMAIL="|T....@..T...C"]|T....@..T...C[/EMAIL]..@|
00000110  f1 60 20 0e 00 e2 40 20  0e 02 e2 10 20 f6 07 62  |.` ...@ .... ..b|
00000120  3f 20 f6 05 ea f1 01 aa  c3 87 23 80 ea c2 81 38  |? ........#....8|
00000130  12 88 c3 80 ea 43 81 62  c8 18 a4 26 95 00 4e 03  |.....C.b...&..N.|
00000140  ea 4d 01 e2 64 20 4e 07  e2 0c 20 4e 04 e2 38 20  |.M..d N... N..8 |
00000150  8e 05 e2 04 20 4e 02 e2  78 20 ce 04 da 81 6e 5e  |.... N..x ....n^|
00000160  1e 1a ce 05 aa cb 01 e2  6c 20 ce 02 e2 02 20 2e  |........l .... .|
00000170  04 e2 22 20 ce 07 ea 47  57 5f 4f 00 37 00 f5 d5  |.." ...GW_O.7...|
00000180  01 71 2d 10 37 02 71 13  10 57 03 71 05 10 97 03  |.q-.7.q..W.q....|
00000190  71 15 10 d7 00 71 25 10  37 03 cd 47 37 af 1d 28  |q....q%.7..G7..(|
000001a0  de 06 c4 1d 40 dc 0a 94  6f 01 8a 21 e3 89 04 f0  [EMAIL="|....@...o"]|....@...o[/EMAIL]..!....|
000001b0  24 a0 be 09 40 dc 0f c4  93 81 78 0a 10 f7 00 fe  [EMAIL="|$...@.....x"]|$...@.....x[/EMAIL].....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 ed 02 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=======Devices which don't seem to have a corresponding hard drive==============
sdb 

 

```

---

### Post by Quackers on 2010-12-20
The boot script output looks ok :-)
I think you may have a graphics problem.
If you hold down the shift key during boot up the grub menu should appear. Ubuntu will be the top option and it should be highlighted. At this point press the "e" key (for edit) and in the next screen navigate to the end of the line that says "quiet splash" and using the back space delete those words and type in "nomodeset" without the quotes, then ctrl + X to boot.
There are other boot prompts you may need to explore for your graphics card.

---

### Post by Experimenter on 2010-12-20
Hi again. Okay, I did that. Interesting process, but it would be very cumbersome for somebody non-technical.
 
After changing quiet splash to nomodeset, I did ctrl-x to reboot as you said. System hung with one black screen (no signal) and the other with a horizontal band of white lines in the lower third. It looked at me like this for a few minutes with no apparent disk activity, so I hit the hardware reset key and rebooted again. 
 
Made no changes this time, and system booted okay. But upper-left-sticky-cursor problem still happens.
 
So I'm guessing that either my changes did not fix the problem or they were not made persistent across a hard boot?
 
Any other ideas? Thanks!

---

### Post by Experimenter on 2011-06-09
Greetings and long-time no speak.
 
Apologies for my absence and lack of followup on this problem.
 
So I'm "bumping" this thread from December to see if anybody else might have any ideas on this.
 
My graphic card is an ATI 5750 and the cursor sticks in the upper left corner.
 
Any thoughts?  Thanks!

---

### Post by Favux on 2011-06-09
Hi Experimenter,

When the cursor sticks in the left upper corner that usually indicates the X driver isn't feeding any information to the Xserver, at least for the Wacom tablet.  I would imagine that would be true for the USB mouse and trackball.  If that's the problem then you would need to figure which .conf file should be matching the pointing devices and placing them on the appropriate X driver in xorg.conf.d.  So you may need to determine and add the appropriate keywords for the match.

Who makes the mouse and trackball?  Do the following with the devices plugged in.

If the kernel recognizes the devices then you should be able to find the appropriate lines for them in the output of *lsusb* entered in a terminal.  Please post those.  Vendor and Product ID's will be in them.

Also let's see what pointing devices the system sees when you run *xinput list* in a terminal.

---

### Post by Experimenter on 2011-06-09
Wow, thank you for the super fast response.
 
Here are my devices:
 
1.  Logitech Trackball (my main pointing device).  This device is wired, with a USB plug into a PS2 adapter into an old PS2 KVM switch.  I was doing my initial testing with this device without switching the KVM, it's consistently set to PC1 (the workstation in question).
 
2.  I also have a Logitech wireless keyboard and mouse.  The transmitter is typically connected via USB.
 
3.  Since my original post in December, I have replaced the old Wacom tablet with a Wacom Intuos 4 but I have not yet tried Ubuntu with it.  The old Wacom and the new Wacom both have an included mouse.
 
Initially, I think it might be advisable to try to boot Ubuntu without any tablets or wireless mice, and only the trackball; then see if I can produce the output you requested.
 
And man oh man it's difficult doing anything without a mouse.  And to come back to this forum and respond (if I can't get the mouse working) will require that I swap hard drives back to my Windows 7 disks.  Safe but time-consuming.
 
I'll post back.

---

### Post by Favux on 2011-06-09
I'm no pointer guru.  In fact I do know a little about Wacom tablets so we should be able to get the Intuos4 working as a "pointing device" at the minimum.

I think this is new information:
> 1. Logitech Trackball (my main pointing device). This device is wired, with a USB plug into a PS2 adapter into an old PS2 KVM switch. I was doing my initial testing with this device without switching the KVM, it's consistently set to PC1 (the workstation in question).

2. I also have a Logitech wireless keyboard and mouse. The transmitter is typically connected via USB.

The PS2 adapter/KVM switch may be the problem with the trackball, because otherwise I'd think the Logitech wouldn't have a problem.  Then I suspect a bluetooth problem with the mouse.  Does the keyboard work over bluetooth?

If at all possible can you plug the tackball directly into a usb port?

---

### Post by Experimenter on 2011-06-09
Whoohoo!

It works!

I booted with the Wacom and wireless USB transmitter both unplugged.

Cursor was still stuck in upper left corner.

Next, I navigated to terminal and entered the XINPUT LIST command as you said, and I saw my pointers listed but also...my Kore 2 controller device was listed as a pointer.

So I unplugged its USB cable and rebooted.  Proper mouse function now!

Next question:

When I booted, Ubuntu wanted to update itself to Natty Narwall.  I said cancel, but I wonder if I should consider it since this one was built back in December.

Opinions?

And thanks for the help on the mouse, yay!

---

### Post by Favux on 2011-06-09
Nice work!

Natty has the new Unity interface.  It's sort of Ubuntu's version of Apple's Lion or HP's Web OS or Microsoft's Win 8.  Ubuntu beat everybody to the punch!

So it is a major interface change and maybe should be considered a Beta 1 version.  So it depends on what you want.  I guess I'd stick to Maverick for now until you know a little more.

---

### Post by Experimenter on 2011-06-09
Yes, the messages also indicated that a seemingly lot of stuff gets broken and/or de-installed.  I want to at least have a chance to play around with the music stuff.  So now I guess I have to see if I can get one of my audio/midi interfaces working.

Thanks again for the help!  

I'll try to apply the "[Solved]" tag to this thread now and I'll start a new thread for any other issues.

See ya around!

---

