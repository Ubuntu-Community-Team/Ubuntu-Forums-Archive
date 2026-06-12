---
title: "Installing ubuntu... quick question"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by botulismo on 2007-04-13
I'm installing Edgy and I'm having a little problem. When I installed Kubuntu, the x server fails to start and it kicks me right back to the command prompt. This is all well and good, because all I do is type in sudo apt-get install xorg-driver-fglrx , aticonfig --initial, and startx...

I'd installed ubuntu before, and when the x server fails to start, it gives me the blue screen but instead of kicking me to the command prompt, it does nothing. So, I was told some command combination (ie Shift, Ctrl, or Alt and some other key) that would bring me to the command prompt.

The question is: What is that combination?

I was trying to install Feisty beta clean but a.) it did the same thing, wouldn't allow me b.) when I installed in safe graphics mode and then did the sudo apt-get install xorg-driver-fglrx and aticonfig the whole dang thing just broke... I guess I did something wrong... Well, that's another question for another forum.

---

### Post by mac.ryan on 2007-04-13
> **botulismo said:**
> The question is: What is that combination?

On a working ubuntu system (and many other GNU/Linux distro):

```
CTRL-ALT-F*X*
```

where *X* from 1 to 6 are text consoles while 7 is the one where the ubuntu X session should be running.

BTW: have you tried to run in failsafe mode? If you are doing it from Edgy liveCD, mind [this known issue]("https://wiki.ubuntu.com/EdgyKnownIssues/59618").

---

