---
title: "Cannot mount /dev/loop1 on /cow (not the same as the other questions!)"
date: 2015-09-20
forum: MINT
---

### Post by Matthew_Smith on 2015-09-20
Hello,

I DO know this may not be the right forum, but since Linux Mint is based on Ubuntu, I thought I'd ask here anyway. So , I had this problem once when I was installing Ubuntu, and I solve dit somehow, but I cant remember how. I tried using UNetBootin like I did that time, to make a Mint 17.2 Cinnamon live USB, and if I set persistence to 0, it worked - but every time I make a persistence file (or UNetBootin does, rather) then when I boot up using the USB, the command line/log reads: Cannot mount /dev/loop1 on /cow. I saw that this can be fixed by selecting "no persistence"or something similar, but what if you actually WANT persistence?

Thanks,
Matt

---

### Post by Bucky Ball on 2015-09-20
*Thread moved to **MINT**.*

It goes here, as does any thread regarding Linux Mint. If we make one exception then there's others and then there's not much point in having a Ubuntu forum for Ubuntu and the officially supported flavours.

Mint has an extremely active and vibrant forum. Have you posted there as well?

Try Universal USB Installer. That will create a persistence install from memory. Set the slider for how much you want reserved.

---

### Post by Matthew_Smith on 2015-09-20
Ok, thanks. I'll try that.

Ok, UUI seems to work (not yet tested), but what if I want a 2GB persistence file? it only lets me have a 390MB one :/...

---

### Post by yancek on 2015-09-20
The pendrivelinux site actually has a tutorial on it, see the link below.  It's a little dated on how to access GParted but that is the tool you need.

[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

---

### Post by Matthew_Smith on 2015-09-21
Nope, it's OK :). The persistence size issue was because there was data already on there from previous install attempts. I have made the drive and will post boot results soon.

AAAHH!!! I am soooo pissed off! It failed AGAIN!

---

### Post by yancek on 2015-09-21
If you are still using pendrivelinux (UUI), you might leave the default file size for the casper-rw persistent file then resize it as explained at their link below.  The instructions at this site are if you have a casper-rw 'file' rather than a partition.

[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

---

### Post by Bucky Ball on 2015-09-21
Reformat the drive to FAT32 before using creating the USB install. Completely wipe it. If you have artifacts hanging over from previous attempts you are almost definitely going to have issues. Just one errant file along with the ISO installer on the USB can cause havoc.

So, bottom line, use Gparted or something else to delete everything on the USB, create one FAT32 partition, _then_ use whatever you're using to get the ISO on the USB. 

If you use dd command to create the USB this is not necessary as dd totally wipes and formats the drive as part of the process.

---

### Post by Matthew_Smith on 2015-09-21
Yancek - What do you mean? Do you want me to not create a persistence file, but a partition instead? Or create a small (1MB-ish file) and expand it? Please clarify. Also, are you Polish by any chance?

Bucky Ball - I have formatted the drive with the Windows formatting function, and then I checked the "format dive F:" checkbox in UUI.

I will try LiLi as a inal attempt and post results here (probably tommorrow) Is there anything I can do from the Initramfs command line that could save me, though?

---

### Post by yancek on 2015-09-21
You indicated in an earlier post that UUI would only let you create a 390MB persistence file.  Accept that and change it later per the instructions at the link.  Because it is FAT32, you are limited to 4GB.  If you want a casper-rw partition larger than 4GB you will need to use a Linux fielsystem.

> Also, are you Polish by any chance?

The user name here is just something I made up.

---

### Post by Matthew_Smith on 2015-09-22
Yancek - Ok, let's clarify some things. 1 - I said already that the problem with the partition fixed itself when I formatted the drive 2 - How do I use a linux FS? Do I use a partition on my computer to store the persistence file/partition?

Anyway, LiLi created a drive which took me to a grub command prompt. I tried  [http://forums.fedoraforum.org/showthread.php?t=211383](http://forums.fedoraforum.org/showthread.php?t=211383) but I cannot find the stage1 thing anywhere, although ls shows that a boot folder does exist. WTF?

---

