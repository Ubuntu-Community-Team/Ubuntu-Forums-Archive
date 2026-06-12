---
title: "Live cd - blank screen when booting"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CbrPad on 2009-10-10
I had an early alpha installed on a spare partition (which was working fine) but decided to download todays daily image - [http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/current/karmic-desktop-i386.iso) (10th October)

I can start booting and choose English, but after that nothing.  The screen goes blank and a logo flickers for a fraction of a second but that's it.  This is the same no matter whether I choose a live session, to install or even to check the disk.   I cannot get a console or anything and Ctrl-Alt-Del flickers the logo again before restarting.   Checksum etc is ok.

I've read about a similar bug with Intel graphics but I cannot even see a cursor.  I've a HP Pavilion DV2000 laptop with Nvidia Geforce 7200 graphics.

Any ideas of any way to solve ?  I've only a small monthly download allowance so can't download any more images, so I'm disgusted that I've blown it all on one that's probably useless (been using Ubuntu since the very first release inc most alphas and never had anything like this before, ah well).

---

### Post by emarkay on 2009-10-10
If your card is an AGP, this same issue affected me, ensure your AGP Aperture is set for 256Mb or more.  Otherwise, it's up to the rest of us to assist.
I do recall a few of these sort of non AGP issues, so do a search on some keywords, including your graphics card name, in the case that there may already be a solution.

---

### Post by cariboo on 2009-10-10
Have you tried starting in safe graphics mode?

Press F4 at the menu screen and select safe graphics mode then press Enter. Select what ever choice you want from the men and press enter, you should be taken to a desktop.

---

### Post by CbrPad on 2009-10-12
I'm afraid my bios has no options for changing anything like that.   I have tried safe graphics mode, noapic, etc, but nothing either.  Sometimes I might get a continuously flickering screen full of garbage, I can just about make out a wallpaper for a tenth of a second before it changes again.

---

### Post by exploder on 2009-10-12
My situation is very similar, except I get dumped to a console. I have Intel graphics and have tried everything to get to the desktop with no luck either.I can see the desktop start to load for a couple of seconds if I type startx but is crashes every time.

I have read some posts where some with NVidea graphics are having the same problem. The most common answer I have found is that there is something wrong with the current kernel. I just keep trying daily builds to see if anything has changed.

---

