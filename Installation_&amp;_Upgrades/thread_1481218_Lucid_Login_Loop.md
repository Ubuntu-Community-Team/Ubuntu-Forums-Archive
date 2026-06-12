---
title: "Lucid Login Loop"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Cyclops_ on 2010-05-12
I've been trying to do research on this but coming up with nothing.

Right now I seem to be stuck in a login loop.  I'm running KDE Lucid Lynx.  I try to log in, and it acts like it's going to start, then spits me back to my login screen.  Here are some things that I have tried:

I tried moving the .Xauthority and .ICEauthority files (they don't get recreated when I try to log in again).

I have tried moving the xorg.conf file and recreating using nvidia-xconfig.

There isn't much in the .xsession-errors file, nor do I see anything relevant in the /var/log/messages or the /var/log/Xorg.0.log file.

I tried sudo apt-get remove --purge kdm, and then installing kdm and kubuntu-desktop again.

Also: this didn't happen after any kind of update or anything that I'm aware of... bugfixes or otherwise.  I don't think I installed anything new.  It was working just yesterday, but when I went down for a reboot: BAM!

I'm still having the same issues.

PLEASE HELP!!! I can't do anything until I get this fixed!

---

### Post by Cyclops_ on 2010-05-12
New information:

I was able to create another user account and login using that!

So, there is something wrong with the current user account.

Any help would be great!

---

### Post by Sulomania on 2010-10-20
I have the same problem. I use gnome and upgraded 9.10 to 10.04 and now whenever I try to login, a dark window appears with the cursor blinking few times on top left and then returning to the login window again and again. 

I created a new user account but did not work for me. I have been reading about plymouth but didn't see any solution yet.

---

