---
title: "Unable to install inside windows XP"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by mchaley on 2011-04-03
I'm trying to install 10.10 but it keeps throwing an error. I'll include the error and log file below:

An error occurred: 
Permission Denied 
For more information, please see the log file: c:\...

---

### Post by mchaley on 2011-04-03
I should also add that I've burned two disks with the same error. It boots to Ubuntu fine and only throws this error at the very end. 

Not sure what the issue is or how to fix it.

---

### Post by MButterman on 2011-04-03
It appears as if you might have the 64 edition and if I am reading this right, the pentium D is only a 32 bit with hyperthreading.
 
XP had a 64 edition but it didn't have much momentum comercially. This doesn't say the program you used to burn it with. XP has some burning utilities but are very basic and wouldn't including burning iso's. Google for checking the checksums of the cd's burn. Try reloading. [www.ubuntu.com]("http://www.ubuntu.com") is the most trusted source for the iso you require
 
Personally, I don't use wubi and use Oracle Virtual Box to install a system to. It won't mess with any of the XP internal programming.

---

### Post by bcbc on 2011-04-03
Errno13 is usually a bad burn or incompatible burning technique or even an incompatible optical device. You can boot from the CD, press space when you see the keyboard icon bottom centre and then from the advanced menu run "Check disk for errors".

But the easiest way to install wubi in this case is to copy the wubi.exe file and the downloaded .iso file into the same folder and run wubi from there.

---

### Post by mchaley on 2011-04-03
> **bcbc said:**
> Errno13 is usually a bad burn or incompatible burning technique or even an incompatible optical device. You can boot from the CD, press space when you see the keyboard icon bottom centre and then from the advanced menu run "Check disk for errors".

But the easiest way to install wubi in this case is to copy the wubi.exe file and the downloaded .iso file into the same folder and run wubi from there.
Didn't know you could do that - trying it now

---

### Post by racie on 2011-04-03
> **mchaley said:**
> Didn't know you could do that - trying it now

Wubi installs Ubuntu like a program.  You can uninstall it with the click of a button in your control panel in Windows.  The only downside to Wubi would be if you want to keep Ubuntu and eliminate Windows... it's definitely more complicated because Ubuntu isn't installed to it's own partition.  However, if you're planning on keeping Windows, then it's certainly a great option.

---

### Post by mchaley on 2011-04-04
> **racie said:**
> Wubi installs Ubuntu like a program.  You can uninstall it with the click of a button in your control panel in Windows.  The only downside to Wubi would be if you want to keep Ubuntu and eliminate Windows... it's definitely more complicated because Ubuntu isn't installed to it's own partition.  However, if you're planning on keeping Windows, then it's certainly a great option.
Yep, just want to learn more about linux at this point. That trick worked - installing wubi with iso in the same folder. Thanks for the tip!

---

### Post by fudoki on 2011-04-04
wubi installs Ubuntu in a large file on your Windows partition.  Running defrag before installation will make wubi perform better - the large file won't be broken up into as many pieces.  Also, avoid installing wubi on a VFAT partition, NTFS is a lot faster.  Remember, Ubuntu is having to rely on the underlying Windows system for its file access, printer support, etc - so the more you can optimise your Windows setup, the better wubi will run!

Remember this, because Ubuntu installed "native" (not inside Windows) will run 4 to 12 times faster!  Linux is not deliberately slowed down to sell Intel chips like Windows is...

Finally, on the architecture issue, you should only have 32-bit Ubuntu using wubi.  32 or 64 bit Windows will run it fine.  64-bit Windows will run it much better, obviously, much more power.  Running a 64-bit OS using a virtual machine or wubi on a 32-bit Windows machine will cause the use of software emulation - that's spelled S-L-L-O-O-O-W-W....  Very slow.

Your best bet is to spend $50 on a second hard disk and install Linux on it - then you can see what a slow slug Windows is by comparison on the same machine!!! ;)

---

### Post by bcbc on 2011-04-04
Wubi does run a little slower, but it's because it uses a loop device instead of a regular partition. But it's not a VM - it makes full and direct use of the computer hardware. So it doesn't matter whether windows is 32 or 64 bit. You can run 64bit wubi if it's supported (this is the default for wubi.exe when run standalone i.e. when it has to download the ubuntu desktop image itself).

---

