---
title: "Monitor Sleep glitch got worse in Lucid"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Uruz on 2010-05-04
You know that glitch where your monitor doesn't come back after switching off for power saving? That's gotten WAY worse since switching to Lucid. It used to happen every other day or so, now it happens 2-3 times a day. Songbird used to keep it from switching off on Karmic, but Songbird doesn't work on Lucid so that's out the window.

Also: as similar error happened when restarting after the glitch happened this latest time. Ubuntu started running its routine disk check and I hit C to skip it. The screen went down like it does in the Monitor Sleep glitch. I reset again, it did it again. Eventually, I just let it do the check. This has NEVER happened before.

Anyone have any advice?

---

### Post by strollerdude on 2010-05-29
I have experienced the same thing in the last few weeks. Sorry, no answers yet.

---

### Post by efflandt on 2010-05-29
Depending upon what video card/chip you have, it might have something to do with the new kernel mode setting (KMS) video drivers.  That was somewhat sluggish on my older system and broke suspend and hibernate.  I fixed that using **nomodeset** kernel boot parameter to use video modules instead.  Now Lucid is as quick as Karmic, and suspend and hibernate work.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by strollerdude on 2010-05-30
Thanks efflandt,
I have added nomodeset to grub2 and will see how it goes. So far so good.

---

### Post by strollerdude on 2010-06-06
Things haven't improved using nomodeset. It seems like there are a few threads trying to find a solution, so let's hope there is one soon.

---

### Post by knuckleheadTech on 2010-10-28
> **strollerdude said:**
> Things haven't improved using nomodeset. It seems like there are a few threads trying to find a solution, so let's hope there is one soon.

I know this thread has gone a bit cold but have you guys found the fix for this yet? I am researching this same problem for a friend.

---

