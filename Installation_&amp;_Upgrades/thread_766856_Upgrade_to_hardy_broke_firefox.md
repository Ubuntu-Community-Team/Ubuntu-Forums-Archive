---
title: "Upgrade to hardy broke firefox"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by JayeD on 2008-04-25
I upgraded overnight and have found that hardy has installed a beta version of firefox when I had a fully working version of 2.0.0.14. I'm not happy about that. Anyway, I reinstalled 2.0.0.14 and now none of my add-ons will install. I used a number of them daily and they don't work for firefox 3 and now don't work for 2 either.

Any ideas?

---

### Post by jledhead on 2008-05-08
I think it was very sloppy of the ubuntu team to include a beta release over a full release.  upgrading broke my firefox also.  none of my addons work with firefox 3, which is why I didn't upgrade firefox on my own.  Also with the upgrade, Hardy decided not to add java to firefox 3.  I have tried everything to get this to work and it will not.  So I tried to back up to firefox 2 and removed everything firefox, guess what, now it doesn't work.

After some time I was able to manually get java working in firefox2.  so thanks ubu team for breaking my firefox :(

---

### Post by JayeD on 2008-05-08
I forgot that I'd posted this...

Anyway, I used a plug-in called Night something (sorry I forget) that overrides the checks for the plug-in versions and that worked for a while, but then a few days ago everything stopped working again. No idea why. I fixed it by removing firefox 3b5 completely, saving my bookmarks and any other settings I could export and then deleting my firefox profile folder ~/.firefox (double check though, I'm at work on winblows). I then opened firefox 2 and reinstalled my plug-ins. Next, I went to System>Preferences>Preferred Apps and set my default browser to be firefox-2. Everything seems perfect now.

I did find a funny thing during reinstalling my plug-ins though. I forgot to remember the theme I used so I looked for a new one (I've just remembered, it was iFox, lol). I searched for linux styled ones and got a list of them. Funny thing was that I was told I couldn't install the linux styled themes on Linux. How mad is that? lol In the end I went for a simple Gnome styled theme where the little foot has its toes pulsing as the page loads. :)

---

### Post by paulmcnally on 2008-05-08
Has anyone found a solution to this problem? I have spent hours reinstalling everything related to firefox. Why was a beta version of firefox distributed?

paul

---

### Post by jledhead on 2008-05-08
I am now running firefox2 and it seems to work fine.  But none of the addons works, they can't be uninstalled, enabled, or upgraded.  I make a change (like enabling or uninstall) and it says it will happen when firefox restarts.  Restart firefox and nothing, they are still there saying they are waiting for firefox to restart.  exit out of FF and do #ps aux|grep firefox 
and its not running.  start it back up and same thing, they are in a completly non-working state.

I still think this was very very irresponsible for the ubu team to include a beta release of FF.

---

