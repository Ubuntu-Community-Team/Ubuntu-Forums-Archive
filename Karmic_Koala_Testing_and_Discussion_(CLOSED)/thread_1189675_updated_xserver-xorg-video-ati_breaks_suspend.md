---
title: "updated xserver-xorg-video-ati breaks suspend"
date: 2009-06-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-06-17
I have an oldish HP Pavilion laptop with an ATI Radeon Xpress 200M 5955 chipset. I have learned that suspend works if I set --quirks-none to true - that's a whole 'nother story in itself.

However, a week or two ago the new version of xserver-xorg-video-ati and -radeon came out (versions 1:6.12.2-2ubuntu1), and messed up my Karmic install - it failed to boot even to the login prompt, with a black screen that could not be unfrozen even with [alt][sysrq]REISUB. After trying to read logs I was still stumped - most logs were full of a dump of package descriptions after a block of @@@@ in reverse video, after an uninformative log of what looked like normal operations.

So I re-installed karmic (well, actually upgraded a clone of my working Jaunty install, for reasons we won't go into here), and it seemed to work better, except that suspend failed to resume, even with --quirk-none set to true. The pm-suspend.log was -- guess what? -- filled with a block of @@@ in reverse video after a normal suspend sequence, but no resume sequence.

I checked versions, and removed the newer -video-ati and -video-radeon packages, then re-installed the earlier (Jaunty) versions, (1:6.12.1-0ubuntu2). Now suspend and resume work fine.

I'm surprised not to see other reports here, but maybe I'm the only one testing Karmic on a 200M 5955 chipset - or maybe there are other problems.... Anyway, it has taken me a couple of weeks to sort this out, so even if it's only me I'll file a bug on launchpad.

---

### Post by zaomaster on 2009-07-02
I will attest to this happening on my thinkpad t30... sigh, the things i put up with to help others out... ;)

---

