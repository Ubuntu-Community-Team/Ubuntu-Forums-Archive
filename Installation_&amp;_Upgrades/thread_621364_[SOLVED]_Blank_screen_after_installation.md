---
title: "[SOLVED] Blank screen after installation"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by kafpauzo on 2007-11-23
Forgive an almost total newbie! After installing 7.10, all I get is a blank screen.

First question: Are there some log files somewhere that I could check, to find out what the problem really is, rather than guessing and experimenting?

Second question: One possible culprit might be the following, as explained in the 7.10 release notes (but I have some doubts that this is the problem):

[INDENT]Blank screen with some ATI hardware
   *  People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716
[/INDENT]
The search tool finds two files with this name: /etc/X11/xorg.conf and /usr/share/xresprobe/xorg.conf. Which one is it? From the comments in the files I would guess it's /etc/X11/xorg.conf. Is that right?

Which section is the "driver section" where I'm supposed to enter this text? I can see three sections that seem like they might be related to this problem in one way or another:

[INDENT]Section "Device"
[INDENT]	Identifier	"ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
[/INDENT]EndSection

Section "Monitor"
[INDENT]	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
[/INDENT]EndSection

Section "Screen"
[INDENT]	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
[/INDENT]EndSection
[/INDENT]
Is it one of these sections or one of the others?

Do I just put the string on any random line within the section, or does it have to be appended at the beginning or the end of the section?

While searching for information about this problem, I found that some people tested by removing xorg.conf. If I rename the file so the system can't find it, is this likely to give me a usable system? Would this allow me to put this problem aside for a while, while trying to solve some other problems I have with this installation?

I think this is only one among several different problems that I have to cope with, so it would be great to know a solution for putting this particular problem aside, to work on the others, and then if necessary go back to this problem and solve it the correct way. I have made a large number of attempts to install Ubuntu, with or without changes to the above file, getting a blank screen in all attempts except one, and that one died on the first reboot. Oddly enough, the one attempt that worked briefly did not have any change in xorg.conf.

Curiously, the 7.10 Live CD works fine on my computer (but only with Gnome -- if I press ctrl-alt-F1 I get a blank screen with weird patterns). However, after installation, the newly installed system gives me a completely blank screen (no weird patterns, and no reaction at all to ctrl-alt-F1). I don't know if the system goes on working with that blank screen or just stops completely and dies, because my hard disks have no access light, and they are very quiet. It would be nice if there's a log file that can tell me if it boots or just dies.

---

### Post by foytix on 2007-11-23
i'm having the exact same problem, loaded fine for the most part at work and my home desktop, but the ati graphics are giving me a fit on my vaio laptop.  i've looked alot of places and can't find a decent guide for this problem.  Live CD worked fine but once installed just a black screen, sorry but i think i'm even more of a noob.

---

### Post by HydroModeler on 2007-11-23
I am having the exact same problem.  The live cd works but after I install...nothing but a blank screen.  

Even more weird, I think, is that I had it installed as a dual boot with windows xp and that worked fine.  Then I decided I would make the move to just Ubuntu and after re-install, I get this problem. ??

Any help would be great.

---

### Post by HydroModeler on 2007-11-23
One more thing...  I think this thread provides some insight to the problem, but not enough to fix it.

[http://ubuntuforums.org/showthread.php?t=614152](http://ubuntuforums.org/showthread.php?t=614152)

---

### Post by kafpauzo on 2007-11-26
I've found an alternative that works very well for me. It's not Ubuntu, but I didn't necessarily need Ubuntu, even though I *really* liked Ubuntu. The important thing for me was that I wanted an open-source Unix-ish system.

It turns out that [PC-BSD]("http://www.pcbsd.org/") is just as easy to install as Ubuntu, and it offers an impressively rich set of features and applications. In fact, so far it seems to beat Ubuntu in all respects except one. When scrolling and dragging windows, movement on PC-BSD is jittery where Ubuntu is smooth. That's probably because PC-BSD is a single one-size-fits-all version, whereas Ubuntu has a special amd64 version.

But jittery movement is far better than a blank screen! :-D So far I'm *very* satisfied with PC-BSD.

---

### Post by kafpauzo on 2007-11-26
I just discovered that apparently [this solution]("http://ubuntuforums.org/showthread.php?t=622748") will give a working Ubuntu installation on our systems!

---

