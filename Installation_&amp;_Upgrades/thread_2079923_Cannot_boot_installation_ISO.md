---
title: "Cannot boot installation ISO"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by wyclif on 2012-11-02
For some mysterious reason, I cannot upgrade my old Jaunty system to the newest LTS, or even 10.04.4 LTS. 

I'm doing this on an older box with an Adaptec 29160 SCSI card. The SCSI card is in slot 3 of the motherboard. There are two devices terminated or chained on the SCSI interface: the HDD is device #0, and the CD-ROM drive is device #3.

I thought this would be easy, as the CD-ROM drive is in good working order.

I can't upgrade the system over the network anymore via apt-get or Update Manager, because Jaunty is no longer supported :(

1. I burn the Ubuntu 10.04.4 LTS iso. On startup, I enter the system BIOS and change the boot order so that the CD-ROM boots first, then restart. I get an error during post: "DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER." But the disk is already in the drive, and when I press "Enter", I get a blank screen with a blinking cursor in the upper left hand corner of the screen.

2. I wonder if I can change the boot order in the SCSI BIOS. So I reboot and press CTRL-A to access the SCSI BIOS, and change the first device in the boot order from "0" to "3" (the device number for the CD-ROM drive). Restart, but the disk doesn't spin up and I get the same error, "DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER."

I'm at my wit's end. I thought this would be simple, and I know the drive works because I installed Jaunty via CD. 

What am I doing wrong?

---

### Post by Bashing-om on 2012-11-02
hi ! wyclif !

Sounds to me like a bad cd... did you check the MD5sum ??

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)[INDENT]Just try'n to help <== BDQ

[/INDENT]

---

### Post by wyclif on 2012-11-02
Thanks, but I was careful to verify the checksum. 

When I navigate (via the file browser) to "computer:///" and click on "CD-ROM drive" the system tells me "Unable to mount location, no media in the drive" even though the install CD is in the drive.

---

### Post by wyclif on 2012-11-02
Here's some relevant output from the command line:

$ sudo mount /media/cdrom
mount: no media found on /dev/sr0

$ sudo umount /media/cdrom
umount: media/cdrom: not mounted

$ sudo mount /dev/sda0 /media/cdrom
mount: special device /dev/sda0 does not exist

$ sudo mount /dev/scd0 /media/cdrom
mount: /dev/sr0: unknown device

$ ls -l /dev/sr0 /dev/scd0
lrwxrwxrwx 1 root root         3 2012-11-02 22:23 /dev/scd0 -> sr0
brw-rw---- 1 root cdrom 11,    0 2012-11-02 22:23 /dev/sr0

$ sudo mount /dev/scd0 /media/cdrom -t udf
mount: no medium found on /dev/sr0

Any help is greatly appreciated!

---

### Post by offgridguy on 2012-11-02
You did burn the CD as image file? not data.

---

### Post by wyclif on 2012-11-02
Thanks, offgridguy, but can you be more specific? I grabbed a MacBookPro and burned the ISO with Disk Utility, and verified checksum, &.

So, yes, I burned an .iso image of 10.04.4 LTS just to get a base for an upgrade path on this older machine that should be perfectly usable. It's got an AMD Athlon on a Tyan ATX motherboard, and has an Adaptec SCSI card in the third slot. Everything is clean and has been kept free of dust, and has been standing on a floor. The CDROM drive is a Plextor Ultraplex Wide:

[http://reviews.cnet.com/cd-drives/plextor-plextor-ultraplex-wide/4505-3207_7-132486.html](http://reviews.cnet.com/cd-drives/plextor-plextor-ultraplex-wide/4505-3207_7-132486.html)

There doesn't seem to be any reason why this older, but still quality system can't be reused with a fresh install of Ubuntu/Lubuntu/Xubuntu LTS, and turn out to be a decent programming machine.

I wonder if I might be able to simply unplug the SCSI and plug an IDE CDROM drive onto the motherboard to install. I don't really want to do this though; I'd rather figure out what is amiss here and learn something.

---

### Post by tokyobadger on 2012-11-02
Do you still have the Jaunty CD and if so does the CD-ROM boot from it?

---

### Post by wyclif on 2012-11-03
I do, and I tried using it again but I get the same "Verifying DMI Pool... 
"DISK BOOT FAILURE. INSERT SYSTEM DISK AND PRESS ENTER."

wyclif@red:~$ mount /dev/cdrom
mount: no medium found on /dev/sr0
wyclif@red:~$ mount /dev/sr0
mount: no medium found on /dev/sr0
wyclif@red:~$ mount /cdrom
mount: no medium found on /dev/sr0

Still can't upgrade!

---

### Post by tokyobadger on 2012-11-03
Do you see the CD drive when you run the utility "Disks" (under applications)? What happens when you insert a music CD in the drive?

Have you checked the connections of the CD drive?

If the hardware is good, maybe a server install image is needed to load the correct drivers?

---

### Post by grahammechanical on 2012-11-03
I am confused. You say that both the hard disk and the CD drive are on the SCSI card. Then you say that you entered the _System_ BIOS to change the boot order. That means the BIOS is looking for a non-existent CD drive. It is not looking at the SCSI card for an operating system on the either the hard disk or the CD drive.

You also say that you have changed the boot order in the _SCSI_ BIOS. I would suggest that you keep the System BIOS booting to the SCSI card and only change the boot order in the SCSI BIOS so that the System BIOS looks for an operating system on the SCSI card and then the SCSI BIOS directs the search away from the hard disk and towards the CD Drive.

Even without an operating system on a disk in the CD drive the machine should still load an OS. It should look to the hard drive if it fails to find an OS on the CD. This is not happening.

I think that you have told the System BIOS not to look for an OS on the SCSI card. So, it cannot find one even on the hard disk.

Regards.

---

### Post by wyclif on 2012-11-03
Thanks, @grahammechanical.

That makes total sense. So I edited the boot order in the BIOS to boot "SCSI". Then edited the SCSI BIOS to boot from the CDROM drive which is device #3.

Rebooted. Still won't boot from the CDROM!

---

### Post by wyclif on 2012-11-04
So, does anybody have expertise with SCSI who can tell me what's wrong here? :confused:

---

