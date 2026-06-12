---
title: "Upgrade from 9.10 to 10.04 results in video,mouse issue"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by sethtriggs on 2011-01-26
Hello,

I had an ill-advised upgrade from Ubuntu 9.10 to 10.04 (due to needing to beta-test a particular program). My gut told me that I shouldn't do it, but I went ahead and did it anyway.

The problem that makes this worse is that I have an ATI Radeon HD 3650, and ATI hates Linux. So upon booting into 10.04 I ended up with no screen. It took a lot of futzing around in the terminal to get things going (including making an xorg.conf file). Installing the ATI proprietary drivers (Catalyst) was an epic failure. Trying to make "radeon" the driver? Epic failure, resulted in a completely unbootable system.

To at least get the system to boot, I deleted xorg.conf (since 10.04 allegedly will discover devices automatically without it) and played around with options in GRUB. Please see my attached menu.lst; that should be my only configuration.

The other issue at this point is that my only working driver (that I can find anyway) is vesa. Unfortunately, when using Vesa, my mouse wants to scroll everything down and to the right. This means that if I open any window that has a scrollbar, it will move such so that the scrollbars are to the other end. This makes it all but impossible to make things work.

To make matters worse, now my WINE (specifically, Irfanview) cannot view GIFs. But at least I have a workaround (FTP) to get things to where I can work on them.)

If anyone can suggest some fixes that don't involve trying to go through the pain of unbootable systems with ATI (I've followed every last suggestion in this forum, I feel, with no joy)...I would be most appreciative. At this point I'd be satisfied if I could just get the mouse to stop messing up. I accidentally made it work at one point but I can't retrace the switches I set to make it so.

I've tried setting a basic xorg.conf, an ATI-generated xorg.conf, and now *no* xorg.conf.

-Seth

---

### Post by irv on 2011-01-26
I have had nightmares in the past so from now on I do it this way. See link.
[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11")

I know this is after the fact, but it might be a way to fix things. It worked for me.

---

### Post by sethtriggs on 2011-01-26
> **irv said:**
> I have had nightmares in the past so from now on I do it this way. See link.
[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11")

I know this is after the fact, but it might be a way to fix things. It worked for me.

Very interesting. Maybe I can do this as a reinstall you think?

What's also interesting is that I was able to upgrade all the way to 10.10 on the laptop, and it works optimally. That laptop has an ATI Radeon XPress card of all things.

-Seth

---

### Post by irv on 2011-01-26
You sound a little like me. I have three computer in house running Ubuntu Linux and one at the chapel that I am always playing with. The one at the chapel is a laptop (no-name) I use on the sound system. I need to run 9.04 because I can't get the newer versions of Ubuntu to load on it. For what I am using it for it works great. I do all the sound recording on it. I use an analog digital converter to grab the sound in Audacity. I have one desktop, one laptop and a server at home.

---

### Post by sethtriggs on 2011-01-26
> **irv said:**
> You sound a little like me. I have three computer in house running Ubuntu Linux and one at the chapel that I am always playing with. The one at the chapel is a laptop (no-name) I use on the sound system. I need to run 9.04 because I can't get the newer versions of Ubuntu to load on it. For what I am using it for it works great. I do all the sound recording on it. I use an analog digital converter to grab the sound in Audacity. I have one desktop, one laptop and a server at home.

You would know this certainly; what other drivers, if specified in xorg.conf, would allow an ATI Radeon HD 3650 to at least display without causing me such a mouse issue? Vesa at least gets me with an operating system, and this would be tolerable if I had, well, a working mouse.

-Seth

---

### Post by irv on 2011-01-27
I agree. Some of the hardware out here is just not Linux friendly when it comes to drivers. You would think that the manufactures who want to sell there products would support as many OS's as they can to gain a larger customer base. But there are some who key in on the large user base and forget the rest of us. The best thing to do is to support those who support us.

---

### Post by sethtriggs on 2011-01-27
> **irv said:**
> I agree. Some of the hardware out here is just not Linux friendly when it comes to drivers. You would think that the manufactures who want to sell there products would support as many OS's as they can to gain a larger customer base. But there are some who key in on the large user base and forget the rest of us. The best thing to do is to support those who support us.

Yeah that's a good point there irv.

Argh, don't really have the money right now to buy another AGP video card, and I admit I'm a bit scared as to whether it would fail or something down the road. This is utterly confounding.

Do all of the NVidia cards work? Can anyone out there recommend an AGP card that works with Ubuntu 10.04 and beyond?

In addition, is there *anyone* with a working Ubuntu 10.04 and Radeon HD 3650 card? What are your boot parameters, and do you have an xorg.conf?

Oh, by the way, inspecting my /etc/X11 folder, wow there's a lot of spare copies of xorg.conf! Would that have anything to do with it? Should any of those extras (there is no actual xorg.conf) be deleted?

-Seth

---

### Post by sethtriggs on 2011-01-28
Bump - Anyone out there have a working ATI Radeon HD 3630 or similar card? What is your configuration if you do?

-Seth

---

