---
title: "Installation problem"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by colinchiang on 2008-04-12
I have downloaded Ubuntu 7.10 and installed on an old PC.

The configuration of the PC is AMD 1800+ processor with 1GB DDR266 RAM, 80GB hard disk.

I booted from the CD and the first stage installation had been successfully completed. I removed the CD and let the machine reboot.

The machine started and running the initialization of Ubuntu. Then it stopped at the line

* Running local boot scripts  (/etc/rc.local)                           [OK]

and the cursor stopped right below this line.

I waited more than 30 minutes and nothing further happened.

I tried to reboot the machine (both Ctl-Alt-Delete) and hard switch off.

I also tried to re-install from CD again.

I have performed the above procedures 5 times and still can't get ubuntu running.

Therefore, I would be appreciated if anyone would help to identify and fix what goes wrong with my installation.

Thanks

Colin

---

### Post by Partyboi2 on 2008-04-12
When it gets to > Running local boot scripts  (/etc/rc.local)                           [OK] press Ctrl+Alt+F2 to get to a terminal and then type
```
sudo dpkg-reconfigure xserver-xorg
```and choose the correct videocard for your system. If unsure choose vesa and finish answering all the questions. then type
```
startx
``` back in the terminal

---

### Post by colinchiang on 2008-04-12
Thank you very much. However, it requires to login as root.

During the installation process, it only asked me for creating a user account and entered the password for the newly created user. It did not ask me for a password setup for the user root.

Is there any default password for the user root?

Thanks.

Colin

---

### Post by Partyboi2 on 2008-04-12
The root password is the same password you use to login with. (The one created at installation) [Here]("https://help.ubuntu.com/community/RootSudo") is more on sudo if you are interested.

---

