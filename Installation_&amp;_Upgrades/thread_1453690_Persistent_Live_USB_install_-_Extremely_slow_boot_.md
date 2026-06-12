---
title: "Persistent Live USB install - Extremely slow boot time"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by macplaxton on 2010-04-13
Hi, I've spent the last 3 days solid trying to get a USB stick to work the way I want it and have run out of ideas.

The object of the exercise is to have a Live USB bootable stick running Ubuntu 9.10, but it also needs to be persistent.

I've tried a few different ways of running it.

1) From a ISO image burnt to a CD for a Live version - works fine, takes a couple of minutes to boot, but obviously no persistence.

2) Installing to 4GB FAT USB stick using the USB installer option after loading Live CD - again works fine, prompts for language just like the CD and boots in around a minute, again no persistence. Same method, but using the slider to use the spare space on the stick as a persistence file - works, but takes 8 minutes to boot. 

3) Partitioning a 4GB USB stick in a variety of ways. All boot okay to Live version. Add in persistence and the boot time shoots up from less than a minute to 8 minutes.

As well as trying option 2), my preferred arrangement is to have the 4GB partitioned as 3x ext2: 1GB boot "ubuntu_0910", 1GB "casper-rw" for persistence, 2GB "storage" for everything else. After getting my head around setting up the boot loader (EXTLINUX) and configuring the the boot options correctly, I still have the same issue. Fast boot Live / Slow boot live with persistence.

Removing 'splash' and 'quiet' and I can see at what stages in the boot it stalls.

Without "cdrom-detect/try-usb=true", Live will take 8 minutes to boot. It spends 7 minutes of that in a "no medium found" merry-go-round not being able to open various devices and waiting for nothing. Then it eventually loads.

Adding in "cdrom-detect/try-usb=true", Live will take less than a minute to boot, as although it flags up 16 lines of "no medium found" for my two optical drives sr0/sr1, it ignores them and cracks on with booting up.

The problem I have is that when I add the magic word "persistent" into the boot options, it spends 7 minutes dithering again in a "no medium found" state, before giving up and magically finding what it's spent the last 7 minutes looking for on the USB stick.

Is there a precise order to the boot options? Or is there one missing I could use to sort this out? Currently I've got:

kernel /casper/vmlinuz
append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz cdrom-detect/try-usb=true --

time taken = 39 seconds (from the log).

kernel /casper/vmlinuz
append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz  cdrom-detect/try-usb=true persistent --

470 seconds.

Adding "floppy=off", "live-media-path=/casper/" and "ignore_uuid" made no difference.

I've drawn the conclusion that either I'm doing something wrong, or there's a bug.

Any suggestions most welcome,
Rich

---

### Post by Kismet on 2010-05-05
I too have seen this, and am curious if there is a solution. 

USB boots take forever on my system.

---

### Post by efflandt on 2010-05-05
Does the USB stick by any chance have U3?  That is a pseudo cdrom device that ends up as an sr device.  And that can significantly bog down boot time.

64-bit 10.04 LTS iso on USB does seem significantly slower for me than 64-bit 9.10.  About 2:45 to language prompt and 4:40 total from On to X.  But this was with a 4 GB PNY stick (1.1 GB persistent file) on an early Athlon64 3200+ (2 GHz single core, 2 GB RAM).  The longest lag in dmesg was about 48 seconds between polling an empty fd0 and finding and setting up swap.

I seem to remember 9.10 booting from assorted devices, a faster 4 GB HP stick, or SD or microSD in a card reader, in not much over a minute.  A Sandisk mini-Cruzer with U3 took more than twice as long (over 2 minutes).  But that testing was on a somewhat faster 1.66 MHz dual core laptop w/1 GB RAM.

---

### Post by macplaxton on 2010-05-05
After trying various things and taking a break, I did find the workaround.

My problem was like [THIS]("http://ubuntuforums.org/showpost.php?p=8839154&postcount=7") one.

Most of the time the system was hanging around looking for fd0, the floppy drive, and instead of skipping over it, sat there for 7 out of the 8 minutes. Had to disable the floppy drive in the BIOS as a workaround. I'd rather not have to do that, but I left it at that to get on with things.

From memory, without the "quiet" & "splash" boot options, the boot stalled on a line like "/init: line 1: can't open /dev/fd0: No Medium found" only ever did it with "persistent" boot option

---

### Post by wilee-nilee on 2010-05-05
A ISO loaded on a thumb will never give you lightning boots, it is only running faster then a CD because it is a ssd.

---

### Post by dydzej on 2010-11-17
Same bug.
Loading of locales takes a lot of time. Then the screen with choose of Try/install shows. After pushing the Try button, it takes five or more minutes to start logscreen. After that everything works yust fine. 
Presistent Live USB is absolutly unusable.

//Ubuntu 10.10
//Netbook Lenovo S12 ION

---

### Post by C.S.Cameron on 2010-11-18
Boot times usually get a little faster after the drive has booted a few times.

---

