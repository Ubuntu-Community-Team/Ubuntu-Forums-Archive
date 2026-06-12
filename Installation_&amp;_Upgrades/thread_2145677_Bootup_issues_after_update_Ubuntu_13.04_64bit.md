---
title: "Bootup issues after update Ubuntu 13.04 64bit"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by Romeo9 on 2013-05-16
I turned my computer on this morning and was prompted to do a Ubuntu Base update. I did the update as instructed and was prompted to restart.

As the computer was restarting I noticed that my boot splash screen had dissapeared and was replaced with commands running from the top of the screen. It eventually then gets stuck on this line: IPv6:ADDCONF... ...eth0:link becomes ready It stays on this line for about 5 minutes after which it goes to a blank Maroon cloured screen and doesn't move from there.

If I press ctrl alt delete on this line:IPv6:ADDCONF... ...eth0:link becomes ready it goes into the OS but gives me a screen which says your computer is running in low graphics mode, and gives me a few options, none of which work.

Here's the really strange thing this only happens every second boot-up, every other boot-up in runs through the boot and even gives me the splash screen but in a dos like look and boots into Ubuntu just fine.

I'm really having a hard time trying to figure out what is wrong with my OS. I really hope someone can help me solve this issue. Here is the log entry of my update I did today:
Start-Date: 2013-05-16  09:31:34
Commandline: aptdaemon role='role-commit-packages' sender=':1.55'
Install: linux-headers-3.8.0-21:amd64 (3.8.0-21.32), linux-image-3.8.0-21-generic:amd64 (3.8.0-21.32), linux-headers-3.8.0-21-generic:amd64 (3.8.0-21.32), linux-image-extra-3.8.0-21-generic:amd64 (3.8.0-21.32)
Upgrade: linux-headers-generic:amd64 (3.8.0.19.35, 3.8.0.21.37), linux-image-generic:amd64 (3.8.0.19.35, 3.8.0.21.37), linux-libc-dev:amd64 (3.8.0-19.30, 3.8.0-21.32)
End-Date: 2013-05-16  09:33:17

---

### Post by uligraf on 2013-05-18
Same with me: Fresh install of 13.04 amd64, low graphic resolution with open sorce drivers, fine after installing Nvidia-310, installing full gnome desktop, still OK, update to linux-image-3.8.0-21-generic gives the same as above. Booting linux-image-3.8.0-19 is OK. How can I solve the problem, except of booting into linux-image-3.8.0-19?

---

