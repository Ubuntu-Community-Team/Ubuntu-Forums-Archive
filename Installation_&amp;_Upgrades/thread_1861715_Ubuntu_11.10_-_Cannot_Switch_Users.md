---
title: "Ubuntu 11.10 - Cannot Switch Users"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Smaress on 2011-10-15
Installed Ubuntu 11.10 yesterday.  Installation worked fine, however Ubuntu locks up when switching between user accounts.  Password prompt appears as expected however once entered the session does not change to the new user account.  Only option is to do a power off of the PC, shutdown does not work.  Any thoughts on how to fix? Thanks.

---

### Post by flawedmatrix on 2011-10-16
I think this might be a bug. I have the same problem as well. I cannot switch users because the password prompt locks up. For now, I guess the only alternative is to log off before changing users.

---

### Post by CraigK on 2011-10-16
Same problem here. i have to power off to log back in. Has anyone else sent a bug report to fix the issue?

---

### Post by michalsi on 2011-10-16
I confirm the problem. I have the same situation on both PCs with 11.10. I have to press Ctrl + Alt + F7 to get to my logged user and here I can restart it without power button. When I press Ctrl + Alt + F8 there is locked LightDM. Could you please someone report this bug? I haven't good English enough to do it. It happens when you have more users and try to switch to another user quickly through the upright menu.

---

### Post by mike1312 on 2011-10-16
Same problem 64bit version. Have to log out before switching to other user.

---

### Post by jorisjoris on 2011-10-16
Me2; recent distribution upgrades have been very buggy... :=(  (and unity sucks)

---

### Post by KillerSiafu on 2011-10-17
I too am having this same issue... attempt to switch user, enter the password, nothing happens.

I'll file a bug report when I get home if no one else has done it by then.

---

### Post by simonbutt on 2011-10-17
Same problem here.  Don't get on with unity either, will be following the youtube instructions soon on how to get Gnome back.

[http://www.youtube.com/watch?NR=1&v=YTtn4PPT1e8](http://www.youtube.com/watch?NR=1&v=YTtn4PPT1e8)

---

### Post by rizos on 2011-10-17
same here... is there a bug report done yet?

---

### Post by Smaress on 2011-10-17
Also, in reference to the previous post, the YouTube link shows how to get GNOME back using 11.04.  Doesn't work with 11.10.

---

### Post by bobemoe on 2011-10-18
Same here, can't find much info about it apart from this thread, and a [bug report]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/841351").

---

### Post by esoniat on 2011-10-18
An orderly shut down can be achieved by doing CTRL-ALT-F1 to get a console terminal, login, then "sudo shutdown -rf now"  This will shutdown and restart with out doing a file system check.

---

### Post by bobemoe on 2011-10-18
The link I posted earlier is a dupe of [this bug report]("https://bugs.launchpad.net/unity-greeter/+bug/835310"), which has a solution that has worked for me: Remove the package libpam-smbpass and reboot.

---

### Post by KillerSiafu on 2011-10-18
> **bobemoe said:**
> The link I posted earlier is a dupe of [this bug report]("https://bugs.launchpad.net/unity-greeter/+bug/835310"), which has a solution that has worked for me: Remove the package libpam-smbpass and reboot.

I can confirm this method worked for me as well.

---

### Post by m4rc310 on 2011-10-24
Same problem here! Also I have to enter "startx" to get graphical environment!

---

### Post by aztektum on 2011-11-23
I have the same problem, but rather than reboot, I CTRL+ALT+F1 and do

```
sudo service lightdm restart
```

I have not tried the above fix of removing the package.

---

