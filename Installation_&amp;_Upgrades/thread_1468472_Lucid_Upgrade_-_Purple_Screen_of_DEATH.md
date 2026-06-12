---
title: "Lucid Upgrade - Purple Screen of DEATH"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by zzyzx1 on 2010-05-01
Hello, sorry for another *HELP* thread... but i feel like i should be on the payroll if I have to work so hard and long to get these things working. (ranting stopped, for now)

I have ATI Mobility Radeon HD 4330 GPU in my Dell Zino system and finished the upgrade from 9.10 to 10.04 LTS and got the purple screen of death. tried the intel [recommended fixes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") but got nothing. I cant even get into recovery mode.

Any references or recommendation are appreciated!

Thank you.

---

### Post by skbhat03 on 2010-05-01
Do the following:

1. When you insert the CD and boot, you will get a screen with a small rectangle (keyboard) and a human figure at the bottom of the screen. When u arrive at that screen, just press any key, space bar will do.
2. You will get the language option, select English and press enter, you will be taken to a screen with options for installation.

3. Make sure the option "Try Ubuntu without any changes" is selected (don't hit enter yet)

4. Now press F6 on ur keyboard.

5. You will see a small pop up on the right hand side of the screen, just hit escape to make it go away. And you can see a long command line which is already there.
Just start typing 
i915.modeset=0 xforcevesa and press enter.

And from there it should work fine :)


Best regards,
Subbu.

---

### Post by zzyzx1 on 2010-05-01
Maybe i am missing a step from above, but your recommendation does not do anything for the 10.04 load on my hard drive, when i hit enter (your last step) it simply boots me into the CD... am i missing something?

Thank you.

---

### Post by zzyzx1 on 2010-05-01
i was able to interrupt boot and append i915.modeset=0 xforcevesa to the generic boot sequence after quiet splash, then ctrl-x to reboot. It did not work. Any others suggestions out there?? Please..??

Thank you.

---

