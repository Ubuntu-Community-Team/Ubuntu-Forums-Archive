---
title: "Ubuntu users' perspective on 8.04 to 8.10 transition"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by edoviak on 2008-11-02
**EDIT:**

First, thank you to those of you who responded to my post. 

Reason for this edit: Some respondents wrote about the improved features in Ibex, whereas I was hoping to start a discussion about **[color=darkred]whether Ubuntu's development model is[/color]** (wholly or partly) **[color=darkred]responsible for the troubles that Ubuntu users have when they upgrade from one release to the next[/color]**.

Don't get me wrong. There are advantages to Ubuntu's approach. Namely, an Ubuntu user gets the "latest and greatest" software with each new release. I just wonder if Ubuntu compromises stability in the process. 

Looking forward to hearing your thoughts on the issue.


=============================================================
**ORIGINAL:**

While browsing Ubuntu Forums this evening, I noticed that some users were quite upset with the 8.04 to 8.10 transition. (My impression is that there were more complaints about previous transitions however). 

Although I don't use Ubuntu, I do like the distribution for what it has done to make GNU/Linux more user friendly, so it saddens me when users struggle through the upgrades.

To that end, I'm curious to hear the perspectives of seasoned Ubuntu users on why there are a significant number of complaints about the transition. In particular, do you feel that the criticisms quoted below are on target or is there something that he is missing?

[quote="Eck"]
from: [**Here's my rant regarding the new Ubuntu release**](http://forums.debian.net/viewtopic.php?t=26275)

What do I see, for an example of why Ubuntu hasn't ever even gotten installed on my PC? Their Release Notes suggest that users of the previous LTS version should wait until the 8.04.1 point release sometime in September before upgrading! Their forums are filled with pages and pages of, not minor problems regarding not knowing how to do things or minor tweaks that work around some bugs, but serious defects in use of not just the proprietary videocard drivers but the free open source xorg drivers as well! Major problems with hardware detection, freezing installations, booting into nothing, etc etc. Many complain that vital hardware that worked fine with a fully updated previous version now is broken whether upgrading or fresh installing 8.04.

Why does this not surprise me? Because the exact same situation exists every single time Ubuntu releases a new version of their distro.

Why does it happen? Because for reasons I cannot fathom Ubuntu, and distros that take Ubuntu as its base as well, choose to start off with the Unstable distribution of Debian as a base and fix and build from that point. Even Debian NEVER does that after accepting a version of testing as a new stable distribution. It copies THAT repo and duplicates it as the new testing. NOT the unstable Sid repo that it will never base ANYTHING upon since it is direct from upstream, untested, buggy software. Yet all these derivatives take a snapshot of Sid, fix as many bugs as they can, add some nice GUI administrative tools, and release it as a stable distribution. It would be IMPOSSIBLE for it to be a fully functioning release using this philosophy. What are these developers thinking?

A proper mass distributed Debian based distro would take a snapshot of TESTING, add the missing pieces from unstable and bug fix their way of getting those parts to fit (Debian does that but is in no hurry as they can wait until all parts get upgraded naturally and the patches are applied in time). Testing at all times remains a mostly stable Linux distribution. Unstable is at RARE times a stable distribution. Most stuff works, sure, as the software is released by upstream and as far as upstream knows it works okay. But all installable, not breaking other things or itself, and patched up to get around found bugs? NEVER. And that's what Ubuntu bases their new distro release on? It's CRAZY![/quote]

---

### Post by sonofusion82 on 2008-11-02
with the fast growing number of users, this leads to a fast growth in the number of variation of user and machine configuration. this is both good and bad. good is that this will probably improve ubuntu or linux as more people test their machines against the software but the bad is the for those unfortunate user, they might feel disappointed due to increased expectation with every release.

anyway, i have just upgrade to 8.10 yesterday and so far so good for me.

---

### Post by tuxxy on 2008-11-02
Ibex is excellent update heres my thoughts, also with a boot up speed test vs Vista 64-bit :)

[http://ubuntuforums.org/showthread.php?t=962542](http://ubuntuforums.org/showthread.php?t=962542)

---

### Post by N00bB00b on 2008-11-02
Well, here's my perspective:  I did the update, rebooted, and now I can't get X, and therefore Gnome to start.  So, I wouldn't know if this update is any good or not BECAUSE I CAN'T EVEN BEGIN TO USE IT.

---

### Post by jerrylamos on 2008-11-02
I'm a glutton for punishment so I slog thru the early Alpha, Beta, Release Candidate, etc. on Feisty, Gutsy, Hardy, now Intrepid.

My impression is Intrepid gets more users where it just plain doesn't work.  I've no statistics.

Seems to be two main causes from my overview:
1. ! Any number of people like me ran 8.04 with compiz O.K.  On 8.10 it locks the computer up tight on boot.  Took me weeks to figure that one out.  The official "fix" is to "blacklist" a number of intel drivers (maybe others?) and not run compiz hence "desk top eye candy effects".  These work fine on 8.04 compiz, but 8.10 compiz chooses to freeze the computer instantly making it hard to find the cause.

Removing compiz, 8.10 runs fine and with latest flashplayer does a credible job on BBC and You Tube videos on this 1 gHz IBM Thinkpad with 512 mb.

2.  Another bunch of people have problems with "X".  My 3 computers don't so I can't comment.  

I do wonder if the Debian folks are using the same level of compiz & X, and what their experience is.

Jerry

---

### Post by 00b00nt00 on 2008-11-02
Just my 10 cents worth:

There seems to be a perceptible speed increase between 8.04 and 8.10. Intrepid shaved 25 seconds off the boot time of my laptop (800Mhz P3), which now boots in ~56 seconds. Also, screen re-draws are faster, and flash video plays faster, too.

---

### Post by edoviak on 2008-11-03
[quote="sonofusion82"]with the fast growing number of users, this leads to a fast growth in the number of variation of user and machine configuration.[/quote]
True. Ubuntu will get more complaints because it is more widely used (both in people terms and configuration terms).

[quote="jerrylamos"]My impression is Intrepid gets more users where it just plain doesn't work. I've no statistics.[/quote]
But that raises my original question: Why do users run into so many upgrade troubles?

[quote="jerrylamos"]I do wonder if the Debian folks are using the same level of compiz & X, and what their experience is.[/quote]
I use Debian, but I can't answer your question because I don't like Compiz at all. Sorry!

Too much eye candy distracts me from my work.

---

