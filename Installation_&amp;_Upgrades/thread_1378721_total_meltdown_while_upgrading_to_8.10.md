---
title: "total meltdown while upgrading to 8.10"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by endtheembargo on 2010-01-11
Hey everyone,

I have a toshiba A135 laptop that has been running an old old version of Ubuntu, mainly because I didn't have it set up to receive automatic updates.

I decided to upgrade it (to version 8.10), and in the middle of the upgrade, it froze. I had no choice but to reboot the computer. Once I did, it would no longer boot. I tried booting in recovery mode and "fix" the broken packages, and that didn't fix it. When I boot the computer it prompts me to enter my username and password, and then it sits at the blank pink screen forever and doesn't advance on into the desktop.

The next thing I tried was booting from an ubuntu 9.10 disk in hopes that once I was inside the computer, I could at least back up some files that I didn't want to loose on an external hard drive - especially if I was going to end up having to reinstall.

I am able to get to the alternative boot source screen and select boot from cd. Then I select "trial run of ubuntu 9.10 and it just sits at a black screen with the cursor flashing forever.

Now I'm at a loss. I would like to be able to at the very least get into my computer and save some files to my external drive but I can't seem to able to do it. I need some help :(

---

### Post by zvacet on 2010-01-11
You tried to upgrade your not updated version.I don´t know f this will work but try it anyway.In recovery mode

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by endtheembargo on 2010-01-11
Thank you I'll try that. And I probably should've specified that I'm not always very good at this techy stuff though I'm trying. When I start up the computer, where exactly do I go so that I can input sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade?

---

### Post by ulfj on 2010-01-11
the terminal is where you do that.

---

### Post by endtheembargo on 2010-01-11
How do I access the terminal when I can't get into the desktop?

---

### Post by zvacet on 2010-01-12
Boot in recovery mode and after login type 

```
 apt-get update && sudo apt-get upgrade
apt-get dist-upgrade
```

---

