---
title: "upgrading from ubuntu 7.10 to 8.04: xorg problem"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by tp21 on 2008-07-03
hi
i am using thinkpad T40. yesterday i upgraded from ubuntu 7.10 to 8.04. while installing i became 3 warnings, they say respectivly that xserver-xorg, xorg and ubuntu-desktop could not be installed. but the installation process went till the end. after completing the installation phase i received a message saying that the upgrade could not be completed, and that my system is now unstable. the message also says that i have to send this bug, mentioning that i should send /var/log/dist-upgrade with the report, and that installArchive() failed!!

i rebooted. the system either just stuck in the splash screen, or after a long time showed a black screen with lines of information ending with ok. and at the end the cursor!!

after couple of tries, i found out that reverting the kernel and using kernel 2.6.15 generic instead of 2.6.19 let me access the gui. after logging in in gnome, i found out that the system is upgraded as far as i can see. ubuntu info says that this is ubuntu 8.04. and all programs are working fine as far as i can see, except some font issue.

i assume that ati driver is making the trouble. but i don't know how to proceed? 
thankful for every feedback

---

### Post by dstew on 2008-07-03
You can try to re-set your xorg.conf by booting the 2.6.24-19 kernel in recovery mode (if you can), and choosing **xfix** from the Recovery Menu. Then, in the GUI, hit alt-F2 to get a command line, and enter```
gksudo displayconfig-gtk
```See if you can find your monitor there. If you do, that will get you the best display possible using the native driver. After that, you can try to install a restricted driver if you want (System --> Administration --> Hardware drivers).

Of course, if this doesn't work, there might be a bug in the 2.6.24-19 kernel relative to your hardware.

---

### Post by tp21 on 2008-07-03
thanks for the answer
i booted from the covery modus, and i choosed xfix. it took a while and then i recieved a message, what i could read was that it was a warning from xserver-xorg and it is about writing a backup file.
then i went out of recovery mode menue, and the system booted, amazingly, in a good resolution modus.
so i did not type gksudo displayconfig -gtk
i rebooted using the normal kernel. it took a long time, but it rebooted in the good normal resolution modus. great!!!
BUT no sound!!
clicking on the sound i receive that no suitable GStreamer plug in was found.
how come?
thanks again

---

