---
title: "Bad Ububtu Install experience"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by wheedan on 2007-09-27
Heya, just wanted to pass along some feedback

I just spent about 30 hours trying to get a working Ubuntu 6.04 install. Hardware is a AMD 64 3200 with 1.5gb RAM and a AGP nvidia 6600.

First attempt was from the live CD. No go, it would hang at seemingly random parts of the install process. So I switched to the non standard install. This installed the OS fine. Then the real problems started.

Essentialy, I was getting random hangs after between 5-10 minutes of up time. I did some searching of the forums, and this seems to be a fairly common error. I found and tried the following fixes:
Noapic
nolapic
reconfigure xserver-xorg to use vesa or nva
Turn off powernowd

None of these made any difference whatsoever to the symptoms I experienced. I notice that a lot of the forum posts list mem checks in response to this issue - which seems pointless when I known good hardware that has been successfully running windows with no Issues for approx 2 years. The general vibes in the forum seem to be that no one has any idea why this occurs, or really cares as long as it doesn't happen to them. Not really very helpfull.

I realize that Ubuntu is offereed for free, and that there are a lot of people who it works fine for, but if this issue is as widespread as my searching of the forums seems to indicate, I really think you need to work out what is causing it, and fix it. And unless im missing something, if its occurring on systems that run other OS's fine, its definately not a hardware problem. An incompatability perhaps, but one this prevalent seems to me to be an OS issue.

Ant way, back to reinstalling craptastic XP for me. Hope you fix this so I can get ubuntu working :)

---

### Post by ddrichardson on 2007-09-27
There's no point suggesting bugs that need to be investigated in these forums, if you feel there is an issue it needs to be in the bug tracker (launchpad). That is where the developers will find out about it. Also, launchpad asks for the information that developers actually need, such as certain file outputs to assist their debugging.

You will also always get people who suggest certain solutions to problems because either a) they are the type of person who fault finds from the start of the problem to the end and needs to tick all the boxes on the way; b) it worked in thier case. The forums are not staffed by paid support staff, they're community volunteers and enthusiasts who mean well and try their best.

I notice from your post count that you haven't actually tried to open your own thread regarding your problem and so aren't really giving the system a chance -- no two problems are the same. If you wish to post more information on your particular system then I'm glad to help.

---

### Post by wheedan on 2007-09-27
This was intended more as feed-back than a bug report - from my forum browsing there are already a number of bug reports on freezing issues. And please dont take it the wrong way - from having a play around with the live CD, overall the OS seems pretty nifty.

As far as giving the system a chance goes - what Information do I need to provide? Are we talking more specific hardware information, or logs?

Also, I'm trying linux mint as well, one of the forum posters with a very similar issue was saying that worked, even tho the build is almost identical to ubuntu - Ill post if that works.

---

### Post by jrmink on 2007-09-27
Well I can also say I haven't had the best experience with Ubuntu...Im still working on my issues though.  Im almost to the border of going back to windows atm.. But tell me how ubuntu mint is and if its nice could you post some links to it because this is the first I have heard of it.

---

### Post by Warren Watts on 2007-09-27
[http://linuxmint.com/]("http://linuxmint.com/")

---

### Post by kshane on 2007-09-27
> **wheedan said:**
> Heya, just wanted to pass along some feedback

I just spent about 30 hours trying to get a working Ubuntu 6.04 install. Hardware is a AMD 64 3200 with 1.5gb RAM and a AGP nvidia 6600...



Why haven't you tried to install Fiesty, the most recent release?

In my experience (though short), it goes in* very* smoothly...

Kevin

---

### Post by jrmink on 2007-09-27
Will I be able to run linux-mint on a 192mb ram laptop pentium III processor?

---

### Post by Warren Watts on 2007-09-27
Linux Mint is pretty resource hungry in my experience.  It ran pretty slowly on my 256MB 700MHz Duron.  Too slow to suit me, in fact.

The only way you are really going to know is to install it and see.  You really can't make any judgements from the Live CD, because it doesn't use the hard drive...

---

### Post by JBAlaska on 2007-09-27
wheedan, have you checked your CPU temp? a overheating CPU could cause freezes like the ones your describing.

Just a thought

---

### Post by wheedan on 2007-09-27
> **kshane said:**
> Why haven't you tried to install Fiesty, the most recent release?

In my experience (though short), it goes in* very* smoothly...

Kevin

Sorry, forgot to mention, tried 7.04 first, exact same issue. Installed 6.04 LTS as its meant to be the "It just works version.

> **JBAlaska said:**
> wheedan, have you checked your CPU temp? a overheating CPU could cause freezes like the ones your describing.

Just a thought

As far as I can tell ( Cant check CPU temp while running as its a complete hardware lockup, but checked immediately after restart), CPU temp is normal. Any chance that linux would have heat issues at a lower temp than windows? ( unlikely, but me is a linux n00b)

I also found i get the same issue with Linux mint.

Im leaning towards this being a X issue - thats the thing that runs the desktop gui right? Box seems to run fine as long as its in text install or recovery mode, but the moment i run it with a desktop it starts freezing :(

---

