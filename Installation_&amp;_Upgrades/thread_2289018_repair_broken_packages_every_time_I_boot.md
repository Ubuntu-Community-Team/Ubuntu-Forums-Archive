---
title: "repair broken packages every time I boot ?"
date: 2015-07-31
forum: Installation &amp; Upgrades
---

### Post by philipp21 on 2015-07-31
Ubuntu 14.04 freezes during boot (login screen appears, but keyboard and mouse are dead). It works only after I restart, enter recovery mode, choose "repair broken packages", and reboot. 
This error is fully reproducible. 
I checked memory and hard disk with no errors.

I'm relatively new to Ubuntu, so help is greatly appreciated!

Philipp

---

### Post by Bashing-om on 2015-07-31
philipp21; Hello;

My 1st thought as :
> 
 (login screen appears, but keyboard and mouse are dead).

we have such an advisory, is to check in bios that the USB settings are correct .
Also that 'plug and play' is enabled as 'buntu is a 'plug and play' operating system.

As an aside. can you boot the liveDVD(USB) with no problems ?

[INDENT][INDENT]it all starts in bios
[/INDENT][/INDENT]

---

### Post by philipp21 on 2015-08-01
USB boot option is enabled and working. I didn't find pnp options in BIOS however...

---

### Post by mc4man on 2015-08-01
If you are 'resuming normal boot' from recovery mode then you are booting without video drivers being loaded so those drivers may be your issue instead of broken packages.

---

### Post by philipp21 on 2015-08-02
I double-checked my drivers. It's Nvidia GeForce GTX 945. I used **sudo apt-get install nvidia-current nvidia-settings. **It says drivers are up to date.

---

### Post by Vladlenin5000 on 2015-08-03
> **philipp21 said:**
> I double-checked my drivers. It's Nvidia GeForce GTX 945. I used **sudo apt-get install nvidia-current nvidia-settings. **[COLOR=#ff0000]It says drivers are up to date[/COLOR].

Except they aren't. The *nvidia-current *package is actually nvidia 304, a very old version. You need the 346 or 352, at least.

---

### Post by mc4man on 2015-08-04
nvidia-346 is now available in trusty, added for the upcoming 14.04.3 release. You should use it. 
(either nvidia-346-updates or nvidia-346, basically the same though I'd use the former package. If you need even newer on 14.04  then there are ppa's or nvidia itself.

---

### Post by philipp21 on 2015-08-23
I did update to 346. This is what I used to double-check...

philipp@philipp-XPS-8700:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  346.87  Tue Jul 14 18:29:34 PDT 2015
GCC version:  gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) 

But the problem still persists: I need to run "Repair broken packages" first before I can successfully boot. Otherwise the keyboard is frozen at log-in

---

### Post by tgalati4 on 2015-08-23
Try disconnecting the mouse and keyboard and see if the system boots completely.  I've seen wireless keyboards fail, and it is not pretty.

---

### Post by VMC on 2015-08-23
I'm curious. Is there anything inside folder "/var/crash".

---

### Post by philipp21 on 2015-09-07
Yes! That was it! Disconnecting keyboard and mouse prevents it!!

But can I do something to fix it?

Thanks!!!!!

---

### Post by tgalati4 on 2015-09-07
Open a terminal and take note of the last line of:

```
dmesg
```

Then plug in the mouse only.

```
dmesg
```

Only post the mouse-related stuff.  Troubleshooting in linux requires *decomposition*--breaking a big problem down into little problems and tackling one-at-a-time.  It's boring and tedious, and patience is key. But everything is fixable.

Remove the mouse.  Perhaps try the same thing with the keyboard.  Even post the results.

Find a new keyboard and mouse to test with.  Use a wired keyboard and wired mouse.  Wireless adds another layer of complexity that makes troubleshooting difficult.

---

### Post by philipp21 on 2015-09-07
The last line reads:
[ 2104.754299] type=1400 audit(1441644444.812:85): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3036 comm="apparmor_parser"

And actually I'm using a wired mouse & keyboard.

---

