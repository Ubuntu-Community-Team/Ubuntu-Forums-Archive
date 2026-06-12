---
title: "Access partly formatted Windows drive from Live session?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by newyear on 2008-01-06
Ok, I screwed up. I was about to install Ubuntu 7.10 from a Live session and accidentally clicked on my windows drive. I immediately clicked cancel when the installation program started to format the drive but of course damage was already done. So now i can't access windows and Gparted partition editor in the Live session I'm running now says that the drive is of unknown file system (on /dev/sda1). I can't see the drive in the /media folder.

Is there any way of getting at least some of the files back?
I tried [**this**]("http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/")  guide but it didn't work since it's not a valid NTFS drive.

---

### Post by logos34 on 2008-01-06
Try TestDisk on the SystemRescueCD

---

### Post by newyear on 2008-01-09
I used Testdisk and managed to locate a linux partition on the drive, which I then installed Ubuntu on. The windows partition is still listed as 'unknown'.

I think I'll get a new drive and install windows on it. Maybe then I'll find a windows program that can recover the lost partition

---

