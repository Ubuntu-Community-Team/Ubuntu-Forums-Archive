---
title: "Not able to install Ubuntu"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Anijith Anirudhan on 2012-02-06
I tried to install Ubuntu on my Dell laptop, having Windows 7 Ultimate Edition..when the installation is about to complete it throwing one error "Permission Denied". I also tried to install Run as Administrator,but getting the same errror. Please help me to resolve this issue..

---

### Post by jayshomebrew on 2012-02-07
My suggestion is to use the 'live-cd' to install..
download and burn iso file to a dvd.
1. download 10.04 LTS here: (or any other version of your choice)
[http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts)

If you don't have a burning windows app, use infrarecorder here:
[http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable)

If you don't know how to burn an iso, follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

2. burn the iso file to a cdr or dvdr

3. reboot your computer hitting <f12> while booting, so that you get the dell boot menu:
[IMG]http://t0.gstatic.com/images?q=tbn:ANd9GcQLC3DyY9G-ZHzicupS12N0X1gk5OQHpJPA8Vs6HEoU68lziN7EqgncWmbmcg[/IMG]
select cd/dvd and boot.

4. the cd or dvd should boot, select try ubuntu:
[IMG]http://tomoyo.sourceforge.jp/1.8/media.ubuntu10.04/startup-en.png[/IMG]

5. install using the desktop icon.
[IMG]http://www.cernea.net/wp-content/uploads/2010/04/4187174337_fa65b6f9ba.jpg[/IMG]

---

### Post by Mark Phelps on 2012-02-07
It looks like, from your comments, that you are trying to install Ubuntu from INSIDE Windows (using Wubi). If you were booting from CD or USB, you would not be getting permission errors.

To install from Wubi, you need the following:
1) The Wubi ISO file stored in the same directory as the wubi.exe program
2) Right-click on wubi.exe and select Run as administrator.

That should prevent you from getting permission errors.

---

### Post by Rafterman414 on 2012-02-07
+1 on having the ubuntu iso in the same directory as wubi. This is a common error message that many people are getting. Also some users have been getting the permission denied error even though the install completes.

---

### Post by Mark Phelps on 2012-02-08
> **Rafterman414 said:**
> ... Also some users have been getting the permission denied error even though the install completes.

Very good point!

So (to the OP), if this happens, try starting Ubuntu anyway.  It just might work.

---

### Post by Anijith Anirudhan on 2012-02-09
> **jayshomebrew said:**
> My suggestion is to use the 'live-cd' to install..
download and burn iso file to a dvd.
1. download 10.04 LTS here: (or any other version of your choice)
[http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=lts)

If you don't have a burning windows app, use infrarecorder here:
[http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable)

If you don't know how to burn an iso, follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

2. burn the iso file to a cdr or dvdr

3. reboot your computer hitting <f12> while booting, so that you get the dell boot menu:
[IMG]http://t0.gstatic.com/images?q=tbn:ANd9GcQLC3DyY9G-ZHzicupS12N0X1gk5OQHpJPA8Vs6HEoU68lziN7EqgncWmbmcg[/IMG]
select cd/dvd and boot.

4. the cd or dvd should boot, select try ubuntu:
[IMG]http://tomoyo.sourceforge.jp/1.8/media.ubuntu10.04/startup-en.png[/IMG]

5. install using the desktop icon.
[IMG]http://www.cernea.net/wp-content/uploads/2010/04/4187174337_fa65b6f9ba.jpg[/IMG]
Thank you for the support... this method worked and able to install Ubuntu..Thank you..

Anijith

---

### Post by Mark Phelps on 2012-02-09
Glad to see you got it working.  Please use the Thread Tools at the top of the thread to mark this thread as SOLVED.  thanks

---

