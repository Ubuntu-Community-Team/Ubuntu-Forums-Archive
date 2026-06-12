---
title: "Display resolution frustration solved by Fedora, why not Ubuntu?"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by quercusmax on 2010-08-30
I have bad news for Ubuntu fans.  Here's my story:

Fed up with the Windows world, earlier this year I decided to set up  Linux on one of my spare machines and try to make it work for me.   Ubuntu seemed to be the distro with the most buzz, so I tried it, and tried hard to make it work, but now have given up.

The installation was much smoother and nicer than what I remember from  Red Hat some years ago, and all was well -- until the display came up in  800x600 resolution (on my 1280x1024 LCD monitor) and no better resolutions were offered through the Monitors GUI.  I worked on this for  hours, Googled everything, tried Xrandr, tried editing xorg.conf in all  of its arcana and folklore, trying to determine monitor timings and junk  like that, and eventually somehow coaxed my monitor to display in 1280x1024, but with stuff clipped  off on both sides that no amount of fiddling with various settings would fix.

I asked many people including some very knowledgeable and helpful people who seemed to speak for/from Ubuntu  and Canonical, and was told that probably the problem was that my  monitor was reporting some wrong EDID (?) values.  Maybe so, but Windows  handles this with aplomb.  I did eventually try installing Ubuntu using  a different monitor and that helped, but I was worn out trying to solve what should be a non-problem.

Why not just accept 800x600?  Because quite a few GUI items in Ubuntu don't even work properly at that low resolution - for example, the Monitor GUI itself!

This is the kind of thing that will prevent Linux from ever making even a small dent in the Windows market share.

But here is the new news: Last week I tried installing Fedora 13.  It allowed my  monitor to come up with a higher res mode, but still not what I wanted.   BUT -- Fedora provides a utility called SYSTEM-CONFIG-DISPLAY that  allows you to set what ever resolution you want - *just like Windows!*

Message to Canonical:  Just because something works on one machine doesn't make it good enough.  This display resolution thing has been a MAJOR frustration to a lot of people - just Google "Ubuntu display resolution" for lots of frustration and little success.  There are solutions to this:  Windows has one, Mac does, and even Fedora.  But not Ubuntu.

In response to my pleas for help on this in other forums, one person said "what do you expect for free?"    Very helpful.

Subsequently I found that Fedora also does a better job of handling some of my other Ubuntu frustrations, so I'm on Fedora now for keeps because it works.

Sorry Ubuntu and Canonical.  I really wanted to like you, but you just made it too hard for me, and probably many others.

---

### Post by wojox on 2010-08-30
Yeah, I dual boot Fedora and Ubuntu. Both great distro's. 

What graphics card/chip do you have?

---

### Post by Mark Phelps on 2010-08-31
Not that it's any consolation, but I share your frustration with resolution woes in Ubuntu.  

I used to have an old HP laptop, and nothing I would do in Ubuntu would get the display over 800x600.

In stark contrast, OpenSUSE, Fedora, and PC LinuxOS ALL set the display to 1024x768 by default.

Also, there used to be an Ubuntu utility that would work much like the display utility you mentioned.  It's been a while, but I think it was named something like gtkdisplay-config.  It opened a panel where you could select from various resolution settings.  

Canonical got rid of that a while back.

---

### Post by quercusmax on 2010-08-31
> **wojox said:**
> Yeah, I dual boot Fedora and Ubuntu. Both great distro's. 

What graphics card/chip do you have?
I don't think the graphics card and chip are at issue here - I believe the problem is the monitor I generally use.  I tried installing Ubuntu 9.10 and 10.04 on *3* widely different machines with the same 800x600 result.  About the only useful help I got was from someone who pointed out that my monitor was probably not reporting its capabilities correctly (EDID value or something like that).

Sure enough, when I tried installing on one of those computers but with a different monitor, it gave me higher resolution, thus confirming it is how Ubuntu is handling the value reported by the monitor.

While some might want to stand on purity, that's not the real world.  This same expensive LCD monitor has given no problem to Windows (several versions) and now Fedora, so this is an eminently solvable problem.

My point is not to knock Ubuntu which seems generally nice in most other ways, but instead to point out a fundamental deficiency that Ubuntu should address if the product is to have broader appeal.  Diehard Linux hobbyists might not mind hacking xorg.conf to get these settings right (after spending lots of time just figuring out which settings to make), but for most other people just expect their monitor to work at best resolution automatically so they can use Ubuntu to do other things that are fun or interesting.

My suggestion to Ubuntu/Canonical:  Do Fedora one better by incorporating Fedora's SYSTEM-CONFIG-DISPLAY functionality into the Monitors GUI program.

---

