---
title: "Detecting hardware"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by xscript on 2007-03-12
Hi.
I'm trying to install Ubuntu 6.06.1 LTS - Desktop AMD64.
Live CD works. When I initiate instalation everything is fine until hardware detection. Actually, hardware detection starts OK, but when it comes to 93% it stops. The problem is similar to this: [http://ubuntuforums.org/showthread.php?t=4031]("http://ubuntuforums.org/showthread.php?t=4031").

It says, in the solution suggested above, that I should type 'linux noapic nolapic' into the boot prompt. But I'm a newbie; I don't know where boot prompt is.

I had Ubuntu installed from the same CD on the same system few months ago. Installation went smooth then. I added TV card since then but shouldn't be such a problem.

Can someone give me a hint?

---

### Post by dstew on 2007-03-12
Try alt+F4.

---

### Post by xscript on 2007-03-12
When? Where?
When I close the instalation window, nothing happens, if that's what you ment.

Anyway, I found the boot prompt (don't laugh) and wrote 'noapic nolapic' right after 'casper'. It made some difference (I got sound), but instalation still stops at 93%.

Ideas?

P.S. 
Is there a way to find out why instalation stoped; error messages, some log or something?

---

