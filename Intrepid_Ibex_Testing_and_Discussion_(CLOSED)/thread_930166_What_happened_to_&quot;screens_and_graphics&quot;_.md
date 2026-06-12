---
title: "What happened to &quot;screens and graphics&quot; in ibex?"
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SunnyRabbiera on 2008-09-25
I decided to give ibex a test run in a virtual machine and I noticed that the screens and graphics app is completely gone now in the menu's even when I try to edit it.
Was this app completely wiped?
I see that the screen resolutions app in the system menu has new features but it wont let me configure anything.
I know this is a alpha/ beta but is this app going to be scrapped for a super primitive app that cant detect my monitor or graphics card?
I mean even in virtual machine mode I was able to get hardy in its alpha/beta phases running at my top resolution [1024x768] with help of the screens and graphics app but now I can only run at 800x600.
I cannot run my system at 800x600 and I am sure other users wont want to manually edit xorg just to get the screen working the way they need it.
I thought we were going to make things easier not harder...

---

### Post by klange on 2008-09-25
It shouldn't really be necessary, but if it is, you should still have it (I think), if not, install it.
The command is [FONT="monospace"]displayconfig-gtk[/FONT].

---

### Post by SunnyRabbiera on 2008-09-25
> **WindowsSucks said:**
> It shouldn't really be necessary, but if it is, you should still have it (I think), if not, install it.
The command is [FONT="monospace"]displayconfig-gtk[/FONT].

its not on there nor is it in the repositories.
What a stupid move here!
This means that there is no longer an easy way to configure the monitor, as the screen resolution app in this is limited and that means everyone will have to edit xorg manually.
What kind of a genius came up with that idea?
It will make ibex impossible to use for newbies who had issues with hardy to configure things the way the need it.
Why this app was removed I have no idea, but its stupid because if Ibex is released in this sorry state and people come to it without knowledge to configure xorg they will run back to vista in a heartbeat.
I thought Ubuntu was supposed to attract new members not scare them away.

---

### Post by RAOF on 2008-09-25
So.  You are seeing a bug - the 1024x768 resolution is not detected when running under VirtualBox.  I can't quickly find an obviously applicable bug, so I can't tell if your experience is common or what the cause might be.  If you could attach your /var/log/Xorg.0.log file, it might be possible to (a) see what's wrong, or (b) see whether you're hitting a reported bug.

In Intrepid, the best that you could hope for from displayconfig-gtk is that it wouldn't *break* your working system.  Xorg autodetect is pretty much up to the point that specifying anything in xorg.conf will at best do nothing!  Most, if not all, the exceptions here are covered by the Hardware Drivers manager - if you've found a case where xorg.conf needs tweaking, that would probably be an appropriate point to add it.

---

### Post by Starks on 2008-09-25
doesn't the lack of proper xrandr support make displayconfig-gtk rather useless?

---

### Post by shazbut on 2008-09-25
What happens if xorg autodetect does not work when the monitor signal is passed through a kvm switch?  Will there be a way to force the right resolution like I can do now with displayconfig-gtk?

---

### Post by RAOF on 2008-09-25
> **shazbut said:**
> What happens if xorg autodetect does not work when the monitor signal is passed through a kvm switch?  Will there be a way to force the right resolution like I can do now with displayconfig-gtk?

I honestly don't know.  I'm not even sure that a Monitor section in your xorg.conf will be respected if it's not connected on startup, although it probably is.

It would be easy enough to test with an Intrepid live CD, though - either Alpha 6, a daily CD, or wait a couple of days for a Beta CD.

---

### Post by SunnyRabbiera on 2008-09-25
> **RAOF said:**
> I honestly don't know.  I'm not even sure that a Monitor section in your xorg.conf will be respected if it's not connected on startup, although it probably is.

It would be easy enough to test with an Intrepid live CD, though - either Alpha 6, a daily CD, or wait a couple of days for a Beta CD.

the reason why I wanted to test it in a vbox is that I wanted to see how well it preforms without breaking my puter.

---

### Post by Ocxic on 2008-09-25
screens and graphics was dropped due to lack of development, usage, and the amount of bugs that needed to be fixed. I was bummed when i heard that, apparently it was not coming along very well.

---

### Post by RAOF on 2008-09-25
> **SunnyRabbiera said:**
> the reason why I wanted to test it in a vbox is that I wanted to see how well it preforms without breaking my puter.

Absolutely.  That's perfectly fine.  Now you've hit a bug, and we'd need some information from you to work out what's going wrong and how to fix it!

Edit: maybe you missed this?
> **RAOF said:**
> So.  You are seeing a bug - the 1024x768 resolution is not detected when running under VirtualBox.  I can't quickly find an obviously applicable bug, so I can't tell if your experience is common or what the cause might be.  **If you could attach your /var/log/Xorg.0.log file, it might be possible to (a) see what's wrong, or (b) see whether you're hitting a reported bug.**

In Intrepid, the best that you could hope for from displayconfig-gtk is that it wouldn't *break* your working system.  Xorg autodetect is pretty much up to the point that specifying anything in xorg.conf will at best do nothing!  Most, if not all, the exceptions here are covered by the Hardware Drivers manager - if you've found a case where xorg.conf needs tweaking, that would probably be an appropriate point to add it.

---

### Post by SunnyRabbiera on 2008-09-25
> **Ocxic said:**
> screens and graphics was dropped due to lack of development, usage, and the amount of bugs that needed to be fixed. I was bummed when i heard that, apparently it was not coming along very well.

well that sucks, and the default screen resolution app isnt good enough.
I am afraid this means ubuntu's popularity will hit a big snag, without a easy to use graphical interface to edit video drivers and such people will turn away from Ubuntu.
I wonder if its possible to develop something as a alternative while Ibex is still in the beta phases.
I just dont think newcommers will be thrilled with using the terminal and having to manually edit xorg, that sort of brings Ubuntu to the way it was in Breezy almost.
For newcommers I guess most of us will be directing to other distros like Mandriva what have easy to use graphics modfication tools pre installed.
There has to be a new way to modify xorg without having to edit it manually and possibly break the system.

---

### Post by RAOF on 2008-09-25
I would suggest that almost nobody actually *needs* to edit their xorg.conf, either from a text editor or from a graphical configuration tool.  Certainly a fair amount of effort has been expended to ensure that this is the case.

Let's make this a little more clear: *No one **ever** wants to edit their xorg.conf in any way*.  They want their mouse to work, or to use a new driver, or connect their second screen.  Having a tool to edit xorg.conf is a temporary work-around because X was crap and forced people to edit xorg.conf to do these tasks.  X has now improved to the point that it's more worthwhile making everything just work than it is improving the xorg.conf editing experience.

You *may* need to edit xorg.conf, to make your particular case work.  But you may not - you may be seeing a driver bug that fiddling with xorg.conf won't fix.  No one can tell unless you give the relevant information.

---

### Post by SunnyRabbiera on 2008-09-26
> **RAOF said:**
> I would suggest that almost nobody actually *needs* to edit their xorg.conf, either from a text editor or from a graphical configuration tool.  Certainly a fair amount of effort has been expended to ensure that this is the case.

Let's make this a little more clear: *No one **ever** wants to edit their xorg.conf in any way*.  They want their mouse to work, or to use a new driver, or connect their second screen.  Having a tool to edit xorg.conf is a temporary work-around because X was crap and forced people to edit xorg.conf to do these tasks.  X has now improved to the point that it's more worthwhile making everything just work than it is improving the xorg.conf editing experience.

You *may* need to edit xorg.conf, to make your particular case work.  But you may not - you may be seeing a driver bug that fiddling with xorg.conf won't fix.  No one can tell unless you give the relevant information.

yeh but there are still quite many monitors and graphics cards that dont exactly click with ubuntu.
Like my issue back in Gutsy, I had a :evil: of a time getting my monitor to work under it.
The screens and graphics app helped, otherwise I would have been stuck at 800x600 resolution.
The monitor detection and graphics card detection has improved yes but i still feel there need to be a helpful tool for those who are not as fortunate.
There has to be something there other then the default screen resolution app or gedit.

Maybe in the future we should develop something like mandriva's control center, arguably the best configuration tool available for linux.

---

### Post by tretle on 2008-09-28
+1, My LG FLATRON L1715S also has never had its resolution detected properly with Ubuntu slapping me in 800x600.. This is a huge regression, until auto detection works correctly it should not be forced upon people.
Posted many times in the Hardware Testing app that the auto detection wasn't working with my monitor and it was never resolved.
Not being able to choose what graphics driver you use is also a huge regression in terms of testing as I used to switch between nvidia drivers and vesa to test metacity compositing.

---

### Post by RAOF on 2008-09-28
> **tretle said:**
> +1, My LG FLATRON L1715S also has never had its resolution detected properly with Ubuntu slapping me in 800x600.. This is a huge regression, until auto detection works correctly it should not be forced upon people.
Posted many times in the Hardware Testing app that the auto detection wasn't working with my monitor and it was never resolved.
Not being able to choose what graphics driver you use is also a huge regression in terms of testing as I used to switch between nvidia drivers and vesa to test metacity compositing.

Have you filed a bug?  I'm not sure where the Hardware Testing app's data goes, but it certainly doesn't translate to bugs on launchpad.net.  Depending on your monitor's quirks, it should be fairly easy to add a quirk for it to get it to work properly.

---

### Post by ycason on 2008-09-28
I just want to add my take on this situation.

When "Screens and Graphics" was first released I thought it would be great.  I gave it a fair shot, but every time I even opened the program, it would kill my xorg.conf for the next boot and put me into 800x600 mode.  This is why I hid this program on both my computer and my girlfriend's computer.  Never had problems again.  On the other hand is the resolution switcher app.  This has never broken anything and provides a much better interface to dual monitor, resolution issues.

As far as editing xorg.conf, there is no graphical program that I've used that didn't mess it up.  I've been much happier editing by hand than dealing with the quirks resulting from GUI programs.

---

### Post by jlacroix on 2008-09-28
> **RAOF said:**
> In Intrepid, the best that you could hope for from displayconfig-gtk is that it wouldn't *break* your working system.  Xorg autodetect is pretty much up to the point that specifying anything in xorg.conf will at best do nothing!  Most, if not all, the exceptions here are covered by the Hardware Drivers manager - if you've found a case where xorg.conf needs tweaking, that would probably be an appropriate point to add it.

Unfortunately that's not the case on my machine, I have to add a couple things in my set up. First, my monitor is detected at a 75hz refresh rate (which is wrong). Second, SLI isn't enabled automatically in the new Xorg. Third, I have to add the line "PCI:XX:YY:Z" for X to even start. (I reported the third bug already, but it doesn't seem to have a high priority which is sad).

On the flip side, I can see that progress has been made.

Edit: Not installing "Screens and Graphics" by default is a huge mistake. Unless I'm not understanding and the configuration has moved, there has to be a way to change the resolution. For example, say someone's monitor is correctly configured at 1280x1024. That doesn't mean they want 1280x1024, they may want 1024x768. Who knows. That's why the options are important. (I've met several people that have a hard time seeing their default resolution).

---

### Post by nanog on 2008-09-29
With all due respect, RAOF, if I were to file a bug for every display quirk I have noticed I'd have several months of work ahead of me. IMO, its hardware quirks that are the biggest problem not necessarily x. Windows and mac osx both enable manual display settings in addition to plug and play for this very reason. Linux should too.

---

### Post by RAOF on 2008-09-29
> **nanog said:**
> With all due respect, RAOF, if I were to file a bug for every display quirk I have noticed I'd have several months of work ahead of me. IMO, its hardware quirks that are the biggest problem not necessarily x. Windows and mac osx both enable manual display settings in addition to plug and play for this very reason. Linux should too.

It's been a while, but I used windows from 3.11 to XP, and as far as I can recall there is nothing *remotely* similar to editing xorg.conf there.  Sure, you can select your resolution, but you can do that here, too.  You can't, as far as I can remember, select your video driver or mouse driver or whether or not you want to load font handling modules.

I suspect Steve Jobs would grow to gigantic proportions and destroy Tokyo if you *ever* had to do something as crass as *choose a driver* in OS X :).

We probably could do better when the monitor is broken or doesn't support DDC, though.  It's entirely possible to do that sort of manual configuration without touching xorg.conf, but I don't think our graphical tools expose that.

---

### Post by netz on 2008-09-29
> **jlacroix said:**
> Edit: Not installing "Screens and Graphics" by default is a huge mistake. Unless I'm not understanding and the configuration has moved, there has to be a way to change the resolution. For example, say someone's monitor is correctly configured at 1280x1024. That doesn't mean they want 1280x1024, they may want 1024x768. Who knows. That's why the options are important. (I've met several people that have a hard time seeing their default resolution).

Under System --> Preferences there is a program called "Screen Resolution" where I can change resolution on my monitor to 640x480 if I want to.

---

### Post by sdowney717 on 2008-09-29
with xorg autoconfig, it is a great idea.
The monitor reports to xorg what it can do. mode lines resolutions date manufactured, model numbers, etc... all sorts of information.

The driver tells xorg what it can do. 
Xorg sorts all this out and it just works.

Actually you can have an empty xorg.conf
I was having resolution problems on a hardy box. 
I tried the screens and graphics, it wrote all sorts of monitor settings into xorg and still computer gave me only 800 by 600 or even worse, 640 by 400!!

I finally edited out all xorg.cong settings and then I had every resolution the monitor can support.

This is only for the free radeon or nv drivers.
The proprietary drivers still I think have a tiny bit of mostly useless info in xorg.conf, such as 'configured video device, etc... no settings information.

the driver  "fglrx" in xorg.conf then tells xorg to use the proprietary binary driver.

---

### Post by chewearn on 2008-09-29
> **sdowney717 said:**
> with xorg autoconfig, it is a great idea.

In theory, yes.  In practice, we have seen all sorts of breakages.

> The monitor reports to xorg what it can do. mode lines resolutions date manufactured, model numbers, etc... all sorts of information.

First breakage:
Not all monitors (and I mean computer monitors, projectors and flat panel TV) report the correct information.  Some KVM switches probably break the DDC link.

> The driver tells xorg what it can do. 

Second breakage:
Not all drivers did that.  The nvidia binary driver is one.

> Xorg sorts all this out and it just works.

Great!  Except for the two breakages above.

> Actually you can have an empty xorg.conf
I was having resolution problems on a hardy box. 
I tried the screens and graphics, it wrote all sorts of monitor settings into xorg and still computer gave me only 800 by 600 or even worse, 640 by 400!!

I finally edited out all xorg.cong settings and then I had every resolution the monitor can support.

This is only for the free radeon or nv drivers.
The proprietary drivers still I think have a tiny bit of mostly useless info in xorg.conf, such as 'configured video device, etc... no settings information.

the driver  "fglrx" in xorg.conf then tells xorg to use the proprietary binary driver.

It has been made clear the old "screen and graphics" utility doesn't work anymore.  Now, the million dollar question is, what then will replace it?

Xorg autoconfig is not 100% and I will argue that it will never be.  New monitors are made and sold all the time.  You will always have someone selling misbehaving hardware.

---

### Post by PGHammer on 2008-09-29
> **RAOF said:**
> I would suggest that almost nobody actually *needs* to edit their xorg.conf, either from a text editor or from a graphical configuration tool.  Certainly a fair amount of effort has been expended to ensure that this is the case.

Let's make this a little more clear: *No one **ever** wants to edit their xorg.conf in any way*.  They want their mouse to work, or to use a new driver, or connect their second screen.  Having a tool to edit xorg.conf is a temporary work-around because X was crap and forced people to edit xorg.conf to do these tasks.  X has now improved to the point that it's more worthwhile making everything just work than it is improving the xorg.conf editing experience.

You *may* need to edit xorg.conf, to make your particular case work.  But you may not - you may be seeing a driver bug that fiddling with xorg.conf won't fix.  No one can tell unless you give the relevant information.

The problem isn't necessarily folks with older graphics cards (which are pretty well supported), but folks with older monitors (particularly CRTs) with bad/incomplete/missing EDID information (which tends to be the case more often with Linux than Windows).  These are the ones that often need to make changes to xorg.conf (I happen to fall into that category).

---

### Post by jlacroix on 2008-09-29
> **netz said:**
> Under System --> Preferences there is a program called "Screen Resolution" where I can change resolution on my monitor to 640x480 if I want to.

I'm a Kubuntu user. I don't see where this option is.

---

### Post by nanog on 2008-09-29
Raof,
> We probably could do better when the monitor is broken or doesn't support DDC, though. It's entirely possible to do that sort of manual configuration without touching xorg.conf, but I don't think our graphical tools expose that.

Is this something that needs to be blueprinted? I'd be will to help draw  up a draft, if so.

---

### Post by RAOF on 2008-09-29
> **nanog said:**
> Raof,


Is this something that needs to be blueprinted? I'd be will to help draw  up a draft, if so.

Nah.  It'd actually be pretty trivial to do - you can call out to **cvt** to generate the modeline, and pipe that into xrandr.

Actually, some good UI mockups might be worthwile.

Of course, this will only work for drivers that support XRandR 1.2.  That's currently all of the open-source drivers, and possibly fglrx.  The nvidia blob *doesn't*, though.

---

