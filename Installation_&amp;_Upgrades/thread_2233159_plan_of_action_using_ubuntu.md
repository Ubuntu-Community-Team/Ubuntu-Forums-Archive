---
title: "plan of action using ubuntu"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by rbnjr on 2014-07-06
0) add special hard drive and load ubuntu, boot with drive,add software to drive,import all images and music to drive.

1) find my new hardware using ubuntu drivers on my mac pro. (2 pci hard drives from ozc called revo drives)

2) stripe raid zero array of the 2 drives.

3) clone special drive to the raid zero array.

4) boot up using new drives and ensure all this works using my current mac pro (2012)

5) load more software and add more hard drives.

ok i need to know if all of this is possible with Ubuntu ...

any and all comments welcome..thank you.

---

### Post by Bucky Ball on 2014-07-06
*Thread moved to **Installations & Upgrades**.*

Welcome. ***Forum Feedback & Help*** is specifically for forum issues, not tech support. 

PS: Yes, all looks possible, but what do you mean by 'special' hard drive? Either way, I'd go ahead and do it and if you hit any brickwalls or have any questions as you go, post in the appropriate support section (probably ***Installations & Upgrades***). Cheers and good luck. ;)

---

### Post by rbnjr on 2014-07-06
nothing really special about the "special" drive..just needed a name to call it..had i known Installations and upgrades was a section and could navigate to it i would has posted there.
this forum is a bit different from the common discussion forum layout..now back to the subject, if you believe this OS is capable of what i want perhaps a class for beginners like me to help locate simple things like the hardware installed on the machine for example. 
would be handy..so where do i find the section i need called "installations and upgrades"? i want to post more questions regarding my quest..thanks much for your assisiance and have a good week.
cheers!

---

### Post by Bucky Ball on 2014-07-06
In the first section ***Ubuntu General Support***, top of third column here:

[http://ubuntuforums.org/](http://ubuntuforums.org/)

Yes, these forums do run a little different to others. We have support areas and non-support areas and generally like to stick to one support request per thread. Less confusing that way. We also encourage users to post new threads rather than 'hijacking' threads by other users which might be about something similar to their problem, but 99.9% of the time it isn't the same. There are too many variables (for instance, hardware config, Ubuntu version/flavour, etc.). ;)

To identify your hardware:

```
sudo lspci
```

If you want to get specific, say with your network hardware, you can use:

```
sudo lshw -C network
```

You can replace 'network' with other things. For example 'video'.

My tip is to tackle each issue as it arises. Start at the beginning and when you get stuck, research. If no joy, post a thread with where you're at and all relevant details you can think of on a new thread with a descriptive title. This might not necessarily be in 'Installations & Upgrades'. Look for the most appropriate section on the link I provided at the beginning of this post to improve your chances of support.

Good luck with your plan of action.

---

### Post by Bucky Ball on 2014-07-07
Slight misunderstanding. I didn't mean duplicate post. ;)

I have moved this, your original thread, to ***Installations & Upgrades*** and deleted your duplicate. ;)

---

