---
title: "Boots into terminal?"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Shichifuku on 2010-04-04
So, I haven't messed with Ubuntu in ages and kinda started to miss it, so I decided to go ahead and try to install it on my laptop

I got it to install (using Wubi) and the thing is when I start my computer it ask if i want to boot into Windows 7 or Ubuntu..I select Ubuntu..then it ask if i want to boot into 4 or so options, one of them being Unbuntu..I select that and it just starts showing text.  After a while the loading screen pops up and it goes back to the text but this time ask for my username and then password, after that it lets me type in stuff.

I looked around and did a few things.  I was told to try typing like..."startx" or something similar, and it made me go to a normal looking desktop, but the thing is that my keyboard nad mouse both started not responding when I did that.

Any suggestions as to what I should do>

I am using a Toshiba Satellite 505D laptop.

Sorry if I posted this in the wrong place >.<

---

### Post by me13221 on 2010-04-05
What are the "4 options" you mentioned?

---

### Post by lisati on 2010-04-05
Is it possible that you installed the server edition, which doesn't come with a GUI? The "desktop" version of Ubuntu, which comes with a GUI, works on laptops too.

---

### Post by oldfred on 2010-04-05
While I do not think this is your problem it may be in the future and you should do this update:

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Have you tried booting from the recovery mode and running all the updates to see it that fixes anything?

---

