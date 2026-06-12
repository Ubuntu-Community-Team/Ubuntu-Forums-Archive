---
title: "can't read camera pics in hardy"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by jgoldstick on 2008-05-19
I just got an mpc transportx3000 and loaded clean ubuntu (hardy).  Using gthumb I couldn't import pics.  It gave error message can't read camera.  Weird thing is one day it worked, but not now again.

I have an HP photosmart camera.  I also tried fspotwith similar results.  

what to do?

Joel Goldstick

---

### Post by GregA on 2008-05-19
OK, you have the pics in your Camera memory.  And you have the USB mini-cable that came with the camera?   Have you tried these things:
>  Attach the camera with PC off and boot up, log in.  Do you get a pop-up window listing the device, that you can click on to read the files in nautilus or Konqueror?
>  Same as above, but this time, attach the cable (with camera on of course), while PC is on.   Do you see a device pop-up window?
>  Have you tried just reading in the card?  I'm not familiar with your laptop, but if you don't have any ports for the memory card (SD, XD, etc), can you pickup a cheap MMC reader from Walmart or similar store?  They're only 10 or 15 dollars, and come with USB mini-cable that you hook up to your laptop, and then you insert the card into the MMC.

Since digital photos are jpg or similar default file type, there really is NO requirement for any special camera or photo software (in Linux or Windows) to get to those files and copy them to your hard drive.  Then you can use many applications to work with the files.

---

### Post by jgoldstick on 2008-05-29
The device doesn't show up.  But, when I reboot to WinXP I can read the pics in.  This solves my immediate problem of downloading my files.  Then I copy them from windows since I have access to the disk when I boot In Ubuntu.

But, I would rather it just worked.  It doesn't show up as a removable drive at all.  On my other Ubuntu machine, which is running Fiesty, this worked fine.  Since it works for Windows, I figure the cable is good.  Any other thoughts? or tests or is there a log file I could copy and post here?

thanks

---

### Post by viljun on 2008-05-29
Is it recognized any more? type 'lsusb' into terminal. is it mounted? type 'mount -a'

---

### Post by jgoldstick on 2008-05-29
result of lsusb
Bus 001 Device 005: ID 03f0:4002 Hewlett-Packard PhotoSmart 720 / PhotoSmart 935

I did the mount (needed to sudo)

when I start gthumb and try to import I get the pop up and it says: an error occurred in the io-library.. No error description available

---

### Post by viljun on 2008-05-30
Oh... sorry, i mean just 'mount' to see if it's mounted automatically or not, not 'mount -a'. 

what did 'mount' command output?

---

