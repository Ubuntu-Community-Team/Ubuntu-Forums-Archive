---
title: "My screen looks garbled when I try to install! Help!"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Ruge1X on 2008-11-14
Hey again,

Finally got the Ubuntu 8.10 to try to install, but its hard to install when I see the screen like this!!

[http://img528.imageshack.us/img528/6445/img0039mediumlj3.jpg](http://img528.imageshack.us/img528/6445/img0039mediumlj3.jpg)

But in "safe mode" everything is okay..

any tips?

---

### Post by damis648 on 2008-11-14
I had that exact same problem when I tried to install on a laptop I have lying around! Inspiron 8000 series, right? :popcorn: Press Fn+F7.:popcorn: I think there is an xorg.conf fix but that will at least get you through the installation.

---

### Post by Ruge1X on 2008-11-14
Roflmao yes! Dell Inspiron 8000! Hahaha that worked! but it looks tiny now! Is there a way, following installation, that I can get it to occupy the entire screen?

---

### Post by damis648 on 2008-11-14
> **Ruge1X said:**
> Roflmao yes! Dell Inspiron 8000! Hahaha that worked! but it looks tiny now!

Press it a second time, it should get big again. My Inspiron's HDD went bad after I installed Intrepid so I never got a chance to find a permanent fix so I don't have to do that every boot... I will look for it now and let you know what I find. (Let me know if you do too, I will need that if I end up buying a new hard drive for this...):popcorn:

EDIT note: It is small, by the way, because the graphics card driver isn't loaded, so it is displaying in 640x480. That font key resets the display, fixing that display problem, as well as change the display setting so that small resolutions display small on this 14XX something by 12xx something display (can't recall). Pressing it again makes it big. Once you get the video driver loaded, though, it won't get small when you do that and set it to maximum resolution.

**ALSO!:**When I tried to install Ubuntu on this, the network card did not show up. At all. Not even in lspci or anything of the sort. Maybe some updates fixed that, but AFAIK it still doesn't work. You would have to get a PCMCIA card for it.

---

### Post by Ruge1X on 2008-11-14
Thanks for that mate, its now installing with me knowing whats going on lol! I hope the GFX card is detected and that I can get it on the native res but ill search the net for any fixes..

Hmm network card issue, well im dual-booting so I can use WinXP for the use of the network card, but I do have a D-Link wireless card which i hope will work on Ubuntu!

**EDIT:** Hmm my install seems to have frozen at the "Copying files.." section, at 55%. I can move the mouse but it won't progress...

---

### Post by damis648 on 2008-11-14
Poster #5 seems to be pretty knowledgeable about the video issue here:
[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

Glad I could help btw! :guitar:

---

### Post by damis648 on 2008-11-14
> **Ruge1X said:**
> **EDIT:** Hmm my install seems to have frozen at the "Copying files.." section, at 55%. I can move the mouse but it won't progress...

Hmm... wait a bit and see if it moves. If it doesn't in fifteen minutes, then we have a problem.

---

### Post by Ruge1X on 2008-11-14
Yikes, no cigar.... thats odd, just wont progress!

EDIT: yep completely frozen, cant move the mouse anymore either.

Could it be that ive runn out of space of my C: this is how im setting up

C: [10GB Max, say 4GB free]
E: [10GB Max, Ubuntu goes here!]

Edit 2: Also when I do a Safe-Mode install, it freezes after [140.530648] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8

---

### Post by damis648 on 2008-11-14
> **Ruge1X said:**
> Yikes, no cigar.... thats odd, just wont progress!

EDIT: yep completely frozen, cant move the mouse anymore either.

Could it be that ive runn out of space of my C: this is how im setting up

C: [10GB Max, say 4GB free]
E: [10GB Max, Ubuntu goes here!]

Edit 2: Also when I do a Safe-Mode install, it freezes after [140.530648] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8

That is odd... i wish I would offer some input on this, sorry. I will bump it though. :guitar:

---

### Post by Ruge1X on 2008-11-14
No worries dude, thanks for your help on the GFX issue, ill play around and see what I can do with this. Cheers.

---

