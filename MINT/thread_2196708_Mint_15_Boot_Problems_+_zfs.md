---
title: "Mint 15 Boot Problems + zfs"
date: 2013-12-31
forum: MINT
---

### Post by weston260 on 2013-12-31
Hi guys/gals. 

I come here out of desperation to try and solve a probably basic problem i've ran into. 

I have a computer that i use as a nas for streaming videos in my house, and it stopped functioning properly out of the blue. I was using zfs for a raidz-2 array and the zfs apparently stopped working. My hard drives are all functional, but no data appears in the zfs folder, and any zfs commands in the terminal result in nothing. I will run a zfs command and it never completes, whenever I exit out of that terminal i get a message that a process is still running. 

This led me to my second problem. After trying to fix the computer through a remote connection to no avail, I hooked it up to a monitor and was greeted with a blank screen with only a "_" underscore after I choose my OS in the grub 2 menu. Choosing my OS in the grub 2 menu seemed to have locked my computer into some kind of loop, so I made a liveboot usb stick of ubuntu and booted into it to use boot-repair. In the past boot-repair worked for me without any problems, but I ran it twice and it got me nowhere. After the boot-repair recommended operation, it takes me to a grub command line and my usb stick that my OS is installed to doesn't show up for uefi booting in the boot menu. 

I would like to get my computer functioning again and hopefully get my data off the zfs array if it's not too late.
Here is the paste of the info from boot-repair: paste.ubuntu.com/6661490

Thanks in advance to anyone that helps. 

My computer config:
 AMD 5800k using proprietary amd beta driver
16 GB Ram
                             gigabyte motherboard
                             8x Seagate 3TB hard drive zfs raidz-2
                             32GB Sandisk extreme USB 3.0 drive (OS is installed here)

---

### Post by tgalati4 on 2013-12-31
So, if I understand correctly, you were running the operating system from a USB drive?  If you didn't take precautions for running completely in RAM, then your log files and temporary files will get dumped onto the flash drive, which will shorten its life.  It looks like your flash drive failed which locked up your server.  The zfs raid is probably OK, but you will need to create another OS flash drive to boot--use a new flash drive, not a used one.  Boot repair would  not fix this problem.

---

### Post by weston260 on 2013-12-31
> **tgalati4 said:**
> So, if I understand correctly, you were running the operating system from a USB drive?  If you didn't take precautions for running completely in RAM, then your log files and temporary files will get dumped onto the flash drive, which will shorten its life.  It looks like your flash drive failed which locked up your server.  The zfs raid is probably OK, but you will need to create another OS flash drive to boot--use a new flash drive, not a used one.  Boot repair would  not fix this problem.
I wasn't using a swap file cause I had 16GB of RAM. Last thing I did on the computer was transfer over about 500GB of data and turn it off through the terminal. 

The computer was running fine through the remote connection. I know flash drives and ssds default to read  only status when they degrade, but I've only been using the usb since june/july, so I don't see how it could die so fast. Anyway I could test the drive?

---

### Post by tgalati4 on 2013-12-31
Six months is about right.  You can't really run an operating system from a flash drive.  You can't.  You can load an operating system from flash drive and run in RAM, but you can't hit a flash drive with a lot of writes and expect it to last.  You can't.  In linux every device is a file and gets written to frequently.  Swap or no swap, a flash drive will die when running directly from it.  No way around it.  Ubuntu Live USB is different.  It loads the OS and runs from RAM only.  Loading the OS onto a flash drive and running it from there is not recommended.

A Haiku

Running from flash drive?
Lots of writes destroy the drive.
Short life expected.

You can test the drive by putting it on another linux machine and running *badblocks* on it.  That will only test read performance.  You would have to risk the OS on it by doing non-destructive write tests, but my guess is that the controller is having problems with too many relocated sectors.  The disk could be OK for simple data storage--after a clean wipe, but it is probably not suited to OS use.

---

### Post by weston260 on 2013-12-31
I knew it had a limited lifespan, but I didn't think it would be so short lived. :frown:

i'm trying to use badblocks now, but I get told the device is in use by the sytem and it's not safe to run badblocks. After I eject the usb I get "No such file or directory while trying to determine the device size" 

I was trying the command sudo badblocks -nsv /dev/sdj

---

### Post by tgalati4 on 2014-01-01
The drive needs to show up using:

```
sudo fdisk -l
```

You cannot touch the drive with the file manager--because then it gets mounted.  Just run the test and see what comes up.  My guess is that it is toast.  Flash drives (especially the big ones) are designed for digital camera use--write once, read many.  The controller will move the writes around to spread out the wear and that works OK for photos because they are big and don't move around.  But when using it for an OS, there are thousands of small files (look in /proc) that are constantly being updated every second and the controller quickly gets overwhelmed.

Your best bet is to format it in a camera (clean wipe, FAT32) and just use it for simple storage or monthly backup files.  To recover your zfs pool, create a *freenas* USB stick.  It is designed to run in RAM and store configuration in a few files that get written back to the USB stick only when you "backup" the configuration.  Mount the zfs drives and you should be able to see your data.

---

### Post by weston260 on 2014-01-01
it shows up in fdisk and gparted, I can copy files from it. 

I think i'll just try to install freenas and recover my zpool from there. I was going to do that originally, but wanted to try out some other things in linux also.

---

### Post by weston260 on 2014-01-01
How exactly do i mount the zpool? I've tried importing on freenas and mfsBSD with -f switch and it crashes the OS. I'm going to try some other stuff out to see if it works.

---

### Post by tgalati4 on 2014-01-02
You have to create a zfs volume and then mount it:  [http://doc.freenas.org/index.php/Volumes](http://doc.freenas.org/index.php/Volumes)

---

### Post by weston260 on 2014-01-03
could you be more specific? Wouldn't creating a new volume destroy my old one? i get fatal trap 12 page fault error when I try to import it. 

I'm going to try running memtest and then see if the freenas forums can help me. no offense to anyone here. 

Thanks for the replies tgalati

---

### Post by tgalati4 on 2014-01-03
Make sure you are using the same version of ZFS on both the zpool and on freenas.  My understanding is you create the volumes (which makes the mount points) then you mount them using the existing devices.  There may be differences between the how Ubuntu stripes the zpool and how freenas does it, so these zpools may not be swappable between the two operating systems.  For that you will have to ask around.

The alternative is to boot an Ubuntu Live USB or DVD and load *zfs-fuse* and try to mount the zpools and check their status.  Don't reboot, because you will loose* zfs-fuse*.  Be prepared to make a backup of critical data.  Or, buy a small SSD drive and put a new Ubuntu install on that and try to reattach your zpools.

---

