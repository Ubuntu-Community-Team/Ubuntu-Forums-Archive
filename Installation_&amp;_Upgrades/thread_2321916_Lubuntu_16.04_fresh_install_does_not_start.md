---
title: "Lubuntu 16.04 fresh install does not start"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by 8mabmzqcnyc18-contact on 2016-04-25
Hi there!

So I just installed Lubuntu 16.04 on my old computer.
Before that, it was running version 15.10 (iirc) correctly.

First thing, I wasn't able to download updates during install. The checkbox was greyed out and I had no option to chose a network.

But that's not my issue: when I boot the computer up, the only thing it displays is:
```
/dev/sda1: clean, 121563/920272 files, 701079/3680256 blocks
```

Any idea?
Thanks by advance! :-)

---

### Post by grahammechanical on 2016-04-25
The message you are seeing is a normal Linux message. It means that the  file system has been checked for hard disk damage. We all see that.

> First thing, I wasn't able to download updates during install. The  checkbox was greyed out and I had no option to chose a network.

WiFi adapter switched off in hardware? 

Did you tick the box "Install third party software?" That would bring in a proprietary video driver from the internet but with no internet connection that might have caused a problem. I do not know.

At the Grub boot menu we can select Advance options for Ubuntu and from the sub-menu select a recovery mode kernel. Then at the recovery menu we can select Resume. That may load to a log in screen and a working desktop where you can change video drivers.

Regards.

---

### Post by 8mabmzqcnyc18-contact on 2016-04-25
The WiFi adapter is started, I even have the popup saying networks were detected, but no way to connect to one.
I tied reinstalling without the third party components, same problem.

I'll try the recovery mode later.

---

### Post by mörgæs on 2016-04-25
Have you tried installing using a wired internet connection?

---

### Post by vasa1 on 2016-04-25
> **grahammechanical said:**
> The message you are seeing is a normal Linux message. It means that the  file system has been checked for hard disk damage. We all see that.
...
I see that as well in 16.04 but don't recall seeing it in 14.04.

---

### Post by Tucker_Cahooter on 2016-04-27
I don't have an answer for you, but just confirming that I also am experiencing this problem. Downloaded the Lubuntu 16.04 32-bit ISO, cut it to a USB, booted then installed it on a Dell Inspiron 910 without any problems. Didn't choose to download updates during installation. Rebooted and saw the same message, system hung at that point. Tried installing it both with and without installing the third party apps, this didn't have any effect.

[EDIT: I dug out a 14.04.2 32-bit ISO and successfully installed it on the same PC, so it is definitely a regression bug, not some issue with incompatible hardware]

---

### Post by Stump86 on 2016-04-27
I have the same issue on a fresh install. 
Check out this thread: [http://ubuntuforums.org/showthread.php?t=2322111](http://ubuntuforums.org/showthread.php?t=2322111) which seems to offer a workaround for now.

---

