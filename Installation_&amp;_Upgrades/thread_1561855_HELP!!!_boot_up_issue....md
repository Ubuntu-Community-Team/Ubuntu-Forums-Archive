---
title: "HELP!!! boot up issue..."
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by teckn1ckal on 2010-08-26
Hello all,
   I'm a n00b to Linux and Ubuntu for that matter and have ran into an issue with a boot up. The system has ran perfectly fine for almost 2 months with no issues.  The error I'm receiving is:

 mount: mounting /dev on /root/dev failed: No such file or directory
 mount: mounting /sys on /root/sys failed: No such file or directory
 mount: mounting /proc on /root/proc failed: No such file or directory
 Target filesystem doesn't have /sbin/init
 No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

Then it says "(initramfs)".

Now I've tried booting up the Live CD and it will not load it instead sits for a hour with Ubuntu and the dots flashing. I've tried loading the cd 3 times now and get nothing. So, everything I've looked up will not work for me due to the cd not wanting to boot. 

If anyone can please help me, I'll be super gracious.

Thank you for your time everyone!

---

### Post by quixote on 2010-08-27
It sounds like you get your initial grub menu, but then for some reason the default boot choice can't be found.  Given the CD issues, the simplest thing is to use  grub command line to help it get its tiny mind back.  These instructions are from the [community grub2 documentation]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode"), starting at the "Using CLI to Boot" section.

When the grub choice of operating systems first comes up, hit "c" for command line. (If there's no choice shown, hold down the Shift key from the beginning of booting, and a menu should appear.)

Once you see the grub> prompt, type```
ls
```to see which drives and partitions grub2 recognizes.  E.g. if it returns *(hd0) (hd0,1) (hd1,5)*, then sda, sda1, sdb5 are recognized. There's an explanation of the grub2 numbering scheme in the docs.  If you think you know which one has your ubuntu install on it, then take a look at it.  E.g. it's on the third partition of the first hard drive -- (hd0,3) in grub2-speak, /dev/sda3 otherwise -- then type ```
ls (hd0,3)/
```That will show the contents of the root directory of that partition.  If it's bootable, it will contain a "vmlinuz" and an "initrd.img".  You can also "ls (hd0,3)/boot/" to see the actual boot files, which are similar names to initrd and the like but with version numbers. You need to keep looking through the various partitions grub2 recognizes until you find these files.  This is tedious, but keep at it  ;).  In the following steps, I'll pretend the right partition is /dev/sda3 or  (hd0,3).  Substitute the right designation for your situation. Hit the enter key after each command.
```
set prefix=(hd0,3)/boot/grub
linux /vmlinuz root=/dev/sda3 ro
initrd /initrd.img
boot
```
Hopefully, that will boot.  Once it does, and before you reboot, run```
sudo update-grub
```That should fix your grub entries.  If it doesn't work, you can tell it exactly which kernel to boot, which I can run through if this doesn't work.

---

### Post by Trizzy on 2010-10-05
I've been searching for a few hours on this issue. My wifes laptop is an acer travelmate 4230, with a fresh install of lucid lynx. This was bought used from a friend, so hardware failure such as the HD or Ram is a definite possibility. 

I have followed your steps, and others in similar posts. After issuing ```
initrd /initrd.img
boot
```

the computer boots back to the original problem screen, stating 

> mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg.

I can't remember exactly, but I'm pretty sure the laptop was shutdown improperly. I didn't notice any performance issues before, and made no significant changes. I think the last thing I did was install wine, but hadn't made any config changes of any kind. Also, I've attempted to run the memtest86+ (version 4.0) but being as I have never used it, I'm not sure what to expect. Should I be seeing a progress bar of some kind, or for that matter any output at all? The memtest will load to the blue screen, and from there does nothing. Some suggest running it overnight, which is on my to-do list.

Many posts suggest booting into a live CD, however when I insert my CD and tell it to boot from CD, it eventually comes back to this screen. This could be because my CD is a plain .iso and not an actual "live" CD, but its from 8.04 so I can't remember. 

My next steps are to run the 8.04 CD in the computer I'm working on now to see if it is a live-CD or an alternate install CD, and let memtest run on the troubled laptop for several hours. I'll post any updates, and thanks in advance for any advice given.

---

### Post by wilee-nilee on 2010-10-05
I use the same basic commands but include the tab to load correctly.

Manual boot from grub prompt for grub2
set root=(hd0,X)    X=the partition # of OS 
linux /boot/vmlinuz(tab=kernel) root=/dev/sdaX (enter)
initrd /boot/initrd(tab, then enter) 
boot (enter)

---

### Post by Trizzy on 2010-10-05
```
linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1
boot
```

Drops me to the same start-up screen.

> mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg. 


My 8.04 CD does not seem to be a live-CD, so I'm currently downloading 10.04 live-CD and will burn it to a CD probably in the morning. As for the Memtest86, I left it for a little over an hour before trying the [tab] suggestion, and it still gave me absolutely no output. No progress bar, no information of any kind. I'm starting to guess that means my hardware is VERY faulty? I'm not sure and I have not been able to find a relative forum post on the subject just yet.

---

### Post by wilee-nilee on 2010-10-05
If you get the live cd booted you might run the bootscript in my sig for yourself and or post it in code tags. You can generate code tags in the reply; click on the # and put the text in between.

---

### Post by quixote on 2010-10-05
Trizzy, those are the messages you get if grub is looking on the wrong partition for a bootable OS, and therefore not finding it.  Or, if you know, 100%, it's pointing to the right place then grub needs to be reinstalled.  Final possibility is, as you say, hardware problem.

I'm sure you know, but just in case anyone else reading this doesn't, I thought I'd amplify wilee-nilee's suggestion a bit. Hit enter at the end of each line.

Blue = fill in your own value, italicized inside square brackets = comment: ```
set root=(hd0,[COLOR="Blue"]X[/COLOR])                                *[X=the partition # of OS]*
linux /boot/vmlinuz*[-hit-tab-here]* root=/dev/sda[COLOR="Blue"]X[/COLOR] 
```
*[hitting tab after "vmlinuz" will autocomplete the kernel filename.  If you have several, hit it twice or three times and it will show you the choices. If you prefer, you can just type it out.]*
```
initrd /boot/initrd*[-hit-tab-here]*
boot
```

---

### Post by Trizzy on 2010-10-11
I have tried the live-CD, and still no success. Regardless of which option I try, install ubuntu, try ubuntu etc., it goes to the ubuntu screen with the loading dots, and stays there. I've tried a few options suggested by some others, enabline nomodeset options and such, but still to no avail. Hitting esc shows the screen 
```
W: Skipping nonexistant file /cdrom/dists/lucid/main/binary-i386/Packages
W: Skipping nonexistant file /cdrom/dists/lucid/restricted/binary-i386/Packages
```

I'll keep researching this and post back here if I have any changes.

---

### Post by Trizzy on 2010-10-11
I FINALLY got a live-CD to load. I read in a different thread that this error code could be from trying to install 32bit where 64bit is required. The laptop in question is a daul core, so that might be a possibility. The live-CD ubuntu-10.10-desktop-amd64.iso is what worked. I am now running some SMART disk check to see if my hard drive is at fault. I will post back here any updates I find.

---

### Post by Trizzy on 2010-10-11
Wow, this is a nice little script. One that I will definitely keep on a CD somewhere, thanks for the link to it. Here is the Results of the bootscript. Also, I ran some SMART tests, and the Hard Drive -should- be working properly. The Filesystem check however, cameback with a message saying it is not clean.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   228,489,215   228,487,168  83 Linux
/dev/sda2         228,491,262   234,440,703     5,949,442   5 Extended
/dev/sda5         228,491,264   234,440,703     5,949,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0c779683-de39-4638-9e45-59ef79be733e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c6477fab-0539-4a64-8060-ac57318ab791   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0c779683-de39-4638-9e45-59ef79be733e
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0c779683-de39-4638-9e45-59ef79be733e
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0c779683-de39-4638-9e45-59ef79be733e
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0c779683-de39-4638-9e45-59ef79be733e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0c779683-de39-4638-9e45-59ef79be733e
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0c779683-de39-4638-9e45-59ef79be733e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0c779683-de39-4638-9e45-59ef79be733e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0c779683-de39-4638-9e45-59ef79be733e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=0c779683-de39-4638-9e45-59ef79be733e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c6477fab-0539-4a64-8060-ac57318ab791 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 107.5GB: boot/grub/core.img
  81.8GB: boot/grub/grub.cfg
 107.6GB: boot/initrd.img-2.6.32-24-generic
 107.6GB: boot/vmlinuz-2.6.32-24-generic
 107.6GB: initrd.img
 107.6GB: vmlinuz
```

---

### Post by Trizzy on 2010-10-11
Solved!

I used the command [EDIT: I ran this command inside a terminal while running a Live-CD]
```
sudo e2fsck -C0 -f -v /dev/sdax
```

and when I got back into my ubuntu i ran

```
sudo update-grub
```

Thanks for everyones help, and [COLOR="Red"]anyone reading this months from now is more than welcome to PM me for help[/COLOR]. I'm no expert but I can at least try to point you in the right direction now that I've been through this. 

Again to reflect on this issue, I believe it was caused by the laptop coming unplugged, or at least not shut down properly.

---

### Post by quixote on 2010-10-12
Trizzy, great to hear you got it sorted out, and how you did it!  I didn't know that 64-bit could be required in some cases.  I thought you could always use 32-bit, although you'd lose some potential functionality.  Interesting.

---

