---
title: "Grub not booting karmic"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by _neutrin0_ on 2009-11-30
Hi,

I did a fresh install of karmic but grub refuses to load the OS.

Grub gets stuck on
```

Grub Loading.

```
...and after that I have to basically ctrl-alt-del to reboot the system.

I was running Jaunty quite nicely on the same system and I can also boot into the karmic live cd. I don't know, maybe there is some problem with the drive/partition setup with grub. Grub just hangs, not even bringing up the menu when shift is pressed.

I tried loading karmic with an older grub version. This time grub loaded but I couldn't boot into the system (probably due to some config problems with the current version).

I reformatted the partition and reinstalled karmic, but again the same problem.

Here are the results of running [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/")
```

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #12402180 on boot drive #1
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8a8a8a8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     8,193,149     8,193,087   7 HPFS/NTFS
/dev/sda2           8,193,150    10,233,404     2,040,255  82 Linux swap / Solaris
/dev/sda3          10,233,405    32,885,054    22,651,650  83 Linux
/dev/sda4          32,885,055   156,296,384   123,411,330   f W95 Ext d (LBA)
/dev/sda5          32,885,118    53,367,929    20,482,812   7 HPFS/NTFS
/dev/sda6          53,367,993    94,333,679    40,965,687   7 HPFS/NTFS
/dev/sda7          94,333,743   156,296,384    61,962,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="11880F908A469FC9" LABEL="SWAP" TYPE="ntfs" 
/dev/sda2: UUID="2df12c27-1123-4eba-b720-45618ade17ef" TYPE="swap" 
/dev/sda3: LABEL="Linux" UUID="67aa01fc-be44-48f1-bd55-ec633f0c6f6a" TYPE="ext4" 
/dev/sda5: UUID="E26C7D126C7CE2A9" TYPE="ntfs" 
/dev/sda6: UUID="9DC88C14DC7B9E11" LABEL="DEV" TYPE="ntfs" 
/dev/sda7: UUID="008F53F0A469FC90" LABEL="Misc" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows XP" 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTOUT

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root=(hd0,3)
search --no-floppy --fs-uuid --set 67aa01fc-be44-48f1-bd55-ec633f0c6f6a
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 67aa01fc-be44-48f1-bd55-ec633f0c6f6a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=67aa01fc-be44-48f1-bd55-ec633f0c6f6a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 67aa01fc-be44-48f1-bd55-ec633f0c6f6a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=67aa01fc-be44-48f1-bd55-ec633f0c6f6a ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 11880f908a469fc9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=67aa01fc-be44-48f1-bd55-ec633f0c6f6a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=2df12c27-1123-4eba-b720-45618ade17ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


   5.2GB: boot/grub/grub.cfg
   5.2GB: boot/initrd.img-2.6.31-14-generic
   5.2GB: boot/vmlinuz-2.6.31-14-generic
   5.2GB: initrd.img
   5.2GB: vmlinuz

```

Thanks.

---

### Post by oldfred on 2009-11-30
I see several issues but nothing that should prevent booting grub or Ubuntu.

If your windows is Vista you will have to repair it anyway since it shows it starts at 63 and when you edited partitions you did not have the checkbox unchecked. So I would repair the Vista install first since it will overwrite the MBR anyway. Then reinstall grub to the MBR.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Also you have a label on the windows partition of swap, since it is just a label and all the UUID's look correct it should not cause a problem but I would change it.

In your windows your boot.ini refers to the wrong windows partitions. As part of fixing windows you will have to update boot.ini from partition(4) to partition(1). I do not know if you want to boot the other sda6 partition but 3 & 4 are incorrect since you must have deleted  partitions. If you use a Ubuntu text editor be careful to only change the number. Linux and Windows do not use the same line ends and may mess up the file.

---

### Post by _neutrin0_ on 2009-11-30
Thanks for your info. Hmmm.... those Vista  entries in the results log do look a bit suspicious. 

Yes I had installed Vista once-upon-a-time long long ago, but I have long since removed and replaced it with Ubuntu/XP combo. It's been this way since 8.04 or maybe earlier, and I never once had similar situation with grub.

I will take your suggestions and try and fix the problems you have pointed out.

---

### Post by _neutrin0_ on 2009-11-30
Nope!

Fixed and did a fresh install, still no luck! Same thing with Grub.

Is there a way to use an older version of grub? In fact I tried it and I even got the white ubuntu logo loading screen, but after that it gave me a whole host of errors.

Thanks.

---

### Post by darkod on 2009-11-30
> **_neutrin0_ said:**
> Nope!

Fixed and did a fresh install, still no luck! Same thing with Grub.



Can you specify more clearly what you did? Since you say you are not using Vista you did not try to restore vista mbr on the drive right? You should use windows XP repair in that case.

And both sda5 and sda6 show some suspicious message about starting from sector 63. I guess you can't just move the data temporarily and format as ntfs those partitions right? You could do that with one partition if it's only data, move the data to another partition or external hdd, format, and put the data back. But one of the two partitions is your XP system I guess, and you can't do the same with it.

Is reinstalling the XP an option?

Another question is, did your system Ubuntu/XP work exactly like this with Jaunty? The XP on sda5 (or sda6) is on logical partition inside extended, there is still confusion if XP can work like that at all. Personally, I never had XP on logical, and I've seen articles saying it demands primary partition. If somehow during the upgrade to Karmic XP was "moved" from primary to logical, that can be a problem too.

---

### Post by oldfred on 2009-11-30
If a NTFS partition is for XP or before starting at 63 is ok, it was the change to Vista that starts at a higher number.

Darko is correct in that you cannot boot Windows in extended partitions. But I have seen cases where a Vista or Win7 can boot from the extended partition if the first windows boot is in a primary partition. Win7 and Vista combine all windows boots into one partition and in the boot.ini you select which windows to boot. Grub can then only boot into that one windows in the primary partition. 

Is the only error message you still get is grub loading and nothing?

---

### Post by _neutrin0_ on 2009-12-01
> **darkod said:**
> Can you specify more clearly what you did? Since you say you are not using Vista you did not try to restore vista mbr on the drive right? You should use windows XP repair in that case.

Yeah, I did fix booting into XP using it's CD -- Fixmbr, Fixboot and FixNtldr and fixing the XP boot. I can boot into XP which is on sda5 with XP's boot loader.

> **darkod said:**
> 
And both sda5 and sda6 show some suspicious message about starting from sector 63. I guess you can't just move the data temporarily and format as ntfs those partitions right? You could do that with one partition if it's only data, move the data to another partition or external hdd, format, and put the data back. But one of the two partitions is your XP system I guess, and you can't do the same with it.

XP is on sda5. sda6 had Vista long ago, but I removed it (long ago).

> **darkod said:**
> 
Is reinstalling the XP an option?


Oops! That is going to be a pain ](*,). 

> **darkod said:**
> 
Another question is, did your system Ubuntu/XP work exactly like this with Jaunty? The XP on sda5 (or sda6) is on logical partition inside extended, there is still confusion if XP can work like that at all. Personally, I never had XP on logical, and I've seen articles saying it demands primary partition. If somehow during the upgrade to Karmic XP was "moved" from primary to logical, that can be a problem too.

It's been like this since 7.10 (Gutsy) and there have been no problems. In fact I have several machines where XP is on a logical partition and they are working ok. In fact, this machine also boots into XP (on sda5) with only the XP's boot loader.

> **oldfred said:**
> 
Is the only error message you still get is grub loading and nothing?

Unfortunately yes. Grub (the newer version) just hangs on the "Grub Loading." prompt. I tried an older version and it goes beyond the grub menu and I can even see the loading ubuntu logo  but after that the boot fails with messages like "can't mount /proc/(something)". (Sorry but I did copy those messages). Oh, and I can boot into XP (sda5) with the older grub version without problems.

Looks like my machine has gone fubar.

Thanks.

---

### Post by oldfred on 2009-12-01
The boot flag is on sda1 so your boot of sda5 is thru sda1 and that is about the only way to boot windows in an extended partition.

Using old grub have you tried turning off the spash and quiet entries to see it boot line by line. That will stop at the error and give a better explanation of the problem. Grub2 seems to be doing more checking so it may be the same problem.

---

### Post by _neutrin0_ on 2009-12-01
> **oldfred said:**
> The boot flag is on sda1 so your boot of sda5 is thru sda1 and that is about the only way to boot windows in an extended partition.

That is correct. Oh I see what you mean when you said "windows can't install on logical partition". You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot **is** via sda1. sda1 is there only for that purpose.

> **oldfred said:**
> 
Using old grub have you tried turning off the spash and quiet entries to see it boot line by line. That will stop at the error and give a better explanation of the problem. Grub2 seems to be doing more checking so it may be the same problem.

Ok will try that.

Thanks.

---

### Post by _neutrin0_ on 2009-12-01
Thanks all you guys. I managed to solve this issue by replacing Grub2 with an older version of grub.

I guess earlier there was a conflict between versions (probably config files). 

This is what I did to get rid of grub2 

Boot into the live cd, connect to the internet and start a terminal.

Then chroot into your installed system. In my case (sda3)
```

$ sudo mount /dev/sda3 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ cp /etc/resolv.conf /mnt/etc/resolv.conf
$ sudo chroot /mnt
```

backup the grub files.

```

# sudo cp /etc/default/grub /etc/default/grub.old
# sudo cp -R /etc/grub.d /etc/grub.d.old
# sudo cp -R /boot/grub /boot/grub.old
```

remove grub2
```

# sudo apt-get purge grub2 grub-pc
```

install old grub
```

sudo apt-get install grub
```

create the menu.lst and stage1/stage2 files
```

# sudo update-grub
# sudo grub-install hd0
```

come out of chroot.
```

# exit
# sudo umount /mnt
```

Reboot.

Further reference.
[Uninstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

Thanks.

---

