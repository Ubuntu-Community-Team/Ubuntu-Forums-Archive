---
title: "Error: no such device, grub rescue"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Axman10 on 2011-03-29
I just installed Ubuntu on a separate hard drive alongside Vista, and after restarting, my computer booted to a screen that said, "error: no such device: xxxxx-xxxx-xxxxx-xxxx (I don't remember exact number, if I need them I'll go back and write em down) grub rescue>"

After a bit of searching I found this thread: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  I tried the first part twice which didn't change anything, so I tried the last part which was too fix the vista bootloader, which worked perfectly, and now I can get into at least one operating system.  Would anyone please help me get a bootloader working so I can choose between Ubuntu and Vista?

Also, is it worth mentioning that right before the computer shut down after installation, I had a huge list of I/O errors?

EDIT: After further searching I read that the I/O errors were commonly because of a faulty cd or it was spinning too fast. I think my problem with that was that it was spinning too fast, it was incredible loud and there was a huge amount of wind coming out of my computer XD. iirc I have to go to the BIOS to change disc speed?

EDIT2: I think all my problems stem from a faulty CD. I remember setting the burning speed too the highest setting when I burnt the live CD, I guess I thought faster was better.

---

### Post by Dutch70 on 2011-03-29
The cd should always be burnt at the slowest speed possible. 

Please post your boot info script

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]
Then open a terminal (Cntrl+Alt+T) and run the following command...

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just highlight the info and click the # symbol in the toolbar.

---

### Post by Rubi1200 on 2011-03-29
+1 to the boot script suggested by Dutch70.

It is essential we see the results to help you troubleshoot and fix the issue.

---

### Post by Axman10 on 2011-03-29
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304   625,139,711   625,041,408   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdf2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdf5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D7-0907                              vfat       DellUtility                   
/dev/sda2        8A96C99396C98065                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5   ext4                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        c7b0ebae-15d7-40a6-8f48-d66be8827910   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdf1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 07d7-0907
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8a96c99396c98065
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

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf1 during installation
UUID=dd0ee3eb-47bc-42b6-81d4-9b7f2b5d47f5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
UUID=c7b0ebae-15d7-40a6-8f48-d66be8827910 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdf1: Location of files loaded by Grub: ===================


 103.2GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
  47.8GB: boot/initrd.img-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-22-generic
  47.8GB: initrd.img
    .2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

Thanks for the responses. Since I am extremly impatient, I managed to restore my hardrive with Vista on it and format my drive that had Ubuntu on it so I could try again. I burned a new CD from a newly downloaded .iso on the lowest speed but I ended up with the same results, so I am back at the same place.

All your help is appreciated, I'm probably just going to try and wait for a response this time, I don't want to mess things up to badly XD

---

### Post by Dutch70 on 2011-03-29
Hi Axman, 
It looks like you don't have Grub2 installed, but I've got a couple questions about this one myself, so I've asked a friend to take a look at it.

---

### Post by Hedgehog1 on 2011-03-29
***The Hedgehogs have arrived***..... Well, one, anyway.

Can we Begin by asking you to create a LiveUSB to bypass any issues with burning and reading the LiveCD?

Also - are you installing Ubuntu on an external Drive?

If the second drive is not external, do you have a mix of an IDE hard drive and a SATA hard drive?  Is the second drive (if internal) plugged into an add-on card?

Thanks,

***The Hedge***

:KS

***p.s. Is the script file you posted from the 'before' or 'after' then second install? If it's not the 'after', can you please refresh it?***

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> ***The Hedgehogs have arrived***..... Well, one, anyway.

Can we Begin by asking you to create a LiveUSB to bypass any issues with burning and reading the LiveCD?

Also - are you installing Ubuntu on an external Drive?

If the second drive is not external, do you have a mix of an IDE hard drive and a SATA hard drive?  Is the second drive (if internal) plugged into an add-on card?

Thanks,

***The Hedge***

:KS

***p.s. Is the script file you posted from the 'before' or 'after' then second install? If it's not the 'after', can you please refresh it?***

Alright! 

1 - Can do.

2 - No, it is an Internal Drive.

3 - I'm quite sure that they are both SATA Drives, (I've seen it in several places on my computer) and although I don't know what an add-on card is, I don't think it is. It's plugged in the exact same way as the original hard drive that this computer came with.

4 - The script I ran is from the second, most recent install.

I'm going to hop over to Windows to set up a LiveUSB, or can on do it right here from this Ubuntu test?

---

### Post by Hedgehog1 on 2011-03-30
Go hop into windows.... That will give me time to write up your next steps...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
We are going to have you setup your partitions manually, and be in complete control of your install.

The picture below are for a dual boot with 1 drive.  You have a dual boot with 2 drives, so you will have to translate the partition names a bit

In gparted, create 3 partitions on your second 'Ubuntu' drive:

1) sdf1: ext4 '/' - about 10 gigs
2) sdf2: Linux swap - the size of your RAM + 10%
3) sdf3: ext4 '/home' - the rest of the disk

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

Remeber, you need to translate the sda5=sdf1, sda6=sdf2 & sda7=sdf3. Now you will 'map' the three partitions on /dev/sdb.

First, make /dev/sdf1 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Axman10 on 2011-03-30
I just found this handy little utility in the System/Administration Menu for creating StartUp Discs :D I'll stay here and beat my time on Mines while I wait.

Thanks for the help.

EDIT: I found GParted! Sorry, would you give me a quick lesson on how to do the first step, the only avaliable buttons are Unmount and Manage Flags and I don't know what either mean :(

---

### Post by Hedgehog1 on 2011-03-30
**Remember, you need to translate the sda5=sdf1, sda6=sdf2 & sda7=sdf3.** 

The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Yeah - I know you are installing Ubuntu on the second drive, but the Grub (**GR**and **U**nified **B**oot loader) ***has to boot from the same drive as windows does***, so it can then offer Windows or Ubuntu as you select.

[SIZE="4"]**Install the Boot Loader on /dev/sda (NOT sda1 or sda2 - but _sda_)**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
I edited my last post, but in case you didn't see that I'll post it here. I don't know how to do the first step, there are only a few avaliable options, and I don't know what they mean, "Unmount, Manage Flags, Partition Table". Would you be able to go into more depth on the first step?

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> I just found this handy little utility in the System/Administration Menu for creating StartUp Discs :D I'll stay here and beat my time on Mines while I wait.

Thanks for the help.

EDIT: I found GParted! Sorry, would you give me a quick lesson on how to do the first step, the only avaliable buttons are Unmount and Manage Flags and I don't know what either mean :(

Goodness but you are a lot of trouble! :D

First lets clean the /dev/sdf disk:

[IMG]http://img834.imageshack.us/img834/8480/gpartedpartitiontable.png[/IMG]

In the upper right hand corner - select the drive that you will reinstall Ubuntu on.  PLEASE SELECT THE CORRECT DRIVE!

Then follow the menu options you see displayed.

---

### Post by Hedgehog1 on 2011-03-30
Next we will create the partitions we need:

Right click on the 'unallocated space to get the menu, choose create:

[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]

[SIZE="3"]This picture shows the creation of a *logical* partition - your are creating only ***primary*** partitions today - please select your option accordingly.[/SIZE]

---

### Post by Hedgehog1 on 2011-03-30
Then create a Linux-swap partition:

[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]

And your third partition for you '/home', repeating the steps of you did for the first 'ext4' partition.

The you will be ready to install Ubuntu following the earlier posts.

[SIZE="3"][B]Remember:

1) Install from the LiveUSB
2) Install the Boot Loader on /dev/sda[/B][/SIZE]



***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
Wow, I am quite a bit of trouble :P

I got an error when attempting to apply the changes I made:

[SIZE=2]GParted 0.6.2[/SIZE]
 [SIZE=2]Libparted 2.3[/SIZE]
    [SIZE=2]**Create Primary Partition #1 (ext4, 9.77 GiB) on /dev/sdf**  00:00:01    ( ERROR ) [/SIZE]       [SIZE=2] create empty partition  00:00:01    ( ERROR ) [/SIZE]     [SIZE=2] libparted messages    ( INFO ) [/SIZE]        [SIZE=2]*Partition(s) 1, 5 on /dev/sdf have been written, but we have been  unable to inform the kernel of the change, probably because it/they are  in use.  As a result, the old partition(s) will remain in use.  You  should reboot now before making further changes.*[/SIZE]          [SIZE=2]========================================[/SIZE]
    [SIZE=2]**Create Primary Partition #2 (linux-swap, 2.15 GiB) on /dev/sdf**[/SIZE]    [SIZE=2]========================================[/SIZE]
    [SIZE=2]**Create Primary Partition #3 (ext4, 99.88 GiB) on /dev/sdf**[/SIZE]    [SIZE=2]========================================

EDIT: I also had an Error while creating Partition Table, but it continued on.
[/SIZE]

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> Wow, I am quite a bit of trouble :P

I got an error when attempting to apply the changes I made:

[SIZE=2]GParted 0.6.2[/SIZE]
 [SIZE=2]Libparted 2.3[/SIZE]
    [SIZE=2]**Create Primary Partition #1 (ext4, 9.77 GiB) on /dev/sdf**  00:00:01    ( ERROR ) [/SIZE]       [SIZE=2] create empty partition  00:00:01    ( ERROR ) [/SIZE]     [SIZE=2] libparted messages    ( INFO ) [/SIZE]        [SIZE=2]*Partition(s) 1, 5 on /dev/sdf have been written, but we have been  unable to inform the kernel of the change, probably because it/they are  in use.  As a result, the old partition(s) will remain in use.  You  should reboot now before making further changes.*[/SIZE]          [SIZE=2]========================================[/SIZE]
    [SIZE=2]**Create Primary Partition #2 (linux-swap, 2.15 GiB) on /dev/sdf**[/SIZE]    [SIZE=2]========================================[/SIZE]
    [SIZE=2]**Create Primary Partition #3 (ext4, 99.88 GiB) on /dev/sdf**[/SIZE]    [SIZE=2]========================================

EDIT: I also had an Error while creating Partition Table, but it continued on.
[/SIZE]

I think this happened because the LiveCD/USB uses the swap that was already on the hard drive.

You can reboot to the LiveUSB and begin the install.

**You can still read and post to the forum as you go; Just select 'TRY' first and then click the 'Install' icon on the desktop, Firefox will work that way during the install...**

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> I think this happened because the LiveCD/USB uses the swap that was already on the hard drive.

You can reboot to the LiveUSB and begin the install.

You can still read and post to the forum as you go; select 'TRY' first and then click the 'Install' icon on the desktop...

***The Hedge***

:KS
Ok, I'll post back here in a bit if I have success, or fail once again XD. Thanks alot.

---

### Post by Hedgehog1 on 2011-03-30
We will be here...

Did I already mention mention that you should:

**[SIZE="4"]Install the Boot Loader on /dev/sda[/SIZE]**

I think I did... Can't remember for sure... :D

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
Axman10 - it's been 16 minutes...  Hoping your doing ok....

***The Hedge***

:KS

p.s. Anyone seen Dutch70?  I think he was helping before I 'swooped' in...

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> Axman10 - it's been 16 minutes...  Hoping your doing ok....

***The Hedge***

:KS

p.s. Anyone seen Dutch70?  I think he was helping before I 'swooped' in...

Alright here's an update. I tried to boot from the USB and it got stuck at the copyright (copyright?) right at the beginning. I figured the USB wasn't working properly, so I went into windows and made a LiveUSB again, and decided to format the Ubuntu drive as we are doing a clean installation. Booted from the USB nice a smoothly, and I just set up the partitions without any errors and Im going onto the Installation.

PS. When I formatted the drive it changed to sdg, I don't think it makes a difference though, if I have to at any point I will replace sdf with sdg.

---

### Post by Dutch70 on 2011-03-30
I'm checkin in from time to time, looks like you've got it covered.

---

### Post by Axman10 on 2011-03-30
Ok, followed the original guide word for word and I am installing, I'm feeling good about this now. Thanks alot for all your help.

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> PS. When I formatted the drive it changed to sdg, I don't think it makes a difference though, if I have to at any point I will replace sdf with sdg.

It looks like each disk format/install attempt is going to the next letter (sd**f** to sd**g**).

Very weird, that...  I had expected the 2nd hard drive to be /dev/sd**b**, so this has been happening a while to get to these letters...

***The 'pondering' Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> Ok, followed the original guide word for word and I am installing, I'm feeling good about this now. Thanks alot for all your help.

Already marked it solved and everything!  That is confidence.

We will keep an eye on  this thread just in case you need us again.

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> It looks like each disk format/install attempt is going to the next letter (sd**f** to sd**g**).

Very weird, that...  I had expected the 2nd hard drive to be /dev/sd**b**, so this has been happening a while to get to these letters...

***The 'pondering' Hedge***

:KS


Hehe, a couple of weeks ago I tried this a few times, although it was from a LiveUSB, and they all worked, and it was me that screwed it up... I have a habit a messing with things when I don't know how they work, I got into several situations where the only thing I could manage to do was reinstall Windows and do some restoring and formatting.

I format entirely too often, is that a bad thing?

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> Hehe, a couple of weeks ago I tried this a few times, although it was from a LiveUSB, and they all worked, and it was me that screwed it up... I have a habit a messing with things when I don't know how they work, I got into several situations where the only thing I could manage to do was reinstall Windows and do some restoring and formatting.

I format entirely too often, is that a bad thing?

Naah - no harm done.  Just a lot of frustration for you.

GRUB and Ubuntu reference the partitons on the drive using UUIDs, and the /dev/sd**x9** are just 'for this session' names.

At least you are getting really good at formatting and reinstalling.

By the way - that '/home' as a seperate partition will allow you to upgrade and downgrade Ubuntu with a lot less pain.  Your 'stuff' will be in the '/home' partition, while the OS installs happen in the '/' (said out loud as 'root' ) partition.  So your data will survive install/update screw ups... :D

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> Naah - no harm done.  Just a lot of frustration for you.

GRUB and Ubuntu reference the partitons on the drive using UUIDs, and the /dev/sd**x9** are just 'for this session' names.

At least you are getting really good at formatting and reinstalling.

By the way - that '/home' as a seperate partition will allow you to upgrade and downgrade Ubuntu with a lot less pain.  Your 'stuff' will be in the '/home' partition, while the OS installs happen in the '/' (said out loud as 'root' ) partition.  So your data will survive install/update screw ups... :D

***The Hedge***

:KS


Haha I guess I am getting pretty good at that :P And thanks for helping me set it up like that! Less pain is good :D

---

### Post by Axman10 on 2011-03-30
Ok here's what happened. After awhile of downloading packages, the time remaining skyrocketed to 327:34 or something left. I was also unable to load anything on the internet, but it wasn't my network as I could use the internet just fine on my ipod. I looked into the bar on the bottom and after quite a while of it just sitting there it started saying that it was deleting files. It deleted python, and a couple of other things I can't remember off the top of my head. 

Then it completed Installation and asked me to restart :D.... :(

 Error: no such device, grub rescue

Here's a new Boot Info...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext4
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

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304   625,139,711   625,041,408   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2042 MB, 2042764800 bytes
32 heads, 63 sectors/track, 1979 cylinders, total 3989775 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,987,647     3,987,585   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    20,482,047    20,480,000  83 Linux
/dev/sdc2          20,482,048    24,987,647     4,505,600  82 Linux swap / Solaris
/dev/sdc3          24,987,648   234,440,703   209,453,056  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D7-0907                              vfat       DellUtility                   
/dev/sda2        8A96C99396C98065                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8044-7ED3                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4a32e09d-e920-48b8-9419-3cdb3258e9dd   ext4                                     
/dev/sdc2        16c656e0-7924-42de-86e7-df65c772c090   swap                                     
/dev/sdc3        33c2dc25-a8c9-48c7-b1d5-e6aa0908b182   ext4                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 4a32e09d-e920-48b8-9419-3cdb3258e9dd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 4a32e09d-e920-48b8-9419-3cdb3258e9dd
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 4a32e09d-e920-48b8-9419-3cdb3258e9dd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4a32e09d-e920-48b8-9419-3cdb3258e9dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 4a32e09d-e920-48b8-9419-3cdb3258e9dd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4a32e09d-e920-48b8-9419-3cdb3258e9dd ro single 
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 4a32e09d-e920-48b8-9419-3cdb3258e9dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 4a32e09d-e920-48b8-9419-3cdb3258e9dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 07d7-0907
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8a96c99396c98065
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdg1 during installation
UUID=4a32e09d-e920-48b8-9419-3cdb3258e9dd /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdg3 during installation
UUID=33c2dc25-a8c9-48c7-b1d5-e6aa0908b182 /home           ext4    defaults        0       2
# swap was on /dev/sdg2 during installation
UUID=16c656e0-7924-42de-86e7-df65c772c090 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   6.8GB: boot/grub/core.img
   6.8GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.35-22-generic
   6.8GB: boot/vmlinuz-2.6.35-22-generic
   1.5GB: initrd.img
   6.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 08 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 f4 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  81 d8 3c 00 80 00 29 d3  7e 44 80 4e 4f 20 4e 41  |..<...).~D.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 10  02 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by Hedgehog1 on 2011-03-30
Yeah... Had a feeling this might come up...

Please do this:

Reboot off the hard drive, select ubuntu, let the error messages roll by.

Count to 10, slowly, then type: exit

If the GUI comes up, it is an easy fix.

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> Yeah... Had a feeling this might come up...

Please do this:

Reboot off the hard drive, select ubuntu, let the error messages roll by.

Count to 10, slowly, then type: exit

If the GUI comes up, it is an easy fix.

***The Hedge***

:KS

I'm not sure what you mean, as soon as I turn on the computer, it shows the dell screen, then it immediatly says Error: no such device, grub rescue.

---

### Post by Hedgehog1 on 2011-03-30
As a side note - remember how that drive WAS sdg, and now it's sdc?

This is why we use UUID of the partitions in fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# **[COLOR="Red"]/ as on /dev/sdg1 during installation[/COLOR]**
UUID=4a32e09d-e920-48b8-9419-3cdb3258e9dd /               ext4    errors=remount-ro 0       1
# **[COLOR="red"]/home was on /dev/sdg3 during installation[/COLOR]**
UUID=33c2dc25-a8c9-48c7-b1d5-e6aa0908b182 /home           ext4    defaults        0       2
# **[COLOR="red"]swap was on /dev/sdg2 during installation[/COLOR]**
UUID=16c656e0-7924-42de-86e7-df65c772c090 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

This make fstab (**F**ile **S**ystem **TAB**le) immune to these changes.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> I'm not sure what you mean, as soon as I turn on the computer, it shows the dell screen, then it immediatly says Error: no such device, grub rescue.

OK - once that message comes up, count to 10 before you type: **exit**

Does the GUI come up then?  If so, stay in Ubuntu and we can fix it from there.

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> OK - once that message comes up, count to 10 before you type: **exit**

Does the GUI come up then?

***The Hedge***

:KS

I'll try right now one minute.

---

### Post by Axman10 on 2011-03-30
It's telling me exit is an unknown commmand.

---

### Post by Hedgehog1 on 2011-03-30
I noticed you unmarked the 'solved' tag. :D

What we are trying to see is: does the drive need a little more time before it is ready to be mounted.  If so, we set a root delay option.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
OK, we we are not getting to the 'busy box' level of grub.

Let me check my notes...  I think we can still get this set up anyway...

BRB

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
OK - here goes:

Boot from the LiveCD/USB, select 'TRY' and from the terminal do:

```
sudo mount /dev/sdc1 /mnt
```

```
gksudo gedit /mnt/etc/default/grub
```

*[COLOR="RoyalBlue"]change the line:[/COLOR]*
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
*[COLOR="RoyalBlue"]to:[/COLOR]*
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **rootdelay=120**"
*[COLOR="RoyalBlue"]save the file, exit the editor[/COLOR]*

```
sudo grub-install --root-directory=/mnt /dev/sda
```

And reboot off the hard drive. Do we get into Ubuntu?

I can explain what these commands are doing if you want.

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
Sadly it did not. Back to the no such device. There was a message in the terminal after executing the grub install should I go try again to get it? It said something a out this could cause boot errors because fixnet I think it was, was running.

---

### Post by Hedgehog1 on 2011-03-30
> **Axman10 said:**
> Sorry we did not. Back to the no such device. There was a message in the terminal after executing the grub install should I go try again to get it? It said something a out this could cause boot errors because fixnet I think it was, was running.

Here is what is going on - I missed it earlier:

```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the
 same drive in partition #1 for (,msdos1)/boot/grub.
```

This is what is killing it - it thinks the /boot/grub directory on on the 1st disk, not the second.

Now how do we fix this...

Let me think...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-30
I have work tomorrow and will be logging off shortly.

Here is the wiki on grub - grub rescue is near the end: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Look for this section:

```
1. ls
2. set prefix=(hd**X,Y**)/boot/grub
3. set root=(hd**X,Y**)
4. set
5. ls /boot
6. insmod /boot/grub/linux.mod
7. linux /vmlinuz root=/dev/sd**XY** ro
8. initrd /initrd.img
9. boot
```

For your PC, with Ubuntu on the 2nd disk (dh0,dh1) & 1st partition (count starts at 1), I think you will enter:

```
1. ls
2. set prefix=(hd**1,1**)/boot/grub
3. set root=(hd**1,1**)
4. set
5. ls /boot
6. insmod /boot/grub/linux.mod
7. linux /vmlinuz root=/dev/sd**c1** ro
8. initrd /initrd.img
9. boot
```

This will get you into Ubuntu from the hard disk.

Then do:

```
sudo update-grub
```

I ***think*** you will be OK from there. 


***The 'sleepy' Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
Alright I'll try my best with this. Thanks alot.

---

### Post by Axman10 on 2011-03-30
I'm writing this before I log off for the night and because I will be busy most of tomorrow. After a bit a playing around in the grub rescue thing, I realized it's only listing one hard drive with ls: (hd0) (hd0,msdos2) (hd0,msdos1) so I tried to reinstall grub based on what the wiki said and tried again. No luck. So I looked in my bios and its not detecting my 120gig hard drive. Could It have died?

---

### Post by Hedgehog1 on 2011-03-30
It is possible that the drive has (or is slowly) dying. When it does not appear in BIOS, that is a bad sign.

Also, the fact that the LiveUSB showed as /dev/sd**b** and the hard drive as /dev/sd**c** (it should have been the other way around) means the drive is responding late.

This would explain the other weird behavior of the drive showing up as /dev/sd**f**, and then /dev/ds**g**
 
Does your budget support a single new hard drive to dual boot Windows and Ubuntu from?

You can use **dd** or **ddrescue**e to copy the windows drive (without reinstalling) onto the new drive, then add the Ubuntu partitions to the new, fast, BIGGER hard drive.

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> It is possible that the drive has (or is slowly) dying. When it does not appear in BIOS, that is a bad sign.

Also, the fact that the LiveUSB showed as /dev/sd**b** and the hard drive as /dev/sd**c** (it should have been the other way around) means the drive is responding late.

This would explain the other weird behavior of the drive showing up as /dev/sd**f**, and then /dev/ds**g**
 
Does your budget support a single new hard drive to dual boot Windows and Ubuntu from?

You can use **dd** or **ddrescue**e to copy the windows drive (without reinstalling) onto the new drive, then add the Ubuntu partitions to the new, fast, BIGGER hard drive.

***The Hedge***

:KS

I don't have the budget for a new drive any time soon, although I may be able to convince my little brother to let me use his spare one. If I can't get another one, I'm just going to scrap the 120gig and try a dual boot from one harddrive. And if all else fails, I'm getting rid of Windows all together. I love Ubuntu! :D

I won't be able to respond at all today as I am at school, I will get back to you later.

---

### Post by Hedgehog1 on 2011-03-30
I hate to make you have to borrow a drive from your ***little brother***; you will never hear the end of it! :D

It appears your primary drive is 320 gigs:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304   625,139,711   625,041,408   7 HPFS/NTFS
```

You can shrink the size of /dev/sda2 (called 'C:' in Vista) using Vista's Disk Manager utility.  If you can get 30 gigs free, that is a decent amount of space.

**You could do:**

/dev/sda3 extended partition (all 30 gigs)
__/dev/sda5 ext4 '/' 8 gigs
__/dev/sda6 linux_swap RAM size plus 10% of RAM (2 gigs RAM, 2.2 gigs swap)
__/dev/sda7 ext4 '/home/ remaining space left.

**You also could do this:**

/dev/sda2 NTFS (your Vista install) Shrink to 60 gigs
/dev/sda3 NTFS  230 gigs - Common storage for Music, Videos (D: drive in Vista, and mounted in Ubuntu)
/dev/sda4 extended partition ( 30 gigs)
__/dev/sda5 ext4 '/' 8 gigs
__/dev/sda6 linux_swap RAM size plus 10% of RAM (2 gigs RAM, 2.2 gigs swap)
__/dev/sda7 ext4 '/home/ remaining space left.

The second plan likely means creating the NTFS /dev/sda3 smaller than 230 gigs at first, moving videos & music over to it, then shrinking /dev/sda some more - until you get where you want to be.

**REMEMBER:** If you are forced to shrink an NTFS partiton with gparted, always defrag that partition using Windows first, *then* shrink ('resize' in gparted terms) that partition with gparted.


***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-30
> **Hedgehog1 said:**
> I hate to make you have to borrow a drive from your ***little brother***; you will never hear the end of it! :D

It appears your primary drive is 320 gigs:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304   625,139,711   625,041,408   7 HPFS/NTFS
```You can shrink the size of /dev/sda2 (called 'C:' in Vista) using Vista's Disk Manager utility.  If you can get 30 gigs free, that is a decent amount of space.

**You could do:**

/dev/sda3 extended partition (all 30 gigs)
__/dev/sda5 ext4 '/' 8 gigs
__/dev/sda6 linux_swap RAM size plus 10% of RAM (2 gigs RAM, 2.2 gigs swap)
__/dev/sda7 ext4 '/home/ remaining space left.

**You also could do this:**

/dev/sda2 NTFS (your Vista install) Shrink to 60 gigs
/dev/sda3 NTFS  230 gigs - Common storage for Music, Videos (D: drive in Vista, and mounted in Ubuntu)
/dev/sda4 extended partition ( 30 gigs)
__/dev/sda5 ext4 '/' 8 gigs
__/dev/sda6 linux_swap RAM size plus 10% of RAM (2 gigs RAM, 2.2 gigs swap)
__/dev/sda7 ext4 '/home/ remaining space left.

The second plan likely means creating the NTFS /dev/sda3 smaller than 230 gigs at first, moving videos & music over to it, then shrinking /dev/sda some more - until you get where you want to be.

**REMEMBER:** If you are forced to shrink an NTFS partiton with gparted, always defrag that partition using Windows first, *then* shrink ('resize' in gparted terms) that partition with gparted.


***The Hedge***

:KS

I'm going with plan A for simplicities sake. I can get up to 100 gigs after shrinking Vista. The more the merrier?

---

### Post by Hedgehog1 on 2011-03-30
100 gigs is plenty to keep you rolling!

Looking forward to you first post from the hard disk installed Ubuntu!

***The Hedge***

:KS

---

### Post by Axman10 on 2011-03-31
I'm so very excited right now! Posting from a newly installed Ubuntu! Thanks for every bit of help you've given me, and I have one last questing. When I try to connect to a network, it asks for a password for keyring 'Default' which I don't know. I hit cancel twice then it lets me put the networks password in, then it asks for the keyring pass again. If I press cancel on the last keyring it connects me to the network. This seems odd.

---

### Post by Dutch70 on 2011-03-31
The keyring password should be the same as your login, unless you've changed it.

---

### Post by Hedgehog1 on 2011-03-31
> **Axman10 said:**
> I'm so very excited right now! Posting from a newly installed Ubuntu! Thanks for every bit of help you've given me, and I have one last questing. When I try to connect to a network, it asks for a password for keyring 'Default' which I don't know. I hit cancel twice then it lets me put the networks password in, then it asks for the keyring pass again. If I press cancel on the last keyring it connects me to the network. This seems odd.
 
 
Happy to hear you are up and running!  For a while there this was a real hard install...
 
***The Hedge***
 
:KS

---

