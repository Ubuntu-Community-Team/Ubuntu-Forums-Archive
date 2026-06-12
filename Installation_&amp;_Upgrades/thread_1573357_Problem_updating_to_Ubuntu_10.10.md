---
title: "Problem updating to Ubuntu 10.10"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by Gahan on 2010-09-12
I was in the middle of updating Ubuntu 10.04 to 10.10 when my system froze completely. All of the new packages had already been downloaded, but only a few had been installed. 

I rebooted and discovered that Ubuntu simply booted into a terminal, no graphical interface at all. (The kernel has already been updated, btw) 

So far I've tried the following:

-checking for broken or missing packages
-reinstalling gnome-desktop-data, ubuntu-desktop and xorg
-checking for dependency problems
-starting gnome manually (gnome-session results in an error, it can't initialize. problem persists after reinstalling)

Finally I attempted to reinstall all the packages by entering: sudo dpkg-reconfigure -phigh -a

dpkg-reconfigure runs for a bit, but pretty quickly I get the following error message and it terminates:

update-intramfs: Generate /boot/initrd.img-2.6.35-20-generic
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package

Does anyone have any idea's what could be causing the GUI failure or the dpkg-reconfigure error? Halp please

---

### Post by Gahan on 2010-09-12
I just realized that the generic kernel is booting and I'm running a 64-bit machine. I'll try (re)installing the correct kernel and see if that works

---

### Post by M0nk3yM4n on 2010-11-14
Hey Gahan, just FYI I'm having the same problem and I don't know how to fix it! Did you end up solving it?

---

### Post by sikander3786 on 2010-11-14
> **M0nk3yM4n said:**
> Hey Gahan, just FYI I'm having the same problem and I don't know how to fix it! Did you end up solving it?
The thread is pretty old.

Where did your upgrade process break and what are you getting now? Can you get to the desktop? If not, can you get to the recovery mode and drop to the root shell and perform some commands?

If you can either get to the desktop or root shell, try these commands and post the output.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by jwdonal on 2011-03-07
> **sikander3786 said:**
> ```
sudo dpkg --configure -a
```
You are the man!!!  This thread may be old but it saved my life! THANKS A TON! :-D

---

