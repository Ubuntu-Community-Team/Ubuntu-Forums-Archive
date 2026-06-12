---
title: "[SOLVED] Install Problem"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by darkzeus85 on 2008-04-18
I have custom build desktop that is a little old but not too bad (3 or 4 years since last upgrade / build). I have plenty of hardware resources  like ram and processor fairly good graphics card as well even to todays standards. My problem arises when trying to run live.(Ubuntu 7.1)  I insert disk and click on run/install, it dose the whole bouncing bar thing then the screen goes to what is like a DOS prompt and the screen flickers 3 or 4 times and the curser appears in the form of an X and a dialog box pops up saying that it can not auto detect the screen or graphics card and i can either manually configure shut down or continue in low graphics mode. I thought fine continue in low graphics mode until i can complete install. It goes back to the prompt looking thing and stops completely. So I go back through the loading process back to the dialog box and click configure. Now no matter what configuration I use it still goes to the prompt and stops. No loading sounds the cd drive eventually slows to a stop and it idles, or seems to idle. please help because I am tired of windows.

---

### Post by overdrank on 2008-04-18
> **darkzeus85 said:**
> I have custom build desktop that is a little old but not too bad (3 or 4 years since last upgrade / build). I have plenty of hardware resources  like ram and processor fairly good graphics card as well even to todays standards. My problem arises when trying to run live.(Ubuntu 7.1)  I insert disk and click on run/install, it dose the whole bouncing bar thing then the screen goes to what is like a DOS prompt and the screen flickers 3 or 4 times and the curser appears in the form of an X and a dialog box pops up saying that it can not auto detect the screen or graphics card and i can either manually configure shut down or continue in low graphics mode. I thought fine continue in low graphics mode until i can complete install. It goes back to the prompt looking thing and stops completely. So I go back through the loading process back to the dialog box and click configure. Now no matter what configuration I use it still goes to the prompt and stops. No loading sounds the cd drive eventually slows to a stop and it idles, or seems to idle. please help because I am tired of windows.

HI and welcome, what is the model for the graphics card and have you tried when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga= 771  or 775 then press enter. Hope fully this will let you run the live cd and you could always install via the alternate cd as it is a text based installer.

---

### Post by darkzeus85 on 2008-04-18
I feel like a moron. I was reading other threads about problems like my own and seen that someone had a problem close to mine and someone recommended loading live in safe graphics mode. Light bulb! I tired it and got to the desktop or whatever ubuntu calls it, started the installation process and now I am waiting on it to resize the main partition although the progress bar has not moved. If this becomes a problem I will let you all know and go from there but I will let it set for a while and work since it seems to be doing just that.

---

### Post by darkzeus85 on 2008-04-18
I believe my graphics card is an ATI Radeon 9600 All in wonder with like 512k. But as my last post says my first problem is solved for now thanks for the help.

---

