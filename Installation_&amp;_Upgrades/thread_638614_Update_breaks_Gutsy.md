---
title: "Update breaks Gutsy"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by TMC on 2007-12-12
Hello,

I got a security update this morning - sorry, can't remember exactly what; it was a single file, something to do with 2D vector graphics - and now I can't boot my PC.  I used the GUI updater and everything seemed to go OK, my laptop ran fine afterwards and there were no errors or warnings.  It was when I shut the lid that the problem started - when I reopened the lid all I got was a blank, black screen.  Neither desktop nor password prompt came up and the pointer only appeared if I moved the mouse, flickering and then disappearing again when I stopped moving the mouse.  CTRL-ALT-Backspace took me back to the same situation.  Rebooting takes me through GRUB and the Ubuntu logo / progress bar screen, which wends its merry way to 100% - then I get a blank, black screen with the spinning cartwheel 'I'm doing something' pointer and nothing else happens.  I have left the computer going for about half an hour at this stage with no change.

I am running 7.10 on a Dell Inspiron 510m laptop (currently courtesy of the live CD as I have no other computer and cannot boot into the installed OS).

Any ideas on how I can fix this?  Many thanks, in advance,

David Shaw

---

### Post by TMC on 2007-12-12
Sorry, should have said - this is not the problem that so many of us were having with the experimental Intel drivers - I had that one and had switched to the 810 driver already.

David Shaw

---

### Post by TMC on 2007-12-12
Me again  :-)

After a re-install and update, I have narrowed it down to the libcairo2 update - without this update, everything works OK (-ish, see below).  As soon as I update the file, the problem returns.

However, I was unable to fully test  this as the intel driver resume-from-suspend problem recurred (unsurprisingly) but switching to the i810 graphics driver no longer cures this (which *was* rather surprising), causing the boot to fail with a series of text messages on the screen about running local boot scripts, but then hanging without GDM coming up.  I was able to alt-F1 into a terminal and log in, but don't have enough Linux knowledge to know how to fix the problem.  Frustratingly, the first message on halting the system was that GDM was shutting down  :-S

So I've downgraded to Feisty and everything works like a charm again - not an ideal solution but, hey!  It works! :-)

David

---

