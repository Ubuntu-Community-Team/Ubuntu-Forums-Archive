---
title: "No USB devices detected"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by olmshoop on 2010-03-04
Hi,

I am just getting started with Ubuntu and love it so far.  It has breathed new life into an old Compaq Presario V2000 and once I get up to speed on it I hope to start running it on all the rest of our machines.

The only major problem I am having is that none of the USB devices I have plugged in are being detected.  From what I have seen online I should be getting a notification and should be able to view the devices at Places/Computer but so far, nothing.  Googling this problem it appears that individual devices often don't work but I could not find anything on _**all**_ USB devices not working.

Any ideas as to what I am doing wrong here?

---

### Post by quixote on 2010-03-05
First, dumb question: is the computer so old that maybe there's a hardware issue recognizing USB 2.0 devices, assuming that's what yours are?  Maybe it can't see anything beyond early USB 1.0?

You could also try attaching some of the devices, then opening a terminal (Accessories > Terminal) and typing "lsusb" (without quotes) and see if it lists anything.  (It stands for "list usb devices".)

If that comes up blank, the last thing I can think of to see whether the hardware is seeing anything to do with usb is to look at the boot log.```
sudo dmesg | grep -i usb > dmesg-usb.txt
``` That says "show me dmesg, but only the lines referring to usb, and pipe the output to dmesg-usb.txt.  The file will appear in your home directory.  Assuming the output isn't too long, you may want to copy that into your answer here.

---

