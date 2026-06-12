---
title: "Cannot get bootable usb to boot"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by bparkman on 2010-03-06
Please forgive me if this has been covered, I searched but didn't find anything relevant.  I have an HP 2140 with Windows 7 RC build 7100.  It's expired, and now shuts down every two hours.  I decided I'd rather install Linux than put a new Win7 on it.  Anyway, I have tried EVERYTHING to get a bootable USB to work.  The funny thing is I installed Win7RC from a USB over WinXP.  For some reason, no matter what method I try, and I've tried all I can find, my computer will not run files from the USB on boot.  The computer has an option to boot from USB, and I've done it before, but am baffled as to why I can't do it with a Ubuntu USB drive.  All I want to do is install Ubuntu 9.10, clean from a USB flash drive, erasing all evidence of Win7RC.  I can't believe how hard this has been.  I do not want my first encounter with Linux to end negatively!  Please help!!

---

### Post by PRC09 on 2010-03-06
How did you create the usb drive? Does it not boot at all ? Any error messages?

---

### Post by hatalar205 on 2010-03-06
Try this. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by presence1960 on 2010-03-06
If your flash drive is under 4 GB it may be showing under hard disks in BIOS. When you boot the flash drive go into BIOS and look in the hard disk boot order. If the flash drive is listed there move it up to first disk to boot, save changes to CMOS and continue booting.

---

### Post by motorhead_1 on 2010-03-06
I'm sorry to put this question in your thread but I've a similar problem, is it possible that my BIOS doesn't have a boot option for my USB external HD ?

---

### Post by presence1960 on 2010-03-06
> **motorhead_1 said:**
> I'm sorry to put this question in your thread but I've a similar problem, is it possible that my BIOS doesn't have a boot option for my USB external HD ?

The only way to tell if your BIOS is capable of booting from USB is to either go into BIOS and look or refer to the motherboard/BIOS documentation. If you don't have the documentation as long as you know your motherboard make & model you can get the documentation at the manufacturer's web site.

---

### Post by bparkman on 2010-03-06
Thank you for the quick replies.  I should have put more info in my original post.  I have tried unetbootin and usb-installer.  Even tried downloading the entire DVD image, unpacked it to the USB drive (8GB Kingston DataTraveler) and it wouldn't boot from that either.  My BIOS does have USB Hard Drive listed as a boot option, but when I choose it on boot (press F9 to get boot device options), it just goes to a black screen with a flat cursor blinking in the upper left.  It's as if my computer isn't finding anything it can, or wants to, run on the flash drive when booting.  Is there some file that needs to be on the flash drive root that will tell the computer to run files there?  Do you think Win 7 RC is interfering?  Does anyone have a screenshot of the root level of a USB drive that is bootable?  I've seen some sights where you have to move files around and even rename file from iso* to sys*, etc.

---

### Post by bparkman on 2010-03-06
Got it to work!!  My fault too.  When using UNetbootin, I failed to make the USB drive and partition 1 active, so my computer wasn't seeing it as bootable.  Once I did that, voila!  Now in the process of wiping win7rc and loading Ubuntu 9.10 on HP 2140!!!  Can't wait to dive in!   :D

---

