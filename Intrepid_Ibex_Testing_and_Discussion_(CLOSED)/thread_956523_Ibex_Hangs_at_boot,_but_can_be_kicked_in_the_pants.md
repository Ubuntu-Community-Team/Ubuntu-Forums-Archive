---
title: "Ibex Hangs at boot, but can be kicked in the pants"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by converted on 2008-10-23
I upgraded Hardy to Ibex about two weeks ago.  I actually got an error at the end of the process, but was prepared to reinstall if necessary, so just rebooted anyway to see what would happen.  (I didn't jot it down, which I would have done if I'd expected to be posting for opinions - sorry)

Long story short, everything has seemed fine.  Further updates have gone off without a hitch, and I can't detect any problems at all.

There is one exception, however.  Since the Hardy to Ibex upgrade, my laptop will not boot fully without me hitting the space bar (I suspect any key would work) at several points in the boot process.  The initial back-and-forth progress bar hangs about 1/4 of the way across on its first pass, and I have to hit the bar several times to get it to go fully across, and come back.  Once it changes to a standard progress bar, I have to hit the space bar a few times prior to about 30% completion, then it goes the rest of the way by itself.

I tried a verbose boot, and had to interact roughly the same number of times to get it to boot, and noticed nothing alarming on the screen at the times when the bar needed to be hit.  Like a normal boot, it would just stop until I interacted with it.

I know there is a bug around regarding silent boot problems, but it sounds like my symptoms don't quite match those.

I don't mind waiting for the release to see if it clears up, and I don't really mind reinstalling after Final is out to see if that fixes it, but I'm curious whether anyone has had similar problems and if it sounds like the kind of thing that is likely to be resolved in these last few days before release.  I don't know whether to think it is related to the error I got when first upgrading or not.

Any thoughts?

The laptop in question is an HP DV9910US.

---

### Post by spikenick on 2008-10-23
:(I am experiencing this same problem, I believe it has something to do with the new kernel. Just for the info I have a dv6700CTO (custom to order, no specific model) with the basic amd turionx2 and nvidia graphics I too would really like to know what is going on here, if anybody finds an answer please post it back.

---

### Post by pBeseda on 2008-10-23
I'm having a similar issue, I don't know if it warrants a new thread. It runs through the loading screen, the gold progress bar reaches full, and then it goes to the screen that displays the status of everything starting up.

The last thing it displays is "Checking battery status     [OK]"
and then it stops.

I learned I can ctrl+alt+ F1-F6 and login and stuff works fine, but no gnome.

---

