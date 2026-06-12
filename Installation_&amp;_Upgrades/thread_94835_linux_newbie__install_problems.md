---
title: "linux newbie:  install problems"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by homer39 on 2005-11-25
Trying to install on an old E-machines 466mhz celeron.  Things seemed to be going well as it guided me through the process. I opted for the choice to erase the hard disk and make the ide-1 as my master.  then it got stuck during base installation at 6% and message said "retrieving asil-utils".

I turned off machine after 30 minutes of this, and now when i try to boot to cd drive message says boot record not found, then it tries floppy with same result, and finally last message says "ide no operatins system found".  

Where do I go from here?

---

### Post by homer39 on 2005-11-26
[QUOTE=homer39]Trying to install on an old E-machines 466mhz celeron.  Things seemed to be going well as it guided me through the process. I opted for the choice to erase the hard disk and make the ide-1 as my master.  then it got stuck during base installation at 6% and message said "retrieving asil-utils".

I turned off machine after 30 minutes of this, and now when i try to boot to cd drive message says boot record not found, then it tries floppy with same result, and finally last message says "ide no operatins system found".  

Where do I go from here?[/QUOTE]

Ok, I turned off machine for several hours, and now it proceeds through the install process.  I've already made it through language, keyboard, but it can't get past detect and mount cd-rom. I've tried at this juncture several times with now progress.  help!

---

### Post by aysiu on 2005-11-26
Sounds like a bum installer disk. Did you [verify the image](http://www.linuxiso.org/viewdoc.php/verifyiso.html) before burning it? Did you burn it at a slow enough speed?

---

### Post by homer39 on 2005-11-26
[QUOTE=aysiu]Sounds like a bum installer disk. Did you [verify the image](http://www.linuxiso.org/viewdoc.php/verifyiso.html) before burning it? Did you burn it at a slow enough speed?[/QUOTE]

I did not verify the image.  I downloaded the link md5summer.exe but I'm not sure exactly what to do?

---

### Post by homer39 on 2005-11-26
[QUOTE=homer39]I did not verify the image.  I downloaded the link md5summer.exe but I'm not sure exactly what to do?[/QUOTE]

well, i think i verified the iso image, but after attempting a reinstall, it is still getting stuck at the unable to mount cd-rom detection.

---

### Post by homer39 on 2005-11-28
ok, I switched cd-rom drives and it took me all the way to the part where it says to remove the cd and allow the remaining packets to be installed from the ide drive (hd).  
I did this but now when it tries to boot from the hard drive, it says drive not ready, then it attempts to boot from the secondary devices, which of course has no media.  
What to do now???

---

### Post by aysiu on 2005-11-28
[QUOTE=homer39]well, i think i verified the iso image, but after attempting a reinstall, it is still getting stuck at the unable to mount cd-rom detection.[/QUOTE] You *think* you verified it? What about when you reburnt it? Did you burn it at a slow speed (2x or 4x is ideal)?

---

