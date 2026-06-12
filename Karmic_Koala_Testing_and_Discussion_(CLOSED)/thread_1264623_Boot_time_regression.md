---
title: "Boot time regression"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by godhika on 2009-09-12
I am fully aware that the people are still working at this point, but I must admit so far the "progress" has been quite disapointing. With every new kernel version, Karmic boots slower for me. I started with 21 seconds around the same time as it was with Jaunty for me) with Kernel 2.6.31-4 and now, with the newest version (2.6.31-10) I am up to 46 seconds To be fair, with the first kernel version I used the radeon driver, and now I use the fglrx driver, which added around 6 seconds for me - but still, even before I used that driver, the boot time already doubled. Is anyone else experiencing such big regressions?

---

### Post by Funnnny on 2009-09-12
Seem different from me. The boot time decrease after each update. The boot time descreasing is noticable with the lastest update ( about 1 days ago )

---

### Post by FuturePilot on 2009-09-12
I just upgraded one of my computers to Karmic and I have noticed that the boot time is definitely slower than Jaunty was. :(

---

### Post by woedend on 2009-09-12
Here as well...from kernel boot to gdm was 17 seconds on jaunty...with all updates fresh karmic install, its in the 35-40 second range...if i remember right this really started in the move from readahead to sreadahead.  That and I do wonder if the graphical splash pre gdm and pre session are slowing things down a bit.

---

### Post by zika on 2009-09-12
In early stages of Karmic testing (before gdm got upgraded) boot-time was perfect. Now it is getting longer and longer to the point where Jaunty was really faster. I hope it will go back to early stages ... But since it is so stable (even though I use many PPA's and stuff from early development) it really does not make a big deal. I know that laptop user would not agree ...
(I'm still happy with the fact that today I managed to enable 3D acceleration on my ATI HD3650 with open-source drivers so that might be the reason I do not take (today) boot time regression seriously ...)

---

### Post by tad1073 on 2009-09-12
Same here. Before, my boot time was about 50 sec. from pushing the power button to a usable system, now it is about 1 min. 15 sec.

---

