---
title: "Firefox add-ons broken"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by peterwr on 2007-07-25
**RESOLVED** - see #4 below. 

Hi All 

Here's the situation: I'm using Firefox 2.0.0.5, and none of my add-ons (extensions or themes) work. When I go to Tools > Add-ons, they all show "This add-on will be installed/uninstalled/upgraded when Firefox is restarted", but none of them ever are, and none of them seem to work, regardless of which option is selected. The buttons to install/uninstall/upgrade are greyed out seemingly at random - i.e.the state of the buttons has no apparent relationship to the alleged state of the add-on. This is particularly painful in the case of the Web Developer toolba, which I rely on. 

The damage seemed to occur when I upgraded from Dapper to Edgy by altering the names of the repositories; this screwed up not just FF (I was on 1.5.x at the time), but also blitzed the partition table, so Edgy lost its swap partition. Upgrading to Feisty fixed the partition issue, but Firefox Add-ons are still fritzed. 

Any ideas? I've tried deleting profiles, but that didn't seem to fix it. FF just made a new profile as futzed as the previous one. 

TIA...

---

### Post by DC@DR on 2007-07-25
I would recommend fresh install over upgrading, or you could try this project which install mozilla FF version manually: [http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by peterwr on 2007-07-25
A fresh install of Feisty? Hmmm. I was hoping to avoid that, but thanks. I was wondering which files hold the screwed-up information and how I could edit/remove/reinstall them to make it right. I've tried reinstalling FF, but that didn't fix it, and if I trye to Remove or Completely Remove FF, it wants to take the whole of Gnome with it, apparently. I'm hoping not to get that drastic. Yet. :(

Thanks anyway, DC.

---

### Post by peterwr on 2007-07-26
Aha. I seem to have found a fix for this, semi-accidentally. In [another thread on a similar subject]("http://ubuntuforums.org/showthread.php?p=1739590#post1739590"), I found a suggestion to go to **about:config** and set **xpinstall.disabled** to **enabled**. That wasn't quite my problem, but out of curiosity I disabled it and then tried downloading and installing an extension. FF popped up a prompt saying software installation was disabled and offered me the option of enabling it, which I did and installed the extension. I then noticed that some of the broken extensions were now fixed. I went through the sequence a couple more times (disable installations, try to install stuff, enable installation when asked) and all my extensions were fixed. The same procedure worked for the Themes. 

HTH.

---

