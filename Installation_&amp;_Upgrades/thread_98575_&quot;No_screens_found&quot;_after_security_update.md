---
title: "&quot;No screens found&quot; after security update"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by B0rsuk on 2005-12-03
Hey

I led my Kubuntu life happily for a while, until I noticed that I didn't uncomment some important lines in /etc/apt/sources.list. Specifically, security updates after the two "backports" lines. I thought everything past "backports comments" was backports.

Up to the point I had all packages installed and upgraded. I have an old GeForce2MX card, so I used glx-legacy package and it worked.

So when I uncommented the "security" lines and did "fetch updates" and upgraded all packages... + reboot...

X wouldn't start. The error was something about framebuffer. I did "sudo dpkg-reconfigure xserver-xorg.conf" (or something) and after several tries fixed my problem by choosing "the other one" - the option which uses no framebuffer.

But my hardware acceleration packages wouldn't load properly. I quickly checked old xorg.conf and it appears that "nv" drivers are loaded instead of "nvidia". After fixing that it still wouldn't work.

So I'm tinkering with it again... I just wanted to tell you it shouldn't happen. I have a strong belief upgrades should be safe. I'm still kinda safe because apparently reverting to old settings is a matter of choosing older kernel (..9 instead of 10) in grub, but still...

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

---

### Post by towsonu2003 on 2005-12-04
it is possible that your upgrades include the kernel upgrade (nothing to do with backports). do ```
uname -r
``` do you see "2.6.12-**10**-somethingsomething" instead of "2.6.12-**9**-somethingsomething"? if yes, you did a kernel upgrade and if you did not do so yet, you need to recompile your nvidia just like you did a while ago after installing ubuntu...

---

### Post by Tallowwood on 2005-12-04
I have had a similar error message after running the Breasy 5.10 LIVE CD. I have the Hoary 5.04 distribution with Gnome installed on my machine, also with a nvidia graphics adaptor (MX440 still supported, just). I probably posted in the wrong place (!) see:  [http://ubuntuforums.org/showthread.php?t=98764](http://ubuntuforums.org/showthread.php?t=98764)

There are some posts on other forums mentioning a similar sort of error in different circumstances (eg. [http://ubuntuforums.org/showthread.php?t=98757](http://ubuntuforums.org/showthread.php?t=98757)) and also on the nvidia site's own forums. 

Sorry I can't help with a solution. 

cheers, Tallowwood

---

### Post by mo_x on 2005-12-04
Try reinstalling the nvidia-glx-legacy package.
```
apt-get install --reinstall nvidia-glx-legacy
```

---

