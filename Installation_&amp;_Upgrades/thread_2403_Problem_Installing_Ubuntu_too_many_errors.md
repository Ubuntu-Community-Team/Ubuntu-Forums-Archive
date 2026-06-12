---
title: "Problem Installing Ubuntu too many errors?"
date: 2004-10-27
forum: Installation &amp; Upgrades
---

### Post by adept22 on 2004-10-27
Heya ppl. Just downloaded the 4.1 Warty release of ubuntu and having some problem with the install. Im fairly new to linux and not that experienced so any responses please bear that in mind O:) 

It goes the the base install fine no problems, its just when the machine reboots and it goes to install what i think is the X11 packages and gnome etc it comes up saying processing was halted becuase there were too many errors.

I can log into the machine fine and everythign seems to work except for X which is what i think is bombing out on the install process. Can somebody please help?

---

### Post by Rancoras on 2004-10-27
You're going to have to give us the errors you're getting in order for us to help.  Your system specs would help as well.

---

### Post by adept22 on 2004-10-27
How do i  find out what the errors are? are they posted to a log file? as evetrything flows on the screen too fast for me to see the errors. and all i see is the Too many errors occured message.

Also P4 512mb Ram, 80gig hdd, onbard video (asus p4800s mobo)

---

### Post by Rancoras on 2004-10-27
Look through the output of the dmesg command.  See if there's anything unusual looking about the video or display.

---

### Post by adept22 on 2004-10-27
Nope cant appear to see anything  in the dmesg log.. complete head scratcher as im not sure where else to look. the errors that occured during the install process would thye be posted to a install.log or sum such thing??

---

### Post by jdong on 2004-10-28
try an **apt-get install ubuntu-desktop**. Upon an error, hit CTRL+C, then they should be pretty darn visible.

---

### Post by adept22 on 2004-10-29
Thanks everyone, turns out it was a CRC error from when it was installed. I cleared the apt-get cache,  redownloaded the needed packagees and it worked a treat!

yay

Cheers

---

