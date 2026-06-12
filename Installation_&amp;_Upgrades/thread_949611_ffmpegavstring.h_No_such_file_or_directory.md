---
title: "ffmpeg/avstring.h: No such file or directory"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Obsurd on 2008-10-16
anonymous@anonymous-desktop:~/a1$ gcc sample4a1.c -o sample -lavformat -lavcodec -lavutil -lz -lm `sdl-config --cflags --libs`

sample4a1.c:18:29: error: ffmpeg/avstring.h: No such file or directory
sample4a1.c: In function ‘main’:
sample4a1.c:412: warning: ‘img_convert’ is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
sample4a1.c:420: warning: ‘img_convert’ is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
sample4a1.c:447: warning: ‘img_convert’ is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)



I've installed ffmpeg from Sypnatic's package manager and I've installed the dev's also.

Any suggestions? I'm only concerned about the ffmpeg/avstring.h not being there.

---

