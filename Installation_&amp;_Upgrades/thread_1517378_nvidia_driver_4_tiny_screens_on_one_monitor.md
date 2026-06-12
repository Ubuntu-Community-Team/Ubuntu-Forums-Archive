---
title: "nvidia driver 4 tiny screens on one monitor?"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by moparisthebest on 2010-06-25
This happened after ubuntu pushed an nvidia graphics update about a week ago, on upgrade I booted up into this:

[[IMG]http://img691.imageshack.us/img691/1250/20100624163005.th.jpg[/IMG]](http://img691.imageshack.us/i/20100624163005.jpg/)

Obviously I had to take this picture with a camera, since a screenshot only showed one screen.  It's perfectly usable like this, except that it's too small to read.

I of course have tried 'sudo nvidia-xconfig', and a minimal xorg.conf:
```

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
EndSection


```
Along with purging and reinstalling all of the nvidia packages numerous times.  I'm currently running on the VESA driver, which sucks.  My chipset is a 9200M, but like I said, it worked perfectly before the last upgrade.

In all my years of using linux and kubuntu, I've seen and fixed numerous nvidia driver errors, but I've never seen one this strange, usually it will run or not run.

---

### Post by VH-BIL on 2010-06-25
have you tried the nVidia driver from "http://www.nvnews.net/vbulletin/showthread.php?t=122606". I just installed the new "NVIDIA-Linux-x86-256.35" and it is running nicely!

---

### Post by moparisthebest on 2010-06-25
No, I haven't tried any official nvidia packages yet, I thought they wouldn't work with 10.04 due to the new way drivers are handled.

edit:
Here: [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)
Is that still the case?

---

### Post by VH-BIL on 2010-06-25
This is how I got it working...

For The Driver:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Fix the plymouth boot screen for the new nVidia driver:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Hope this helps you out!

---

### Post by moparisthebest on 2010-06-25
Thanks for the help, I got it working.  I guess the current nvidia driver in the ubuntu repos is just messed up at the moment.

---

### Post by VH-BIL on 2010-06-25
Did you get the new nVidia driver working? or through the repos?

---

