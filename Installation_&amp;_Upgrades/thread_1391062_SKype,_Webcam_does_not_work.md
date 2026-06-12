---
title: "SKype, Webcam does not work"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by sushilsc on 2010-01-26
Hi,

         I have Ubuntu 9.10 installed on my dv2000 hp latpop.  I also installed the Beta version of Skype. But when I test webcam in skype the light of the webcam glows but I do not see image on the test screen. the test screen remains back.  Could someone suggest what could be the problem and a possible solution?

PS:  The webcam works fine with "Cheese".  

Thanks a lot.
with best regards,
sushil

---

### Post by phillw on 2010-01-26
Hi, skype are mindful of issues with Linux in general. Some Web-cams work okay, for others there are problems. Using the beta will keep you with the latest one.

The list of various web-cams and how they 'get-on' can be found over here --> [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Along with a good set of general resources to help get you going.

Regards,

Phill.

---

### Post by sushilsc on 2010-01-26
Hi,
Thanks for the information.  From where I can download the older version of skype?? I tried but did not find the weblink.

thank a lot.
with best regards,
sushil

---

### Post by Funkey Monkey on 2010-01-28
Hi sushilsc,

Try the following:
1) Open Skype > Options
2) Go the Video Devices section
3) Ensure that the "Enable Skype Video" box is ticked.
4) Then click on the "Test" button

I am able to "see" myself on my webcam

---

### Post by gradinaruvasile on 2010-01-28
> **sushilsc said:**
> Hi,
Thanks for the information.  From where I can download the older version of skype?? I tried but did not find the weblink.

thank a lot.
with best regards,
sushil

Do not download older versions - the beta is not really a beta - i use the 2.1 betas and had no problem with them whatsoever (on 6 computers, different hardware and Ubuntu versions) - the new ones have better sound quality, more features.
 
There is a workaround to the webcam issue - just launch skype like this:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a terminal. If works, modify the menu entry too with the menu editor.

---

