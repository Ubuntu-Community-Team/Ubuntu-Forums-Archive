---
title: "Hard-lockups"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-02-22
Is anyone else still experiencing occasional hard-lockups in Lucid? Perhaps once or twice a day I get a hard-lockup when launching a project in Eclipse or just doing other tasks.
I read about people experiencing problems when pressing enter, and this appears to be when my problem occurs, but it is not all the time?  
Cheers,
JC

---

### Post by zika on 2010-02-22
Try purging plymouth. That solved all main problems to me. Except shutdown...

---

### Post by JCoster on 2010-02-22
Cheers for your quick response.  Is plymouth not required?

---

### Post by VMC on 2010-02-22
> **JCoster said:**
> Cheers for your quick response.  Is plymouth not required?

You can boot without it, but your suppose to be able to boot using it.

Read my [**bug#521175**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521175") to get an idea of what's happening. There's several open bug reports on Plymouth

---

### Post by zika on 2010-02-22
> **JCoster said:**
> Cheers for your quick response.  Is plymouth not required?No, as far as I'm concerned, at this moment of development, not that it is not required, it is not desired... I can not remember a piece of SW that made so many problems, even though it is "needed" only at boot and at shutdown, as far as I'm concerned, for cosmetic purposes... OK, I'm in a tinny minority but, I unloaded that from my chest... Sorry...

---

### Post by emarkay on 2010-02-22
> **zika said:**
> "...as far as I'm concerned, for cosmetic purposes... OK, I'm in a tinny minority but..."

Yea, strange we are just a smidgen of Ubuntu users, apparently.
Those of us that want stability, security and flawless core OS performance, anytime anywhere; before any "dog and pony show" "gee whiz" bovine feces that just gets in the way of real productivity and credibility...

---

### Post by zika on 2010-02-22
I was having a great week without freezes with KMS (after I've got rid of plymouth) but, just minutes ago, one struck again. Now I'm back to no-KMS... So, purging plymouth is not the magic pill. There is something else rotten in this garden...

---

### Post by JCoster on 2010-02-22
Yeah, I don't think it's so much an issue with Plymouth as something deeper within the system..?

---

### Post by sirkeith on 2010-02-22
For me Plymouth is a no-no. But even after removing it there has been some stuff seems odd. Oddest is having Firefox return after removing it. But my machine works better once I get Firefox off the system. I am really enjoying my Lucid at this point in time.

keith

---

### Post by zob on 2010-02-22
I also had a sudden crash though I had removed plymouth.

But then I discovered that some recent update auto-installed plymouth on my system and now with a sibling: plymouth-x11.

So I uninstalled both of them, and I'm crash-free once again.

I hope all the problems it makes will be worth it. At this moment I don't see the point either.

---

### Post by voidmage on 2010-02-23
I've also had hard lockups basically at random. Sometimes I get them right after logging in several times in a row, other times they're 6 hours apart. I had a similar problem in karmic that was fixed by changing my nvidia driver from 195 to 190. Except that the 190 driver isn't packaged in lucid anymore. This worked for my nvidia GT 240, has anyone else had a similar thing?

---

### Post by JCoster on 2010-02-23
I had about 5 lockups yesterday (was working all day) and have experienced one today.

Everyone else only seems to be experiencing problems with nvidia cards whilst i'm on an ATI?

Has anyone else with an ATI experienced a hard lockup?
(by hard I mean that I cannot do anything- the mouse can be moved but literally nothing else works, not even switching to a tty)

---

### Post by zika on 2010-02-23
> **JCoster said:**
> I had about 5 lockups yesterday (was working all day) and have experienced one today.

Everyone else only seems to be experiencing problems with nvidia cards whilst i'm on an ATI?

Has anyone else with an ATI experienced a hard lockup?
(by hard I mean that I cannot do anything- the mouse can be moved but literally nothing else works, not even switching to a tty)I'm with ATI and I'm having these, I call them freeze, for quite some time. My solution was to switch KMS off. I had a peaceful period, using KMS, last week, then freeze came back this weekend. I'm now on KMS and I'm just waiting next freeze... Even if it doesn't come, just the fact that I'm fearing from it is not a good sign... But, I really believe it will be solved, and that culprit lies in GTK, as I was told on Phoronix, and have done some research, as far as my (sparse) knowledge permits...

---

