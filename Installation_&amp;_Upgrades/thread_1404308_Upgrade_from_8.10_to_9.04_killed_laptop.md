---
title: "Upgrade from 8.10 to 9.04 killed laptop"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by boomcat on 2010-02-11
I have an ancient laptop, an IBM T-20 with a Pentium 3 and 250 megs of RAM, which works great for blogging and email. I have used Ubuntu on it for nearly four years now. 

Last night I upgraded from 8.10 to 9.04 and now it won't get to the log-in screen. The BIOS splash screen appears, then the GRUB screen, then the Ubuntu trademark screen appears, with the horizontal progress indicator scrolling from left to right. And when it gets all the way to the right, the screen goes blank. Then the screen flashes twice, as if it's trying to display in a resolution it doesn't support, and then it goes blank again. The HD activity light flashes about every five seconds and the keyboard is unresponsive.

Powering off and on again just repeats the process.

Any ideas?

---

### Post by dabl on 2010-02-11
It does sound like a video display issue.  You might try the "xforcevesa" boot option, along with the other most likely options.

However (to point out the obvious), there comes a time for every ancient hardware platform that still "runs", that its ability to support a brand new OS is too compromised to bother with.

I'd try Xubuntu and maybe the Netbook Remix, if you're up for experimentation.  If they don't work, I guess it's slax for you.  :D

---

