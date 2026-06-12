---
title: "Jaunty - ATI video card"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by prem1er on 2009-03-24
Anybody having success with the ATI Mobility Radeon HD 3650 video card?  Never could get it working 'out of the box' with 8.10 and figured I would check if anyone has had success with it on 9.04 and the new kernel/x.org server. Thanks.

*I'm going to install alpha 2 when I get home from work.  I will post findings here if you are interested.

---

### Post by timmy334 on 2009-03-24
Your card is new enough that you should be able to use fglrx driver. My Mobility Radeon X600 is too old to use it :-(

---

### Post by prem1er on 2009-03-24
> **timmy334 said:**
> Your card is new enough that you should be able to use fglrx driver. My Mobility Radeon X600 is too old to use it :-(

Are you suggesting I follow this article?  

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Reiger on 2009-03-24
Nah. Do a search for fglrx in your package manager frontend of choice (Synaptic, Adept, Aptitude) and install what you need of those..

... Works with my HD4870 at least, so I guess the 3xxx series can only work better (being older and all that).

---

### Post by prem1er on 2009-03-24
Is the config file for the current video driver being used in Xorg.conf?

---

### Post by zika on 2009-03-24
I have ASUS ah 3650 (a.k.a. ATI HD 3650) and it works with radeon and worked with this new fglrx 8.600. just say if I could be of any help. for radeon You need just vanilla xorg.conf. it is almost also the case with fglrx because all the settings are done through aticonfig and amdpcsdb (or whatever is the name) ... just say what You need. You might want to read [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593) ...

---

### Post by homeriq5 on 2009-03-24
I have the same card and it seems to work fine, minus this weird lag that occurs when trying to maximize windows that were previously minimized. Try the latest alpha of jaunty, it finally worked for me when I tried recently.

---

