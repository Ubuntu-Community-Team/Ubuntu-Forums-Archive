---
title: "Just upgraded to 8.10 and firefox problems!"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by IreneMcKeever on 2008-11-01
I am about to lose it.  New to Ubuntu.  Upgraded to 8,10 firefox now not loading gets a page load error and the error console reads
failed to load XPCOM component: /usr/lib/xulrunner-1.9.03/compents/pyabout.py and failed to load XPCOM component: /usr/lib/xulrunner-1.9.03/compents/libpyloader.so

Day two update-my wireless connection says that it is working tried to install opera and seamonkey and get same message (page will not load)

Did the upgrade do something to the interent connection,

??

---

### Post by Rbchound on 2008-11-01
I am also having problems with firefox.  After upgrade my saved homepage loads then dims.  I have to force quit the application.  I am now using Swiftweasel until this is resolved.  I did switch sessions to Kubuntu desktop and the problem doesn't happen with firefox.
I also switch to the other kernel Linux 2.6.24-21-generic because I was getting that 4gb memory error at startup.
Next time I will just do a regular install instead of the upgrade.
Heck, if this persists I may just reinstall Hardy.

---

### Post by IreneMcKeever on 2008-11-02
Bear with me I am VERY new to this and a windows person.  How do I do that?  I just updated my post that any internet browser is not working and i am wondering if it did something to wireless connection even though the wireless connection indicator says that it is working??

---

### Post by LilyAyanami on 2008-11-02
> **Rbchound said:**
> I am also having problems with firefox.  After upgrade my saved homepage loads then dims.  I have to force quit the application.  I am now using Swiftweasel until this is resolved.  I did switch sessions to Kubuntu desktop and the problem doesn't happen with firefox.
I also switch to the other kernel Linux 2.6.24-21-generic because I was getting that 4gb memory error at startup.
Next time I will just do a regular install instead of the upgrade.
Heck, if this persists I may just reinstall Hardy.

I am also getting the dimming problem and the 4GB memory error at startup.  If you give it enough time, Firefox will undim and respond, but will periodically dim again and be unresponsive.  It is very frustrating.  In addition, I'm having problems with my DVD drive.  I am afraid of what else doesn't work :\

---

### Post by dgibsonky on 2008-11-02
I also have the 'dimming' problem.  It does not appear on every page; only some of them.  For instance, Gmail will do it every time.  As noted, it will eventually sort itself out and come back, then periodically "dim" again.  FWIW, I removed Firefox using Synaptic and installed "Seamonkey" with the same results.

---

### Post by bjorn_johansson on 2008-11-05
Hi, sorry for perhaps bumping, I recently made a fresh install of 8.10 and did all the updates, including (I think to FF 3.0.3). Now I can access all webpage EXCEPT gmail. This is driving me crazy! :confused:

---

### Post by ghjf345 on 2008-11-05
> **IreneMcKeever said:**
> Bear with me I am VERY new to this and a windows person.  How do I do that?  I just updated my post that any internet browser is not working and i am wondering if it did something to wireless connection even though the wireless connection indicator says that it is working??

You can go to System > Administration > Network Tools > Ping, then enter in the address field google.com and then click the Ping button. If the "Successful Packets" indicator reaches 100%, then it means your network is working fine.

---

### Post by dgibsonky on 2008-11-05
Hi guys--I was able to fix my issues by following the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=969845](http://ubuntuforums.org/showthread.php?t=969845)

I don't entirely get why Flash would affect Gmail, but it runs slick as a whistle now.  Good luck!

---

