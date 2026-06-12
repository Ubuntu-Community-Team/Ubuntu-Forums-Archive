---
title: "Older PC will ONLY boot from legitimate Windows 7 Disk"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by Ranvier_Saber on 2016-04-22
Hello guys, I have an odd problem that's driving me nuts. 

I have an older (read: very old Pentium 4 custom built pc) that I am trying to load Ubuntu on, but for some reason, no matter what I try, I cannot get it to boot from the DVD. I've burned two different disks, using windows own iso burner, swapped out the dvd drive, and still won't boot. Thinking something was up with the pc I put in an old legitimate windows 7 disk and it booted just fine, but just won't boot from my live ubuntu dvd. I tried booting  from the dvd on another comp to make sure there's nothing wrong with the disk, and it boots just fine on my other PC. What gives?

Any idea why it will only boot a legitimate windows 7 disk but not my live ubuntu dvd?

Thanks in advance

---

### Post by DuckHook on 2016-04-23
Welcome to the forums Ranvier_Saber.

On very old machines, the DVD drives will sometimes not read burned DVDs but can still read commercial DVDs. The reason is that commercial DVDs are composed of actual physical pits on the substrate, whereas burned DVDs are composed of a dye that changes colour under specific wavelengths of laser light. The old DVD drives could not reliably read the different dye colour. The lasers on DVD drives also degenerate over time. Last but not least, many of the older DVD drives were only capable of either +R or -R (different DVD formats), and have difficulty reading something in the other format.

If it cannot read music or plain data (say, from a backup) from a burned disk, then one of the above is very likely the problem.

Also, you may not like the performance from an older box running Ubuntu, and may be better off running lighter flavours: L/X/ubuntu.

The easiest solution to the DVD problem is to convert the DVD image onto a LiveUSB and install that way.

---

### Post by Bucky Ball on 2016-04-23
All of the above, and here's some tips for making a bootable live X/L/Ubuntu USB (presuming the machine can boot from USB, have a look in BIOS or at the boot device list at boot time) directly from the ISO:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by poorguy on 2016-04-23
How old is old. I did an install Ubuntu mate 16.04 (32bit) on a 2005 dell GX620 p4 2.8 GHZ 3.0 GB ram runs excellent.
I have had cheap DVD burners that didn't do a good quality burn and some computers wouldn't boot from a poorly burned DVD.

Also infrarecorder works very well.

[http://infrarecorder.org/](http://infrarecorder.org/)

---

### Post by Ranvier_Saber on 2016-04-23
> **DuckHook said:**
> 

[FONT=Verdana]On very old machines, the DVD drives will sometimes not read burned DVDs but can still read commercial DVDs. The reason is that commercial DVDs are composed of actual physical pits on the substrate, whereas burned DVDs are composed of a dye that changes colour under specific wavelengths of laser light. The old DVD drives could not reliably read the different dye colour. The lasers on DVD drives also degenerate over time. Last but not least, many of the older DVD drives were only capable of either +R or -R (different DVD formats), and have difficulty reading something in the other format.[/FONT]

[FONT=Verdana]If it cannot read music or plain data (say, from a backup) from a burned disk, then one of the above is very likely the problem.[/FONT]

[FONT=Verdana]Also, you may not like the performance from an older box running Ubuntu, and may be better off running lighter flavours: L/X/ubuntu.[/FONT]

[FONT=Verdana]The easiest solution to the DVD problem is to convert the DVD image onto a LiveUSB and install that way.[/FONT]

Huh, I had no idea about that, thanks so much for that explanation, that was new to me. 

I just swapped out the drive with a more recent drive, and it booted just fine! Installing at the moment, thanks so much for your detailed explanation!

---

### Post by DuckHook on 2016-04-23
Happy it worked out so easily for you. That's what we're here for. Please mark thread "solved". This will help others who google or search and land on this thread.

---

### Post by Bucky Ball on 2016-04-24
Useful info there leading to a fix, Duckhook. I'll stick that in the attic for future use. :)

---

