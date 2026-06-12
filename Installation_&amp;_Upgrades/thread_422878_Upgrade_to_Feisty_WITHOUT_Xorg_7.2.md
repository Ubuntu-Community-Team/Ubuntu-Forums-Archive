---
title: "Upgrade to Feisty WITHOUT Xorg 7.2?"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by wyth on 2007-04-25
Easy enough question, I hope.  I tried upgrading to Feisty, but my old video card doesn't play well with Xorg 7.2 (really need fglrx, and it's not working with ATI 9000 in Xorg 7.2), nor could I get Network Manager to work with any secure networks.

However, I kind of miss the upgraded Gnome, the newest Open Office, and some of the other perks that came with Feisty (and worked great on my laptop).   

Is there a way to get the new Gnome/Open Office through the repositories?  I tried to install the newest OOo via a few how to's, but every time I installed anything else, apt would remove OOo.  Or is there even a way to upgrade to Feisty but keep Edgy's Xorg, and python?  I just want a way to get some of the Feisty features in Edgy, at least until some of the Feisty issues get ironed out.

---

### Post by jda1701 on 2007-04-25
Nope,

Feisty requires the use of Xorg 7.2  Its simply a package dependency.  

Could you elaborate on why your video card doesn't work well with 7.2?

---

### Post by wyth on 2007-04-25
Quickly on the video card: I have an ATI 9000 (Radeon R250).  The radeon driver doesn't work well for it.  My screen shreds with any video, any QT app (amarok), and anything graphics-intensive.  It also ramjets my fan.  I use fglrx in Edgy, and it works perfectly.  But right now, fglrx isn't supporting my card in Xorg 7.2, so it looks like I'm stuck.  It's a 5-year-old laptop; I know there are older ones that are being supported, so it's a little frustrating.  I've already been all over the multimedia and video forum here trying to get a solution.  Seems like the solution is not to upgrade to Feisty (yet).

So the other question, then: Is there a way to get the latest Gnome and OOo in Edgy, preferably through the repositories?

---

