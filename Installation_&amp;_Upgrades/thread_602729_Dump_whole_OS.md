---
title: "Dump whole OS ?"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by WardLoockx on 2007-11-04
Is it possible to dump my whole System into a file or image so I can restore it later when something fails? I'm just running Kubuntu no windows or anything? I'll probably will need to do partitioning myself?

Greets

---

### Post by drratchet on 2007-11-05
Of course!

This looks like  a good guide to easy backup and restore:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Another thing you can do, if you are feeling courageous (and are willing to do something tricky), is make an image of your entire disk. Doing this requires some knowledge of how Linux works with things like disks. You will also need someplace to put the image, like a second disk, as an image of a disk tends to be as big as the disk itself.

In Linux, as in all unix-style OS's, all the hardware can be accessed as if it is a file. That means you can copy the contents somewhere else, just like any file. These "special files" that are really hardware devices all live in the directory "/dev".

So, let's say you have an external USB hard drive plugged in and mounted at /media/usbdisk, and you want to image your first internal drive. You can access the entire first internal drive as /dev/hda (or, if it's SATA or SCSI, as /dev/sda). And you can pretend that /dev/hda is just a file, even though it's actually the whole disk, so if you do this:

sudo cat /dev/hda > /media/usbdisk/disk-image

You will end up with (after some time) a complete and perfect image file of your hard disk.

To restore it, boot a live CD (like the Ubuntu desktop CD) and mount the USB drive, and do this:

sudo cat /media/usbdisk/disk-image > /dev/hda

This will restore everything, boot sector, partition table, everything.

As the disk image will be very big (as big as the disk itself!) make sure you have enough room on your usb disk. Also, I usually compress the image as I create it, like this:

sudo cat /dev/hda | gzip > /media/usbdisk/disk-image.gz

And to decompress it as I restore:

sudo cat /media/usbdisk/disk-image.gz | gunzip > /dev/hda

BTW don't try to just "cp /dev/hda /media/usbdisk/disk-image", because cp will just copy the "special file", and not the data *inside* the file. It's the data in the special file (which is the data on the disk) that we want.

As with everything, it is best to do this stuff with understanding, rather than just by wrote. If you don't know much about the "/dev" filesystem, it's best to read up on it a little before you try this.

---

### Post by louieb on 2007-11-05
partimage will do it on a partition by partition basis. I use the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") to run it. Theres a good tutorial on how to use  it on [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")

---

