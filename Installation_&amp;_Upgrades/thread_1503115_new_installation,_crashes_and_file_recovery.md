---
title: "new installation, crashes and file recovery?"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by jwin on 2010-06-06
I have an old computer that has been running Windows XP (Pentium 4, 256Mb RAM, 40 Gb hard drive). I have never used ubuntu in any form but thought it might get better performance since the system was so slow as to be basically unusable.

Downloaded lubuntu, installed on a USB drive. Started up from the USB, no problems. I clicked Chromium for web browsing to see how it works. Gmail works, then as soon as I typed facebook.com, it crashed with the message "208 getpwuid_r failed due to unknown user id." Turned off computer, restarted from USB again. Tried facebook again, same thing happened. Restarted again, browsed some other sites and after a few minutes got the same crash. Restarted again, this time followed instructions to install lubuntu on my hard drive. It succeeded, but I still get the 208 error message seemingly at random while internet browsing. This is one problem.

Second problem: I thought I was setting up a dual boot option for XP/lubuntu, but in my repeated installation attempts I must have done something wrong, because I don't have a boot option anymore, just straight to lubuntu. That's ok, like I said XP was basically unusable anymore. But in the installation I seem to have wiped the hard drive, so it shows 36/40 Gb free space. 

I need to attempt some file recovery, but I am in an unfamiliar operating system, cant even figure out how to install applications. Apparently the lubuntu GUI is just "different" enough that most of the ubuntu instructions are not quite right. Help!
:confused:

---

### Post by Jorge Alban on 2010-06-07
To install software in Lubuntu just go to SOFTWARE MENU > PREFERENCES > SYNAPTIC PACKAGE MANAGER (the very same app used for any and all members of the XXbuntu family).

Lubuntu 10.04 uses Grub2. At first it seems awkward as it cannot (or shouldnt) be edited directly. However there's magic to it !

In order to check if your WinXP filesystem is still there. Open a  Terminal (SOFTWARE MENU > ACCESORIES > LXTERMINAL and code:

```
os-prober
```

If a Windows filesystem is reported then just code:

```
update-grub
```

And voilá your windows partition is back in the boot menu !

There are literally dozens of video screencasts at this page showing how to do everything (from video encoding to email client setup) the Lubuntu way, with low-resource, mean-and-lean apps: 

[http://lubuntu.net/]("http://lubuntu.net/")

How did you install to USB ? Did you use UNetbootin (no persistence) or usb-creator with a persistence partition enabled ?

---

