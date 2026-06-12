---
title: "After upgrade to 18.04 System freeze after login. Gnome Video  issues"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-10-21
I upgraded one of my machines form 16.04 LTS to 18.04.1 viat the automated upgrade.

The system boots fine.
I get the greeter screen and can login

One user (me) freezes the entire machine as soon as I click anything.
I have only a bar at the top with Applications on the left and the time, network icon speaker icon and shutdown icon on the right.

Another users (my wife) works for a while but will freeze the same way. That seems related to Firefox.
This one shows the same as the first one but with a line of application icons on the right below the Applications

A third user (the one I'm using now seems to work long enough to do this. It eventually froze. 
It has a different appearance  with a top bar with Applications Places and The current Application on the left and the day and time  network icon speaker icon and shutdown icon on the right.
There is a bar across the bottom with the open applications shown.

I think it's related to the video driver or the x gnome configuration.  The prosessor is an AMD Phenom II x2 560 video is NViDIA GeForce 7025 Nforce 630a.

I have been able to determine which video driver is loading.

Kernel driver in use: nouveau
Kernel modules: nvidiafb, nouveau

I have used Nvidia Current in the past but this chip may not be supported by the latest version. I have stayed away for noveau because I've had issues with it freezing.

I've now been using one user configuration for a while and it seemd to be working but eventually froze.  Simple resetting the other users to match that one may solve the problems. The freezing seems to be affected by the desttop option I select.How can I reset a users graphics configuration to the system default?

---

### Post by dino99 on 2018-10-21
As you have made a dist-upgrade, think to clean the system to get rid of deprecated packages and settings.Use autoremove, gtkorphan & bleachbit (as root, carefully select features), then reboot and glance at 'journalctl -b'

---

### Post by rsteinmetz70112 on 2018-10-23
Thanks. I did autoremove. autoclean. I haven't tried the other two. I'll be traveling for a couple of weeks before I can get back to it.

I really think there is a problem with noveau since I've always had similar problems when using it.

---

