---
title: "Today's Lucid A3 update crashed my system."
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by drs305 on 2010-03-10
I did a fresh install of A3 yesterday after not being able to move from nvidia to nouveau drivers.

The fresh install went well and I ran all the updates. The nouveau drivers worked well, and the only problem I was having was the 'ureadahead' issue on boot. I had to hit ENTER to get the boot to proceed past the black screen and manually log on. After that things ran well.

Today's update now boots to an empty Destkop screen, where dual cursors slowly migrate across the screen and leave a black trail.  The only way to exit was to poweroff.

So far, the remedy for me was to boot in safe mode and remove plymouth from the command line. This allowed me to boot normally once again.

I know today's update was going to work on the *ureadahead* problems. I don't know if this was related or not, but whatever the cause I just wanted to provide a method to fix it should it happen to you.

amd_64
nvidia 7600GS

---

