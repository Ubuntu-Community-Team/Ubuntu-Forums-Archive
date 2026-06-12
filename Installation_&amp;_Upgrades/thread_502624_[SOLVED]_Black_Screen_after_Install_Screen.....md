---
title: "[SOLVED] Black Screen after Install Screen...."
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by ReaderRat on 2007-07-16
When I try to install Ubuntu from either the i386 Live Cd or the Alternate CD, immediately after the install screen, the screen goes black (sometimes with a small cursor at the upper left corner of the screen). I have tried most of the options: 1)Install Ubuntu, 2)Safe Graphics Mode, 3)Checked both disks for errors, 4)Text Mode, 5)F4 To change video modes, and every time when I press ENTER, it goes to a black screen. I am using on-board video (ASUS M2A-VM mobo).  I have over a Gig of RAM. I have been through the BIOS setup to see if there were problems there, and I am stumped. What do I do next?

---

### Post by jgordon510 on 2007-07-16
2 things:

1)  When you get to the menu, add the following boot option (I think you press F6 for other options - not sure - it'll say).  A long string will come up and you'll have a cursor.  Add the text "acpi=off".  That's worked for me in a similar situation.

2)  If the first thing didn't work, use the alternate install disc.  You won't get the livecd experience, but it will probably install.

---

### Post by confused57 on 2007-07-16
Hi ReaderRat...a search of your mobo mentioned that your integrated graphics is probably ATI Radeon
Xpress 1250.   The alternate install cd is an excellent idea, then you can probably boot into recovery mode and install the fglrx drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by ReaderRat on 2007-07-18
Thank you for your support, confused57.  I did not know I had an ATI video. (It was on the mobo box, in fine print.) As it turns out, the problem was a bad (brand new) 1 gig  memory stick. It hosed my Vista and my Ubuntu installs.

---

