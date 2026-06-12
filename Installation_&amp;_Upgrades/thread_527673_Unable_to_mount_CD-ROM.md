---
title: "Unable to mount CD-ROM"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Ubunme2 on 2007-08-16
Dell Inspiron with Ubuntu 7.04, everything else is fine but it won't mount the CD-ROM.

The CD-ROM works, the operating system was installed from it, it is enabled in the bios, it shows up fine in the CD-ROM drive properties dialog box as a Samsung CD-ROM SC-148F.

Yes, there is a CD in the drive.  Yes, I have tried many different CDs both audio and data.  Yes, I have checked the forums and read dozens of similar threads.  Yes, I have tried to mount the device through the terminal, (many different ways) "mount point does not exist" or "permission denied".  Yes I have tried etc/fstab "command not found".  I have also installed "p mount" -hal for auto mount.  All to no avail.

I recycle and donate old computers, have installed Ubuntu on many different computers and never had a problem before.

Thank you all for helping with this terrific operating system.

---

### Post by Pumalite on 2007-08-16
All I can think of, is trying different settings for your IDE configuration (if you are using IDE) in your BIOS. I fixed my problem with an ASUS mobo setting IDE conf. to 'Enhanced Support for PATA+SATA'

---

### Post by Ubunme2 on 2007-08-16
Thank you for your help, I went back into the bios and checked the "secondary IDE master" type was set to "auto" the choices are:
none, User, auto, CD-ROM, ATAPI removable, other ATAPI, IDE removable.
 
When I select "CD-ROM" instead of "auto", a new window comes up with:
LBA mode control = enabled
multi-- sector transfers = 16 sectors
PIO Mode = auto
ultra DMA = disabled
(I was going to just try to select "CD-ROM" until I saw this screen) LOL

---

### Post by Ubunme2 on 2007-08-17
Any suggestions on what to try next?

---

### Post by Pumalite on 2007-08-17
You can set your CD-ROM to 2nd Master in your computer and then set it to 'Auto' in your BIOS.

---

### Post by Ubunme2 on 2007-08-17
Thanks again for your help, I feel as though I am only a click or two away from solving this problem.

The CD-ROM is set to the: 
secondary IDE master

And it is set to type:
auto
in the bios

I finally got into:
sudo nano etc/fatab  
and I found:
/dev/scd0 /media/cdrom0 udf ,iso9660 user ,noauto 00

I also just tried the floppy disk, and it works and shows:
/dev/fd0 /media/floppy0 auto rw ,user .noauto 0 0

---

### Post by Pumalite on 2007-08-17
What do you mean you are 'almost' there?. YOU ARE THERE.

---

### Post by Ubunme2 on 2007-08-17
No, but I see other people with similar problems are finding a solution by typing a new command in the terminal.  (I am just hoping to be so lucky)

---

