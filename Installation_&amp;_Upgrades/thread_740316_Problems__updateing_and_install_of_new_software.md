---
title: "Problems  updateing and install of new software"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by Rich West on 2008-03-30
I am newibie to the Linux, testing my feet in the other world of the computing . I have just installed Ubuntu 8.0.4 and I am having difficulty updating my system by the Start Package Manager or and to do a regular install for example adobe reader and java. This is the message I get when I am attemping to update my system; [COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.
[/COLOR]. [COLOR="Black"] Then when I tried to install Adobe Reader, I was told that wasn't possible because of another installation in progress [/COLOR] Actually complains that[COLOR="Red"] there can only one installation taking place at one time and that I must cancel and close other installation[/COLOR]s. Of course I have already done that, help, there has got be somebody who more of about than I do. 

Feel free to email me at [email]richwest@lycoc.com[/email]. Thanks

---

### Post by kellemes on 2008-03-30
Type from the terminal..
```
sudo dpkg --configure -a
```

---

