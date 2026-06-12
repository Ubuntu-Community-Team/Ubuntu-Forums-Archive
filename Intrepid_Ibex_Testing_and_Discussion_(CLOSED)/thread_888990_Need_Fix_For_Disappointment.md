---
title: "Need Fix For Disappointment"
date: 2008-08-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by newguy1950 on 2008-08-13
This post is part rant, part question, so bear with me...

I've been using Linux for quite a while now (7 years) and during that time tried numerous distros, none of which came close to Ubuntu in the end. Of course, some I did run when Ubuntu hadn't even been founded yet, but in the end it won me over with very well supported packages, sensible choices and everything working right out of the box. "Polished" seems to be a well justified adjective in this case.

I run Linux because it simply runs well (as in stable) and gives me lots of freedom. Not in the political way; I simply like it's easy to do what I want with a few lines of python from the command line, as well as decent hardware support for a *nix system. There are times when things get rough, but it usually always boils down to buying supported hardware (an art which I have down by now, after paying dearly for it) or learning something new, which is a good idea anyway. When my friends ask me why I installed Linux on my Apple Laptop, I tell them it's less complicated for me to use then OS X - and I really mean it.

However, all that changed radically with Hardy Heron. It is a huge disappointment because it has one (or more?) major bugs that pretty much obliterate it's usefulness: It crashes. Hard. Keyboards blink, screens freeze, work gets lost and frustration rears its ugly head.

Now to err is human, but this seems to have been a problem present in alphas, betas, release candidates and has not been fixed. I am talking about [Bug 204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996"), or the common hardy hardlocks (search the forums and you will find at least two threads with over 1,500 replies combined). My new media center PC hardlocks. A friend's PC who upgraded from gutsy hardlocks. My girlfriend's laptop hardlocks. Except for my computer, every x86 machine with a simple Hardy install that I have seen has hardlock issues. These machines range from laptops with wireless to barebones without to simple office computers.

As usual, I tried to fix the problem by researching it, however there has not been a single good answer for this question. It is an open issue. The only fix that seems to work on at least one machine (as I have found out through hours and hours of testing) seems to be to use kernel 2.6.26 from Intrepid. Even that would be fine, one can at least consider it a testament to the flexibility of the distribution.

But it's not.

I have not found one convenient way to install Intrepid Ibex kernels as a hardy backport or similiar. Of course, you could say I am not supposed to - but in this case, it's required to USE the system. There is no alternative yet. The release has been out for more then 3 months. The bugreport is solved with "fixed in Intrepid" - great. But isn't this supposed to be Ubuntu 8.04 LTS, long time support? I have to spend hours to get a system running on which I can reliably copy a few hundred gigs via scp or watch a movie. What do I tell other people that come to me for support?

Rolling a (non-custom!) kernel from Intrepid Ibex is a major, major pain in the ***. Other packages are simple to backport, this one isn't. Yes, _I_ can do it, but it takes time. I can edit the build scripts if I need to, research the necessary things online, read bits of code if need be and knowingly disable ABI checks.

I don't want to, though. I'd rather use my system then chase frequent updates with new kernels because no one is going to investigate that "fixed" bug (I have tried, if anyone wants netconsole logs from kernel crashes, let me know).

This needs to get fixed. At the moment, Hardy is a damn shame when it could be so much fun. I do not say this lightly, I have looked at the whole issue for weeks, without any fix showing up. Either make it easier to install Intrepid kernels (hard to believe that there is not one kernel dev who can spare two hours to set up a build system and a "use at your own risk"-apt repository) or investigate and fix the issue.

I like Ubuntu. Please don't make me regret that.

---

### Post by phidia on 2008-08-13
Well I think this is mostly "rant" although it may be justifible. I'm guessing the mods will move this to the community cafe section-don't know though.

I'm at the help forums a fair amount and I think some of what you said is hard to disagree with-not only that but (2 points of my own) 
1) some people probably just give up, move on after experiencing the crashing-freezing and never say anything.
2) There continue you to be several posts a day about crashing-lock-ups-freezing with Hardy and some of the people creating these posts seem unaware of the big threads you mentioned.

Some people claim that disabling any proprietary drivers helps with these issues-but that's not a great solution. What about using Gutsy in the meantime though? 
Gutsy is not a bad release I use it along with an intrepid install-both are working well.

---

### Post by newguy1950 on 2008-08-13
> **phidia said:**
> 1) some people probably just give up, move on after experiencing the crashing-freezing and never say anything.

That's true. The friend I mentioned just wants to try OpenSuSE now, for example. I told him to wait until I get a chance to roll some kernel packages, so he can at least try them and help me out testing.

> **phidia said:**
> What about using Gutsy in the meantime though? 
Gutsy is not a bad release I use it along with an intrepid install-both are working well.

It's not really an option. For example, the laptop won't work as good with Gutsy, as it did with Hardy (wireless drivers, etc.). Also, Hardy is a long time support release and features phonon, a brand new media framework. When setting up a media PC, if I did it on Gutsy, I'd set it up for a soon-to-be-deprecated environment.

Also, keep in mind that the software in Gutsy is older. Current software in Ubuntu is one of its main sellings points (see Debian on how not to do it). There's no way I'm going back to Firefox 2 or Psi 0.10. Of course, you can backport all that to Gutsy, but then you'll be backporting a lot of software. By the time you get to something major (like a KDE or GNOME), you're bound to give up.

Gutsy may work fine on your server, but even there - if you want a new version of WordPress installed on your blog or wrote a custom web application in Python using some new syntactic sugar, you'll want Hardy packages, at least. In the end, you may end up with hardy running on a Gutsy kernel, if that is possible.

---

### Post by Taxman415a on 2008-08-13
I can't disagree that there were too many unfortunate decisions to go for features over stability in Hardy. But if you note that's some of the reasons you don't want to go back to gutsy.  More importantly though there are two paths to go by now. You can stay mad and your post will stay here and be seen by a few but probably won't change much. Or you can jump in and try to make the next release better. Of course you are under no obligation to help fix anything or contribute anything, but then again neither is anyone else. Features only make it into opensource software like Ubuntu because people decide to contribute them. And the software only gets better because people test it and submit bug reports and those get fixed.

Maybe you can or can't code, but you can make a difference either way. Learn to file good bug reports. Contribute useful testing reports [https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing) or help improve the documentation. There are huge amounts of good information in these forums that don't make it into the Ubuntu wiki where they should go, and if they were there, everyone's experience could be better finding answers. It's as easy as finding good information here and adding it to the appropriate wiki page in the community documentation [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)  I haven't done as much of that as I should either. My only frustration is that they are sticking with something other than Mediawiki for the wiki software. I think the wiki would be much more successful with Mediawiki. Anyway my two cents.

Taxman

---

### Post by newguy1950 on 2008-08-14
> **Taxman415a said:**
> You can stay mad and your post will stay here and be seen by a few but probably won't change much. Or you can jump in and try to make the next release better.


Maybe I didn't make that clear above, I have tried. But in this case, there is nothing to do - there already is a bug report. No one can pinpoint the issue and the few logs about the crash I have the developers can reproduce easily themselves.

What bothers me is that there doesn't seem to anyone who thinks it's worth looking into. The bug is "solved" as "fixed in Intrepid". Just now someone _proposed_ to backport the fix. By the time anyone gets done doing anything about it, Intrepid will be out and it will almost be meaningless.

A good fix for the issue (Intrepid kernel in Hardy, in "no-promises"-packages) will - I'm guessing here - take a "real" dev, with a build environment, experience and knowledge of the godawful debian scripts half a day. He can also create "official" ABI numbers, while I have to hack something onto the kernel or change the name, etc. Take that into account before you critisize me.

I do help out on IRC, occasionally file and report bugs, and volunteer doing end-user support for a whole university (where we get surprisingly few "customers" with linux problems, out of 20,000 people). I do not want to make running an operating system any more a life style then I already have. Implicating I should fix things myself, do more and then quoting from a "How To Get Involved" is not solving the issue and carries some insult at least.

---

### Post by Taxman415a on 2008-08-14
Considering that this is the LTS, if fixes get backported it is probably worth it. And anything you contribute is appreciated, so no it is not an insult at all what I said. It's just very simply repeating what you proabably already know (but lost sight of) that nothing gets fixed in free software without someone choosing to do it.

---

