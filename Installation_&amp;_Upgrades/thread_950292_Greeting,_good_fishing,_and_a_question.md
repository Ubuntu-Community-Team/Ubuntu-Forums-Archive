---
title: "Greeting, good fishing, and a question"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by UbeeNewbie on 2008-10-17
Hello, and thanks for reading my newbie-ish topic!  I'm very new, so please be gentle!

I'm attempting an install of Ubuntu onto a system I bought at auction.  It's a Compaq dual 1GHz Xeon machine with 1Gb of ECC RAM.  The video card is a Fire GL 2.

(Please bear with the following story as I think it has bearing on my current dilemma.)  I had previously installed Debian, the KDE flavor, which seemed to go along fine and installed okie dokie. . . .That is, until the installation was complete and Debian attempted to fire up the log-in screen.  At this point, the screen went crazy, with a horizontally striated pattern that scrolled vertically upward.

I tried various, desperate things to get this fixed to no avail.  I know the system was working (or at least I think it was), because I could hit ALT+F2, turn on NUMLOCK, hit ALT+F3, and watch the NUMLOCK turn off.  I could switch back to F2 and NUMLOCK would turn back on.  Bottom line is that I think the system was working other than the video being screwy.

Okay, fast forward to the Ubuntu attempt.  I'm trying to get Ubuntu to save the day, but it's having an even harder time than Debian.  Or at least I think it is.  The initial Ubuntu boot screen will appear, but soon after I hit ENTER, the screen goes dark and the system never recovers, and nothing gets installed that I know of.

Can you guys help me with this?  I think it may have something to do with this Fire GL 2 card, but I'm just too inexperienced to troubleshoot the system by myself.  Any help would be greatly appreciated!

---

### Post by cariboo on 2008-10-17
Could you please tell us what version you are trying to install, we have to know that before we can help you as things have changed quite a bit over the last 4 or 5 releases.

Jim

---

### Post by UbeeNewbie on 2008-10-17
Hello.  Thanks for your response.  The version I'm trying is 8.04.

---

### Post by Bucky Ball on 2008-10-17
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by UbeeNewbie on 2008-10-17
Okay, thanks much!  I'll give this link a shot and let you guys know how it goes. . . .

---

### Post by UbeeNewbie on 2008-10-19
All right, I've been trying to get to the point that I can try this, but I can't get that far.  Here's my current situation: I put in the Ubuntu CD, fire up the system with the BIOS set to load from the CD first.  The system goes into the initial Ubuntu screen that allows you to do an install, live install, etc.  At this point, I've tried LIVE and LIVE-INSTALL.  Both start okay, with the system saying its loading something or other.  Within about ten seconds of issuing the LIVE-INSTALL command, the font style of the text on the screen changes to a finer one, and then within a second the screen goes blank.  The floppy drive light comes on, and the floppy clicks for about ten seconds.  Then the light goes out, the CD spins up audibly, and that's it.  It won't go any further - just a blank (black) screen.

So, I can't get anywhere as of now so that I can try installing the drivers for the Fire GL 2 card.  In other words, I can't make it to a command line prompt.

Do you guys have any suggestions as to what I might try to at least get to a command line prompt?  Thanks again!

---

### Post by UbeeNewbie on 2008-10-19
Okay, more updates on my progress.

I had another video card that I swapped for the Fire GL 2.  The Fire GL 2 was an AGP Pro, while the one I found was AGP.  I plugged the "new" card into the AGP Pro slot, and now it seems like everything works okay!

All right, so now I'm going to install Ubuntu with this card, but eventually I'd like to try to get the Fire GL 2 card working.  So, my question becomes this.  How can I install Ubuntu with one card, and then switch to the other?

Also, I'm trying to install Ubuntu as I write this, but a previous install of Debian seems to be interfering.  The install stops with the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


What does this mean, and how can I get Ubuntu to install over Debian?  I have nothing on the hard drive that I want to save.

And thanks yet again!

---

