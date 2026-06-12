---
title: "Proper way to back up 9.10 / install 10?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by blueghoti on 2010-05-28
Hi all - 

I'm relatively new to linux, having installed Ubuntu 9.10 on my laptop (clean install) about a month ago.  I have been concerned that the HDD (2 years old) has become unstable, so I have bought a new drive and - now that 10.x is out - will install 10 from scratch.

I have an external hard drive and want to back up my files and configuration (Evolution, Firefox, installed apps) to the external drive, install the new drive and 10.x, then copy all my settings over to the new environment.  Any suggestions on how to do this?

Thanks!
Chris

---

### Post by jerrrys on 2010-05-29
for installed apps

[ATTACH]158656[/ATTACH]

---

### Post by WinRiddance on 2010-05-29
> **blueghoti said:**
> Hi all - I have an external hard drive and want to back up my files and configuration (Evolution, Firefox, installed apps) to the external drive, install the new drive and 10.x, then copy all my settings over to the new environment.  Any suggestions on how to do this?

.
Well, plenty of different opinions and options out there but I still prefer to see what's going on and to be in charge of what's happening on my machine. The following will work even if you're previously installed apps. like Thunderbird, Firefox, and others as third party apps on earlier versions of Ubuntu.

**1.** Make a backup of your entire home/user folder to another drive/partition/USB stick.
**2.** Backup any personal files that you might have had elsewhere ... docs, pics, mp3, etc.
**3.** If you installed third party apps elsewhere, be sure to copy/backup those as well.
    (all of this can be done very easily with the Nautilus file manager - enable hidden files)
**4.** For Ubuntu 9.10 and later (10.04) the new disk/partition should be formatted to ext4
**5.** Restart with a LiveCD and install Ubuntu fresh on the newly formatted ext4 partition.

The entire process of steps 1 - 5 will more than likely not take more than 30 - 45 minutes (upgrade time included) and _doesn't have to be repeated_ the next time around when you upgrade to the next version of Ubuntu from within your update manager. It's just that the **ext4** file system is much more important than some people seem to think. Lots of corroboration for that can be found directly via official Ubuntu channels and Linux websites.

**Alright, onward we go ...**
Now that Ubuntu has been installed go to your software center in order to install things such as Thunderbird and others if they're not already installed. Your old Thunderbird and Firefox files will be located in your backed up copy of home/user within the two .mozilla folders. You should be able to import all of your old stuff directly into the new Mozilla installations ... all of my email accounts and dozens of email folders with sub-folders ranging back about 8 years were imported without a problem. Since I keep my actual email messages in a separate folder too, I still had to point Thunderbird to the correct location ....

**Good luck, and enjoy your Ubuntu!**

---

### Post by blueghoti on 2010-06-01
Thanks again for your help guys.  I'm now running Ubuntu 10.04 from a totally clean install on a brand new hard drive.  Very nice so far.  Only problem was, the install was a bit bumpy - had to have a go about 3 times as it seemed to have some timeout issues.

---

