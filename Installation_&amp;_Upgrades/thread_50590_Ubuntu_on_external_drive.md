---
title: "Ubuntu on external drive"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by Cool Dude 2k on 2005-07-20
Can Ubuntu work on a external hard drive?
The external hard drive I have is a Western Digital USB 2.0 Series II Hard Drive. Can Ubuntu work on it?
Thanks for you help. :cool:

---

### Post by netrattler on 2005-07-20
From "propagandhi"

STEP1: INSTALL THE OS

*IMPORTANT: when you boot the Ubuntu install CD, make sure you type 'expert' before pressing enter to start the installer.

The reason for this is that using the Expert installer, you get access to a shell before you have to reboot, and u have a bit more control over the install process THIS IS CRUCIAL IF YOU WANT TO AVOID PROBLEMS.

Install Ubuntu to the USB drive, by selecting the '(sda)' or whatever the drive is (it will generally NEVER be (hdc) or (hda)

STEP 2: CONFIGURE THE MKINITRD SCRIPT

After you have finished all the installation items (IE: install base system, configure network, select input locales, copy remaining packages to HDD),
you need to select the option "Execute A Shell".

Once the shell is loaded, type the following:

'nano /target/etc/mkinitrd/modules'

This will load up the file that tells the mkinitrd script which modules need to preloaded in the kernel initialisation process.

ADD THE FOLLOWING LINES:

sd_mod
ehci-hcd
uhci-hcd
ohci-hcd
usb-storage

Once you have done this, type the following:

'nano /target/etc/mkinitrd/mkinitrd.conf'

EDIT the line that says DELAY=0 and change it to anything over 10 (i chose 15 to be safe).

This step just ensures that the kernel will wait long enough for the USB device to appear before attempting to mount the root partition. If it doesn't
wait long enough, you will get the message " Kernel panic: Unable to sync VFS!" or something similar.

STEP 3: BUILD THE INITRD IMAGE

Now that you have told the script which modules to build into the Initrd ramdisk, you simply need to type the following:

chroot /target
mount -tproc none /proc
mkinitrd -o /boot/usbinitrd.img-(kernel version OPTIONAL)

STEP 4: CONFIGURE GRUB BOOT LOADER

The last step will involve adding an entry to the new kernel/ramdisk in the menu.lst config file of GRUB. MY particular entry is as follows:


title Ubuntu Hoary (5.04 USB)
kernel (hd1,4)/boot/vmlinuz-2.6.10-5-386 ro root=/dev/sda5
initrd (hd1,4)/boot/usbinitrd.img

You can do this by typing 'nano /target/boot/grub/menu.lst' and adding the entry that's appropriate for your setup. After that u need to do a /sbin/grub-install /dev/sdaX (where X is the partition number).

Now just type exit until you see the installer again and choose the option "Finish Installation". Reboot, and u should be able to boot into your new linux USB installation.

Joe

---

### Post by Cool Dude 2k on 2005-07-21
Thanks very much for you help I'll try this out. :)

---

### Post by Cool Dude 2k on 2005-07-21
I get a error on the 4th step.
[QUOTE=netrattler]STEP 4: CONFIGURE GRUB BOOT LOADER

The last step will involve adding an entry to the new kernel/ramdisk in the menu.lst config file of GRUB. MY particular entry is as follows:


title Ubuntu Hoary (5.04 USB)
kernel (hd1,4)/boot/vmlinuz-2.6.10-5-386 ro root=/dev/sda5
initrd (hd1,4)/boot/usbinitrd.img

You can do this by typing 'nano /target/boot/grub/menu.lst' and adding the entry that's appropriate for your setup. After that u need to do a /sbin/grub-install /dev/sdaX (where X is the partition number).

Now just type exit until you see the installer again and choose the option "Finish Installation". Reboot, and u should be able to boot into your new linux USB installation.

Joe[/QUOTE]
I get  > Error Opening terminal: Bterm When entering ```
nano /target/boot/grub/menu.lst
```

---

### Post by SkIMMas on 2005-07-21
Getting the same problem listed above.

And two newbie questions:

The above solution meant to work with a bios that does have usb drive support isn't it? any way to get ubuntu working in a bios without usb support? 

by following the steps above where will grub be installed?

---

### Post by fanoodlehey on 2005-07-22
I had the same problem as this some time back. If I remember rightly you should be able to edit the menu.lst config file line by line from GRUB. This will allow the system to boot and then from within the installed ubuntu you should be able to edit menu.lst permanently as root.

Grub should be installed on the external drive.
I don't think this can possibly work without bios support for booting from USB.

---

### Post by SkIMMas on 2005-07-22
I've been doing some investigation and found the following things:

about  "Error Opening terminal: Bterm"

just type **exit** once and you'll be able to use the nano command, when finished do **chroot /target** again.

I feel I'm almost there. I wonder if it's possible to install grub to a floppy

About installing linux without bios support i found [this](http://www-128.ibm.com/developerworks/library-combined/l-fireboot.html) 

I'll keep trying and I'll post how I did it if I succed

---

### Post by ol_geezer on 2005-07-22
Regarding step 4,

How do I know what is appropriate for my setup?

I have no way of knowing which is the correct partition to set here.  I used the automatic partitioning and I'm not sure where to point GRUB.

sda1, ?  The existing grub entries show sda1,0

Laptop - internal IDE drive hda1 (windows XP) , External USB drive sda1 (Ubuntu)

 ](*,)

---

### Post by ol_geezer on 2005-07-22
I keep getting the error:

Filesystem type unkown, partition type 0x7

Error 17:  cannot mout selected partition

Did I set my partitons up wrong?

I believe they are as follows:

#1 - /boot - etxt3
#2 - swap - swap
#5 - home - ext3

Is this correct?

---

### Post by netrattler on 2005-07-23
Did you setup a / partition

Joe

---

### Post by EchoBeach on 2005-07-23
The entry in menu.lst above (STEP 4) is: ```
title Ubuntu Hoary (5.04 USB)
kernel (hd1,4)/boot/vmlinuz-2.6.10-5-386 ro root=/dev/sda5
initrd (hd1,4)/boot/usbinitrd.img

```I changed this for my set up thus:
```
title Ubuntu Hoary (5.04 USB)
kernel (hd0,1)/boot/vmlinuz-2.6.10-5-386 ro root=/dev/sdb1
initrd (hd0,1)/boot/usbinitrd.img
```'(hd0,0)' because I'm asking my PC (using its own boot menu) to boot from the USB drive - so it's the first drive.  '/dev/sdb1/' because that how the partitions were identified during the partition phase of the install.

The entry in menu.lst that refers to my Windows XP partition on the PC's internal HDD also uses '(hd0,1)' because the default boot disk is the main disk - if you see what I mean!  (The Recovery System is the first partition and the NTFS partition is the second one hence the ',1' instead of ',0')

Result:
If I request the PC to boot from the USB drive, Ubuntu (HH 5.04) boots up just fine.
If I request the PC to boot from the internal HDD, Grub still starts and I have to choose the correct partition to boot - but it boots into Windows XP correctly.

All I need to do now is to restore the MBR so that booting from the main disk doesn't involve Ubuntu. [(see my other post)](http://ubuntuforums.org/showthread.php?p=268790#post268790)
We're getting there.
Echo

---

### Post by ol_geezer on 2005-07-25
[QUOTE=netrattler]Did you setup a / partition

Joe[/QUOTE]


I let the install auto-partition the drive.  I do not believe there is a / partiton, but I'm not sure how to check.

What are the reccomended partitions (and partion types - ext3, swap, JFs, etc.) for this application (external USB drive)?  I think creating them manually might help solve this problem.

It's a 60GB drive
512MB RAM  (I think the swap was 1.5GB)

Thanks Joe

---

### Post by Rapaport on 2005-08-05
netrattler:

I followed your steps exactly until the last phase when your wrote:

> After that u need to do a /sbin/grub-install /dev/sdaX

I could not complete this in the shell and I'm not sure if it has anythign to do with the error I received.

```
Starting Ubuntu...
Pivot_root: no such file or directory 
/sbin/init: 428 : cannot open dev/consoles no such file  
Kernel panic - not syncing: attempted to kill init
```

I followed all the instructions exactly except the last one because I couldn't.
And also, I had an issue with mount -tproc none/proc, the system couldn't recognize this command. Any ideas?

---

### Post by telcomguy on 2005-08-07
I'm working through all of this and haven't gotten it to work yet, but I have learned this.  After you execute the "chroot /target" command, you need to do an "exit" at the prompt before you can use "nano" again.  Before you execute the "/sbin/grub-install" command, you need to "chroot /target" again.

---

### Post by ol_geezer on 2005-08-08
[QUOTE=Rapaport]And also, I had an issue with mount -tproc none/proc, the system couldn't recognize this command. Any ideas?[/QUOTE]


Make sure that your command has a space after 'none' - looks like you mashed none and /proc together.

mount -tproc none /proc

Also, sometimes you have to do a CTRL+ALT+F2 and use that terminal
(use CTRL+ALT+F1 to get back)

---

