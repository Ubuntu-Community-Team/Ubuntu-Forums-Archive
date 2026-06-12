---
title: "Installed Windows 7 - No more grub!!!"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Topher88 on 2009-12-11
So...  Might have made a dumb move.  I tried looking for the probability of this happening before installing, but I didn't see anything so I just figured it shouldn't be a big deal.
 
I bought a Vista laptop back in August and got a free copy of Win7 sent to me.  I went ahead and dual booted Ubuntu with Vista.  I got the Win7 update today, and proceeded to install it over Vista on the corresponding partition, not thinking it would effect GRUB - it did.  There is no more GRUB menu at startup.
 
How screwed am I?

---

### Post by darkod on 2009-12-11
Not at all. For restoring different bootloaders look here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You want grub2, for 9.10 I guess.

---

### Post by waspbr on 2009-12-11
not entirely screwed provided you did not erase your ubuntu partitions, windows in general does not play nice with other operating systems, so you need to either download a supergrub cd and and get yourself a new grub or install it through a live cd.

---

### Post by Topher88 on 2009-12-11
> **darkod said:**
> Not at all. For restoring different bootloaders look here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You want grub2, for 9.10 I guess.

Um...  Yeah, so I followed those instructions, and now I get this when I boot up:

[ATTACH]139447[/ATTACH]

Now I can't log into anything except for a liveCD or liveUSB.

Help please...

---

### Post by Topher88 on 2009-12-11
UPDATE:  I understand that I could use the above command line to do what I need, but if possible I'd really like the grub menu that actually lets me scroll and choose which OS to boot into.  Can anyone help me get that one back?  Thanks.

---

### Post by Topher88 on 2009-12-12
Alright, so...  My liveCD is absolutely worthless.  Takes 5 minutes to load each time, and another 5 minutes JUST to connect to the internet if it even makes it that far before crashing...  LiveUSB works much better, but I only have a liveUSB of  9.04 and don't have the means by which to create a 9.10 liveUSB at the moment.  Is there seriously no way to install GRUB without having a LiveCD/LiveUSB of the proper version?  I can't just use the internet to get it or anything?

Or could someone at least explain to me how to work my way around in the >grub command as pictured above, so I COULD make the proper LiveUSB and get things rolling?

---

### Post by wilee-nilee on 2009-12-12
You can use unetbootin to load the thumb with 9.10 in W7.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by blue_ on 2009-12-12
> **wilee-nilee said:**
> You can use unetbootin to load the thumb with 9.10 in W7.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Guess you missed the part where he said he cant get into anything :P


Sounds like you didnt follow the steps correctly and missed the step of setting the grub list file. 

Are you using multi-partions 1 hd or multi-drives win7 on 1 linux on other? 

One thing you can do is use the windows disk to run fixmbr which would make windows boot then you could do this to add ubuntu to the windows boot loader.
[http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

This tut should walk you through booting into either windows or ubuntu from the grub command line :)
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)


Repair your MBR for ubuntu
"How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD." This was taken from another thread [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by wilee-nilee on 2009-12-12
Good call missed the can't boot into either OS. I think starting with the fix MBR is the best solution.

OP I would make sure you always have a ISO burned to a CD or installed on a thumb of any currently running OS it will save you a lot of time. Your on the net saying you can't get to it can you download a ISO from that computer?

---

### Post by blue_ on 2009-12-12
some one just told me if you run update-grub it should automaticly grab your windows os also.

---

### Post by Topher88 on 2009-12-12
Alright, so here is what all has transpired thus far, for clarification purposes:

-Install Windows 7 - No Grub.
-Attempt to use LiveCD to follow directions in link left by first replier.  LiveCD acts very unstable, and can't use Internet because it requires external drivers that require restart.
-Realize that I have LiveUSB (but FORGET that it is 9.04 and not 9.10, which likely causes the following problem.
-Use LiveUSB to follow directions in link left by first replier.  Instead of re-implementing Grub, it simply provides a Grub command prompt, as shown in the image, and I was unable to log into to any OS.
-Use LiveUSB to use the Internet and copy down instructions for fixing Windows bootloader.  Succes.  Am now back where I started, with Windows 7 working but no Grub.
-Use Windows 7 to create LiveUSB of 9.10 with unetbootin.
-Attempt to follow Blue_'s advice - doesn't work.  Tells me Grub is not installed.  Must be a problem with new LiveUSB.
-Try LiveCD, and surprisingly it actually loads.  Open terminal, and issue "Grub" command.  Still tells me that Grub is not installed.  

Now I'm really up a creek, because I can't install it because I can't get on the internet on live media!  How the eff did Grub get uninstalled altogether?

Tomorrow, I'm going to re-create the LiveUSB using my GF's Ubuntu 9.10 computer in hopes that it will work better than the unebootin one - at least then I can get on the internet with it, like I could with the 9.04 LiveUSB, install Grub, and try Blue_'s advice once more.

---

### Post by darkod on 2009-12-12
> **Topher88 said:**
> Alright, so here is what all has transpired thus far, for clarification purposes:

-Install Windows 7 - No Grub.
-Attempt to use LiveCD to follow directions in link left by first replier.  LiveCD acts very unstable, and can't use Internet because it requires external drivers that require restart.
-Realize that I have LiveUSB (but FORGET that it is 9.04 and not 9.10, which likely causes the following problem.
-Use LiveUSB to follow directions in link left by first replier.  Instead of re-implementing Grub, it simply provides a Grub command prompt, as shown in the image, and I was unable to log into to any OS.
-Use LiveUSB to use the Internet and copy down instructions for fixing Windows bootloader.  Succes.  Am now back where I started, with Windows 7 working but no Grub.
-Use Windows 7 to create LiveUSB of 9.10 with unetbootin.
-Attempt to follow Blue_'s advice - doesn't work.  Tells me Grub is not installed.  Must be a problem with new LiveUSB.
-Try LiveCD, and surprisingly it actually loads.  Open terminal, and issue "Grub" command.  Still tells me that Grub is not installed.  

Now I'm really up a creek, because I can't install it because I can't get on the internet on live media!  How the eff did Grub get uninstalled altogether?

Tomorrow, I'm going to re-create the LiveUSB using my GF's Ubuntu 9.10 computer in hopes that it will work better than the unebootin one - at least then I can get on the internet with it, like I could with the 9.04 LiveUSB, install Grub, and try Blue_'s advice once more.

Depending whether you had grub1 or grub2 before windows wiped the MBR, the recovery instructions are different. And also depending whether you are restoring grub1 or grub2 you need to use 9.04 image (or before) or 9.10 image.

And all of the above is under the assumption you actually had ubuntu installed, not wubi inside windows.

Let us know how you get on.

PS. Unetbootin LiveUSB is not very partical for recovery because unfortunately unetbootin creates its own boot menu replacing the ubuntu menu (so you don't have the Try Ubuntu option for example). To get rid of the unetbootin menu you can do:
1. Open the stick.
2. In the root folder rename syslinux.cfg to syslinux.old
3. In the isolinux folder find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
4. Go back and rename the whole folder isolinux to syslinux

If this helps you with your newly created LiveUSB 9.10 boot with Try Ubuntu but do not try to restore grub. Go into your ubuntu root partition in /boot/grub folder and take a look. If you have menu.lst file there most probably you are using grub1. If you have grub.cfg then it's grub2. So use the appropriate instructions depending.

---

### Post by wilee-nilee on 2009-12-12
> **Topher88 said:**
> Alright, so here is what all has transpired thus far, for clarification purposes:

-Install Windows 7 - No Grub.
-Attempt to use LiveCD to follow directions in link left by first replier.  LiveCD acts very unstable, and can't use Internet because it requires external drivers that require restart.
-Realize that I have LiveUSB (but FORGET that it is 9.04 and not 9.10, which likely causes the following problem.
-Use LiveUSB to follow directions in link left by first replier.  Instead of re-implementing Grub, it simply provides a Grub command prompt, as shown in the image, and I was unable to log into to any OS.
-Use LiveUSB to use the Internet and copy down instructions for fixing Windows bootloader.  Succes.  Am now back where I started, with Windows 7 working but no Grub.
-Use Windows 7 to create LiveUSB of 9.10 with unetbootin.
-Attempt to follow Blue_'s advice - doesn't work.  Tells me Grub is not installed.  Must be a problem with new LiveUSB.
-Try LiveCD, and surprisingly it actually loads.  Open terminal, and issue "Grub" command.  Still tells me that Grub is not installed.  

Now I'm really up a creek, because I can't install it because I can't get on the internet on live media!  How the eff did Grub get uninstalled altogether?

Tomorrow, I'm going to re-create the LiveUSB using my GF's Ubuntu 9.10 computer in hopes that it will work better than the unebootin one - at least then I can get on the internet with it, like I could with the 9.04 LiveUSB, install Grub, and try Blue_'s advice once more.

If you can startup karmic with the thumb you can also mount the original Karmic partition and pull out anything you want to save onto a external HD and then just reinstall Karmic, this would have you back with the grub bootloader. This is just an option, if you can't get the grub to reinstall in the MBR. If it was me I would go this way, but I know what I like on a install so a install is easy for me.

---

### Post by presence1960 on 2009-12-12
we need to get a clear snapshot of what exactly is installed on your machine and it's boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by albannach1 on 2009-12-12
EDIT: doesn't work, mod please delete.

---

### Post by Mark Phelps on 2009-12-12
You said you installed Win7, so I'm presuming you have a real Win7 DVD, right?

If that's true, another approach to getting into your OS would be to do the following:
1) Use the Win7 DVD to restore Win7 boot (unless you have that already)
2) Use easyBCD to add entries to the Win7 boot loader for Ubuntu.

The first is done by booting from the Win7 DVD and running Startup Repair until boot is restored (may take up to three tries).

The second is done by going to the NeoSmart Technologies website, downloading the EasyBCD Beta (built 76) and installing that.

They have forums and tutorials that will help you figure out how to configure it.

---

### Post by Topher88 on 2009-12-12
> **presence1960 said:**
> we need to get a clear snapshot of what exactly is installed on your machine and it's boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

"No such file or directory"

EDIT:  Oops, misread the comment.  Didn't download the script.

---

### Post by Topher88 on 2009-12-12
Sorry about that!  Here are the results:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 337065775 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2cf04d55

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   336,963,575   336,961,528   7 HPFS/NTFS
/dev/sda2         598,761,472   625,135,615    26,374,144   7 HPFS/NTFS
/dev/sda3         336,979,440   598,758,614   261,779,175   5 Extended
/dev/sda5         336,979,503   588,043,259   251,063,757  83 Linux
/dev/sda6         588,043,323   598,758,614    10,715,292  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004c41b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="6888d448-4c09-47d1-ad90-0221855a5556" TYPE="ext3" 
/dev/sda1: UUID="4411211C49FA9980" TYPE="ntfs" 
/dev/sda2: UUID="ECE2D3E4E2D3B0D6" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="db2adc9f-a29c-4891-85b8-baa899e0b3cf" TYPE="ext4" 
/dev/sda6: UUID="bbedb0bf-d056-41db-9abb-e28610638e1d" TYPE="swap" 
/dev/sdb1: LABEL="TOPHER" UUID="BD4D-78EC" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sr1 on /media/U3 System type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set db2adc9f-a29c-4891-85b8-baa899e0b3cf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4411211c49fa9980
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ece2d3e4e2d3b0d6
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=db2adc9f-a29c-4891-85b8-baa899e0b3cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bbedb0bf-d056-41db-9abb-e28610638e1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 172.5GB: boot/grub/grub.cfg
 172.5GB: boot/grub/stage2
 172.5GB: boot/initrd.img-2.6.31-14-generic
 172.5GB: boot/initrd.img-2.6.31-15-generic
 172.5GB: boot/initrd.img-2.6.31-16-generic
 172.5GB: boot/vmlinuz-2.6.31-14-generic
 172.5GB: boot/vmlinuz-2.6.31-15-generic
 172.5GB: boot/vmlinuz-2.6.31-16-generic
 172.5GB: initrd.img
 172.5GB: initrd.img.old
 172.5GB: vmlinuz
 172.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by presence1960 on 2009-12-12
you do not have GRUB 2 installed to MBR, but you do have GRUB 0.97 installed to boot sector of sda5! How did that happen?

You need to reinstall GRUB 2. Boot from the Live CD/USB. Choose "Try ubuntu without any changes." When the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```

Then in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot. Refresh the GRUB 2 menu in terminal with ```
sudo update-grub
```

---

### Post by Topher88 on 2009-12-13
Sweet!  That worked!  Thanks!

> you do not have GRUB 2 installed to MBR, but you do have GRUB 0.97 installed to boot sector of sda5! How did that happen?Well, it might because earlier I tried to install GRUB 2 from a 9.04 thumb drive, forgetting that it needed to be 9.10...  But I don't know if that has anything to do with it.

---

### Post by presence1960 on 2009-12-13
> **Topher88 said:**
> Sweet!  That worked!  Thanks!

Well, it might because earlier I tried to install GRUB 2 from a 9.04 thumb drive, forgetting that it needed to be 9.10...  But I don't know if that has anything to do with it.

well that explains it! Glad you got it working! Enjoy Ubuntu.

---

