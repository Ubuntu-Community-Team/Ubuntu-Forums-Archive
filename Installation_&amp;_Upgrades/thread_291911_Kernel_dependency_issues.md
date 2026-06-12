---
title: "Kernel dependency issues"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by theblessedlunatic on 2006-11-03
I think I screwed up real bad.  Normally when something seriously catastrophic occurs I am able to figure out how to fix it, but I'm starting to despair now.

So I performed the upgrade to Edgy using the Upgrade Manager like everyone said I should.  The thing goes fine, but when it comes time to install the new kernel, something goes wrong, the kernel doesn't get installed, the upgrade crashes.  Computer restarts, and when the thing boots into the new kernel it undergoes "kernel panic" and just hangs.  I booted into the previous 386 kernel and was able to get a login at least, although x.org crashed HARD and gave me a bunch of output that I do not understand.

So I did the usual stuff to try and reinstall the new kernel, but every time I tried I would get a message to the effect of:

Package linux-image-2.6.17-10-386 is not configured yet.  Dependency problems - leaving unconfigured.

This same message is given for each of the packages in question, and then a thing at the end saying:


Errors were encountered while processing:
linux-image-2.6.17-10-386
linux-image-386
linux-restricted-modules-2.6.17-10-386
linux-386


I've tried running all the commands people say you're supposed to run in these situations.  Ran "dpkg --configure -a", got the same message.  Ran "sudo apt-get install -f", still didn't do anything.  I made sure the restricted repositories were enabled 'cause I'd read something about that in a totally unrelated thread.  That didn't do anything either.

At one point I was getting a message that my /boot directory was full.  I don't see this message anymore, but it might be at the top of the readout where I can't scroll up to see it.  If this is the case, how do I clear out my /boot directory if I can't apt-get remove any of the old kernels?  'Cause every time I do, it just takes me back to the installation of the new 386 kernel and dies.

It's worth mentioning at this point that I have an AMD Athlon so I should really be running the K7 kernel, but by the time I figured this out it would have been a real pain to go back and redo all my settings and stuff.  This has never been a problem before, and I don't see it being one now.  When I try to apt-get install the K7 kernel it gives me the same song and dance about not being able to do anything with the 386.

I'm about to go crazy with this thing; I thought I'd finally gotten proficient enough with Ubuntu to not have to reinstall the OS every other week, had managed to go almost an entire year without irrevocably screwing the thing up.  I really don't relish the thought of redoing all my settings, so any help you might be able to provide is greatly appreciated.

---

