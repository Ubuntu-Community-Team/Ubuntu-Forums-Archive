---
title: "Solved Mandrake migration problem : &quot;Your session only lasted less than 10 seconds&quot;"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by Sauli on 2005-05-26
Before installing Ubuntu Hoary Hedgehog 5.04 to my Mandrake 10.1 system I first tried the live-CD. To my happy surprise everything worked fine.

When I made the proper install with the install-CD I had some unexpected problems.
I think the problems were related to my old Mandrake system. In Mandrake I used to have three partitions, Root (/), home (/home) and swap. I didn't want to delete my old home directory files so I decided to format only the root partition in the ubuntu installation. After the installation I got the login screen where I entered my name and password. Gnome didn't start properly, instead it told that "Your session only lasted less than 10 seconds ..." and  "Could not set mode 0700 on private per-user configuration directory ..." .

Based on some previous posts about similar problems I went to terminal (Ctrl + Alt + F1) and first tried to change the access rights to 777. I took me some time to realize that I coud not do it as a normal user but  instead had to use 'sudo'. Then it took me some more time to realize that the password 'sudo' expects is my own password, not admins or superusers. Actually getting 'sudo chmod 777 ...' work didn't solve the problem, but luckily it lead me to the right direction. I noticed that all the files in my old home directory had 501 as the owner. After changing them all (in /home directory 'sudo chown -R myname.myname mydirectory') I finally managed to start gnome a bit further.  Now gnome started half way with an error message "GConf error: No database available to save your configuration: Unable to store a value ... There are some common causes of this problem ... mistakenly created two gconfd processes". And yes, that was it, from 'ps aux | grep' I could see that I had multiple gconfd running, maybe because of my previous unsuccessful gnome tries. After killing them all I managed to start gnome. 

I hope this account helps somebody.

---

### Post by jonrkc on 2005-05-27
I feel sure it will help somebody.  In the past week, for one reason or another I've had to reinstall a couple of times (once during migration to a larger hard drive). The most common kind of problem I've run into has been permissions being wrong.  Your post will at least give some installers a clue what to check for.  In fact, I've got so that now, if I don't know the cause of a problem, permissions is the first thing I check.  If they turn out to be OK, at least I know there's some other cause for what's wrong.

---

