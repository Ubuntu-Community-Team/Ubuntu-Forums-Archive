---
title: "icewm: ClickToFocus=0 stopped working [Resolved]"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by dskloet on 2007-05-01
Hi,

I just upgraded to Fiesty (using the update-manager) and now window focus doesn't follow my mouse anymore in icewm. Any idea why that could be?

I have
```
#  Focus windows by clicking
ClickToFocus=0 # 0/1
```
(and more) in $HOME/.icewm/preferences

Any help is very much appreciated,
David

---

### Post by aysiu on 2007-05-01
Have you tried going to Settings > Focus > Sloppy Mouse Focus?

---

### Post by dskloet on 2007-05-01
No, never noticed that. Is it new? I've always been used to using the preference file. It worked, thanks!
Any idea where this is saved, if not in the mentioned file? Strangely enough, I could change the PointerFocusDelay from that file. And I restarted icewm in both cases.

At least it works now, thanks again!

Edit: I guess I found the answer: there's a new file in my .icewm directory called focus_mode with just the following content:
```
FocusMode=0
#FocusMode=2
```

---

### Post by aysiu on 2007-05-01
Yeah, it's a new thing. Thanks for digging up what configuration file it uses.

In IceWM, multiple configuration files can specify the same thing, but sometimes one file overrides another. For example, if you specify a background in the ~/.icewm/preferences file, the background specified by the theme will override what's in the preferences file.

Glad you got it sorted, though.

---

