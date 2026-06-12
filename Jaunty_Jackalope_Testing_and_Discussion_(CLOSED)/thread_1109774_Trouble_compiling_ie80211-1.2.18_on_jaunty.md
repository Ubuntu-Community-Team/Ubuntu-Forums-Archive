---
title: "Trouble compiling ie80211-1.2.18 on jaunty"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by modz on 2009-03-29
Hi all, I am  completely new to linux and ubuntu and only know some a few very basic things.

I did find in another topic that some of the files needed to be modified, but even after making the changes i have issues compiling.

Here is what happens when I attempt to compile ieee80211-1.2.18

```
nick@nick-laptop:~$ cd ieee80211-1.2.18
nick@nick-laptop:~/ieee80211-1.2.18$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.28-9-generic for ieee80211 components...
make -C /lib/modules/2.6.28-9-generic/build M=/home/nick/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-9-generic'
/home/nick/ieee80211-1.2.18/Makefile:17: 
/home/nick/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/nick/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/nick/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/nick/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/nick/ieee80211-1.2.18/ieee80211_module.o
  CC [M]  /home/nick/ieee80211-1.2.18/ieee80211_tx.o
  CC [M]  /home/nick/ieee80211-1.2.18/ieee80211_rx.o
  CC [M]  /home/nick/ieee80211-1.2.18/ieee80211_wx.o
/home/nick/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_translate_scan’:
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:61: error: too few arguments to function ‘iwe_stream_add_event’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:70: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:70: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:70: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:70: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:73: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:73: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:73: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:73: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:80: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:80: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:80: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:80: error: too few arguments to function ‘iwe_stream_add_event’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:90: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:90: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:90: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:90: error: too few arguments to function ‘iwe_stream_add_event’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:98: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:98: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:98: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:98: error: too few arguments to function ‘iwe_stream_add_event’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:102: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:102: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:102: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:102: error: too few arguments to function ‘iwe_stream_add_event’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:111: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:111: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:111: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:111: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:131: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:131: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:131: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:131: error: too few arguments to function ‘iwe_stream_add_value’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:138: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:138: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:138: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:138: error: too few arguments to function ‘iwe_stream_add_value’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:188: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:188: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:188: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:188: error: too few arguments to function ‘iwe_stream_add_event’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:195: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:195: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:195: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:195: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:215: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:215: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:215: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:215: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:236: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:236: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:236: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:236: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:248: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:248: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:248: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:248: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:269: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:269: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:269: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:269: error: too few arguments to function ‘iwe_stream_add_point’
/home/nick/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_wx_set_encodeext’:
/home/nick/ieee80211-1.2.18/ieee80211_wx.c:631: warning: format not a string literal and no format arguments
make[2]: *** [/home/nick/ieee80211-1.2.18/ieee80211_wx.o] Error 1
make[1]: *** [_module_/home/nick/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-9-generic'
make: *** [modules] Error 2
nick@nick-laptop:~/ieee80211-1.2.18$ 

```

If anyone has any suggestions, I'd be willing to try just about anything...

---

