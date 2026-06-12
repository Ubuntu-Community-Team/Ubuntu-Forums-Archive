---
title: "The Install program 'dies' after I tell it my keyboard...."
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by clarjon1 on 2006-08-23
Hello all, hope you can help.

I'm trying to install Ubuntu Dapper Drake from the CDs I got from shipit.ubuntu.com site.  All goes well up untill after I press the next/forward (i'm too tired to remember now)  button on the keyboard layout page.  After that, nothing happens.  No more CD accesses (unless i do something like start a program, or move mouse over icons on desktop, or something like that)
I'm going to try installing ubuntu breezy, and try upgrading manually to dapper, and see if that works.  wish me luck!  Also, if someone could explain to me what is going on here, as i would rather be able to install from the program.

Here's my vital stats:
Compaq P3 866mhz
128mb RAM  (could not enough mem be the problem?)
1+gb SWAP partition being accessed

i tried running the install prog from the terminal (sudo ubiquity gtkui), but that's a nogo.  I mean, no err messages from there.  It's very annoying.

Any help/suggestions/money would be greatly appreciated!

--Jonathan

---

### Post by avtolle on 2006-08-23
Given that you have 128 mb RAM, you should download the Alternate Install iso, burn it as an iso image to CD (at a slow speed, 4x or so), and try; however, given the low amount of RAM, I would recommend obtaining the alternate install iso for Xubuntu, and installing that. Rationale: the CD shipped by Ship-It is the Desktop CD; the graphical installer supplied therewith really needs a minimum of 256 mb RAM to work. The alternate install uses a text based installer, thus will work better on a low RAM machine. Xubuntu has the apps, etc. of Ubuntu, but uses a low resource DTE, Xfce. HTH.

---

### Post by wpshooter on 2006-08-23
Have you tried clicking on the keyboard test box at the bottom on the screen (you don't have to type anything in it - just click on it) and then click back on the keyboard box at the top of the screen and THEN click on the next buttom.

Make sure you give your CD drive time to spin down between each step in the installation process and you **MAY** be good to go.

But then again, due to your low amount of RAM, you may be forced to use the alternate install CD or try the Xubuntu version.

Good luck.

---

### Post by clarjon1 on 2006-09-22
I got it to install...

For some reason, it only seems to act up if I select the american keyboard layout.  After some trial and error, I was able to install it using the british english layout.  Thanks for the suggestions, though!

---

