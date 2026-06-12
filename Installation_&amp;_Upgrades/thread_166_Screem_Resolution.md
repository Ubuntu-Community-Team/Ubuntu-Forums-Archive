---
title: "Screem Resolution"
date: 2004-10-11
forum: Installation &amp; Upgrades
---

### Post by LongTooth on 2004-10-11
I can't seem to keep my screem resolution. I've set it to 1024x768 and have said 'yes' when asked if I wanted to keep this as default. But it doesn't keep. Any way to work around this? Thanks.

---

### Post by LongTooth on 2004-10-11
Sorry to all, that should read ...screen...not screem. Thanks.

---

### Post by ubuntu-geek on 2004-10-11
Fire up a terminal window and run:

> sudo nano /etc/X11/XF86Config-4
Look for this line: XX will be 16, 24, 32 etc..
> DefaultDepth    XX
Then look for the section to match it: Mine is set to DefaultDepth 24 so mine looks like:
>         SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
This makes 1280x1024 the primary resolution. You can adjust that line accordingly to suit your needs. :)

---

### Post by LongTooth on 2004-10-15
A follow up on this: the recomended solution did not help me at all. I still had to manually set the screen resolution. The last time I did I, for the hell of it, **unchecked** the 'make default for this computer (ubuntu) only' box. That seemed to do the trick. At any rate, I can now power up and my screen is the correct resolution.

---

### Post by AndyGates on 2004-11-29
At last!  I've been banging my head against this same problem (I like to work in 1024x768, but on restart I get 800x600 which is way too small).  I just tried UNchecking the "make this the default" box and whaddya know, it works - the 1024x768 setting stuck perfectly.

Problem solved, another happy convert - but is this a case of counter-intuitive labelling in a dialogue, or is it a bug?

---

