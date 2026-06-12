---
title: "new to Ubuntu (new to Linux), problem installing Ubuntu Server 16.04LTS"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by rich2016 on 2016-10-21
I'm not new to computers, but I am to Linux....trying to install Ubuntu Server 16.04LTS on my old WindowsHomeServer computer (since MS shut down the server).  I downloaded the ISO and wrote it to a DVD (using Nero's ISO burner).  I get the language screen, then the "Install Ubuntu Server" option (along a list of 6 or 7 menu options)...my DVD light flashes a couple times as does my HDD light, then the monitor goes blank and the lights go out.....nothing further happens (I sat and waited for 15min...)  Here is my system:

ASUS M4A88TD-M motherboard
AMD Phenom II X6 1090T CPU  (64bit)
4GB RAM
3 WD 1TB Hard Drives

I just tried doing a second ISO burn from a newly downloaded ISO and I get the same thing.   In the meantime, I'm gonna try installing a regular Linux flavor just to see if it works.....


Any help would be appreciated.

---

### Post by Bucky Ball on 2016-10-21
Welcome. Yes. Try another version and see if that works. If it's exactly the same or not will give us some further clues.

When you say the monitor goes blank and the lights go out; the lights go out on the monitor? There is no action from the machine at all? 15 minutes seems a bit long in any case. :-k

You can run 'Check for defects' from the first options menu but seeing as you've created two and they're the same probably not that. What have you actually got on the drive at the moment? Does the install media work fine if you use a live session (choose 'try ubuntu' from the first option screen when you boot the disk/USB).

---

### Post by TheFu on 2016-10-21
Linux "servers" don't have a GUI, so if you are completely new to *nix systems, the learning curve will be extremely steep.  Server distros don't have as many drivers included as desktop ones too - like odd network devices and wifi. Just sayin'.  

Best to start with a desktop distro and ease into shell-only server use after 6-12 months (or 5 yrs).  Before trying to install a desktop distro, it is smart to "Try Ubuntu" or whatever distro you like and see how much of the HW and drivers work. Check video, keyboard, mouse, sound, networking ... and wifi if that is important to you.  Since Linux doesn't have 90+% of the OEM market, sometimes things don't work.

I'd think that nero should work fine, but haven't booted from optical media in years - perhaps 6 or more. If the machine will boot from USB flash drives, that might be easier, plus flash is faster than optical almost always (while still being really slow compared to HDDs or SSDs).  Haven't used Windows to make a media disc/flash drive in almost as long, but I know lots of people use a tool called Yumi to create multi-boot flash drives which easily support 8-15 different Linux distros on a single 8G flash device.  Nothing helps learning more than experimentation. ;)

BTW, the entire OS install shouldn't require much more than 15 min. Of course, that depends on whether you patch during the install and how fast the internet connection is and how large the distro is.  TinyCore would need 20 sec to install while a full Ubuntu with patching might take 25 min.

---

### Post by rich2016 on 2016-10-21
Disregard......come to find out my DVD drive is bad..(I tried installing Ubuntu desktop and Mint from the DVD and both failed the same way as the Ubuntu server)....I installed the iso on a flashdrive and it's working...  So, pending any further issues....

Moderators, feel free to delete this thread or leave it to remind others that they may also need to check their hardware when there is a problem.

---

### Post by Bucky Ball on 2016-10-21
We don't delete threads, especially solved ones. :)

Please mark the thread as SOLVED from 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post to help others. This will not close the thread to further discussion.

Good luck and hope you enjoy Ubuntu.

---

