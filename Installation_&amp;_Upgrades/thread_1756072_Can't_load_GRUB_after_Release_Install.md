---
title: "Can't load GRUB after Release Install"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by nash black on 2011-05-11
Hi all,

I just installed the newest Ubuntu release through the update manager and, after the restart, GRUB won't load.

Before GRUB would normally load I get the message:

error: the symbol 'grub_xparts' not found
grub rescue>


How can I fix this? :confused:


Background: Running an XP and Ubuntu dual boot with the two OSs on different hard discs.

Thanks,
Nash

---

### Post by wilee-nilee on 2011-05-11
To see the whole setup and finds and what's up click on the bootscript link in my signature. Follow the instructions that will generate a text file. Open a regular reply, not a quick reply in the thread click on the **(#)** in the reply panel generating code tags and paste all the text from that file between them.

---

### Post by nash black on 2011-05-12
Thanks for the reply. 

I followed those instructions and generated a RESULTS.txt file. Here are the contents:

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 293863418 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   321,669,494   321,669,432   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   293,587,874   293,587,812   7 HPFS/NTFS
/dev/sdb2         293,587,875   781,417,664   487,829,790   5 Extended
/dev/sdb5         293,587,938   769,336,784   475,748,847  83 Linux
/dev/sdb6         769,336,848   781,417,664    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0E3C22C43C22A6A5                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C800CC6D00CC6452                       ntfs       DRV3_VOL1                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1c06334a-c9e9-4856-bee8-a03007c3f77f   ext4                                     
/dev/sdb6        cfc719b5-5f8b-4adf-a202-c0759e82277d   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=1c06334a-c9e9-4856-bee8-a03007c3f77f ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=1c06334a-c9e9-4856-bee8-a03007c3f77f ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=1c06334a-c9e9-4856-bee8-a03007c3f77f ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=1c06334a-c9e9-4856-bee8-a03007c3f77f ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c06334a-c9e9-4856-bee8-a03007c3f77f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0e3c22c43c22a6a5
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1c06334a-c9e9-4856-bee8-a03007c3f77f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=cfc719b5-5f8b-4adf-a202-c0759e82277d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 150.6GB: boot/grub/core.img
 156.3GB: boot/grub/grub.cfg
 167.5GB: boot/initrd.img-2.6.32-22-generic
 167.5GB: boot/initrd.img-2.6.35-28-generic
 153.9GB: boot/vmlinuz-2.6.32-22-generic
 152.2GB: boot/vmlinuz-2.6.35-28-generic
 167.5GB: initrd.img
 152.2GB: vmlinuz 
```



Thanks again

---

### Post by Quackers on 2011-05-12
Which drive is set to boot first in the bios?

---

### Post by nash black on 2011-05-12
I remember setting it up like this:

      sda: Windows partition
      sdb: Ubuntu and a large partition that I use for storage for both operating systems

As far as I can tell from the script that was generated that is correct.

In the BIOS, the first boot device listed is the sda drive with windows (then the op drive then the network card). I haven't messed with the boot sequence in years, unless the upgrade could have messed with that for some reason.

---

### Post by Quackers on 2011-05-12
Ok thanks.
One more question before we try to fix it.
Is the second hard drive (sdb) an internal or a USB HDD?

---

### Post by nash black on 2011-05-12
Both drives are internal.

---

### Post by Quackers on 2011-05-12
Ok, thanks.
You said earlier that you installed the latest Ubuntu. In fact you appear to have 10.10 installed (not 11.04, which came out recently). You should use the 10.10 live cd/usb to fix this.

The grub_xputs error means that one or more of grub's files have not been fully installed. To fix it you will need to purge then re-install grub.
To do this you can follow the CHROOT section of the guide below.
Early in the guide you will need to mount a partition. The one you need to mount is /dev/sdb5.
However grub needs to be installed to /dev/sda later in the guide (if sda is the first hard drive to boot in your bios settings).
If you get stuck anywhere just holler :-)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by nash black on 2011-05-13
Thanks a lot. Tryin' that right now.

---

### Post by Quackers on 2011-05-13
Good luck then :-)

---

### Post by nash black on 2011-05-13
Alright, problem 1:

when I try to run the commands under "Purge GRUB 2 Packages" I get the following:

```

ubuntu@ubuntu:~$ sudo apt-get purge grub grub-pc grub-commonapt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package grub-commonapt-get
E: Unable to locate package purge
ubuntu@ubuntu:~$ 

```This is after following the inital instructions for step 1C "If you have a normal installation"
The first and second steps appear to have gone smoothly.


EDIT: nevermind, I just noticed that I pasted the command in twice with no space. Now its working!

---

### Post by drs305 on 2011-05-13
It looks like there was a copy error with duplicates:
> sudo apt-get purge grub grub-pc grub-commonapt-get purge grub grub-pc grub-common

Change to:
```
sudo apt-get purge grub grub-pc grub-common
```
If you haven't ever used grub on the system, you can omit "grub", otherwise you will just get a message saying 'grub' (Grub legacy) isn't installed.

Note however, depending on which part of the guide you are using, 'sudo' is not used if you are 'chrooting'.

---

### Post by Quackers on 2011-05-13
And shouldn't you be root by now?
The terminal prompt should be root@ubuntu not ubuntu@ubuntu

---

### Post by nash black on 2011-05-13
Yes, indeed!

Okay, I'm not sure if this one is a problem or not, its just a bit of a confusing message:

Screenshot:
[http://imageshack.us/photo/my-images/231/configuringgrub.png/](http://imageshack.us/photo/my-images/231/configuringgrub.png/)


This is just throwing me off because it doesn't seem to be showing anything...

---

### Post by drs305 on 2011-05-13
> 
This is just throwing me off because it doesn't seem to be showing anything...

That is a normal screen asking if you need to designate any special kernel options. Unless you need a kernel option (if you don't know, you don't), just TAB to OK and ENTER.

On the next screen, you will be asked where to install Grub 2. Select the *drive* with the SPACEBAR, then TAB to OK. Do not select any of the partitions.

---

### Post by nash black on 2011-05-13
```
&#9474; 
GRUB failed to install to the following devices:                          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; /dev/sda                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Do you want to continue anyway?  If you do, your computer may not start   &#9474; 
 &#9474; up properly.                                                              &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; GRUB installation failed.  Continue?   

 
```

Ahh darn.

These messages pop up over the command line in terminal, so I can't see the exact errors anyway, but is the fact that I only ran Chroot with sdb causing this?

If I switch My other HD to the first boot device would there be a problem with trying to install GRUB on sdb?

I kind of like the idea of having Ubuntu and GRUB on one drive and Windows on the other. My inital thought was that if I did this I might be able to just disconnect sdb if I ever have to reinstall windows since it doesn't like to play nice with GRUB or Ubuntu.

---

### Post by drs305 on 2011-05-13
> **nash black said:**
> 

If I switch My other HD to the first boot device would there be a problem with trying to install GRUB on sdb?

I kind of like the idea of having Ubuntu and GRUB on one drive and Windows on the other. My inital thought was that if I did this I might be able to just disconnect sdb if I ever have to reinstall windows since it doesn't like to play nice with GRUB or Ubuntu.

Your installation plan was a good one.

You could install it on the other drive. Of course, it would overwrite the MBR which points to the Windows bootloader. We can restore Windows pretty easily from the Ubuntu CD if this happens but it could be a bit of surprise if you can't boot either OS.

I'd prefer to find out why the installation failed. Are you using the same CD as the release (Maverick)? 
Did you mount /dev/sdb5 ? 
Are you sure when you booted from the CD that the drive designations remained the same (sda is still Windows, and sdb is still your Ubuntu drive)?
Were you running the commands from within the 'chroot' (root prompt)?

---

### Post by Quackers on 2011-05-13
Yes, you can install grub to sdb but it will be useless unless you can change the boot devices in bios so that sdb boots before sda.

As we can't see your terminal output it makes it difficult to determine what's happening.

As you should have been root when you were posting before, and weren't, it seems you didn't do everything in the guide correctly.
Maybe that's what's wrong.

---

### Post by drs305 on 2011-05-13
I'll let *the duck* continue, as he has a good handle on what is going on...

---

### Post by nash black on 2011-05-13
Ha alright, well thanks for the help, drs305.

Yeah I missed a line earlier. I've gone through the instructions again and now the prompt reads correctly. I'm back to reinstalling the GRUB packages.

I think I would like to have GRUB and Ubuntu on the same drive, but what was drs305 saying about overwriting the MBR? If installing GRUB on sdb would get tricky, I wouldn't have a huge problem with putting GRUB on the windows drive...

---

### Post by Quackers on 2011-05-13
I personally would prefer to install grub to the Ubuntu drive and then change the boot device in your bios so that the Ubuntu drive boots before the Windows drive.
By all means install grub to sdb (if it's still the same designation as it was earlier), then change the bios.
According to the boot script output grub is already installed to sda so the Windows bootloader has been over-written already. That can be fixed though, with either a Windows XP repair/installation disc or even with the Ubuntu live cd.

---

### Post by drs305 on 2011-05-13
> **nash black said:**
> I think I would like to have GRUB and Ubuntu on the same drive, but what was drs305 saying about overwriting the MBR? If installing GRUB on sdb would get tricky, I wouldn't have a huge problem with putting GRUB on the windows drive...

I was just trying to say that by installing Grub2 to sda it would write to the sda MBR (so no more pointing to the Windows bootloader). The actual G2 files would still be written to your Ubuntu partition, and the Windows boot files would still be intact on sda1. It's just the BIOS wouldn't look for the sda1 Windows files any longer.

---

### Post by nash black on 2011-05-13
Installed to sdb and updated successfully. Lets see if I can boot up!

---

### Post by nash black on 2011-05-13
Alright, I switched the primary boot drive and GRUB loads. I can boot into Windows and Ubuntu 2.6.32-22, but the newest kernel, 2.6.35-28 is a bit odd.

I can boot into it and log in with no GUI, but all I get is an ubuntu command line. It tells me that a new version is available and gives a command that I can enter to install it.

I'm currently booted through the old kernel, but I'm thinking that there may have been more than a couple problems with the 10.10 install. Do you think that it would be a good idea to try to install 11.04, rather than trying to fix this piece by piece?

---

### Post by Quackers on 2011-05-13
Hmm, what is the command it gives you please?

You are managing to boot fully to the desktop though with the older kernel?

---

### Post by nash black on 2011-05-13
Yeah, It loads the normal 10.10 login screen and desktop and everything with the old kernel. If the new one loaded like this I wouldn't even notice a problem with the install.

With the old kernel, after it loads up ("ubuntu 10.10, flashing red/white loading dots) it gives this with no GUI:

[I]Ubuntu 10.10 Computus tty1
Computus login:[/I]

(I enter my username and pass)

*Welcome to Ubuntu!*
**Documentation :* (web address)

(some other text)

[I]New release 'natty' available
Run 'do-release-upgrade' to upgrade it[/I]

(some other text)

(command prompt):

---

### Post by Quackers on 2011-05-13
I'll have to leave that matter for somebody else I'm afraid.
That's something I've never seen at a login attempt. It may even be more than one problem at once. 
On the other hand you could do just what it says :-)
I just don't know!

---

### Post by nash black on 2011-05-13
Ha, yeah its weird. I was thinking about just trying to upgrade to 11.04 through the update manager or terminal in the old kernel. Maybe that would replace everything that needs to be replaced   [-o<

If no one else has chiped in by tomorrow afternoon I'll probably try that.


Thanks for the help with GRUB though. Its been a pleasure.

---

### Post by Quackers on 2011-05-13
You're welcome.
It's a good idea to leave the thread as it is for a while. 
There may yet be more views on your possible options :-)

---

### Post by nash black on 2011-05-14
Upgraded to 11.04. GRUB and the old kernel still work, but another new kernel is giving me issues.

This title doesn't really fit the problem anymore, so I started a new thread:

[http://ubuntuforums.org/showthread.php?t=1758359](http://ubuntuforums.org/showthread.php?t=1758359)


Thanks again for the help!

---

