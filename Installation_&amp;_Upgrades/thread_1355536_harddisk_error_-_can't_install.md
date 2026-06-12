---
title: "harddisk error - can't install"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by Angrylemur on 2009-12-15
I had Ubuntu working perfectly but it displayed an error message saying my harddrive was failing.  When I clicked to see more information about the problem, it failed to finish scanning and I ended up resetting the machine.

Now when I boot up, I get the platform option screen and select Ubuntu, but then the screen goes black and nothing else happens.

I've tried reinstalling Ubuntu but it won't finish the installation because it says "problem with the harddrive" or something along those lines.

I'm using the latest version of Ubuntu - has anyone else had this same problem?  Windows still will install and work fine, so I'm suspecting there really is no harddrive problem.

Thnx ^^

---

### Post by Angrylemur on 2009-12-15
I've come to think that this problem is not caused by my hardrive and rather by the new update everyone is complaining about.  I'm getting a similar black screen of death when I boot up - and many others have had the same after the update.

So the question is now: how do I get Ubuntu reinstalled with this harddrive error thing in the way of installation?

---

### Post by vikramk.ibs on 2009-12-15
I got the same error message on my laptop Compaq nx7300 model.

I simply ignored the message and thats all... my system is working fine.

---

### Post by Spaarkplug on 2009-12-15
Perhaps your hard drive is really failing, I installed the newest ubuntu on a failing hard drive and i got this message. And then, I installed in another old desktop with a hard drive with several bad sectors, and i got the same message again. 

I am not sure or heard of the new update issue which you have mentioned, but I have installed the koala on about 10 new or good computers in the past two weeks, and all of them work fine, with all current updates.

I am only sharing what I know. Perhaps you should do a diagnostics on that hard drive elsewhere.

---

### Post by presence1960 on 2009-12-15
> **Spaarkplug said:**
> Perhaps your hard drive is really failing, I installed the newest ubuntu on a failing hard drive and i got this message. And then, I installed in another old desktop with a hard drive with several bad sectors, and i got the same message again. 

I am not sure or heard of the new update issue which you have mentioned, but I have installed the koala on about 10 new or good computers in the past two weeks, and all of them work fine, with all current updates.

I am only sharing what I know. Perhaps you should do a diagnostics on that hard drive elsewhere.

you probably have some errors or bad sectors on your hard disk which is prompting the "drive is failing" message from palimpsest, which is also under System > Administration > Disk Utility

What you should do is go to your hard disk manufacturer's website and download a bootable version of their hard disk software. I have seagate and downloaded theirs. I had a lot of errors which the Long Test identified and gave me the option to repair. After that palimpsest says that disk is healthy.

If you don't want palimpsest to run at startup go System > Preferences > Startup Applications and untick disk notifications.

---

