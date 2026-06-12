---
title: "fud - is there a problem with 2.6.17.12?"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by engine on 2007-09-18
A friend sent me a link to an article [kernel-update-breaks-ubuntu]("http://www.lockergnome.com/nexus/linux/2007/07/19/kernel-update-breaks-ubuntu/").

A couple of days later, synaptic started offering me 2.6.17-12 ... I know the article says it's general advice and not pointing fingers at specific kernels, but it's a bit worrying for a user who just want to get on with *using*, not scrabbling about under the bonnet to correct things that shouldn't have gone wrong in the first place. I've already had this particular problem once, and don't want to grapple with it again.

Can anyone out there reassure me by putting his or her hand on heart and saying updating to 2.6.17-12 did **not** shut down the GUI? thanks in advance!

---

### Post by hardyn on 2007-09-18
It was a problem in edgy... quite a while back... (current kernel is 2.16.20).  seeing at the article that you referenced was several months ago, im sure that whatever caused a problem has been fixed.

---

### Post by dabl on 2007-09-18
> **engine said:**
> 

Can anyone out there reassure me by putting his or her hand on heart and saying updating to 2.6.17-12 did **not** shut down the GUI? 



You realize, of course, that if you install a proprietary graphics card driver, EVERY kernel upgrade will break your GUI, until you re-install the proprietary driver?  Just checking ....   :)

---

### Post by hardyn on 2007-09-18
only if you don't the repo drivers.

---

### Post by dabl on 2007-09-18
> **hardyn said:**
> only if you don't the repo drivers.

Right -- I should have said "if you install the non-packaged proprietary drivers".  :)

---

### Post by engine on 2007-09-19
> **hardyn said:**
> current kernel is 2.16.20

So how come synaptic is offering me 2.16.17.12 as the latest and greatest? just curious ...

---

### Post by hardyn on 2007-09-20
because you are using an old version... it probably is the latest and greatest for that release.

---

### Post by engine on 2007-09-22
d'oh ... good point - perhaps it's time to bite the bullet and rush forward to 7.04

Thanks for the reminder

---

### Post by engine on 2007-09-23
<sigh> Sat down to run the upgrade, and it failed. There's something it doesn't like about timidity, and synaptic won't even let me remove timidity to sidestep the problem. Someone else has already posted about this, and not got any help.

---

### Post by engine on 2007-09-23
FUD, again ... after frightening messages assuring me the whole upgrade had failed, my system was probably unstable and doom was just around the corner, I assumed the upgrade had failed.

Then I restarted the system anyway, just to discover the worst. ```
cat /etc/issue
``` just out of curiosity, and whaddayouknow - 7.04

So perhaps I _am_ now running 7.04 ... only time will tell.

The good news is ... the new release, whatever it may be, has let me use synaptic to uninstall timidity. Which, of course, I had to be able to do in order to upgrade to the new release. System message: the normal sequence of cause and effect is suspended for the duration of this installation <g>

---

### Post by SpiritIsReality on 2007-09-23
howdy
this help?
[http://www.google.ca/search?hl=en&q=command+%22ubuntu+version%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=command+%22ubuntu+version%22&btnG=Search&meta=)

trails

---

