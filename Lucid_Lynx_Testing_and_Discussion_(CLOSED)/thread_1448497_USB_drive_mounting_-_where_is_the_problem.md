---
title: "USB drive mounting - where is the problem?"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2010-04-06
Hello All

I'm seeing problems with mounting usb drives and external hard drives on Lucid at present (vfat and ntfs).

One installation is a 'stock' full Gnome desktop one running 2.6.32-19-generic kernel on a t42 think pad. It was installed from an alpha 3 CD and then updated regularly

The other is a 'minimal' one, installed from the Beta 1 alternate cd with just the base system, xorg, openbox and usbmount for automounting of usb drives at command line. Installed last night and updated through today.

In the case of the 'stock' installation, a usb stick is recognised and appears in the 'places' menu. Read and write is fine. Can't unmount it, I have to use sudo umount /media/whatever-weird-number-it-was-given. Eject does not.

See [http://ubuntuforums.org/showthread.php?t=1435899&highlight=mounting+usb+drives](http://ubuntuforums.org/showthread.php?t=1435899&highlight=mounting+usb+drives)

I have rebooted.

In the case of the bare bones system, USB stick is recognised, and I can ls and list files from the ordinary user account, but I need to add lines to fstab to get it to mount and be writable by ordinary user. Again, I have to sudo umount /media/something-sensible-I-chose to unmount the drive. See 

[http://ubuntuforums.org/showthread.php?t=1448092](http://ubuntuforums.org/showthread.php?t=1448092)

Has anyone any definite information on what is going on with this and how to begin to track down what is quite a major bug? The two machines are quite different as regards hardware(Centrino laptop, AMD dual core desktop), and the Ubuntu set up being used. I'll have some time for some research and reading tomorrow evening and I'd like to *understand* this one.

I haven't seen too many posts on this so I'm assuming most people are not seeing this (or have 50Gb Ubuntu One accounts :evil:)

---

### Post by cariboo on 2010-04-06
Do your thumb drives still have U3 installed? Before I removed if from the last devices I got, they would always mount as a CD and and a 4Gb filesystem.

---

### Post by keithpeter on 2010-04-06
> **cariboo907 said:**
> Do your thumb drives still have U3 installed? Before I removed if from the last devices I got, they would always mount as a CD and and a 4Gb filesystem.

Good idea to check, but no, the one drive I formatted today on a windows laptop, just 2Gb of blank vfat :).

I've had similar issues with a 250Gb usb external hard drive. That was NTFS formatted, and I had to use a sudo ntfs-3g command to mount it.

I'm in testing mode here and just trying to track down what this is, and why so few people appear to be seeing this...

---

### Post by wkulecz on 2010-04-06
FAT32 USB memory stick mounted and worked as expected for me.  My external USB drive formatted ext3 also mounted and unmounted as a normal user.  I had write access where the userID matched my 10.04beta userID.  This appears to fix an issues I'd been having in 9.10 where the external drive was mounting read-only and was only really usable if I did su -i.

So far, no USB drive mounting issues for me, but your post prompted me to test it. I'm more concerned with will the development tools I need be ready at release, some are still missing but they are starting to appear in Software Center, just no "install" button yet.

---

### Post by cariboo on 2010-04-06
I just tried most of my external devices, 2x4Gb thumb drive, 3X1Gb thumb drive 1 8Gb thumb drive, 1 80Gb ext4 external hard drive and 1 120Gb NTFS external hard drive. All worked without a hitch, the only thing I noticed is nautilus doesn't open automagically when the ntfs drive is plugged in, with all the other devices, it did.

---

### Post by keithpeter on 2010-04-06
> **wkulecz said:**
> I had write access where the userID matched my 10.04beta userID.  This appears to fix an issues I'd been having in 9.10 where the external drive was mounting read-only and was only really usable if I did su -i.

I've never seen that on 9.10, everything just worked ok, at least on a stock Ubuntu (Gnome &c) installation. How do I find the userID for a freshly formatted vfat32 2Gb USB drive? Where does it get one from? Just trying to understand.

---

### Post by keithpeter on 2010-04-06
> **cariboo907 said:**
> I just tried most of my external devices, 2x4Gb thumb drive, 3X1Gb thumb drive 1 8Gb thumb drive, 1 80Gb ext4 external hard drive and 1 120Gb NTFS external hard drive. All worked without a hitch, the only thing I noticed is nautilus doesn't open automagically when the ntfs drive is plugged in, with all the other devices, it did.

OK, I'll try a fresh install of the stock Ubuntu from a Beta 2 iso tomorrow evening and see what happens...

---

### Post by psyke83 on 2010-04-06
I'm also having this problem when plugging in an external drive via USB. If you manually modprobe "usb-storage", your drive should be recognised - that's how I got it working, at least.

---

### Post by keithpeter on 2010-04-07
> **psyke83 said:**
> I'm also having this problem when plugging in an external drive via USB. If you manually modprobe "usb-storage", your drive should be recognised - that's how I got it working, at least.

Thanks very much psyke83, that works for my 'bare bones' install in the sense that with the usb-storage module loaded, the sticks are automatically mounted to /media/usb0, /media/usb1 &c. I've removed the lines from fstab that I was using so that I could back up work &c. **OH no, the problem is back again. Still getting permission errors after a reboot and modprobe.**

I still can't unmount them from the user account, I still have to use sudo umount /media/usb0 and so on. In that sense, I now have the same issue on both the stock Ubuntu install and the bare bones: can't release or eject storage sticks from the user account.

I've noticed a number of other people have this same issue, so I'm checking launchpad for bugs.

---

### Post by dino99 on 2010-04-07
> **keithpeter said:**
> Thanks very much psyke83, that works for my 'bare bones' install in the sense that with the usb-storage module loaded, the sticks are automatically mounted to /media/usb0, /media/usb1 &c. I've removed the lines from fstab that I was using so that I could back up work &c. **OH no, the problem is back again. Still getting permission errors after a reboot and modprobe.**

I still can't unmount them from the user account, I still have to use sudo umount /media/usb0 and so on. In that sense, I now have the same issue on both the stock Ubuntu install and the bare bones: can't release or eject storage sticks from the user account.

I've noticed a number of other people have this same issue, so I'm checking launchpad for bugs.

maybe you can try mountmanager rights

---

### Post by keithpeter on 2010-04-07
> **dino99 said:**
> maybe you can try mountmanager rights

I just tried it on the T42. No change, still can't unmount a usb stick except by using sudo. 

What I'm trying to get my head around is what is causing the change in default behaviour from previous versions, why only some people are seeing the 'can't unmount' problem and what can be done to stock Ubuntu 10.04 to correct the issue

Thanks.

---

### Post by psyke83 on 2010-04-07
You shouldn't need to manually mount via sudo.

As a temporary workaround, add the usb-storage module to your /etc/modules.conf file. Afterwards, any drives you insert should be auto-mounted as per the previous behaviour...

---

### Post by keithpeter on 2010-04-07
> **psyke83 said:**
> You shouldn't need to manually mount via sudo.

As a temporary workaround, add the usb-storage module to your /etc/modules.conf file. Afterwards, any drives you insert should be auto-mounted as per the previous behaviour...

Hello psyke83

They mount ok, just read only for the normal user. To write to the drive or to **umount** it I have to become root. This is with a 'bare bones' install (cli + xorg + openbox + usbmount which has pmount as dependency).

The stock ubuntu install automounts ok but won't umount without becoming root.

---

