---
title: "Stuck on blank screen with mouse cursor"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by Skyler0 on 2009-12-23
So I'm trying to install Ubuntu 9.10 and I'm having an odd problem. I tried searching but couldn't finda anything.

When I try to install or load the live CD for the disk, it starts to load a bit but then goes to a black screen with a mouse cursor on it. The mouse cursor functions and I can move it around.

I've tried different hard drives, testing the disk, and unplugging all the USB ports and what not.

I'm really hoping someone knows how to help :/

Thanks,
Sky

---

### Post by BZiadie on 2009-12-23
I just wanted to say that I'm having the same problem. Trying to install Ubuntu Netbook Remix on an ASUS EEE PC 1000HE from a USB.

---

### Post by byStanderone on 2009-12-23
...try this thread, i think it is related your problem:
[http://ubuntuforums.org/showthread.php?t=1308941](http://ubuntuforums.org/showthread.php?t=1308941)

---

### Post by Skyler0 on 2009-12-23
Alright

Update:

I booted the install with that line from the other thread, and in graphics safe mode. Worked fine all that jazz.

I install Ubuntu, and NOW when I boot it normally it still boots fine. Not sure why though :S.

I noticed some of the command line stuff that came up right before the black screen with mouse and it said over and over a few times:

"ata2.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6"

Not sure what it means, but seems to be working now I guess.

Thanks :P
-Sky

EDIT: After a few more testing it looks like it the Safe Graphics option that is letting it boot, not the i915.modeset=0. Any idea why?

Hardware:
P4 3.0 w/ HT
AGP ATI HD3650
1.5GB DDR Ram
(yes I'm aware its a little old haha)

---

### Post by byStanderone on 2009-12-27
...have a look at this: [http://omgili.com/hd3650-mobility-radeon](http://omgili.com/hd3650-mobility-radeon)

specially that one marked as 'solved'

---

### Post by Skyler0 on 2009-12-27
Thanks, but it works now without having to do anything weird, and if I'm booting Live CD I just use the graphics recovery. 

Also, its not the mobile version, but the desktop version.

---

