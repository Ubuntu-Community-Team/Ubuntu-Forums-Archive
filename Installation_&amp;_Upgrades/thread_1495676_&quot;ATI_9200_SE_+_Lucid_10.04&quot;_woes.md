---
title: "&quot;ATI 9200 SE + Lucid 10.04&quot; woes"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by tada on 2010-05-28
Hi

I've been meaning to get back into linux for a couple of years now.
It seems I may have left it too long for my hardware.
I'm struggling to freshly install lucid 10.04 onto a pc with an ATI 9200 graphics card.
Can someone give a definitive answer on this - the internet is full of different solutions and I cannot get any to work.

Thanks

---

### Post by ajgreeny on 2010-05-28
Oh dear, oh dear!  I offer you my commiserations, and feel you may have a bit of a problem with this.

However, it can be done even though the outcome is not as good as most previous versions of ubuntu.

1.  Up to 9.04 all worked with no problems at all as far as I could see using the open source ati/radeon driver.

2.  9.10 had a problem running compiz at resolutions above 1024x768, and would give a black desktop background, though the panels would show, and program windows were also visible unless you maximised them.  Running at 16 bit colour fixed that, and all was well again.

3.  10.04 is much more of a problem because of KMS being enabled in the kernel, and this graphics card not being able to deal with that, and **plymouth** boot system, causing big problems.  Somehow or other I have managed to get the OS running, but I do have difficulties with a standard desktop live CD not booting.  I did get the UNR version of 10.04 to run as live CD and install with no problem, and then added the **ubuntu-desktop** package to that.  In effect I now have a standard ubuntu 10.04 system running without too many problems, but I still need to run it at 16 bit colour for speedier refresh rates, which I do with a manual edit of /etc/X11/xorg.conf.  It is still nowhere as good or fast a display as 9.04 or 9.10, but I am assuming that eventually an update of the ati/radeon driver will appear and overcome the mess it is at the moment.

Incidentally I have also tried Mint9 as a live CD along with all the supposed workarounds using **nomodeset** or **radeon.modeset=0** boot parameters, but still can not get that running at all; a complete no go for me.  Similarly the multiboot DVD with ubuntu, kubuntu and xubuntu, that came with Linux Format Magazine here in the UK this month will not boot to a desktop either.  I agree with you that this whole business is most disappointing, but that is perhaps the price we pay for old hardware, and using a new, free, OS.

Perhaps it's worth trying my trick with the UNR live CD to see if that works for you as well.

---

### Post by tada on 2010-05-28
Wow - the brick wrapped in velvet eh ? :)

I have to say this was a last ditch hopeful post that someone would point out something utterly trivial and it would just work - but I fear we're doomed :(

My second step will be to buy a new-to-me pci graphics card and try that.

Thanks for the support

---

### Post by ajgreeny on 2010-05-29
Yes, sorry about that sad story.

However, as I said I am now running 10.04 without too many problems on my machine, sempron 2400+, ati 9200SE, 2GB ram, and even though the refresh rates are not as good as they were (glxgears down from about 1900 fps to 750 fps) it is still very usable, and I now forget about the frame rates and just get on with things.  The plymouth splash screen will not show properly either, just appearing for a second and then changing to a low resolution mess for a second just before the login screen, but I'm not too worried about that.

What is more annoying is tha inability I have to use 10.04 on my old Acer Travelmate laptop with an ati 9000m card.  The machine gets extremely hot with 10.04, but runs beautifully with jaunty and karmic, so I've stuck with karmic for that, and hope that 10.10 will have a better implementation of the system for these old cards.

Try my UNR trick if you can, I have no real idea why it works so well, but it seems to do so.

---

### Post by nyarfal on 2010-05-30
I've been using Ubuntu for a long time on this machine, with an rv280 card. It was a little disappointing to see the snappy effects degrade as I upgraded from 9.04 to 9.10 to 10.04.

I tried some of the fixes, but none of them really seemed to help, and the ati-radeon driver performs well enough without it being a huge issue. I wonder why I didn't find this thread earlier. It would've saved me a lot of time!

That said, I don't know if I'm the only person who gets problems like in the screenshot...

---

### Post by ajgreeny on 2010-05-30
> **nyarfal said:**
> I've been using Ubuntu for a long time on this machine, with an rv280 card. It was a little disappointing to see the snappy effects degrade as I upgraded from 9.04 to 9.10 to 10.04.

I tried some of the fixes, but none of them really seemed to help, and the ati-radeon driver performs well enough without it being a huge issue. I wonder why I didn't find this thread earlier. It would've saved me a lot of time!

That said, I don't know if I'm the only person who gets problems like in the screenshot...
Yes, very occasionally I also get that problem display effect, but it does not stay and quickly disappears, so is not a problem.  I think it is a result of using compiz which I like to use when I can, but disabling compiz does not appear to make my display any snappier.

---

### Post by nyarfal on 2010-05-30
I could've sworn I had more than two posts' worth of issues. Hmm.

I think the biggest issue is on boot up and shut down, when it tends to give a screenful of that glitchy stuff for a second, and in Firefox, when some graphically taxing pages fail entirely to render and just dump black and purple mess onto my screen.

I've even considered down-grading to 9.04 and just staying there... has anyone else considered that?

---

### Post by bildr on 2010-05-30
I would rather be using an ATI card for liking their business practices, but nvidia binary drivers just work better for me.

---

### Post by ajgreeny on 2010-05-31
> **nyarfal said:**
> I could've sworn I had more than two posts' worth of issues. Hmm.

I think the biggest issue is on boot up and shut down, when it tends to give a screenful of that glitchy stuff for a second, and in Firefox, when some graphically taxing pages fail entirely to render and just dump black and purple mess onto my screen.

I've even considered down-grading to 9.04 and just staying there... has anyone else considered that?
Yes, I did think about that, but apart from the graphics problem with 10.04, which I presume will improve even further than it has so far, and it has got a lot better than at the start, everything else is much better than previous Ubuntu versions, and also 9.04 will lose all support very soon (October).

---

### Post by blackest_knight on 2010-09-25
Hi was just having similar issues, i finally got things working quite nicely and using kms 

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

its a little extreme and who knows a new build might break it again. 

however it all works now and desktop effects can be enabled without getting a black desktop.

my cards a 9200se

---

### Post by tada on 2010-11-04
My original mobo died.  When I replaced it with a new one with an integrated graphics card my problems went away :)

---

### Post by pbpersson on 2010-12-05
I wanted Compiz to work on my test 64-bit Lucid machine with an ATI Radeon 9600XT but based upon what I am seeing there is no easy solution.

I have seen about five different sites with all sorts of confusing instructions.  Here is a nice one:
[B]
In order to use the fglrx internal AGP support, you have to make
sure that the kernel agpgart support is not active (i.e. it is not compiled
into the kernel and the kernel modules are not loaded). If the fglrx kernel
module detects that the kernel agpgart support is active, it will automati-
cally use that even if its internal AGP support is requested in order to
avoid conflicts that can cause problems under some circumstances.[/B]

Now....how in the world would I know what is down inside the kernel?  :o

I am just going to run this test machine without desktop effects and hope that when I migrate to production with NVidia it will all work.

However, this is the very reason why I cannot recommend Ubuntu to my friends.  Most people would not accept "you cannot use eye candy" as a reasonable answer.  I know, it is not the fault of Linux but it is what it is.  I just don't have a day to spend fooling with trying to get this to work.

Maybe I should look into getting a new NVidia card for this machine - nope, this mobo needs an AGP card and the world is on PCI express now - no help there.  :(

---

