---
title: "Fail to boot Live USB"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by Quackers on 2010-12-25
I was thinking of joining the rest of you in the 21st century by making an Ubuntu Live usb :-) I'm perfectly happy with my Live cd's but just thought I'd give it a try.
I've used Startup Disk Creator, Unetbootin for Linux, Unetbootin for Windows and although all attempts appear to complete, when I try to boot from the usb key all I get is a blinking cursor in the top left :o
Bios is set as USB Flash  first boot device, cd drive 2nd boot device and HDD 3rd boot device.
I decided to give up, but I've changed my mind :-) I'm not giving up on such a simple task!
Any suggestions would be great :-) 
Thanks.
Season's greetings to all :popcorn:

This is what nautilus shows is on the drive

---

### Post by wilee-nilee on 2010-12-25
Although it sounds like its getting to the thumb try the per-session boot and let it rest like 5 seconds before hitting the usb boot maybe its just not reading it correctly, with it set first in the bios.

---

### Post by Quackers on 2010-12-25
Although I said I'm trying to join the 21st century, my laptop isn't :-) There is no per-session boot option on it :-( I have to set the bios the old way :-)

---

### Post by C.S.Cameron on 2010-12-25
Have you checked the iso MD5SUM.

---

### Post by Quackers on 2010-12-25
Yes I have checked the MD5SUM. This is the same download that I used for the live cd so it's definitely ok. Sadly I can't get far enough to check for errors on the usb!
The bios is obviously seeing the usb stick and it's attempting to boot from it, but something may be missing, I'm not sure. Having said that though, all 3 methods to make the usb fail to boot in the same way, so I'm really not sure what's wrong:-(

---

### Post by C.S.Cameron on 2010-12-26
If grub is working, the grub2 method of booting Live iso's should also work.
MultiBootUSB will boot single iso's on a flash drive as well as multiple ones:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by Rubi1200 on 2010-12-26
You may have to apply boot parameters.

In your case, nomodeset.

I create LiveUSBs with UNetbootin and then go to the syslinux.cfg file and remove quiet splash and add in whatever is relevant for my machine.

Hope this helps.

---

### Post by Quackers on 2010-12-26
Thanks for the further suggestions guys. I'm still experimenting with different images and persistent/non-persistent settings but no joy yet.
Rubi1200, with any live cd I have used I haven't needed nomodeset, or any other boot options, so I wouldn't think one would be necessary. 
But anyway, I'm not getting that far :-)
I'll report back after more tests :-)

---

### Post by Quackers on 2010-12-26
No deal :-(
I've tried 3 different .iso files with 3 different methods using persistence and non-persistence and they all do the same thing on booting.
The blinking underscore appears top left and the light on the usb flashes for 2 or 3 seconds, then it stops flashing and the blinking underscore keeps blinking. No further usb flashes, so it's not being accessed after the first 2 or 3 seconds.

One thing has been bothering me though.
The stick is a 2GB stick. It appears in gparted as 2 drives (sdc at 1.9GB and sdd at 1.5MB) but in Startup Disk Creator sdc appears as sdc and sdc1 (BOTH at 1.9GB)
Is that normal?
Cheers

---

### Post by C.S.Cameron on 2010-12-26
> **Quackers said:**
> No deal :-(
I've tried 3 different .iso files with 3 different methods using persistence and non-persistence and they all do the same thing on booting.
The blinking underscore appears top left and the light on the usb flashes for 2 or 3 seconds, then it stops flashing and the blinking underscore keeps blinking. No further usb flashes, so it's not being accessed after the first 2 or 3 seconds.

One thing has been bothering me though.
The stick is a 2GB stick. It appears in gparted as 2 drives (sdc at 1.9GB and sdd at 1.5MB) but in Startup Disk Creator sdc appears as sdc and sdc1 (BOTH at 1.9GB)
Is that normal?
Cheers

If you are using Startup Disk Creator in Windows, Windows can only see the first partition of a multi partition flash drive.
Do not try to format a multi partition flash drive with Windows.

Startup Disk Creator will show the drive as sdx and sdx1.

Don't understand gparted seeing the drive as 2 drives, could sdd be something else?

---

### Post by Quackers on 2010-12-26
I'm using Startup Disk Creator in Ubuntu.
No, C.S.Cameron, sdd is definitely from the flash drive

---

### Post by C.S.Cameron on 2010-12-26
I have not seen that before.
Can you format sdd

edit:
Are you doing all this in Natty?

---

### Post by Quackers on 2010-12-26
I am currently booted into Natty, and I was while doing this job :-)
And yes, I can format sdd - all 1.5MB of it :-)

---

### Post by C.S.Cameron on 2010-12-26
Oops, I have not tried Natty yet.
usb-creator has seemed to have problems with Development Releases since it's beginning.
UNetbootin and Universal probably are not ready for 11.04 yet either.

How about trying to boot the iso using grub2?

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by Quackers on 2010-12-26
I don't know what you mean by that :-)
I can try the process again using Maverick, but I suspect that the disc/partition thing is going to be a problem. I can delete the partitions and end up with 2 unallocated spaces on sdc and sdd, but I can't get sdc to join with sdd, even though they are on one flash stick. But, as soon as I format sdc, sdc1 appears on its own. I don't understand that part.

---

### Post by C.S.Cameron on 2010-12-26
I''m interested if 10.10 will boot from that disk.

---

### Post by Quackers on 2010-12-26
I'm a little ties up at the moment, but I will try from Maverick and let you know :-)
Thanks for your suggestions.

---

### Post by martingugino on 2011-07-23
I have also not been able to boot from a USB. I saw a remark someplace that SanDisk Cruzer was a problem, and so used a 3.0 usb from Super+Talent (??), with exactly the same result.
I created the USB stick by
1) downloading the 10.4 ISO and then tried the 11 iso, and
2) System/Administration/ Startup Disk Creator

I am a newbie at Ubuntu. 
I have not read this entire thread, but I will go back up and do that.
I see the last post is 2010, and I feel sure that there are other comments, someplace, this year on this topic....

July 2011

bad news: I followed the instructions from here:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
Pretty instruction, but doesn't work.

---

### Post by Quackers on 2011-07-24
2 different Sandisk Cruzers work here.
Depending on your system it can be necessary to choose USB HDD in the bios settings, rather than USB flash drive. One of my other sticks is read as a USB HDD for some reason.

---

