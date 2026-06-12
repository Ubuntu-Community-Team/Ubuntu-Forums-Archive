---
title: "&quot;Workaround&quot; for Ejecting CD/DVD Tray (Karmic)"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jperez on 2009-10-06
For all those that usually have to type in "eject" just to get the tray open due to the hardware not communicating with the OS (bug), I figured I'd lend a (slightly) helping hand.

Easy way to go about doing this without having to type in eject all the time is to put a launcher in on the top panel (if you have a top panel) and have it execute the "eject" command.  Mine is simply as follows:

Name: Eject
Command: eject
Description: Eject CD/DVD Tray

Can't find an icon to fit the new Humanity theme in place?  I created a small SVG icon for you to use (see attachment).  Hope this helps anyone until it's entirely fixed! :)

Jesse~

---

### Post by Squonk07 on 2009-10-06
That works very well. Thanks for the suggestion (and the icon).

---

### Post by jperez on 2009-10-06
No problem. :)

Figured it would be much easier for users in general, whether they know a lot about the system or are beginners.  And it can be a great thing to use in case you don't feel like reaching over and pressing the button on the tray yourself. :lol:

Jesse~

---

### Post by emarkay on 2009-10-06
Hmm, I was wondering about this...  Has a Bug Report been made on this yet?

---

### Post by TrueJournals on 2009-10-06
[https://bugs.launchpad.net/ubuntu/karmic/+source/devicekit-disks/+bug/397734](https://bugs.launchpad.net/ubuntu/karmic/+source/devicekit-disks/+bug/397734) seems to be the relevant bug...

---

### Post by executorvs on 2009-10-08
there seem to be a couple different bugs.
1.) can not eject once you mount media.
2.) eject button opens the drive but media is no longer detected. (work around is to use the eject cdrom command in terminal and NEVER touch the button)
3.)there is a third variant but I can't find it right now and it was supposedly fixed a couple weeks ago...

I would love to have a hardware support wiki which support public comments and links to bugs affecting any given piece of hardware. I may look into it after my midterms and tests are done... feel like I'm in a meat grinder right now and am trying to get info on bugs for 4 peoples' computers in hopes of aiding in solving the issues before final.

---

