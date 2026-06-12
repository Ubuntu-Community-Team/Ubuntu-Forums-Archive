---
title: "Unable to load Ubuntu 12.04 was due to Nvidia driver"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2014-02-04
Last night after a program manager  update I restarted Ubuntu and it just hung. 

I have fresh reinstalled about 4 times today and it seems the video driver is the cause. 

Each time I tried to access the the dual monitor, the second monitor was not recognised. The system was being  described in Display, as a laptop with one screen only.

I  opened the update drivers app and found that if I changed the default from Nvidia 173 to 304 (the recommended driver) I could not get into ubuntu. The system would hang before I had logged in. My card is a GeForce 7600 GS and until last night I had no problems with running the two monitors. 

Has anyone else experienced this problem and what have you done to over-ride it?

At the moment I can only use one monitor and I do not like that at all.

Robin

---

### Post by grahammechanical on 2014-02-04
When we use a proprietary video driver the Displays utility is not active. Instead we get a settings manager from either Nvidia or ATI. Search the Dash. I have had problems in the past with Nvidia drivers breaking the desktop. I now use Nouveau all the time. I have also heard stories (how true I do not know) of Nvidia dropping support in the newest drivers for old graphic cards. I only have one monitor by the way.

Regards.

---

### Post by Robbyx on 2014-02-04
The Nvidia X server only shows one monitor!

Do you find Nouveau to be good. I have tried them in the past and they had their faults, and somehow I would get the Nvidia driver to work, but not this time.

---

### Post by ibates on 2014-02-06
I have what could be a similar problem.  I have been operating normally on Ubuntu 12.04 updated, since it was released, but about a week ago, I loaded the nVidia drivers.  All seemed OK for a few days, but then a few days ago, Ubuntu would not load.  I was left looking at a whole heap of *no irq* lines and then a black screen with a stationary cursor in the top left hand corner.  No response from anything.  Only a hard reboot would get any action - right back to the same situation.

I can boot with no problems on the LiveCD, and can access any file on the "failed" HDD.  But of course, I cannot open any App on my normal drive.

Is this likely to be the nVidia driver?  What else could it be?  And if i is possible that nVidia is the culprit, how can I uninstall it on a HDD to which I cannot boot?

---

### Post by Robbyx on 2014-02-06
I am using Nouveau and it seems to work well. Just untick (remove)  the additional nvidia drives and it will default to  Nouveau. I could then set up the dual monitors.

---

