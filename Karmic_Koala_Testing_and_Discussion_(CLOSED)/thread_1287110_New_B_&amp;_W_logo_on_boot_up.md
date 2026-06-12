---
title: "New B &amp; W logo on boot up"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pt123 on 2009-10-09
it looks slick but provides no indication of anything is happening in the background. Also if there is an error like fsck inconsistency it doesn't break away from the black logo to the error. 
Misleads the user to thinking there computer has frozen. I feel this would be would cause more problems for people trying out Ubuntu for the first time. 

Using Karmic Beta,
Linux tricky 2.6.31-13-generic

---

### Post by Squonk07 on 2009-10-09
When I first saw this I had thought that it was a glitch. Lately the Ubuntu Symbol has been showing up once out of every three shutdowns for me, so I figured it had somehow gotten tacked onto the beginning of the reboot by mistake.

I don't mind the presence of something to cover up the text, though the procession from Ubuntu Symbol to Ubuntu Throbber to GDM to Ubuntu Throbber again to desktop seems too complicated, not to mention that the transitions between these elements have been inconsistent for me--sometimes they fade in, other times they pop jarringly onto the screen. I recognize that this is still a beta, but the fundamental issue is that this procession has too many members. I'd prefer that the Throbber screen immediately show up where the Ubuntu Symbol now does (the animation would assure the user that the machine is indeed doing something), and then remain until the GDM appears. The Ubuntu Symbol should only appear at shutdown or restart.

---

### Post by pt123 on 2009-10-09
It is fine having it on the shutdown, has a nice symbolic touch to it. 

But on the startup if there is an error it should show up the error. 

I really don't mind seeing the bootup messages, it really shows the user how open Linux and Ubuntu is. Yes they can beautify it like how many games do (ET Quake Wars).

You are right there are currently too many items in the boot up process. Some of them could have the same style applied to have continuity.

---

### Post by hanzomon4 on 2009-10-09
I don't want to see those ugly messages especially since the resolution of my ttys are all wrong. A press spacebar to see messages would be nice, so you could check the messages if suspect something is wrong. However seeing them can cause unnecessary panic amongst some and let's be honest most of those ERROR messages are meaningless anyway.

---

### Post by darco on 2009-10-09
Show the logo in the forefront and the scrolling text in the background would be an idea. Or the logo takes up 3/4 of the screen and the remaining screen show the text running.


darco

---

### Post by pt123 on 2009-10-09
> **hanzomon4 said:**
> let's be honest most of those ERROR messages are meaningless anyway.
maybe on Windows but on Linux they are very useful. Even for a Linux-noob it allows them to post the message on a forum like this and are more likely to get better support.

---

### Post by buzzmandt on 2009-10-09
agreed the error should be seen.  I like the idea of 3/4 screen pretty, the rest some text. or all screen pretty, and text breaks into the bottom (or top) small portion if an error is found

---

### Post by emarkay on 2009-10-10
This can be eliminated partially by editing  /etc/default/grub and removing the words "quiet splash", but there is a non-critical bug on this process:
[https://bugs.launchpad.net/xsplash/+bug/439284](https://bugs.launchpad.net/xsplash/+bug/439284)

---

### Post by damava on 2009-10-10
> **pt123 said:**
> Also if there is an error like fsck inconsistency it doesn't break away from the black logo to the error. 
Misleads the user to thinking there computer has frozen.

Yeah I think that should definitely be reported. Does anyone know if there is already a bugreport for that behavior?

---

