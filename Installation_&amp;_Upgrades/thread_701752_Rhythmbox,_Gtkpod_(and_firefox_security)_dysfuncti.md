---
title: "Rhythmbox, Gtkpod (and firefox security) dysfunctional after libgpod2 compile"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by casperlingus on 2008-02-19
Using Gutsy 7.10, i386

**PART 1 - **
I totally hosed my Rhythmbox & gtkpod in an attempt to compile a new version of libgpod2 to get my new iPod Nano working.  I believe the problem cropped after I removed libgpod2, rhythmbox and gtkpod then ran the command:
```
sudo apt-get build-dep libgpod2
```

I eventually got libgpod2 compiled and then reinstalled rhytmbox and gtkpod, but both of them start and then freeze immediately, needing to be killed.  Completely unusable.  I've tried all sorts of things to remove and reinstall everything back to it's original state, but I suspect that doing the build-dep command compiled a bunch of stuff that's incompatible with existing packages on my computer.  I remember seeing al ist of packages pop up that were going to be compiled/installed by build-dep, but I didn't take note of them, and now I can't figure out what it was.

Does anyone else know what might be the problem?  Perhaps there's a way to trace the error?  Rhythmbox with debugging output from the command line is useless.

**PART 2 - **
And as a side effect, firefox now pops up a dialog when it starts 
> *"Could not initialize the browser's security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behavior when accessing security features."*
I've tried everything on the website:

[http://support.mozilla.com/kb/Could+not+initialize+the+browser+security+component](http://support.mozilla.com/kb/Could+not+initialize+the+browser+security+component)

to no avail.  I don't think it's a problem with my ~/.mozilla directory but something else on the machine.  I'd also like to figure out what directory it can't access

EDIT:  I forgot to mention that I followed the directions on the middle of page 4 of the following thread, to try to compile libgpod2:
[http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+nano&page=4](http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+nano&page=4)

---

### Post by vagabond_gr on 2008-03-08
I had the same problem with firefox (and the security component) after following [this howto]("http://ubuntuforums.org/showthread.php?t=658523#post4074311")
 to get my 3rd gen iPod to work with rythmbox. To fix the situation I had to do the following:

1. Install back the original version of all installed packages.

In my case I had to downgrade the packages installed from hardy using more or less the instructions from [this link]("https://help.ubuntu.com/community/DowngradeHowto"). This does not apply unless you installed packages from hardy (next ubuntu version).

2. Reinstall the packages libnss3-0d and libnss-mdns. This can be done by selecting the in synaptic, right-click and select "mark for reinstallation" and click "apply".

---

