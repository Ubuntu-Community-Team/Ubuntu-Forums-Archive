---
title: "Can you reenable quickboot and srt after dual boot install?"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by steeny124 on 2013-03-06
Please don't murder me if this is covered elsewhere.  I couldn't find a straight answer.  Assuming I follow the top paragraph here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  to install ubuntu for a dual boot with windows, can I REENABLE quickboot/fastboot and smart response technology after I've installed everything correctly?   It'd be a bit of a bummer if I had to sacrifice those features.  At least the srt.

---

### Post by oldfred on 2013-03-07
I think quick boot bypasses UEFI keys so if Windows does not boot then you may not have a way to even change UEFI to boot a repair disk or you have a brick. Some have special keys to get around that issue.

It may depend on how you installed and you may need RAID drivers in Linux to see Windows.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
      
 Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by steeny124 on 2013-03-07
Well, I haven't installed anything yet.  Just ordered a new laptop, and I plan to try to do a dual-boot.  Technically this will be my first dual boot. 

 I bought my current laptop about 5-6 years ago and Just have ubuntu.  I wanted to try a dual boot this time around because there are some things I miss being able to do on Windows.

  Anyway, just trying to do my homework before hand, because I'm not sure what to expect. I'm definitely NOT an expert in this field.  In fact, I'm pretty hesitant because I don't want to end up messing anything up on my computer.  Any recommendations on whether I should just go ahead and see what happens or to wait to try to install ubuntu and see if things get easier in the future?

---

### Post by oldfred on 2013-03-07
What vendor & what system?
Higher end systems end up with more issues as UltraBooks have Intel SRT which uses RAID for the small SSD.
They also have dual video which usually needs bumblebee.

Standard systems from some vendors just install without any issue.

---

### Post by steeny124 on 2013-03-07
It's an Acer Aspire m5 481pt-6644, 500 gb hdd with a 20 gb ssd.

---

### Post by oldfred on 2013-03-07
A 20GB SSD sounds like an UltraBook or something similar. While ever vendor is different the Intel SRT is the same.

 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

      
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

