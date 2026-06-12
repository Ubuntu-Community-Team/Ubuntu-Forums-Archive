---
title: "broken fstab - cant save fix!!"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by pwhalley on 2009-12-02
Greetings all:

I have a problem with a 9.10 WUBI install on an Win7 ACER AR3610 nettop - these have no optical drive.  I don't think I have an SD card large enough to do any kind of install to. I have no other removable media or fixed drive that I can boot from via esata or usb. The unit is connected to my network and is running at 1G.

The source of the problem is that I edited an error into the fstab file.  Boot now drops to a recovery shell root@ubuntu.  I am able to edit the fstab but cannot save with a "file system is read only" error. EG "sudo nano /etc/fstab"

I have tried reading the root.disk file using explore2fs without success on the win7 os.  I copied the file to an xp machine and tried using explore2fs there to access files inside with same results.

How can I:
[LIST] Change the file system to RW when I am in the recovery shell?
[LIST]Open edit and re-write the file on the windows side?
[LIST]Another option would be to rename the broken file and put back the original.  Any option will do.
[/LIST][/LIST][/LIST]

This would save me at least a day (probably more) of work re-installing everything.

P.S.  I also tried "mount -n -o remount,rw /" as I found elsewhere and received "mount:mount point does not exist".   

I was sooo close...

Thanks for your time.

Peter

---

### Post by sisco311 on 2009-12-02
try to remount the root partition:
```
sudo mount -o remount,rw /
```

---

### Post by pwhalley on 2009-12-02
Thanks sisco311,

I already tried that.  Your post apparently crossed my edit to the original post.

If there is any hope, it may lie in  'loop' but I have no idea how this works.  

When I guessed and tried "mount -n -o loop,rw /  the response is "/: is a directory" at least that seems like a little progress to me - the ignorant!

I suppose I could come up with a sd card big enough but I don't want to spend the coin till I am certian that I can make such an install read and write to the files in the root.disk file that contains ubuntu.
 
Any further input would be appreciated!

Peter

---

### Post by pwhalley on 2009-12-03
OK for the sake of others as green as myself..

I went [[COLOR="DeepSkyBlue"]here[/COLOR]]("http://www.pendrivelinux.com/install-rip-linux-to-usb-from-windows/#more-3138") and downloaded RIPLlinux (9.3).  It was small enough to load on a 1G USB stick.  I haven't checked how much extra space there is (if any).  Neither have I checked out how well x or networking capabilities are...
I downloaded and installed to USB stick on another PC but that should not be necessary as long as your Win7 install isn't broken - it wasn't in my case.

I then rebooted the '3610 with the broken wubi install.   Remember to enable boot from usb and put before your HD in cmos setup first (I leave this enabled for convenience sake). Select "boot linux system! (64 bit kernel)" during the boot phase.  Upon completion of boot you are root (no need to prefix commands with sudo).

I then followed the directions found [[COLOR="MediumTurquoise"]here[/COLOR]]("http://neosmart.net/forums/showthread.php?t=5004").

Credit goes to the link but this is the essence:

```
fdisk -l
```
This command lists disk devices.  For the ACER AR3610 you will see at least 3 partitions.  The first contains the recovery data to restore to factory default, the second (bootable) contains the stuff to manage the windows 7 boot process and the third has all the windows 7 stuff you know and can't yet bear to part with!  The third is the only one of concern here.

Prepare a place to mount the windows file system.
```
mkdir /win
```

Mount that third partition (windows) there.
```
mount /dev/sda3 /win
```

Prepare a place to mount the virtual file system contained in root.disk file on the windows partition you just mounted.
```
mkdir /vdisk
```

Mount the virtual disk/file system at /vdisk.
```
mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

From this point you can access any files in the virtual drive and rename, edit etc. as root.

All I needed to do was edit fstab to remove an errant / at the end of the file, save, reboot normally (without usb stick) selecting ubuntu.
```
nano /vdisk/etc/fstab
```
"make changes"
save and exit nano
```
reboot
```

I could have renamed the bad fstab as badfstab (or deleted) and put back the backup copy but I still needed to work on the other entries...

It took me as long to write this as it did to download RIP put it on a stick, boot, edit the file, save and reboot.

The key to the whole thing was the way you need to mount the virtual file system that is the root.disk file.  You might be able to use this mount command if you copied the root.disk file to another linux machine from the windows side but the way I did it was a lot easier faster and I think safer.  Hope this helps someone in the long run and yes, I will very soon (I hope) moving this system entirely to Ubuntu.  I just need to find a good way to copy that first partition completely to somewhere else on my network in case I need it....  suggestions welcome.

Peter

---

### Post by sisco311 on 2009-12-03
Cool! I'm glad you solved your problem and thanks for posting the solution as well.

I don't use Windows, but it's good to know that you can mount the Wubi image as loop device. 

With Best Regards,
sisco311.

---

