---
title: "Fonts not refreshing in OOO Writer?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tweak42 on 2009-04-08
Has anyone experience font refresh rendering problems with OpenOffice Writer?

While I'm typing and editing a my term paper, refreshes such as deleting a single character or moving a paragraph don't appear automatically.  I must do something to force refresh the screen such as alt-tab away-back, hit ctrl-shift-r or page up-down for text to appear right.  

It didn't happen while I was typing this post in firefox or text editor and I discovered turning **[Visual Effects: None]** seems to fix it.

Details: OpenOffice 3.01, Nvidia 180.44 closed source drivers, mscorefonts

---

### Post by FuturePilot on 2009-04-08
It's a known bug
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904")

---

### Post by Tweak42 on 2009-04-09
Thanks for the tip.

I didn't experience any refresh problems in FireFox, Text Editor, Nautilus file manager, or xterm.  I don't normally have the effects turned on, but they were enabled when I upgraded to Jaunty.  I'll try to run some more tests and file a bug report when I have time.

---

