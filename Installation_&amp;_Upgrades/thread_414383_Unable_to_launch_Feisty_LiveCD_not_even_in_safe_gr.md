---
title: "Unable to launch Feisty LiveCD not even in safe graphics mode!"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by lex_luthor on 2007-04-19
Hi all,

I just tried launching the Ubuntu 7.04 LiveCD on my Dell 6400 laptop witout much success.  A Subsequent attempt to launch in safe graphics mode returned the following error on the console:

```

X Window System Version 7.2.0
Release Date: 22 January 2007               .2
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting
        (++) from command line, (!!) notice, (II) informational
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time Fri Apr 20 09:29:00 2007
(==) using config file "/etc/X11/xorg.conf"

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X(main+0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d23ebc]
5: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

```

The laptop contains an ATI Mobility Radeon video adapter (x1400) and UXGA+ widescreen (1440x900).
Does anyone know what's going on???

---

### Post by bwhite82 on 2007-04-19
Yes, this is a well known bug with Feisty and your laptop. Unfortunately they did not have enough time to fix the issue before release. Although, you may get it to boot with a "boot option", but you'll have to dig around for it. Innocent plug: Might I suggest Debian Etch? I have the same computer as you (E1505/6400) and debian installed without a hitch.

---

### Post by Askrates on 2007-04-19
I have the same problem as you. Unfortunately it seems like Feisty is broken for users with ATI Raedeon x1400 or x1300 cards.

However, you might be able to sole your problems by reading this:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Good luck!

---

### Post by odelay on 2007-04-19
This is depressing.  Mostly because this affects a ridiculously large number of people (what, like every dell laptop sold in the last 2 years?) and they aren't going to get the "it just works" Ubuntu experience promised.  

I don't want this to turn into a "they should have postponed it until they fixed it" debate.  Every single release, someone get's screwed, and that someone always feels betrayed that they would actually release an update knowing it wouldn't work properly on their computer.  I'd be lying if I said I didn't feel a little bit of that right now, but I understand the even more massive backlash that would ensue of they missed a deadline.  Sorry for the rant...

My actual question is this: is there any chance of Ubuntu releasing a patched "7.04.1"??  As far as I know, they've never done this because of the confusion it could cause...but I'm not sure.  But then, as far as I know this many people haven't been unable to install an Ubuntu Release.  Of course, some of the xorg problems with Edgy probably affected more people...but at least you could install it without any problems.

Thanks.

---

### Post by thayerw on 2007-04-20
Well, I agree that it shouldn't turn into another debate, but darn it I think it's a big deal. The early herds didn't boot for me, but when the Beta worked I thought for sure the kinks were worked out... guess I was wrong.

I too have a Dell Inspiron 6400 with the ATI X1400 graphics.  I just spent the last 2 hours trying everything to get a working desktop with the Live CD.  I understand that no release is perfect, but I do think Dell notebooks make up a large portion of users and I guess what really irks me is that, unless I'm mistaken, the Release Candidate was skipped in order to make the launch date. We went straight from Beta to Final and according to the Fiesty Roadmap there should have been an RC release  on the 12th ([https://wiki.ubuntu.com/FeistyReleaseSchedule)](https://wiki.ubuntu.com/FeistyReleaseSchedule)).

I think the RC would've caught this show-stopping bug in time to get a fix for the final.  Maybe I'm reading the Release Schedule wrong, and if that's the case, so be it, but it really sucks to have been troubleshooting the development releases, Herd 3 through Final, only to end up with an unbootable Live CD.  I guess I'll add them to my stack of unbootable OpenSUSE Live DVD's...

All in all, I'm ever more impressed with Ubuntu, but... *arrrrgh!*

---

### Post by Askrates on 2007-04-20
I agree this should have been caught before release. It is not just Dell machines that are affected though, my Gateway is down for the count as well.

However, the good news is that according to the bug report, the developers are working hard on a release. 
As one of them says, "Please, no need to confirm this anymore, we know it's broken and are
trying to find the cure."

In the mean time, what we can do is go to [https://bugs.launchpad.net/bugs/89853](https://bugs.launchpad.net/bugs/89853) and help out.

Cheers.

---

