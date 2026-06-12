---
title: "Fiesty Kernel Panic"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by 2n01cal on 2007-04-29
I've just installed 7.04 x86_64 on my PC (AMD Venice +3000, Ga-KA8NXP-SLi, Ati X850 XT Sapphire, Ram 1GB KingMax, Sata 160 Seagate, Samsung 931c LCD monitor max resolution 1280x1024).
 And I am having trouble starting it normally. Just after I am pressing ENTER in Boot Menu..my screen goes black and CapsLock and ScrollLock blinks. 

There was the same problem with betas and alphas...but with Edgy was everything cool.
I guess the problem is in X as usual, because I am thinking Fiesty is trying to start in some crazy high resolution... 
But i can easily start Ubuntu in Recovery Mode. (And installation was easy also...I've changed resolution with F4, can I do the same trick in here?)
Can anyone recommend me some usefull commands to fix that. I am new to Linux.

---

### Post by 2n01cal on 2007-04-29
bump...

---

### Post by bulldog on 2007-04-29
Try in recovery mode```
sudo dpkg-reconfigure xserver-xorg
``` choose the desired resolution and the correct driver for your graphics.
I use nVidia so I'm not very well informed about ATI,but there should be useful postings on the forum,just do a search.

---

### Post by 2n01cal on 2007-04-30
Hmm...maybe the problem is not in Xorg but somewhere else...because it starts fine in recovery mode, with good resolution and etc...

And also one question. How can i see what is the problem...does it store some crash log on my PC? Because I wanna find out why its not working in normal mode, only in recovery.

My xorg file in the attachment.

---

### Post by bulldog on 2007-04-30
Did you install any driver for the graphics?

---

### Post by 2n01cal on 2007-04-30
No..I've made fresh install..and just after the installation I am trying to start it. And it's not working.

---

### Post by 2n01cal on 2007-05-01
bump...any way to debug this error?

---

### Post by arik23m on 2007-05-06
I have thae same problem with this Screen 931C Samsung..
i came here through google... is anyone Have any solution???

---

