---
title: "Installing new graphics card...  what order to do things?"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by cryptotheslow on 2010-02-12
Hi,

Relative newcomer to Linux, so apologies if this is a dumb question.

I'm currently running karmic fine with an onboard ATI Radeon X1250 graphics chip.

That's not up to the job for a game I like (Urban Terror), so I have the loan of an XFX NVIDIA 7900GS - which I know is a few years old but should be up to the job.

Question is, how to go about installing it with out killing X irrevocably.

1. If I make a backup of the current xorg.conf and all goes completely wrong, will it just be a case of restoring the backup conf file and re-enabling the onboard graphics?

2. Should I use envy to install the nvidia drivers or is there a better way?

3. What order to do things in? Is it..

**A**
a1 Backup xorg.conf
a2 Install envy
a3 Install correct driver
a4 Power down and install card
a5 Power up

or

**B**
a1 Backup xorg.conf
a2 Install envy
a3 Power down and install card
a4 Install correct driver with envy
a5 Power down
a5 Power up

... or some other order  :confused:

And yes I know I could just restart gdm / X in some places instead of rebooting, but for some reason rebooting gives me comfort...  hopefully more time away from microshaft will rid me of that habit :D

All help welcome :)

Thanks

---

### Post by ajgreeny on 2010-02-12
Just rename your old xorg.conf as backup, then shutdown, change the graphics card and boot up again.  With no xorg.conf present, the system should detect the new card and give you the open source driver for it,just to get a gui, but then it will allow you to use the System ->Administration ->Hardware Drivers utility to install the new nvidia driver very easily.

---

### Post by cryptotheslow on 2010-02-12
Thanks ajgreeny

As long as I know that when all goes wrong I can just put the previous xorg.conf file back from a terminal login and be back where I started I'm happy.

I think I'm having a disbelief crisis that things can be that easy to recover.... I've been away from a proper OS for too long :)

---

### Post by cryptotheslow on 2010-02-13
OK... I've fallen at the first hurdle :D

I don't seem to have an xorg.conf file to backup  :confused:

Not in /etc/X11

```
graham@gt-desktop:/etc/X11$ ls -la
total 84
drwxr-xr-x   9 root root  4096 2010-01-13 02:16 .
drwxr-xr-x 134 root root 12288 2010-02-13 12:36 ..
drwxr-xr-x   2 root root  4096 2009-10-28 21:04 app-defaults
drwxr-xr-x   2 root root  4096 2009-10-28 21:04 cursors
-rw-r--r--   1 root root    14 2009-10-28 21:05 default-display-manager
drwxr-xr-x   6 root root  4096 2009-10-28 21:00 fonts
-rw-r--r--   1 root root 17394 2009-06-22 23:57 rgb.txt
lrwxrwxrwx   1 root root    13 2010-01-13 01:33 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2009-10-28 21:04 xinit
drwxr-xr-x   2 root root  4096 2009-10-28 20:55 xkb
drwxr-xr-x   2 root root  4096 2010-01-13 02:16 Xresources
-rwxr-xr-x   1 root root  3730 2008-06-25 03:05 Xsession
drwxr-xr-x   2 root root  4096 2010-02-08 19:00 Xsession.d
-rw-r--r--   1 root root   265 2008-06-25 03:05 Xsession.options
-rw-r--r--   1 root root    13 2009-08-25 01:37 XvMCConfig
-rw-------   1 root root   601 2009-10-28 20:56 Xwrapper.config
graham@gt-desktop:/etc/X11$ 

```Only reference I can find to it is the man file:

```
graham@gt-desktop:/$ locate xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
graham@gt-desktop:/$ 
```
I may have a hangover... but I don't think I'm blind....  where is it??

---

### Post by falconindy on 2010-02-13
If it's not there, it's not there. Add the new card.

---

### Post by ajgreeny on 2010-02-13
> **falconindy said:**
> If it's not there, it's not there. Add the new card.
+1
xorg.conf will only be present in karmic if you make one manually, or add a proprietary driver, most, if not all of which will produce the file for you.

---

### Post by cryptotheslow on 2010-02-13
Card in and working perfectly - although I had to manually edit the vertical refresh rates for the monitor in xorg.conf after the driver install in order to get the correct resolution choices showing up.

Thanks everyone :D

---

