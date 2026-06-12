---
title: "Ubuntu 16.04 Live USB not starting after update."
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by Halpm on 2016-05-12
Just out of interest, did this ever work out for the op? I'm trying to run an updated live USB of 16.04 with an updated kernel, because I can't run my hardware with the original kernel (the computer overheats and shuts down after about a minute), and I want to check if it's fixed in the newest kernel. I get the same error message as the OP.

---

### Post by sudodus on 2016-05-12
> **Halpm said:**
> Just out of interest, did this ever work out for the op? I'm trying to run an updated live USB of 16.04 with an updated kernel, because I can't run my hardware with the original kernel (the computer overheats and shuts down after about a minute), and I want to check if it's fixed in the newest kernel. I get the same error message as the OP.

This thread is old, and the original poster never returned. So I will ask a moderator to move your post and my post to an own thread.

There might be a solution for you: Download the trusty daily iso file, which has an updated kernel, and try if it works for you. You can also try the daily 16.04 LTS or even the daily Yakkety iso files. 

[64-bit version trusty daily](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/119174/downloads)

[32-bit version trusty daily](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/119176/downloads)

***Edit:*** The iso testing web site: [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

---

### Post by howefield on 2016-05-12
Posts moved to own thread as requested.

---

### Post by Halpm on 2016-05-16
Blimey - all this time doing this, and it never crossed my mind to look for a daily image - cheers. I'll give it a go :)

---

### Post by sudodus on 2016-05-16
Please keep us informed of the result - Good luck :-)

---

### Post by matey3 on 2016-05-17
gee I wonder which program causes the overheat? reminds me of my Samsung phone, I did an update on some of my apps (not the OS) and it started to get hot and ran the battery down quick (maybe in 20 to 30 min.) 
I am no expert but can you like do a ps and see? is it really the kernel file? 
this is interesting. I was just going to ask if I should upgrade from 12.04 on my desktop pc....I'll wait n see.
thanks.

---

### Post by Halpm on 2016-05-27
No, still no luck booting from the USB, not even with the latest daily from the 27th may. Fan just goes crazy and the machine turns itself off after about a minute. If anyone has a brainwave, then I've got a thread on this problem here: [http://ubuntuforums.org/showthread.php?t=2321724](http://ubuntuforums.org/showthread.php?t=2321724)

---

### Post by Halpm on 2016-05-27
.

---

### Post by Halpm on 2016-05-27
> **matey3 said:**
> gee I wonder which program causes the overheat? reminds me of my Samsung phone, I did an update on some of my apps (not the OS) and it started to get hot and ran the battery down quick (maybe in 20 to 30 min.) 
I am no expert but can you like do a ps and see? is it really the kernel file? 
this is interesting. I was just going to ask if I should upgrade from 12.04 on my desktop pc....I'll wait n see.
thanks.

How do you mean a ps? If you tell me how, then yeah I'll do one :smile:

---

### Post by ubfan1 on 2016-05-27
In a terminal (ctrl-alt-t to pop one up) type ps ux  to see your processes, cpu % is col 3.   However, the top command might be more useful to pick out excessive cpu use, it's sorted.

---

