---
title: "Upgrade to 10.04 and now I have no audio on web video"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by Jengle on 2011-04-11
Since I upgrade my PC to 10.04 lucid I cannot get any audio when I play videos on the web.  I can have tried YouTube, Comcast, Hulu, etc... The video plays just fine, but no audio.  I can go to Apple.com and play videos just fine with audio.  I can play any other audio just fine (mp3's, CD's, etc...).  So I have narrowed it down to possibly a Flash player issue.  I have tried flashplayer-nonfree, flashplugin, etc... and no luck.  Here is where it gets weird.  I saw a similar post and they tried creating a new account and it worked.  So I tried that.  I created a test account and all of the videos play just fine without any issue.  

Does anyone know if there is a way to rebuild or repair an account in Ubuntu?  I have checked all of the group memberships and they all match the new account that I setup.

---

### Post by mörgæs on 2011-04-11
If you have a directory with configuration files for Flash in your /home folder, try to rename it.

---

### Post by lightalone on 2011-04-11
I had the same problem, but after I did all the updates update manager recommended everything seemed to work fine. I'm new, so I'm not sure why this worked, but it's easy to do and might fix your problem.

---

### Post by Jengle on 2011-04-11
Thanks for the suggestions.  I am current on updates so that didn't do it for me.  I did find a directory \home\.adobe\Flash_Player.  I renamed that and of course a new one was created once I launched Firefox.  Unfortunately, my problem still continues.

---

