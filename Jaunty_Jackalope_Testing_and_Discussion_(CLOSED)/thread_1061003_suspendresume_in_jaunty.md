---
title: "suspend/resume in jaunty"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-02-05
I've got a Thinkpad T30 that is having issues waking up from suspend in Jaunty. Things have worked just fine in other 'stable' releases, so I want to be able to post the issue to launchpad, but I don't know what log to look at to help them.

Any thoughts about where to look?

Any ideas on what the issue might even be?

Thanks.

---

### Post by Slug71 on 2009-02-05
I think this has been an issue for a while with previous versions too.
I think there is a fix for it in the 2.6.29 Kernel.

---

### Post by biasquez on 2009-02-05
one question: i have 768 mb for ram and 500 mb for swap. hibernate doesn't work...is it normal?

---

### Post by Nathan_M on 2009-02-05
> **biasquez said:**
> one question: i have 768 mb for ram and 500 mb for swap. hibernate doesn't work...is it normal?

Yes... when your computer is powered down, everything stored in the RAM (the session) is lost. When you hibernate, the computer copies the session from the RAM to the swap, then restores it when you power up. So you need at least as much swap as you have RAM. Actually, you need considerably more, because your computer sometimes uses swap as a substitute for extra ram, so you need space for that too. I think the guide is 1.5 - 2 x your RAM... so for you, 1.2 - 1.6 Gb swap.

---

### Post by Slug71 on 2009-02-05
Nathan beat me to it but yes he's correct.

You should have about 1200mb - 1536mb for swap.

---

