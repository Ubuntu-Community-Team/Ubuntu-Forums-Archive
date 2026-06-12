---
title: "upgraded to compiz 0.9.2 and totem kills the display"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by fazza on 2010-11-17
Not sure if I've put this in the right forum, maybe it should be under development...

Anyway - earlier today, I used [this]("http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html") guide to upgrade my compiz from 0.8.6 to 0.9.2. After a few hiccoughs, I eventually got it to run purrrrrrfectly.

Except for one problem. Totem will -not- work. I open any file that uses it, and it will freeze. The file will play - I can hear it - but the display freezes entirely (except for the cursor).

I can open totem from the menu, but as soon as I open a file, it again freezes. I thought maybe it was a video colourspace issue (the YV12 option isn't in the new ccsm), but VLC works fine. I haven't yet tested video in banshee, which I believe uses gstreamer, so I guess that might be the problem.

And for the record, totem does work in recovery gnome, where compiz is replaced by metacity.

After the big freeze, I can switch to a console, and kill totem from there, but I cannot switch back to graphic mode, as the display is dead. I can't kill compiz from the console, whether I use "killall compiz", "sudo .." or kill it using the PID via top. Sometimes it even ends up running twice.

Whatever the case, the point it is doesn't work. Which you could say is annoying. But it isn't intended to run on 10.10, and the guy on the howto who recompiled the code for 10.10 said he hasn't tested it on 64-bit. 

Just thought it would be worth mentioning :) Did a quick google and couldn't find anything particularly helpful.

---

