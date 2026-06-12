---
title: "Newly upgraded - when i log in, nothing happens"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by kstella on 2007-11-06
Last night, I upgraded from 7.04 to 7.10 using the Update Manager. I left my computer alone and did other things; as far as I can tell, downloads and installation were uninterrupted so I assumed everything went smoothly. But now, when I log in, nothing happens after the startup screen disappears. The drums play, but there's no splash screen, just a big, flesh-colored blank screen - it just stops there.

Could someone please lend me a hand? My friend recently upgraded and is thrilled; he told me to expect some great stuff. :(

---

### Post by kstella on 2007-11-06
This is from the release notes and sounds close to my problem:

[INDENT]People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. Bug #132716[/INDENT]

I'm afraid I didn't understand it completely. :/ In any case, if it's a problem with my graphics card, according to the Device Manager in Windows, it's an S3 Graphics ProSavageDDR. It came with my computer package.

Also, I did happen upon another post regarding the blank screen and ATI display adapters, but he said it was a **black **screen. So... this might not apply to my problem after all.

Anybody? Just so you know, I'm still pretty new at these things. I first installed Ubuntu only a few months ago and was pretty happy getting around with a mouse; I've only just begun learning to use the terminal.

---

### Post by kstella on 2007-11-07
Here's an update: it works when I log in using Failsafe GNOME. And it's preeeeeetty! :D Won't consider this solved till I'm sure it's solved, of course.

---

### Post by bulldog on 2007-11-07
I think you mean recovery mode instead of failsafe?
Anyway did you install a graphics driver for the ATI card yet?

---

### Post by kstella on 2007-11-07
Er... is the S3 an ATI card?

I mean when the startup screen came, I changed the session to Failsafe GNOME before logging in; I remember someone recommending that once.

Thanks for replying, btw. :) I was starting to think I was talking to myself.

---

### Post by bulldog on 2007-11-07
Nope it's not,I didn't read your second post till the end,my mistake.

Well this can be hard because I don't know a thing about your graphics :(
Had to deal with ATI and nvidia but never with something exotic as that one.

Did you do a search on the forum if there are more users of this graphics?

---

### Post by kstella on 2007-11-07
I seem to be the only one. I'm starting to think, though, that the graphics card isn't the problem. What else do you think it could be?

Oh, and someone posted with a similar problem to mine [here]("http://ubuntuforums.org/showthread.php?t=602683").

---

### Post by kstella on 2007-11-10
SOLVED... sort of. After I first logged in using the Failsafe Mode, things now boot up in default mode fine. Still no splash screen, though.

I should be happy (and I am :D), but I'd still like to know: what happened? And why do I still have no splash screen?

---

