---
title: "please help install flyingwindows; lack screenhack.h"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by blesbok on 2012-11-05
Flyingwindows is intended for xscreensaver but it wouldn't compile. Before getting into that, on my Ubuntu 12.04, every existing xscreensaver file seems to have a binary in **/usr/lib/xscreensaver** and an xml file in **/usr/share/screensaver/config**. There's no xml file to be seen after untarring.

Here's what I did:
Copied the flyingwindows-0.2 folder into the /usr/share/xscreensaver directory. Linked the file there: ```
./link.sh /usr/share/xscreensaver

```
make gave this output:
```
gcc -O2 -Wall -I/usr/X11R6include -I/usr/X11R6/include -DUSE_XPM   -c -o flyingwindows.o flyingwindows.c
flyingwindows.c:38:24: fatal error: screenhack.h: No such file or directory
compilation terminated.
make: *** [flyingwindows.o] Error 1
```

Any tips, please?

---

