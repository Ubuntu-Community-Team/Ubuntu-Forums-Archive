---
title: "No Grub menu"
date: 2010-01-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by code850 on 2010-01-30
Just installed lucid from lucid-desktop-i386.iso. So far so good, but grub is not working the way I'm used to it. The problem is that when I try to enter recovery mode by pressing 'Shift' or 'Esc' the system reboots instead of showing grub menu. I've checked grub.cfg file and there is an entry present for the recovery mode. Any one has similar experience and any idea how to fix this?

---

### Post by autocrosser on 2010-01-30
If you have only Lucid installed & no other OS's--you will not get a menu by default...Look at the tutorials thread here>>>  [http://ubuntuforums.org/showthread.php?t=1195275&highlight=Grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=Grub2)

---

### Post by code850 on 2010-01-30
That tutorial has no solution to my problem. According to it I had to edit /etc/default/grub and uncomment the following line in order to display grub menu:
#GRUB_HIDDEN_TIMEOUT_QUIET=true
and set its value to false, which I did and followed it with update-grub. The result is that when booting grub enters a cycle of boot and immediate reboot. The reboot take place at the moment when grub has to display the boot menu. The system is not usable now and I am reinstalling it because i don't know how to restore grub.cfg file.

---

### Post by ranch hand on 2010-01-30
Reinstalling may help, it may not.  You redo the grub.cfg file every time "sudo update-grub" is run.

Instead of throwing up your hands and reinstalling it would have been better to post your /etc/default/grub file and let someone that can read it have a look.

You are running an OS that is not half way through development.  A little patience and an expectation of problems is required.  Read the warning on the install disk.  Read the notice at the top of the menu page for this forum.  Believe them.

I have one install of 10.04 that goes back to early november when the tool chain first went up.  It still works.  The second one I put on had to be replaced as it was totally screwed.  I am running a bunch right now and they all work, today.  Tomorrow may be different.

A little information on your box would be a good idea too.  These things do make a difference.  See my sig for one way to display info on your box.  Your video card or controller is important to know.  All information will help.

---

### Post by code850 on 2010-01-31
I know that lucid is still under development but I thought basic functionalities like grub and booting should be sufficiently functional so that people can do testing. Grub is obviously broken in my system even after fresh install.

So, the problem again is that when I boot the system and want to get grub menu by pressing 'shift', the system reboots immediately befor displaying the boot menu. Consequently I can never choose recovery mode when i need to do some tweeks or recovery of the system. Normal boot is perfect. I installed lucid on a laptop that is 5 to 6 years old 'Euronote725' with lucid as the only os. Karmic was fully functional on this laptop. It has intel 855GM graphics controller, see my lspci output below for more info. 

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
01:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
01:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)


PS: You suggested to see your sig. I'm new to this forum so I don't know what 'sig' means.

---

### Post by zika on 2010-01-31
'sig'=signature, line below the post. I think he meant [this page](http://ubuntuforums.org/showthread.php?p=8191211#post8191211).

---

### Post by VMC on 2010-01-31
> **code850 said:**
> I know that lucid is still under development but I thought basic functionalities like grub and booting should be sufficiently functional so that people can do testing. Grub is obviously broken in my system even after fresh install.

So, the problem again is that when I boot the system and want to get grub menu by pressing 'shift', the system reboots immediately befor displaying the boot menu. Consequently I can never choose recovery mode when i need to do some tweeks or recovery of the system. Normal boot is perfect. I installed lucid on a laptop that is 5 to 6 years old 'Euronote725' with lucid as the only os. Karmic was fully functional on this laptop. It has intel 855GM graphics controller, see my lspci output below for more info. 

Boot your system with a LiveCD out output your **grub.cfg** file and **fstab** file from the installed OS, so we can see it. Also 
```
sudo fdisk -l
sudo blkid
```

edit:seeing that you have just 3 posts, what is you Linux experience level?

---

### Post by kansasnoob on 2010-01-31
Regarding all things "grub" related I now like to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Quite often that provides all of the info needed to see what we're dealing with. It's always a good start :)

---

### Post by ranch hand on 2010-01-31
> **kansasnoob said:**
> Regarding all things "grub" related I now like to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Quite often that provides all of the info needed to see what we're dealing with. It's always a good start :)
+1

When I mentioned my sig I was actually referring to the"Dell 480 XPS 3G ram Quad Core 2.40GHz, Radeon HD 2400 PRO, Audigy1,  3x320G HDD, 320G External".

Your lspci out put is quite nice to have.  A big help.

Please follow kanasnoobs link.  That is one great tool.

---

### Post by code850 on 2010-01-31
@VMC

Here are my grub.cfg and fstab files as well as the outputs of fdisk -l and blkid:

========================
grub.cfg
========================
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro   quiet splash resume=/dev/sda6
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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


===================
fstab
===================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=244ea055-95fc-446f-a50e-5bdb19229b5e /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b462d76c-419f-4f01-b550-060322e4ea40 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================
output of: sudo fdisk -l 
=========================
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 48.0 GB, 48004669440 bytes
255 heads, 63 sectors/track, 5836 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         912     7325608+  83  Linux
/dev/sda2             913        5836    39552030    5  Extended
/dev/sda5             913        5532    37110118+  83  Linux
/dev/sda6            5533        5836     2441848+  82  Linux swap / Solaris

==========================
output of sudo blkid:
==========================
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7794966f-f0f5-4221-b17b-2cef7ac8cc0e" TYPE="ext4" 
/dev/sda5: UUID="244ea055-95fc-446f-a50e-5bdb19229b5e" TYPE="ext4" 
/dev/sda6: UUID="b462d76c-419f-4f01-b550-060322e4ea40" TYPE="swap"


Hope this will help.

cheers

---

### Post by code850 on 2010-01-31
I checked out bootinfoscript and i think that my previous post covers most if not all the information reported by this script.

---

### Post by ranch hand on 2010-01-31
> **code850 said:**
> I checked out bootinfoscript and i think that my previous post covers most if not all the information reported by this script.
There should be some more info from the script.  Please post the results.

If there really is no more info, that in itself will tell us some things about your problem.

---

### Post by code850 on 2010-01-31
I forgot to mention that I have partitioned my drive into 3 parts: one for the root, second for the home dir and a third for the swap. Details of the partitions and their file system types are listed by below as part of the boot-info-script output:
```

============================= 
Boot Info Summary: 
==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 48.0 GB, 48004669440 bytes
255 heads, 63 sectors/track, 5836 cylinders, total 93759120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd478bc7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    14,651,279    14,651,217  83 Linux
/dev/sda2          14,651,280    93,755,339    79,104,060   5 Extended
/dev/sda5          14,651,343    88,871,579    74,220,237  83 Linux
/dev/sda6          88,871,643    93,755,339     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7794966f-f0f5-4221-b17b-2cef7ac8cc0e   ext4                                     
/dev/sda5        244ea055-95fc-446f-a50e-5bdb19229b5e   ext4                                     
/dev/sda6        b462d76c-419f-4f01-b550-060322e4ea40   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)


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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro   quiet splash resume=/dev/sda6
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=244ea055-95fc-446f-a50e-5bdb19229b5e /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b462d76c-419f-4f01-b550-060322e4ea40 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ranch hand on 2010-01-31
Boy, that all looks good to me.  I use an ATI card but I have not heard of this problem with the intel controller.

Try adding this to your /etc/grub.d/40_custom file;
```

echo "Adding Ubuntu on sda1" >&2 
cat << EOF
menuentry "Ubuntu on sda1" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Ubuntu on sda1 recovery" >&2 
cat << EOF
menuentry "Ubuntu on sda1 recovery" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro single
        initrd /initrd.img
}
EOF

```
Make sure that the preferences in gedit do not allow text wrapping.

Run "sudo update-grub" and then "sudo grub-mkconfig" after saving that file.

The entries should be at the bottom of your menu screen.

This is just grasping at straws here but the entry for normal boot should work and never need updating.  The recovery one should too but with the trouble you are having I just do not know.

Try it and see.

---

### Post by code850 on 2010-01-31
Ranch hand, I did setup 40_custom file with the code you provided. Then i did update-grub and grub-mkconfig. The new grub.cfg file was created and all went smoot. Then rebooted the laptop. Once the screen displays 'Grub' or 'loading grub' then the system reboots immediately. The process get iterated indefinitely. This is the same symptom as when i enable showing the grub menu in /etc/defalut/grub

---

### Post by ranch hand on 2010-01-31
I would chroot into the system from the live cd and run;
```

apt-get purge grub-pc grub-common

```
and then;
```

apt-get install grub-pc grub-common

```
What is happening is obviously not right.  The grub you get through the installer is not working.  Lets try one straight from the repos and see what happens.

I have to go and get fire wood.  I will be back in about 3 hours.

---

### Post by Ibidem on 2010-01-31
You edited the wrong line!  /etc/default/grub should be like this:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"

Note that the solution is to comment out GRUB_HIDDEN_TIMOUT    
 and simply  uncomment
GRUB_HIDDEN_TIMEOUT_QUIET=true
This is copy and paste from a working setup...
Basically, you told GRUB to tell how long till boot while still hiding the menu.
GRUB_HIDDEN_TIMEOUT=0
"The menu will be hidden unless a # symbol is present at the beginning of this line."

---

### Post by code850 on 2010-01-31
@Ibidem,

Commenting out GRUB_HIDDEN_TIMEOUT triggers the boot/reboot iteration.

---

### Post by code850 on 2010-01-31
@[ranch hand]("http://ubuntuforums.org/member.php?u=647614")

I did boot from live cd and chroot. Then I purged grub packages and reinstalled them. Then run update-grub but it complained about missing /dev and /proc. So i mounted these and update-grub worked fine and generated new grub.cfg. Rebooted the system and i did not notice any change. Still, when i press shift key the system reboots immediately. If i don't touch the keyboard, the system boots fine to gdm.

Now its midnight in stockholm/sweden, so i'm going to sleep.

---

### Post by ranch hand on 2010-01-31
Wow,  I am glad you are done for the night.  Have to think about this.

I sure hope that kanasnoob is still watching this.  This is weird.

---

### Post by jerrylamos on 2010-01-31
Had some "no grub menu" trouble, fiddled around with /etc/default/grub, now running O.K.  Mystery.....

Linux version 2.6.32-12-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-1ubuntu1) ) #16-Ubuntu SMP Wed Jan 27 18:34:19 UTC 2010

VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]

Jerry

---

### Post by VMC on 2010-01-31
code850, I'd like to try something if you don't mind. copy the contents below into "/boot/grub/grub.cfg", replacing the current grub.cfg file. You will have to do this usder root using sudo.
Its a streamlined version of what you have with timeout set for 11 seconds. It won't hurt anything, you issue another grub-update to recreat your grub.cfg file again:
Everything in the first CODE BLOCKS only.
```
	default=0
	gfxmode=640x480
	insmod gfxterm
	insmod vbe
	timeout=11
	menu_color_normal=white/blue
	menu_color_highlight=light-cyan/cyan
menuentry "Ubuntu" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
	linux /vmlinuz root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet
	initrd /initrd.img
}
menuentry "Ubuntu(recovery mode)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
	linux /vmlinuz root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
	initrd /initrd.img
}

```

I just want to see if grub will wait long enough for you to make your choice.
Forget about the DO NOT EDIT. When you issues a update-grub, it all goes back to the way you had it.
==============================================================================
Also, later, if that doesn't work, try chrooting into your ubuntu OS using a LiveCd and reinstall grub, using the following commands:

```
mount /dev/sda1 /mnt/
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev/pts /mnt/dev/pts
mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt/ /bin/bash
grub-install /dev/sda

if any errors, then:
grub-install --recheck /dev/sda
```

---

### Post by ranch hand on 2010-01-31
He can boot into his system if he just leaves every thing alone.  Then it goes through and boots.

There is no need to chroot (I already had him do that - I feel silly).

The problem is that he can't boot recovery because he  can't select anything.

If he does it just loops back to reboot.

Purging grub-pc and grub-common an reinstalling made no difference.  It is just really weird.

I am thinking that he needs to boot in and go to System>Administration>Login Window>Security and change it to require a password login.  Then reboot and see what happens.

---

### Post by VMC on 2010-01-31
You had him re-install grub program and grub.cfg, not re-install the grub boot loader.

---

### Post by ranch hand on 2010-01-31
This is true.  I am tired and stupider than normal.  That is a good idea.  I like the replacement grub.cfg idea too.  I have edited that bugger before (well you were around for 9.10A2).  It is a nice way to try things out.  Doesn't work?  Update grub.

I do not think it will help but it will give a little more info.  As weird as this bugger is it may even work.  At this point I am in favor of grasping at straws.

I think it is kind of like the looping gdm and wonder if plymouth is involved.  I really think that trying the password boot is a good idea too.  I just hope he does them one at a time so we know what each does.

---

### Post by VMC on 2010-01-31
> **ranch hand said:**
> This is true.  I am tired and stupider than normal.  That is a good idea.  I like the replacement grub.cfg idea too.  I have edited that bugger before (well you were around for 9.10A2).  It is a nice way to try things out.  Doesn't work?  Update grub.

I do not think it will help but it will give a little more info.  As weird as this bugger is it may even work.  At this point I am in favor of grasping at straws.

I think it is kind of like the looping gdm and wonder if plymouth is involved.  I really think that trying the password boot is a good idea too.  I just hope he does them one at a time so we know what each does.

Another thing he can try, but all hell will break loose. And that is insert debug into the grub.cfg string. You won't believe all the messages that flow out. but maybe if anything comes out then at least grub was woken up.

---

### Post by code850 on 2010-02-01
I think that neither gdm nor plymout are involved or causing the problem. Grub reboots the system_ immediately_ after i pres shift key. Rebooting happens even befor kernel boot or starting init. Therefor it is a grub problem.

---

### Post by code850 on 2010-02-01
Good news. VMC asked to test the new grub.cfg settings with timeout set to 11 seconds. Now when i boot the system grub menu is displayed nicely with two menu options: 1-ubuntu normal boot. 2- ubuntu recovery. And the count down is displayed. I selected recovery mode to see if everything working as expected, and it is. My aim is to have grub boot the default system without waiting to user input and that it displays the menu only when i press the shift key. I'm not a linux expert but my gutfeeling says that reinstalling the bootloader will not solve this problem. It may be the configuration that is causing the problem.

---

### Post by amsterdamharu on 2010-02-01
Editing the grub menu is too tedious since grub2, I don't see myself changing some bash script look like files in several different places to change a simple menu.

Therefore we have "startupmanager" a gui to edit your grub menu, it is not installed by default on my lucid/lynx but added it with synaptec and worked ok for me.

Not sure about the package name because I am not on the Lucid machine now.

---

### Post by ranch hand on 2010-02-01
So all you need do is set the time out in /etc/default/grub run update-grub and you are all set.

That is really great.

---

### Post by VMC on 2010-02-01
> **ranch hand said:**
> So all you need do is set the time out in /etc/default/grub run update-grub and you are all set.

That is really great.

Yes, someone up above suggested he change "/etc/default/grub" to a correct value.

---

### Post by code850 on 2010-02-01
Ibidem suggested to use the following settings in /etc/default/grub:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"

Again these settings trigger the boot/reboot symptom. Using these settings also trigger the same symptom:
GRUB_DEFAULT=0
 GRUB_HIDDEN_TIMEOUT=0
 #GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT="10"

The only settings working right now are the ones provided by VMC in message #22. How can we modify these settings to make grub disply its menu only in response to pressing shift key?

I also reinstalled grub in /dev/sda without joy.

---

### Post by drs305 on 2010-02-01
> **code850 said:**
> The only settings working right now are the ones provided by VMC in message #22. How can we modify these settings to make grub disply its menu only in response to pressing shift key?

Unless your Grub 2 is not working correctly, this should boot the first menuentry with no delay.
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"

```
Run "sudo update-grub" for the setting to take effect. 
And unless you are really lucky, you'll have to *hold* the shift key to display the menu since the scripts look for a "stuck" key.

---

### Post by code850 on 2010-02-01
This code works perfect:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"

Witht this code grub does not wait for key strokes and boots the default kernel. 
But if I change GRUB_TIME_OUT="0" to GRUB_TIME_OUT="5" then the 
boot/reboot thing starts again and the system is unusable.

---

### Post by drs305 on 2010-02-01
> **code850 said:**
> This code works perfect:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"


Glad the code provided works. 

For the second part, are you really using "GRUB_TIME_OUT" or "GRUB_TIMEOUT". I assume it's a typo but it would be important if it's not. 

I haven't heard anyone else having an issue such as yours based on a TIMEOUT entry. If you are still seeking a solution, did you try to alter any of the scripts manually which may have altered any of the code referencing "GRUB_TIMEOUT"?

---

### Post by code850 on 2010-02-01
As far as i can tell there is no typo error in the code. And i did not alter any code in any script. The symptom shows up even after fresh apt-get install grub. Anyway, I'm using linux since 1997 and have never came across something like this before.

---

### Post by drs305 on 2010-02-01
> **code850 said:**
> As far as i can tell there is no typo error in the code. And i did not alter any code in any script. The symptom shows up even after fresh apt-get install grub. Anyway, I'm using linux since 1997 and have never came across something like this before.

The only thing I can think of that might cause the problem would be if there is a graphics issue with the Grub 2 menu that would cause the system to crash and reboot. However, if you can hold down the shift key and the menu displays properly I would think that could also be ruled out unless it was an initial timing issue of some sort with the video mode.

> 
Anyway, I'm using linux since 1997 and have never came across something like this before.
Sometimes being unique isn't a good thing.  ;-)

---

### Post by VMC on 2010-02-01
> **code850 said:**
> As far as i can tell there is no typo error in the code. And i did not alter any code in any script. The symptom shows up even after fresh apt-get install grub. Anyway, I'm using linux since 1997 and have never came across something like this before.
Well at least you know the area where the bomb went off. Now regarding 1997. That was the year of the last car I bought and back then we didn't have grub2(fortunately), we had grub, lilo.

Don' take my lead, but I have my own way of dealing with grub2.

Thanks to the likes of drs305, [Herman]("http://members.iinet.net/~herman546/index.html"), and others, grub2 has become more manageable.

---

### Post by code850 on 2010-02-01
It must be late 1998 that i started with suse. Now i remember my ex girlfriend leaving in 98. Then i had plenty of time and decided to check out linux to play with. And i found 'lilo' sounds funny.

I may be ignorant here, but i noticed the following error message displayed immediately after grub loading. I dont know if it is related to grub or not:
mount: mounting none on /dev failed. No such device.

I will stick to VMC settings for the moment until i get new ideas.

Thanks for the help guys, i really appreciate it.

---

### Post by meierfra. on 2010-02-01
Let' s see whether the rebooting is caused by pressing the "esc" or "shift" keys.  Use this for your grub.cfg:


```

        echo "Wait for the count down to start and then press Esc"
        sleep 5
        sleep --verbose --interruptible 10
        echo  "Good. Pressing esc during sleep did not reboot the computer. Wait for further instructions."
        sleep --verbose 10
        echo  "Hold down the shift key until further notice."
        sleep 5
        sleep --interruptible 10
        echo  "Good. Holding the shift  key during sleep did not reboot  the computer. Wait for further instructions."
        sleep --verbose 10
        echo "Hold down the shift key until further notice"
        sleep --verbose 5
        if keystatus; then
           if keystatus --shift; then
              echo "Good. Grub detected the shift key and did not reboot"
           else
             echo "Grub did recognize the shift key and did not reboot"
           fi
        else
            echo  "Grub did not detect any key and did not reboot."
        fi
        echo "The Grub menu should appear in 10 seconds"
        sleep --verbose 10

     	default=0
	gfxmode=640x480
	insmod gfxterm
	insmod vbe
	timeout=11
	menu_color_normal=white/blue
	menu_color_highlight=light-cyan/cyan
menuentry "Ubuntu" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
	linux /vmlinuz root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet
	initrd /initrd.img
}
menuentry "Ubuntu(recovery mode)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
	linux /vmlinuz root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
	initrd /initrd.img
}
```

This is the same file VMC gave you. plus some key testing at the beginning.  After you saved the above code as /boot/grub/grub.cfg" reboot(don't run "update" grub). Then follow the instruction on  your monitor and lets us know exactly what happened.

---

### Post by code850 on 2010-02-01
Good day Meierfra, I test your code by booting the system with grub.cfg code you provided. It asked me to press esc key until further notice. This was fine, no errors. Then it asked to press shift, again no errors. Then it asked to hold down shift key, which was fine as well. So, grub did detect the esc and shift without rebooting. Finally, grub menu was displayed and i could boot default kernel.

---

### Post by meierfra. on 2010-02-01
That's good news. Let's try this:

Take VMC's code for grub.cfg  and add this to the beginning of the file:

```

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
```


Reboot. Boot  once with holding the "shift" key and once without. Report exactly what happened in each case.

Just as an explanation. I'm trying to figure out what exactly makes your computer reboot. Then, hopefully, we'll find a way to hide the grub menu.

---

### Post by meierfra. on 2010-02-01
If  the tests from my previous post did not cause any reboot, try this:

Use the same code for grub.cfg as in the previous post, but change the line

timeout 11

to

#timeout 11.

Reboot, once with holding  the shift key and once without.

---

### Post by code850 on 2010-02-01
I changed 

timeout 11 
to 
#timeout 11

Grub menu gets displayed whether i hold shift key pressed or not.

---

### Post by meierfra. on 2010-02-01
Maybe there was some miscommunication. Anyway, try this  code

```

   timeout=0
if keystatus; then
   if keystatus --shift; then
      set timeout=-1
   fi
fi
 

        default=0
	gfxmode=640x480
	insmod gfxterm
	insmod vbe
       #timeout=11
	menu_color_normal=white/blue
	menu_color_highlight=light-cyan/cyan
menuentry "Ubuntu" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
	linux /vmlinuz root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet
	initrd /initrd.img
}
menuentry "Ubuntu(recovery mode)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
	linux /vmlinuz root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
	initrd /initrd.img
}

```

for grub.cfg. boot once with holding the shift key and  once without,

---

### Post by code850 on 2010-02-01
Super, it works. Now grub menu gets displayed only when i press the shift key. Thus, without touching the keyboard grub boots the default kernel perfectly. So, what should i learn from this? and why i'm seemingly the only one affected?

---

### Post by meierfra. on 2010-02-01
> Would it work if we just put timeout=-1 and remove all the if/then statements?
No. Then you will always get the Grub Menu. 

> what should i learn from this? 

Not much. We  still have no clue what caused the problem.  
Also your current  grub.cfg will be overwritten  during the next kernel update.  So, if you don't mind,    I would like to try  to  fix up the automatically generated "grub.cfg".  Since I don't know the current state of all the configuration files, I suggest to start from beginning:

```
sudo apt-get purge grub-pc grub-common
```
make sure to select "yes" when asked whether files should be removed.

```
sudo apt-get install grub-pc grub-common
```

Post your new grub.cfg

Then reboot while holding down the shift key.

---

### Post by code850 on 2010-02-02
Good morning Meierfra,

I did purge grub-pc and grup-common then reinsttalled them. New installation did not report any errors. But now the problem is back: when hold down shift key during boot, the system reboots immediated after display 'loading grub'.

 Here is my new grub.cfg:

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux    /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro   quiet splash
    initrd    /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    echo    Loading Linux 2.6.33-020633rc6-generic ...
    linux    /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

### BEGIN /etc/grub.d/40_custom.old ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.old ###

---

### Post by meierfra. on 2010-02-02
Well I still have no clue what is causing the problem.  Try this as grub.cfg:

```
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
[COLOR="Red"]#if loadfont /usr/share/grub/unicode.pf2 ; then[/COLOR]
set gfxmode=640x480
insmod gfxterm
insmod vbe
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
fi
[COLOR="Red"]#fi[/COLOR]
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.33-020633rc6-generic ...
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.32-12-generic ...
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.old ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.old ###
```

---

### Post by code850 on 2010-02-02
No go. The new grub.cfg behaves exactly the same as the previous one. When i press shift key, the system reboots.


It may be worth noting that early on when i started searching for information in google to solve the problem i found a posting from someone who had relatively comparable issues with grub. There was a suggestion to add a couple of words at the beginning of grub.cfg file. Both words has something related to 'keyboard' (not boot arguments like 'noacpi' etc..). I don't remember what these words were. But I remember that my grub started to behave differently. Here, when i pressed shift  key, system did not reboot. Instead, nothing was displayed on the screen. Likely the menu was activated but not displayed because when i pressed 'enter' the system booted normally. I hope this info will help  a little. If i get a list of possible 'words' or 'drivers' that can be added to grub.cfg i may identify them immediately. But i don't know where to find such a list.

cheers,

---

### Post by drs305 on 2010-02-02
> If i get a list of possible 'words' or 'drivers' that can be added to grub.cfg i may identify them immediately. But i don't know where to find such a list.


There are at_keyboard and usb_keyboard modules which can be loaded (they are in the /boot/grub folder). Do either of those sound familiar?

---

### Post by code850 on 2010-02-02
Yes, at least the first one. I will try it now and report later when done.

---

### Post by code850 on 2010-02-02
I did this:

update-grub
rebooted the laptop and held down shift: system reboots immediately.

then I added these two lines to grub.cfg:

insmod at_keybord
terminal_input at_keyboard

restarted the system and held down the shift key. No reboot. Grub does not wait (no paus) and boots the default kernel. Was it expected?

---

### Post by meierfra. on 2010-02-02
> restarted the system and held down the shift key. No reboot. Grub does not wait (no paus) and boots the default kernel. Was it expected?
At least I'm not surprised. I think we ruled out keyboard problems with the test in my first post. So "insmod at_keybord"  did not solve a key_board problem, but introduced one.The shift key seems to be no-longer  recognized.

Anyway, try this code:

```

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
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
[COLOR="Red"]#set locale_dir=/boot/grub/locale
#set lang=en
#insmod gettext[/COLOR]
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
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.33-020633rc6-generic ...
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.32-12-generic ...
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.old ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.old ### 
```

---

### Post by code850 on 2010-02-02
No go. When booting with shift key pressed, the system reboots immediately.

---

### Post by meierfra. on 2010-02-02
> No go. 
Darn.  I really don't see anymore places which could be causing the problem.
So lets try the debug mode.  This will produce lots of messages during booting and they will pass by really fast. If you are lucky you might be able to read the message just before the computer reboots.
Use:

```
[COLOR="Red"][COLOR="Red"]set debug=all[/COLOR][/COLOR]
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.33-020633rc6-generic ...
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.32-12-generic ...
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.old ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.old ### 
```

---

### Post by code850 on 2010-02-02
I will try it, if i manage to catch any errors by eye then i report it back. If the text goes to quick, i will  videotape the boot process and analyze it. Results will come tomorrow.

---

### Post by VMC on 2010-02-02
> **code850 said:**
> I will try it, if i manage to catch any errors by eye then i report it back. If the text goes to quick, i will  videotape the boot process and analyze it. Results will come tomorrow.

I suggested that a few pages ago as a last resort. Get ready for either/or several minutes and tons of output messages. I doubt you can make anything out, but its worth a try.

---

### Post by meierfra. on 2010-02-02
> I suggested that a few pages ago 
Sorry, I should have acknowledge that. I didn't even know about "debug" before I saw your post. 

> I doubt you can make anything out, but its worth a try. 

That's my feeling, too

> as a last resort

If "debug" does not yield anything new ,  we'll just have to systemically remove parts of code until we find the  line of code which causes the reboot.  The difference between the code which works and the one which doesn't isn't all the big. So I'm sure we will find the offending line.

---

### Post by code850 on 2010-02-03
Good mornin/evening (i don't know your location;),

I setup grub with debug on. The output scrolled so fast that not even my camera could catch it. 

By alternating pressing 'pause' and 'enter' i managed to read part of the output. I id that at least 10 times. The only error i found is the following:

disk.c:245: Opening 'hd0'
fs.c:84: Detecting ext2
fs.c:90: ext2 detection faild    <====
diskk.c.333:closing 'hd0'


I noticed several times that there is a pause at 'fs.c:84: Detecting ext2', and that this message was the last one I could see. I also noticed that the last module that gets loaded prior to reboot was the video_fb module. Are there any other modules are supposed to be loaded after this one?

---

### Post by VMC on 2010-02-03
> **code850 said:**
> Good mornin/evening (i don't know your location;),

I setup grub with debug on. The output scrolled so fast that not even my camera could catch it. 

disk.c:245: Opening 'hd0'
fs.c:84: Detecting ext2
fs.c:90: ext2 detection faild    <====
diskk.c.333:closing 'hd0'
...

Since debug is an undocumented option, those "fs.c:84" errors could mean almost anything. from 'c" library, to "fs" filesystem. Who knows.

Maybe "Ctrl+s" will suspend the data flow. If so the "Ctrl+q" should restore flow. Or try "Pause" key. It would be nice to be able to redirect the data flow to a file.

---

### Post by meierfra. on 2010-02-03
> Since debug is an undocumented option, those "fs.c:84" errors 
I looked at the source code and  found a file with the name "fs.c". So I guess "fs.c:84" refers to line 84 of  that file. I don't have time right now, but will have  a closer look later. In  the mean time,  lets see whether we can find  the offending line by a process of elimination. Try this code:



```
#
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.33-020633rc6-generic ...
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.32-12-generic ...
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.old ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.old ###
```

---

### Post by meierfra. on 2010-02-03
> fs.c:90: ext2 detection faild <====
This  message is  indeed from line 90 of the fs.c.  But I get the same message during boot up. So I think its harmless.

> the last module that gets loaded prior to reboot was the video_fb module. 

This seems to indicate that reboot occurs in this part of grub.cfg:

```
insmod vbe
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
fi
fi
set locale_dir=/boot/grub/locale
set lang=en
insmod gettext
```


Try the  code from my last post, I'm pretty sure that  your computer will still reboot when you boot with holding down the "shift" key. But it will narrow  the  area we have to search by quite a bit.

---

### Post by code850 on 2010-02-04
Hi,
I tried your code listed in your message #62. With this code system reboots continuosly, with or without pressing 'shift' key.

---

### Post by meierfra. on 2010-02-04
> With this code system reboots continuosly, with or without pressing 'shift' key. 

Sorry. I took out some parts of of the code which was clearly needed later. I try to be more careful.

Next attempt:

```
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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
insmod gfxterm
insmod vbe
[COLOR="Red"]#if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
#terminal gfxterm
#fi[/COLOR]
fi
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.33-020633rc6-generic ...
linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro quiet splash
initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
recordfail
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
echo Loading Linux 2.6.32-12-generic ...
linux /boot/vmlinuz-2.6.32-12-generic root=UUID=7794966f-f0f5-4221-b17b-2cef7ac8cc0e ro single
echo Loading initial ramdisk ...
initrd /boot/initrd.img-2.6.32-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7794966f-f0f5-4221-b17b-2cef7ac8cc0e
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom.old ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.old ###
```

---

### Post by code850 on 2010-02-04
Good job.

Holding down shift key during boot brings up grub menu. I booted recovery mode and all was fine. Rebooted and selected default kernel and this was perfect too. Then rebooted without touching the keyboard, grub booted default kernel automatically. It worked perfect.

What's next?

---

### Post by meierfra. on 2010-02-04
Ok.  Open the file 00_header via


```
gksudo gedit +92 /etc/grub.d/00_header
```

Look for

```

  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
```

(it should be in the  middle  of the screen)

and change it to

```
 
  [COLOR="Red"]#[/COLOR]if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  [COLOR="Red"]#[/COLOR]fi
```



Save the file. Then

```
sudo update-grub
```

and reboot  while holding down the shift  keep.  If the computer still reboots,  then edit  the same block of code in  "00_header" one more time so that it looks like

```
 [COLOR="Red"]
  #[/COLOR]if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
  [COLOR="Red"]#[/COLOR] terminal gfxterm
  [COLOR="Red"]#[/COLOR]fi
```

and run "update-grub" again.  

That should be it. 
 You might consider filing a bug-report at launchpad.

---

### Post by code850 on 2010-02-04
[COLOR=Red]It worked with the this code:

  #[/COLOR]if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
   terminal gfxterm
  [COLOR=Red]#[/COLOR]fi
So, disabling the if/then statement while leaving 'terminal gfxterm' untouched the system
boots nicely and displays grub menu when shift key is held down.

Do you want me to try commenting 'terminal gfxterm' and see what happens?

---

### Post by code850 on 2010-02-04
I've just received grub-pc and grub-common updates. Installed them and 00_header file got overwritten. Then I rebooted the system with the new 00_header file and all  seems fine. I can hold down shift key without triggering system reboot. Also, grub menu gets displayed only in response to shift key press. 

The 'if terminal_output gfxterm;' statement is present in the new 00_headers file.

---

### Post by code850 on 2010-02-04
I also noticed that the new grub throws this message: 'unknown command terminal'.
 It does'nt seems to be harmful, but it is spoiling the aesthetics of my boot ;)

---

### Post by zika on 2010-02-04
> **code850 said:**
> I also noticed that the new grub throws this message: 'unknown command terminal'.
 It does'nt seems to be harmful, but it is spoiling the aesthetics of my boot ;)Last version of GRUB that came through upgrade spoiled everything... (today...)

---

### Post by code850 on 2010-02-04
Really, what happend to your grub? what are the symptoms?

Mine works fine now after the update. I must admit that i have the most basic setup: no other os, no themes, etc.

---

### Post by zika on 2010-02-04
Mine is totally default (with Vista that I did not opet for months, I used to update it every month or so, but, now, I do not do event that) with exception that I disable recovery entries.  It took me patience and experience to get to machine once it was  upgraded. I had to disable splash and I still do not get any messages  while booting, GRUB menu is there all the time... I got to boot into  2.6.32-12 and 2.6.33-999, eventually, but, it was rough ride. The sunny  side of that is that I've tried LiveCD from 02.2010... Something is in  transition in GRUB so, I keep the fingers crossed for the guys  developing it...
I have an additional problem that occurs on boot, namely my (brand new) Samsung 2343BW doesn't get information about that it is hooked to Digital output of ATI HD3650 Radeon 512M and I have to either wait until it does or toggle switches, so, it makes a difficult boot even more difficult...
Interesting piece from dmsg> [drm] radeon defaulting to kernel modesetting.
[   12.887017] [drm] radeon kernel modesetting enabled.
[   12.887214] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.887220] radeon 0000:01:00.0: setting latency timer to 64
[   12.891981] [drm] radeon: Initializing kernel modesetting.
[   12.892007] [drm] register mmio base: 0xFEAF0000
[   12.892009] [drm] register mmio size: 65536
[   12.892821] ATOM BIOS: 9598.10.88.0.3.AS01
[   12.892828] [drm] Clocks initialized !
[   12.893750] [drm] Detected VRAM RAM=256M, BAR=256M
[   12.893755] [drm] RAM width 128bits DDR
[   12.899550] [TTM] Zone  kernel: Available graphics memory: 1545658 kiB.
[   12.899569] [drm] radeon: 256M of VRAM memory ready
[   12.899571] [drm] radeon: 512M of GTT memory ready.
[   12.899635] [drm] Loading RV635 CP Microcode
[   12.899640] platform radeon_cp.0: firmware: requesting radeon/RV635_pfp.bin
[   12.930155] platform radeon_cp.0: firmware: requesting radeon/RV635_me.bin
[   12.933480] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   12.966627] [drm] ring test succeeded in 1 usecs
[   12.966724] [drm] radeon: ib pool ready.
[   12.966790] [drm] ib test succeeded in 0 usecs
[   12.967183] [drm] Radeon Display Connectors
[   12.967185] [drm] Connector 0:
[   12.967187] [drm]   DVI-I
[   12.967189] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   12.967191] [drm]   Encoders:
[   12.967193] [drm]     DFP1: INTERNAL_UNIPHY
[   12.967195] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   12.967197] [drm] Connector 1:
[   12.967198] [drm]   DIN
[   12.967199] [drm]   Encoders:
[   12.967200] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   12.967202] [drm] Connector 2:
[   12.967203] [drm]   DVI-I
[   12.967205] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   12.967207] [drm]   Encoders:
[   12.967208] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   12.967210] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[   13.009193] usbcore: registered new interface driver snd-usb-audio
[   13.380085] [drm] fb mappable at 0xD0141000
[   13.380088] [drm] vram apper at 0xD0000000
[   13.380090] [drm] size 9437184
[   13.380091] [drm] fb depth is 24
[   13.380092] [drm]    pitch is 8192
[   13.380096] [COLOR=PaleGreen]fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver[/COLOR]
[   13.380169] Console: switching to colour dummy device 80x25
[   13.380394] Console: switching to colour frame buffer device 256x72
[   13.382104] executing set pll
[   13.430024] executing set crtc timing
[   13.430059] [drm] TMDS-15: set mode 2048x1152 22
[   13.499114] fb0: radeondrmfb frame buffer device
[   13.499116] registered [COLOR=Red]panic[/COLOR] notifier
[   13.499121] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   13.500764] vga16fb: initializing
[   13.500768] vga16fb: mapped to 0xffff8800000a0000
[   13.500814] fb1: VGA16 VGA frame buffer deviceIt struck me when I saw "panic" ...

---

### Post by meierfra. on 2010-02-04
> Then I rebooted the system with the new 00_header file and all seems fine. I can hold down shift key without triggering system reboot.
Seems they fixed that bug.


> 'if terminal_output gfxterm;' statement is present in the new 00_headers file. 

I also noticed that the new grub throws this message: 'unknown command terminal'.

Just for good measure do

```
sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc grub-common

```

If that did not get rid of of the 'unknown command terminal' message place a "#" in front of   "terminal gfxterm"  in 00_header.

---

### Post by VMC on 2010-02-04
> **zika said:**
> ... I had to disable splash and I still do not get any messages  while booting, GRUB menu is there all the time... I got to boot into  2.6.32-12 and 2.6.33-999, eventually, but, it was rough ride...

So it boots, but you have the grub boot menu all the time your booting?

Also, do you have gfxpayload activated? I have the following and I can see my boot process even though its not frame buffered:

```
  #gfxpayload=1024x768
  linux /vmlinuz root=UUID=ded24c86-7f4e-4e43-b5fd-ddeffc1c4f97 ro #splash
```

---

### Post by zika on 2010-02-04
> **VMC said:**
> So it boots, but you have the grub boot menu all the time your booting?

Also, do you have gfxpayload activated? I have the following and I can see my boot process even though its not frame buffered:

```
  #gfxpayload=1024x768
  linux /vmlinuz root=UUID=ded24c86-7f4e-4e43-b5fd-ddeffc1c4f97 ro #splash
```
This is my grub.cfg:
> 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="1"
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set xxx
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --xxx
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-999-generic" {
        recordfail
    set gfxpayload=keep
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux    /boot/vmlinuz-2.6.33-999-generic root=UUID=xxx ro nomodeset
    initrd    /boot/initrd.img-2.6.33-999-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    set gfxpayload=keep
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=xxx ro nomodeset
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic" {
        recordfail
    set gfxpayload=keep
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux    /boot/vmlinuz-2.6.32-11-generic root=UUID=xxx ro nomodeset
    initrd    /boot/initrd.img-2.6.32-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set xxxx
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


---

### Post by code850 on 2010-02-04
@Meierfra

I purged and reinstalled grub-pc & grub-common but this did'nt help getting rid of the 'unknown terminal' warning. Then I commented '#terminal gfxterm' and this seems to work, but now grub throws multiple 'syntax error' messages. I thought that this might be caused by the empty 'else ... fi'. Then i just put something like 'echo ""' inbetween and now the syntax error messages are gone.

Now i want to see where this message is coming from: 
mount: unable to mount none on /dev: no such device. It appears immediately after grub loading message.

Does grub has anything to do with this?


Many thanks for the help.
cheers

---

### Post by ranch hand on 2010-02-04
Your " unable to mount none on /dev: no such device" is of interest to me as I have that on my install that I put the 2.6.33-999 kernel on.  Got it right on the first boot into the kernel and about gave me a heart attack.

After the last update it boots better than the rest of them that need to be booted CLI from recovery.

---

### Post by zika on 2010-02-04
After many problems with Ubuntu last several days it came time to reinstall. A difference from previous (very rare) re-installs is that I managed to preserve all personal data (properly backed-up, although) on my disk and, after reboot, I was greeted with a bit different but well known environment. So, without separate 7home partition, I preserved everything important. Shortcuts, history, bookmarks, documents... Here is a new grub.cfg generated in this transformation (different from the one gained in numerous upgrades...)> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="2"
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
set root=(hd0,2)
search --no-floppy --fs-uuid --xxxx
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
set locale_dir=/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-999-generic" {
        recordfail
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux    /boot/vmlinuz-2.6.33-999-generic root=UUID=xxxx ro   quiet splash
    initrd    /boot/initrd.img-2.6.33-999-generic
}
menuentry "Ubuntu, with Linux 2.6.33-999-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --xxxx
    echo    Loading Linux 2.6.33-999-generic ...
    linux    /boot/vmlinuz-2.6.33-999-generic root=UUID=xxxx ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.33-999-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=xxxx ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    echo    Loading Linux 2.6.32-12-generic ...
    linux    /boot/vmlinuz-2.6.32-12-generic root=UUID=xxxx ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic" {
        recordfail
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux    /boot/vmlinuz-2.6.32-11-generic root=UUID=xxxx ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    echo    Loading Linux 2.6.32-11-generic ...
    linux    /boot/vmlinuz-2.6.32-11-generic root=UUID=xxxx ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set xxxx
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set xxxxchainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###The only problem, not so important, is that 2.6.33-999-20100204 doesn not work with this install, now. It'll come to terms with it in few next days, I'm sure...
Now, when I do the upgrade, since LiveCD is several days old, we'll see if new version ofBRUB will make life hard, again...

---

### Post by meierfra. on 2010-02-04
> Then I commented '#terminal gfxterm' and this seems to work, but now grub throws multiple 'syntax error' messages. I thought that this might be caused by the empty 'else ... fi'. Then i just put something like 'echo ""' inbetween and now the syntax error messages are gone.

Opps. Should have thought about  that.  Just to save 1/100 seconds  in your boot up time use:
```

  #if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
  # terminal gfxterm
  #if
```

in 00_header.


> unable to mount none on /dev: no such device" 
Sound like a message from the kernel and not from grub. I have seen it in a couple of threads, but have no idea what's causing it.

---

### Post by code850 on 2010-02-04
> **meierfra. said:**
> Opps.   Just to save 1/100 seconds  in your boot up time use:


And hopefully it will make me live 1/100 seconds longer;)

---

