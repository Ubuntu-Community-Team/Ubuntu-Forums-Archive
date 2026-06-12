---
title: "Graphics corruption in Karmic (X? SiS?)"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Count Chocula on 2009-10-26
Is anyone else having problems with graphics corruption in Karmic Koala? I am not sure how to report the bug or bugs I am encountering. Sometimes the screen freezes and doesn't respond. More often things aren't being drawn correctly. Usually it is when something is moved on screen it looks like the computer doesn't update correctly. Sometimes when I scroll a window, the newly revealed image data is drawn, but the rest of the window doesn't move/scroll.

Other times I get lines drawn across the whole screen (particularly when I launch some java programs, but I've had it happen other times too.)

I am wondering if it is specific to my computer having mainboard SiS 760 graphics controller with shared graphics memory? I didn't have any such problems with Jaunty or previous Ubuntu releases.

Anyone else with SiS graphics controllers having trouble like this?

---

### Post by fancypiper on 2009-10-27
I had a sis grapics board once.  I quickly got rid of it because of the problems you are having.  I suggest buying a better supported graphics card.

---

### Post by Count Chocula on 2009-10-27
> **fancypiper said:**
> I had a sis grapics board once.  I quickly got rid of it because of the problems you are having.  I suggest buying a better supported graphics card.

Well, I had an nvidia card but I gave it to a relative. Now I'm unemployed and can't buy squat. 

But anyways, this system worked fine in Jaunty and before then with the SiS onboard graphics. Also it works fine for stretches of time now. So I think it is a new bug rather than a fundamental incapability of the card, no?

I guess if I'm the only one in the world like this, sure I'll donate some blood plasma and get another graphics card :) I just am wondering how many other folks out there may be having similar issues in a few weeks after the Karmic Koala actual release.

---

### Post by fancypiper on 2009-10-27
[img]http://www.icalledit.com/forums/images/smilies/trink4.gif[/img]I have been reading about all the problems people have been having understanding the patent restrictions imposed by non-open source stuff which is easier for me to get than installing a few things I wanted in Windows. It was so very easy for me to upgrade this box through two releases that I am puzzled at the amount of trouble.  I just waited until less than a week to go for each one and here I am with only two very minor problems to straighten out. I'll bet another install after the release and you'll be there.  I could give you my card and install a better one I have in the closet if worst comes to worst.

Good luck, everybody!

---

### Post by Count Chocula on 2009-10-27
Interestingly enough, I find that if I boot with my last Jaunty kernel (2.6.28-15-generic), with everything else being Karmic packages, I don't have the graphics problems. (Though other stuff breaks, like sound and hibernate. At least there are no freeze-ups.)

I've used this setup since Hoary Hedgehog, without graphics trouble. What's that, ten releases? But I'm not complaining, just investigating. Anyone know what happened?

---

### Post by cariboo on 2009-10-28
The problem is more than likely because of changes in xserver-xorg.

---

