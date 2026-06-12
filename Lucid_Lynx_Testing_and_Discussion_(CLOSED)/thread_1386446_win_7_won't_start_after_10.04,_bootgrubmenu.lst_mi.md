---
title: "win 7 won't start after 10.04, /boot/grub/menu.lst missing"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeremyjjbrown on 2010-01-20
Sorry if this has been answered before. I couldn't find it.

I installed lucid and now win7 won't boot. I manually specified the partitions and did not shrink the WIN7 partitions. Win7 shows up on the grub options, but when I select it the computer just restarts the BIOS instantly without win7 starting, freezing or even showing up on the screen. I tried to check my /boot/grub/menu.lst but it does not exist.  A point in the right direction would be great.

Thanks

---

### Post by hemimaniac on 2010-01-20
as with all newer releases the /menu.lst has been replaced with /grub.cfg

a look through there may help you get on the right track

---

### Post by tad1073 on 2010-01-20
open a terminal and type:
```
sudo update-grub
```
Reboot and try to get into W7.

If that doesn't work then open a terminal and type:
```
sudo fdisk -l
```

How did you shut down W7 before you installed Ubuntu?

---

### Post by VMC on 2010-01-20
> **jeremyjjbrown said:**
> Sorry if this has been answered before. I couldn't find it.

I installed lucid and now win7 won't boot. I manually specified the partitions and did not shrink the WIN7 partitions. Win7 shows up on the grub options, but when I select it the computer just restarts the BIOS instantly without win7 starting, freezing or even showing up on the screen. I tried to check my /boot/grub/menu.lst but it does not exist.  A point in the right direction would be great.

Thanks

I curious how grub boots Windows7, because it uses that recovery boot partition to boot windows7. Are you chainloading, and if so does it point to that hidden partition?

---

### Post by Reiger on 2010-01-20
If sudo update-grub fails to fix the issue; the Fedora wiki documents a (similar?) problem & manual fix: [https://fedoraproject.org/wiki/Common_F12_bugs#recovery-partition-boot](https://fedoraproject.org/wiki/Common_F12_bugs#recovery-partition-boot)

---

### Post by jeremyjjbrown on 2010-01-21
> **tad1073 said:**
> open a terminal and type:
```
sudo update-grub
```
Reboot and try to get into W7.

If that doesn't work then open a terminal and type:
```
sudo fdisk -l
```

How did you shut down W7 before you installed Ubuntu?

That's a good question. I was not the one who shut down the machine. I should have restarted it and shut it down myself.

the grub.cfg file is set to boot from sda1 so I doubt it is trying to start the recovery Partition.

None of the listed solutions helped, any other ideas?

Thanks

---

### Post by kevpan815 on 2010-01-21
If I Were You, I Would Wait Until Wubi.Exe Is Fully Functional In The Desktop CD Of Ubuntu 10.04 Alpha 3 (Currently Due Out On February 25th, 2010) And Then Use That In Order 2 Dual Boot Windows 7 And Ubuntu 10.04!

---

### Post by kansasnoob on 2010-01-21
The most helpful thing would be if you'd post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Then we can see what's actually going on.

---

### Post by ranch hand on 2010-01-21
> **kansasnoob said:**
> The most helpful thing would be if you'd post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Then we can see what's actually going on.
Yes, please do that.

---

### Post by xebian on 2010-01-21
> **jeremyjjbrown said:**
> Sorry if this has been answered before. I couldn't find it.

I installed lucid and now win7 won't boot. I manually specified the partitions and did not shrink the WIN7 partitions. ....

Thanks

I have to guess from what you said/did that you installed Lucid over the Win7 partition effectively wiping it out.  The Win7 menu entry is probably just the restore/recovery partition.

---

### Post by jeremyjjbrown on 2010-01-21
> **kansasnoob said:**
> The most helpful thing would be if you'd post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Then we can see what's actually going on.

Thanks for all of the help

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19aa19a9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    58,587,135    58,380,288   7 HPFS/NTFS
/dev/sda3          58,589,055   484,375,814   425,786,760   5 Extended
/dev/sda5          58,589,118   120,744,539    62,155,422  83 Linux
/dev/sda6         120,744,603   484,375,814   363,631,212   7 HPFS/NTFS
/dev/sda4         484,375,815   488,392,064     4,016,250  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43df71d1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F8146A7C146A3DAE" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="56AC78E4AC78C053" TYPE="ntfs" 
/dev/sda4: UUID="ec7b670f-991a-4f3f-9159-66aa46232595" TYPE="swap" 
/dev/sda5: UUID="deaf4275-880d-4125-a199-313d912c14da" TYPE="ext4" 
/dev/sda6: UUID="3293FBC4220C343B" TYPE="ntfs" 
/dev/sdb1: UUID="CA38FCF438FCDFFD" LABEL="Fixie2" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /media/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jeremy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeremy)
/dev/sdb1 on /media/Fixie2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set deaf4275-880d-4125-a199-313d912c14da
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
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set deaf4275-880d-4125-a199-313d912c14da
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=deaf4275-880d-4125-a199-313d912c14da ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set deaf4275-880d-4125-a199-313d912c14da
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=deaf4275-880d-4125-a199-313d912c14da ro single 
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set deaf4275-880d-4125-a199-313d912c14da
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set deaf4275-880d-4125-a199-313d912c14da
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f8146a7c146a3dae
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
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sda5 during installation
UUID=deaf4275-880d-4125-a199-313d912c14da  /               ext4         errors=remount-ro         0  1  
# swap was on /dev/sda4 during installation
UUID=ec7b670f-991a-4f3f-9159-66aa46232595  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sda6                                  /media/sda6     ntfs         nls=iso8859-1,umask=000   0  0  

=================== sda5: Location of files loaded by Grub: ===================


  29.9GB: boot/grub/core.img
  29.9GB: boot/grub/grub.cfg
  29.9GB: boot/initrd.img-2.6.32-10-generic
  29.9GB: boot/vmlinuz-2.6.32-10-generic
  29.9GB: initrd.img
  29.9GB: vmlinuz

---

### Post by jeremyjjbrown on 2010-01-21
So I need to change SDA1 to SDA2 in the gurb.conf. But, that document clearly states in the first line not to edit it manually.

Is there now a GUI for that? I'm not finding much on google.

---

### Post by ranch hand on 2010-01-21
You must realize that the /boot/grub/grub.cfg file is generated from the scripts listed right there in the grub.cfg file (00_header through 40_custom).  It is a real pain to edit it directly and not worth the effort as it is over written every time update-grub is run.

Try to boot to MS by highlighting the menu entry and hitting e.  This will alow you to edit the entry for that one boot only.  Change the 1 to 2.  Hit "Ctrl + x" to boot.

If that works do the stuff below.

Run;
```

gksudo gedit /etc/grub.d/40_custom

```
and;
```

gksudo gedit /boot/grub/grub.cfg

```
copy/paste your Win JerryLewis Pro entry from grub.cfg to 40_custom
Above (before) that entry put;
```

echo "Adding MS on sda2" >&2 
cat << EOF

```
Below (after) your entry put;
```

EOF

```
Save the file.

Run;
```

sudo update-grub

```
That should do it

---

### Post by VMC on 2010-01-21
> **jeremyjjbrown said:**
> So I need to change SDA1 to SDA2 in the gurb.conf. But, that document clearly states in the first line not to edit it manually.

Is there now a GUI for that? I'm not finding much on google.

From what I've read in other posts, you need to use Windows7 boot loader partition(sda1) and not Windows7 partition(sda2), in order to boot Windows7. I would be very interested that what your trying succeeds.

I wish there was an easy way to defuse Windows7 from ever creating that recovery partition. I found at least on [**hack**]("http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/"), that you can use to achieve this from the installation but not from an already installed Windows7. But this is not for the faint of heart.

I know MS reasoning for creating it in the first place - Wanting total control. 
For us grub'ers though, it makes it yet another hurtle to jump.

---

### Post by kansasnoob on 2010-01-21
Ranch hand, I'm curious what this does:

> copy/paste your Win JerryLewis Pro entry from grub.cfg to 40_custom
Above (before) that entry put;

```
echo "Adding MS on sda2" >&2 
cat << EOF
```

Below (after) your entry put;

```
EOF
```

I've always just added the entry without that.

Like:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7 (loader) (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set 56AC78E4AC78C053
chainloader +1
}

```

Still learning :D

I might note for the OP that I changed sda1 to sda2 and (hd0,1) to (hd0,2) and also changed the UUID to that of sda2.

BTW, just so you know, drive numbering still begins with 0 (zero) in grub2 but partition numbering now begins with 1 (one).

---

### Post by kansasnoob on 2010-01-21
> **VMC said:**
> From what I've read in other posts, you need to use Windows7 boot loader partition(sda1) and not Windows7 partition(sda2), in order to boot Windows7. I would be very interested that what your trying succeeds.

I wish there was an easy way to defuse Windows7 from ever creating that recovery partition. I found at least on [**hack**]("http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/"), that you can use to achieve this from the installation but not from an already installed Windows7. But this is not for the faint of heart.

I know MS reasoning for creating it in the first place - Wanting total control. 
For us grub'ers though, it makes it yet another hurtle to jump.

I'll bet you're right! I'd only installed the Win 7 RC and I installed over an existing XP!

At the very least the OP is going to need bootmgr and Boot in sda2. Eeeeeeeeeerm ........... ugly scenario :(

I almost wonder if it would be easier to use Easy BCD to boot :confused:

---

### Post by jeremyjjbrown on 2010-01-21
> **kansasnoob said:**
> Ranch hand, I'm curious what this does:



I've always just added the entry without that.

Like:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7 (loader) (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set 56AC78E4AC78C053
chainloader +1
}

```

Still learning :D

I might note for the OP that I changed sda1 to sda2 and (hd0,1) to (hd0,2) and also changed the UUID to that of sda2.

BTW, just so you know, drive numbering still begins with 0 (zero) in grub2 but partition numbering now begins with 1 (one).

Thanks for the script.

I'm going to look at my laptop when I get home to see what partition it's booting win7 from. It is functioning properly with win7 and 9.10

---

### Post by kansasnoob on 2010-01-21
> **jeremyjjbrown said:**
> Thanks for the script.

I'm going to look at my laptop when I get home to see what partition it's booting win7 from. It is functioning properly with win7 and 9.10

Did you read VMC's post though?

---

### Post by ranch hand on 2010-01-21
> **kansasnoob said:**
> I'll bet you're right! I'd only installed the Win 7 RC and I installed over an existing XP!

At the very least the OP is going to need bootmgr and Boot in sda2. Eeeeeeeeeerm ........... ugly scenario :(

I almost wonder if it would be easier to use Easy BCD to boot :confused:
Because there may be someone under a rock somewhere that is not familiar with my feelings toward that horrid OS, I beg to differ with you.

The easiest thing to do is delete Win JerryLewis Pro or whatever they want to call it.  Gives you a cleaner, safer and healthier box all around.

---

### Post by jeremyjjbrown on 2010-01-21
> **kansasnoob said:**
> Did you read VMC's post though?

Yes, that is exactly why I want to see what partition it's booting win 7 from. I may be barking up the wrong tree trying to edit grub. I am suspicious that win7 was not shutdown properly and WIN7 left a flag to boot from the first partition that Grub picked up to boot from recovery. The laptop boots properly so it's grub.cfg will tell me what setting to have it on. The first or second.

Perhaps the problem is with WIN7 and the best thing to do is repair it and then restore grub.

---

### Post by jeremyjjbrown on 2010-01-21
> **ranch hand said:**
> Because there may be someone under a rock somewhere that is not familiar with my feelings toward that horrid OS, I beg to differ with you.

The easiest thing to do is delete Win JerryLewis Pro or whatever they want to call it.  Gives you a cleaner, safer and healthier box all around.

I would like that, but I have to use proprietary software that doesn't run on linux, and is not convenient for a virtual machine.

---

### Post by Merk42 on 2010-01-21
> **ranch hand said:**
> The easiest thing to do is delete Win JerryLewis Pro or whatever they want to call it.

OFF TOPIC I know, but I never understood why you call it that.

How is calling the OS the name of someone who has had a long career with many awards and is a humanitarian a bad thing?

---

### Post by ranch hand on 2010-01-21
Ah, the man ought to be best known for his work on behalf of MD.

One of the largest research groups for MD is in France.  It utilizes boinc for its pure math research.  The absolute worst work units (or WUs in boinc speak).  They produce a lot of repeat WUs that have to check the work on the original buggy WUs.  One of the few institutions using MS as a platform for pure math calculation and analysis.

I assume they do this, being where the man is just about a God, because MS supplies them with a custom OS - Win JerryLewis Pro.  Can't think of another reason to use MS for that at all.

I have 4 of those WUs running right now.

---

### Post by oldfred on 2010-01-21
Your boot info script says you have the install of windows with the extra boot partition. Part of the boot files are in sda1 and the rest & install is in sda2. You have to boot thru sda1.

I also suspect win7 was not shut down correctly. It may require installing the windows boot loading and running repairs, then reinstalling grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Someone posted this that windows only repairs one thing each time:
Hi there, dont worry, boot from Windows 7 dvd and select repair your computer at the Install Now screen.
Run Startup repair thrice and reboot.

You will need to boot with your Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Make sure it boots windows then reinstall grub.

---

### Post by tad1073 on 2010-01-21
If you have the W7 cd yo might be able to get a way with running ckdisk on a th W7 partiton. That might clean up the orphaned nodes.

---

### Post by jeremyjjbrown on 2010-01-23
> **VMC said:**
> From what I've read in other posts, you need to use Windows7 boot loader partition(sda1) and not Windows7 partition(sda2), in order to boot Windows7. I would be very interested that what your trying succeeds.

I wish there was an easy way to defuse Windows7 from ever creating that recovery partition. I found at least on [**hack**]("http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/"), that you can use to achieve this from the installation but not from an already installed Windows7. But this is not for the faint of heart.

I know MS reasoning for creating it in the first place - Wanting total control. 
For us grub'ers though, it makes it yet another hurtle to jump.

There is. Use a live cd to create an ntfs partition with gparted. Install win7 on that partition. You will end up with win7 all on C:/, and stop MS from wasting a primary partition.

The problem here is GRUB2. There is a bug report already in about this. I've tried everything including a fresh installs. The only workarounf I've found is getting the new alpha of BCD and creating a boot loader with that. I just wish Ubuntu would wait to upgrade thing like GRUB. What's the rush?

I'm putting 8.04 back until the bug is cleared.

---

### Post by kansasnoob on 2010-01-23
> I'm putting 8.04 back until the bug is cleared.

You can revert to legacy grub you know:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by blkcat1028 on 2010-04-10
OldFred's solution worked perfectly for me. Thanks a lot. You saved my blood pressure!

---

