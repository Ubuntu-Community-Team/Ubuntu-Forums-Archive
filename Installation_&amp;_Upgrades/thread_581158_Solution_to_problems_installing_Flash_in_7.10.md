---
title: "Solution to problems installing Flash in 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Brian Kendig on 2007-10-19
Here's a tip to help anyone else who runs into the same problems I did.

I just installed Ubuntu 7.10 from scratch, and it didn't have Flash video support. I went to YouTube.com and it told me that I had to install Flash, and it linked me to the Adobe web site, where I was very confused by the offerings and couldn't figure out which of their downloads I needed...

There's no Flash plugin listed in Synaptic, either, except for the freeware Gnash player, which I've seen sites telling me to avoid because it's not compatible with most Flash content.

Eventually, after surfing around for a while, I came across a page which brought up a popup window which prompted me to install Flash, and gave me two options: Flash or Gnash. I selected Flash, and got an error that flashplugin-nonfree couldn't be found.

Frustrated, I dug around ubuntuforums for a while, until I found a post which said to turn on 'universe' in Synaptic. I did that, and now Firefox was able to install the Flash plugin, and it works fine now.

This is way too confusing for the average user out there, and I hope it's made easier in a future release of Ubuntu.

---

### Post by benhur99ph on 2007-10-20
I ran into the same problem that you did. But instead I selected to install GNASH. Yes, there are incompatibilities with most flash content. On youtube, the movie controls are all jumbled up. 

My solution -- Installed Opera Browser. It already has flash so no need to fiddle around.

---

### Post by Nameless_one on 2007-10-22
1) You should check whether the "universe" and "multiverse" repositories are enabled - they contain many useful programmes. However, you should be aware what they are. You can read all about it [here](https://wiki.ubuntu.com/AddingRepositoriesHowto).

2) Opera doesn't already have flash, it has to have been installed some way. Flash is a plugin, it is independent of browsers. How it worked for you out of the box I can't imagine.

---

### Post by benhur99ph on 2007-10-23
Well, I dunno. I installed a deb package. After that I started browsing with it. When I went to a site that uses flash, it immediately played the flash video....

---

