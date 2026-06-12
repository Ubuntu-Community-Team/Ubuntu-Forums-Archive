---
title: "splash &amp; login screen not visible"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by corto72 on 2006-09-18
Hi, 

I let the installer upgrade my machine today, and it worked fine for about an hour. Suddenly the screen faded away. I rebooted it thinkning the screen was gone, but this is not the case - I can see the bios booting screen as well as the ubuntu startup procedure, but as soon as gnome start the screen is dark. I know I can still login, as I can hear the welcome sound, but that's all...

anybody got an idea??

Thanks in advance for the help

Cheers
Corto

---

### Post by corto72 on 2006-09-18
I should have mentioned that I rebooted after the install - and then it worked fine for 1h...

---

### Post by jonjpeterson on 2006-09-18
I've been having the same problem since update manager yesterday. I just shut down and restart and usually on the third try I can see the screen again and it works fine for a while. It must have been something in the update. If anyone finds a solution please share. I'm going to look at any changes in the standby settings that may have occured.

---

### Post by jonjpeterson on 2006-09-18
I just ran another update using the update manager about two hours ago and haven't had a problem since.

---

### Post by artinla on 2006-09-18
Odd.. do you get the crosshatch screen and X mouse cursor before it goes blank?

I would try a sudo dpkg --reconfigure xserver-xorg

make a backup of /etc/X11/xorg.conf first, just in case!

---

### Post by jonjpeterson on 2006-09-19
Well I guess no one has an answer, but I just did a restore of the vir and it seems to have fixed the situation and I won't do a update anytime real soon. I'll give it about a week.

---

### Post by corto72 on 2006-09-19
I tried rebooting several time, but I can't get through to the login screen...So I cnn't even update it further :mad:

Artinla, I don't even see the crosshatch screen and X mouse cursor, all I see is the cursor just before gnome start and then a black screen... It is very strange, last night I let my pc switched on after a reboot, and I heard my screen going in power saving mode (it's a CRT...) so it must be receiving a signal somehow...

---

### Post by corto72 on 2006-09-19
Hi there just to let you know I manage to fix the problem thanks to Artinla - see following thread [http://ubuntuforums.org/showthread.php?p=1518661#post1518661]("http://ubuntuforums.org/showthread.php?p=1518661#post1518661")

Thanks again Artinla.

---

