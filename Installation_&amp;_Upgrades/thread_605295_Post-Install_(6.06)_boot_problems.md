---
title: "Post-Install (6.06) boot problems"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Cynikiss on 2007-11-06
I looked around briefly to see if this error was covered elsewhere, but didn't find anything. If anyone knows of a pre-existing thread where this is covered, please point me in the right direction. :)

If not, here's the problem I'm having:

I downloaded 6.06 and burned the image onto disc. I was able to boot from the disc to the "live CD" version of the OS, and was checking things out. After I spent some time playing around with the OS, I decided to go ahead and run a true install of it, using the 'Install' icon on the desktop. I went through the Install wizard (which was really quite simple), and when the install finished, I rebooted the system and removed the disc from the drive (as instructed).

When the system rebooted, however, I got the following error:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.

When doing the install of Ubuntu, I decided that, rather than having it dual-boot alongside Windows, that I would just format the drive and run an all-Linux system. So, I don't know why I'm getting Windows messages in the first place, and why Ubuntu isn't booting properly.

Any assistance anyone could provide would be greatly appreciated! :)
[COLOR="Red"]
Edit: PLEASE IGNORE THIS! Lol, I feel like a noob, but I fixed the problem myself. :p  The problem was that I actually have two hard drives (one the boot drive, the other a storage drive), and the storage drive was set to boot before the boot drive in the BIOS for some reason. Sorry for the inconvenience! (Devs, if you'd like, you can just delete this post!)[/COLOR]

---

