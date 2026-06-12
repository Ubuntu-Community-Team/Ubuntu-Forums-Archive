---
title: "upgrade interrupted at package download stage"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by sulemankm on 2008-05-07
Hi, I was upgrading from 7.10 to 8.04.  The upgrade process was at the 'Downloading Packages' stage.  Unknowingliy, my kid restarted the computer (soft reboot) and interrupted the upgrade.

Now I get the partial upgrade option by the upgrade manager.  What should I do to continue the previous upgrade process?

---

### Post by Pumalite on 2008-05-07
Finish the partial upgrade, then intent the upgrade at that point. If still having trouble; come back.

---

### Post by sulemankm on 2008-05-09
Ok, the upgrade has finally concluded.  Here is what I had to do.

 * When I got the Partial upgrade option, I ran the following commands
  - dpkg --configure -a     (didn't do anything)
  - sudo apt-get install -f  (didn't do anything)
  - sudo apt-get update  (didn't do anything)
  - sudo apt-get upgrade (installed many packages and required reboot)

 * After reboot I found that I'm still running gutsy kernel and the  partial upgrade option is still there.  I opted the partial upgrade but is showed me the message that this application doesn't support upgrade from Hardy to Gutsy.
 * So I issued the following command in a terminal
  - sudo apt-get dist-upgrade   (this installed the new kernel and many other packages)
 * After reboot, I found that it did not find my /home partition. So I edited the /etc/fstab file and changed all the /dev/hd* entries to /dev/sd* and rebooted.   The upgrade tool should have done this automatically.  Its bad that it didn't.
 * After reboot, the X server didn't start correctly and I was dropped to a maintenance shell.
 * I edited the /etc/X11/xorg.conf and set the Fail safe Driver to 'vesa'.  After giving a 'sudo gdm restart' command, the X server was running.
 * I also got a lot of application crash reports pertaining to firefor 2.0.0.14, network manager and other Gnome applications.  Removing the remaining Gutsy apps fixed this problem.
 * I ran 'sudo apt-get autoremove' to remove any orphaned packages.

Now, my system is happily running 8.04.  My display driver NVIDIA XGL, webcam, audio and everything seems to be working.  Some of the services at startup have failed however. I'll look into this soon.

---

### Post by Pumalite on 2008-05-09
Congrats!

---

### Post by sulemankm on 2008-05-09
Thanks for the help.

BTW, is there a way I can completely clean my system of any gutsy libs or packages still lurking around on the disk?  This may happen as during the upgrade process, the upgrade manager disables third party repos.  So apps installed from those repos will not be upgraded and may fail in the new version of the system.

---

