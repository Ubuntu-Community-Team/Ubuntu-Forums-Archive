---
title: "DVI output screwy; VGA is OK"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Aikon- on 2010-03-27
Hi everyone,

I just built a new computer and decided that I may as well start with the Lucid Beta, since I have never really had much luck with dist-upgrades. I had a hard time getting it installed due to a bug in Ubiquity in the current daily builds, so I went all the way back to Beta1 and did an install followed by full apt-get update and apt-get upgrade.

My video card has two DVI outputs. When I booted the LiveCD using either of these DVI outputs, the screen was shifted (I'll try to explain more below), so I used a DVI->VGA adapter for the install, which worked fine. Now I am trying to get my installed system to use the DVI ports correctly, since I don't like the fuzziness caused by VGA (either bad DACs on the video card or bad ADCs on the monitor), but I can't seem to get it to work.

Basically the problem is this: It appears that the screen resolution is the correct 1920x1200 when using DVI, however the monitor is not recognizing this -- it shows a cropped area of the expected screen that does not fill the full monitor. On second thought, I've taken a [picture of this]("http://media.thebadness.org/starbuck/lucid.jpg") to show you what I mean. You can see how the login windows is shifter further left than it should be, and how the screen only fills a square-ish portion in the centre of the monitor.

All of the BIOS screens show fine, but they are running at a lower resolution. The virtual terminals are also shifted the same way; if I login using one of those and do `ls -la', the first column I can read is the minutes of the modified time.

Any and all suggestions welcome.. I would really /really/ like to get DVI up and running as VGA is hurting my eyes =(

-Aikon

---

### Post by Killigrew on 2010-03-27
Hi

Would you mind telling us which graphics  adapter you use?
and which drivers are loaded?
otherwise it is nearly impossible to help you ;)
i have an Ati x1400 with radeon driver and sometimes, if i get strange Graphic Effects on DVI, 
i switch to Shell via Strg+Alt+F1 and back to Desktop via Strg+Alt+F7.
If your card is supported you can try the proprietary graphics drivers, 
if not, you can try the xorg edgers ppa perhaps this solves your problem.

greetings from germany

---

### Post by Aikon- on 2010-03-27
Sorry, I meant to post system specs and it slipped my mind:

Intel Core i7 860
ASUS P7P55D-E
ATI Radeon HD 4650

The driver is whatever Ubuntu loads as a default; this happens identically in both the LiveCD and my fresh install. I have not tried installing or changing the drivers yet in any way. When I look at "Hardware Drivers", it just says "No proprietary drivers are in use on this system", and the list is completely empty.

If there is some other specific information that would help diagnose the problem, please let me know and I'll grab it.

I tried switching back and forth from the shell but to no avail; the shell actually exhibits identical behaviour (next time I boot up the machine I'll grab a picture of that as well).

-Aikon

---

### Post by Aikon- on 2010-03-29
OK, I haven't made any progress on this other than to narrow down the issue to Lucid. Here is some further information:
[LIST=1]
[*]This monitor shows correctly using DVI on old desktop computer running Karmic
[*]This monitor shows correctly using DVI on this new computer running Windows 7
[*]This monitor shows correctly using VGA on this new computer running Lucid
[*]This monitor shows **incorrectly** using DVI on this new computer running Lucid
[/LIST]

I have taken some better images that should be more useful; the first is a screenshot of what the desktop *should* look like; the second is a picture of the monitor (with flash this time) **without changing anything** on the screen; you can clearly see how the output is off-center and not fully displayed, even though the resolution is correct.

[Picture]("http://media.thebadness.org/starbuck/picture.jpg") | [Screenshot]("http://media.thebadness.org/starbuck/screenshot.png")

Anyone have any other ideas?

-Aikon

---

