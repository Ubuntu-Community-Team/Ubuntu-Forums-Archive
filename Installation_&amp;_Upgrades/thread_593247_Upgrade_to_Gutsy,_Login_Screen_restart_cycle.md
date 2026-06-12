---
title: "Upgrade to Gutsy, Login Screen restart cycle"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Kschikan on 2007-10-27
Tried upgrading from 7.04 to 7.10. I used the Upgrade-manage (graphical) which I had used to upgrade from 6.04 and 6.10 successfully in the past. As the packages were going to take a while to download, I set it to run, went to sleep/work. When I got home, the screen was blank (as if in screensaver) but I could not get anything to show on the screen from either mouse movement or key presses. So (in a fit of idiocy) I rebooted.

Of course, the upgrade had failed at that point, so I logged in through a tty terminal (a la CTRL-ALT-F2) and was able to login. I ran apt-get update, apt-get clean, apt-get dist-upgrade and was able to install most of the packages. I had problems with the gnome-themes and ubuntu-desktop package, which I was able to resolve by finding some duplicated library files and moving the copies. I was then able to install all the packages (and ran apt-get upgrade to be sure).

Reboot, go through the loading sequence, get to the login screen. It shows the tan background with a spinning mouse cursor, flashes the login text field, and returns to the tan background and spinning cursor. It does this repeatedly. Switching to a tty terminal, I was able to login, but the system couldn't find my HOME directory (!!). 

I tried running dpkg-reconfigure xorg-xserver... no help. I also tried /etc/init.d/gdm restart (as well as /etc/init.d/gdm stop; startx, which failed) . 

Running on a hp pavilion ze5300, with the following:
CPU - 2.8-GHz Pentium 4
System memory - 512MB of DDR266 SDRAM
Graphics - ATI Radeon IGP 345M using main memory 

I can view the drive with the Linux System Rescue CD (which seems to indicate that my /home drive is ok, but isn't being found). I would rather not lose the data I have there (I know... make backups). Google + these forums has gotten me to this point. Anybody out there have any ideas?

Thanks in advance, sorry for the long post.

---

### Post by tcoffeep on 2007-10-31
I had this very problem!

It got me so frustrated I attacked my laptop!!! (I'm an idiot like that :( )
I'm not even kidding. I can't use my beloved Ubuntu because of it, but there's a difference. I was just doing a system update, and upon installation on one point, everything froze. I didn't get to write down which one, and so I basically did what you did, and I had a frustrating battle between myself and the login screen restart cycle...GAH! It was horrid.

Well, I'm anxious to see if anyone has an idea on it.

---

### Post by Sirkent on 2007-11-08
I have this exact same problem too. Have either of you managed to fix it?

There's nothing being logged in /var/log/gdm and nothing in syslog or messages either, so I'm at a loss to figure this out. I have noticed though that when it continuously cycles it eats alot of CPU.

Does anyone have any ideas? Any logs to look at or anything to go on? I'm at a loss...

---

### Post by Sirkent on 2007-11-09
It looks like this may be related to PAM, as I get the following message in /var/log/auth.log:
pam_nologin(gdm:auth): cannot determine username

---

### Post by bluknight on 2007-11-09
Sirkent, tcoffeep, Kschikan,

Keep cool - this problem has happened many times before when (as root) you moved files related to your users profile resulting in a permission denial. When the login screen comes on, hit CTRL-ALT-F2 (or F1, depending on your machine) to get a login prompt window. Login as root and type the following as commandline:

chown -R <name> /home/<name>
chgrp -R <name> /home/<name>
chmod -R 755 /home/<name>
chmod 644 $HOME/.dmrc

...where <name> is your login name. You need to do for as many login names in /home directory.
Get back to a login screen by CTRL-ALT-F7 (or F8?) and you're all set.

HTH :KS

---

### Post by Sirkent on 2007-11-09
Bluknight: The login screen isn't fully appearing for me. The orange screen and the loading mouse icon appears, then nothing happens for a second or two, the screen flickers and it does that again. The login screen never actually appears.

I will have a look at permissions though. Any other ideas?

---

### Post by beansdad on 2007-11-09
I had a problem with the upgrade to my desktop. After posting here I couldn't solve it so have burnt an ISO CD and carried out a complete re-install which seems to be OK so far. You may need to do likewise.

---

### Post by Kschikan on 2007-11-26
I would love to try the possible solution, but as noted in the OP, I can't see my home directory once I login . I think I will try to reinstall the OS and then link the home directory manually, but I'll use a different thread for that.

---

### Post by Sirkent on 2007-11-27
I had to reinstall Ubuntu.

---

