---
title: "USB startup disk. 9.10 beta (Karmic Koala)"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ljkjp2 on 2009-10-12
Hi!

I have a notebook PC with cd/dvd drive, 10.1 inch screen, intel core duo 1.2 GHz processor with 2GB RAM so I thought the UNR version of Ubuntu 9.10 (beta) would best suit this machine.
I downloaded the .iso & burned it to a cd, restarted the PC into 9.10 (beta) & used "Create USB Start Up Disk" to use a 16 GB flash drive stick as a portable Ubuntu OS.
All went well. I allotted 4GB for a persistence file (the max. in a FAT 32 file system, I believe) & booted up from the stick.
No problems. Home wireless network was joined after entering details. Installed "WINE" & Mozilla Thunderbird, added Japanese language support - everything went beautifully (except that I could not get the time set to my location) until I tried to update things.
The update went fine (374 packages) until the "grub" package near the end. On restart, the PC froze on the white logo for Ubuntu.
Next day, I tried again but got the same result so I reformatted the stick and followed the same procedure but updated things before adding anything else. Same thing happened.
It seems that problems in 9.04 with Create USB Start Up Disk have been resolved - the persistence file seemed fine. The date & time settings utility seems to be unco-operative and the update manager works well but something in the updates is causing the system to freeze part way through the start up.
I am an "end user" with no knowledge of the inner workings of Linux. I was impressed by my first look at Ubuntu 9.10 & hope it becomes useable as a portable system. The PC belongs to my employer so I can't replace the Windows system or even install a dual boot one on it - a bootable USB stick would be ideal.
Any constructive ideas would be very welcome.

Thanks & best regards.

---

### Post by Mighty_Joe on 2009-10-12
If you plan to use your bootable USB drive for any amount of time, do a full install rather than a Live USB (see my post [here]("http://ubuntuforums.org/showthread.php?t=1193680") for the procedure I use). It will be faster, and you can use the whole drive, rather than just a 4Gb partition. 
I haven't had good luck with "persistent" Live USB's lasting more than a few boots.  There's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702") where the persistent partition isn't unmounted cleanly that may explain what I've seen.

---

### Post by ljkjp2 on 2009-10-14
Thanks for the post, Mighty Joe,

Since I last posted I messed around a bit and things are working OK at the moment.

I take your point about formatting the flash drive for linux and doing a "real" install on it - the FAT 32 file system has its limitations & flash drives are getting a lot cheaper so I will look at this again after the final release of 9.10 next week.

I got the date/time sorted by right-clicking on the date in the top menu bar and following the obvious. Using the Admin -> date&time control panel didn't work.

My problems with the persistence file in 9.04 ended when I replaced the casper-rw file with one from pen-drive linux
[http://www.pendrivelinux.com/downloads/casper-rw/4GB-casper-rw.zip](http://www.pendrivelinux.com/downloads/casper-rw/4GB-casper-rw.zip)

I also used Create Start Up Disk on the flash drive which had frozen without re-formatting the drive & updated choosing only Canonical sources in Admin -> Software Sources. Somehow something worked.

Much obliged for your comments.

All the best.

---

