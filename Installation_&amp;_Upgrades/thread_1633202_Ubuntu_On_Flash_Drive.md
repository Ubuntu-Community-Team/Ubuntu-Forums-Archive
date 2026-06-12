---
title: "Ubuntu On Flash Drive"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Tanner2007 on 2010-11-29
How could I install and run Ubuntu on a flash drive?
   *by that I mean have it so I can **RUN** Ubuntu off of the flash drive on any PC it is plugged into.*

Thank you, 

-Tanner Summers-

---

### Post by beew on 2010-11-29
Check out this thread for C.S.Cameron's tutorial.

[http://ubuntuforums.org/showthread.php?t=1632887](http://ubuntuforums.org/showthread.php?t=1632887)

You don't need the fat32/ntfs partition unless you want Windows to access data in your flash drive (I never see any need of that as Linux can access Windows file systems and if you are using a flash drive you won't be storing any data anyway) Also for a flash drive (8G?) there is no need for /home either. Format the drive to be ext3 or ext4 and make it your boot partition and then save maybe 1 G of memory for swap and that would be it.

Installations in usb flash drives may be slow (depends of course too on what computer you plug the usb into), an external hard drive would be much better performance wise.[URL="http://ubuntuforums.org/showthread.php?t=1632887"]
[/URL]

---

### Post by C.S.Cameron on 2010-11-29
> **Tanner2007 said:**
> How could I install and run Ubuntu on a flash drive?
   *by that I mean have it so I can **RUN** Ubuntu off of the flash drive on any PC it is plugged into.*

Thank you, 

-Tanner Summers-

Hey, I was raised up in Riverside!

Another alternative is a persistent install, which is good on a smaller drive as it uses a compressed O/S.

Usb-creator from the Live CD or Universal from PendriveLinux.com will make one of these.
Unetbootin also works but needs tweeking to make it persistent.

---

### Post by Tanner2007 on 2010-12-05
> **beew said:**
> Check out this thread for C.S.Cameron's tutorial.

[http://ubuntuforums.org/showthread.php?t=1632887](http://ubuntuforums.org/showthread.php?t=1632887)

You don't need the fat32/ntfs partition unless you want Windows to access data in your flash drive (I never see any need of that as Linux can access Windows file systems and if you are using a flash drive you won't be storing any data anyway) Also for a flash drive (8G?) there is no need for /home either. Format the drive to be ext3 or ext4 and make it your boot partition and then save maybe 1 G of memory for swap and that would be it.

Installations in usb flash drives may be slow (depends of course too on what computer you plug the usb into), an external hard drive would be much better performance wise.[URL="http://ubuntuforums.org/showthread.php?t=1632887"]
[/URL]

Thank you i will check this out when I have time today, cheers.


> **C.S.Cameron said:**
> Hey, I was raised up in Riverside!

Another alternative is a persistent install, which is good on a smaller drive as it uses a compressed O/S.

Usb-creator from the Live CD or Universal from PendriveLinux.com will make one of these.
Unetbootin also works but needs tweeking to make it persistent.

Haha thats coool bro, anyways ill try that way aswell,


like I said basically I just want to have linux on a flash drive so I COULD RUN it on another computer not INSTALL =] I really want ubuntu.....also sorry for the long wait on my reply

---

### Post by efflandt on 2010-12-05
Actually for regular install to usb stick or SD in a card reader, etc. ext2 file system may be best.  It is basically ext3 without journaling, so it reduces the amount of writes to flash.  That should be no problem as long as you do not unplug it (or power) while writing to it (which could corrupt any file system).

You probably want to stick with default video drivers, unless you want  to temporarily install proprietary drivers for a particular PC.  One advantage of regular install vs. iso on USB, is that you "can" install video drivers on a regular install (cannot on iso).

So I would just make one ext2 partition for / and no swap (unless running on memory impaired computers).  Then in /etc/fstab set add noatime option for the USB partition and tmpfs for /tmp (which is cleared on reboot anyway) to avoid writing small temporary files to flash:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=14d80882-07f4-4f4a-a1f4-6ad1543d8779 /    ext2    errors=remount-ro**,noatime** 0       1
**tmpfs    /tmp    tmpfs    defaults    0    0**
```That is basically what I had set up on 8 GB USB stick until natty development got stable enough that I installed it on SSD (solid state drive).  I actually set the SSD up similarly, but using ext4 with journaling disabled and another option to enable trim, but some of those things are unnecessary for a USB stick (which does not have trim).

---

### Post by Tanner2007 on 2010-12-18
Well sorry for long post, internet got cut off for a while, im try the first one soon but so far the idea C.S.Cameron game me only made it so i can install from flash drive well anyone else got other guides? my flash drive is 4gb I just want to be able to plug in and run =]

---

### Post by garvinrick4 on 2010-12-18
## For a 4 gig flash drive:
With a 4 gig flash drive I would say use the startup disk creator in Ubuntu and set for 4 gig of persistance. 
Is more or less a large Live USB that you can install your repositories and get your ubuntu-restricted-extras 
a media player of choice, your panels set up and settings and just leave it that way. Has a seperate boot that 
does not use mbr so just choose flash drive in BIOS and you are cool. Will hold all changes (persistence) up to 
the size of your 4 gig flash so why do a install when Live USB is just as good for 4 gig. Once set up just turn off updates
in software sources and leave it be. If interested about the install google squashfs and casper. 
I imagine all you want it to do is work and this does that.

---

### Post by C.S.Cameron on 2010-12-18
Universal or Startup Disk Creator should have given you an option for persistence.
Startup Disk Creator f5om the live CD calls it "Stored in reserved extra space"

You can do a Full install to a flash drive just like to internal HDD.
Unplug your internal HDD plug in your flash drive and b0oot he Live CD and do an install.


If you can't unplug your internal HDD I can give further instructions.

---

