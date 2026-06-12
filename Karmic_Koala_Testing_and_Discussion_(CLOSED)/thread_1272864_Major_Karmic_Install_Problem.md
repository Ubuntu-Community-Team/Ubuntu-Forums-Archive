---
title: "Major Karmic Install Problem"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ted Kord on 2009-09-22
Hi

I mistakenly upgraded to the 'Developmental' version of karmic. I marked all packages for upgrade and I think I ticked the unsupported packages box or something. Anyway, I restarted and now I can only get a blank login prompt. 

The also screen continually flashes (this is probably an nvidia problem) but the main problem is that during boot time, it says

"No resume image, doing normal boot"

1. Is there a way to roll back this upgrade?

2. Even if there isn't, is there a way for me to get access to my hard drive to copy my files. Then, I could reinstall 9.04.

Note: because the screen is flashing continually, it's virtually impossible to type my username and password at the login prompt.

Any help is appreciated as I'm dying here!! HELP!

Thanks

Ted

---

### Post by forumache on 2009-09-23
"No resume..." message is OK, it means it didn't find a resume image (put there by hibernate) so it will boot normally. Otherwise, it would have loaded the image and "resume" from hibernation.

About the flickering, it "should" stop after 5-10 flickers (when it realises that it cannot start graphical mode). Then, either you login in at the console and solve it somehow, or it will ask you if you want to start a "safe mode" graphical stuff. Your choice.

You can boot from an Ubuntu CD and access all your files.

---

