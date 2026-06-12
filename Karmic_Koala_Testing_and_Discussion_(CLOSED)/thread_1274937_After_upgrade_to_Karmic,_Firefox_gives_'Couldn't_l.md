---
title: "After upgrade to Karmic, Firefox gives 'Couldn't load XPCOM.'"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2009-09-25
Hi,

I upgraded from Jaunty to Karmic. On Jaunty. I already had Fx 3.5 installed. After upgrading to Karmic, Firefox does not work anymore. If I start Fx in the terminal, I get the following message in the terminal and Fx does not start:
```
Couldn't load XPCOM.
```

I really don't know what to do to solve this. I already purged and reinstalled firefox and xulrunner, I uninstalled packages from Jaunty which where still there, I looked into /etc/gre.d to see if the corresponding config files are available.

Can someone help me solve this issue, or do people around here have the same problem? I also filled a bug report on LP: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/436190](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/436190). However, I did not get a response on that report yet.

---

### Post by philinux on 2009-09-25
I know some people will say the opposite but I've never had good mileage from upgrades, especially if I've been doing a lot of fiddling and tweaking. I always do a clean install now. 

Home on it's own partition so I can be back up and running in 30 mins.

---

### Post by ernstblaauw on 2009-09-25
> **philinux said:**
> I know some people will say the opposite but I've never had good mileage from upgrades, especially if I've been doing a lot of fiddling and tweaking. I always do a clean install now. 

Home on it's own partition so I can be back up and running in 30 mins.

Well, I think I'll do that - as I have a separate home partition. But as this is the only problem, I still hope it is easy to solve.

---

### Post by philinux on 2009-09-25
Well I'd get rid of ubuntuzilla if it's installed.

---

### Post by philinux on 2009-09-25
Found this.

[http://ubuntuforums.org/showthread.php?t=967284](http://ubuntuforums.org/showthread.php?t=967284)

---

### Post by ernstblaauw on 2009-09-30
On [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/436190"), some guy commented it was the libnss3-0d package which interfered with firefox. As I reinstalled Karmic (not for this problem, but because resizing of my system partition failed), I can't confirm it, but the package seems familiar to me so I guess that was the problem. 
Thanks for all your help!

---

