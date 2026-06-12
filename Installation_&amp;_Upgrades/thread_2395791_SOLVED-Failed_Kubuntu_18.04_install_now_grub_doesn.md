---
title: "SOLVED-Failed Kubuntu 18.04 install now grub doesnt see my LM KDE"
date: 2018-07-06
forum: Installation &amp; Upgrades
---

### Post by dirigible on 2018-07-06
Hi, 
I had been running LM KDE LTS but because they are dumping the KDE flavour I decided to try Kubuntu.  

Booted off a USB and attempted to manually install onto a pre-existing separate partition.  Have used this partition several times before for this very purpose.  
Anyway, the installer failed while I was entering my details but by this time GRUB had already been rewritten.  
Attempted to fix grub with Boot-Repair-Disc but although it said it found all my OSs and fixed the problem I only get the option to boot to Kubuntu 18.04 (broken just hangs)  or Windows 7 which is still working.  

Does Boot-Repair-Disc still work?  

Is there another way to get LM back into GRUB?

---

### Post by deadflowr on 2018-07-07
Run the boot repair's boot-info and post the pastebin link it gives.

---

### Post by dirigible on 2018-07-07
Thanks for taking an interest in my problem.  
sdb1 is what I'd like to restore.  
sdc2 is where the problem occured.  


Here's the log.  

[https://paste.ubuntu.com/p/Jn4pybTGDS/](https://paste.ubuntu.com/p/Jn4pybTGDS/)

---

### Post by yancek on 2018-07-07
Is sdc2 where you were trying to install Kubuntu?  Have you tried re-insalling Kubuntu to sdc2?

Did you make the change suggested at the end of the boot repair output, setting sdb (120GB drive) to first boot priority in the BIOS?  If so, what is the result?  If windows boots then one of the bootloaders of Grub must be functioning and the only grub.cfg file I see on your systems is on Mint (sdb1).   The only sign of what might be Kubuntu is on sdc2, sdc3, sdc4 all of which have problems.

---

### Post by dirigible on 2018-07-07
Yes I checked the boot order and have tried other things.  
Now I think this may be a problem with my desktop not liking USB installs.  
I can run Boot-Repair-Disk off USB but I just remembered I've always installed OSs from DVD.  
My DVD drive is not recognising DVDs at the moment.  
On Monday I'll get a new one and try again.  

Thanks for looking at my problem.  

Marked as SOLVED.

---

