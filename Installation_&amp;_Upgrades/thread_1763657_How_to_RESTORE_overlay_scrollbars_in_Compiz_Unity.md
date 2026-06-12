---
title: "How to RESTORE overlay scrollbars in Compiz Unity"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by rtimai on 2011-05-20
I'd like to know how to restore the default overlay scrollbars in Compiz/Unity should I ever find out how to get right-click working for my Synaptics Touchpad (touchpad currently disabled.)

Background:
Upgraded to 11.04 Unity and got missing Launcher and Panel symptom. Fixed by switching to Classic Ubuntu on login, Googling the symptom, and following instructions for resetting Unity to default options. Hooray! 

Disabled Unity's default overlay scrollbars because it didn't provide a clue to how long a page was (I liked that the scroll button size was a rough indicator of page length.)

But if I should ever get my Touchpad working, I'd like the option of restoring the overlay scrollbars (which seems to be designed for touch controls.) 

As a test, I tried re-installing the overlay scrollbars from Synaptic Package Manager, but doing so did not have any effect on the scrollbars even on restarting. Could find no "restore overlay scrollbars" information anywhere.

EDIT: Answering my own question

I realized later on that the answer was kind of self-obvious, but didn't get around to testing it for a while, because of other issues (they got fixed by subsequent Unity/Compiz updates.)

sudo rm /etc/X11/Xsession.d/80overlayscrollbars

And if one removed the packages, re-install the overlay-scrollbars and liboverlay-scrollbars (the current versions should be listed in the Software Center.)

---

