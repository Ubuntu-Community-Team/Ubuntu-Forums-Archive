---
title: "Upgrading Wubi-installed Ubuntu broke Hardy, help!"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by zhinker on 2008-04-22
Hi,

I installed Hardy on my laptop today via Wubi.  It seemed to work just fine, everything was going great.  I noticed a hundred or so updates available so I downloaded that and enabled the proprietary Nvidia drivers while I was at it.  The driver change required a system restart, so I rebooted my computer.  

Everything seemed to boot up just fine except right before when you would expect the login screen to show up this picture popped up on my screen that looked like the screen was broken.  Stranger still, it started off grayish looking then gradually changed to a more ubuntuish orange over a minute or two (see attacked pictures).

Ctrl+Alt+Backspace didn't fix anything, neither did Ctrl+Alt+Delete.  When I push Ctrl+Alt+FunctionKey I switch to a terminal view as normal, but switching back doesn't change anything.  

Just so you know, nothing is wrong with my monitor, Vista still runs just fine on my laptop.

Does anyone know how I can fix this?  

Thanks!

---

### Post by Pumalite on 2008-04-22
I don't know anything about wubi, but in a normally installed Ubuntu, when your xserver fails, you reconfigure it:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg

---

### Post by zhinker on 2008-04-23
That did the trick, thanks.

Apparently whenever I enable the Nvidia proprietary drivers that problem occurs (I tried doing it again).  Does anyone have any idea how to fix this problem?

Apart from that my system seems to be working at 95% (My screen flickers a lot whenever I move around windows or scroll up/down in firefox.  Alsoeven though Ubuntu detects my dual monitor setup perfectly, it just clones the output of one screen on top of the other instead of extending the screens)

---

### Post by overdrank on 2008-04-23
> **zhinker said:**
> That did the trick, thanks.

Apparently whenever I enable the Nvidia proprietary drivers that problem occurs (I tried doing it again).  Does anyone have any idea how to fix this problem?

Apart from that my system seems to be working at 95% (My screen flickers a lot whenever I move around windows or scroll up/down in firefox.  Alsoeven though Ubuntu detects my dual monitor setup perfectly, it just clones the output of one screen on top of the other instead of extending the screens)

Hi and when you enable the restricted drivers again then use the command that (Pumalite suggested previously) again but with the -phigh tag ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Also what is the model of the nvidia graphics ?

---

### Post by zhinker on 2008-04-23
No, the -phigh tag didn't do anything different.  What is it supposed to do?

My video card is an Nvidia GeForce 8400M GS

---

### Post by overdrank on 2008-04-23
> **zhinker said:**
> No, the -phigh tag didn't do anything different.  What is it supposed to do?

My video card is an Nvidia GeForce 8400M GS

HI and for the lack of a better term it is like automatic setup. You may look at [[COLOR="Green"]Envy[/COLOR]](http://albertomilone.com/nvidia_scripts1.html) to help with the drivers

---

