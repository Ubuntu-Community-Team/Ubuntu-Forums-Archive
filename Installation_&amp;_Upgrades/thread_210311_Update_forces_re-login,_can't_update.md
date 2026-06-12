---
title: "Update forces re-login, can't update"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Preserved Killick on 2006-07-06
Hi.

My system was up to date last night, but today the update icon was back, so I tried to run it.  I was prompted for my password and the list of available updates appeared (briefly) and then it seems like X crashed and I was at the main Ubuntu login screen.  I tried this three times, every time with the same result.  I think one of the updates was about login, coincidentally.

Anyone know if there's a bug in the updater?:( 

-- PK

---

### Post by golfbuf on 2006-07-06
I had no problem with the latest update to "login".

Maybe you can reboot into recovery mode and at the root prompt enter:

/usr/bin/apt-get dist-upgrade

After upgrade occurs, reboot.

HTH,

---

### Post by ajgreeny on 2006-07-06
If the three updates were the same as mine it was ppp, login and passwd, all of which went as usual, without problem.  It sounds as though your machine might have crashed just at the wrong moment.
My suggestion is to boot into recovery mode, then at the terminal type:-
apt-get reinstall -f ppp login passwd
Hit return and see if you can reinstall all three that way.  If that doesn't crash you out again, try logging in normally and see if you're now OK.  If that does not work, however, I'm afraid it needs somebody else's suggestions to put you right.

---

### Post by BioTeX on 2006-07-06
I had the same problem on both my laptop and my desktop.  When opening the update manager to get the login, passwd and ppp updates, the gnome session was terminated in an ugly mess of pixellation and I ended up back at the login screen.

You don't have to go to recovery mode to fix it though.  Just log back in, open a terminal and type ```
sudo apt-get upgrade
``` instead of going to the graphical update manager.

---

### Post by VirtuAlex on 2006-07-06
See [http://ubuntuforums.org/showthread.php?t=210030]("http://ubuntuforums.org/showthread.php?t=210030")

---

### Post by Preserved Killick on 2006-07-06
OK, it seems there is a bug, but it may be a bug in nvidia drivers.  I have an nvidia driver.  If you don't use the x-window system to do your update, then you're OK.

sudo apt-get update

then 

sudo apt-get upgrade

done.

Thanks for all your replies and helpful links.

-- PK

---

