---
title: "GRUB menu gone - can't boot"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by bingasedu on 2011-10-07
I have a multi-boot Dell Optiplex with Vista, XP, and FreeBSD in partitions on one drive, and Ubuntu 9.10 on a separate drive.  The multibooting has been managed by Ubuntu's GRUB and has been working well for some time.  I recently tried to update FreeBSD and had some trouble, but was still able to access the GRUB menu.  At some point however, the GRUB menu disappeared, and the machine now only tries to boot into a bad FreeBSD install.  I thought I'd been careful not to install the FreeBSD boot mgr, but it looks like I wasn't careful enough.  I have backups of everything, but I would _much_ rather find a way to repair GRUB, than reinstall everything.  Can anyone provide me with some guidance on how to go about doing this?  Thanks very much for any help.

- Jon

---

### Post by mhgsys on 2011-10-07
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

read this closely though, I only know the live cd chroot way..so advice you to start reading from there.

---

### Post by mhgsys on 2011-10-07
btw, Although normally I would definitely advice to read above information.. I realized your a new user (beans and all) and thought this might be easier for you 
From the first link>
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by drs305 on 2011-10-07
Do you know if you were using Grub 2 or Grub legacy. If you are still using 9.10 it could go either way.

If you are using Grub 2, and you have a 9.10 Ubuntu CD, you should be able to boot the LiveCD, mount your Ubuntu partition and reinstall Grub 2 (which will write to the MBR as well). Then, as long as your BIOS points first to your Ubuntu installation, you should have your Grub 2 back.

For XY, substitute the drive letter for X and Y for the partition (sdb1, etc). Don't include the partition in the second command.
```

sudo mount /dev/sd**XY**  /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**
```

---

### Post by bingasedu on 2011-10-07
Thanks very much.  I used the 9.10 Live CD to reinstall GRUB (Grub 2 v1.97~beta) on the drive containing Ubuntu, but the machine still tried to boot into FreeBSD.  The FreeBSD/Vista/XP drive is SATA-0 and the Ubuntu drive is SATA-4, and I can't change the boot order.  I simply disabled SATA-0 as a temporary workaround and then the GRUB menu came up again.  I booted into Ubuntu successfully, though the boot process balked at it's inability to find SATA-0 for roughly a minute, before continuing on.

Do you have any idea how I can unmark the drive at SATA-0 (/dev/sda) as a bootable device?

---

### Post by drs305 on 2011-10-07
> **bingasedu said:**
> 
Do you have any idea how I can unmark the drive at SATA-0 (/dev/sda) as a bootable device?

Can you just switch the cables?

I remember when G2 came out there were problems with long delays on boot up. I'll have to try to find it. Meanwhile you could press 'e' at the Grub menu to edit the menuentry, then use the DEL key to completely remove the 'search' line'. Then CTRL-x to boot.

That was a solution to one of the early problems, but I don't recall if it was related to your issue. The edit is not persistent, so if it doesn't help it will be gone the next time you boot anyway.

---

### Post by bingasedu on 2011-10-07
If I switch the cables, won't that change the meaning of /dev/sda and /dev/sdb and leave me completely unable to boot?  I'm not as concerned about the boot delay as I am recovering access to the OSes on SATA-0.  I think I need is a way to mark SATA-0 as non-bootable, but I don't know how that's done.

---

### Post by mhgsys on 2011-10-07
you can use gparted to manage flags...right click the partition you want to edit and manage flags

---

### Post by drs305 on 2011-10-07
> **bingasedu said:**
> If I switch the cables, won't that change the meaning of /dev/sda and /dev/sdb and leave me completely unable to boot?  I'm not as concerned about the boot delay as I am recovering access to the OSes on SATA-0.  I think I need is a way to mark SATA-0 as non-bootable, but I don't know how that's done.

If you leave the 'search' line in the menuentry I don't think the drive designation will affect Ubuntu booting. One of the improvements in Grub 2 was the ability to use UUIDs, but in the Grub 2 beta I don't recall if your version is completely free of sdX use. You can try it and if it doesn't work just reset the cables.

Grub/Linux doesn't use the 'boot' flag, if that is what you are trying to remove.

You *can* install Grub 2 on the mbr of the non-Ubuntu drive and it will still boot Ubuntu. I prefer to leave the MBR of the non-Ubuntu drive alone just as a fallback (so the other OS's will still boot if Grub fails), but you can install Grub 2 to that MBR as well, using the same commands as I gave earlier and substituting the other drive in the second command. It's done all the time (putting Grub 2 on multiple MBRs) but since I'm not familiar with your other OSs did not mention it earlier. 

In all likelihood, Grub 2 originally was installed on your other drive's MBR if it's the only one that will boot and you were using Grub 2 before.

---

### Post by bingasedu on 2011-10-07
It was easy enough to try swapping cables, so I did.  Ubuntu booted fine, but Vista and XP squawked and would not boot.

GRUB/Linux may not use the boot flag, but I think what I'm trying to do is mark the drive in such a way that the BIOS does not find boot blocks there, or does not look for boot blocks there.

I'm pretty certain that GRUB was never on the other drive.  I believe it had a FreeBSD boot mgr on it.  What I'm curious about now is the fact that, prior to this problem, the GRUB menu (from SATA-4) came up whenever the machine was booted, but now the machine tries to boot from SATA-0 first.

Or is it possible that, when I originally installed Ubuntu 9.10 on the SATA-4 drive, it wrote GRUB to SATA-0?  I doubt that I would have specifically told it to do that - though I very likely said I wanted to manage multi-booting with GRUB.  Perhaps the installer wrote GRUB to SATA-0 to be sure GRUB managed multi-booting - that seems to make sense.  I think I'll try writing GRUB to STAT-0 as you suggested.

---

### Post by drs305 on 2011-10-07
> **bingasedu said:**
> GRUB/Linux may not use the boot flag, but I think what I'm trying to do is mark the drive in such a way that the BIOS does not find boot blocks there, or does not look for boot blocks there. 
There are a couple of forum members who know this stuff and frequent Grub posts -*oldfred* and *srs5694* in particular. Perhaps they will chime in.

> 
Or is it possible that, when I originally installed Ubuntu 9.10 on the SATA-4 drive, it wrote GRUB to SATA-0? 
This happens frequently. Grub 2 won't normally install itself on another drive, but especially when Grub 2 was introduced the documentation wasn't extensive and some of the online installation selections were not as clear as they could have been. Users often unknowingly installed Grub 2 to the wrong drive or to a partition.

---

### Post by oldfred on 2011-10-07
Some Dells (One IDE & one SATA port) seem to only boot from sda, but I thought the newer ones with multiple SATA drive support also let you choose which drive to boot.

Grub defaults to install to sda, so in a multiple drive install and using defaults you probably did install grub2's boot loader to sda.

Windows has to have the boot flag on a primary partition to know which partition is the active or bootable partition. A few BIOS (mostly Intel motherboard) will not let you boot anything unless you have a boot flag on a primary partition (must assume Windows?).

With multiple drives & multiple installs I like to have a copy of the Boot info script just to record what is where. Even if you do not fully understand all the details it is worth having. See BIS in drs305's signature if interested.

---

### Post by Hakunka-Matata on 2011-10-07
Please install and run boot_info_script.  Post the results, if you haven't used boot_info_script before, you'll like the information it provides.  It will make your troubleshooting process much more efficient.

---

### Post by bingasedu on 2011-10-07
> **oldfred said:**
> Some Dells (One IDE & one SATA port) seem to  only boot from sda, but I thought the newer ones with multiple SATA  drive support also let you choose which drive to boot.
This Dell Optiplex 745 is at least a few years old.  It let's me choose  the boot order between such devices as floppy, DVD, and disk, but I  can't specify an order among various devices of the same type.

> **oldfred said:**
> Grub defaults to install to sda, so in a  multiple drive install and  using defaults you probably did install  grub2's boot loader to sda.
This makes sense and explains the observed behavior well.  I'll write  GRUB to SATA-0 tomorrow and try to confirm that I've recovered the original  booting behavior/capability for all OSes.  I wish I could use Ubuntu on  SATA-4 instead of the painfully-slow-to-boot Live CD, but with SATA-0  enabled I can't boot to SATA-4.  Oh well...

> **Hakunka-Matata said:**
> Please install and run boot_info_script.   Post the results, if you haven't used boot_info_script before, you'll  like the information it provides.  It will make your troubleshooting  process much more efficient.
Wow - that script provides a lot of info.  (I ran it on SATA-4.)  Once I've written GRUB to SATA-0 I'll be able to run the script with both SATA-0 and SATA-4 enabled and then I'll post the results.  Thanks very much.

---

### Post by bingasedu on 2011-10-07
I was able to get back to it today after all.  Writing GRUB to the SATA-0 drive did the trick, and restored the boot process to the way it was before.  I'll go ahead and mark this tread as solved.  Thank you all for the very expert help!

Here's the (extensive) output of boot_info_script.sh:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958)/boot/grub on this 
    drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              96,390    64,131,479    64,035,090   7 NTFS / exFAT / HPFS
/dev/sda3          64,133,120   156,295,167    92,162,048   7 NTFS / exFAT / HPFS
/dev/sda4    *    156,296,385   312,496,379   156,199,995  a5 FreeBSD


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e1cf8

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,941,503,444 1,941,503,382  83 Linux
/dev/sdb2       1,941,503,445 1,953,520,064    12,016,620   5 Extended
/dev/sdb5       1,941,503,508 1,953,520,064    12,016,557  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0706                              vfat       DellUtility
/dev/sda2        AEF0EE48F0EE15FD                       ntfs       
/dev/sda3        E2F89C04F89BD4DF                       ntfs       
/dev/sda5                                               ufs        
/dev/sda7                                               ufs        
/dev/sda8                                               ufs        
/dev/sda9                                               ufs        
/dev/sdb1        f8ad6986-8cd9-477e-a2ea-2d102598b958   ext4       
/dev/sdb5        e347dfed-bbf7-4c5f-85f9-460bcb579a00   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="${saved_entry}"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
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

### BEGIN /etc/grub.d/09_freebsd ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "FreeBSD 8.2-release" {
#set root=(hd0,4,a)
#freebsd /boot/loader
set root=(hd0,4)
chainloader +1
}
### END /etc/grub.d/09_freebsd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.34.1" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.34.1 root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.34.1
}
menuentry "Ubuntu, Linux 2.6.34.1 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.34.1 root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.34.1
}
menuentry "Ubuntu, Linux 2.6.31.12-sctp.1" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31.12-sctp.1 root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31.12-sctp.1
}
menuentry "Ubuntu, Linux 2.6.31.12-sctp.1 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31.12-sctp.1 root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.31.12-sctp.1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-22-generic-pae root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-22-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-22-generic-pae root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f8ad6986-8cd9-477e-a2ea-2d102598b958
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 07d7-0706
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set aef0ee48f0ee15fd
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=f8ad6986-8cd9-477e-a2ea-2d102598b958 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e347dfed-bbf7-4c5f-85f9-460bcb579a00 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#JTL - 2010-06-02, mount FreeBSD 7.2 /home on sata1 here
#/dev/sda10     /mnt    ufs     -o ufstype=5xbsd
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.484393597 = 0.520113664    boot/grub/core.img                             1
  12.613471508 = 13.543611904   boot/grub/grub.cfg                             2
 418.056052685 = 448.884268544  boot/initrd.img-2.6.31.12-sctp.1               4
   0.339179516 = 0.364191232    boot/initrd.img-2.6.31-14-generic              2
   0.737624645 = 0.792018432    boot/initrd.img-2.6.31-20-generic              1
   4.050590038 = 4.349287936    boot/initrd.img-2.6.31-21-generic              1
  34.065982342 = 36.578070016   boot/initrd.img-2.6.31-22-generic              1
  34.073470592 = 36.586110464   boot/initrd.img-2.6.31-22-generic-pae          1
  28.109286785 = 30.182116864   boot/initrd.img-2.6.34.1                       1
   4.064754009 = 4.364496384    boot/vmlinuz-2.6.31.12-sctp.1                  1
   0.232169628 = 0.249290240    boot/vmlinuz-2.6.31-14-generic                 2
   0.624755383 = 0.670825984    boot/vmlinuz-2.6.31-20-generic                 2
   2.054881573 = 2.206412288    boot/vmlinuz-2.6.31-21-generic                 1
   4.081790447 = 4.382789120    boot/vmlinuz-2.6.31-22-generic                 1
   6.054122448 = 6.500564480    boot/vmlinuz-2.6.31-22-generic-pae             1
   2.058688641 = 2.210500096    boot/vmlinuz-2.6.34.1                          1
 418.056052685 = 448.884268544  initrd.img                                     4
  28.109286785 = 30.182116864   initrd.img.old                                 1
   4.064754009 = 4.364496384    vmlinuz                                        1
   2.058688641 = 2.210500096    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea f0 ff  00 f0 bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200

```

---

### Post by drs305 on 2011-10-07
Glad it's working for you.

Checking your RESULTS.txt, it's pretty obvious you have a lot of older kernels. If you want to reduce the number, a great app to rid some of them and clean up your Grub menu a bit is Ubuntu Tweak.

I just installed it in a Karmic VM to make sure it would work and it does. If you are interested, here is a link about removing older kernels. There is a section on installing and using Ubuntu Tweak to accomplish this:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by bingasedu on 2011-10-14
Thanks - Ubuntu Tweak is very straightforward to use.  Nice suggestion.

---

