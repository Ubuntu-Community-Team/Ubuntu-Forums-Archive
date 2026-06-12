---
title: "Unable to burn/boot 9.10 iso image"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by cfder on 2009-12-03
Hello,
    I finally decided to upgrade my computer from the vernerable Dapper, so I downloaded the 9.10 386 iso image and checked the md5sums to make sure the image was good.  Try as I might, I have been unable to burn the image on this machine.  If I right click on the image icon and select "Write to Disk", and try to burn at the lowest speed, it goes straight from "preparing to burn" to "finishing" without actually writing any data.  If I try a command line burn with cdrecord, I get the following errors:

status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488

The burn failure was very repeatable - I've several new coasters now.  I thought maybe image file was too large for the media, or the hardware was bad, but I was able to successfully burn and then boot a 6.06 iso image, and a Knoppix 5.0.1 image, both of which are larger than the 9.10 image.

Next I tried to burn the 9.10 cd on a different computer, this one running 8.10, and... no problem.  I got a good CD which booted into the live system without issue on the second computer.   However, when I try to boot the disk on  the Dapper system, I make it to the language selection screen and choose the option to boot the live filesystem, but after a minute or so of the ubuntu symbol glowing at me, the screen goes blank.  When I hit a key, I get an error message saying "Unable to locate a medium containing a live file system" and am dumped into a shell.  dmesg reports buffer IO errors on /dev/sr0.  Same if I just try to check the disk.

A search here in the forums turned up the same boot error with suggestions to try different boot options (including setting all_generic_ide), try a DVD instead of a CD, etc.  I tied all with no luck.  Another suggestion was to use a bootable thumb drive, but unfortunately, this MB is old enough that the only usb boot options are floppy, zip, and cdrom, none of which work with the thumb drive.  The only suggestion I didn't try was to remove all but one stick of RAM.

Even though the drive works fine with other disk images, I did try pulling the dvd writer from the second computer and putting it in the dapper system, but this didin't fix anything.  If there is a hardware problem, its in the IDE controller.  Why it would only show up with this particular disk image...

So, to recap:
   I am unable to burn the 9.10 ISO image, though I can burn other, larger ISO images
   I am unable to boot a good 9.10 CD (burned and booted on a different computer)

Much as I'd like to use this as an excuse to build a new system, I'd really like to get this machine upgraded.  I've considered pulling the hard drive, temporarily installing it in the second computer, doing the install there, and then moving it back, but I'm not sure how well it'll handle the hardware changes.  At this point I'm open to any and all ideas.

Thanks,
Ray

---

### Post by jmate24 on 2009-12-03
Have you tried this:

[HTML]https://help.ubuntu.com/community/HowToMD5SUM[/HTML]


jmate24--

---

### Post by cfder on 2009-12-03
Yes, I did check the md5sum on the iso image, and it is fine.  As I stated , the CD burned from the same image file on a different computer boots fine on that computer.  It only has problems on the mac hine I want to update.

Ray

---

### Post by cfder on 2009-12-05
Well I got things working.  I tried replacing the cd drive ribbon cable, and low and behold, the 9.10 CD booted fine.  Curious that the 6.06 disk booted fine with the old cable, but, oh well.  At least now I can update my machine.

Ray

---

