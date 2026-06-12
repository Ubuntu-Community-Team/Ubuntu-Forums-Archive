---
title: "Kubuntu won't uprade..."
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by Win2Mac2Linux on 2007-12-23
Hello!!!  I am trying to upgrade my just installed Kubuntu to 7.10.  I followed the very simple (or so I thought) prompts during the upgrade process.  I eventually get to the "Distribution Upgrade" box/window and it goes through its' steps.  I get a green checkmark next to "Preparing the upgrade", "Modifying the software channels", and "Fetching the upgrades".  However, it seems to get stuck on "Installing the upgrades" and stays at 0%.  I have tried cancelling out of this step and retrying with the same results.  Any help would be greatly appreciated. Thanks.

---

### Post by Partyboi2 on 2007-12-24
What version are you upgrading from?
Make sure that all 3rd party Software is unticked in "Software Sources"
You could have a look at the  log files /var/log/dist-upgrade to see if that gives you any clue.
You could also try using the alternate cd to upgrade
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by Win2Mac2Linux on 2007-12-25
First, thanks for that "safe ubuntu(ing)" link.  At first I thought it was just some sort of line, but I'm glad I ended up checking out the link.  I had no idea.  It's a shame people have to be like that.  I could easily be one of those people following some advice without being a little suspect.

Back to my issue, I'm not sure which version of Kubuntu I originally installed.  I had just downloaded it the other day from the newsgroups and it was listed as 7.10.  However, after installing, I went to update and it showed there was a version upgrade available to 7.10 so...

I have a bigger (I'm afraid, but hopefully it will work out) problem now.  Whenever I boot, it goes through the Kubuntu startup screen with the blue bar extending across.  After that the screen goes blank and nothing else happens.  I've never seen that happen before (regardless of OS) :confused:.      I downloaded the Kubuntu 7.10 cd to my laptop and burned that to try a fresh install.  The same thing happens.  I get the Kubuntu startup screen and then when I expect to see the install process (or the inititiation of the desktop startup) the screen blanks and nothing else happens.  Any suggestions?  

Thanks for responding to my initial post.   :)

---

### Post by Partyboi2 on 2007-12-25
When you get to the blank screen are you able to get to a terminal? (Ctrl+Alt+F1)
If so what does dmesg say? Any error messages?
```
dmesg |tail
```

---

### Post by Win2Mac2Linux on 2007-12-27
I ended up just reinstalling using Ubuntu 7.04 and did a full upgrade for 7.04 and then a version upgrade to Gutsy.  So far, so good.  I'll post more if I run into problems again.  Thanks for your help.

---

