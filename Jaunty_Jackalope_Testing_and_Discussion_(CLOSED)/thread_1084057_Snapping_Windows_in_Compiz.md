---
title: "Snapping Windows in Compiz"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scaine on 2009-03-01
The default in Ubuntu when you use desktop effects (compiz) is to "snap" the windows to the nearest screen edge, or edges of other screens.

I hate this and immediately turn it off (snap inverted in the move plug-in).  It appears to be broken.  Can anyone confirm and if so, I'll be happy to raise a bug.

Incidentally, the <shift> button modified does work to invert the snap so that windows don't snap anymore, but like I say, this bug is about inverting that behaviour so that the <shift> key would invoke the snap and windows ignore edges otherwise.

---

### Post by olskar on 2009-03-01
> **scaine said:**
> The default in Ubuntu when you use desktop effects (compiz) is to "snap" the windows to the nearest screen edge, or edges of other screens.

I hate this and immediately turn it off (snap inverted in the move plug-in).  It appears to be broken.  Can anyone confirm and if so, I'll be happy to raise a bug.

Incidentally, the <shift> button modified does work to invert the snap so that windows don't snap anymore, but like I say, this bug is about inverting that behaviour so that the <shift> key would invoke the snap and windows ignore edges otherwise.

Perhaps even raise a bug about not having it snap by default? I would support it.. +1

---

### Post by scaine on 2009-03-01
I doubt they'd listen to a bug on that subject.  Things got pretty heated when they first introduced snapping and basically, if I remember correctly, the upstream maintainer of Metacity in gnome pretty much just turned this on and claimed it made the world a better place.  Around 2006, I think.  I'll have a search for the reference later.

These days, whenever gnome makes a decision like this, I have to admit that I just can't bring myself to beat my head against that wall yet again.  I just chalk it up as one-more-thing-I-have-to-change-after-a-fresh-install and move on.

Maybe one day, they'll fix gnome-screensaver.  I doubt it - considering that they don't consider it broken, despite the fact you can't edit the properties of any screensavers.  Something about themes.  I just stopped using screensavers...

---

### Post by scaine on 2009-03-01
Oops - sorry, I went in again to get details for a bug report and after clicking on the snap_inverted tick box a couple of times, it's now taken and all seems well!  It *was* ticked when I just fired it up there though, so there *was* a problem - but not any more!

EDIT : Ah, goddam!  It only works for windows on the screen at the time you tick the box.  New windows generated after you've closed down Compiz Settings Manager revert back to snapping.  It's getting late - I'll file a bug tomorrow.

---

### Post by Nerd_bloke on 2009-03-08
Another user created [Bug 327442]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/327442") about about snapping-by-default; head on over if you want to subscribe/click on the bug's "affects me too" link.

---

### Post by Therion on 2009-03-08
Try opening the "Wobbly Windows" plugin.

Clear the checkbox for **Snap Inverted**.

Joy??

---

### Post by andrewsomething on 2009-03-08
> **Therion said:**
> Try opening the "Wobbly Windows" plugin.

Clear the checkbox for **Snap Inverted**.

Joy??

I bet this is the issue.

Every time I do a fresh install, I end up hunting around CCSM trying to remember where they hide that, until I remember it's in "Wobbly Windows." Some times all the overlapping functionality in the plugins can be very annoying.

---

### Post by scaine on 2009-03-08
Fraid not - it's always "wobbly windows" where I tick the "Snap Inverted" box (EDIT : I see that I confused the issue in my first post, claiming it was in the "move" plug-in - sorry about that).  In Jaunty, it takes the value until the next reboot, then reverts to snapping again.

At least I can over ride it with the snap key (default is shift), but it's a pain, cos I'd prefer the default to not snap, which is what "snap inverted" does.

Thanks, Nerd_bloke, for pointing out that bug, although I'd already found it in my search to create a new bug... but I didn't subscribe because I'm not completely sure it's describing the problem exactly.  Although I see you've noted a regression against old behaviour, so hopefully this will get the ball rolling.

---

### Post by scaine on 2009-03-08
For interest, here's the original metacity snapping discussion :
[http://ubuntuforums.org/showthread.php?t=94299](http://ubuntuforums.org/showthread.php?t=94299)

---

