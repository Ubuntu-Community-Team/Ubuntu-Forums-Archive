---
title: "Jaunty Not Allowing Login Due to Xorg issue"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-01-30
Hey:

I have always tested Ubuntu releases so this is not a complaint, merely a call for help in order to test the latest our distro has to offer.  I downloaded Alpha 3 and ran it off a Live USB/CD on an old HP Pavilion DV1000 series laptop.  It gets to login screen and when it automatically logs in to the main desktop, it shows some weird looking bars and goes back to login screen.  This continues to happen in an endless loop.  I am assuming its a Xorg issue here.  I tested it on a Virtual Machine and it works great.  

My laptop is a standard one so it doesn't have an Nvidia chip which has been causing more problems lately.  So, what could be it?

---

### Post by ronacc on 2009-01-30
it may be just about any video gpu not just nvidia they all have problems right now ,but none of that should affect the live cd because it should not have the accelerated drivers activated . can you get to a terminal session and run startx from there and see what happens ?

---

### Post by cariboo on 2009-01-30
Try running the LiveCD in safe graphics mode. Press F4 at the Menu screen to access it.

Jim

---

### Post by todd1814 on 2009-01-30
Take a look at what you have in /usr/local/lib.  Bad lib's will cause this problem.  I had something similar happen after a build of x11rdp failed.  It left some lib's in /usr/local but they were either bad or everything needed wasn't there.  Try moving any libs in that folder into a sub-folder.

---

### Post by entangled on 2009-01-31
On my Vaio VGN-FS115B (Intel 915GM) I had to run in Safe Graphics mode to get live CD to work. Normal Graphics was completely unusable, even for terminal access.
Strangely I found my 'odd' Mac Mini (Intel 945GM) worked without any trouble, right resolution too.

---

### Post by xerosis on 2009-01-31
There's known xorg issues which are still ongoing.

---

