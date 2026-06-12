---
title: "Notification Area - Where did the speaker icon go?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by egruber on 2010-05-01
I upgraded to Lynx and the speaker icon is no longer shown in the notification area.  Everything works, though.  Any ideas?

---

### Post by matej on 2010-05-01
Install indicator-sound package and log off/on. I had the same issue.

---

### Post by egruber on 2010-05-01
I checked Synaptic and it is already installed. But I reinstalled it anyway.  It did not help.  One thing I should mention.  When I push the volume up/down buttons, I still get the graphic showing the volume change on the upper right of the screen. That always worked.  I just lost the notification area speaker icon after the upgrade.

---

### Post by deathblossom on 2010-05-01
Do you have indicator status on your panel? For some reason they stuck the the volume with the email  icon and you have to have both, even if you don't sync your email.

---

### Post by egruber on 2010-05-01
That was it!  The indicator applet put it back.  Don't know why I lost it.  It was always there.  Thanks for your help!

---

### Post by grnorris on 2010-05-06
That's kind of strange.  I didn't realize the difference between 'indicator applet' and 'notification area' before.  Apparently there was only one thing that appeared in my notification area that doesn't appear in my indicator applet so I just deleted the notification area.  Hopefully that will take care of things (it's also strange because the notification area showed a battery icon but only the one in the indicator applet actually works).

Edit:  I realized that my wireless icon has been disappearing and that is actually part of the notification area so, I re-added the notification area, only one battery icon (the one that works) showed up and everything appears to be working correctly with it again.

---

### Post by chiques on 2010-10-18
Indicator Applet fixed it for me too!

 Ubuntu 10.04 LTS
                - the Lucid Lynx

---

### Post by CaronMargarete on 2010-10-23
Adding the indicator applet only added the envelope icon for me, not the speaker icon. I've tried twice without success. 

Ideas?

---

