---
title: "stuck in tty1 after update to 13.04"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by swimon on 2013-05-07
The update went without any issues.  When the laptop is restarted it tries to boot and goes to tty1.

I tried hitting ctrl+alt+F7, but there's just some random start up messages, not sure which are relevant/important. 

How do I print a start up log or something to pinpoint the error? 

Thanks in advance.

---

### Post by swimon on 2013-05-08
anyone?

---

### Post by steeldriver on 2013-05-08
What graphics card do you have? did you have proprietary drivers installed before the update? Usually these things are graphics driver related

---

### Post by swimon on 2013-05-08
I did try to update the drivers manually a couple weeks before I tried the update, because there were other graphic related errors. I downloaded and ran an update I found on nvidia.com. It fixed the problem I was having back then. 

So this is what probably caused this? Anyway to fix it from TTY1? 

Graphic card: Nvidia Geforce 9100M G

---

### Post by swimon on 2013-05-09
Found solution in different topic:
[http://ubuntuforums.org/showthread.php?t=2077528&p=12323881#post12323881](http://ubuntuforums.org/showthread.php?t=2077528&p=12323881#post12323881)

Reinstall drivers from terminal:
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

---

### Post by swimon on 2013-11-05
I'm back... 

The same problem emerges with this laptop. I get stuck in TTY1 screen. 

I tried the fix I did last time (see post above this one). But it doesn't fix it this time :s After the reboot command, I get another TTY1 screen.

Any ideas why it doesn't work this time?

---

