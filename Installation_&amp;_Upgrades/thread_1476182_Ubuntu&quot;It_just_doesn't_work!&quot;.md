---
title: "Ubuntu:&quot;It just doesn't work!&quot;"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by nikefalcon on 2010-05-07
Hallo 
I have been trying to do a clean install of Lucid ever since it was released.I tried the _Live_ cds(both i386 and amd64) on my  PC. When i boot from disk' plymouth(??) shows the purple screen with the blinking dots, and then my screen powers off and doesn't respond. Same result when i try to run ubuntu without installing. I succeeded in installing  from the alternate cd(i386); but when i boot into Lucid the same thing happens all over again!(and i don't even get an error message) 
I can't even file a bug report.:mad:

[Here]("http://www.facebook.com/l.php?u=http%253A%252F%252Fwww.gigabyte.com.tw%252FProducts%252FMotherboard%252FProducts_Spec.aspx%253FProductID%253D3024&h=4ffc1&ref=nf") are my mobo's specs- just in case its a problem with the video card(embedded graphics).But i don't get any sound either.

Please help me out!

---

### Post by davidmohammed on 2010-05-07
should just use the 386 install

when trying the livecd, press F6 and add "xforcevesa" in the command line - does it boot into the desktop?

---

### Post by nikefalcon on 2010-05-09
by adding "xforcevesa" to the boot options i can boot and install Lucid but have to use it in low-graphics mode. Its very annoying!
I found two more similar threads:
[http://ubuntuforums.org/showthread.php?t=1476548](http://ubuntuforums.org/showthread.php?t=1476548)
and
[http://ubuntuforums.org/showthread.php?t=1476640](http://ubuntuforums.org/showthread.php?t=1476640)

---

### Post by davidmohammed on 2010-05-09
Ok, thats shows your boot issue is due to the intel graphics issue - possibly this wiki may help - 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

instead of xforcevesa - if you use
i915.modeset=1

what happens?

Also, just to confirm what your graphics card is - boot into your desktop (via xforcevesa) - open a terminal and type

lspci

Dump the contents here.

---

### Post by nikefalcon on 2010-05-09
Partial output of lspci:
```

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

i tried i915.modeset=1 boot parameter; didn't work.
anyway, i fixed it. Here's the tutorial:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
had to use "0" instead of "1"

Thanks :)

---

### Post by nikefalcon on 2011-03-17
Here are the links to for anyone who's interested, if at al....
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379)

Note: Fixed in Maverick.

---

