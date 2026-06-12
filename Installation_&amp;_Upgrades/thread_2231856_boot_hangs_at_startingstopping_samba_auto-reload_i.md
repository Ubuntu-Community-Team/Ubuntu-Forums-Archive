---
title: "boot hangs at starting/stopping samba auto-reload integration"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by sataylor56 on 2014-06-28
I posted this on the Kubuntu forums but have not had any replys. Thought I'd try here also. My system has been running fine until I had a problem with MySQL. I have been trying to purge MySQL and reinstall it. I have been having problems getting the reinstall to work but I finally got it to the point where the MySQL server would start. Now I have tried to reboot my computer and it won't finish booting. From the splash screen I hit F1 and the last items shown are "starting samba auto-reload integration" and then "stopping samba auto-reload integration." Then it just hangs there seemingly forever. I can login to the command line on one of the terminals and the system is running, it just won't fully boot to the GUI. What can I do to get it working?

---

### Post by sataylor56 on 2014-06-28
I should have added that I am running 14.04 which I had updated from 13.10, which in turn had been updated from 12.04.
Thanks,
Steve

---

### Post by sataylor56 on 2014-07-06
It turns out this had nothing to do with my MySQL problem and was related to some of the latest 14.04 upgrades. I followed the advice given in another thread:
[https://www.kubuntuforums.net/showth...Kubuntu-update](https://www.kubuntuforums.net/showth...Kubuntu-update)

 Also, try re-installing kubuntu-desktop
 sudo apt-get install --reinstall kubuntu-desktop
 It will pick up missing dependencies and config files. 

 This solved the problem and got me back to the desktop.

---

### Post by andy74 on 2014-08-12
The link you pasted is broken.  I'm having this issue and is blocking me getting work done.  Please please what's the solution to this issue?

---

### Post by hamshan33 on 2014-10-11
I am having the same issue. At the risk of opening a new thread I want to bring this up.

I cannot boot into ubuntu. I have 14.04. The problem started after removing gnome desktop. 
I was using kubuntu or unity as desktops and it boots using kubunto.
I have tried to install it back, and do package update with a live CD but it never worked.


It usually hangs at "Samba auto-reload Integration", or If I wait long enough at "Read required files in advance", 
or sometimes it shows this unreadable message: "anac(h)ronistic cron"???

I have also tried the method descried here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but it did not work.

Thanks for any help.

---

### Post by hamid3 on 2015-04-24
> **hamshan33 said:**
> I am having the same issue. At the risk of opening a new thread I want to bring this up.

I cannot boot into ubuntu. I have 14.04. The problem started after removing gnome desktop. 
I was using kubuntu or unity as desktops and it boots using kubunto.
I have tried to install it back, and do package update with a live CD but it never worked.


It usually hangs at "Samba auto-reload Integration", or If I wait long enough at "Read required files in advance", 
or sometimes it shows this unreadable message: "anac(h)ronistic cron"???

I have also tried the method descried here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but it did not work.

Thanks for any help.

Although you might have most probably got that solved, I put the solution worked me here for possible future references.
Try this:
When your machine stops at  "Samba auto-reload Integration" which is also [OK] (!), press 'Alt+Ctrl+F1' to navigate to tty1. Then use ```
sudo dpkg-reconfigure gdm
``` (or lightdm). Remember this works only if you already have gdm installed. If not, you can simply install gdm by this simple command: ```
sudo apt-get install gdm
```. This way, during installation you can choose from kdm, gdm, and lightdm.
I found this working for me after I tried to understand what gdm is!
Hope it works!

---

