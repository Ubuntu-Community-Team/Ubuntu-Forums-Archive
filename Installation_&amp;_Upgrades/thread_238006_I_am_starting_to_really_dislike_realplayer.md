---
title: "I am starting to really dislike realplayer"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by Mikawa Ossan on 2006-08-17
Why is Realplayer such a pain in the !"#!% to install?

I have it working perfectly on my desktop, but I can not get it to work on my laptop to save my life.

Here's what happened before I gave up and decided to ask for help:

1)  I made sure sound was working fine and I tried to install realplayer from "Add/Remove Apps"

It told me that there was a conflict with another program, so I could not install it.  Instead I should go to advanced mode to troubleshoot.

2)  So I did.  It told me that I needed some xlib or something.

3)  I did a search for the xlib and then installed the best looking thing that fit the description.  Sorry, I forgot what it's called.

4)  Tried to install realplayer again.  No dice.

5)  This time I tried installing Helix instead.  It installed without a hitch, but it wouldn't play the smil file I wanted it to.  (In other words, I couldn't listen to NPR online.)

6)  Since Helix gave me the option to check for updates, I did, but the only thing that showed up was the realplayer download page.

7)  I completely uninstalled Helix.

8)  I installed Automatix and used it to dowload and install Realplayer.

9)  Realplayer installed fine.  But there's one little problem:  I can'T get it to run!  The icon shows up in the Applications menu, but when I click it, nothing happens.  When I type "realplay" in the terminal, the following message appears:

cp: cannot stat `/usr/lib/realplay-10.0.7/share/default/.realplayerrc': No such file or directory

I checked, and my sound overall still works, but realplayer is once again, a dud.

Please help me.  I have no idea why realplayer has decided to hate me so.:-({|=

EDIT:  I tried in terminal again and this time I got a longer eror message

cp: cannot stat `/usr/lib/realplay-10.0.7/share/default/.realplayerrc': No such file or directory
/usr/bin/realplay: line 78: 14249 Segmentation fault      $REALPLAYBIN "$@"

Hope this helps somewhat.

---

### Post by kerry_s on 2006-08-17
I just used the real player10.deb package here-> [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

