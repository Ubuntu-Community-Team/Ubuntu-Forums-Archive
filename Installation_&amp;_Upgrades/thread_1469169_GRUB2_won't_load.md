---
title: "GRUB2 won't load"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by phibit on 2010-05-02
So I recently tried to install Ubuntu Lucid in the following configuration

RAID1 500GB Array (2x500GB):
 - /dev/md0 : mounted as /
 - /dev/md1 : mounted as swap
 - /dev/md2 : mounted as /home

The installation procedure went fine, and it said it had successfully installed GRUB2. But then, when I tried to boot up the fresh system, GRUB2 didn't even load!!

It's not giving me any GRUB errors, or giving me a 'grub recovery>' prompt, so I suspect that it really isn't even booting into GRUB.

I tried booting into the LiveCD, and installing grub to BOTH /dev/sda and /dev/sdb, but it still does not work, and I am at a loss.

Has anybody else had this problem?

Thanks!

---

### Post by cjames1968 on 2010-05-02
I'm having the same problem.  I have been through every solution out there.  Manual Partition from LiveCD, manually installed Grub and tried setup from command prompts.  

Do not have /boot/grub/stage1 so bombed.  Went through the process on the 'Dual Boot' thread (which I'm not but that's where my searches kept bringing me.)  

I'm trying to boot to my /dev/sbd1.  All looks clean when sudo fdisk -l. Has asterisk as the boot partition.  Used the sudo grub-install commands but still bombed.  Pretty much a newbie so am limited on commands.

PS - System hangs on GRUB menu on boot.  Cannot access Grub menu - have to reset machine.

---

### Post by phibit on 2010-05-02
What your describing isn't exactly the same as my problem, because GRUB actually loads in your case.

Also, GRUB2 doesn't have /boot/grub/stage1, so you should ignore all solutions that involve a stage1. Maybe you could try reinstalling from scratch? Otherwise I'd suggest just booting into a LiveCD and running the following:

sudo grub-install /dev/sdX

Where X is your corresponding drive. This will regenerate a few things for you automatically, and should rewrite your MBR on /dev/sdX IIRC.

As for my issue, GRUB2 doesn't even load at all, so there's either a problem with the way GRUB is being written to the bootsector, or there's something keeping it from loading.

What I'm trying right now might be stupid but:

1. Booted into the LiveCD (NOT ALTERNATE)
2. Choose to 'Try Ubuntu bla bla'
3. Installed mdadm and mounted my relevant RAID arrays /dev/md0, /dev/md1 and /dev/md2.
4. When into the Installation mode, it now sees /dev/md0.
5. Chose to mount /dev/md0 as /, /dev/md2 as /home
6. Started installing...

I know this isn't the recommended way, and I have a feeling it will completely glitch without using the alternate CD. ARGH!!

---

### Post by utnubuuser on 2010-05-02
Have you googled "Fake-raid Ubuntu"?
Here's one of the RAID threads:
> [http://ubuntuforums.org/showthread.php?t=1453069]("http://ubuntuforums.org/showthread.php?t=1453069")

---

### Post by phibit on 2010-05-02
Hey guys, thanks for the replies. Turns out this last solution I tried worked, oddly enough. I guess it was just a GRUB2 bootsector issue after all.

All my raid devices are working fine!! This is excellent!

---

### Post by dino99 on 2010-05-02
Note: grub2 does not like grub1, its important, so remove/purge everything about grub1.

Only grub-pc and grub-common might be installed, then:

sudo grub-mkconfig && update-grub

there is a solution to access your distro partition from outside when you cant boot:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

follow this tread with your real path

---

### Post by cjames1968 on 2010-05-02
> **phibit said:**
> Hey guys, thanks for the replies. Turns out this last solution I tried worked, oddly enough. I guess it was just a GRUB2 bootsector issue after all.

All my raid devices are working fine!! This is excellent!

Which solution worked for you?  I'm @ wits end.  This is a fresh install, so I've blown it away several times to no avail. Thanks in advance...

---

### Post by cjames1968 on 2010-05-02
OK - all.  As you'll see from my 'beans' I'm a total neophyte.  I finally figured out what I was doing wrong.  It's a classic case of either all the posts are totally wrong, or I'm an idiot.  Guess which?  I'm an idiot.  Due to 20 years of misplaced windows-centricity, I was totally misunderstanding partitioning for /,/boot,and swap.  Back up and running...obviously this belongs on a different thread anyway.  Thanks...

---

### Post by phibit on 2010-05-02
Glad you finally got it working! As a sidenote, grub2 takes roughly 20 seconds to kick in for me... Is that usual?

---

### Post by phibit on 2010-05-02
ARGH!! Ubuntu was working fine, then for some reason I rebooted it, and now grub2 is telling me:

unknown filesystem
grub rescue>

I tried using the livecd to run grub-install /dev/sda but it says the same thing, unknown filesystem, grub-probe not able to determine filesystem.

How do I fix this?! I was so happy :(

---

### Post by phibit on 2010-05-03
Okay, so I'm still not able to boot with GRUB2. Bearing in mind I have the following configuration:

RAID 1 Array (sda + sdb):
 - /dev/md0 : 20 GB for /
 - /dev/md1 : 2 GB for swap
 - /dev/md2: 470GB for /home

Windows 7 partition (sdc1) -- I'm not sure if this matters.

GRUB2 is supposedly installed on both /dev/sda and /dev/sdb, like it should be, but when I try to start up, grub gives me this error:

```

grub error
reason: unknown filesystem
```

And when I tried to reinstall grub from the LiveCD, I get the following error (with /dev/md0 mounted on /mnt):

```
$ sudo grub-install --modules="raid mdraid" --root-directory=/mnt /dev/sda
/usr/sbin/grub-probe: error: unknown filesystem
Installation finished. No error reported.
```

The "installation finished" part leads me to believe that the problem is fixed, but sadly my machine still won't boot.

I'm at a loss as to what to do... I looked through some launchpad bug reports and it seems like this type of bug already existed for RAID1 and grub2, but since has been fixed.

Any ideas?

Below are the results to the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,961,779    41,961,717  fd Linux raid autodetect
/dev/sda2          41,961,780    50,363,774     8,401,995  fd Linux raid autodetect
/dev/sda3          50,363,775   976,768,064   926,404,290  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    41,961,779    41,961,717  fd Linux raid autodetect
/dev/sdb2          41,961,780    50,363,774     8,401,995  fd Linux raid autodetect
/dev/sdb3          50,363,775   976,768,064   926,404,290  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   205,519,544   205,519,482   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62    15,650,907    15,650,846   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/md0         89b61075-d6ae-4e8f-8892-b2b450961764   ext4                                     
/dev/md2         378da989-75cd-4996-8cae-0e01aeaecb65   ext4                                     
/dev/sda1        60598e32-0e8e-8583-e368-bf24bd0fce41   linux_raid_member                               
/dev/sda2        62afbb0c-7391-44b3-e368-bf24bd0fce41   linux_raid_member                               
/dev/sda3        6423cc0e-a85f-2d7a-2b4a-84e6e0eac0d2   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60598e32-0e8e-8583-e368-bf24bd0fce41   linux_raid_member                               
/dev/sdb2        62afbb0c-7391-44b3-e368-bf24bd0fce41   linux_raid_member                               
/dev/sdb3        6423cc0e-a85f-2d7a-2b4a-84e6e0eac0d2   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9CF87743F8771AAA                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        d3b1aa4b-1ce1-4725-9921-db721cab8d0b   ext3                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        60C8-E84B                              vfat       USBKEY                        
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/d3b1aa4b-1ce1-4725-9921-db721cab8d0b ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/9CF87743F8771AAA  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== md0/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 89b61075-d6ae-4e8f-8892-b2b450961764
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 89b61075-d6ae-4e8f-8892-b2b450961764
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 89b61075-d6ae-4e8f-8892-b2b450961764
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=89b61075-d6ae-4e8f-8892-b2b450961764 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 89b61075-d6ae-4e8f-8892-b2b450961764
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=89b61075-d6ae-4e8f-8892-b2b450961764 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 89b61075-d6ae-4e8f-8892-b2b450961764
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 89b61075-d6ae-4e8f-8892-b2b450961764
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 9cf87743f8771aaa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=89b61075-d6ae-4e8f-8892-b2b450961764 /               ext4    errors=remount-ro 0       1
# /home was on /dev/md3 during installation
UUID=378da989-75cd-4996-8cae-0e01aeaecb65 /home           ext4    defaults        0       2
# swap was on /dev/md2 during installation
UUID=1660a5dc-be29-4dd7-889e-e0224e1b1529 none            swap    sw              0       0

#Media Drive
UUID=d3b1aa4b-1ce1-4725-9921-db721cab8d0b	/media/MediaDrive	ext3	defaults	0	0

==================== md0: Location of files loaded by Grub: ====================


   2.6GB: boot/grub/core.img
   2.2GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-21-generic
  17.4GB: boot/vmlinuz-2.6.32-21-generic
   2.4GB: initrd.img
  17.4GB: vmlinuz

```

---

### Post by phibit on 2010-05-03
Oh there's a new development. Grub no longer gives me an 'unknown filesystem' error, now I'm getting.

```
grub error: no such disk
```

And when I run the ls command in the grub rescue> shell, it does not list my raid devices (e.g. md0, md1, md2).

---

### Post by phibit on 2010-05-03
The latest procedure I have tried:

[LIST=1]
[*]Boot into LiveCD
[*]apt-get install mdadm
[*]mdadm --auto-detect
[*]mount /dev/md0 /mnt
[*]mount --bind /dev /mnt/dev && mount -- bind /proc /mnt/proc && mount -- bind /sys /mnt/sys
[*]chroot /mnt
[*]grub-install --no-floppy --recheck --modules="raid mdraid" /dev/sda
[*]grub-install --no-floppy --recheck --modules="raid mdraid" /dev/sdb
[*]umount all of the above and reboot
[/LIST]

Still no success... I think this procedure might have been exactly analogous to the last, because I was presented with the same exact error.

---

### Post by phibit on 2010-05-03
I've recently tried crying, that didn't work either...

---

### Post by Edward_P on 2010-05-03
Well, if it helps: 

I've followed about the same path and am stuck at about the same place...:sad:

Have an AMD Athlon64 system. Worked fine on previuous Ubuntu 9.10.

I have two disks:
sda with windows XP en two extra partitions and 
sdb with Ubuntu on sdb1, 2 and 3.
Used Grub1 very happily, then switched to grub2, also fine.
A few days ago I tried to upgrade to Ubuntu 10.04 AMD64 and problems escalated from there onward.

I can only work on my computer with a live version of Ubuntu. 
Windows doesn't want to load... and I have some pretty essential things that I need there.

Still haven't lost courage. I will try to re-install Ubuntu 9.10 and grub1 of -2.
Will see if things will return to normal.

Bon courage!

---

### Post by phibit on 2010-05-03
Seriously, how is it possible that grub2 can't be configured to boot with RAID1? I refuse to believe that...

---

### Post by phibit on 2010-05-03
Also, I should specify that I'm not using FakeRAID, but a Linux Software Raid... Not sure how much of a difference that makes.

---

### Post by phibit on 2010-05-04
Okay, the crying is over. I am writing this post from my recently fixed Ubuntu installation.

**Preface Notes:**
[LIST]
[*]This **mainly** applies to the specific RAID1 situation that is described earlier in the thread. If it can be applied to your specific situation,  great, but be aware this specifically relates to SOFTWARE RAIDS and GRUB2.
[*]If at all possible, use the alternate CD installer and do an installation from **scratch** (i.e. repartition your RAID devices, format them). The only reason I struggled with this for so long was because I was trying to save a specific RAID partition with my /home directory on it.
[*]Before trying this, have at least one liveCD ready on a USB key or CD/DVD, or another computer. Having access to firefox and google helped a lot.
[/LIST]

**The Problem**:
Somewhere along the way, in my stupidity, I had run the following command from LiveCD when trying to fix my grub boot-loader:

```
grub-install --modules="raid mdraid" **/dev/md0**
```

Since an md device doesn't have a boot sector, this somehow made the file-system on /dev/md0 unreadable. This is why I kept getting the error:

```
grub-probe error: unknown filesystem
```

I finally figured it out by running the following command:

```
file -s /dev/md0
```

THIS COMMAND IS SUPPOSED to give back something along the lines of 

```
/dev/md0: Linux rev 1.0 **ext4 filesystem** data, UUID=4f94e18a-8e26-461e-be90-7e4103ec8bbf (needs journal recovery) (extents) (large files) (huge files)
```

But instead was reading back something about a boot sector.

Luckily for me, I was able to scrap my /dev/md0 installation and simply reinstall ubuntu. I chose to do it from the regular LiveCD, not the Alternate CD that has default RAID support.

To be clear, it is possible to do a RAID1 install from the regular LiveCD, with the following steps, though I would recommend the alternate CD, (it's easier and lets you partition your RAID devices in the actual installer).

**The Solution:**

[LIST=1]
[*]Boot into the LiveCD, select Try Ubuntu
[*]Open a terminal, enter ```
sudo apt-get install mdadm
```
[*]Assuming you already have all your raid devices configured, simply run "sudo mdadm --auto-detect" and it should detect them (** if you don't have your devices configured, create the partitions manually using fdisk, then use mdadm --create, and mkfs.ext4 or mkswap on the new /dev/md* devices)
[*]From here, you can select Install Ubuntu
[*]Follow the steps until you reach the partitioner, then select "manual"
[*]Here you should see your raid devices like /dev/md0, /dev/md1 etc... Select the proper filesystem types and mount points
[*]Continue with the installation as normal, grub will be installed etc..
[*]At the end of the installation (THIS IS VERY IMPORTANT), select "keep testing ubuntu" and go back to the terminal.
[*]Right now, your root filesystem should be mounted on /target, so run ```
sudo mount --bind /dev /target/dev && sudo mount --bind /proc /target/proc && sudo mount --bind /sys /target/sys
```
[*]Run a ```
sudo chroot /target
```
[*]Now you are chrooted into your fresh install, make sure to install ```
# apt-get install mdadm
```. This will install mdadm on your hard disk.
[*]I think the mdadm installation automatically reconfigures grub, but for good measure run: ```
# update-grub
``` and then ```
# grub-install /dev/sdX
```" for all X of your raid devices (e.g. /dev/sda and /dev/sdb)
[*]Press Ctrl+D to exit the chroot shell, then umount all the previous folders in reverse order.
[*]Reboot and pray that grub catches on, detects all your md devices properly.
[/LIST]

Note that if you stop and reboot at step 8, GRUB will load but booting will fail and you will be dropped to an initramfs> shell, saying that the root device wasn't found. I learnt this the hard way, but you can still recover by booting back into the LiveCD and following steps 9-14.

Forgive me if the instructions are a bit off, it's all from memory, but essentially that's the gist of it.

---

### Post by frantid on 2010-05-04
nice post phibit.

---

### Post by phibit on 2010-05-04
thank you :)

---

### Post by Puscifer on 2010-09-19
I've been working with Ubuntu for a few months, everything is easy to do but you have to read some webpages to get it done. 

Now I install windows XP in sda2 and I had Ubuntu in sda1. I followed [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html) and I got Ubuntu working but no Grub Menu, just blank screen with a blinking cursor and then I get my Ubuntu login. 

computer Specs: Lucid 10.04, Kernel Linux 2.6.32-24-generic
Dell dimension 9150 Intel Pentium D 2.8

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   408,275,909   408,273,862  83 Linux
/dev/sda2         408,275,910   602,839,124   194,563,215   7 HPFS/NTFS
/dev/sda3         602,839,125   613,072,529    10,233,405   7 HPFS/NTFS
/dev/sda4         613,072,894   625,141,759    12,068,866   5 Extended
/dev/sda5         613,072,896   625,141,759    12,068,864  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              40       409,639       409,600 System/Boot Partition
/dev/sdc2   1,661,245,208 1,953,262,983   292,017,776 HFS+
/dev/sdc3         409,640 1,661,245,207 1,660,835,568 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        74deb115-cde7-4747-88a4-13814e10a443   ext4                                     
/dev/sda2        506CFFDD6CFFBBB2                       ntfs                                     
/dev/sda3        905CA45B5CA43E3A                       ntfs       Swap                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2c0be9c1-bb75-4a95-8c3b-26aae20c25de   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a2abf679-a95e-466c-a025-419e8fa31c40   ext3       Musica                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        70D6-1701                              vfat       EFI                           
/dev/sdc2        cba04167-e73b-3562-a163-e3e212dd7478   hfsplus    AppleBack                     
/dev/sdc3        806b43f6-4a88-4dc8-9917-113c70f8f1c5   ext3       Puscifer                      
/dev/sdc: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Musica            ext3       (rw)
/dev/sdc3        /media/Puscifer          ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc2        /media/AppleBack         hfsplus    (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
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
search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
set locale_dir=($root)/boot/grub/locale
set lang=
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
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=74deb115-cde7-4747-88a4-13814e10a443 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74deb115-cde7-4747-88a4-13814e10a443
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
proc       /proc          proc  nodev,noexec,nosuid  0  0  
/dev/sda1  /              ext4  errors=remount-ro    0  1  
/dev/sda5  none           swap  sw                   0  0  
/dev/sdb   /media/Musica  ext3  default              0  0  
/dev/sdb1  /media/Musica  ext3  defaults             0  0

=================== sda1: Location of files loaded by Grub: ===================


 197.7GB: boot/grub/core.img
  41.7GB: boot/grub/grub.cfg
 197.7GB: boot/initrd.img-2.6.32-21-generic
 199.7GB: boot/initrd.img-2.6.32-22-generic
 199.3GB: boot/initrd.img-2.6.32-23-generic
 197.9GB: boot/initrd.img-2.6.32-24-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
 197.7GB: boot/vmlinuz-2.6.32-22-generic
 198.6GB: boot/vmlinuz-2.6.32-23-generic
 197.8GB: boot/vmlinuz-2.6.32-24-generic
 197.9GB: initrd.img
 199.3GB: initrd.img.old
 197.8GB: vmlinuz
 198.6GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  d4 1f f8 3f 4f 76 9e 02  07 f7 55 c5 c2 8c a5 05  |...?Ov....U.....|
00000010  37 c8 97 39 ff fa 3e 15  03 20 ff e4 5d d0 b7 42  |7..9..>.. ..]..B|
00000020  62 19 13 f6 ba e0 72 f8  e6 56 fa 1d 75 8c 0a 06  |b.....r..V..u...|
00000030  e8 9d d8 52 44 ad 0e fa  2b 75 35 4c 8a 5c 90 5b  |...RD...+u5L.\.[|
00000040  e5 ea 30 c9 42 0d 20 78  6c ad e2 d4 0a e1 85 26  |..0.B. xl......&|
00000050  a0 46 61 73 2d 93 4b a0  b0 65 aa 6d 53 d3 da ba  |.Fas-.K..e.mS...|
00000060  ca 5d d0 41 eb b4 34 b2  b5 42 5c 59 5a 5f 44 57  |.].A..4..B\YZ_DW|
00000070  ec 4b 80 f0 20 9b 51 8a  99 0d 21 9c d8 2f d7 61  |.K.. .Q...!../.a|
00000080  ac af e4 a7 81 64 6a 66  5b 1f 56 38 85 3f 2e 79  |.....djf[.V8.?.y|
00000090  10 d5 b7 70 e3 03 00 ea  39 f8 39 b2 62 00 54 c8  |...p....9.9.b.T.|
000000a0  0a 6c 8b 7b 4c 66 d1 30  03 2d dc 5e fd e1 27 18  |.l.{Lf.0.-.^..'.|
000000b0  28 e0 90 9c a7 21 02 fd  95 15 43 d3 f5 47 ed 76  |(....!....C..G.v|
000000c0  43 ce 81 44 3c 5b 0b 24  fd 1c 6c db 72 6a bf af  |C..D<[.$..l.rj..|
000000d0  32 a4 d7 a8 05 98 11 cd  46 a5 99 53 18 8c d6 67  |2.......F..S...g|
000000e0  f4 39 1a 3c 1f b5 c0 3f  a6 6a 99 b0 d7 5c 12 08  |.9.<...?.j...\..|
000000f0  10 e0 69 b5 7c 89 f9 31  83 f1 4a 75 a5 e6 f8 83  |..i.|..1..Ju....|
00000100  ab 59 21 59 01 7a 27 36  11 50 7b 2f e5 c6 b6 33  |.Y!Y.z'6.P{/...3|
00000110  80 35 f9 44 f8 e4 1c d6  b3 e1 6d c4 c2 f2 ab 28  |.5.D......m....(|
00000120  e4 ab ab 9e 92 e1 4b 5b  79 7a 53 ae b3 17 60 52  |......K[yzS...`R|
00000130  23 5e cd 52 0c 9d 1f 70  8c 3b 22 61 c6 7a e6 76  |#^.R...p.;"a.z.v|
00000140  54 15 ed 98 33 c0 19 3b  81 34 de ea 3c 82 e5 0d  |T...3..;.4..<...|
00000150  e5 0e d7 c8 2c 0a 2e 52  dc 9b ee 3b d3 8c 72 c9  |....,..R...;..r.|
00000160  c9 ef 98 b0 0c c5 68 a6  a9 5d b6 4c ce 84 88 f0  |......h..].L....|
00000170  b5 4f c7 f9 f3 c5 a7 4b  b6 65 97 44 8c e3 0a 12  |.O.....K.e.D....|
00000180  d3 4b bf 53 5a 29 d2 2c  a8 e2 be 0f f5 3e cd 34  |.K.SZ).,.....>.4|
00000190  d2 53 9a 18 29 05 82 64  21 45 e5 66 68 69 98 f1  |.S..)..d!E.fhi..|
000001a0  f9 25 69 22 81 f3 6b e6  1f 97 b4 fd 2d 1b dd 15  |.%i"..k.....-...|
000001b0  3c 25 a6 1f 0c 6f 76 28  71 13 ec f0 60 ae 00 fe  |<%...ov(q...`...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 b8 00 00 00  |...........(....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

This is the result for my boot test, everything looks fine and now Im really lost and with no direction to follow.

---

