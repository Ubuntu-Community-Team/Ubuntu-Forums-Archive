---
title: "How Do I Know If I have Ubuntu 14.04.1?  (Quick Question)"
date: 2014-07-31
forum: Installation &amp; Upgrades
---

### Post by hoodbrothers2 on 2014-07-31
Hey this is a pretty noob question, but I was wandering...  I have ubuntu 14.04 LTS with the software up to date. However, when I type 

sudo update-manager -d

in the terminal it says that 14.10 is available.  I want the latest LTS that is not a beta or alpha, which I thought was 14.04.1.  So, my questions are, do I have 14.04.1 right now?  If not how do I get it?  And what is 14.10; LTS, alpha, or what?

---

### Post by Bashing-om on 2014-07-31
hoodbrothers2; Hi !

If you are fully updated, you have 14.04.1 .
To check:
terminal command:
```

lsb_release -a

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Rob Sayer on 2014-07-31
I think many newer linux users coming from windows may think that 14.04 and 14.04.1 are like windows 8 and 8.1.  They aren't really.  As far as I've been able to ascertain it those .1 etc numbers are just there to reduce the number of updates you have to do when you're installing or after install.  The OS hasn't changed.

Though some users will wait for the x.1 release because they've had more time to do the inevitable bug fixes.  I think that's a very good idea.  Though I didn't do that when I installed xubuntu 14.04 on my netbook.  I would have waited for 14.04.1 except the wireless adapter has had some support issues (fixed now AFAIK).  In 13.10 I had to recompile the backported wireless driver every time the kernel updated, which was getting annoying.  But otherwise I'd recommend waiting.

You're quite right to not want to update to an alpha or beta release.  Those are for highly knowledgeable users who have good terminal recovery skills.  An alpha/beta may work fine when installed but I'd consider it almost certain that at some point an update will break it.

When I install ubuntu I go into the software sources settings in the update manager and turn off the check for new release option.  I don't really see the point of it for myself.

---

### Post by grahammechanical on 2014-07-31
I recommend that you use Update Manager to update your system. The next version of Ubuntu will be called 14.10. It is due to be released towards the end of October this year but we can install the development version from an ISO image or upgrade to it from 14.04. This allows for testing prior to release.

During the first two years of a Long Term Support (LTS) release of Ubuntu it will get 4 or 5 of what are called point releases. These are not seen as new releases by Update Manager. That is why that command did not report 14.04.1 as being available. 

These point releases not only bring in all the updates since 14.04 was released but also bring the work done by the Linux developers to make Linux compatible with the latest hardware. So, in 2 years time potential new users will be downloading 14.04.4 which will be as up to date with newer hardware on the market as the Linux developers can make Linuxe.

We get these point releases through the normal method of updating. If you have run Update Manager recently then you will be on Ubuntu 14.04.1.

Look at the charts at the bottom of this Ubuntu wiki page.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by hoodbrothers2 on 2014-07-31
Thank you everyone for your detailed answers!  They all helped a lot.  Bashing-om, I tried the command and it did confirm that I had 14.04.1, so thank you!  Grahammechanical, Rob Sayer, thanks for clarifying the other parts!  Rob, you mentioned that there were some wireless issues, which was exactly why I wanted to be sure I was upgraded.  It would help me a lot if anyone could check out my other thread, because I have a wireless card that worked well in 12.04, and stopped working good in 14.04.  I thought the update would help me but it seems to have not. :(. Anyways thanks for helping me!

---

