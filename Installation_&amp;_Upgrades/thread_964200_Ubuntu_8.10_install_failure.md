---
title: "Ubuntu 8.10 install failure"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by mybrownianmotion on 2008-10-30
Hello! 
I have been unable to install intrepid on my computer. 
I am using the alternative cd installer, and the cd passed a verification test. The install works fine past the partitioner, then 73 percent of the way through installing the base system, it pops up a box saying " Please insert the disc labeled: 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)' in the drive '/cdrom/' and press enter. Media change.

I have tried the install several times but it stops at this point every time. Anyone have a solution?

---

### Post by Sef on 2008-10-30
Did you burn the iso at 4x or less?  If not, then reburn at 4x or less.

---

### Post by kipfel on 2008-10-30
I get the same error with the alternate cd. 
Downloaded (different mirror) and burned it twice already.

anyone?

---

### Post by mybrownianmotion on 2008-10-30
I reburned the disc at slow speed, but it still ran into the same problem, asking me to insert the disc halfway through base install. Anyone have any other ideas?

---

### Post by kipfel on 2008-10-31
> **mybrownianmotion said:**
> I reburned the disc at slow speed, but it still ran into the same problem, asking me to insert the disc halfway through base install. Anyone have any other ideas?

same here.

---

### Post by mybrownianmotion on 2008-10-31
Ok, I decided to go with 64 bit to see if it made a difference, I burned the 64 bit alternate iso, and installed, and had the exact same issue. It is asking me for my cd at 73 percent. :(

---

### Post by The Pinny Parlour on 2008-10-31
If you have a second optical drive laying about, try it instead.

---

### Post by mybrownianmotion on 2008-10-31
For some reason, using another optical drive worked, The optical drive I was using works fine so :confused: , but I was able to install using another cd drive. Thanks a lot!

---

### Post by The Pinny Parlour on 2008-10-31
> **mybrownianmotion said:**
> For some reason, using another optical drive worked, The optical drive I was using works fine so :confused: , but I was able to install using another cd drive. Thanks a lot!

Your welcome.  I'm very happy to hear you got it sorted out.  The reason I said to use a different optical drive is that I see this type of problem a lot on the job.  

:)

---

### Post by shawn_g on 2008-11-03
I am having the same problem, yet for some reason the desktop install worked fine but the server install will not work..

The base system keeps failing =(

---

### Post by shawn_g on 2008-11-03
Ok, Reburned CD @ 4x and it worked.. no idea but it worked so wow!

---

### Post by The Pinny Parlour on 2008-11-04
> **shawn_g said:**
> Ok, Reburned CD @ 4x and it worked.. no idea but it worked so wow!

I always check the MD5Sum on all my distro downloads. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Seems burning at a slower, more reliable speed did the trick.  :)

---

