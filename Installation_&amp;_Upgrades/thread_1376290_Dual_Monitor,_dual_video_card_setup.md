---
title: "Dual Monitor, dual video card setup?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by aaron_the_dude on 2010-01-09
I just got another video card from a friend and I wanted to see if I could get it to display a second screen.  I have two monitors, both VGA CRT monitors (I'm oldschool, and slightly poor)  The first video card is a Geforce 8400gs pci-e and the card given to me is a Geforce FX 5500 pci.  I could get them both to work separatly under low graphics mode when I go into the bios and switch the video adapter from pci-e to pci, but not together.  Any idea where to go, or what to do to make both cards work in harmony?

---

### Post by aaron_the_dude on 2010-01-09
bump

---

### Post by gradinaruvasile on 2010-01-09
First, do you have the proprietary drivers installed?

Second, does any of them have more that 1 video connector? The 8400 has dual screen support AFAIK. Plug both monitors in it, open nvidia-settings(from the proprietary drivers) and set up.

About using the 2 cards: i dont know if and how it can be done. I heard that 2 cards were used in SLI mode and the Xserver can be configured to use more than 1 card, but it is tricky. 
AND you must have BIOS option for it. If not, it wont work.

You are better off using the 8400 dual screen mode. That is simple and straightforward, except you may run into resolution problems because of old monitors.

---

### Post by aaron_the_dude on 2010-01-12
Ok, I kinda got it to working, but not to my liking just yet.  I now have both monitors running right now with both the video cards.  Only thing is, the second is set to use as a second display, and when I try to enable Xinerama and restart my xserver, or the whole computer, it gets past the login, but when it tries to turn the monitors on, it keeps trying, and trying until a message pops up saying that it tried starting up the monitors 6 times in the past 30 seconds and then I restart it.  Restore my backed up xorg.conf file, and am stuck with two separate screens that I can't drag stuff accross.  Also, when I click on most applications on the second screen, it opens them on the first screen, how do I get around that?

---

### Post by aaron_the_dude on 2010-01-12
bu-ump

---

