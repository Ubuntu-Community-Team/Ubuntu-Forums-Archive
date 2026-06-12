---
title: "Dual Boot Setup failure"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by EngDrewman on 2011-01-06
Recently got a new Gateway FX6840. Like with any new computer I get, the first things I do are:

1. burn the recovery partition to DVDs
2. make it dual boot Win/Ubuntu

So, I fired up Ubuntu, manually edited the partitions like I've done a million times now, and ran the installer. Ubuntu installed correctly, but when I try to get into Win 7, I get the following error code:

"Status: 0xc0000225

Info: The boot selection failed because a required device is inaccessible"

I've googled that error code to no avail. To make matters worse, the recovery disks only offer to completely wipe the hard drive. No recovery console.

:confused:

System specs:
Gateway FX6840-15e
Intel i7 CPU
8GB Ram
1TB hard drive
ATi Radeon 5750 HD
Win 7 Home Premium x64
Ubuntu 10.10 x64

---

### Post by stargazergal62 on 2011-01-06
I'm having the same problem.  I downloaded Ubuntu 10.10.  Initially, I had the problem on the "Who are You" screen and was told that lower case letters were needed.  Long story short, I was given a work-around since there was a partition on my hard drive.  Ubuntu installed correctly - works just fine.  However, upon booting up, if I choose Windows 7, it takes me to Recovery and wants to reinstall factory specs.  What's the best way to resolve this?  Is going back to factory specs and then reinstalling Ubuntu a viable option?  This is brand new computer and I've downloaded nothing - wanted to make sure everything was working fine before I did that - so I would have no problem with doing that.  I'm extremely new to Linux/Ubuntu, so I'm a little lost on all of this.  Thanks for the help.

---

### Post by Mark Phelps on 2011-01-06
> **EngDrewman said:**
> To make matters worse, the recovery disks only offer to completely wipe the hard drive. 

What I recommend is to start over and do the following:
1) Do a complete restore using the recovery disks
2) When Win7 is back, use the Backup feature to create and burn a Win7 Repair CD.  You can use that later to do startup repairs -- WITHOUT having to reinstall or restore Win7.
3) Manually edit the partitions using the Win7 Disk Management utility.  Do not use GParted or the Ubuntu installer to do this.
4) Reboot into Win7 after the partition changes to ensure that it still boots.

THEN, you're ready to reinstall Ubuntu.

---

### Post by Mark Phelps on 2011-01-06
> **stargazergal62 said:**
> ...What's the best way to resolve this?

Best way is to NOT hijack someone else's thread only a few minutes after they have posted it.  It's hard enough to solve one person's problems.  When another hijack's their thread, it only becomes confusing.

Please start your own thread.  Just because it might be the same problem, does not mean that it is.

---

### Post by Quackers on 2011-01-06
EngDrewman, the recovery dvd's are only a copy of the recovery partition, which often does not include the repair tools. A Win 7 repair cd would do that, which you could have made from the Backup/restore centre in Control Panel.
Please follow the directions below.

stargazergal62, although your symptoms may be similar they may have a very different cause. I would suggest that you create your own thread and include the output from the boot script below.

Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by EngDrewman on 2011-01-06
> **Mark Phelps said:**
> Best way is to NOT hijack someone else's thread only a few minutes after they have posted it.  It's hard enough to solve one person's problems.  When another hijack's their thread, it only becomes confusing.

Please start your own thread.  Just because it might be the same problem, does not mean that it is.

I think that could have been said a little nicer. He sounds like a newbie, and when stuff like this happens, panic sets in. Yes you have a good point, but try to be more sensitive next time.

nuff said.

Now, back to how to fix my computer...

---

### Post by EngDrewman on 2011-01-06
Note: there is another empty partition on my HD called "WinXP" because I also plan to install XP 32bit for my old programs that don't work in win7. Note that these are plans-the partition is empty. I did all of the partitioning with Gparted.

Results of the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       204,799       202,752   7 HPFS/NTFS
/dev/sda2    *        204,800 1,748,725,759 1,748,520,960   7 HPFS/NTFS
/dev/sda3       1,748,727,806 1,953,523,711   204,795,906   5 Extended
/dev/sda5       1,748,727,808 1,851,127,807   102,400,000   7 HPFS/NTFS
/dev/sda6       1,851,129,856 1,949,618,175    98,488,320  83 Linux
/dev/sda7       1,949,620,224 1,953,523,711     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        CAB427BCB427A9C1                       ntfs       SYSTEM RESERVED               
/dev/sda2        E05629B256298A7C                       ntfs       Win7                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2592F79622FC4113                       ntfs       WinXP                         
/dev/sda6        248a26cf-eb82-4795-b34c-beff57cfe36a   ext4                                     
/dev/sda7        ec3192b5-9f08-4ecc-bf80-6a16e600210e   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 248a26cf-eb82-4795-b34c-beff57cfe36a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 248a26cf-eb82-4795-b34c-beff57cfe36a
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 248a26cf-eb82-4795-b34c-beff57cfe36a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=248a26cf-eb82-4795-b34c-beff57cfe36a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 248a26cf-eb82-4795-b34c-beff57cfe36a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=248a26cf-eb82-4795-b34c-beff57cfe36a ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 248a26cf-eb82-4795-b34c-beff57cfe36a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 248a26cf-eb82-4795-b34c-beff57cfe36a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set cab427bcb427a9c1
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=248a26cf-eb82-4795-b34c-beff57cfe36a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ec3192b5-9f08-4ecc-bf80-6a16e600210e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 969.5GB: boot/grub/core.img
 967.3GB: boot/grub/grub.cfg
 948.7GB: boot/initrd.img-2.6.35-22-generic
 969.6GB: boot/vmlinuz-2.6.35-22-generic
 948.7GB: initrd.img
 969.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
```

---

### Post by Quackers on 2011-01-06
I can only see one thing which looks amiss with your boot script output. The boot flag is set at sda2. sda2 does not have the Win 7 boot files - they are in sda1.
I would suggest moving the boot flag with gparted to sda1 and then reboot. Ubuntu should boot directly, but if you then open a terminal and run ```
sudo update-grub
``` then watch as grub.cfg is run, you should hopefully see the Windows Loader appear. If it does, reboot and you should see the grub menu, which will give you a choice of OS to boot. Try Windows and see if it boots ok.

To move the boot flag in gparted, right-click on sda1 partition and select "Manage flags" then check the box for "boot" and close.

---

### Post by EngDrewman on 2011-01-06
> **Mark Phelps said:**
> What I recommend is to start over and do the following:
1) Do a complete restore using the recovery disks
2) When Win7 is back, use the Backup feature to create and burn a Win7 Repair CD.  You can use that later to do startup repairs -- WITHOUT having to reinstall or restore Win7.
3) Manually edit the partitions using the Win7 Disk Management utility.  Do not use GParted or the Ubuntu installer to do this.
4) Reboot into Win7 after the partition changes to ensure that it still boots.

THEN, you're ready to reinstall Ubuntu.

I do have another machine with Win 7 Pro 32 bit and can download 7 Pro 64 bit setup disk- would either of those work to create a repair cd? Note that the version on the broken computer is Home Premium.

---

### Post by Quackers on 2011-01-06
If you get back into Windows using post  8, you can make your own :-)

---

### Post by EngDrewman on 2011-01-06
> **Quackers said:**
> I can only see one thing which looks amiss with your boot script output. The boot flag is set at sda2. sda2 does not have the Win 7 boot files - they are in sda1.
I would suggest moving the boot flag with gparted to sda1 and then reboot. Ubuntu should boot directly, but if you then open a terminal and run ```
sudo update-grub
``` then watch as grub.cfg is run, you should hopefully see the Windows Loader appear. If it does, reboot and you should see the grub menu, which will give you a choice of OS to boot. Try Windows and see if it boots ok.

To move the boot flag in gparted, right-click on sda1 partition and select "Manage flags" then check the box for "boot" and close.

Here is the original setup of the hard drive partitions:

| Recovery 15GB (sda1) | System 100MB (sda2) | Win 7 rest of drive (sda3) |

I burned the recovery partition to DVDs and deleted it. Here's how my new setup looks (note [ ] indicates extended partition)

| System 100MB (sda1) | Win 7 895GB (sda2) [ WinXP 50GB (sda 5) | Ubuntu 50 GB (sda 6) | swap (sda 7) ]

---

### Post by Quackers on 2011-01-06
If you've deleted the recovery partition that could be the reason the boot flag is wrong - maybe :-)

---

### Post by EngDrewman on 2011-01-06
sudo update-grub did not do the trick.

---

### Post by EngDrewman on 2011-01-06
And note: the Win 7 partition does have a boot flag

---

### Post by Quackers on 2011-01-06
If you've moved the boot flag and rebooted, then run sudo update-grub and the Windows Loader is still not picked up, it may be necessary to re-install grub, or repair the Windows boot laoder then re-install grub.

---

### Post by Quackers on 2011-01-06
> **EngDrewman said:**
> And note: the Win 7 partition does have a boot flag

Yes, it does, but the first 2 Windows boot files are in sda1, as I explained earlier. With the boot flag on sda2 the boot sequence will not find those first 2 boot files.

---

### Post by EngDrewman on 2011-01-06
Mounted sda1 and you are correct that the Win 7 loader is on it. Tried changing the boot flag to sda1, update-grub, still same error message.

---

### Post by Quackers on 2011-01-06
Did you reboot in between changing the boot flag and running sudo update-grub?

---

### Post by EngDrewman on 2011-01-06
> **Quackers said:**
> Did you reboot in between changing the boot flag and running sudo update-grub?

Just did- still nothing

---

### Post by Quackers on 2011-01-06
Oh dear!
We are back to choosing between repairing the Windows mbr with a Win 7 repair disc, or re-installing grub.
As you are booted in to Ubuntu I would suggest trying tt re-install grub first.
From a terminal please copy/paste these commands in one at a time pressing enter after each one.
```
sudo mount /dev/sda6 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```
Then, if that runs without errors
```
sudo update-grub
``` and watch to see if the Windows Loader is picked up.
If it still does not appear, you should try repairing the mbr by running Startup Repair, up to 3 times, from a Win 7 repair disc. Then re-install grub again, with the above commands, from the Ubuntu Live cd/usb desktop.

---

### Post by EngDrewman on 2011-01-06
Found a win 7 x64 repair disk: [http://www.addictivetips.com/windows-tips/windows-7-recovery-disk-boot-disk/](http://www.addictivetips.com/windows-tips/windows-7-recovery-disk-boot-disk/)

Going to try noodling with that...

---

### Post by EngDrewman on 2011-01-06
Grrr... that disk is worthless- won't even boot.

Tried those commands...
```
drew@BFG-Ubuntu:~$ sudo mount /dev/sda6 /mnt
[sudo] password for drew: 
drew@BFG-Ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
drew@BFG-Ubuntu:~$ 

```

---

### Post by EngDrewman on 2011-01-06
Oh boy. Tried sudo update-grub after those commands. Reboot. Now grub won't load. When I turn on my computer I get:

```
error: file not found
grub rescue>_
```

---

### Post by EngDrewman on 2011-01-06
~bump~

---

### Post by Quackers on 2011-01-06
Please re-run the boot script from the live cd and posts the results.

---

### Post by kansasnoob on 2011-01-06
At this point I'd first try using lilo to create a Windows readable MBR by booting any Ubuntu Live CD and then running these commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

If that allows Windows to boot the next thing I'd want to try is reverting the Ubuntu install to legacy grub using a chroot.

I'll watch and see what luck you have.

---

### Post by oldfred on 2011-01-06
If you need a windows repair CD this works.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you moved sda3 to sda2, then windows boot sector and BCD may be incorrect. Also sda2 to sda1 may need fixing. The windows boot sector has to match the partition location, start & end and the BCD may be looking for the wrong place. Windows or testdisk can rebuild the NTFS boot sector, but I  do not know of any tools other than windows to work on the BCD. Neosmart also has third party windows tools for BCD repair.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by EngDrewman on 2011-01-06
Running from the live CD, here are the results of the grub installation commands:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

```

---

### Post by EngDrewman on 2011-01-06
Well, it printed the error message above, but upon reboot, it worked! Both Ubuntu and Windows! Thanks guys!

---

### Post by oldfred on 2011-01-07
Glad it is working.

It looks like a lot of users have some proprietary software that uses Flexnet for its DRM security. Grub modified its code to work around Flexnet.

---

### Post by Quackers on 2011-01-07
Nice one :-)
Flexnet does crop up every now and again - as a nuisance :wink:

---

