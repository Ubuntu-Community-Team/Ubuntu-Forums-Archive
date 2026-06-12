---
title: "Having a hard time installing Ubuntu"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by galay2 on 2015-12-04
So, I recently upgraded my motherboard and processor. Windows was a real pain to me so I decided to go with Ubuntu. However, I ran into more than a few problems with my installation:

When I tried booting without adding kernel params, the display flashed briefly, then the monitor turned off
-Added nomodeset to kernel params, screen resolution was funky, and froze halfway through the installation (got to the part where the top toolbar loads, background is gray, mouse is stuck)

After this, I did a bit more research, and tried changing and combining different parameters. Some errors I got were:

DRM fails to create channel -22
Unable to read directory block (squashfs)
Nouveau end trace errors
Asking me to login to tty on install (used ubuntu as username and it froze)
For the record, I did get this to work on my old motherboard and processor with everything else exactly the same

I tried to run a memtest, but it got stuck at 6% on the first pass

If any one has any suggestions, please help me!! I'm sorry I couldn't be more specific but if you need them I can try to replicate the errors.

Side note: I couldn't boot any OS properly, when I tried windows it just froze

I am using: Gtx 970 i7-4790k 16gb ram Z97-a mobo by Asus

If you need more specifics on specs I'll be happy to provide them

Thanks

---

### Post by ian-weisser on 2015-12-04
Seems like you need to do some hardware troubleshooting.

---

### Post by Bucky Ball on 2015-12-04
You might have a look at your RAM and make sure it is firmly seated. Pull them out and put them back in again. If you can get to a live session (try Ubuntu) you can check that all the RAM is being recognised. There might be a dud stick.

You can also try by pulling all the RAM out and inserting only one stick. Try them one by one and see if one of the sticks is dead or one of the RAM slots.

When did the option to login at a TTY appear?

---

### Post by galay2 on 2015-12-05
Thanks for all the suggestions, you guys were right. I played around with different RAM configurations and finally got it to work.

---

### Post by RobGoss on 2015-12-06
Glad you solved your problem, can you mark this thread as **Solved** thanks so much

---

