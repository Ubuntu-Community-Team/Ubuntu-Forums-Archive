---
title: "No proprietary drivers are in use on this system"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-10-14
I had a working setup and the latest update caused problems. 

My current problem is that System - Administration - Hardware Drivers lets me know that ¨No proprietary drivers are in use on this system¨. And it does not show any installed drivers to activate. But I downloaded and installed the nvidia-glx-185 driver through Synaptics.

My graphics chip is GeForce 6100
Kernel in use 2.6.28-11-generic

Michael

---

### Post by forumache on 2009-10-14
I had/still have the same problem.

I'll check when I get home. I think I solved it by adding nvidia-modaliases or something. I don't remember, but in a couple of hours I'll post back.

---

### Post by ikisham on 2009-10-14
nvidia-modaliases is what makes Jockey (the proprietary driver manager) see the drivers you need and tell which one you have, so if it isn't installed you have the driver working but it wont show up in System - Administration - Hardware Drivers.

---

### Post by NRDNick on 2009-10-14
I was having this issue as well, and installing the modaliases did correct it. Just curious do the modaliases do anything other then let Jockey see the driver you have installed?

---

### Post by ikisham on 2009-10-14
> **NRDNick said:**
> I was having this issue as well, and installing the modaliases did correct it. Just curious do the modaliases do anything other then let Jockey see the driver you have installed?

no (not that I know..if you see its description in Synaptic it says that it can be safely uninstalled).

---

### Post by Yumi on 2009-10-14
Thanks, your advice solved my problem.

Michael

---

### Post by ranch hand on 2009-10-15
Then, for other folks sake, you ought to mark this thread "Solved".  Under Thread Tools at top of this page.

---

### Post by Yumi on 2009-10-15
Actually, I did. I shows as (solved) in my initial article, but for some reason not in the forum.

-Sorry, learned something new. I always edited the subject line as (solved). But the function is actually in the ¨Thread Tools¨. 

Michael

---

### Post by forumache on 2009-10-15
> **Yumi said:**
> Actually, I did. I shows as (solved) in my initial article, but for some reason not in the forum.

Michael


You edited the title of your first post. This is not enough.
You have to use the special item under "Thread Tools" at the top of the page. Only the thread opener (i.e. you) can do this.

---

