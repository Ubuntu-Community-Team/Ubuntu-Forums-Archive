---
title: "evince symbol lookup error"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by manzdagratiano on 2010-02-07
This started with doing something stupid:
I was trying to enable certain karmic repositories in my jaunty (by creating a file in the sources.list.d directory) in order to pull the latest virtualbox (to be able to run Dustin Kirkland's testdrive) - with the hope of using apt-pinning. The apt-pinning did not quite work I guess because on a sudo apt-get update followed by sudo apt-get upgrade, it asked me to upgrade a few libraries (no major kernel upgrades or anything). I let it happen (I do not remember which libraries I upgraded - major bummer!), and all went fine, except that I realized later that trying to install the new virtualbox would break certain other packages. I immediately disabled the karmic repos, and rebooted: all was fine and nothing was broken after the reboot, except for something I realized later on - my evince has become useless.

Upon double clicking on a pdf document, there would appear an applet stating "opening..." and then disappear. Upon using the command line, I get the error:

evince: symbol lookup error: evince: undefined symbol: ev_view_update_view_size

Unistalling and reinstalling has proved fruitless. Any ideas to track down which libraries it links to are creating the problem?

---

### Post by manzdagratiano on 2010-02-07
And yes... I am stubborn enough to refuse to do a clean install merely for the sake of this annoying trifle... and I am stubborn enough not to resort to acroread - too bloated for me (it's enough that I use adobe-flashplugin)... There HAS to be a way to detect what the culprit is!

---

### Post by manzdagratiano on 2010-02-08
No takers? Must I remain subject to bending xpdf to my will?

---

### Post by Herry Susilo on 2011-05-07
I have just installed Ubuntu 10 Lucid. I have the same error. When I double-click on pdf, it's not shown. When i try to run it from terminal, it shows the symbol lookup error. I have removed and reinstall evince. It doesn't change anything. It's better to remove Evince. It's use less.

---

### Post by manzdagratiano on 2011-05-08
Well this thread is a little more than a year old, but I should still state that no measure I took in Jaunty solved this problem for me, until a clean install of Karmic. I have since then decided to **never**, ever mix sources - it is a panacea for disaster!

---

