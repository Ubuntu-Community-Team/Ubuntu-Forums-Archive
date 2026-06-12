---
title: "OpenOffice.org ugly after Feisty upgrade"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by amake on 2007-04-25
Hello.  I recently updated my Edgy installation to Feisty via the alternate CD (and did subsequent net updates).  Everything went fine, except that afterwards I find my OpenOffice.org's UI fonts to be wildly ugly.  I tried searching for other threads about ugly OO.o UI fonts, but none of the tips seemed to work.

One catch is that I run my environment with language ja-JP.  I've attached a screenshot.  Compare to the Nautilus window in the background.

Any ideas?

---

### Post by jgcamp99 on 2007-04-25
USA English OO is just fine for me.

---

### Post by Hagar Delest on 2007-04-26
Perhaps these thread might help :
- [Linux user doesn't like UI]("http://www.oooforum.org/forum/viewtopic.phtml?t=52973")
- [OO 2.0.2 UI fonts look horrible]("http://www.oooforum.org/forum/viewtopic.phtml?t=33084").

---

### Post by rrwo on 2007-04-26
Open an OO application (such as Writer),go to Tools -> Options -> Fonts, and set a font substitution for whatever font it's using.  From reading up on this, it seems to be different for different systems.  On mine, it was "DejaVu Sans". I set it to always replace the font with "Sans" (which I typed in).  Check "always" and "screen".

You might also have to go to Tools -> Options -> View and adjust the scaling and font anti-aliasing.  Possibly restart your X session.

---

### Post by amake on 2007-04-26
I tried replacing the fonts, but I have no idea what the font being used is.  I didn't try restarting my X session, though.  I'll try that.

---

### Post by tuga on 2007-04-30
Hello,

I have the same problem with the fonts on OO 2.2 (AMD64). The other applications are ok. You can see the diference between OO and firefox on the attached screenshot.
I checked several threads but none of them worked...

---

### Post by tuga on 2007-04-30
The solution was here:
[http://ubuntuforums.org/showthread.php?t=406273&page=2](http://ubuntuforums.org/showthread.php?t=406273&page=2)

Change antialiasing from 1 to 25.

Edit: It is even better if antialiasing is disabled.

---

