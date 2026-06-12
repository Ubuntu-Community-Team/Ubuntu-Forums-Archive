---
title: "Using GRUB2 and want other OS kernel boot in different resolution"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by cwwilson721 on 2010-09-10
I had only 10.04 installed on my machine, but decided to add Slackware64 13.1 in a dual boot. (I'm a long time Slacker. What can I say? It sure helps when I need to compile or "dive under the hood" in Linux)

I used ```
sudo update-grub
```with no issues. And it added my Slackware install.

However, SW boots with all that text, and I want it at a different resolution. grub currently boots with a 1024x768, and that is what I want SW to boot in. But it boots in 640x480

Ideas? I'd like SW to boot in 1024x768 also

Thanks

---

### Post by grief -l on 2010-09-10
[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

found that with google and was happy to see that it's the same as the boot codes used in tiny core and damn small linux. Hope it helps

---

### Post by cwwilson721 on 2010-09-10
> **grief -l said:**
> [http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

found that with google and was happy to see that it's the same as the boot codes used in tiny core and damn small linux. Hope it helpsThat's for regular grub, NOT GRUB2. There are MAJOR differences

Kind of a pet peeve of mine, answering when the answer is SPECIFICALLY asked.

Anyone with a GOOD answer, that read my post? And the TITLE?

---

