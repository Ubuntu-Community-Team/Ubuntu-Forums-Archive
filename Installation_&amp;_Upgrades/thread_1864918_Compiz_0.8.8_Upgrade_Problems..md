---
title: "Compiz 0.8.8 Upgrade Problems."
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by G_khan on 2011-10-19
Hello chums,

I have a problem with my desktop now after upgrading my compiz.  I followed this guide: [http://ubuntuforums.org/showthread.php?t=1780509](http://ubuntuforums.org/showthread.php?t=1780509)  

Before going to this guide and upgrading, I noticed that I could no longer view the cylinder or watch it spin.  When I would switch the desktop to a different face, I wasn't able to see it spin any more.  So I upgraded compiz and now I no longer able to use certain shortcut keys, like calling the terminal for example (Ctrl + Alt + T).  On top of that, every window I open looks funny as if it's missing something around the edges.  Moreover, any window I open appears at the top left corner of the screen and in the case of firefox, I cannot move it around.  When I type "compiz" into the terminal I get the following message:

compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Clearly something is funky with compiz, but I don't know how to fix it (obviously right?)  I am dual booting lucid with windows 7 on a Toshiba Satellite A665-S6050, by the way.  According to alsamixer I have an HDA Intel card, not sure if that is relevant.

---

### Post by Luffield on 2011-10-19
I'm not sure your complied compiz is the problem. I'm running Lucid on my netbook and after I updated my system (about 14 hours ago) compiz stopped working here too. Trying to start it manually gives the same error messages as yours. Compiz was not one of the packages that got updated. The only relevant ones that was updates are probably Xorg packages (core and common).

---

### Post by Luffield on 2011-10-19
This seems the bug that casues the problem on my system, and possibly yours too.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905)

I suggest you wait until you get the fix before trying to fix something that might not be broken.

---

### Post by G_khan on 2011-10-22
Hello,

First off thanks for your quick response and my apologies for my late one.  It's just that I'm flooded with math hw so haven't exactly been online.  

I checked out the launchpad link you provided and I guess when you say wait for a fix, it would be posted on there, right?  

I ran the usual command "sudo apt-get upgrade && sudo apt-get update" and I can at least see that the four desktop faces are back (on the bottom right hand corner of the screen), but I'm still unable to switch between the faces.  This blows and I hope this problem doesn't persist else I'm going to contemplate upgrading to Natty.  But I really don't want to.  Thanks again.

---

### Post by G_khan on 2011-10-30
Luffield,

I was wondering if the problem on your system has been fixed.  According to launchpad, everything should be working fine by running sudo apt-get update && sudo apt-get upgrade.  But the problem persists on my system.

-Khan

---

### Post by G_khan on 2011-10-30
Also I've been unable to post anything or send messages on ubuntu forums.  Right now I'm working from  Win7 so I'm able to post messages.  Not sure if that problem is related to the  problem mentioned in my first post.

---

