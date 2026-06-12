---
title: "Change time to check for updates"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by feedmecereal on 2008-08-20
How do I change the time that Ubuntu checks for updates? It currently checks for updates at about the time that I wake up but I want it to check sometime in the middle of the night when I am asleep.

---

### Post by Partyboi2 on 2008-08-21
You could use cron and setup the time of day you want your machine to be updated. Here is more info:
[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
[http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm](http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm)

---

### Post by newOldUser on 2009-06-19
Assuming you leave your machine on all the time....

Read this: [http://gaarai.com/2009/03/18/changing-when-daily-cron-jobs-run-in-ubuntu/](http://gaarai.com/2009/03/18/changing-when-daily-cron-jobs-run-in-ubuntu/)

Then using a terminal and the sudo command invoke a text editor on /etc/crontab

change the 'hour of the day', 2nd field from left, to some other hour like 2 or 20

save the changes and you should be okay.

---

