---
title: "Why is the update to Open Office not in the channel?"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by eltonw on 2010-03-12
I just checked [Mar. 12, 2010 16h:00 EDT], there is no update in the (Canonical) channel for Open Office. I regularly download updates both automatically as well as manually, Yet my current version is:
OpenOffice 3.1.1
OOO310m19 (Build:9240). 
On my mac OSX 10.6.2, I already have 000320m12 (Build:9483).

Why is Canonical taking so long to place the newer version in the channel? 

My reason for seeking the update is to try and resolve a problem that I have just noticed today. I have not needed to print envelopes since January, and now I find that printing envelopes on my HP C4345 multifunction no longer works as before. 

Instead of putting the output on the RIGHT side (where the envelope is fed), OO is consistently sending the output to the LEFT side (easily confirmed by placing a standard letter size sheet in place of the #9 envelope, which (the latter) invariably comes out as "blank" (no print on it).:sad::sad:

I am hoping that an update will resolve this issue before I resort to submitting a bug report.

---

### Post by Hagar Delest on 2010-03-13
The new version won't be in the channel. Ubuntu doesn't update applications (except for security fixes). There is the PPA repositories where you can get the latest version but it's not maintained by Canonical.

If you want the latest and official (Sun) version, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by eltonw on 2010-03-14
Synaptic and Ubuntu Software Center show that OO is NOT installed, _they both state_: 
**"[COLOR="Red"]Canonical provides critical updates for openoffice.org until April 2011[/COLOR]."** _below the software description_.

Despite this, I am able to launch the OO applications. [Perhaps I may have corrupted the system somehow ... <*shrug*> :-( ]
I have now re-installed, but no updates show. Could you kindly provide me with 'dummy / newbie' instructions on how to add the PPA to the repositories list? 

... thank your for your assistance!;)

---

### Post by Hagar Delest on 2010-03-14
OOo is not in the Ubuntu software center because you've installed the Sun version.

Note that critical updates are only in case of major security issue. So this rather means: no update at all!

For the PPA way, a quick search gave me that link: [PPA For OpenOffice.org 3.0.1 For Hardy/Intrepid]("http://www.rebelzero.com/ubuntu/ppa-for-openofficeorg-301-for-hardyintrepid/94") for example.

---

