---
title: "IE 8  with Wine can't access internet or anything"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by kooia on 2010-04-12
IE 8 can't access about:Tabs or [http://www.winehq.org/](http://www.winehq.org/)

It has a blank screen

What do I need to do to make it work?

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]http://kooia.info/images/abc123xm.png[/IMG]

---

### Post by BbUiDgZ on 2010-04-12
> **kooia said:**
> What do I need to do to make it work?

Windows?

Why would you want to run IE8?

you could always run a windows Virtual machine

---

### Post by Mark Phelps on 2010-04-12
Which MS Windows OS are you running?  IF it's XP, you should be able to use IE8.  IF it's Vista or Win7 -- it won't work.

See the Winehq link below for details:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

---

### Post by kooia on 2010-04-12
Yes, I'm using XP.

---

### Post by drreed on 2010-04-12
Whether you use Wine or VirtualBox, you still have to configure the networking in windows. I assume you did that right?

This sounds like a memory problem, i.e. you don't have enough to load that browser. I had trouble this morning trying to run windows in VirtualBox (yeah, I had to install windows to use 1 program that uses .NET)

I wound up allocating slightly over half my memory to get that resource hog to function (with some work arounds, i.e when the stack is too high, I save my work and kill the machine, then start over)

I also run News Rover in Wine (the best news reader ever) and that acts flaky, usually requiring a restart of Wine.

Another thing you could try, is to clean up hat browser by turning everything off you don't need.  I can't see what you wrote at the moment, but you mentioned XP. Why does that matter if your just running that browser under wine? XP isn't even there.
I can't imagine how MS IE any version would run properly without the whole kit-and-kaboodle that goes with it. If you are running windows (somehow that I don't understand) then clean up windows too. Switch to classic view, kill uneeded desktop icons, kill unnecessary services (go edit your startup.msi or whatever it's called)

ctrl-alt-del and check running processes. Shutdown spoolers, printer drivers, everything that you don't need. (somewhere in the forums of a game called Aces High II there is an excellent tutorial about what services are needed under windows and which ones aren't. They traditionally have needed every byte of ram they can muster for best game performance, and their tech guy wrote that after helping a zillion people clean up windows enough to play the game)

Hope this helps\

---

