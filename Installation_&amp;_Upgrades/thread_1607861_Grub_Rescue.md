---
title: "Grub Rescue"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Dumpy Dumpster on 2010-10-28
Tearing my hair out over installation of Lubuntu onto an old laptop P3/700/256 RAM using a Lexar CF 8MB drive.  Version 10.10 would not install at all, but version 10.04 worked its way through only to not boot up and give the Grub Rescue prompt.
I have tried to work through the Grub rescue notes but nothing works out with commands - I just end up with command not found or some such instruction.  The 'ls' command is the only one that produces anything and that is: (hd0) (hd0,1) and (fd0)
I have tried to reinstall Grub with Rescatux and that says that the Grub reinstallation was successful - but still the system will not boot up.
Any help available please?

---

### Post by Rubi1200 on 2010-10-28
Please post the results from the boot-script linked at the bottom of my post.

Wrap the text with the # tag when posting back here.

Thanks.

---

### Post by arpanaut on 2010-10-28
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Dumpy Dumpster on 2010-10-29
Thanks Rubi1200.  All I get is 'No such file/command' with both the variations of input - so no file for you.

Thanks also arpanaut, I will have a go at that link.  I do get the impression that it is more to do with the BIOS than the installation as I get similar results with the Hardy Heron disc, even though the memory is a bit small to actually run the OS

Also for info, I have set 'partman/alignment=cylinder' at the start of installation but that seems to make no difference.

So in the absence of other suggestions, I will reflash the BIOS and if that does not work, it is for the rubbish skip!

Thanks again to you both

---

### Post by adrian15 on 2010-10-29
> **Dumpy Dumpster said:**
> 
I have tried to reinstall Grub with Rescatux and that says that the Grub reinstallation was successful - but still the system will not boot up.
Any help available please?

Is there any possibility that you repeat the Rescatux's Restore Grub to the MBR option, then use the View Logs option and post here the

grub-install.log file contents?

I want to make sure that it is not a Rescatux's problem but a grub2 one.

Thank you very much!

adrian15

---

### Post by Dumpy Dumpster on 2010-10-29
Thanks adrian15.
I now feel the problem does not lie with Grub.  Here is the story:  Tried to install 2 OS, Lubuntu 10.04 and Puppy 4.3.1 using CDROMs. Not both at once!, but each having sole occupancy. All went in OK, but on the reboots, I get the Grub error.  Each time, I removed the CF drive from the laptop and connected it up to a standard desktop and the system booted up perfectly normally!  So the problem cannot be with the installation or CF drive, but must lie with some compatibility problem inside the laptop.  The laptop is a Dell L400, which I agree is old, but then Lubuntu(and indeed Puppy)should fit the bill there nicely.
Rather a puzzle!

---

### Post by adrian15 on 2010-10-29
> **Dumpy Dumpster said:**
> Thanks adrian15.
I now feel the problem does not lie with Grub.  Here is the story:  Tried to install 2 OS, Lubuntu 10.04 and Puppy 4.3.1 using CDROMs. Not both at once!, but each having sole occupancy. All went in OK, but on the reboots, I get the Grub error.  Each time, I removed the CF drive from the laptop and connected it up to a standard desktop and the system booted up perfectly normally!  So the problem cannot be with the installation or CF drive, but must lie with some compatibility problem inside the laptop.  The laptop is a Dell L400, which I agree is old, but then Lubuntu(and indeed Puppy)should fit the bill there nicely.
Rather a puzzle!

Just in order I know what your situation is. The CF drive instead of being 8 MB size as said in your first message is 8 GB size, isn't it?

Are you installing Lubuntu from the CF to the internal hard disk or are you installing Lubuntu to the CF itself?

If you are installing Lubuntu to the CF itself it might be that either you are seeing internal hard disk boot or that maybe:

Lubuntu installation is considering your CF as a first hard disk and maybe it is a second one when plugged it in your old computer. (Or viceversa).

There is an advanced option at *Ubuntu installation that lets you choose a partition to install Grub to. What I am not sure if it lets you define the bios hard disk boot order as you can do in Fedora installations.

Another workaround that might work would be to install syslinux into the CF (Fix Boot of Windows on Super Grub1 Disk) and set the Linux partition as the bootable one and then install grub into the partition boot sector.

adrian15

---

### Post by Dumpy Dumpster on 2010-10-30
Thanks again adrian15,
To answer:  Sorry typo error - it is 8GB
I am trying to install direct to the CF drive - no other disc is present or connected when using the CF.
I have looked at Syslinux and it's use is well above my capabilities!
Your idea to put the Grub onto its own partition seems the way - I was wondering if the Dell could 'see' the very first part of the OS partition where presumably the Grub files reside.  So I will try with Gparted, putting a unused partition or else just a blank partition or even the Linux-swap first and see if that helps.  From what I have found out, it seems to be a partition problem and allowing Lubuntu or Puppy to do partitioning for themselves does not seem to work out with this setup.
If the Grub needs its own partition, perhaps you could suggest what/where it should be.   At present I have the main partition (/dev/hda1 ext2 flagged bootable) and Linux-swap.
(/dev/hda2/2xRAM) only.
I have just placed an unallocated 500MB space in front of the /dev/hda1 partition - still no boot but the Grub error is now 17 not 2 as before.  Significant?

---

### Post by Dumpy Dumpster on 2010-10-30
Tried another install - Lubuntu to do its own partitioning, but not to include the F6 options ie noapic,nolapic, nodmraid but including partman/...   No change - back to Grub Rescue.
Ran Rescatux - said sucess - looked in grub-install - no log.file.contents, but grub-install_log text reads: Have to copy this out.....

sudo unable to resolve host debian
sda1 sda2 sda5
Detected grub install partitions: sda1
a: TRUE sda1 ununtu-10.04-LTS-
sda1
DEBUG: detected hard discs: sda
sda
1
cp: cannot stat '/boot/grub/device.map': No such file or directory
/proc/devices: No entry for device-mapper found (repeated many times)
Installation finished  No error reported
 
etc - few more lines on backup and unmounting

Hope you can still help, as I am getting to my wits end!
Thanks

---

### Post by adrian15 on 2010-10-31
> **Dumpy Dumpster said:**
> Thanks again adrian15,
I am trying to install direct to the CF drive - no other disc is present or connected when using the CF.

That make things easier.

> **Dumpy Dumpster said:**
> 
I have looked at Syslinux and it's use is well above my capabilities!

It is just the Fix Boot of Windows option of Super Grub1 Disk. It is very easy to use.

> **Dumpy Dumpster said:**
> 
Your idea to put the Grub onto its own partition seems the way - I was wondering if the Dell could 'see' the very first part of the OS partition where presumably the Grub files reside.

Well, there is another idea that might be better, given that your computer is old is to reserve a 200 MB size partition as the /boot partition when installing Lubuntu.

It would probably get recognised by your BIOS without too much trouble.

> **Dumpy Dumpster said:**
> 
  So I will try with Gparted, putting a unused partition or else just a blank partition or even the Linux-swap first and see if that helps.  From what I have found out, it seems to be a partition problem and allowing Lubuntu or Puppy to do partitioning for themselves does not seem to work out with this setup.

Try with the /boot partition instead.

> **Dumpy Dumpster said:**
> 
If the Grub needs its own partition, perhaps you could suggest what/where it should be.   At present I have the main partition (/dev/hda1 ext2 flagged bootable) and Linux-swap.
(/dev/hda2/2xRAM) only.
I have just placed an unallocated 500MB space in front of the /dev/hda1 partition - still no boot but the Grub error is now 17 not 2 as before.  Significant?
The grub partition is called /boot mount point and should be /dev/hda1.

adrian15

---

### Post by adrian15 on 2010-10-31
> **Dumpy Dumpster said:**
> 
Ran Rescatux - said sucess - looked in grub-install - no log.file.contents, but grub-install_log text reads: Have to copy this out.....

In Support menu there is a View Logs option that opens the log folder where you have found the file that you are copying.

> **Dumpy Dumpster said:**
> 
sudo unable to resolve host debian
sda1 sda2 sda5
Detected grub install partitions: sda1
a: TRUE sda1 ununtu-10.04-LTS-
sda1
DEBUG: detected hard discs: sda
sda
1
cp: cannot stat '/boot/grub/device.map': No such file or directory
/proc/devices: No entry for device-mapper found (repeated many times)
Installation finished  No error reported
 
etc - few more lines on backup and unmounting

I definitively need to improve the grub install log because I get a bit lost reading it.

What it is interesting is that /boot/grub/device.map is not found, maybe the grub2 packages is not installed at all? Yes, yes it is, because a /sbin/grub-install is found on your system so maybe grub2 is installed but not configured ok?

I need to put a meierfra's bootinfo equivalent script too in Rescatux.

> **Dumpy Dumpster said:**
> 
Hope you can still help, as I am getting to my wits end!
Thanks

Check my previous /boot piece of advice.

adrian15

---

### Post by Dumpy Dumpster on 2010-11-04
Thanks again adrian15 for your last suggestion.
I am getting more and more confused and still have the booting error.  None of this fiddling should be necessary.

Can we just go back to first principles - 

The CF card boots quite normally on another desktop, so there cannot be much wrong with that. The same errors occur with Puppy and Ubuntu installations.
Lubuntu 10.04 will not boot on the Dell, therefore the problem must lie with the Dell hardware.
Therefore it is either compatibility or a motherboard problem.
The  CF card seem to work so my thoughts now lie with a motherboard problem.  In other words, a CD drive can write to the CF card, but the board cannot read it back.  Is this possible?

I can get hold of another motherboard and can change it.  Either that or else fork out for a conventional hdd.

You have already done more than your fair share of helping me, but I would appreciate your advice further.  Thanks again.

---

### Post by adrian15 on 2010-11-05
I would try GRUB1 with the --force-lba option (or without it) when reinstalling GRUB in the CF to see if it improves anything.

The other option is to install grub into an ext3 partition and make a "Fix Boot of Windows" with SG1D so that Syslinux is installed in CF's mbr. (Run SG1D in the computer that only has CF and no other hard disk)

I think these are my last ideas.

adrian15

---

### Post by Dumpy Dumpster on 2010-11-06
Hi there again adrian 15,
What you suggest is really getting beyond my simple competence.  However I did manage the 'simplest' fix in [http://www.linux.com/community/forums?func=view&id=4219&catid=18](http://www.linux.com/community/forums?func=view&id=4219&catid=18).  It all seemed to work as expected and came back with 'No error found' at the end!  This coupled with the Rescatux disc which still gives a successful reinstallation of the Grub, leads me to suppose that there is something fundamentally wrong with this old lappy and that it is not the fault of the OS at all.
I would like to thank you again for all your patience and effort in trying to sort this one out for me.  It is a hallmark of this forum.
As the saying goes - 'Over and Out'!!

---

### Post by adrian15 on 2010-11-06
> **adrian15 said:**
> I would try GRUB1 with the --force-lba option (or without it) when reinstalling GRUB in the CF to see if it improves anything.


That actually means: Install Ubuntu 8.04 in the CF card (That might be complex because I do not know if Ubuntu 8.04 already had an official method for installing it into a USB device).

And then if it does not boot you should boot into a live, do a chroot, and inside it run the 
```

grub-install --force-lba /dev/sda 

```
command where I am assuming that your CF card is sda.

Actually you should do as advised as most Recover your grub installation howtos that involved a live cd and a chroot that were pre-Ubuntu 8.10 but the grub-install command should have the option: --force-lba in it.

> **adrian15 said:**
> 
The other option is to install grub into an ext3 partition and make a "Fix Boot of Windows" with SG1D so that Syslinux is installed in CF's mbr. (Run SG1D in the computer that only has CF and no other hard disk)

This options means that you install Ubuntu into CF card, and at Advanced step instead of choosing sdb (as your CF card boot device) you choose sdb1 supposing that your / partition is the first one of course.

After that you boot Super Grub1 Disk from a Cdrom and at the same time CF is inserted and after identifying it with 
```

Super Grub Disk & No Help
Boot & Tools
Show Partitions

```
you go to 
```

Super Grub Disk & No Help
Advanced
Windows
Fix Boot of Windows

```
and you select CF's hard disk.

If CF's ubuntu's / (root) partition is not the first one you should use Super Grub1 Disk again and 
```

Super Grub Disk & No Help
Boot & Tools
Activate partition

```
And choose the / partition where Linux is.

> **adrian15 said:**
> 
I think these are my last ideas.


I have another idea because you know some BIOSes offer USB boot but not in an standard way but in a USB-FDD way. The USB is supposed to be a floppy.

I think that the only software that can work like that is Super Grub2 Disk hybrid disk. So you get latest Super Grub2 Disk version and with dd you put it into the CF.

So from a live system you do:
Insert the CF card.
Detect which device it is with:
```

sudo fdisk -lu

```
or gparted.

Umount its probably mounted data partition with:
```

sudo umount /dev/sdb1

```
where sdb is the CF device.

And if Super Grub2 Disk image is found at tmp and it has been renamed to sgd2.img you can do:
```

sudo dd if=/tmp/sgd2.img of=/dev/sdb
sudo sync

```

And voila, perhaps, something might boot. If SG2D boots we will ask Jordan Uggla what to do next in order to put a normal Ubuntu in the same CF.

By the way that former dd command wipes all the CF contents.

If I were you the first thing I would try is to put Super Grub2 Disk in the CF and see if that boots in your old laptop system.

:guitar::guitar::guitar:

adrian15

---

### Post by Dumpy Dumpster on 2010-11-20
Finally got the Results.txt file out.  Here it is:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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

Disk /dev/sda: 8002 MB, 8002584576 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15630048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    14,844,059    14,843,997  83 Linux
/dev/sda2          14,844,060    15,615,179       771,120   5 Extended
/dev/sda5          14,844,123    15,615,179       771,057  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        ba868cc8-fc66-4caa-b1f9-1afb11f68325   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2f6cc81f-e57c-41e2-95f8-2b81760c0e67   swap                                     
/dev/sda: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

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
search --no-floppy --fs-uuid --set ba868cc8-fc66-4caa-b1f9-1afb11f68325
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
search --no-floppy --fs-uuid --set ba868cc8-fc66-4caa-b1f9-1afb11f68325
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba868cc8-fc66-4caa-b1f9-1afb11f68325
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba868cc8-fc66-4caa-b1f9-1afb11f68325 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba868cc8-fc66-4caa-b1f9-1afb11f68325
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ba868cc8-fc66-4caa-b1f9-1afb11f68325 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba868cc8-fc66-4caa-b1f9-1afb11f68325
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ba868cc8-fc66-4caa-b1f9-1afb11f68325
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2f6cc81f-e57c-41e2-95f8-2b81760c0e67 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
   3.3GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.32-21-generic
   3.3GB: boot/vmlinuz-2.6.32-21-generic
    .8GB: initrd.img
   3.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 


Going to try a complete reinstall of Grub now.

Just done that using the Chroot from drs305's excellent post (even I can follow it)
and the result is - wait for it - grub rescue again!!

---

### Post by Dumpy Dumpster on 2010-11-21
I am now trying to get a /boot/ partition seperate from the main partition for the Grub files.
Using Gparted, I have shrunk hda1 to allow a 500MB partition formatted to Ext3 in front of it.  This is now hda3.
How do I rename the partitons to get them with hda1 'at the front' for Grub?  How do I copy over the Grub to this new partition?
I am finding all this VERY confusing so please keep explanations simple!

---

### Post by adrian15 on 2010-11-21
> **Dumpy Dumpster said:**
> I am now trying to get a /boot/ partition seperate from the main partition for the Grub files.
Using Gparted, I have shrunk hda1 to allow a 500MB partition formatted to Ext3 in front of it.  This is now hda3.
How do I rename the partitons to get them with hda1 'at the front' for Grub?

I do not know.
> 
  How do I copy over the Grub to this new partition?
I am finding all this VERY confusing so please keep explanations simple!

The simple thing is to reinstall Ubuntu and set up a /boot partition (with custom partition) and grub2 will be installed there.

The not so simple thing is from your running system (that means either booting into your system with Super Grub2 Disk or getting into from a chroot, making sure you mount bind dev, proc and tmp) something like this:
```

mkdir /mnt/boot_partition
mount -t ext3 /dev/hda3 /mnt/boot_partition
cp -a /boot/* /mnt/boot_partition
umount /mnt/boot_partition
sync

```

And add this line to your /etc/fstab file, just below the (/) line, the one that makes reference to hda1.

You just edit with:
```

gksudo gedit /etc/fstab

```
and the line is:
```

/dev/sda2 <TAB> /boot <TAB> ext3 defaults 0

```

Where <TAB> means you to press the tab key instead of using spaces.

And optionally if you want to save some space, and **before rebooting not after** you can do:
```

rm -rf /boot/*

```

Now you can do:
```

mount -a

```

If 
```

mount 

```
shows you that your /boot partition has been mounted ok.
You should be able to run:
```

grub-install /dev/sda

```
that eventually will take care of your /boot partition.

If you have any doubt just ask it.

adrian15

---

### Post by Dumpy Dumpster on 2010-11-22
Good afternoon adrian 15
Reinstalled using advanced partitioning as follows:
hda1     ext2    /boot     353MB   Flagged boot
hda2     ext2    /         6.57GB
had3     linux-swap        541 MB

After rebooting it was back to Grub Rescue again!

ls found hd0 hd0,3 hd0,2 hd0,1 fd0
ls (hd--) all produced unknown file system except hd0,1 which gave another rescue prompt.  But ls (hd0,1)/boot returned 'file not found'

Another BoofInfoScript to follow -

---

### Post by Dumpy Dumpster on 2010-11-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 98955 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8002 MB, 8002584576 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15630048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       722,924       722,862  83 Linux
/dev/sda2             722,925    14,506,694    13,783,770  83 Linux
/dev/sda3          14,506,695    15,615,179     1,108,485  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        f258c8e3-9525-4eeb-a91b-d7f990a996be   ext2       /boot                         
/dev/sda2        a46b5e1c-877e-42d7-8766-b90d2cf64d71   ext2                                     
/dev/sda3        f8765e7c-1c29-4419-995d-ee35564a994f   swap                                     
/dev/sda: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set a46b5e1c-877e-42d7-8766-b90d2cf64d71
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
search --no-floppy --fs-uuid --set f258c8e3-9525-4eeb-a91b-d7f990a996be
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f258c8e3-9525-4eeb-a91b-d7f990a996be
	linux	/vmlinuz-2.6.32-21-generic root=UUID=a46b5e1c-877e-42d7-8766-b90d2cf64d71 ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f258c8e3-9525-4eeb-a91b-d7f990a996be
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=a46b5e1c-877e-42d7-8766-b90d2cf64d71 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f258c8e3-9525-4eeb-a91b-d7f990a996be
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f258c8e3-9525-4eeb-a91b-d7f990a996be
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-21-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a46b5e1c-877e-42d7-8766-b90d2cf64d71 /               ext2    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f258c8e3-9525-4eeb-a91b-d7f990a996be /boot           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=f8765e7c-1c29-4419-995d-ee35564a994f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 

```

_For others seeking a solution to the Dell L400 Boot problem_
I have solved this by changing the HDD from a CF card to a conventional drive.
It seems that there is a compatibility problem with this machine and CF drives.
I now have Lubuntu 10.04 installed and running well - just a wireless card to sort out......!

---

