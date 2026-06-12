---
title: "Ubuntu installation or running without installing hangs opening anything"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by VPenkov on 2010-12-23
Hi.

I read quite a few threads from this forum but couldn't find my solution.

I'm trying to install Ubuntu 10.10 or 10.04.1, however, the installation freezes right on the first window, just before rendering the text which is supposed to be inside.
When I try to run it without installing it, it runs fine; however when I try to open anything, it freezes again.

I've tried the following things:
- Ubuntu 10.10 (i386, x86-64, Netbook Remix) from Wubi, flash drive and CD
- Ubuntu 10.10 alternative install (i386, x86-64) from a flash drive
- Ubuntu 10.04.1 (i386, x86-64, Netbook Remix) from Wubi, flash drive and CD
- Did a Memory test, nothing interesting there

I haven't tried the following things:
- DVD install
- Web install (no idea if Ubuntu has that)
- I don't remember if I tried Kubuntu (doubt it would work, Netbook Remix didn't).

When I enter verbose mode, I can see two interesting errors. One is right at the beginning, something like invalid user ID with uid(0). The second is that it skips some non-existing packages, but I couldn't remember the path. If you think it's important, I can try again and write down the error.

I read that capitalized username causes a similar problem with Wubi, however I don't use a capitalized username, and I've tried other methods that Wubi.

[This]("http://i55.tinypic.com/25s4ugx.png") is my hardware.
I've downloaded the ISO files using the torrents from the official website so they aren't broken.

Here is a video, sorry for the poor quality: [http://www.youtube.com/watch?v=hFakL7wgYzw](http://www.youtube.com/watch?v=hFakL7wgYzw)

---

### Post by zvacet on 2010-12-24
> - Did a Memory test, nothing interesting there

Did you check [md5sum?]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by VPenkov on 2010-12-24
I'm sorry but did you even read my post?
I mentioned torrents - they usually auto-check their md5 sums. So yes. Plus, you can count 7 ISOs in my post.

For now, my progress reaches [so far]("https://bugs.launchpad.net/ubuntu/+bug/531027").

Also, I used the very same CDs/flash drives to install Ubuntu on my home PC and got the same errors but they didn't matter.

---

