---
title: "Make USB Startup Disk - in Ubuntu 8.10"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by boondocks on 2008-10-27
As I understand it, there is a USB start-up disk creator in Ubuntu 8.10
and it does offer persistent storage capabilities.

I have not yet tried 8.10 but if you have esperimented with this feature,
how would you use the persistent storage - if you wanted to carry the
USB disk with you from PC to PC?

What I mean is that if I ran 8.10 off such a USB disk and created an
account for "John".  So after rebooting the system -
Can I log in as "John"?  (As I currently can running off the hard disk.)

Or do I have to do something special to save the session before rebooting?

---

### Post by C.S.Cameron on 2008-10-27
usb-creator creates a bootable copy of the Live CD on the flash drive.
This install is made persistent using folders named casper-rw and home-rw, where changes are automatically saved.
(The Live CD can also be made persistent using a flash drive with ext3 partitions using these labels, this drive will work with a Live USB also).
No changes are ever made to the operating system itself, you cannot actually make an account on it.

---

### Post by boondocks on 2008-10-27
Ok.

How can I do this?
[LIST]
[*]Run Ubuntu off a USB Flash Drive.
[*]Create a user account "John" in Ubuntu.
[*]Make that user account and any system changes persistent.
[*]Carry this USB Flash Drive with me between the 3 PCs that I use regularly.
[*]Log in as "John", edit/save documents, etc.
[/LIST]

---

### Post by C.S.Cameron on 2008-10-27
Sounds like you want a full install.
You can install to flash disk from Live CD the same as to hard disk.

I suggest disabling your hard drive first, then just run install from the CD.

This page gives some options for persistent flash:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by psyke83 on 2008-10-27
> **C.S.Cameron said:**
> Sounds like you want a full install.
You can install to flash disk from Live CD the same as to hard disk.

I suggest disabling your hard drive first, then just run install from the CD.

This page gives some options for persistent flash:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

No, the implementation of usb-creator is much superior to the instructions on that page.

I've been using a persistent flash image on a 2G USB key (on a HP NX9010 laptop with no hard drive installed) for a week or so, and it works very well.

The persistent mode offered by usb-creator differs from the wiki above, as it can make persistent changes *system-wide*. This means not only that your users files and settings are changed, but also system files. For example, you can install new packages.

When you use a persistent image, it can be used on any computer due to the fact that it boots identically to the live cd (with exception to any changes you make via persistence). One downside is that you cannot use a custom xorg.conf; it seems that it is automatically generated for each boot, overwriting the saved version.

> **C.S.Cameron said:**
> No changes are ever made to the operating system itself, you cannot actually make an account on it.

Not true. As I said, the persistence applies to user and system files. I have configured my bootable image to automatically log into a custom-created account (instead of the default "ubuntu").

---

### Post by bpl07 on 2008-10-27
psyke83,

What does it do about the /tmp folder?  Do you expect considerable wear on your usb drive?

---

### Post by psyke83 on 2008-10-27
> **boondocks said:**
> Ok.

How can I do this?
[LIST]
[*]Run Ubuntu off a USB Flash Drive.
[*]Create a user account "John" in Ubuntu.
[*]Make that user account and any system changes persistent.
[*]Carry this USB Flash Drive with me between the 3 PCs that I use regularly.
[*]Log in as "John", edit/save documents, etc.
[/LIST]

It depends on the size of your USB drive. If it is 2gb or less, usb-creator will suit your needs perfectly (see my previous post).

However, if you have enough space, it is possible to do a full install to your drive via the normal ubiquity installer. USB Flash drives are treated no differently than an IDE/SCSI/SATA drive.

N.B. If you choose the latter, I would be cautious about using swap. Excessive disk writes will wear out your drive.

---

### Post by psyke83 on 2008-10-27
> **bpl07 said:**
> psyke83,

What does it do about the /tmp folder?  Do you expect considerable wear on your usb drive?

I'm not running it at the moment, so I can't check. When I'm running the USB drive I don't observe a lot of disk writes, but there is swap active when checking via "free". I didn't check if the swap is configured as a ramdisk or regular swap, however.

---

### Post by psyke83 on 2008-10-27
By the way, here's a link to a thread on usb-creator in the Dev Link forum.

[http://ubuntuforums.org/showthread.php?t=927878](http://ubuntuforums.org/showthread.php?t=927878)

---

### Post by boondocks on 2008-10-27
psyke83,

Thanks for all this info.

With respect to this:
[http://ubuntuforums.org/showthread.php?t=927878](http://ubuntuforums.org/showthread.php?t=927878)
People seem to be having issues with it.

Anyway ...
> The persistent mode offered by usb-creator differs from the wiki above, as it can make persistent changes *system-wide*. This means not only that your users files and settings are changed, but also system files. For example, you can install new packages.

*system-wide* = This is exactly what I need.
> As I said, the persistence applies to user and system files. I have configured my bootable image to automatically log into a custom-created account (instead of the default "ubuntu").

So I just put in the USB Flash drive.
Power up the computer.
Use it just like my current Ubuntu desktop.
(I understand that the different video hardware will impact xorg.conf every time.)
Then shutdown the computer.

Down the road, I would like to:
[LIST]
[*]Add some packages that are normally not included in the Desktop version.
[*]Configure those packages.
[*]Carry the USB Flash drive with me so that I have everything good-to-go.
[/LIST]

Questions:
[LIST=1]
[*]All the changes that I make, are they automatically taken care of via persistence?
[*]Do I have to do anything extra/specific to ensure the persistence of the changes?
[/LIST]

---

### Post by psyke83 on 2008-10-27
> **boondocks said:**
> psyke83,

Thanks for all this info.

With respect to this:
[http://ubuntuforums.org/showthread.php?t=927878](http://ubuntuforums.org/showthread.php?t=927878)
People seem to be having issues with it.

Anyway ...

*system-wide* = This is exactly what I need.

So I just put in the USB Flash drive.
Power up the computer.
Use it just like my current Ubuntu desktop.
(I understand that the different video hardware will impact xorg.conf every time.)
Then shutdown the computer.

Down the road, I would like to:
[LIST]
[*]Add some packages that are normally not included in the Desktop version.
[*]Configure those packages.
[*]Carry the USB Flash drive with me so that I have everything good-to-go.
[/LIST]

Questions:
[LIST=1]
[*]All the changes that I make, are they automatically taken care of via persistence?
[*]Do I have to do anything extra/specific to ensure the persistence of the changes?
[/LIST]

You just need to specify that you want to save changes, and specify the size to allocate in the usb-creator interface - it's pretty intuitive.

I suggest you use the intrepid RC ISO image as the source to create the persistent image (people are complaining about the daily builds, unsurprisingly).

I've installed libdvdcss2 and some of the gstreamer0.10-plugins-* in order to play DVDs, so I can attest that installing extra packages works fine.

---

### Post by C.S.Cameron on 2008-10-27
I agree that usb-creator is a simple method to make a persistent flash drive. you will be able save downloaded programs and settings.
I maintain that you will not be be able to make an account named john on it, nor will you be able to upgrade the kernel. There is no way to use a password at login.
Only the folders casper-rw and home-rw are persistent. When you upgrade, the new files are saved to casper-rw and this seems to fill up quickly.
Currently I understand that U-C is not working with 4G flash drives.
On a computer with lots of ram swap does not seem to ever be used.
I have never heard of a flash drive dying from overuse of the tmp folder, I have been using my oldest flash drive with full install for well over a year and it still has 4 years left on the guaranty.

Oops, I am wrong, I have used System, Administration, Users and Groups to add my name and password as a user, I now get a screen asking for user name and password at login. I then leave blank and hit enter if I want to login as default Live Session User.

---

### Post by Arabiest on 2008-10-27
Nice thing gents.

---

### Post by psyke83 on 2008-10-27
> **C.S.Cameron said:**
> I agree that usb-creator is a simple method to make a persistent flash drive. you will be able save downloaded programs and settings.
I maintain that you will not be be able to make an account named john on it, nor will you be able to upgrade the kernel. There is no way to use a password at login.
Only the folders casper-rw and home-rw are persistent. When you upgrade, the new files are saved to casper-rw and this seems to fill up quickly.
Currently I understand that U-C is not working with 4G flash drives.
On a computer with lots of ram swap does not seem to ever be used.
I have never heard of a flash drive dying from overuse of the tmp folder, I have been using my oldest flash drive with full install for well over a year and it still has 4 years left on the guaranty.

It's necessary to change the GDM preferences to either disable automatic login of the "ubuntu" user, or change it to the username you created - perhaps this is the source of your confusion. It *is* possible to create a new account, and it is possible to install new software.

Installing a new kernel? I doubt it'll work correctly. Remember, usb-creator uses syslinux to boot, not grub, and I would imagine most of the startup scripts expect a static kernel.

To simplify: there will be two images on your USB drive - the read-only casper image (from the livecd), and the read-write casper-rw. The read-only image will not be modified (obviously), but the casper-rw will. They are both mounted as a sort of "hybrid" filesystem; when a file is modified from the read-only image, the file is saved into the casper-rw image. Changes are tracked between the two images, and any "modified" files are read from the read-write image instead of the read-only image.

You have to be realistic when using a persistent live image - there are limits (don't install new kernels, it's not a good idea to upgrade software due to space constraints). Creating a new user is not one of those limits, however.

---

### Post by plun on 2008-10-27
> **psyke83 said:**
> 

Installing a new kernel? I doubt it'll work correctly. Remember, usb-creator uses syslinux to boot, not grub, and I would imagine most of the startup scripts expect a static kernel.



Must be tested....:)

I have been using [Parted Magic]("http://partedmagic.com/wiki/PartedMagic.php") for a while and I must use SysLinux and Syslinux-common from Debian Exerimental for newest kernels (older version within Ubuntus repo), then it works....  PM starts with around 50MB RAM.  :KS

---

### Post by C.S.Cameron on 2008-10-27
The only thing that keeps me using a FULL install to flash drive and not a U-C install is restricted drivers.

A lot of my stuff don't work without Nvidia drivers, Compiz, Desktop Cube, Dual monitors, SketchUp under wine, probably WOW.

Also I am not sure how to clean Casper-RW, Mine seems to fill up after running update manager a few times, then I can't install anything else.

I think U-C is great, But there are a few things that work with a full install that do not (yet) in U-C

---

### Post by sdowney717 on 2008-10-27
I picked up a 16gb flash drive off ebay, can I simply install ubuntu on it?
Is an install different from usb-creator?

I thought it would be fun to try out.

---

### Post by yelo3 on 2008-10-27
I insalled it in my flash and it works! I only noticed one problem: it's really really slow! it seems I have a 486 processor... Is it so slow in your case?

---

### Post by psyke83 on 2008-10-27
> **sdowney717 said:**
> I picked up a 16gb flash drive off ebay, can I simply install ubuntu on it?
Is an install different from usb-creator?

I thought it would be fun to try out.

Persistent mode is not identical to a proper installation and there are certainly drawbacks. In your case, I'd say a full install (via the normal ubiquity) would suit you better.

---

### Post by Scotty Bones on 2008-10-27
Something that might be worth a try?
Setup your system as you like on your PC; user accounts, settings, packages, updates, kernel, etc. Then, use ReMasterSys to create a live cd backup and use that iso as your image for the USB Startup Disk.

---

### Post by C.S.Cameron on 2008-10-27
Doing a FULL install from Live CD, (or Live USB), using manual partitioning, with root and home partitions formatted using Reiserfs seems to speed thing up on flash drive installs.

---

### Post by sdowney717 on 2008-10-28
do you have to format the thumb drive to reiserfs before using the live cd, or will the partitioner in live cd give you that option?

---

### Post by C.S.Cameron on 2008-10-28
The partitioner on Live CD will give you the reiserfs option if you use manual partitioning.

What works for me when manually partitioning a 4G flash drive is:

I generally reduce the size of the FAT32 partition so I can still use it on a windows machine, FAT32, 100M.
To the right of this I create a Reiserfs* partition with a mount point '/home', Reiserfs, 200M.
To the right of this, an Reiserfs* partition for the file system with a mount point '/', Reiserfs, 3.35G.
To the right of this a swap partition, linux swap, 100M.
With a 16G drive you might want to leave more FAT and allow 5G for root to start.

If required the sizes can be adjusted later with gparted.

---

### Post by Rajan Varadarajan on 2008-10-28
There has been a lot of discussion in this message board about creating a USB Startup disk in 8.10. I have an 3 1/2 year old Toshiba laptop with 512MB RAM. I have a Western Digital Passport USB drive (250GB). I would like to partition that disk and run ubuntu from it. The laptop is running WinXP Pro now and I don't want to touch it since I use it for development.

Question: Can the USB creator utility in 8.10 install a bootable version of ubuntu on the passport drive? So, I can have all my Linux work and OS on the passport drive and carry it with me.

One important note: The laptop does not have a USB bootable option in the BIOS. I tried Wubi with 8.04 but could never get it to work.

Thanks in advance.
Rajan Varadarajan

---

### Post by C.S.Cameron on 2008-10-28
With a laptop that new you should be able to plug it in start the computer to BIOS then select the Passport as first hard drive in Boot, hard disk drives.

I just tried usb-creator with my USB HDD and it does not see it.
However you can install to USB hard disk, using the Live USB, the same as to internal hard disk.

---

### Post by psyke83 on 2008-10-28
> **Rajan Varadarajan said:**
> There has been a lot of discussion in this message board about creating a USB Startup disk in 8.10. I have an 3 1/2 year old Toshiba laptop with 512MB RAM. I have a Western Digital Passport USB drive (250GB). I would like to partition that disk and run ubuntu from it. The laptop is running WinXP Pro now and I don't want to touch it since I use it for development.

Question: Can the USB creator utility in 8.10 install a bootable version of ubuntu on the passport drive? So, I can have all my Linux work and OS on the passport drive and carry it with me.

One important note: The laptop does not have a USB bootable option in the BIOS. I tried Wubi with 8.04 but could never get it to work.

Thanks in advance.
Rajan Varadarajan

Rajan,

I would urge you absolutely **not** to use usb-creator in your case. The purpose of a Live USB image is to allow functionality of the Live CD from a USB key - i.e., it allows people to install Ubuntu from a USB drive to another drive. For example, this is the main use-case for usb-creator: a user wishes to install Ubuntu to their hard drive, but their CD-ROM drive is not functioning.

The persistence feature of of usb-creator is an extra bonus, but it is **not** a replacement for a standard install by any means. It is more suitable for people with a small(ish) USB flash drive (preferably 2gb or more) who wish to casually install a few small applications and save their documents. There are many drawbacks to using a persistent USB image.

You should perform a standard installation (via Ubiquity) to your USB drive - after all, it will be treated as a regular block device. Your only hurdle is to configure your BIOS to boot from removable drives.

EDIT: Be careful when using Ubiquity. It may opt to install GRUB (the bootloader) to your hard disk containing Windows. While this won't remove Windows, it may not be what you want. On the other hand, it will circumvent your booting problem, as the bootloader will be contained on your internal hard disk.

---

### Post by C.S.Cameron on 2008-10-28
If you wish to carry your USB HDD with you DO NOT install your boot loader to your Windows disk as you will only be able to boot Windows when the USB drive is attached.
Also your USB drive will not boot on other computers.

---

### Post by panda726 on 2008-10-29
Actually you can install grub to your internal HDD (and still carry your USB disk), HOWEVER, you MUST create a grub partition to do so, as otherwise, as Cameron said, your computer will be unbootable.  See [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_) for how to do this.

If you do opt to do this (I am not advising one way or the other; merely presenting information), I would suggest installing grub on both your internal disk (to the grub partition you create), and to the USB disk so that you can boot it from other computers.

Tor

---

### Post by bpl07 on 2008-10-29
I just did a full install to a 4GB [rally 2 turbo ocz flash drive]("http://www.zipzoomfly.com/jsp/ProductDetail.jsp?ProductCode=10007936") (Read/Write at 30MB/s).  It boots in 27 seconds, versus the 40 seconds for my normal hard drive install.  I just removed my laptop hard drive during the live cd install so that it wouldn't attempt to install grub on it, and if I want to boot from the flash drive I just choose to boot from usb in my boot list from bios.

This is pretty sweet, I wonder if laptop manufacturers might start using a solid state drive (8-16GB) for essential boot stuff (mounted as /), and a normal hard drive for software and file storage (partitions for /opt and /home)?  That would be pretty sweet.

---

### Post by LMF5000 on 2008-10-29
I have formatted two USB flash drives in my life and in both cases they were ruined permanently - what basically happened was that after the format they would be recognised normally by windows, and I would be able to copy files onto them, but when I remove the drive and re-insert it, all the files on the drive are visible but corrupted (I can read the titles of the files just fine though). Does formatting a USB flash drive ruin it permanently? Has this ever happened to you? I'm asking because I'm reluctant to ruin another flash drive by formatting it before installing ubuntu on it...

---

### Post by inportb on 2008-10-29
After copying files onto the flash disk, do you remember to sync changes ("safely remove") before unplugging it? The only way I have broken Flash storage devices is physically.

---

### Post by C.S.Cameron on 2008-10-29
I think I have bricked a couple flash drives alternately formatting in Windows and gparted.
I do not think Windows likes seeing multiple partitions on a flash drive.
Now I use gparted only, and no hint of a problem, I've formatted one of my current flash drives over 50 times.

bpl07:
You can add something like this at the end of your menu.lst :

# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

Oops, I think that is to boot the second hard drive, to boot the first try:

# on /dev/sda1
title        Microsoft Windows 2000 Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Then you have the option to leave your flash drive plugged in and boot Windows from grub.

---

### Post by panda726 on 2008-10-29
[quote=C.S.Cameron]bpl07:
You can add something like this at the end of your xorg.conf :[/quote]

I believe you meant menu.lst.  One would like to think that folks in the Intrepid forum would be able to handle this kind of error, though.

Tor

---

### Post by boondocks on 2008-10-29
Glad to see that all this discussion.
I have learned so much.

Along the same lines ...

On the "Ubuntu 8.10 (Intrepid Ibex)" download page
you can "Select an image"
if you scroll all the way down,
(after all the CD downloads)
there are 2 images available:

Mobile USB image
.../releases/intrepid/ubuntu-8.10-rc-mobile-i386.img

MID USB image
.../releases/intrepid/ubuntu-8.10-rc-mid-lpia.img


Would either of these be a better choice to install and run off a USB Flash drive?
([COLOR="Blue"]as opposed to the Ubuntu 8.10 Desktop with "Make USB Startup Disk"[/COLOR])

---

### Post by psyke83 on 2008-10-29
> **boondocks said:**
> Glad to see that all this discussion.
I have learned so much.

Along the same lines ...

On the "Ubuntu 8.10 (Intrepid Ibex)" download page
you can "Select an image"
if you scroll all the way down,
(after all the CD downloads)
there are 2 images available:

Mobile USB image
.../releases/intrepid/ubuntu-8.10-rc-mobile-i386.img

MID USB image
.../releases/intrepid/ubuntu-8.10-rc-mid-lpia.img


Would either of these be a better choice to install and run off a USB Flash drive?
([COLOR="Blue"]as opposed to the Ubuntu 8.10 Desktop with "Make USB Startup Disk"[/COLOR])

Not necessarily. Look at the descriptions:

> Mobile USB image

The mobile USB image allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This USB image is optimized for ultra-mobile PCs with screens up to 10". You will need at least 256MB of RAM to install from this image.

> MID USB image

The MID USB image allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This USB image is optimized for handheld devices with 4-7" touchscreens and limited processing power. You will need at least 128MB of RAM to install from this image.

---

### Post by LMF5000 on 2008-10-30
> **inportb said:**
> After copying files onto the flash disk, do you remember to sync changes ("safely remove") before unplugging it? The only way I have broken Flash storage devices is physically.
Yes, I always tell it to "safely remove this hardware". To be exact, I had never extensively tested either of the flash drives before formatting them (they were still brand new) so I don't know whether they were defective to begin with. Perhaps the flash drives cannot support FAT32? I tried formats in FAT32 and NTFS but neither worked, in fact it just kept getting worse with each successive format until finally it wouldn't even format. I tried both the windows formatter and the HP formatting utility.

---

### Post by meganox on 2008-10-30
I want to clean install Intrepid on my laptop HD from a USB stick without burning a CD.  I'm currently running Hardy.  

I figure my choices are:

1. Install U-C from a launchpad .deb or repo - where can I find 1.10?

2. Add Intrepid repos to Hardy and install U-C - which repo?

3. Download and mount Intrepid ISO under Hardy, add CD to sources.list, install U-C - how do you add a cd to sources?

Obvioulsy 1 or 2 would be simplest.

The stick is a 4GB Sandisk that's had only light use, possibly not currently bootable though, do I just format it with gparted or do I have to install syslinux myself?

Edit: Also, while I'm here, if I want to encrypt partitions during install, do I need the Alternate CD?  Is U-C ok with the Alternate CD?

Thanks.

---

### Post by snowpine on 2008-10-30
> **meganox said:**
> I want to clean install Intrepid on my laptop HD from a USB stick without burning a CD.  I'm currently running Hardy.  

I figure my choices are:

1. Install U-C from a launchpad .deb or repo - where can I find 1.10?

2. Add Intrepid repos to Hardy and install U-C - which repo?

3. Download and mount Intrepid ISO under Hardy, add CD to sources.list, install U-C - how do you add a cd to sources?

Obvioulsy 1 or 2 would be simplest.

The stick is a 4GB Sandisk that's had only light use, possibly not currently bootable though, do I just format it with gparted or do I have to install syslinux myself?

Edit: Also, while I'm here, if I want to encrypt partitions during install, do I need the Alternate CD?  Is U-C ok with the Alternate CD?

Thanks.

I installed Intrepid on my eee PC last night using a USB stick I created with Unetbootin. It was very easy and I would highly recommend Unetbootin. :)

Sorry, but I don't know the answer to your question about encrypted partitions.

---

### Post by C.S.Cameron on 2008-10-30
U-C is included in the 8.10 Live CD and will install 8.10 to USB right off the CD.

U-C can be downloaded for use with earlier versions here:
[https://launchpad.net/ubuntu/intrepid/+source/usb-creator](https://launchpad.net/ubuntu/intrepid/+source/usb-creator)

U-C will not make a persistent install of 8.04 due to a flaw in Casper with that version.

U-C automatically does all the formatting required to make a Live USB.

I have not had any luck modifying the system partition after a U-C install.

Unibootin makes a live USB just fine however it is not persistent.

note: U-C can be installed on a 1G flash drive which can be cloned to a 4G flash drive leaving 3G free.
This space can be formatted to two ext3 partitions named casper-rw and home-rw.
On boot the U-C flash drive will default to using these partitions for persistence if the casper-rw file in the U-C created system is deleted.
(home-rw partition will work any way).

I think the flash can be formatted to FAT32/ext3/ext3 prior to using U-C, however I have not been able to get U-C to install to a 4G Kingston.

---

### Post by meganox on 2008-10-30
> **C.S.Cameron said:**
> 
U-C is included in the 8.10 Live CD and will install 8.10 to USB right off the CD.


No good, I can't burn a CD :)

> **C.S.Cameron said:**
> 
U-C can be downloaded for use with earlier versions here:
[https://launchpad.net/ubuntu/intrepid/+source/usb-creator](https://launchpad.net/ubuntu/intrepid/+source/usb-creator)
 

This is the source, I was hoping for a .deb, can't find one newer than 1.7 :confused:

> **C.S.Cameron said:**
> 
U-C will not make a persistent install of 8.04 due to a flaw in Casper with that version.
 

No problem, I don't need persistence just to install Intrepid from USB ;)

> **C.S.Cameron said:**
> 
U-C automatically does all the formatting required to make a Live USB.
 

cool, I read a bug somewhere where it wasn't but I don't know how old it was 

> **C.S.Cameron said:**
> 
note: U-C can be installed on a 1G flash drive which can be cloned to a 4G flash drive leaving 3G free.
This space can be formatted to two ext3 partitions named casper-rw and home-rw.
On boot the U-C flash drive will default to using these partitions for persistence if the casper-rw file in the U-C created system is deleted.
(home-rw partition will work any way).

I think the flash can be formatted to FAT32/ext3/ext3 prior to using U-C, however I have not been able to get U-C to install to a 4G Kingston.


Yeah, I was worried about a bug report I read that said you can't install onto anything bigger than 1GB, again I wasn't sure if it was old.  This doesn't look good for me installing Intrepid today, I only have a 4GB stick and no working CD burner  :(

Guess I will try pre-partitioning.  Thanks!

---

### Post by C.S.Cameron on 2008-10-30
Try this page:
[https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.10](https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.10)

You should be able to download the 8.10 iso to desktop start U-C and make your bootable USB from there.

---

