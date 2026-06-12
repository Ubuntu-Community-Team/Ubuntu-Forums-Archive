---
title: "Problem with Latest Updates"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by Nero60 on 2008-06-17
Installed latest updates today (24 total) and now Ubuntu will not boot in latest configuration.  Had to start with older version.  Any ideas??

---

### Post by Sef on 2008-06-17
What version of Ubuntu are you using?

By older version, do you mean an older kernel?

---

### Post by Nero60 on 2008-06-17
Ustilizing Ubuntu 8.04 Hardy Heron - latest version.

---

### Post by shareme on 2008-06-17
He means that he used esc at begin of boot and choose 2.6.24.18 instead of the new 2.6.24.19 kernel..

---

### Post by Yuzem on 2008-06-17
I am also having some problems with the latest updates:
-tomboy applet doesn't start and gives an error
-my bash history is gone.
-thunar configuration is gone.
-System > Preferences > Sessions - does not start.
I think that there are others problems that I have not yet discovered.

---

### Post by shareme on 2008-06-17
Lets make sure it booted into 2.6.24.19 with no major  problems?

Ie you had no grub/menu.lst or x server not starting problems?


> **Yuzem said:**
> I am also having some problems with the latest updates:
-tomboy applet doesn't start and gives an error
-my bash history is gone.
-thunar configuration is gone.
-System > Preferences > Sessions - does not start.
I think that there are others problems that I have not yet discovered.

---

### Post by Yuzem on 2008-06-17
I can boot with latest kernel (2.6.24-19-generic)
The x server starts with no problems.
I had discovered that youtube videos doesn't play, they load and a frame is shown but it hangs there. It was working perfectly before the update.

Also the last week, I am not sure if it was because another update but I change my resolution and I couldn't get it back to 1280x1024 (native resolution)
It is because of the drivers (flgrx). With other drivers it is ok.
Now I am using ati drivers and no compiz :(
I thought that the latest update was going to fix the problem, instead it cause some more...

---

### Post by StevenBirnam on 2008-06-17
I updated from Gutsy to 8.04 - downloaded overnite and did update on both laptop and desktop.
Had niggly issues, but in all it went well.
When I rebooted, both systems displayed multiple versions and subversions of Ubuntu in boot option (along with XP in the second partition). With advice to select remove in Synaptic, I tried to remove the unwanted subversions (not successful the first time, so went back and did Remove Completely, and solved that problem.
Tried update for repositories when I got popup notice that there were new versions of several packages.
My mistake was to use Smart Update - which clobbered my XServer components.
Now I boot to character mode - cannot start XServer because X des not exist.
Error messages: xserver-xorg is broken or not fully installed
etc/x11/x is not executable
init: no such file or directory (errno 2): unable to connect to xserver
init: no such process (errno 3): server error
I don't want to wipe out this install and reinstall from scratch (I am so used to doing this in Windows), but doing apt-get install xserver-xorg doesn't work
apt-get install xserver-xorg-core reponds with error because dependent modules cannot be installed.

Anybody have an idea of how I can restore the X gui and components so I can get back to running GNOME?

StevenB

---

### Post by Yuzem on 2008-06-17
Maybe if you try with aptitude instead of apt-get?
Or try:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall xserver-xorg

Or:
sudo apt-get remove --purge xserver-xorg
And:
sudo apt-get install xserver-xorg

---

### Post by Nero60 on 2008-06-18
Thanks to all for your help.  The problem was the start sequence was not booting the latest kernel (2.6.24.19).  Learned a lot from this experience.  Again, THANKS!

---

### Post by Yuzem on 2008-06-19
My problem was that the update didn't left any space on my disk.
Everything is fine now with the exception of the flgrx driver resolution problem.

---

