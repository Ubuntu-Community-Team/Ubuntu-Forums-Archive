---
title: "Endless generating locales"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by marcello on 2008-09-04
Hi guys

I have a 7.10 (Gutsy) and tried to add a language layout (Chinese) using System/Administration/Language Support and the installation was never concluded since it went on for 4 hours with this message

Generating locales...
    zh_CN UTF-8...

My kernel is 2.6.22-15-generic.

I found a bunch of posts reporting similar behaviour when users tryed to upgrade Ubuntu. Some say this is a bug, perhaps kernel related.

I manageg to stop the processor which was going mad by deleting lock files here /var/cache/apt/archives/lock and here /var/lib/dpkg/lock and restarting. To be able to open any update manager tool again I had to delete everything under here /var/lib/dpkg/updates/*.

Here is where I need help: I can't remove the Chinese Language Layout now. I opened Language Support unselected Chinese and the message "Generating locales..." will appear again along with the crazy going processor side effect.

Please advise.

Marcello

---

### Post by marcello on 2008-09-04
Also, as a result of this I am unable to use any updating tool. The locale is queued for apt and I don't know where the queue is stored. As soon as the updating is started I get stuck with the message "generating locales...".

Another thing is the localedef process runs and I cannot kill it! But that seems to be a already known fact.

Please help.

---

### Post by marcello on 2008-09-15
Anyone?

---

