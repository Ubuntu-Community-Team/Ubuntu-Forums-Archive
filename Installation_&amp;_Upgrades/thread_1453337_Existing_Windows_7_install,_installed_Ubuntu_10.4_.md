---
title: "Existing Windows 7 install, installed Ubuntu 10.4 Beta last night, can't get into win"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by adampyre on 2010-04-13
Hello. HELP!

I've been away from Ubuntu for a while and using windows. Well, I decided to give Ubuntu another try. Loving the beta of 10.4 so far. Didn't have to configure anything

BUT :(

I can't seem to figure out GRUB2. It won't find windows. I have 2 installations of Windows 7 on 2 separate partitions (all on the same disk) as the Linux installation.

Can anyone help me get grub to recognize both of my Windows 7 partitions before I go insane? Wait too late. Can you still help me anyways?

(I've scrubbed Ubuntu Forums, and google for the past 12 hours straight and tried a million different things, nothing helps! I'm afraid I screwed up Grub2!!!!)

Thanks ahead of time!

---

### Post by SkullTraill on 2010-04-13
Its Ubuntu 10.04 ;)

And, do you know where the GRUB file is located and the partition numbers of your WIN7 installations? If you do, just open the GRUB file, and then browse to the place where the different boot listings are locate [It will be clearly marked] Then duplicate one of the existing listings and then change the partition Numbers and descriptions. ;)

---

### Post by adampyre on 2010-04-13
Sorry, 10.04!

Well I don't know what I am doing. Menu.lst doesn't seem to exist anymore, don't know how to edit that now? I know what partitions my installations are on. I just wish Grub knew..... :p

---

### Post by SkullTraill on 2010-04-13
Isn't the file supposed to be grub.txt? I also can't remember the exact location, I'm currently on Win 7. :S

---

### Post by Cabe13 on 2010-04-13
yeah, menu.lst is a goner. you have to change the 'GRUB_DEFAULT' definition in  /etc/default/grub and run 'update-grub' afterwards. i hope that helps. i only changed it to make windows 7 the first choice in Grub and i haven't had any issues after installing ubuntu 10.04. but that's almost certainly because i didn't update grub and kept the old settings :p

---

### Post by adampyre on 2010-04-13
Hmmm. I'm looking in /etc/default/grub and there doesn't seem to be anything there about Windows 7 and I would have no clue how to add something to make it boot into windows 7 if that's required. Heres my grub file under /etc/default/:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by SkullTraill on 2010-04-13
Is that the whole file? o.O
Then something must be wrong, it must then me the menu.lst???
I have no idea :S

---

### Post by adampyre on 2010-04-13
That's the whole file, and from what I've been reading online, menu.lst is no longer included with Grub2. It's so confusing. If I was a total noob I'd be dumfounded. Well I'm a not so noob and dumfounded I guess. I've tried a dozen different things to try and get Grub2 to give me an option to boot indo both my windows 7 partitions. It's not working. :( HELP! HELP! HELP! :)

---

### Post by Cabe13 on 2010-04-13
[http://ubuntuforums.org/showthread.php?t=1452503](http://ubuntuforums.org/showthread.php?t=1452503)

i found this thread. they seem to have found a solution.

---

### Post by SkullTraill on 2010-04-13
According to what I have just gatherd, there should be a file called 40_custom. You should check in that. I think it has to do with that ;)

---

### Post by SkullTraill on 2010-04-13
Read this mate : [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by adampyre on 2010-04-13
Ok, reading those guides and fumbling around with things a bit myself and experimenting, I got 2 entries on my grub list at bootup when holding shift down. However, when I try to select either one, it attempts to load the windows 7 partition it seems and states simply on the screen "BOOTMGR is compressed". Either one. I'm goign to start googling aorudn to fix this error message, but anyone else see this? Know how to fix it?

---

### Post by kansasnoob on 2010-04-14
If you have not found a solution please post the full output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also feel free to send me a very brief PM pointing me back to this thread :)

---

### Post by Mark Phelps on 2010-04-14
I've been running multi-boot systems with Win7 for months now, and have not experienced this personnally, so I have to rely on what others have said ... and the consensus I have found is that this message is produced when you have compressed the partition containing the Win7 boot loader (bootmgr).

From what I could find, the solution was always the same -- repair the boot manager using the Win7 install DVD or Win7 Repair CD.

---

### Post by aleckb on 2010-04-14
I also attempted to install 10.04 a few days ago and now my Windows 7 will not boot.  I had 9.10 installed and Grub was working...booting both hard drives.  Everything worked fine.  I have been trying everything (including reinstalling 9.10) but not Windows 7 (yet) but it is still not working.  I am also getting the Bootmgr is compressed.  I have tried the Windows 7 disk (after trying all the bootsec /fixboot and bootsec /fixmbr) suggestions and nothing is working.  I have two harddrives and can both to the second harddrive and get into Ubuntu but still not Windows 7.  

Here is the cfg file...any ideas?  I REALLY don't want install 7 again...

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 14f88dc4-0f77-401f-aa2f-05902f2a2a76
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 14f88dc4-0f77-401f-aa2f-05902f2a2a76
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=14f88dc4-0f77-401f-aa2f-05902f2a2a76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 14f88dc4-0f77-401f-aa2f-05902f2a2a76
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=14f88dc4-0f77-401f-aa2f-05902f2a2a76 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 14f88dc4-0f77-401f-aa2f-05902f2a2a76
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=14f88dc4-0f77-401f-aa2f-05902f2a2a76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 14f88dc4-0f77-401f-aa2f-05902f2a2a76
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=14f88dc4-0f77-401f-aa2f-05902f2a2a76 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set aed857b9d8577f11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 58a85942a8591fb4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by jmoorse on 2010-04-14
> **adampyre said:**
> Ok, reading those guides and fumbling around with things a bit myself and experimenting, I got 2 entries on my grub list at bootup when holding shift down. However, when I try to select either one, it attempts to load the windows 7 partition it seems and states simply on the screen "BOOTMGR is compressed". Either one. I'm goign to start googling aorudn to fix this error message, but anyone else see this? Know how to fix it?

Found a fix!!!!  Note: Do this at your own risk.

Boot up on the Win 7 recovery disk

Delete the system reserved partition as detailed here
[http://www.sevenforums.com/tutorials/71363-system-reserved-partition-delete.html](http://www.sevenforums.com/tutorials/71363-system-reserved-partition-delete.html)

Reboot into the Win 7 recovery disk

Startup repair fixed it for me!

---

### Post by aleckb on 2010-04-15
Worked like a champ...thanks.  I kept running the startup repair and nothing was happening.  I guess deleting the 100mb partition did the trick.  Thanks again.

---

