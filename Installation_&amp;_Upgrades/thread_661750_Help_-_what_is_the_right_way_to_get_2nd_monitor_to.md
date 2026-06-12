---
title: "Help - what is the *right* way to get 2nd monitor to work?"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by tjwolf on 2008-01-08
Let me preface this with the fact that although I'm pretty familiar with Unix, I don't have much knowledge in the areas of Linux/Ubuntu.

Until a couple days ago, I was happily running Fedora 5 on my Dell Latitude D810 and somehow managed to set it up to support a second screen (a Dell 2007FP connected through the docking station). The notebook's resolution is 1680x1050 and the external monitor's is 1600x1200 and I had it setup so that the built-in was the "default" and the 2007FP was to the left to form a desktop that included both. It worked beautifully.  I guess I got it working by following some how-to that told me to modify the xorg-config file.

So I decided to be wooed by this shiny new Ubuntu 7.10 distribution (I was hooked when the Live CD was able to detect my wireless along with a few other ones - out of the box!   A first for Linux as far as I'm concerned).

Not being versed in the ways of Linux, I forgot that I should be saving my xorg-config file - since I assumed that the built-in **System->Administration->Screens and Graphics** could, by now, surely handle what used to have to be done by hand-coding config files.

So, after flawlessly installing Ubuntu 7.10 and switching to the Restricted ATI driver via the GUI admin tools, I proceeded to try to set up my second monitor using the aforementioned GUI tool.  Seemed very straight-forward.  Screen 1 was already defined and the graphics card was already set to have driver fglrx, so I selected Screen 2 and set it to "Dell 2007FP Analog", set the resolution to 1600x1200, and checked "Secondary Screen" + extend default screen to "Left"...then I hit OK.  The system told me that I needed to restart for the setting to take effect - so I did.

But when I got back into X, both monitors were stuck at 800x600 and I saw no way of reverting things back!

So, could someone point me in the right direction?  Is Linux still in a state where this sort of thing needs to be done with manual config file changes?  The "Screens an Graphics" tool seems the right way to go, but appears to not be up to the task.  If I have to do things manually, what route should I take - I get confused with all the talk of "BigDesktop", "TwinView", etc.  As I said, I have a Dell D810 laptop and the graphics card in it is an ATI Radion X300, I believe.

Many thanks for all info.
tom

P.S. I posted a similar question in the Dell support forum, but didn't get any reply so far.  Since it's actually an installation related issue and is probably not specific to Dell, I figured I'd ask the question here as well.

---

### Post by tgalati4 on 2008-01-08
You are going to hate this suggestion.  Reload Fedora Core 5.  Set up your dual display as you did previously.  Make a copy of your precious xorg.conf file and load it on a USB stick.  Lock it away for safe keeping.  Take out insurance for it.

Reload Gutsy.  Copy your precious xorg.conf to your new distro.

If that doesn't work, then copy sensible portions of it to Gutsy's xorg.conf.  The X Server is a moving target and has been around since the early eighties.  That makes it ~25 years old!  There are many flavors of it and lots of code floating around.  There have been lots of changes from Fedora 5's xserver and what's in Gutsy.

I had to do the same thing to get higher resolution and scan rates for an old Dell using SUSE 10 xorg.conf and moving it over to Gutsy.

---

### Post by tjwolf on 2008-01-08
Thanks for the suggestion.  Unfortunately, this won't help me as I don't remember what I did 2 years ago to get it to work under Fedora 5.  Back then, the GUI tool also didn't work and I followed someone's how-to that manually had me making modifications to the xorg-config file.  I no longer have the link to the how-to I used :(

I don't mind modifying the xorg-config file again, but I just don't know what how-to to follow.  There are postings on getting "Big Desktop" to work and others on how to get "TwinView" to work...and probably a boatload of others.  I'm kinda clueless - I don't know the right terms, I guess.  Thus my posting.

I have an external monitor with resolution 1600x1200 to which I want to extend the desktop when my laptop (resolution 1680x1050) is connected to it.  Can anyone point me to instructions on how to do this?  A URL would be good.

---

