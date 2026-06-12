---
title: "X Hangs after fresh install"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by rhat on 2005-05-25
Hi Everybody,
I've just done a fresh install of 5.04, and I'm getting a problem. The screen seems to blank out and hang whenever X would start. Not only that, but I can't switch back to the console or C-M-Bksp to kill X either. Now, I haven't seen any error dumps, so I'm guessing this is some sort of config problem... does anyone know how to fix this?

Thanks,
Ryan

PS: Just let me know if you need any more info and I'll post whatever specs you need.

---

### Post by rhat on 2005-05-25
After logginf in as root in safe mode I have found that X is spitting out the following error:
```
X: user not authorized to run the X server, aborting.
``` 

I googled around for solutions to this (including dpkg-reconfigure xserver-xorg and changing groups, etc.), but all that accomplished was to foul up the group profile for my login (due to my own incompetence, and not reading the man page throroughly enough  :-P ). 

So, I'm still not sure what the problem is

---

