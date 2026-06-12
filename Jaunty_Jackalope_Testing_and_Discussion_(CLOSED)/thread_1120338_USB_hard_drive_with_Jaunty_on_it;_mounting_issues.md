---
title: "USB hard drive with Jaunty on it; mounting issues"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kumoshk on 2009-04-08
Hello, I just got a new external hard drive and I put Jaunty on a partition. I have lots of other partitions, too (it's 1TB), however, I don't want any of the other partitions to mount automatically when I load Ubuntu from the USB. I didn't select to use any of the other partitions in the installation (on a normal hard drive installation, they wouldn't be mounted here). How do I disable this automount?

Also, when I plug the USB hard drive in after my laptop's hard drive's installation of Ubuntu has loaded (also Jaunty, only 64-bit instead of 32) then all the partitions automatically mount. I want to be able to configure which ones automatically mount and which ones don't. Is this possible?

---

### Post by Michael.Godawski on 2009-04-09
Moved to Jacky Jackalope Testing and Discussion.

---

### Post by knattlhuber on 2009-04-09
You can edit the /etc/fstab file in order to configure which partitions should mount at boot. To prevent a file from mounting at boot time, you have to use the "noauto" option.

A good HOWTO on fstab can be found here:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

Be sure to make a backup copy of your /etc/fstab before messing about! ;)

---

### Post by kumoshk on 2009-04-09
Is fstab really the way to go with USB devices? The partitions that are mounting at boot time don't seem to be in fstab at all. Here are the contents of my fstab file:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=4ee6bab2-e09d-4150-b79b-56d9e253fdb3 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=8852a783-6f3f-4b64-8a61-6bdcc5ec576f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Anyway, sdc5, sdc4, sdc3 and sdc2 are all automatically mounted after I boot up. The only one mentioned in fstab appears to be sdc5, which is the root partition that I want used, as well as the swap partition on the laptop's hard drive (sda4) and the DVD burner.

I'm guessing the solution to this would be the same as with preventing an automount for a flash drive plugged in after the computer has already booted up. How do I do that? Do I still use fstab, somehow, even though it doesn't appear to be related to booting? I'll take a look at that link.

All my partitions are Ext4 on the external USB hard drive.

---

### Post by kansasnoob on 2009-04-09
This may or may not be helpful to you, it was helpful to me ten months ago but I was still using Gutsy at the time!

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I've just not encountered the need to create a persistent USB boot since then.

---

### Post by kumoshk on 2009-04-09
All right, I think I found the solution. It works with stuff inserted after I've already booted up, but I'm in the middle of copying gigabytes of files right now&#8212;so I'll have to wait before I can test it out on my USB installation to see if it stops those from mounting at startup.

Anyway, the solution, perhaps (at least half the solution, if not the full), is to open gconf-editor. Go to apps. Go to nautilus. Go to preferences. Uncheck media_automount. I unchecked media_automount_open for good measure.


> **kansasnoob said:**
> This may or may not be helpful to you, it was helpful to me ten months ago but I was still using Gutsy at the time!

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

I've just not encountered the need to create a persistent USB boot since then.

Ah, I've already got a successful installation on my USB hard drive. It's actually easier on Jaunty, believe it or not. All you have to do is run the installation with the USB device connected, manually configure your partitions, set a partition on the USB device as root, don't include any of the other partitions (unless you know what you're doing and want to), click the advanced button when you get to the screen it's on, select the USB device for the boot loader, and finish installing as you normally would. I just use my internal hard drive's swap partition since I don't plan to use the external installation on multiple computers (I just have it for 32-bit OS purposes since my internal installation is 64-bit and won't run PowerDVD; knowing that, it makes sense that I won't want to mount everything at startup, seeing as I'm just going to watch movies when I use that).

Oh, you'll want to make sure your BIOS can handle booting from the USB, and be sure to make the boot order so that it will boot from the USB device before the hard drive, if you want.

---

