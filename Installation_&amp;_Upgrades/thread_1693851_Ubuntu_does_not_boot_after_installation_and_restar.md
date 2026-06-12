---
title: "Ubuntu does not boot after installation and restart"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by parklinkin on 2011-02-23
The installation just got completed and the laptop has restarted.
Now ubuntu 10.10 does not boot.
"windows failed to start"
Status: 0xc0000225
Previous OS that I used was windows 7
What now, is the whole thing screwed :( ?

---

### Post by FoxEWolf on 2011-02-23
> **parklinkin said:**
> The installation just got completed and the laptop has restarted.
Now ubuntu 10.10 does not boot.
"windows failed to start"
Status: 0xc0000225
Previous OS that I used was windows 7
What now, is the whole thing screwed :( ?


You first say that Ubuntu doesn't load. Then you begin to say Windows fails to start. Do they both fail now?

---

### Post by parklinkin on 2011-02-23
Windows 7 previously was on c drive..
I've formatted the c drive and installed ubuntu 10.10..
Don't know why but, now it says 'windows boot manager', 'windows failed to start'
Help !

---

### Post by parklinkin on 2011-02-23
I just realised that sda1 contains windows loader..
Should the be deleted first ?
What else has to be done ?

---

### Post by FoxEWolf on 2011-02-23
> **parklinkin said:**
> Windows 7 previously was on c drive..
I've formatted the c drive and installed ubuntu 10.10..
Don't know why but, now it says 'windows boot manager', 'windows failed to start'
Help !

That is quite odd indeed. Normally when you format the hard drive, it removes Boot Manager. 
If you reformatted the drive...Windows 7 is lost and gone. I would recommend that you use a Windows 7 Re-Install disc to restore Windows on the HDD. Try using the WUBI Install... You can run both OS's without formatting the whole drive, but merely a partition of it. just run the executable again to uninstall it. I hope you have your important documents backed up. Hope I can help you through this. You can send me an email and we can discuss it more there if it comes to it.

---

### Post by na5h on 2011-02-23
Try to install again from the Ubuntu disc and choose the "erase and use entire hard-drive*" -option when the installer asks you about partitioning. The installer should format the entire hard-drive and install Ubuntu on it as the only OS (which is the goal, right?). Don't know why the Windows loader-partition was still left on the hard-drive after your last install...did you perhaps try to format the hard-drive or do the partitioning manually somehow?  

*might not be the exact words

---

