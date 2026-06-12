---
title: "Interesting monitor problem with 11.04"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by grabbindrivers on 2011-05-06
Hello,

This upgrade to 11.04 has caused me nothing but trouble. If I would've known it would cause this many problems I would've just stayed with 10.04, which worked just fine. But since I can't go back now and I have too much stuff to feasibly back up and reinstall in any realistic amount of time I need to get these errors fixed.


One of the major frustrations outside of the nVidia error everyone is having, including myself, is an interesting problem dealing with my monitor. Two things happen:

1.) Booting up, the monitor will not take a signal after the BIOs boot up messages until the log in screen has been displayed. My monitor has an orange light when it is not active (like if I pull out a cable), but the monitor light stays green this entire time even though the screen is blank.

2.) If the computer hibernates or sleeps the same problem happens. The monitor will stay "on" but the screen will be black. If I remove the cable and plug it back in Ubuntu will display for a fraction of a second and then it will go black again. Likewise, if I power cycle my monitor Ubuntu will once again be displayed for a fraction of a second and then the screen will go black.


Is there anything I can do to remedy this? No Ubuntu up to this version has caused this. This is a major problem and enough to make me drop Ubuntu as a solution all together because it has cost me a few hundred lines of code that were unsaved when the monitor stopped working and the computer had to be restarted. Please post what logs you would like to see as well as I'd be more than happy to post them. Thank you.

---

### Post by Dutch70 on 2011-05-06
Have you tried other boot options? 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by grabbindrivers on 2011-05-06
> **Dutch70 said:**
> Have you tried other boot options? 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")


I added the nomodeset line and attempted to put the computer to sleep to replicate the error, however it didn't replicate. This is a good sign, but I'll update this later tonight after the computer goes to sleep by itself in order to confirm that part is solved.


Addressing #1 however, nomodeset didn't fix it. It still remains blank until the log in screen. No splash, no text boot up. Just blank. It will briefly flash "..................[OK]" where the dots are some boot check, but then it goes blank and won't come back until the log in screen is loaded. Any ideas on that?


EDIT: 

Did not fully fix the problem. Still hangs on a blank screen for a while on boot. Had to restart the computer twice to get to the log in screen.

---

