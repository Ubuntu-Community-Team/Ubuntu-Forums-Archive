---
title: "Screen refresh rate issues can be a show stopper"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by macxek on 2006-09-25
Hi everyone,

I installed Dapper on my gf's computer this weekend and I encountered the same issues I had when I installed Breezy on my computer a couple of months ago.

Basically, I see 3 things that must absolutely NOT go wrong when installing a new OS, otherwise most people will be stuck and give up:

1) Keyboard+mouse setup
2) Screen resolution + refresh rate
3) Network/internet connection setup

The keyboard and mouse were configured correctly this time, which I see as an improvement compared to Breezy. 

Another improvement (compared to Breezy) is the DSL internet connection which was easy, put aside the fact that I had gained some experience from my previous Ubuntu installation. For a complete newbie it could have been a show stopper: using commandline pppeoconfig is tougher to find than a graphical tool that appears in the Gnome menu...

However, the screen resolution and refresh rate is truely something that has driven me nuts. I consider that once the screen has a reasonable resolution and refresh rate (i.e. > 75Hz) you can take your time to fix other issues. However, when working at 60hz, you can't expect someone to work on fixing configuration issues very long as you get tired and irritated. Also, editing xorg.conf, even with all the instructions possible, is not an option for most people...

Is there any plans to improve this aspect? I would see a Windows-like Advanced checkbox on the resolution panel which would give you all possible combinations of resolution/color settings/refresh rates from which you can choose what you *know* is an acceptable setting and go away with it.

Any thoughts?

---

### Post by wpshooter on 2006-09-25
My thoughts are that I am with you, in that, I hope all of this stuff eventually gets fixed by having GUI tools for these type of settings **BUT** I would not hold my breath waiting for it to happen.  

You will find that most people on these forums are pretty much in love with issuing command line syntax and manually editing every configuration file they can get their hands on.

My thought is that it is going to take the developers of this O/S perhaps 2 to 3 years to getting around to doing this type of thing.  I think they have other things which **they** consider more important at this time.  But to me they are probably losing a lot of first time users by putting this type of thing off and these potential users **MAY**never be recovered since they will remember this as their experience with Ubuntu/Linux.  And even when these things get fixed, they will be doubious about trying Linux again in the future.

---

### Post by hajk on 2006-09-25
Don't hold your breath about these issues, since they're not at all clear-cut. I have a nice screen myself (see sig) for which the Dapper installer activates the 1280x1024 mode at 75Hz - yet there is an insistent tremor in some parts of the screen (very tiresome, indeed).

Samsung's manual says that 60Hz is the best refresh rate, but that's not a choice in the System - Preferences - Screen Resolution menu... But it can be forced by editing /etc/X11/xorg.conf and changing the 1280x1024 spec to 1280x1024_60 in Section "Screen" (need only do that for "Display" Depth 24), and after restarting X the 60Hz choice is active, and the tremor gone.

In your case, find the best or recommended rate, then add it in similar fashion to /etc/X11/xorg.conf, and you're all set.

Final thought: you might benefit from reading through some of the stickies in the Beginner's forum to get a better handle on what people (incl. you and gf) may realistically expect from Ubuntu (or any Linux distro). Some tweaking and self-help along the above lines will always be required, a lot of it is only a search of the forums away.

---

