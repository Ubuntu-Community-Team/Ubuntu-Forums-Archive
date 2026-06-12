---
title: "Can't log-in after clean install (twice)"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by TunaCanTommy on 2011-10-13
I just did another clean-install of 11.10 (AMD64) - my second on this machine today. I have an AMD64 desktop, with an Nvidia graphics card (GeForce6200). It was all working very well on Natty.

After both, apparently successful installations, I was not able to log in to a USER session. The Greeter came up, and I was presented with my login but when I typed in my password the screen momentarily went blank and the greeter screen poped back up. I tried both Ubuntu and Ubuntu2D - several times.

I was however able to log into a guest session with Unity running in 2D.

I was also able to log into a TTY session (CNTL+ALT+F1) using my USER name and password. So I don't think I was mis-typing my password.

Just to check, I did a UNIX password change (passwd) and selected the same password.  Tried it again at the greeter and still wasn't able to log in as myself - although the GUEST session was still working OK.

When I did my clean install I put the new installation on a formatted boot partition and a formatted root partition.  I kept my /home directory as it was (didn't format it), and did an update/upgrade.

I'm guessing there is some artifact in my /home partition that is causing my log-in not to work, because a GUEST log-in is working.

Is there perhaps a 'profile' file I need to modify or delete to get this new install to let me log into my USER session and get a Unity Desktop ? ?

Just installed the Gnome3 Desktop, with Gnome-Fallback. I now have all three Gnome choices in addition to the two Unity choices.  But I have the same issue when I enter my pass-word. The screen goes blank for a second or two and the Greeter screen comes back up. Just can't get to my USER session.  Maybe I need to reinstall Natty ? ?

---

### Post by TunaCanTommy on 2011-10-14
Bump . . . . !

Fixed here:  [http://ubuntuforums.org/showthread.php?t=1859571&page=2](http://ubuntuforums.org/showthread.php?t=1859571&page=2)

Needed to delete the .Xauthority file and reboot twice.

---

