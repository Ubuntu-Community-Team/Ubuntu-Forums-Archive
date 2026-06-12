---
title: "Grub error unknown filesystem"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Euroswoop on 2009-12-17
My computer froze so I shut it down. When it rebooted i get 
Grub loading
error unknown filesystem
grub rescue

ive been looking for solutions last night. I tried the one from 
[http://help.ubuntu.com/community/Grub2#reinstallingfromLiveCD](http://help.ubuntu.com/community/Grub2#reinstallingfromLiveCD)

I can't get my hd with ubuntu 9.10 to mount.
i type in sudo fdisk -l and this is what i get
ubuntu@ubuntu:~$ sudo fdisk -l

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e608acb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29275   235151406   83  Linux
/dev/sda2           29276       30401     9044595    5  Extended
/dev/sda5           29276       30401     9044563+  82  Linux swap / Solaris
```when i type in sudo blkid it give me this
```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="9075a94f-f190-4dba-a453-abb090e696db" TYPE="ext4" 
/dev/sda5: UUID="6f722961-888c-4680-ad30-73c4e124cb99" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

```when i try and mount this is what it gives me
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount/dev/sda1/mnt
sudo: mount/dev/sda1/mnt: command not found

```im out of ideas. i hope someone can help me out on this.

---

### Post by darkod on 2009-12-17
You are typing /dev/sda1/mnt together, at least here. It needs space in between, you are mounting /dev/sda1 to /mnt:
sudo mount /dev/sda1 /mnt

Also, if you experienced forced shutdown you might try fsck, a command to check the filesystem. It's even better to be run from LiveCD, LiveUSB. Root must NOT be mounted to do fsck. I haven't used the command myself, just saw it mentioned, you can google it for instructions to use.

---

### Post by Euroswoop on 2009-12-17
Ok i typed it the right way now and i get this
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

i tried using fsck but no luck. i think i might be typing the code wrong. sorry im kinda new to ubuntu.:-(
```
ubuntu@ubuntu:~$ fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root

```

---

### Post by darkod on 2009-12-17
If it says you have to be root, add 'sudo' in front of the command. But if /dev/sda1 is still mounted, unmount first.
sudo umount /mnt
sudo fsck /dev/sda1

PS. Sorry, it didn't even mount, you said there was error. Just try the fsck command.

---

### Post by Euroswoop on 2009-12-17
omfg that worked!!! Thank you so much!!!! that was so simple and easier than replacing the grub. thank you once again!:D

---

### Post by darkod on 2009-12-17
No problem. We all learn here. Glad it got sorted. :)

---

### Post by VulcanTourist on 2010-01-07
This solution, if it actually is one, is not understandable by anyone not already well versed in command-line Linux.  Tonight I tried to reinstall Kubuntu on a system that has had several different distros successfully installed on it before, including Ubuntu 9.10 and openSUSE 11.2, and I got this exact same error response described in the first post, when I first tried to boot Kubuntu after installing it.

I have no idea what happened, nor why, and this thread has not helped me understand it at all.  Would someone care to try again, in a more generalized fashion that doesn't read like some inside joke?

There are some particulars to my setup that might be worth noting:
- it is a dual-boot scenario, with Windows XP 32-bit in a second primary partition, and Kubuntu targeted to a new partition in empty space preceding it.
- I use a boot MANAGER (not LOADER) called BootIt NG; because of that, I did NOT want grub/grub2 to be installed in the MBR, because BootIt NG manages the MBR interactively.  As a consequence of that I instructed the installer to place grub in the Kubuntu root volume instead.

During installation, the root volume was designated by /dev/sda2, and that is presumably where grub got installed.  HOWEVER, in my subsequent attempts to understand what went wrong, it appears that /dev/sda2 has somehow magically become /dev/sda1!  Whe I booted with the live CD, that is how it designated the root volume where it had been installed.

Is that why I'm getting this error message from circumstances completely different than those in the original post?  I have tried to reinstall/reactivate grub where it belongs, using both "grub rescue" and by booting back into the live CD, but I can't figure out how to correct it (in part because there's such a wealth of old/obsolete/unclear information available in forums and blogs).  It was easy enough to verify with the live CD that all the Kubuntu files are there, in what the live CD at least identifies as /dev/sda1.

So what's the problem here?  Has the partition order somehow gotten confused, and so grub is trying to load itself from sda2 when in fact sda2 (now) doesn't contain Linux much less grub?  The partition order might have been virtually altered by BootIt NG, because it has that ability to reorder the appearance of partitions in the MBR (and even exclude them), but to my knowledge I didn't do that in this case.

How can I get grub (re)installed to the Kubuntu 9.10 partition, such that I can use BootIt to jumpstart grub and Linux from there?

---

### Post by meierfra. on 2010-01-07
VulcanTourist:  We need  more information. Please follow these [instruction]("http://ubuntuforums.org/showthread.php?t=1291280") and post the RESULTS.txt.

---

### Post by VulcanTourist on 2010-01-07
All I needed to know was how to reinstall grub to a specific location; I guess I wasn't specific enough, or perhaps too verbose.  Why isn't there a GUI for that?  Why isn't the ability to easily reinstall grub from a menu item a standard feature of every live CD?  If the installer itself can automate that, why isn't that exposed as a separate feature of the live CD?  It would have saved me something like an hour and a half.

Lacking those specific instructions, I simply brute-forced it by reinstalling Kubuntu all over again, and once again using the Advanced button to force it to be installed in the root partition.  That solved it, as I guessed it would.

I also know how it happened: the ordering of the partitions changed between when I installed it and when I first tried to boot it.  When I installed Kubuntu the first time, I was a bit lazy with BootIt and didn't pre-create the target partitions within BootIt and then create a boot menu item for the new install and "boot" to it - to "lock in" that particular partition scheme in the MBR - before booting from the CD.  It's important to use BootIt to pre-create the partition(s) and then specify their use/ordering in a new boot menu item, because if the partitions don't yet exist and the OS installer creates them, then the partition ordering may change relative to what is defined in the boot menu for it.

Instead I simply rebooted directly from Windows XP to the Kubuntu CD, which left the BootIt partition scheme for Windows XP in the MBR.  After installing Kubuntu I created a new BootIt menu item for it, but in doing so I inadvertently altered the partition scheme and effectively guaranteed that grub wouldn't be able to find itself, because it wasn't looking on the partition where the grub stub loaded from, it was looking for itself on a particular ORDINAL partition... but that ordinal had now changed.

It was effectively the same as what happens when partitions are reordered underneath NTLDR for Windows, and what's in boot.ini no longer jives with reality.  I know well how to fix that scenario, but had no idea what the equivalent procedure is for Linux/grub even though I knew the issue was the same.

Since I had already created a BootIt menu item for Kubuntu and defined the partition order for it at the time of the second install, and also tried to boot from it, that established the new partition order for that menu item and so when grub was configured by the installer the root partition ordinal was correct that time.  That's the recommended procedure, and I didn't follow it this time.  I now remember more clearly WHY it's the recommended procedure.

By the way, I happened to find yet another forum post describing this exact same error, and do you know what advice the poor fool was given?  He was eventually told to try swapping disks!  Of course that worked for him, and everybody waltzed away believing there must have been something physically wrong with the original drive.  No one ever corrected or questioned the bad advice.  That incident demonstrates why forum discussions are a lousy means of disseminating wisdom. :|

---

### Post by meierfra. on 2010-01-07
Since you installed Grub to the boot sector rather than to the MBR, you might run into the "rescue" prompt problem again. So just for future reference:

To reinstall Grub if you cannot boot into Kubuntu,  boot from the Kubuntu live CD, open  a terminal (Applications ->System->Terminal) and type

```
sudo mount /dev/sda1  /mnt 
sudo grub-install --recheck -f --root-directory=/mnt /dev/sda1
```

(the first command mounts your Kubuntu partition so you can access it from the Live CD. The second command reinstalls grub.)

This assume that Kubuntu is on "/dev/sda1". If not replace "/dev/sda1"  by the correct partition for Kubuntu.



It is also possible to install Grub so that it boots even if you change the Partition Table via BootIt NG:

Open a terminal in Kubuntu (not in the LiveCD)

```
kdesudo kwrite /boot/grub/device.map
```

Add the  line:

```
(hd1) /dev/sda
```

(This assumes that you have only one hard drive, if you have two, use "(hd2)  /dev/sda" and so on.)
Save the file.

Then 

```
sudo grub-install -f '(hd1,1)'
```

(if you have two hard drives , use '(hd2,1)'.  If Kubuntu is on /dev/sda2 use '(hd1,2)' ....)


Could you do me a favor and run the boot info script and post the RESULTS.txt  (see my last post)? You are only the second person I know who uses BootIT NG. The boot info script is able the read the BootIt NG partition table, but this feature has not been tested very much.  So I would really like to see, how well it performs on our computer. 
Thanks

---

### Post by gbrunati on 2011-08-02
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 427758392 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 NTFS / exFAT / HPFS
/dev/sda2          71,682,046   976,771,071   905,089,026   5 Extended
/dev/sda5          71,682,048    81,446,911     9,764,864  82 Linux swap / Solaris
/dev/sda6          81,448,960   976,771,071   895,322,112  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2404586F04584648                       ntfs       
/dev/sda5        89b27014-15f4-4b27-9bff-048d364bb6e7   swap       
/dev/sda6        0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3
	linux	/boot/vmlinuz-2.6.35-30-generic-pae root=UUID=0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3
	echo	'Loading Linux 2.6.35-30-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-30-generic-pae root=UUID=0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2404586F04584648
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=0ccd8dd9-90bf-4f6f-8a6e-3b9906156ca3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=89b27014-15f4-4b27-9bff-048d364bb6e7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 214.979099274 = 230.832050176  boot/grub/core.img                             1
 214.990242004 = 230.844014592  boot/grub/grub.cfg                             1
 371.099304199 = 398.464843776  boot/initrd.img-2.6.35-30-generic-pae          2
 214.973899841 = 230.826467328  boot/vmlinuz-2.6.35-30-generic-pae             1
 371.099304199 = 398.464843776  initrd.img                                     2
 214.973899841 = 230.826467328  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by jithinjk on 2011-10-04
*I* had windows 7 and Kubuntu installed on my lap previously. Now I have removed the partition containing Kubuntu.After this when I boot my lap I get the error message as shown 

error : unknown filesystem
grub-rescue

which is same error as what for this thread as begun.

what should I do to get back and load Windows and Ubuntu.

---

### Post by irpsit on 2012-03-01
Please do the following:

First type 
grub rescue>ls

You will see your partitions, for example I have a partition (hd0,msdos2) and another (hd0,msdos3) 

Then, type
grub rescue>ls (hd0,msdos2) 

Replacing (hd0,msdos2) with whatever you see listed

And do the same for all other partitions
If you find a partition where do you see linux filesystem, then do the following. I find my case to be (hd0,msdos3) 

So, do this:
grub rescue>set

You will see this:
prefix=(whatever,whatever)/boot
root=whatever,whatever
In my case one whatever is (hd0,msdos2), so it is incorrect, because it is now msdos3

If those aren't correct use the set command to change them:

grub rescue>set prefix=(hd0,msdos3)/boot
grub resuce>set root=hd0,msdos3

Replacing hd0,msdos3 with your partition containing linux, that you see listed with the ls command

At that point you can load the "normal" module and resume booting. Do the following commands:

grub rescue>insmod normal
grub rescue>normal

You should be able at least to start windows or linux to fix the problem. I am still working on that, but at least I went forward from the grub command line.

---

