---
title: "Substantial loss of functions after upgrade from 16.04 to 18.04"
date: 2018-09-30
forum: Installation &amp; Upgrades
---

### Post by francophile on 2018-09-30
Hello,

This is my first posting, stemming from what appears to be a disastrous on-line upgrade. I must confess, at the outset, that I haven't got to grips with manipulating Linux, although I have no qualms about following prescribed input via the terminal. Preamble over, now to the problem.
 
I had responded to a normal update reminder, at the end of which I was invited to update from 16.04 to 18.04. I accepted the invitation and left the machine to get on with it. Several hours later, I returned to my PC to find a new desktop, but apparently precious little else. In fact, LibreOffice Writer doesn't work at all; it boots and immediately freezes. Conversely, LibreOffice Calc readily opens my spreadsheets, even those created in the days of Open Office. Thunderbird and Chromium appear to work as normal, but are prone to freezing when responding to external links. Worst of all, GIMP has gone completely.

I understand it is impossible to backtrack on an update, so how do I go about persuading 18.04 to perform 'properly'?

Thanks in anticipation of knowledgeable aid.

Derek.

---

### Post by Tadaen_Sylvermane on 2018-09-30
I'd suggest backup personal data and do a fresh installation. For some reason it seems that Ubuntu's upgrade process is very problematic. Rarely works correctly near as I understand it. It must work for some people though as they offer it as an option. It has never worked for me though.

---

### Post by francophile on 2018-09-30
Here is the first stumbling block. There are many instances of advice to create a backup, but I can find nothing remotely useful in 'Absolute beginner', 'General help', or 'Installation & upgrades' about the process of creating a backup. I have acquired an external SSD which, when plugged in, shows in 'Disks' and has a dev/*** identity. I am, however, unable to persuade it to accept any entries. Where do I go now?

---

### Post by Tadaen_Sylvermane on 2018-10-01
Use the disks utility to create a partition on the drive, then copy your personal files to the drive. after all of your stuff that you want to save is "backed up" then you can reinstall 18.04. Just don't overwrite the drive with the backups.

If you are reinstalling I'd advise changing main partition structure to LVM so you can make use of snapshots. On the next upgrade you can snapshot the system. Do whatever, if it goes to hell just reload the snapshot. No fuss no muss.

---

### Post by francophile on 2018-10-03
Thank you for these suggestions. I have formatted the SSD, but that is as far as I can get. The SSD is still identified as dev/xxx, but it doesn't appear in the menu on the LHS of the screen. A flash drive, however, inserted in the same socket does show. Similarly, insert both the SSD and the flash drive simultaneously, but only the latter appears. Consequently I am unable to access the SSD to transfer files and folders to create the essential backup. Further advice would be appreciated.
I have looked at internet advice on both 'tar' and 'cpio', but neither will work for me. Perhaps I'm too thick to be using Linux and should revert to the products (and their shortcomings) of Microsoft!

---

