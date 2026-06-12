---
title: "Instal Feisty Fawn on ext hdd failed"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by Philip Hosmer on 2007-08-23
I have a Seagate 300 some odd GB hdd on a USB port. I was trying to install Feisty Fawn and now the partitions are the wrong size, I can't find "root" and I am told to make a partition for it, etc. So I tried to delete the whole mess (no files) by formatting. No luck. The screen shows locks on the partitions. How do I unlock it? Do I need to format to remove all hidden stuff? Then start with a fresh install.
Philip Hosmer

---

### Post by logos34 on 2007-08-23
> **Philip Hosmer said:**
> I have a Seagate 300 some odd GB hdd on a USB port. I was trying to install Feisty Fawn and now the partitions are the wrong size, I can't find "root" and I am told to make a partition for it, etc. So I tried to delete the whole mess (no files) by formatting. No luck. The screen shows locks on the partitions. How do I unlock it? Do I need to format to remove all hidden stuff? Then start with a fresh install.
Philip Hosmer

The locks mean the partitions are mounted.  You have to unmount them to format.  To prevent Feisty from trying to mount them again (it does this with removable/usb drives), go to System>Preferences>Removable drives & media>Storage tab and uncheck 'Mount removable drives when hot-plugged' and all the boxes below it.  Now you should be able to format it. Wipe all the partitions and start over.

---

### Post by CValentine on 2007-08-23
If you actually try to install Ubuntu on that external drive, check out my How-to here:
[http://ubuntuforums.org/showthread.php?t=523861]("http://ubuntuforums.org/showthread.php?t=523861")
It also covers, how to partition the drive...

Regards,

CV

---

### Post by Philip Hosmer on 2007-08-23
Ok so I deleted the formats on the ext hdd and eveything went well until it started to create the partition and I got this:

Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0) (sda)...

and it hung up at 5%. This happened when I installed Red Hat many years ago. I just can't remember the fix. I am really glad to have gotten this far. Does someone know what went wrong?

Then I can continue with "HOW-TO Feisty Live-CD installation to USB Drive" article which looks perfect for what I want to do.

Philip Hosmer

---

### Post by Philip Hosmer on 2007-08-25
Ok. I have been installing now for 10 hours and all seems to be going well. I left it last night when I went to bed appearing that it was hung and I got up today and 63% is now installed. 

Thanks for your help and all your posts on the forums. In reading them I got quite educated. I simply had no idea of the time involved to get the installation done. 

Phil:):):)

---

### Post by CValentine on 2007-08-27
Wow, that's odd... Installation took around 30 mins on mine... Please post some info if it worked though, maybe there's just something wrong with the usb drivers. Interesting though... Hats off to your patience ;-)

---

### Post by Philip Hosmer on 2007-08-28
My thought on it is that the partition was so large 260 GB or so. I decided to just get the installation done then shrink the partition. There seems to be nothing wrong otherwise.

After saying that, I can boot the external hdd as my bios is too old and there is no update or work-around that I have found so far. I am trying to find something to put in the ini file for XP that would halt the installation of XP and give me a choice of where to boot from. Do you know if this is possible?

Or I'll just get a new computer.:confused: Duh? That is a work-around! NO? lol :-P
Thanks,
Phil

---

