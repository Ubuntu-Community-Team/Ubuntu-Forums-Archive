---
title: "Camera No Longer Detected Since Beta Update"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2009-10-05
Hi,

Everything was going well with my USB camera and the integrated camera on my laptop until I upgraded to the BETA from Alpha 6. I used to be given choices of which to use in Skype and cheese but now I get messages saying that no camera is detected. When I run 'lsusb' I can see the USB camera listed, but nothing else is able to detect.

I read through the Cheese help info and it suggests there could be a problem the the gstreamer backend. Any thoughts what I should do to see if I can get this working or should I attempt to make a bug report at launchpad?

Thank you

---

### Post by victor9098 on 2009-10-05
OK...the problem seems to be booting up the laptop with the USB camera connected. I just restarted with the USB camera, ran cheese and got the integrated camera working. Then I plugged in the USB camera, restarted cheese and I could select both cameras again.

They both show up as options in Skype now too. This did not seem to happen under the Alpha 6 so something has changed somewhere. Will just put it down as a glitch and consider it solved.

---

