---
title: "Unable to start after error while upgrading"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by manolomanolo on 2010-12-04
Hi to all.
I was upgrading from 10.04 to 10.10 but my laptop battery went down so the installation did not ended up correctly.
When trying to reboot now, the system is not able to start correctly. No desktop, no icons... nothing.
Starting in recovery mode is impossible too.

Now I am running with live cd.
What can I do to solve the problem?

Thanks.

PD: pls try hard not to make any comments on "why have you been upgrading without electricity, just using battery?". Thanks a lot.

---

### Post by Rubi1200 on 2010-12-04
From the LiveCD, post the results of the boot info script (link at the bottom of my post with instructions).

Thanks.

---

### Post by manolomanolo on 2010-12-04
Ok, later I will run the bootinfo script. Now, please tell me if the following solution suggested by someone on #ubuntu makes any sense.

sudo mount -t ext4 /dev/sda1 /mnt/

After the boot partition of the broken system is mounted then we are going to bind mount the virtual fs's.
sudo mount --bind /dev/ /mnt/dev/
sudo mount --bind /proc/ /mnt/proc/
sudo mount --bind /sys/ /mnt/sys/

sudo apt-get update
sudo apt-get upgrade

then run

sudo dpkg --configure -a

and rerun the two apt commands to check everything has gone well before restarting without the live cd.

---

### Post by Rubi1200 on 2010-12-04
To answer the question, theoretically yes but...

You need to make sure that 1) sda1 is your actual Ubuntu partition and 2) there is no need to use sudo once you have a chroot environment (which is what you have been asked to do). After the mount --bind commands have completed successfully, you will be left with a root prompt (you will see # after the prompt). As such, sudo is not needed for any subsequent commands.

Brief explanation:
the commands you were given allow you to take control of your Ubuntu root file system as if you were booted in normally. This allows you to then perform maintenance tasks and troubleshoot problems.

However, I suggest you run the boot info script first just so we can make sure there are no surprises!

EDIT: I would also add the following command to chroot:
```
 sudo mount --bind /dev/pts /mnt/dev/pts
```When you have finished in the chroot you need to exit and unmount before rebooting:
```
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

To be honest, I would prefer if you enter the chroot using these commands (much cleaner, so to speak):
```
sudo mount /dev/[COLOR=Red]sdax[/COLOR] /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```

Exit using the method I already posted. Here, x represents your partition number; enter the appropriate number of course.

---

### Post by manolomanolo on 2010-12-07
Hi Ruby1200. Thanks for yr replies.
This is the result of the bootinfo script

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

/dev/sda1                  63   117,258,434   117,258,372  83 Linux
/dev/sda2    *    117,258,435   233,472,644   116,214,210   7 HPFS/NTFS
/dev/sda3         234,452,610   308,174,894    73,722,285   b W95 FAT32
/dev/sda4         308,174,895   312,576,704     4,401,810  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        32511665-3b23-4aaa-8667-6d759d1fe31b   ext4                                     
/dev/sda2        28EF5D6B27F4AAF8                       ntfs       COMMON                        
/dev/sda3        5513-BEBE                              vfat       WIN7                          
/dev/sda4        22b909fb-78a3-41fa-9d67-6ba9893eea6c   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

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
search --no-floppy --fs-uuid --set 32511665-3b23-4aaa-8667-6d759d1fe31b
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
search --no-floppy --fs-uuid --set 32511665-3b23-4aaa-8667-6d759d1fe31b
set locale_dir=($root)/boot/grub/locale
set lang=it
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32511665-3b23-4aaa-8667-6d759d1fe31b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=32511665-3b23-4aaa-8667-6d759d1fe31b ro vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32511665-3b23-4aaa-8667-6d759d1fe31b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=32511665-3b23-4aaa-8667-6d759d1fe31b ro single vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32511665-3b23-4aaa-8667-6d759d1fe31b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 32511665-3b23-4aaa-8667-6d759d1fe31b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 28ef5d6b27f4aaf8
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
UUID=32511665-3b23-4aaa-8667-6d759d1fe31b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=22b909fb-78a3-41fa-9d67-6ba9893eea6c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  16.8GB: boot/grub/grub.cfg
  51.1GB: boot/initrd.img-2.6.32-22-generic
   5.2GB: boot/vmlinuz-2.6.32-22-generic

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

So, pls confirm that sda**x** actually is sda**1**.
Thanks

---

### Post by manolomanolo on 2010-12-07
I have just executed yr suggested instructions but unfortunately I get a chroot error 

```
ubuntu@ubuntu:~/Downloads$ sudo chroot /mnt
chroot: failed to run command `/bin/bash': Exec format error

```

What can I do?
Thanks.

---

### Post by manolomanolo on 2010-12-08
> **manolomanolo said:**
> I have just executed yr suggested instructions but unfortunately I get a chroot error 

```
ubuntu@ubuntu:~/Downloads$ sudo chroot /mnt
chroot: failed to run command `/bin/bash': Exec format error

```

What can I do?
Thanks.

The error was due to running chroot from a 32 bit system (the live cd) to a 64 bit system (the broken one).
I solved by running a 64 bit live cd.

Unfortunately I do not think I solved the problems of the broken system.
Running several times the apt-get commands and also the dpkg command gives me this kind of result:
```
root@ubuntu:/# sudo dpkg --configure -a
Setting up dbus (1.4.0-0ubuntu1) ...
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gconf2-common:
 gconf2-common depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing gconf2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-tools-backends:
 system-tools-backends depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing system-tools-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gconf2-common (>= 2.23.2-0ubuntu3); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udisks:
 udisks depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing consolekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of minitube:
 minitube depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing minitube (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gobby:
 gobby depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gobby (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on gconf2-common (>= 2.31); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on gconf2-common (<< 2.32); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on consolekit; however:
  Package consolekit is not configured yet.
dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gnome-session-bin depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on consolekit; however:
  Package consolekit is not configured yet.
 policykit-1 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upower:
 upower depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing upower (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-defaults-service:
 gconf-defaults-service depends on gconf2-common (>= 2.31); however:
  Package gconf2-common is not configured yet.
 gconf-defaults-service depends on gconf2-common (<< 2.32); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gconf-defaults-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gnome-power-manager depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 gnome-power-manager depends on consolekit; however:
  Package consolekit is not configured yet.
 gnome-power-manager depends on upower; however:
  Package upower is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-browser-applet:
 file-browser-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 file-browser-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 file-browser-applet depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing file-browser-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs5-plugins:
 kdelibs5-plugins depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing kdelibs5-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gdm depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gdm depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gdm depends on gnome-session-bin; however:
  Package gnome-session-bin is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-gnome:
 xchat-gnome depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing xchat-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gconf-editor depends on gconf-defaults-service (>= 2.28); however:
  Package gconf-defaults-service is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome | compiz-kde; however:
  Package compiz-gnome is not configured yet.
  Package compiz-kde is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on gconf2; however:
  Package gconf2 is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomeapplet:
 python-gnomeapplet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnomeapplet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnomeapplet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnomeapplet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse:
 seahorse depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing seahorse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of usb-creator-common:
 usb-creator-common depends on udisks (>= 1.0~); however:
  Package udisks is not configured yet.
 usb-creator-common depends on udisks (<< 1.1); however:
  Package udisks is not configured yet.
dpkg: error processing usb-creator-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on policykit-1; however:
  Package policykit-1 is not configured yet.
dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-exe-thumbnailer:
 gnome-exe-thumbnailer depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-exe-thumbnailer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dia-common:
 dia-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing dia-common (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 dbus
 gconf2-common
 system-tools-backends
 gnome-control-center
 udisks
 consolekit
 libgnomevfs2-0
 xsane2tess
 dbus-x11
 minitube
 firefox-gnome-support
 gobby
 network-manager
 gnome-screensaver
 gconf2
 libgnome2-0
 light-themes
 gnome-applets
 onboard
 compiz-gnome
 update-manager
 pulseaudio
 gnome-session-bin
 aisleriot
 policykit-1
 upower
 pulseaudio-module-bluetooth
 gconf-defaults-service
 gnome-power-manager
 libbonoboui2-0
 file-browser-applet
 python-gnome2
 kdelibs5-plugins
 pulseaudio-module-x11
 gdm
 xchat-gnome
 eog
 gnome-system-monitor
 gconf-editor
 gnome-settings-daemon
 compiz
 openoffice.org-gnome
 apturl
 python-gnomeapplet
 capplets-data
 seahorse
 usb-creator-common
 system-config-printer-gnome
 jockey-common
 gnome-exe-thumbnailer
 dia-common
Processing was halted because there were too many errors.

```

What else can I do?
Thanks a lot.

---

### Post by Rubi1200 on 2010-12-08
I assume you are connected to the Internet in the chroot?

I would rerun the commands to get a chroot and then try these commands (note that you do not need to use sudo once you have a chroot environment):

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```

Houseclean:

```
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
```

To exit:

```
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

---

### Post by manolomanolo on 2010-12-08
Yes, I have Internet connection on the chroot.

I rerun those commands several times but unfortunately I get always the same error "**Processing was halted because there were too many errors.**"

This is the complete result of dpkg (same results when launching **apt-get install -f**)

```
root@ubuntu:/# dpkg --configure -a
Setting up gimp (2.6.10-1ubuntu3.1) ...
Setting up kdepimlibs-kio-plugins (4:4.5.1-0ubuntu1) ...
Setting up libmagickcore3 (7:6.6.2.6-1ubuntu1.1) ...
Setting up libsane-hpaio (3.10.6-1ubuntu10.1) ...
Installing new version of config file /etc/hp/hplip.conf ...
Setting up libisccfg60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up qutecom (2.2~rc3.hg396~dfsg1-6ubuntu2) ...
Setting up libsox-fmt-alsa (14.3.1-1build1) ...
Setting up python-ubuntuone-client (1.4.4.1-0ubuntu1) ...
Installing new version of config file /etc/xdg/ubuntuone/syncdaemon.conf ...
Setting up libbind9-60 (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
Setting up libglade2.0-cil-dev (2.12.10-1) ...
Setting up cpp-4.4 (4.4.4-14ubuntu5) ...
Setting up libakonadiprivate1 (1.4.0-0ubuntu1) ...
Setting up mesa-utils (8.0.1-0ubuntu1) ...
Setting up packagekit-backend-aptcc (0.6.8-0ubuntu3.1) ...
Setting up hpijs (3.10.6-1ubuntu10.1) ...
Setting up python-mako (0.3.4-2) ...
Setting up libgdict-1.0-6 (2.31.1-0ubuntu1) ...
Setting up dpkg-dev (1.15.8.4ubuntu3) ...
Setting up libmatroska2 (1.0.0+repack-0ubuntu1) ...
Setting up telepathy-mission-control-5 (1:5.6.0-1) ...
Setting up akonadi-server (1.4.0-0ubuntu1) ...
 * Reloading AppArmor profiles                                                                                                                                 * AppArmor not available as kernel LSM.
                                                                                                                                                       **[COLOR="Red"][fail][/COLOR]**
invoke-rc.d: initscript apparmor, action "force-reload" failed.
Setting up codeblocks (10.05-0ubuntu1) ...
Setting up libextractor1c2a (1:0.5.23+dfsg-7build1) ...
Setting up cclive (0.6.3-1) ...
Setting up telepathy-gabble (0.10.0-1) ...
Setting up filezilla (3.3.3-1ubuntu1) ...
Setting up libmagickwand3 (7:6.6.2.6-1ubuntu1.1) ...
Setting up dbus (1.4.0-0ubuntu1) ...
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libmicroblog4 (4:4.5.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of gconf2-common:
 gconf2-common depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing gconf2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
Setting up gcc-4.4 (4.4.4-14ubuntu5) ...
Setting up libfluidsynth1 (1.1.2-2) ...
Setting up javascript-common (7) ...
Setting up zoneminder (1.24.2-7ubuntu1) ...
start: Unknown job: mysql
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up librpmbuild1 (4.8.1-5) ...
Setting up xjadeo (0.4.13-1build1) ...
Setting up libgwibber0 (0.0.6-0ubuntu1) ...
Setting up libmagick++3 (7:6.6.2.6-1ubuntu1.1) ...
dpkg: dependency problems prevent configuration of system-tools-backends:
 system-tools-backends depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing system-tools-backends (--configure):
 dependency problems - leaving unconfigured
Setting up libevdocument3 (2.32.0-0ubuntu1) ...
Setting up gstreamer0.10-plugins-bad (0.10.20-1ubuntu1) ...
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gconf2-common (>= 2.23.2-0ubuntu3); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up dvdauthor (0.6.18-1build1) ...
Setting up libevview3 (2.32.0-0ubuntu1) ...
Setting up synaptic (0.63.1ubuntu14) ...
Setting up sox (14.3.1-1build1) ...
Setting up perlmagick (7:6.6.2.6-1ubuntu1.1) ...
Setting up libakonadi-kde4 (4:4.5.1-0ubuntu1) ...
Setting up gfortran-4.4 (4.4.4-14ubuntu5) ...
dpkg: dependency problems prevent configuration of udisks:
 udisks depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing udisks (--configure):
 dependency problems - leaving unconfigured
Setting up python-louis (2.0.0-1ubuntu1) ...
Setting up bind9-host (1:9.7.1.dfsg.P2-2ubuntu0.1) ...
dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing consolekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on consolekit; however:
  Package consolekit is not configured yet.
dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
Setting up libcvaux2.1 (2.1.0-2) ...
Setting up vlc-nox (1.1.4-1ubuntu1.1) ...
Setting up rpm2cpio (4.8.1-5) ...
dpkg: dependency problems prevent configuration of liboobs-1-5:
 liboobs-1-5 depends on system-tools-backends (>= 2.9.2); however:
  Package system-tools-backends is not configured yet.
dpkg: error processing liboobs-1-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
Setting up libao4 (1.0.0-4) ...
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
Setting up libkpimidentities4 (4:4.5.1-0ubuntu1) ...
Setting up cpp (4:4.4.4-1ubuntu2) ...
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
Setting up aptitude (0.6.3-2ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of minitube:
 minitube depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing minitube (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gobby:
 gobby depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gobby (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
Setting up gcc (4:4.4.4-1ubuntu2) ...
Setting up lyx (1.6.7-1) ...
Setting up libkcal4 (4:4.5.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-tools:
 gnome-system-tools depends on liboobs-1-5 (>= 2.31.91); however:
  Package liboobs-1-5 is not configured yet.
 gnome-system-tools depends on system-tools-backends (>= 2.9.4); however:
  Package system-tools-backends is not configured yet.
dpkg: error processing gnome-system-tools (--configure):
 dependency problems - leaving unconfigured
Setting up libgvc5 (2.26.3-4) ...
Setting up mkvtoolnix (4.0.0-0ubuntu3) ...
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on gconf2-common (>= 2.31); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on gconf2-common (<< 2.32); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
Setting up libakonadi-kmime4 (4:4.5.1-0ubuntu1) ...
Setting up imagemagick (7:6.6.2.6-1ubuntu1.1) ...
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
Setting up python-apt (0.7.96.1ubuntu11) ...
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up libfolks0 (0.1.17-0ubuntu2) ...
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on evolution (>= 2.27.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-common:
 totem-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing totem-common (--configure):
 dependency problems - leaving unconfigured
Setting up vlc (1.1.4-1ubuntu1.1) ...
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
Setting up vlc-plugin-notify (1.1.4-1ubuntu1.1) ...
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up rpm (4.8.1-5) ...
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 1.2.16-0ubuntu3); however:
  Package dbus is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder:
 rhythmbox-plugin-cdrecorder depends on rhythmbox (= 0.13.1-0ubuntu6); however:
  Package rhythmbox is not configured yet.
dpkg: error processing rhythmbox-plugin-cdrecorder (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 network-manager-gnome depends on network-manager (>= 0.8~rc2); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on consolekit; however:
  Package consolekit is not configured yet.
dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-indicator:
 evolution-indicator depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing evolution-indicator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of inkscape:
 inkscape depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing inkscape (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntuone-client-tools (1.4.4.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of gnome-session-bin:
 gnome-session-bin depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gnome-session-bin depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gnome-session-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aisleriot:
 aisleriot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing aisleriot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-1:
 policykit-1 depends on consolekit; however:
  Package consolekit is not configured yet.
 policykit-1 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing policykit-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upower:
 upower depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing upower (--configure):
 dependency problems - leaving unconfigured
Setting up gscan2pdf (0.9.31-2) ...
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-defaults-service:
 gconf-defaults-service depends on gconf2-common (>= 2.31); however:
  Package gconf2-common is not configured yet.
 gconf-defaults-service depends on gconf2-common (<< 2.32); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gconf-defaults-service (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gnome-power-manager depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
 gnome-power-manager depends on consolekit; however:
  Package consolekit is not configured yet.
 gnome-power-manager depends on upower; however:
  Package upower is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-browser-applet:
 file-browser-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 file-browser-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 file-browser-applet depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing file-browser-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pitivi:
 pitivi depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing pitivi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screenshot:
 gnome-screenshot depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-screenshot (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for python-central ...
Errors were encountered while processing:
 dbus
 gconf2-common
 rhythmbox
 zoneminder
 system-tools-backends
 gnome-control-center
 udisks
 consolekit
 gnome-bluetooth
 liboobs-1-5
 libgnomevfs2-0
 xsane2tess
 dbus-x11
 ubuntu-desktop
 minitube
 firefox-gnome-support
 gobby
 gnome-user-share
 network-manager
 evolution
 gnome-screensaver
 gnome-system-tools
 f-spot
 gconf2
 libgnome2-0
 light-themes
 gnome-applets
 evolution-couchdb
 totem-common
 onboard
 gstreamer0.10-plugins-good
 compiz-gnome
 ekiga
 update-manager
 avahi-daemon
 rhythmbox-plugin-cdrecorder
 network-manager-gnome
 pulseaudio
 evolution-indicator
 inkscape
 gnome-session-bin
 aisleriot
 policykit-1
 upower
 pulseaudio-module-bluetooth
 gconf-defaults-service
 gnome-power-manager
 libbonoboui2-0
 file-browser-applet
 pitivi
 gnome-screenshot
**Processing was halted because there were too many errors.**
root@ubuntu:/# 

```

When launching apt-get upgrade I also get "E: Sub-process /usr/bin/dpkg returned an error code (1)" together with the previous error message at the end of the dpkg result

---

### Post by Rubi1200 on 2010-12-08
I just realized there is a mistake, really sorry :-(

It should be ```
apt-get install -f
``` not as I gave previously.

You can try it again, but I suspect the problem is somewhere else, namely the original error message which is complaining about the dbus package. Did you accidentally remove it when getting rid of something else?

From within the chroot try and reinstall the package.

> apt-get reinstall dbus
followed by 
> apt-get install -f
dpkg --configure -a

---

### Post by manolomanolo on 2010-12-10
I thing almost all of the problems are gone. I can start my system correcty and I am trying to solve the last problems from here.

Anyway, about yr last post, the correct command seems to be
```
sudo apt-get install dbus --reinstall
```

Moreover
```
mano@mano-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
.
.
.
Hit http://it.archive.ubuntu.com maverick-proposed/universe amd64 Packages
Reading package lists... Done                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libboost-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Then
```
mano@mano-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xsane2tess

```

---

### Post by Rubi1200 on 2010-12-10
You may want to try and force or reinstall the [FONT=monospace][/FONT]xsane2tess package to clear things up.

```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by manolomanolo on 2010-12-10
```
mano@mano-laptop:~$ **sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

mano@mano-laptop:~$ **sudo dpkg --configure -a**
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xsane2tess

mano@mano-laptop:~$ **sudo apt-get install xsane2tess --reinstall**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xsane2tess

```

---

### Post by sikander3786 on 2010-12-10
I would recommend to try to remove that offensive package.

```
sudo apt-get remove --purge xsane2tess
```

And again,

```
sudo dpkg --configure -a
```

---

### Post by manolomanolo on 2010-12-10
```
mano@mano-laptop:~$ **sudo apt-get remove --purge xsane2tess**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xsane2tess

mano@mano-laptop:~$ **sudo dpkg --configure -a**
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xsane2tess

```

---

### Post by sikander3786 on 2010-12-11
As the error seems to be limited to only one package i.e, xsane2tess and all the other packages have been configured, did you try to boot Ubuntu from the HDD? Does it boot?

Regarding the package issue, my last shot would be to remove xsane2tess and all its references manually.

See here.

[http://ubuntuforums.org/showpost.php?p=10048487&postcount=6](http://ubuntuforums.org/showpost.php?p=10048487&postcount=6)

Replace firmware-b43-installer with xsane2tess.

---

