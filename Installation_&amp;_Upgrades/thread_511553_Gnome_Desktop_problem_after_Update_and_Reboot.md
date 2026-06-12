---
title: "Gnome Desktop problem after Update and Reboot"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by lmsurprenant on 2007-07-27
I have installed Ubuntu 7.04 Desktop on my hacked up system that I built and everything was working great until...

Recently I used the Update Manager program (clicked icon in top right of gnome desktop) to update 39 packages and rebooted my system.  Now I turn my computer on and the login screen looks normal but when I sign in the screen gets all sorts of messed up (crazy diagonal lines all over and can't see a thing).  In fact, I have tried to use the "Select Session..." from login and each of Last Session, 1. Run XClient Script, 2. GNOME, 3.Failsafe Gnome have this same result.  

I am able to login to the 4. Failsafe Terminal but do not possess the skillz to fix the system.  Please help!

In my feable attempt to fix it, I opened the synaptic package manager from the failsafe terminal to check the packages that were updated but nothing jumps out as me as being culprit.  Updates include bind9-host, dnsutils, iptables, libbind9, libcurl, libdns, libisc*, ttf-opensymbol, and update-manager-core, as well as some others that I haven't written down.  I can provide complete list if this helps.  I tried to rollback the version on these but it did not help.

Could an update cause me this much pain or is something else afoot?  I would have suspected hardware but the splash and failsafe terminal session appear to work perfectly.  Thanks for any help.

---

### Post by Richard Kut on 2007-07-28
Hello, and welcome! It sounds like a video problem to me. Try opening a terminal in the failsafe session and typing:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

This will create a backup copy of your xorg.conf file just in case the next part makes matters worse, and you want to rollback the changes.

Then, in the same terminal session, type:

sudo dpkg-reconfigure xserver-xorg 

This will call up a text-based configurator where you can provide all of the details which are pertinent to your graphics card.

Please update this post with your results and observations.

Good luck!

---

### Post by lmsurprenant on 2007-07-30
Richard, thanks for the prompt reply.  I finally got around to trying your suggestion which made a lot of sense.  At first it didn't change anything, but then I redid it with some safer options and the system seems to be back to normal.  Thanks so much!

-Lee

---

### Post by Richard Kut on 2007-07-31
Glad to hear that it worked, and glad to be of service. Happy computing!

---

