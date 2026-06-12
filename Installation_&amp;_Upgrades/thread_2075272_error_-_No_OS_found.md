---
title: "error - No OS found"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by Bigjon1984 on 2012-10-23
Hi All, I hope I am posting this in the correct part of the forum, I am fairly new to this!

I recently bought an old IBM Pentium 4 that work were disposing of (£20 which went to charity as well, how nice!) As you may expect it was given to me in a completely formatted state but was previously runing Windows XP.  I decided a nice clean install of Ubuntu 12.04 would be best but when I choose DVD (or USB) from the BIOS to boot from I see an error immediately stating "No Operating System found".  

This has me a little stumped, I have installed the OS 3x times on 3x separate machines from the disc and USB stick so I know they are fine.  But as there is no OS on the machine I cannot get into it to see where the problems are.  I am fairly competent with computers but not at a level where I can fix this without a little direction.  Does anyone have any ideas?

In case it is of any use the spec is:
Pentium 4 3ghz single core
186 pin ram 4gb
80gb HDD

---

### Post by dino99 on 2012-10-23
i suspect Big Blue having created a hidden partition on the disk with its useless stuff, but like the devil refuse everything else but damn krozoft.
Find your best formatting tool on cd/usb (partedmagic or gparted) to fully format that hdd, then create a primary ext4 partition of about 10/12 Gib and an extended partition then.
That should resolve such issue.

This is how i install ubuntu:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by darkod on 2012-10-23
That is a message from BIOS because it expects to find a partition with the boot flag on, which is not there. But it's very strange it doesn't allow you to boot from dvd regardless. It has to give you an option to install an OS first. :)

Make sure it's set to boot from dvd and double check why it's not booting.

---

### Post by Bigjon1984 on 2012-10-23
Thank you for the advice guys.  I can confirm the boot method was set correctly to either CD/DVD or USB but the same error re appeared.  

I will try partedmagic and reformat/partition the drive and see how I get on with that and report back on how succesful I was

---

### Post by Bigjon1984 on 2012-10-23
Ok, things are very interesting now.  I managed to load partedmagic and this worked fine!  I managed to find a small partition which still had some Windows data on just as suggested so I have completely formatted the disc again.  Everything seemed fine.  

I rebooted the machine again, placed the Ubuntu CD ROM into the drive and can hear the disc spinning and loading yet this time I am just getting a blank screen, no flashing cursor and no typical Ubuntu startup screens.  I am beginning to lose the will, any more advice guys?

---

### Post by darkod on 2012-10-23
Now that sounds like video issues. Do you know the video card by any chance? Usually for nvidia you need to boot with nomodeset. In case you have nvidia, here are details how:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

