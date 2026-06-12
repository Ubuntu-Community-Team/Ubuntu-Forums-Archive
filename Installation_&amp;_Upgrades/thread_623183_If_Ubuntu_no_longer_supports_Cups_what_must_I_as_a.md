---
title: "If Ubuntu no longer supports Cups what must I as a user do about it?"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by gwm on 2007-11-25
While upgrading to Gutsy, I got messages telling me that Ubuntu no longer supports CUPS.
What does it support then?
What action should I take?
These questions aren't trivial because I now have these new problems. Perhaps they are CUPS problems. Perhaps they are Open Office problems. What am I supposed to use instead of CUPS?
My printer uses HPLIP.

The first job for the day now gets stuck in the print queue. It is marked as pending. Is there some way I can find out why it is pending? It simply hangs in there, blocking!
When I try printing a test page, things clear.

My color cartridge ran empty, so I switched to printing in gray scale until I had a new color cartridge but now It only prints gray, no matter what I do. The PDF image viewer prints OK, so I first print to a PDF file and then use the PDF viewer to do the color printout

Any help would be appreciated
:popcorn:

---

### Post by elctb on 2007-11-26
As far as I know Ubuntu is using cups. Actually, I'm using it on my Gutsy installation.

I would try the following:
. Make sure the cups modules are installed:
  sudo apt-get install cupsys\*
. Configure cups:
  Point browser to localhost:631 and add/configure the printer.

---

