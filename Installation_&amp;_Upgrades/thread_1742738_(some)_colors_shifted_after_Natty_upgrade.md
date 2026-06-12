---
title: "(some) colors shifted after Natty upgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Jenda on 2011-04-29
Hi, I just upgraded to Natty and some images display shifted colors, e.g. bright purple instead of yellow and bright green instead of whatever there used to be. Some images also show properly. I attached a screenshot of a bit of Thunderbird where the bug is visible.

Does anyone have any idea what is wrong, or how to diagnose the problem properly?

Thank you in advance &#12484;

EDIT: and, to make this even more interesting, the attachment I made to the forum displays even more ridiculously once it has been attached - I'm attaching a screenshot of that, too. (although right now I have no idea what it looks like on a working machine)

EDIT2: **To reiterate the problem: apparently, Firefox and Thunderbird rotate colors in indexed images for some reason. I am trying to find a way to fix this, with no luck so far.**

---

### Post by Hedgehog1 on 2011-04-29
It appears you have one of the high-visibility themes selected (somehow?!?!?).

Please right click on the desktop, select 'Change Desktop Background', and select the Ambiance theme:

[IMG]http://img846.imageshack.us/img846/4710/screenshotappearancepre.png[/IMG]


Does this correct the wild colors?

***The Hedge***

:KS

---

### Post by Jenda on 2011-04-29
Thanks for the suggestion, but this doesn't help. I noticed two more details:
- It seems to occur only in Mozilla Thunderbird and Mozilla Firefox, or at least I haven't yet seen an example elsewhere (Or didn't recognize it)
- Your avatar shows a BLUE hedgehog here. There's no way a Gnome theme could do that, is there?

Also, it might be related to gnome-settings-daemon, which used to crash before the upgrade (but seems to be working now).

---

### Post by Jenda on 2011-04-29
Also, I checked on another computer - the screenshots I posted above are accurate. Those are really the colors it shows.

It's funny that only some pictures are skewed - when I open the "New York City" article on Wikipedia, most pictures are ok, but the topmost picture on the right is green-purple, as are the pictures of Times Square, Pizza, Marathon, Stock Exchange and Washington Bridge. They are all jpg and I have no idea what the bad ones have in common. It's probably the way each picture defines color? Anyone have any ideas?

EDIT: YES! Using GIMP, I found out that it is only INDEXED pictures, and only in Firefox and Thunderbird. Any ideas what could cause this?

---

### Post by Jenda on 2011-04-30
If I understand this correctly, indexed images use a "color palette" to determine which color to display in each pixel. This probably means Firefox and Thunderbirds' palettes are borked, but it has to be at some low level, since the interface buttons in Thunderbird use the same, wrong, colors.

---

### Post by chinmaykamat on 2011-04-30
Please check [this]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/751067") bug report against unity. Setting gfx.color_management_mode to 0 in about:config has been mentioned as a workaround. Works for me.

---

### Post by Jenda on 2011-04-30
Thank you so much, chinmaykamat! The workaround worked perfectly - I was beginning to worry I was the only one with the problem, since I couldn't find a bug report or support request anywhere. Chose the wrong keywords, I guess.

---

### Post by kernelles on 2012-07-05
> **chinmaykamat said:**
> Please check [this]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/751067") bug report against unity. Setting gfx.color_management_mode to 0 in about:config has been mentioned as a workaround. Works for me.

I had the same problem after a fresh install of Ubuntu 12.04, but strangely only on one of the two computers I installed it on, and yes, only in Firefox and Thunderbird. This workaround fixed it for me in both programs. Thanks!

---

