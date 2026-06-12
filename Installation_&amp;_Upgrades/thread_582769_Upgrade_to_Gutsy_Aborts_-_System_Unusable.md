---
title: "Upgrade to Gutsy Aborts - System Unusable"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by maxweld on 2007-10-20
I have (or had) a 7.04 Server 386 system with ubuntu-desktop added, and all working fine. I then ran  the Gutsy upgrade.

After downloading 1119 packages, it commenced the download. It produced numerous package errors on the way, and what seemed about 3/4 of the way through it aborted, asking me to report the bug and provide a few files with the bug report, which I have done.

I rebooted the system and now it is unusable. It seems to boot from the original kernel, and Grub has not been updated. I can log in to GDM but there is no Gnome desktop, just a sky blue screen, no Icons or anything.

I am mainly a Gnome desktop user, but can get around a command line. What is the best way to 
a) recover to a workable system, then
b) complete the upgrade.

Thanks

---

### Post by Arenlor on 2007-10-20
I suggest run the CD if you have it, for Feisty if you need to, then edit /boot/grub/menu.lst on the harddrive from there.

---

### Post by maxweld on 2007-10-20
The install does not yet seem to have added the new kernel version, so I am not too woried about which version it boots yet. I suppose I need to concentrate on completing the install. I can acces sthe system from either an old 7.04 partition or using the command line option available in recovery mode.

How mighjt I continue the install?

---

### Post by Arenlor on 2007-10-20
[code]sudo apt-get install update-manager-core
sudo do-release-upgrade[/core]Also some prayer to your version of the divine (for an atheistic view I guess money or the current American Idol?)

---

### Post by maxweld on 2007-10-20
Thanks
after [code]sudo apt-get install update-manager-core
it suggetsed that I needed to run 

dpkg --configure -a

This runs for a couple of minutes, and then complains of 'too many errors' and aborts.

---

### Post by Arenlor on 2007-10-20
That one I'm not sure about how to fix, usually that fixes other things. I'm thinking that means something went horribly horribly wrong with the upgrade process. Try running it multiple times though to see if that may fix everything.

---

### Post by maxweld on 2007-10-20
Hmm - I have tried repeating it and it gets no further - just keeps aborting at the same point.
the upgrade did seem pretty catastrophic, so I am thinking this is terminal and that i will need to rebuild a new system and transfer from the old what can be salvaged. Its a pain and dissappointing for Gutsy.

I wonder if running server version with a desktop is part of the problem. I might try to build a similar system under a VM and attempt an upgrade to see what happens, once I get this one rebuilt.

Thanks for your help

---

### Post by Arenlor on 2007-10-20
No problem, and the server version on a desktop shouldn't make a difference. I don't know what went kablooie on you though.

---

