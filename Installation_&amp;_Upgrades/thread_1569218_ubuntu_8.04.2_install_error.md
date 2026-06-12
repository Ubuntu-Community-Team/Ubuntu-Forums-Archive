---
title: "ubuntu 8.04.2 install error"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by NIPACS on 2010-09-06
I have searched for answer to this question but cannot find one.

I am trying to install ubuntu 8.04.2 on my Acer TravelMate 290 but when I get to the install stage I get the error message "the file system creation in partition 1 of sci1 (0,0,0) (sda) failed".

Any suggestions please.

I am dedicating the entire HD to ubuntu, no windows and no dual boot.

Thanks

---

### Post by mörgæs on 2010-09-07
Rather than using 8.04.2 I would go for 8.04.4
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)
and use the alternate installer. 

Remember to have wired internet access while installing and to choose 'guided partition' (letting Ubuntu decide what is best).

---

### Post by NIPACS on 2010-09-08
> **mörgæs said:**
> Rather than using 8.04.2 I would go for 8.04.4
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)
and use the alternate installer. 

Remember to have wired internet access while installing and to choose 'guided partition' (letting Ubuntu decide what is best).

Thanks mörgæs for your suggestion, I've just tried with 8.04.04 and I got exactly the same error message.

Any other suggestions?

---

### Post by mörgæs on 2010-09-08
All right, so the easy test did not work...


I assume that the error message is 

the file system creation in partition 1 of [COLOR="Red"]**scsi1**[/COLOR] (0,0,0) (sda) failed

There can be several reasons for this, given that the install CD is working. First: If you boot a live CD, can you see the drive using Gparted? 9.10 or 10.04 might be a better choice than 8.04.

---

### Post by NIPACS on 2010-09-17
Thanks folks!

I have installed Ubuntu 9.10 Karmic Koala and everything is working like clockwork.

Although if I try to upgrade to 10.04.4 all hell breaks lose and I have to go back to 9.10 again. I suppose this must be a hardware issue as the laptop is about 6 or 8 years old, isn't it?

---

### Post by mörgæs on 2010-09-17
There can be many explanations, and I can not give a clear answer on that. Main thing is that it works. 

It happens a lot that older versions work better than the newest, but it is hard to convince people to give them a try.

---

