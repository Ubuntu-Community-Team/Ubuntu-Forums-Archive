---
title: "Downgrading to hoary again - impossible?"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by tag on 2005-10-16
I tried out breezy and I didn't like it. So i figured i'd go back to hoary (outlined here [https://wiki.ubuntu.com/DowngradeHowto](https://wiki.ubuntu.com/DowngradeHowto) ) but unfortunately nobody ever told me anything about how to repair a broken sources tree. The article just mentions

> The last step probably will end up a catastrophic mess of incompletely installed packages. We need to fix that now.

Which means, that I am left with a broken treen and cannot install anything without aptitude or apt-get whining about packages that cannot be installed. How exactly does one fix something like this? I find the advice in said Article above more than vague.

---

### Post by Leif on 2005-10-16
that's not advice, that's their way of saying nobody's really bothered doing this.

---

### Post by tag on 2005-10-16
Okay then - has anybody got a real advice for me? Please?

---

### Post by kudu on 2005-10-16
My opinion is the best way to go about these things is a fresh install whether it be Hoary or Breezy.

---

### Post by microo on 2005-10-16
So there's no objection to reinstall Hoary ? Does the repositories will continue to be accessible ?

I would like to run Hoary ....and waiting for Breezy to get fix of all the bugs.

The Ubuntu Guide for Hoary is a fantastic tool for beginners like me.

Thanks

---

### Post by linkunderscore on 2005-10-16
Well, what didn't you like about Breezy? 

I personally wouldn't try to downgrade (unless you are willing to do a completely fresh install. It would be easier for you to try and fix whatever you don't like about Breezy, than it would be to downgrade back to Hoary.

---

### Post by tag on 2005-10-17
What I didn't like? 

[LIST]
[*]My umlauts do not work (this is bad, because I happen to live in Germany)
[*]Noatun doesn't work although i have installed all codecs one can imagine
[*]KDE doesn't talk to my memory stick
[*]The Kernel is compiled with a gcc3.x version but the default compiler is gcc4.x - this makes for a lot of problems (can you say VMWare?)
[*]My screensaver just crashes instead of doing something with the display
[*]My graphics card doesn't do OpenGL acceleration on breezy
[/LIST]

These were just the things that happened to come to mind just now.
Anyhow, I do like the fact, that my printer works over cups. This is something hoary was never able to do right. But then again...without umlauts - it's not much help.

Now, when you say "fresh install" do you mean the same "fresh install" as in "wipe your harddisk and install a new OS?" Because then I would feel like i was in Microsoft land. :p

---

### Post by tag on 2005-10-17
oh...and I didn't mention that i have a dualscreen system, and for some reason lots of programs like kmixer, gxine etc open requesters, or even the fullscreen mode at totally unpredictable and undesirable locations. The Xinerama integration in hoary was much cleaner.

---

### Post by chaok on 2005-10-18
[QUOTE=tag]What I didn't like? 
[*]The Kernel is compiled with a gcc3.x version but the default compiler is gcc4.x - this makes for a lot of problems (can you say VMWare?)
[/QUOTE]

NO JOKE!  I mean this is a pain.  I got VMWare to work, but then when I install my nVidia drivers it yells some more.  I don't know what to do.  For now I'm going back down to 5.02 becuse I don't have time to mess with it.  

If I could find a solution to this I would stay with Breezy.  I liked it for the most part.  Could I recompile my kernel using gcc4 or something?

---

### Post by UbuWu on 2005-10-18
[QUOTE=microo]So there's no objection to reinstall Hoary ? Does the repositories will continue to be accessible ?
[/QUOTE]

Hoary will be supported for at least 12 more months. After that, no garantees, but I expect the repo's will stay online even longer, but you probably will want to upgrade to a newer version by then. So no objections for now...

---

### Post by tonyw50 on 2005-10-18
Edit each repository in Synaptic or Update Manager to change the distribution entry from "breezy" to "hoary".

---

