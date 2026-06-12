---
title: "gutsy images broken or what does it mean -&gt; no installation"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by SleepyHollow on 2007-10-28
Hi Folks,

I'm verry astounded about this problems with the actual gutsy images. I tried:

 ubuntu-i386-desktop (installation failed)
Kubuntu-i386-alternate (installation failed)
->the last with two different images from different locations

I can't install all of the packets and I can't install lilo or grub.

My hardware: I used a laptop amilo L1300, on which was installed Ubuntu warty, breezy, edgy, feisty without problems (except the intersil/prism wlan). Now I tried gutsy and find: this is really a pain in the ***. I tried after this mess the good old debian etch: It installs and runs.

Hey, whats it all about. I liked Ubuntu and I would run it too in the future. Please fix this problems. The Live-System is running like a charm and my ugly prism54/intersil rubbish is running out of the box.

Why doesn't work the installation on my hd?

Greetings
SleepyHollow

---

### Post by Pumalite on 2007-10-28
Funny, I have Gutsy installed in 5 computers and laptops. Never a problem. Clean your burner or read this:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by SleepyHollow on 2007-10-28
**Funny, I have Gutsy installed in 5 computers and laptops. Never a problem. Clean your burner or read this:**

No way, I checked cd-integrity and the mdsum-hash. All was okay, except for the installation procedure. There is something different. Something has changed.  Something went really wrong.

Greetings,
SleepyHollow

---

### Post by Pumalite on 2007-10-28
Something wrong with your hardware maybe.

---

### Post by SleepyHollow on 2007-10-28
**Something wrong with your hardware maybe.**

No, I don*t think so: I tried it once more with the Ubuntu- Desktop-i386 and now I got an idea. The behavior is exactly like this. I started the installation procedure on the Xwin-Gnome-Desktop. It worked and installed packets until 70% or so and then nothing. I see only the Gnome and nothing else. No installation-window, the desktop-icons are disappeared.

 I changed from Xwin to virtualconsole and there it comes

SQUASHFS error: Fail reading block list <offset-address>
SQUASHFS error: sb_bread failed reading block <offset-address>

This error message is within an endlos loop. As I said before: I installed real debian (etch) without any installation problems. Maybe I should install it again and whistle on the wlan rubbish. It simply works.

:confused:

ps: new variation, tried to shutdown gnome and saw really psychedelic colors on the screen.

---

### Post by Pumalite on 2007-10-28
In Ubuntu; when the Live CD does not work in your hadware, you should always install with the Alternate CD before you give up. That's what the Alternate is for.

---

### Post by SleepyHollow on 2007-10-28
**n Ubuntu; when the Live CD does not work in your hadware, you should always install with the Alternate CD before you give up. That's what the Alternate is for.**

Kubuntu-alternate failed too. :(

---

### Post by Pumalite on 2007-10-28
You need a new computer.

---

### Post by SleepyHollow on 2007-10-28
> You need a new computer.

This is ridiculous! Now at this moment, i have running debian etch with gnome and without any error message again on the same laptop which refuses Gutsy.

Thats it for me. Ubuntu 7.10 is to buggy at the moment.  I find an arrangement with debian etch. I won't use gutsy for my productive setup. This would be too risky.

I'm wondering about this release: it seems to be bleeding edge. :mad:

Greetings 
SleepyHollow

---

