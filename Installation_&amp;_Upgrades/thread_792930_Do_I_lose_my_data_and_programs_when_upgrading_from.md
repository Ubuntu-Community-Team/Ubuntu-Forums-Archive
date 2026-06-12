---
title: "Do I lose my data and programs when upgrading from Gutsy to Hardy?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by ddado on 2008-05-13
Well, I guess the title of the topic says it: Do I have to worry about the loss of any data on my computer when upgrading? Also, do I have to worry about the performance of Wine and AWN which I have installed on my Gutsy?

Please tell me, cuz otherwise I'd be too scared to do anything. :-)

Thanx!

---

### Post by pytheas22 on 2008-05-13
In principle, no, you don't have to worry.  On the other hand, in reality it seems rare (from reading these forums) to hear of an upgrade that goes perfectly, but most proceed without any serious issues--you might have to tweak a few things but it shouldn't be a big deal.  Of course, you should always be backing up your data anyway, and if you're not, now might be a good time to start.

---

### Post by Darkchef on 2008-05-13
if i was you i'd probably just backup everyhting i wanted and do a fresh install, it will cause less hassle and should work without any problems :D

---

### Post by pytheas22 on 2008-05-13
> if i was you i'd probably just backup everyhting i wanted and do a fresh install, it will cause less hassle and should work without any problems

I should have said this earlier, but I second this.  Even though upgrading usually works well enough, in my experience it's always been simpler to do a fresh install than to fix all the little problems that you'll probably get after the upgrade.

To make things easier in the future, you set up /home on a separate partition from the rest of the system; that way, you can reinstall next time without even having to backup your personal settings and data.

---

### Post by ddado on 2008-05-13
Well, I do intend to backup my documents and stuff... the thing I'm worried about most are Wine, AWN manager, Emerald themes and stuff like that... Cuz i really don't feel like having to install them all new...that is the reason why i don't want to have a clear install, but only an upgrade...

So, what about those installed programs? Do they usually stay or do they get removed?

---

### Post by pytheas22 on 2008-05-13
> So, what about those installed programs? Do they usually stay or do they get removed?

They'll be removed.  In principle, however, you could back up your system's /usr directory, which contains almost all of the programs on your system, and copy it back in after the reinstall.  In theory this would save you from having to reinstall those things again.  You may also have to backup and copy over /etc, which contains configuration files that some of the programs on /usr might need.  I can see this getting messy, however, with potential problems with permissions, package lists and things.  But maybe it would be ok.

---

