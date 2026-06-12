---
title: "Recent update in 10.04 messed up my fonts in Chrome."
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by ernied on 2011-01-31
I'm running Ubuntu 10.04 LTS on my workstation at work. 

I believe that there was a recent update to the Cleartype fonts, and now I have a lot of trouble with fonts in Chrome. This appears not to affect Opera, but for various reasons I don't use Opera. I don't have the kind of RAM necessary to run both browsers at once either (there's a lot of other windows and programs running concurrently, thanks!), so that easy option isn't really available. 

The specific problems I'm seeing in Chrome are that Horde Groupware (which coincidentally, has no options for fonts and font sizing internally) is suddenly very, very small, and the same goes with several other important web pages (like Munin) which appear to rely on some system defaults. Horde is of course, critical to my job.

The other natural solution is to "zoom" the pages within Chrome, but that doesn't affect just the fonts, and can dramatically change the appearance and usability of the sites in question. Increasing default font sizes within Chrome doesn't appear to have much if any effect either. Even using 16 point fonts doesn't change anything in Horde, which appears to be using about an 8 point font.

Other than that, the fonts look pretty good.

---

### Post by I_can_see_the_light on 2012-01-11
So it's just that the fonts are small? I've not seen that myself but there is a problem with font rendering in newer versions.

[http://code.google.com/p/chromium/issues/detail?id=96926](http://code.google.com/p/chromium/issues/detail?id=96926)

Have you tried changing the "Minimum font size" in Chrome's preferences?

---

