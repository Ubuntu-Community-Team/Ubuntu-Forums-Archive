---
title: "Computer won't start after attempted Ubuntu Installation"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by MatthewJ00 on 2014-06-17
I recently attempted to install Ubuntu 14.04 on my primary computer. The installation process stopped at some point, and the installation process closed, but a dialog box popped up saying to restart the computer, but it did not respond. I (stupidly) decided the best idea would be to shut down the computer and see if it worked. When I went to turn it back on, I took out the boot disk I had been using to try out Ubuntu on, but when I turned it on, nothing responded (I had chosen full installation). The BIOS did not appear to be working, all that showed was the text cursor that appears in the corner just before the computer begins to boot into an OS, but after an hour, nothing had happened. I tried again with the boot disk in, but still nothing. I don't believe BIOS files can be corrupted, can they? Either way, it is urgent that I get this computer to work as quickly as possible.

---

### Post by yancek on 2014-06-17
Did you change the boot priority from CD/DVD drive to the hard drive before rebooting?
Is there any other operating system on the computer?  If so, which?

---

### Post by MatthewJ00 on 2014-06-17
> **yancek said:**
> Did you change the boot priority from CD/DVD drive to the hard drive before rebooting?
Is there any other operating system on the computer?  If so, which?
It had Windows 7 on it previously, but I'm not sure whether it had fully finished erasing the main partition before the installation process froze. Just before the installation process started, I got a few dialog boxes saying that it could not delete the 4 partitions that were created when the hard drive was originally formatted. I don't know anything about boot priority, but when I just had Ubuntu running off of a disk the BIOS started a menu to select either one of the operating systems. Because I cannot start the computer, unless I took out the hard drive, I couldn't even tell whether or not the startup files installed correctly.

---

### Post by MatthewJ00 on 2014-06-17
Actually, never mind. It appears that whatever caused the issue during installation also affected the CMOS battery, so taking it out and putting it back in should fix it. Thank you for your help though.

---

### Post by sammiev on 2014-06-17
Download [Gparted]("http://gparted.org/livecd.php") live and capture a image of your HD and post back the image here.

All specs of your computer would really help us as well.

Update: I guess you have it solved. Please mark the thread as Solved.

---

