---
title: "Logitech Quickcam Communicate STX breaks USB"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marcelkoopman on 2009-04-03
I've got a Logitech Quickcam Communicate STX webcam. I've noticed that the driver for this webcam (gscpa) doesnt work anymore.

What I get is: 
1) usb_set_interface failed
2) mouse stops working (a usb mouse, probably somehow is affected)
3) sound settings (alsa) are messed up
4) nothing works anymore, no keyboard, have to reset.

I replaced the webcam with my PS3 eye cam, which works perfectly.
No freezes anymore.

Did anyone else experience something similar like this?

I'm using Ubuntu 9.04 (8.10 also has this problem) and have a custom kernel 2.6.29 (older ones tried also).

---

### Post by Kareeser on 2009-04-03
I'm using that particular camera on 8.10 x86_64... no problems with mice, although I can't ACTUALLY use it.

I plug it in and it doesn't do much :)

---

### Post by marcelkoopman on 2009-04-03
> **Kareeser said:**
> I'm using that particular camera on 8.10 x86_64... no problems with mice, although I can't ACTUALLY use it.

I plug it in and it doesn't do much :)

I believe the kernel driver for this is broken.

---

### Post by Kareeser on 2009-04-03
Upon followup with Ekiga, the webcam works perfectly.

Sorry about that ;)

---

### Post by Vico Vicario on 2009-04-04
I have a Logitech webcam that uses gspca driver and it is working in Jaunty.

Your problem is related to usb port not being able to reconfigure, not to gspca. Maybe you could try a different usb port, or try issuing a lsusb command before starting the video application.

V.

---

### Post by Sef on 2009-04-05
Moved to Jaunty Forum.

---

### Post by markbuntu on 2009-04-05
My logitec quickcam communicate stx works just fine in jaunty.

---

