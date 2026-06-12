---
title: "Transitioning from Ubuntu to Xubuntu/Lubuntu"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Rhapsody on 2011-05-03
I have a PC here called Chihiro that is currently running Ubuntu 10.10 but probably won't be soon. Unity seems to be a bit much for Chihiro's low specs and after four years it seems time to transition Chihiro to something more lightweight.

The question is exactly how do I do this with the minimum of disruption to the users of this installation. Chihiro uses a separate root and /home setup, so wiping root and reinstalling is an option, but is it reasonably possible to just use the package manager to move from one *buntu to another? How-tos and the sort would be very helpful if they exist, since I haven't been able to find anything on this subject.

As a side question, which does everyone think would be the better choice for these specifications:

AMD Sempron 2800+ (1.6Ghz clock speed)
512MB RAM (64MB shared as video memory, will be upgraded to 2GB with 128MB as shared video memory if I ever get around to it)
"GeForce6-class graphics" (quote from the motherboard manual about the onboard graphics, I don't have details on it)

Xubuntu and Lubuntu are what I'm considering. Xubuntu would usually be my first choice, but I've heard a lot of good things about Lubuntu as of late and anything to lower the load on the ageing Chihiro would be appreciated.

---

### Post by Cheesehead on 2011-05-03
```
sudo apt-get install xubuntu-desktop
```
Try it.

If you decide you like it,
```
sudo apt-get remove ubuntu-desktop
```
Use 'remove' instead of 'purge' to preserve your Gnome settings...because people change their minds.

When apt-get gives you that big list of stuff to remove, **look it over carefully** for unpleasant surprises, like widgets or tools you use frequently. Two minutes spent looking at that list might save you hours of frustration.

I have used Xubuntu for years. Love it - fast, flexible. I don't miss the bling.

---

