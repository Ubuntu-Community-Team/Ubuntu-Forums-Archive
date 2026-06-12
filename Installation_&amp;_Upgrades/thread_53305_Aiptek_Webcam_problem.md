---
title: "Aiptek Webcam problem"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by ePierre on 2005-07-31
Hi!

I just installed Ubuntu Linux on my sister's computer, and it works fine till there.
She has an **Aiptek Webcam**. This is a little Webcam that can also be used as a small digital camera. When I plug it, Ubuntu launches a little software that displays all the pictures stored in the meomry, so I can save them somewhere on my hard drive. Fine.

But I cannot use it as a webcam ! I installed Video4Linux, but when I launch GnomeMeeting, it doesn't recognize my webcam...

I saw there is a website with video drivers : [http://stv0680-usb.sourceforge.net/](http://stv0680-usb.sourceforge.net/)
But the project is not maintained anymore for 2 years, and I don't understand how to use these files... When I try to make, I just have an error, and can't go through...

Is there an easy way to make my Webcam work as a Webcam, and not as a Digital Cam?

Thanks in advance!

---

### Post by PokerFacePenguin on 2005-11-13
Did u ever get this working?  Trying to hook up my aiptek too.

---

### Post by PokerFacePenguin on 2005-11-13
I ended up just doing a "modprobe stv680" and loaded up gqcam...........voila it works.

I guess they loaded up the module for it somewhere along the way....now if I can just figure out where to use the webcam.....

Peace:cool:

---

### Post by javierfh on 2006-12-03
> **PokerFacePenguin said:**
> I ended up just doing a "modprobe stv680" and loaded up gqcam...........voila it works.

I guess they loaded up the module for it somewhere along the way....now if I can just figure out where to use the webcam.....

Peace:cool:

Hello,

do you still have the same camera?
Does it work properly? 
I have aiptek mini PenCam camera (well truth is, that mine it is called rimax, but looks exactly same and ubuntu detects it as aiptek) and well...it kind of works.
But the thing is, that camorama detects it..or at least i can see myself in camorama and i tried also camstreams and seems to work, at least i can see myself there. But then when using amsn, half of the times dont work...well to be honest, when in dapper at some point stopped working and since i moved to edgy only once worked, but the rest of the times shows something weird on the screen..

So can you use it with amsn?
All the help or tricks would be more than welcome.

Thanks in advance,

Javi

---

