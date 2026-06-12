---
title: "fbsplash-0.9.2-r5-2.6.20-rc6 problem applying patch"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by dschaefer79 on 2007-07-22
Hi,

I've successfully applied uvesafb patch on my own kernel compil 2.6.22.1 and now I try to apply the fbsplash-0.9.2-r5-2.6.20-rc6.patch on my 2.6.22.1 x64 kernel. But I get these error
Can anyone help me thanks.

[http://dev.gentoo.org/~spock/projects/gensplash/](http://dev.gentoo.org/~spock/projects/gensplash/)

patching file Documentation/fb/00-INDEX
patching file Documentation/fb/splash.txt
patching file drivers/Makefile
patching file drivers/video/Kconfig
Hunk #1 succeeded at 1075 (offset 191 lines).
Hunk #2 succeeded at 1868 with fuzz 1 (offset 211 lines).
patching file drivers/video/Makefile
Hunk #1 FAILED at 13.
1 out of 1 hunk FAILED -- saving rejects to file drivers/video/Makefile.rej
patching file drivers/video/cfbsplash.c
patching file drivers/video/console/bitblit.c
patching file drivers/video/console/fbcon.c
Hunk #1 succeeded at 90 (offset -1 lines).
Hunk #2 succeeded at 106 with fuzz 2 (offset -1 lines).
Hunk #3 succeeded at 303 (offset 1 line).
Hunk #4 succeeded at 411 (offset 1 line).
Hunk #5 succeeded at 577 (offset 1 line).
Hunk #6 succeeded at 1022 (offset 38 lines).
Hunk #7 succeeded at 1111 (offset 38 lines).
Hunk #8 succeeded at 1307 (offset 40 lines).
Hunk #9 succeeded at 1331 (offset 40 lines).
Hunk #10 succeeded at 1355 (offset 40 lines).
Hunk #11 succeeded at 1834 (offset 40 lines).
Hunk #12 succeeded at 1922 (offset 40 lines).
Hunk #13 succeeded at 2066 (offset 40 lines).
Hunk #14 FAILED at 2143.
Hunk #15 succeeded at 2181 (offset 40 lines).
Hunk #16 succeeded at 2218 (offset 40 lines).
Hunk #17 succeeded at 2256 (offset 40 lines).
Hunk #18 succeeded at 2376 (offset 47 lines).
Hunk #19 succeeded at 2532 (offset 47 lines).
Hunk #20 succeeded at 2676 (offset 58 lines).
Hunk #21 succeeded at 2702 (offset 58 lines).
Hunk #22 succeeded at 2970 (offset 58 lines).
Hunk #23 succeeded at 3465 (offset 88 lines).
1 out of 23 hunks FAILED -- saving rejects to file drivers/video/console/fbcon.c.rej
patching file drivers/video/fbcmap.c
patching file drivers/video/fbsplash.c
patching file drivers/video/fbsplash.h
patching file include/linux/console_splash.h
patching file include/linux/console_struct.h
Hunk #1 succeeded at 19 (offset 4 lines).
Hunk #2 succeeded at 106 (offset 7 lines).
patching file include/linux/fb.h
Hunk #1 succeeded at 11 (offset 2 lines).
Hunk #2 succeeded at 45 (offset 2 lines).
Hunk #3 succeeded at 843 (offset 41 lines).
patching file include/linux/sysctl.h
Hunk #1 succeeded at 165 (offset 5 lines).
patching file kernel/sysctl.c
Hunk #1 succeeded at 89 (offset 2 lines).
Hunk #2 succeeded at 346 (offset -110 lines).

---

