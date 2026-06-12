---
title: "Problems upgrading L-UB from 12 to 14"
date: 2015-07-25
forum: Installation &amp; Upgrades
---

### Post by mringer on 2015-07-25
Sorry if these problems are known or fixed, I could not find 
them reported in this Forum.

Dell Inspiron 1525, dual boot windows and L-Ub 12.04, I 
decided to install 14.04.

I made the Live CD, checked for errors, found none. Booted
from the CD.

1. Wireless network not working. I think this is because I
have one of these **beloved** Broadcom cards, but I think the
CD should be able to identify the card and use the relevant 
driver. 

I started again, wired.

2. "Installation type" screen offers these options:

Upgrade 12 to 14 (default)
Erase 12 and install 14 (will delete all 12 programs/docs/photos)

and some more options, but before I could read them & take notes, 
it advanced to the next screen "where are you?" . There was no
visible way to go back. The back button was greyed out.

3. I proceeded, and got:

error restoring previously installed applications

but it does not say which applications. Please is there any way to 
discover which apps gave errors?

4. and then I discovered that all the users had been deleted. Luckily
there were only a few, and the home files were intact, (and anyway I
had backed up /home). 

I cannot recall exactly what I did next, something like

sudo useradd john

for each user, and then I found that the re-created users all seemed to have
incorrect home directories. For example   john   owned  /home/anne   etc.
After correcting this, I then found that I could not log any of these users in.

In the login panel, I chose john and entered his (correct) password. Screen 
went black and the the login panel reappeared. This is entirely different from 
what happens with an incorrect password. Then, the system behaves properly
and shows a "wrong password" message. I think this was caused because the 
skeleton files did not get created when I re-created the users. 

Eventually I think I solved this problem, not sure how. 

5. 2 further problems with particular apps. They both have an icon on the 
desktop, but when I double-click it:

Emacs: produces this message:

This file is executable. Do you want to execute it?

thornq: produces an error: Invalid desktop entry <filename>

whereas most of the icons on my desktop run correctly

I do not think I encountered anything like these problems going from 8.04
to 12. Please any advice?

---

