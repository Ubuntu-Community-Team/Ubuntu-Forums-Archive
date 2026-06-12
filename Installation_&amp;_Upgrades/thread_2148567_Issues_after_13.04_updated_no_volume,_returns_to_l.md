---
title: "Issues after 13.04 updated: no volume, returns to login screen and does not shut down"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2013-05-25
My wife's HP Pavilion G6 running 13.04   3.8.0-21 64-bit fully up to date.

After upgrading from 12:10 to 13>04 the laptop worked fine.  It then did an upgrade and since then it has developed a problem:

It keeps returning to the login-in screen, which then requires logging in.  All work is lost in the process. This happens a lot as apps are opened, in the midst of using them, no pattern determined as yet.

Any ideas, please?

---

### Post by Jonners59 on 2013-06-06
Any help, someone, please!!!!!!!!!!!!!!!!!!):P

---

### Post by oldfred on 2013-06-06
Is it overheating? That often causes a reboot. 
What gui are you using? 
I use fallback or gnome panel as my old monitor is 4:3 where laptops now may work better with the Unity panels on the side. But Unity does use more resources.

---

### Post by Jonners59 on 2013-06-07
Hiya Oldfred
It doesn't go into reboot, it goes in to the Login Screen.
It does not have a pattern, other than, in my experiences when an application is opened.  Any application, and randomly.  I.e. could be working away opening up applications and using them and then suddenly when opening the next application the screen goes blank and the next thing seen is the login Screen.  All work is lost and it is as if it is a fresh login, so Auto Start applications open and those open before are shut down and any work lost.  This could happen on the first application opened or after some time

No the machine is not hot.  It could happen at the start or after 20 minutes.

Yes, I am by default using 3Gnome of xfce on Kubuntu.....  Do not like Unity

Is there a command I should run to create a log...?  What do you think it could be?

Thanks for popping in...  Jonners

---

### Post by oldfred on 2013-06-07
There are a lot of log filesin /var/log, but I use log file viewer which may not be in your version?
I have only really looked at dmesg which has the startup info to see if something did not load correctly. But there are many other files and folders with logs that may be just one app in the background that fails? And whether something gets written or not may also be an issue.

---

### Post by Jonners59 on 2013-06-09
so how do i go about finding out...?  What can I do?

---

### Post by oldfred on 2013-06-09
Did you look at the log files in /var/log? There are many to review. And you look for errors, warnings, or long times between tasks that should not have a long time.
I normally have just reviewed dmesg which is the boot process. A long time between entries may indicate an issue, a repeated try and failure may indicate an issue.
Not sure what other log files may post but all I can suggest is to look for one's related to the devices you have issues with.

---

