---
title: "upgrade dual boot 8.04 to dual boot 8.10 (and keep win xp intact)?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by bokl on 2008-10-31
Hi, my laptop has dual boot (ubuntu 8.04 + Win XP). I now want to update to 8.10 but keep the dual boot and the Win XP install intact.

How do I do that?

When I boot the 8.10 installer and choose manual I get to the "prepare partitions" screen. It looks like this:
[IMG]http://img126.imageshack.us/img126/2787/78206405sn7.jpg[/IMG]

(The NTFS partition is my win XP installation. The others are for Ubuntu.)

1. What do I need to do to upgrade my dual boot installation from that step?
2. Will the installer automatically keep/add GRUB?
3. Will the installer recognize my current dual boot and migrate all settings or do I manually need to edit /boot/grub/menu.lst so that win XP showns up on the boot menu?

---

### Post by outerspacerace on 2008-10-31
I wish I knew beforehand too :(

[http://ubuntuforums.org/showthread.php?p=6071050#post6071050](http://ubuntuforums.org/showthread.php?p=6071050#post6071050)

---

### Post by saj0577 on 2008-10-31
I believe you just need to declare your mount points "/" and your swap and that is all and it should leave the rest intact.

_**DONT TAKE MY WORK I AM NOT 100% THOUGH**_
Just advise that im fairly sure of.

Saj

Do you have a seperate home partition?

---

### Post by outerspacerace on 2008-10-31
I believe I did both those things correctly.

Now I'm fairly convinced that the install going nuts is what stuffed up my attempt at getting 8.10 up and running.

Sorry to get off topic a bit just wanted to thank the last poster for the advice.

Let me know how you go though okay?

---

### Post by bokl on 2008-10-31
@ outerspacerace: thanks for the link and the heads up. Sorry about the problems you've had. I hope we can find a reliable method for doing this kind of upgrade. (The best thing would of course be if the Ubuntu installer automatically had support for such upgrades. Let's hope that's in place for 9.04!)

@Saj: Ok I will test your suggestion when I get home tonight...
The laptop is not used so often and has no important files so the worst case scenario is just that I'll have to spend some time reinstalling both OS.

Before I go ahead could you clarify the "declare your mount points" part a bit? You see, it was some time since I set up the dual boot system and I, embarrasingly enough, don't remember what exact steps I took to get it working back then. When I earlier tested clicking "Edit partitions" I got to a screen where I could select type and mount point for each device. That's what you suggest that I, right? As you see from the screenshot there are three non-ntfs devices. If I recall correctly I think the large one was mount point "/", the small 246MB one was "/boot", and swap was swap. Does that make sense? If so, then do you still suggest that I should only declare "/" and leave the 246MB one "un-declared"?

---

### Post by caljohnsmith on 2008-10-31
Bokl, I think you might find this tutorial helpful:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

It leads you step-by-step through the Ubuntu installation process with lots of great screen shots. Let me know if that helps. :)

---

### Post by Mark Phelps on 2008-10-31
If you're happy with your previous Ubuntu installation, why not just upgrade using Upgrade Manager?  That will simply install and upgrade your existing installation, leaving your settings intact.

---

### Post by bokl on 2008-10-31
ok, I had less time today than I thought so I'll have to do the 8.10 install later this weekend...

@carljohnsmith: After a quick read (maybe too quick?) I didn't find answers to my specific questions on that page (though it looks helpful in many other respects)

@mark phelps: have you yourself tried to upgrade a dual boot system using the Upgrade Manager and verified that it worked and kept the other OS and GRUB settings intact? Or have you read about it (if so do you have a reference?)

---

### Post by outerspacerace on 2008-10-31
Bokl, see my thread linked above for the solution I found - it may ease your mind about doing a clean install.

Basically, although GRUB and my install was messed up I got it back fairly easily in the end.

BTW I have done the upgrade method (tried that first) and it worked fine, the dual boot was in no way affected. I just wanted a clean, as new interface for a change. 

I reckon you'll be fine to go with that method too, just keep your eye on the installer ;)

Well, that and the upgrade put all the KDE apps in my menus which I didn't want...

---

