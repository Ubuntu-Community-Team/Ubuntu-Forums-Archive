---
title: "user login fails.  Guest succeeds"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by kolibri on 2013-02-04
I am having a similar problem to many of the threads here, but none of the posted solutions seems to work.

I was running gnome classic desktop instead of Unity in 12.04 (don't like unity).  Through the update manager popup, I told it to update, and I got a partial update/upgrade warning.  

After that, I could not login as the sole user account, only as guest. 

(This had happened before, and I only fixed it by a completely new installation.  I cannot afford the time for a complete new installation, I have too many custom programs, including Windows and some specialized programs running in Virtualbox.)

By logging into the terminal and disabling all extra repositories, I managed to do an apparently complete update to 12.10, but I still cannot login as user to a graphic shell, only to terminal.

Ownership of everything in my home folder seems correct.  I tried removing the .Xauthority and .conf files as some threads suggested, it didn't work.  I doubt it's a problem with Nvidia, because the guest login is fine.

Any suggestions?  I'd like to copy out any log files, but not sure how to do that in terminal and make them accessible to me elsewhere.

Failing a complete fix, can I set my computer up to launch directly into my user account without a password login?

---

### Post by kolibri on 2013-02-04
I get a few lines of text on a black screen during the login loop. I tried to look at the lightdm logs but they were empty.  His do I find those error messages?  They go too quick.i

---

### Post by kolibri on 2013-02-04
I installed and switch the display manager to GDM instead of lightdm. I can log in under my primary user but I get two errors.
1.   NAUTILUS cannot create home/ users/.config/nautilus.
2. No space on home.  My home partition is large.  Should be plenty of space.

Solved 1) by copying .config-backup to .config and then chown -R user:user .config



But now, logging into gnome classic, I have a cascade of problems.  Programs keep crashing instead of opening (Thunderbird mail, Software center, Gimp), and the error reports keep saying no space on disk. I should have 20 Gb left on /home according to the partition editor, but system monitor shows 20 GB free, 0GB available.

---

