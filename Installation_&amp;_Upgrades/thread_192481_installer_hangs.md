---
title: "installer hangs"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by bzarnsy on 2006-06-08
install seems to go just fine.it starts copying files but when the progress bar
gets to 84% configuring apt it hangs forever. i had to power down manually.
any ideas? did the search thing and found a similar problem but no solution.
i never had any problems with hoary or breezy.

---

### Post by firefly2442 on 2006-06-19
My roommate has the same problem.  Anyone have any ideas?  Should he try the alternate CD iso?  Is there an expert mode that lets you follow along manually?  Thanks.

---

### Post by confused57 on 2006-06-19
I would definitely try the alternate CD, if it was the Live Desktop CD that stalled...if you have a fast internet connection and the alternate install CD still stalls, you could do a server install from the alternate CD and:

sudo aptitude update
sudo aptitude install ubuntu-desktop

or

kubuntu-desktop
xubuntu-desktop

I once had an installation of the Xubuntu alternate CD hang at about the same place on an old pc, 500 MHz, 256 ram...the week before Xubuntu(same CD) installed completely in about 45 minutes...go figure.

---

### Post by firefly2442 on 2006-06-19
My rommate got it to work by swapping out the network card.  It sounds like a network issue connecting to the server possibly?  It could also be the CD-ROM because he replaced that too.  HTH. :)

---

