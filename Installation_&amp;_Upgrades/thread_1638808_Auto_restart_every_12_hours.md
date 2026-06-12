---
title: "Auto restart every 12 hours"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by lipstick31 on 2010-12-06
Hello and congratulations for the forum.
 
I am a new user of linux platforms ( i have ubuntu 10.04) and i am totally satisfied from this platform .You can do everything you want without needing previous linux or programming experience.
 
I have the following question
 
Is there any bash script that makes an auto restart to the computer every 12 hours without needing my credentials to enter to the OS?
 
Thanks in advance

---

### Post by AbeJarano on 2010-12-06
Use crontab as super user.  Google for examples of super user scripts or writing simple bash scripts.

---

### Post by pricetech on 2010-12-06
Pretty sure an entry in /etc/cron.daily will take care of it.  Just look at the files in there for examples.

---

### Post by efflandt on 2010-12-06
In a terminal see **man crontab** and **man 5 crontab**

Edit crontab as root (chose nano as editor if not familiar with ed or vi):

```
sudo crontab -e
```Example of an entry that would reboot at 6 AM and 6 PM with 5 minute warning to give users time to close what they are doing (ie, 5:55 +5):

```
55 5,17 * * * /sbin/shutdown -r +5
```I have a headless IPCop squid proxy at work (K6/2-400 w/128 MB) that I have set with crontab to reboot once per week.  Although, that might not be necessary, because I have a Celeron 300 in my basement that has been running SuSE 8.2 24/7 without booting since 2006.

```
efflandt@realhost:~> ls -l /var/log/boot*
-rw-r-----    1 root     root            0 2003-05-17 18:03 /var/log/boot.log
-rw-r--r--    1 root     root        20461 2006-07-20 16:00 /var/log/boot.msg
-rw-r--r--    1 root     root        24670 2006-07-20 04:45 /var/log/boot.omsg
```

---

### Post by lipstick31 on 2010-12-07
Thank you guys for your help!!!!!!! It works succesfully!!!

---

### Post by pricetech on 2010-12-07
Cool.  Please mark your thread as solved so others will see it as a solution.

---

