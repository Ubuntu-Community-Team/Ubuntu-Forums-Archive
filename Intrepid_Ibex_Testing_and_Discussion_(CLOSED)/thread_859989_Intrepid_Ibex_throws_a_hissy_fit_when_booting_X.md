---
title: "Intrepid Ibex throws a hissy fit when booting X"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by joeinnes on 2008-07-15
On booting Intrepid Ibex, there seem to be no problems up until the greeter is started. Then, the stopwatch rotates for a turn or two, and hangs - although not completely. The mouse moves every minute or so, catching up to where it ought to be. If the mouse is moved before the screen hangs, then it hangs immediately. The only button that works is the power button (ctrl+backspace, switching to a different console, etc. all don't work).

However, if I boot into the previous kernel, I get a message along the lines of "Greeter application seems to be crashing" if I wait a while, and if I drop into a different console, I can run startx, which boots me into a fully working desktop. Any suggestions?

---

### Post by overdrank on 2008-07-15
> **joeinnes said:**
> On booting Intrepid Ibex, there seem to be no problems up until the greeter is started. Then, the stopwatch rotates for a turn or two, and hangs - although not completely. The mouse moves every minute or so, catching up to where it ought to be. If the mouse is moved before the screen hangs, then it hangs immediately. The only button that works is the power button (ctrl+backspace, switching to a different console, etc. all don't work).

However, if I boot into the previous kernel, I get a message along the lines of "Greeter application seems to be crashing" if I wait a while, and if I drop into a different console, I can run startx, which boots me into a fully working desktop. Any suggestions?

HI and yes intrepid will break and is not meant to be used as a everyday system. You look here
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by cszikszoy on 2008-07-15
It may be best to post this in the development forum here: [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by joeinnes on 2008-07-15
*facepalm* Yep, sorry, will repost in the development forum.

Apologies

---

### Post by overdrank on 2008-07-15
> **joeinnes said:**
> *facepalm* Yep, sorry, will repost in the development forum.

Apologies

No need to repost just use the report button and ask it to be moved. :KS

---

### Post by Kevbert on 2008-07-15
One thing to try is boot into recovery mode and use some of the new tools that are supplied there.  In Intrepid, reconfiguring xorg.conf will make very little difference to your problem.

---

