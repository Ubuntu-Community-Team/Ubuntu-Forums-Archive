---
title: "No Administrator files will execute"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by orcamarine on 2010-03-02
Hi Everyone, and thanks for your help in advance, I am new to Ubuntu and linux in general and have come across a little problem which may be my fault but I cant seem to rectify the problem which is as follows, everytime I try to enter any of the admin controls ie update manager etc the window opens for a split second then crashes also if the sound is turned up or down via keyboard shortcut the sound bar starts flashing very fast and the keyboard becomes inoperative, I have tried rebooting etc with no avail, I have done everything that I can with my very ltd knowledge, this first started after the last update I am using 9:10 KK. 
Any help is greatly appreciated.

---

### Post by cigtoxdoc on 2010-03-02
I have samje problem.  I have tried to get help; but no one seems to know the answer.

I can get by using Failsafe GNOME or logging in to GNOME as root.

John

---

### Post by orcamarine on 2010-03-03
Hi john, thanks for info I will try that, but if anyone has an answer that will be great.

---

### Post by sisco311 on 2010-03-03
What happens when you try to use sudo/gksu/pkexec in a terminal? Do you get any error messages?
```
sudo echo "sudo"
gksu echo "gksu"
pkexec echo "pkexec"
```

Does update-manager return any error message?
```
update-manager
```

---

### Post by orcamarine on 2010-03-03
Hi Sisco,
Thanks for your time, I have this error code,
(update-manager:8652): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-chguacAD9q,guid=4839918c80a06b748836408a4b743fdd failed: Failed to connect to socket /tmp/dbus-chguacAD9q: Connection refused.
Segmentation fault

Many Thanks

---

### Post by orcamarine on 2010-03-03
Ok I think I may have worked around it(although not sure how doh sorry), In the red warning triangle on the task bar there is an option to change servers, my local was guernsey, I changed that to main server and clicked the option to automatically install security updates, this has now allowed the update manager to work and is currently installing 46 updates 8-) 
Hopefully this might shed some light on it somewhere, sorry its not more indepth I was just clicking away lol

---

