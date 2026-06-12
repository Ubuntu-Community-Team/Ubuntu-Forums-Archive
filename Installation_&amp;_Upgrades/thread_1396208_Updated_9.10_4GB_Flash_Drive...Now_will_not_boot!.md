---
title: "Updated 9.10 4GB Flash Drive...Now will not boot!"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by gomab2k4 on 2010-02-01
Hi. I just purchased this Ubuntu branded 9.10 4GB Flash Drive from the Canonical Store below:

[http://shop.canonical.com/product_info.php?currency=USD&products_id=577](http://shop.canonical.com/product_info.php?currency=USD&products_id=577)

That being said, it worked great...until I performed an update. Now, it will not boot up...let alone work. I understand that if this were a Ubuntu flash drive in which I created, all I would have to do is format the flash drive and re-install Ubuntu. Unfortunately, this flash drive will not let me format to re-install. 

Is there any way I can restore the flash drive to its original state? For what its worth, I also have an Ubuntu CD (which I was not able to re-install to this flash drive). Any thoughts are appreciated.

---

### Post by Leppie on 2010-02-01
hi and welcome to the community,

could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by gomab2k4 on 2010-02-02
Is this what you are looking for?

---

### Post by drs305 on 2010-02-02
gomab2k4

It appears you attached the script itself instead of the results. After downloading the script, you should change to the download folder (probably ~/Desktop or ~/Downloads) and run meierfra's script per the instructions on this page: [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

This should generate a file called RESULTS.txt  The contents of that file are what we would like to see. Copy the contents, then paste them into a post. Highlight them and then click on the # icon in the menu entry so the contents are placed between "code" tags.

---

### Post by gomab2k4 on 2010-02-03
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

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

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e7970

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   112,326,479   112,326,417  83 Linux
/dev/sda2         112,326,480   117,210,239     4,883,760   5 Extended
/dev/sda5         112,326,543   117,210,239     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ecee5806-c72f-4db0-986d-4bb6c7b2f16e   ext4                                     
/dev/sda5        57c20213-182d-4d00-bbf4-45f0774539b1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ecee5806-c72f-4db0-986d-4bb6c7b2f16e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=57c20213-182d-4d00-bbf4-45f0774539b1 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: vmlinuz
```

---

### Post by wbloos on 2010-02-03
me too.
I have a 8GB flash drive, it booted after using the "USB startup disk creator", but after installing the updates, when i boot i get the ubuntu logo, then the screen goes blank. Managed to get some text on the screen (all stretched), it said :
```
stdin: error0
mount: mounting /dev/sda5 on /cdrom failed: no such device
init: lin1: can't open /dev/sr0: no medium found
init: lin1: can't open /dev/sr0: no medium found
mount: mounting /dev/sda1 on /cdrom failed: no such device
stdin: error0
mount: mounting /dev/sda5 on /cdrom failed: no such device
init: lin1: can't open /dev/sr0: no medium found
init: lin1: can't open /dev/sr0: no medium found
```

So i reformated the pen drive and reinstalled the the image + updates. I ran the boot info script (from the booted flash drive after updates but before reboot). Results attached.
rebooted, with same result.

cheers,

wbloos

---

### Post by wbloos on 2010-02-03
hmm, could it be because i chose not to install grub to any of the drives?
There was a question about where to install grub when the updates were being processed. I checked none of the drives (checkboxes) because i was afraid that it might jeopardize my laptop (none checked by default).
Possibly, grub would be mandatory because a new kernel was installed during the updates?

---

### Post by wbloos on 2010-02-03
no.
repeated the whole procedure, found out which drive is my pen drive, checked it when the grub question came, same result (screen goes blank when booting, then nothing, same error messages visible after pressing space on the built in keyboard, usb keyboard will not work).

On shutdown, i saw a lot of text on the screen for a fraction of a second, which looked like it contained error messages.
But when i mounted the flash disk, i couldn't find any logs.
Any idea how i could find logging of possible errors that ocurred during shutdown?

---

### Post by gomab2k4 on 2010-02-03
I managed to format the flash drive this morning, and it is working as it should. This time around, I will not be updating it until the issue this issue is resolved. Thanks for everyone's input!

---

### Post by wbloos on 2010-02-04
It seems like performing updates breaks the install.
Am i doing something wrong? This should be documented, there is no mention of this in [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
It only says "works like normal" in the end.

Also, the software center gave me no option to install new software before the update. I was hoping it would after the update, but since the install breaks, i can't find out.
Is not installing new packages per design?

cheers,

WBL

---

### Post by wbloos on 2010-02-08
anyone?

---

### Post by ebro173 on 2010-04-14
Sorry,  I can't help you.  But reading the posts here it seems you could help me.

I installed UNR 9.10 to an 8GB usb flash drive using Universal-USB-Installer (or something like that) from within windows.  I got that executable installer from a website pendrivelinux - I think.

I now want to install 10.04 beta 2 on the usb flash drive.

Using an updated version of that installer fails because it won't reformat the drive.  This may be because Windows can't see that anything in on the drive.

How did you reformat your flash drive?  I tried using the Windows 7 partitioning tool but no luck.

---

### Post by ebro173 on 2010-04-14
Nevermind.  I figured out what was happening.  I was restarting the computer after being in the UNR 9.10 (running from the flash drive) and leaving the flash drive in.  (For some reason the computer in this case would not boot into the flash drive, but would go directly to windows.)  

Anyway, since the flash drive was never plugged in after windows was booted up it saw it but didn't see it...

On the other hand if I plugged in the flash drive after booting windows it recognized the drive and I could see files etc.  That way I was able to re-format and re-install.

---

