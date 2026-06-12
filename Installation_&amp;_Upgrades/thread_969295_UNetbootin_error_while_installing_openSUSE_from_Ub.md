---
title: "UNetbootin error while installing openSUSE from Ubuntu using downloaded .iso"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Jags_FL on 2008-11-03
I'm trying to install openSUSE from Ubuntu 8.10 on another partition using UNetbootin thru downloaded openSUSE-11.1-Beta4-GNOME-LiveCD-i686.iso 

On UNetbootin interface, in order to select the partition where I want to install openSUSE I have to select 'USB Drive' to get '**/dev/sdb1**'. If I select 'Hard Disk' under 'Type', I get only one option of '/' under 'Drive', and 'Show All Drives' becomes grayed out.

Provided path to downloaded openSUSE ISO under 'Diskimage' and upon hitting OK, UNetbootin generated 654 MB 'openSUSE-11.1-read-only.i686-2.7.0' file, boot folder & bunch of other files in /dev/sdb1.

Next I added two entries into Ubunu grub:

:::::
title Option# 1: /boot/i386/loader/linux
root	(hd1,0)
kernel	/boot/i386/loader/linux
initrd	/boot/i386/loader/initrd

title Option# 2: /ubnkern
root	(hd1,0)
kernel	/ubnkern
initrd	/ubninit
:::::

Rebooting with either option I get stuck at following:

:::::
Loading KIWI CD Boot-System....

Waiting for CD/DVD device(s) to appear...
Mounting CD/DVD drive
**Couldn't find CD image configuration file**
rebootException: error consoles at ALT-F3/F4
rebootException: reboot in 120 sec...
:::::

Many thanks, any help is greatly appreciated. - jags

---

### Post by Jags_FL on 2008-11-03
hi...  anyone on installing downloaded .iso thru UNetbootin, please...

Many thanks.

---

### Post by sleepitoff on 2008-12-19
Old thread, but did you ever figure out this problem? I'm trying to boot the OpenSUSE 11.1 LiveCD.iso with UNetbootin and I get the same error. At first thought it might be a problem with UNetbootin, but it works fine with other distros' liveCDs.

---

### Post by Eastisle on 2008-12-23
I'm having the same problem. It seems like openSUSE works differently than other livecds. The initrd of the live CD is programmed to call on the cd for files. 

From [http://en.opensuse.org/Live_USB_stick#How_to_create_a_bootable_openSUSE_11.0_USB_stick_from_a_running_openSUSE_system](http://en.opensuse.org/Live_USB_stick#How_to_create_a_bootable_openSUSE_11.0_USB_stick_from_a_running_openSUSE_system) :
> 
"Other than Ubuntu- and Fedora-type systems, the initrd on SUSE-type live CDs is not directly suitable for booting from a USB stick."

---

### Post by deusdies on 2009-01-04
I figured something. The configuration file UNetbootin sets for installing is based on the fact that you're installing from a CD/DVD drive. I somewhere in the log saw "Could not find configuration at cdrom://" or something like that.

How I solved the problem? I burnt a live CD...

---

### Post by simplysimple on 2009-03-11
Hello, just thought I would post the fix...

Once UNetbootin has finished writing all the files to the usb 

Open the usb so that you can view all the files/folders

You are looking for two files...
config.isoclient and config.kde.isoclient or config.gnome.isoclient the second file depends on if you are installing kde or gnome openSUSE 

Delete config.isoclient

Rename config.kde.isoclient or config.gnome.isoclient depending on which one you have to config.isoclient replacing the file you deleted

Now boot from the usb device and you should get passed the error during boot.

---

### Post by moomooranch on 2009-06-09
> **simplysimple said:**
> Hello, just thought I would post the fix...

Delete config.isoclient

Rename config.kde.isoclient or config.gnome.isoclient depending on which one you have to config.isoclient replacing the file you deleted


THANK YOU!!! This worked perfectly :KS

---

### Post by manit on 2009-10-16
Hi I am trying to boot openSUSE from iso extracted on hard disk partition.Can you post contents of
config.gnome.isoclient file alongwith its location.
Thank you.

---

### Post by mc.prtk on 2009-11-25
will test it out...........

---

### Post by bit mad on 2009-11-25
> **simplysimple said:**
> Hello, just thought I would post the fix...

Once UNetbootin has finished writing all the files to the usb 

Open the usb so that you can view all the files/folders

You are looking for two files...
config.isoclient and config.kde.isoclient or config.gnome.isoclient the second file depends on if you are installing kde or gnome openSUSE 

Delete config.isoclient

Rename config.kde.isoclient or config.gnome.isoclient depending on which one you have to config.isoclient replacing the file you deleted

Now boot from the usb device and you should get passed the error during boot.

I'd love to know where those config.kde/gnome.isoclient files come from, I've tried doing a USB key with openSUSE-11.2-GNOME-LiveCD-i686.iso and failed. Those files aren't in the ISO as far as I can see. :confused:

---

### Post by rajeshgheware on 2010-12-29
I had this problem with openSuse 11.3 booting.  I tried Unetbootin and also tried using initrtud (as a replacement of initrd since some users said this would work) but all in vein.

Finally, after spending couple of nights working on this problem, I got the solution and this is how simple it is:

1. Replaced my USB HDD with USB FDD (for some reason, booting fails with USB HDD)
2. Erased USB FDD (you can Ubuntu Startup disk creator if you wish)
3. Use this command (after su/sudo): dd if=/<iso or .raw file location> of=/dev/sdX bs=8MB

NOTE: /dev/sdX where in sdX, X is where your USB is mapped (check this using 'df -h' command). If you see /dev/sdb (and /dev/sdb1 ...), use /dev/sdb
4. Reboot your laptop/netbook (I used Samsung N148 netbook)

If this does not work for you, then let me know.

Regards,
Rajesh
[http://rajeshg.info](http://rajeshg.info)

---

### Post by rajeshgheware on 2010-12-29
I had this problem with openSuse 11.3 booting.  I tried Unetbootin and also tried using initrtud (as a replacement of initrd since some users said this would work) but all in vein.

Finally, after spending couple of nights working on this problem, I got the solution and this is how simple it is:

1. Replaced my USB HDD with USB FDD (for some reason, booting fails with USB HDD)
2. Erased USB FDD (you can use Ubuntu Startup disk creator to Erase the disk if you wish)
3. Use this command (after su/sudo): dd if=/<iso or .raw file location> of=/dev/sdX bs=8MB

NOTE: /dev/sdX where in sdX, X is where your USB is mapped (check this using 'df -h' command). If you see /dev/sdb (and /dev/sdb1 ...), use /dev/sdb
4. Reboot your laptop/netbook (I used Samsung N148 netbook)

If this does not work for you, then let me know.

Regards,
Rajesh Gheware
[http://rajeshg.info](http://rajeshg.info)

---

### Post by penguin1029 on 2010-12-29
> **rajeshgheware said:**
> I had this problem with openSuse 11.3 booting.  I tried Unetbootin and also tried using initrtud (as a replacement of initrd since some users said this would work) but all in vein.

Finally, after spending couple of nights working on this problem, I got the solution and this is how simple it is:

1. Replaced my USB HDD with USB FDD (for some reason, booting fails with USB HDD)
2. Erased USB FDD (you can use Ubuntu Startup disk creator to Erase the disk if you wish)
3. Use this command (after su/sudo): dd if=/<iso or .raw file location> of=/dev/sdX bs=8MB

NOTE: /dev/sdX where in sdX, X is where your USB is mapped (check this using 'df -h' command). If you see /dev/sdb (and /dev/sdb1 ...), use /dev/sdb
4. Reboot your laptop/netbook (I used Samsung N148 netbook)

If this does not work for you, then let me know.

Regards,
Rajesh Gheware
[http://rajeshg.info](http://rajeshg.info)
Hello, i am having the same problem when i enter that code this happens 
```
dd: unrecognized operand `of/dev/sdb1'
Try `dd --help' for more information.
```

---

