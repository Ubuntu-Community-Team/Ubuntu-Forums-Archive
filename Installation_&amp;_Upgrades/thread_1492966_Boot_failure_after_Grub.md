---
title: "Boot failure after Grub"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by rijidij on 2010-05-25
Hello all,

Sorry if this has already been covered. I did a search, but couldn't find anything on this particular problem.

I have a triple boot system running Ubuntu, WinXP, and Win7.

I had Ubuntu running fine on its own partition (sda1) but an upgrade from Karmic to Lucid turned it into a dog.
So I tar-ed my /home filesystem, split sda1 into 2 new extended partitions, then did a clean install of Lucid with / on sda5, and /home on sda6.

Here is my partition table: ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46274626

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24859   199679855+   5  Extended
/dev/sda2           24860       35255    83505870    7  HPFS/NTFS
/dev/sda3           35256       60114   199679917+   7  HPFS/NTFS
/dev/sda4           60115       60801     5518327+  82  Linux swap / Solaris
/dev/sda5               1        2611    20972794+  83  Linux
/dev/sda6            2612       24859   178707028+  83  Linux
```

Everything was working nicely until yesterday when suddenly it would no longer boot into any OS.
It gets to the Grub menu, but after that, just a blank screen (until the monitor tells me it has lost signal).

Here is the output from bootinfoscript: ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /IO.SYS /MSDOS.SYS

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *            124   399,359,834   399,359,711   5 Extended
/dev/sda5                 126    41,945,714    41,945,589  83 Linux
/dev/sda6          41,945,778   399,359,834   357,414,057  83 Linux
/dev/sda2         399,359,835   566,371,574   167,011,740   7 HPFS/NTFS
/dev/sda3         566,371,575   965,731,409   399,359,835   7 HPFS/NTFS
/dev/sda4         965,731,410   976,768,064    11,036,655  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4206 MB, 4206886912 bytes
128 heads, 63 sectors/track, 1018 cylinders, total 8216576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     8,209,151     8,209,089   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       0743a043-1328-4f89-954c-dd19b18fe02a   ext3                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        465C0C6D5C0C5A57                       ntfs       XP                            
/dev/sda3        6A9E31D642946B90                       ntfs       Win7                          
/dev/sda4        7e218566-a186-4068-b01f-436b642767d6   swap       swap                          
/dev/sda5        baf6c0a7-d45e-4aa8-8176-26e82f54b3ba   ext4       /                             
/dev/sda6        eb35fb4f-1d2c-473e-888b-2681e88b8bbd   ext4       /home                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3023-F7DB                              vfat       Attache                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set baf6c0a7-d45e-4aa8-8176-26e82f54b3ba
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  set gfxpayload=keep
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set baf6c0a7-d45e-4aa8-8176-26e82f54b3ba
insmod png
if background_image /usr/share/images/grub/BootSplash.png ; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set baf6c0a7-d45e-4aa8-8176-26e82f54b3ba
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=baf6c0a7-d45e-4aa8-8176-26e82f54b3ba ro  vga=775  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 465c0c6d5c0c5a57
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 6a9e31d642946b90
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=baf6c0a7-d45e-4aa8-8176-26e82f54b3ba /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=eb35fb4f-1d2c-473e-888b-2681e88b8bbd /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=7e218566-a186-4068-b01f-436b642767d6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-22-generic
  17.3GB: boot/vmlinuz-2.6.32-22-generic
  17.3GB: initrd.img
  17.3GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin /usepmtimer
```

I have no doubt that I've screwed up something, but no idea what. :(
Can any of you lovely people in Ubuntuland help? Please...

TIA
Craig


P.S.
I should also mention that I have already tried re-installing Grub from a live USB to no avail.
BootInfoScript was also run from here.

---

### Post by ronparent on 2010-05-25
Since everything was running fine for a while (you didn't say how long) you may have had a hardware failure that corupted your file system. You may try a filesystem check on all your partitions from the live CD. 

Or a subsequent automatic update may not be allowing the graphics output to function properly. Try edditing the grub bootline and adding **nomodeset** to the kernel bootline?  Also try booting the recovery mode and selecting **dpkg** from the menu.

Keep posting your questions here for more suggestions. It may be a matter of systematically troubleshooting your sustem.

---

### Post by wilee-nilee on 2010-05-25
If you put a live cd in does it boot and run like normal? Did you make a new entry to fstab?

---

### Post by rijidij on 2010-05-25
> **wilee-nilee said:**
> If you put a live cd in does it boot and run like normal? Did you make a new entry to fstab?

Yes, it boots from a live CD or USB.
I haven't changed fstab. It was working fine, for about a week, until yesterday.

Thanks anyway.

---

### Post by kansasnoob on 2010-05-25
Well, it's unusual to see a drive start with an extended partition but I'll review some stuff:

/dev/sda1 is about a 200GB Extended partition and it contains sda5 and sda6

/dev/sda5 is about a 20GB Lucid Root "/" logical partition

/dev/sda6 is about a 180GB Lucid /home logical partition

/dev/sda2 is about an 80GB Win XP primary partition

/dev/sda3 is about a 200GB Win 7 primary partition

/dev/sda4 is about a 5GB SWAP primary partition

Is that all correct?

I'm not sure what kind of problems having a drive begin with an extended partition might cause but we can try a few things. First of all you have a boot flag set on the extended partition:

```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    **[COLOR="Red"]*[/COLOR]**            124   399,359,834   399,359,711   5 Extended
/dev/sda5                 126    41,945,714    41,945,589  83 Linux
/dev/sda6          41,945,778   399,359,834   357,414,057  83 Linux
/dev/sda2         399,359,835   566,371,574   167,011,740   7 HPFS/NTFS
/dev/sda3         566,371,575   965,731,409   399,359,835   7 HPFS/NTFS
/dev/sda4         965,731,410   976,768,064    11,036,655  82 Linux swap / Solaris
```

That's wrong. You should have a boot flag set on each of the Windows partitions (sda2 and sda3), and nothing else! You can do that using Gparted from the Live USB:

[ATTACH]158239[/ATTACH]

You notice in that screenshot the far right column shows "Flags"? If you right click on a partition you can then select to "manage flags". So remove the boot flag on sda1 and add a boot flag to both sda2 and sda3.

Then I'd still reinstall and update grub in a chroot like this (please copy-n-paste):

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
sudo apt-get install --reinstall grub-pc
```

```
sudo grub-install /dev/sda
```

```
sudo update-grub
```

Wait for that to say "done" then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

If that results in any errors I'd like to see the full terminal output.

---

### Post by rijidij on 2010-05-25
Thanks kansasnoob,
sda1 was originally a large primary partition, but after having a lot of problems with the last upgrade, I decided to put /home on a separate partition and do (mostly) clean installs in future.
As I said, it was working fine for about a week, but I must have done something recently, or there has been an upgrade that screwed things up.

I have tried your suggestions, but no luck so far. :(
Gparted would only let me set one boot flag at a time, so I set sda2 and sda3 using fdisk.
The grub reinstall and update went without incident.
Except for a few "sudo: unable to resolve host ubuntu" messages because I had already chroot-ed. But I don't think that's anything to worry about.

So, it's back to the drawing board...

Thanks anyway.

---

### Post by rijidij on 2010-05-26
The good news is; I have had a *small* success since yesterday.
I found an obscure reference to ARC partition numbering which says:> The first logical drive in an extended partition will always be partition 2. Numbering will continue through the remaining logical drives of the extended partition until all logical drives are numbered. Then the remaining primary partitions will be numbered starting with the next number after the last logical drive in the extended partition.
Because I have an extended partition as my 1st partition, I changed the partition number in my XP [FONT="Courier New"]boot.ini[/FONT] file to (1) and, lo and behold, it worked!
I now had access to my _least_ favourite operating system.

Next, I added an entry for Win7 to [FONT="Courier New"]boot.ini[/FONT]
When I choose XP from the Grub menu, I am now presented with a bootloader menu, which includes Windows 7.
If I select Win7 from here, it loads OK, but still not directly from the Grub menu. :confused:

This suggests to me that Grub's menu entries are not pointing at the right places.


Any ideas?... Anyone?

---

### Post by rijidij on 2010-06-02
UPDATE:

After much wailing, gnashing of teeth, and rending of hair (which I can ill afford to lose), I finally gave in and, with the help of clonezilla, rearranged my disk with XP as the first primary partition.
I also have a Win7 primary partition. And an extended partition containing a GRUB partition, Lucid (/ and /home), and plenty of space for other experiments.
In this case, Win7 appears to be the root of all evil. :evil:
Even after I moved XP to the first partition it was showing up as drive D: and screwing up my Windoze software and drivers.
I tried changing the drive letters in the registry (sorry, getting a bit off-linux-topic here), but that was a total disaster. Luckily I still had my clonezilla backup...
After a few more false starts and backup restores, I finally had to delete the Win7 partition then do an in-place upgrade to get XP set up on the C: drive.

Whew!

Not an entirely satisfactory outcome, but all's well that ends well.
Thanks to everyone who tried to help.

---

