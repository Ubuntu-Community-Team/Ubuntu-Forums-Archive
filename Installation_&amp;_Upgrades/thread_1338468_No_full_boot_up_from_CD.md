---
title: "No full boot up from CD"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by andrewtoby on 2009-11-26
Hi,
 
I've used Ubuntu before and I have run it from a CD (without installling it).
I have now downloaded 9.10 and find that after the usual screen and initial question, e.g., language, all I then get is a symbol that keeps getting lighter and fading which is then
followed by just a blinking cursor. And nothing else.
Can anyone help please?

---

### Post by sanderj on 2009-11-26
I think you get stuck in the graphical boot screen.

To see what's going on, don't use the graphical boot screen: In the (second) boot screen (so immediately after the language selection), press F6, then ESC, then BACKSPACE x times to delete "quiet splash", then press ENTER.

Then see what happens.

---

