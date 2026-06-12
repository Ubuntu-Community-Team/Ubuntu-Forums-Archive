---
title: "Please help! After upgrade, nothing works!"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by dado80 on 2008-01-12
I've been using Ubuntu since 5.10, and have just done upgrades up to 7.04. I held off on upgrading to Gutsy, since I had everything working fine.
I decided to upgrade last night, I'm not sure why, started the upgrade and went to bed.
This morning, when I checked my laptop (HP DV1300, 1GB RAM, 80GB HDD) the upgrade was only halfway through, and there was an error message, 
Unable to install dependencies for libcups
I hit OK, the upgrade proceeded. The errors kept popping up, for GNOME, Nautilus, libGTK and a whole bunch others.
After it was done, it gave a message about being unable to lock down. I restarted manually, and still got the Feisty splash screen. After logging in, i just get a blue screen, no icons, the mouse works but nothing else.
I can get into terminal (Ctrl-Alt-F1), but running dpkg --configure -a does nothing.
I tried loading up an older version of the kernel, still nothing.
If i select a different session on the splash screen, like GNOME-failsafe, i finally get into GNOME, but i have no wireless, and the only thing that mounts is /dev/hda.
No CD rom, no usb ports.
It also pops up a message 
Unable to initialize HAL.
I tried to backup some data using a live distro cd, but can't, since I don't have permission to copy the files to my external HDD.
So, any way to fix my system, or at least back up my data so I don't lose it?
Sorry for the wall of text, but I wanted to give as much info as possible.
I'm posting this running a Fedora 8 live CD.

---

### Post by Crenfinkle on 2008-01-12
Had a similar problem on Fedora 8 recently. The best thing to do would be to get a knoppix live CD and use that to back up your data before doing a fresh install. I think it probably failed to install a lot of dependencies, but I'm still learning the ropes (as I think everyone here is)

BTW, Fedora was a sorry POS.

---

### Post by dado80 on 2008-01-12
Okay, got it fixed.
What I did was boot straight into terminal, without any scripts, and then run
sudo dpkg --config -a
It took about 35-40 minutes (!) for it to install all dependencies and what not. Now everything is back in working order, far as I can tell. I'm gonna backup all my data now, and wipe the disk and start fresh.

---

### Post by Crenfinkle on 2008-01-12
if all of the dependencies are in place and everything is good now, a fresh install may not be necessary.

---

### Post by dado80 on 2008-01-12
Well, it's not _necessary_, but I wanna do it anyways! :)
It just seems like my machine has become very bloated, what with all the useless junk I've accumulated over time.
Plus, it'll be an adventure to see if I can get all the little kinks worked out again.

---

